Jasne — poniżej masz **precyzyjne, techniczne wyjaśnienie przyczyny problemów** oraz **jednoznaczne rozwiązanie**, bez skrótów myślowych.

---

# 🔴 PRZYCZYNA PROBLEMÓW

## 1️⃣ Masz środowisko **hybrydowe cgroup v1 + v2**

Z Twoich wyników:

```text
/sys/fs/cgroup              → tmpfs (ro)
/sys/fs/cgroup/cpu          → cgroup v1 (rw)
/sys/fs/cgroup/unified      → cgroup v2 (rw)
```

To oznacza:

* **CPU działa w cgroup v1**
* **cgroup v2 jest zamontowane**, ale **nieaktywne funkcjonalnie dla CPU**

---

## 2️⃣ Kontroler CPU NIE jest delegowany w cgroup v2

Kluczowy dowód:

```bash
cat /sys/fs/cgroup/unified/cgroup.controllers
# (pusty wynik)
```

W cgroup v2:

* `cgroup.controllers` pokazuje **jakie kontrolery kernel udostępnia w tej gałęzi**
* jeśli `cpu` tam **nie występuje**, to:

  * plik `cpu.max` **nie powstaje**
  * próba zapisu kończy się `Permission denied`
  * `cgroup.subtree_control` **nie może zostać zmodyfikowany**

📌 To jest **decyzja kernela / systemd / hosta**, a nie błąd użytkownika.

---

## 3️⃣ Systemd / WSL / VM blokuje delegację CPU w v2

Najczęstsze powody (wystarczy jeden):

* system uruchomiony w **WSL2**
* środowisko **laboratoryjne / wirtualne**
* **systemd** zarządza cgroups i **nie deleguje CPU do użytkownika**
* brak możliwości bootowania z `systemd.unified_cgroup_hierarchy=1`

Efekt:

> cgroup v2 jest „widoczne”, ale **nie można ustawiać limitów CPU ręcznie**

---

## 4️⃣ Dlaczego `sudo` nic nie zmienia

To **nie jest problem uprawnień użytkownika**.

* `sudo tee` działa jako root
* kernel sprawdza: *czy dany kontroler jest aktywny w tej hierarchii*
* odpowiedź: **nie**
* wynik: `Permission denied`

📌 Root **nie może** zapisać do nieaktywnego kontrolera cgroup.

---

# 🟢 ROZWIĄZANIE

Masz **trzy poprawne rozwiązania**. Jedno z nich zastosowałeś.

---

## ✅ ROZWIĄZANIE 1 (ZASTOSOWANE): cgroup v1 – DZIAŁA

Ponieważ kontroler CPU **jest aktywny w v1**, używasz:

```bash
/sys/fs/cgroup/cpu
```

i plików:

* `cpu.cfs_period_us`
* `cpu.cfs_quota_us`

To:

* **realnie ogranicza CPU**
* jest **zgodne z dokumentacją**
* daje **ten sam efekt praktyczny**

➡️ **To rozwiązanie jest w 100% poprawne technicznie.**

---

## ✅ ROZWIĄZANIE 2 (ALTERNATYWA): cgroup v2 przez systemd

Jeśli środowisko wspiera systemd:

```bash
sudo systemd-run --scope -p CPUQuota=20% bash -c 'while :; do :; done'
```

Systemd:

* sam tworzy cgroup v2
* sam aktywuje kontrolery
* omija problem braku delegacji

➡️ To jest „kanoniczny” sposób w nowoczesnym Linuksie.

---

## ❌ ROZWIĄZANIE 3 (NIEDOSTĘPNE U CIEBIE): ręczne cpu.max

Wymaga:

* pełnej hierarchii cgroup v2
* aktywnego `cpu` w `cgroup.controllers`
* delegacji kontrolera do użytkownika

Czyli:

* natywny Linux
* albo VM z unified v2
* albo WSL z pełnym systemd + v2

U Ciebie **niespełnione warunki** → nie zadziała.

---

# 🧠 JEDNO ZDANIE (IDEALNE NA EGZAMIN)

> Problemy wynikały z braku delegacji kontrolera CPU w hierarchii cgroup v2 — mimo że system udostępniał punkt montowania cgroup2, kontroler CPU był aktywny wyłącznie w cgroup v1, dlatego limit CPU należało zrealizować za pomocą `cpu.cfs_quota_us`.

---

# ✅ PODSUMOWANIE

| Element       | Status              |
| ------------- | ------------------- |
| cgroup v2     | obecne, ale bez CPU |
| cpu.max       | ❌ niedostępne       |
| sudo          | działa poprawnie    |
| cgroup v1 CPU | ✅ aktywne           |
| limit CPU     | ✅ skuteczny         |
| rozwiązanie   | ✅ poprawne          |

---

