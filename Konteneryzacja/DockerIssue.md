Problem był dokładnie taki:

Docker próbował wystartować **swoją sieć** (domyślny driver `bridge` + NAT), a do tego potrzebuje w kernelu działających rzeczy z netfilter/iptables: tablicy `nat` i matcha `addrtype`. U Ciebie (WSL2 kernel 6.6.87.1) to się rozjeżdżało, więc `dockerd` wywalał się na starcie.

W logach masz dwa “symptomy tej samej choroby”:

1. **iptables (legacy):**
   `can't initialize iptables table 'nat': Table does not exist`
   czyli brak/nieaktywna tablica NAT w jądrze (albo moduły/konfiguracja WSL tego nie udostępnia w sposób, którego oczekuje Docker).

2. **iptables (nf_tables):**
   `Couldn't load match 'addrtype': No such file or directory`
   czyli brakujący/niezaładowany matcher `xt_addrtype` (albo niekompatybilność wariantu iptables z tym, co jest dostępne w WSL). Nawet jak `modprobe xt_addrtype` zwracało 0, to i tak na ścieżce Dockera się to nie spinało.

Efekt: **Docker nie wstawał**, więc klient krzyczał:
`Cannot connect to the Docker daemon at unix:///var/run/docker.sock`

### Dlaczego “naprawa” zadziałała

W `daemon.json` ustawiliśmy:

```json
{
  "iptables": false,
  "ip6tables": false,
  "bridge": "none",
  "ip-forward": false
}
```

Czyli powiedzieliśmy Dockerowi:
“Nie dotykaj iptables, nie twórz bridge’a, nie rób NAT, nie baw się w forwarding”.

Wtedy `dockerd` nie próbuje w ogóle stawiać tej warstwy sieciowej, na której się wcześniej wywalał — i dlatego usługa startuje, `docker info` działa, a `hello-world` się uruchomił (bo on w zasadzie nie potrzebuje sieci poza samym pobraniem obrazu, a to poszło).

### Co oznacza ostrzeżenie teraz

`WARNING: IPv4 forwarding is disabled. Networking will not work.`

To jest konsekwencja tej “terapii odwykowej” — kontenery w takiej konfiguracji mogą działać, ale **sieć w stylu “Docker na Linuxie” nie będzie działać** (bridge, port mapping `-p`, NAT).

Najmniej-bolesna praktyka w tym trybie to:

* uruchamiać serwisy z `--network host` (w WSL często to i tak jest najbardziej sensowne),
* albo akceptować `--network none` dla rzeczy bez sieci.

Świat jest tu trochę jak smok: działa, ale trzeba go głaskać zgodnie z instrukcją obsługi WSL.
