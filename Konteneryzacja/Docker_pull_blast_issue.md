**co ten błąd oznacza** oraz **dlaczego rozwiązanie wygląda tak, a nie inaczej**.

---

# 🔍 **Co dokładnie mówi błąd?**

Fragment kluczowy:

```
lookup registry-1.docker.io on [::1]:53: read udp [::1]:53249->[::1]:53: read: connection refused
```

Tłumacząc na ludzki język:

- Docker próbuje pobrać obraz z Docker Hub.
- Żeby to zrobić, musi najpierw rozwiązać nazwę domeny `registry-1.docker.io` → na adres IP.
- Do tego używa DNS.
- **WSL2 próbuje użyć DNS na adresie `::1`**, czyli **localhost (IPv6)**.
- Na `::1:53` **nie działa żaden serwer DNS**, więc odpowiedź brzmi: *connection refused*.

Czyli: **WSL2 ma źle ustawiony DNS i Docker nie może rozwiązać nazw domen.**

---

# 🧠 **Dlaczego WSL2 czasem ustawia DNS na 127.0.0.1 / ::1?**

Powody są trzy:

1. **VPN** – wiele VPN-ów podmienia DNS i WSL dostaje błędną konfigurację.
2. **Docker Desktop** – potrafi wstrzyknąć własny DNS, który w WSL nie działa.
3. **WSL regeneruje `/etc/resolv.conf` przy każdym starcie**, czasem błędnie.

Efekt: WSL zaczyna myśleć, że DNS jest na localhost, a tam nic nie działa.

---

# 🛠️ **Rozwiązanie — dlaczego działa?**

Naprawa polega na dwóch krokach:

---

## **1. Ustawiamy poprawny DNS w `/etc/resolv.conf`**

Czyli:

```bash
sudo bash -c "echo 'nameserver 8.8.8.8' > /etc/resolv.conf"
```

To wymusza użycie DNS Google (może być też Cloudflare 1.1.1.1).

Dzięki temu:

- WSL wie, gdzie pytać o adresy domen.
- Docker odzyskuje możliwość pobierania obrazów.

---

## **2. Blokujemy WSL przed nadpisywaniem DNS**

WSL domyślnie **nadpisuje** `/etc/resolv.conf` przy każdym starcie.

Dlatego dodajemy:

```bash
sudo bash -c "echo -e '[network]\ngenerateResolvConf = false' > /etc/wsl.conf"
```

To mówi WSL:

> *Nie generuj własnego resolv.conf, zostaw mój.*

Bez tego — po restarcie problem wróci.

---

## **3. Restart WSL**

```powershell
wsl --shutdown
```

Po ponownym uruchomieniu WSL korzysta już z poprawnego DNS.

---

# 🧪 **Jak sprawdzić, że działa?**

W WSL:

```bash
nslookup google.com
```

Jeśli dostaniesz IP → DNS działa.

Potem:

```bash
docker pull ncbi/blast-static
```

I powinno pójść.

---