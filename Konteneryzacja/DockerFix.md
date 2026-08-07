Pewnie — masz gotowy **fix guide** na podstawie tego, co przerobiliśmy (WSL2 + Ubuntu 22.04 + Docker, problem z iptables/nat/addrtype).

---

## Fix guide: Docker nie startuje w WSL2 (iptables/nat/addrtype)

### Objawy

* `systemctl restart docker` kończy się błędem
* `docker ps` / `docker run hello-world` zwraca:
  `Cannot connect to the Docker daemon at unix:///var/run/docker.sock`
* W `journalctl -u docker.service` widać błędy typu:

  * `can't initialize iptables table 'nat': Table does not exist`
  * `Couldn't load match 'addrtype': No such file or directory`
  * `failed to create NAT chain DOCKER`
  * `failed to append jump rules to nat-PREROUTING`

### Przyczyna (w skrócie)

Docker przy starcie próbuje ustawić sieć (`bridge`) oraz NAT przez iptables/netfilter. W WSL2 (kernel `*-microsoft-standard-WSL2+`) te elementy potrafią być niedostępne lub niekompatybilne (szczególnie `nat`/`addrtype`), więc demon Dockera wywala się podczas inicjalizacji sieci.

---

## Naprawa (działa “tu i teraz”): wyłącz Dockerowi zarządzanie siecią/iptables

### 1) (Opcjonalnie) potwierdź błąd w logach

```bash
sudo journalctl -u docker.service -n 200 --no-pager
```

### 2) Utwórz konfigurację `daemon.json`

```bash
sudo mkdir -p /etc/docker

sudo tee /etc/docker/daemon.json >/dev/null <<'JSON'
{
  "iptables": false,
  "ip6tables": false,
  "bridge": "none",
  "ip-forward": false
}
JSON
```

### 3) Zrestartuj Dockera

```bash
sudo systemctl daemon-reload
sudo systemctl reset-failed docker
sudo systemctl restart docker
sudo systemctl status docker --no-pager
```

### 4) Test

```bash
docker info
docker run hello-world
```

---

## Co po fixie (ważne)

Po tej konfiguracji Docker powinien działać, ale zobaczysz ostrzeżenie:

`WARNING: IPv4 forwarding is disabled. Networking will not work.`

To oznacza:

* klasyczne dockerowe sieci (`bridge`, NAT, `-p 8080:80`) mogą **nie działać**
* kontenery, które nie wymagają sieci, będą OK
* jeżeli potrzebujesz sieci, typowe obejścia to:

  * `--network host` (często najbardziej praktyczne w WSL)
  * albo świadome używanie `--network none`

---

## Szybki rollback (powrót do domyślnego zachowania Dockera)

Jeśli chcesz wrócić do standardowego trybu (i sprawdzać, czy w Twoim setupie już działa):

```bash
sudo rm -f /etc/docker/daemon.json
sudo systemctl reset-failed docker
sudo systemctl restart docker
```

---

### Notatka diagnostyczna (dla potomnych)

W WSL2 można mieć mylące sytuacje typu:

* `modprobe xt_addrtype` zwraca 0, a i tak iptables/nft nie potrafi użyć matcha w sposób, jakiego oczekuje Docker.
* `iptables-legacy` vs `iptables-nft`: przełączanie alternatyw czasem tylko zmienia rodzaj błędu, nie rozwiązuje problemu.