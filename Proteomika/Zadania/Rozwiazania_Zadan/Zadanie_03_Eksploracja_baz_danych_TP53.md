# Zadanie 3. Eksploracja baz danych dla TP53

## Treść / cel

Dla ludzkiego białka p53 (TP53, UniProt **P04637**) wykonać polecenia w czterech bazach:
PRIDE Archive, PhosphoSitePlus, Human Protein Atlas (HPA) i PaxDb.

> Weryfikacja względem podręcznika (rozdz. „Znaczenie baz", str. ~20–23): role baz zgadzają się ze skryptem —
> PRIDE = repozytorium surowych danych MS, PhosphoSitePlus/dbPTM = modyfikacje potranslacyjne,
> HPA = tkanki/komórki/lokalizacja subkomórkowa, PaxDb = abundancja białek.

## Rozwiązanie

### A. PRIDE Archive

> Uwaga: wybór datasetu jest indywidualny — poniższa akcesja **wymaga potwierdzenia**.
> Akcesji **PXD073999** nie udało się potwierdzić automatycznie (zapytanie zwróciło inny rekord).
> Przed oddaniem otwórz stronę projektu na PRIDE i sprawdź, że: (1) istnieje, (2) dotyczy Homo sapiens,
> (3) w opisie/wynikach faktycznie występuje TP53/p53. Jeśli nie — wybierz inny projekt wg metody poniżej.

Metoda wyboru i opisu datasetu:
1. Wejdź na `ebi.ac.uk/pride/archive`, w wyszukiwarce wpisz `TP53` (lub `p53 Homo sapiens`).
2. Zawęź filtr **Organism → Homo sapiens**.
3. Otwórz jeden projekt i przepisz pięć pól:

| Pole | Źródło na stronie PRIDE |
|---|---|
| Identyfikator (PXD…) | nagłówek projektu |
| Tytuł | nagłówek projektu |
| Organizm | metadane (Homo sapiens) |
| Cel eksperymentu | sekcja Description (1–2 zdania) |
| Dostępne dane | zakładka Files: surowe `.raw`, wyniki wyszukiwania `.mzid`/`.mzTab`/`.msf`, identyfikacje peptydów/białek, checksum |

Przykład (do podmiany po weryfikacji): projekt multi-omics dot. hamowania SIRT6 w komórkach czerniaka,
LC-MS/MS (Q Exactive), analiza w Proteome Discoverer; dane: `.raw`, `.msf`, `checksum.txt`.

### B. PhosphoSitePlus — aminokwas K120

Na pozycji **K120** (lizyna 120, w domenie wiążącej DNA) dla ludzkiego TP53 oznaczone są modyfikacje:
- **Acetylacja (K120-ac)** — modyfikacja główna, dodawana przez acetylotransferazy **Tip60 (KAT5)** i **hMOF (KAT8)**;
- **Ubikwitynacja (K120-ub)**.

Znaczenie biologiczne: acetylacja K120 przełącza odpowiedź komórki między zatrzymaniem cyklu a **apoptozą**
i wpływa na specyficzność wiązania DNA. (K120 to lizyna — nie podlega fosforylacji.)

### C. Human Protein Atlas

a) **Lokalizacja subkomórkowa p53:**
- główna: **nukleoplazma** (jądro),
- dodatkowo: **pęcherzyki (vesicles)** i **cytozol** — zgodne z rolą czynnika transkrypcyjnego.

b) **Tkanki z najwyższym poziomem ekspresji:**
- HPA klasyfikuje TP53 jako **Low tissue specificity** (niska swoistość tkankowa) — białko wyrażane szeroko,
  brak jednej dominującej tkanki. **To jest właściwa odpowiedź.**
- Na wykresie słupkowym nieco wyższe wartości bywają w tkankach silnie proliferujących
  (szpik, tkanki limfoidalne, jądro) — odczytaj 2–3 górne słupki z własnego wykresu i zaznacz, że to „low tissue specificity".

### D. PaxDb  *(POPRAWIONE)*

Wcześniejszy wniosek „brak danych" był błędny — wynikał z zatrzymania się na **liście wyników wyszukiwania**
(która pokazuje tylko gatunki z rekordem TP53, bez liczb). Tabela abundancji jest **wewnątrz rekordu ludzkiego**.

Poprawne przeklikanie:
1. `pax-db.org` → szukaj `TP53`.
2. Z listy wybierz **Homo sapiens** i otwórz rekord białka (gen TP53, `ENSP00000269305`).
3. Zjedź do tabeli **„TP53 abundance information"** (wartości w **ppm** — parts per million).
4. Kliknij nagłówek kolumny z wartością, aby **posortować malejąco**.

Wynik i interpretacja:
- Po posortowaniu na górze znajdują się zwykle zestawy **„integrated / whole organism"**; w danych **tkankowych**
  p53 jest **nisko-abundantne**.
- Jest to biologicznie spójne: p53 to ściśle regulowany czynnik transkrypcyjny obecny w małej liczbie kopii.
- W sprawozdaniu podaj **nazwę datasetu i wartość ppm z górnego wiersza własnej, posortowanej tabeli** oraz zrzut ekranu.
  Nie przepisuj konkretnych ppm „z pamięci" — odczytaj je z bazy.

## Do oddania (checklista)
- [ ] Opis jednego, **zweryfikowanego** datasetu PRIDE (5 pól)
- [ ] Modyfikacje K120: acetylacja (+ ubikwitynacja)
- [ ] Lokalizacja: nukleoplazma; tkanki: niska swoistość tkankowa
- [ ] Abundancja TP53 z **posortowanej** tabeli PaxDb + zrzut ekranu
