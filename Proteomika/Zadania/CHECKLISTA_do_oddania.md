# Checklista — co jeszcze po Twojej stronie

Stan: treść merytoryczna zadań 3–20 zweryfikowana i poprawiona. Poniżej tylko to, czego
nie da się zrobić bez Ciebie (zrzuty, wartości z Twojej sesji, własne pliki wynikowe).

Legenda: 🟥 wymagane w „Do oddania" · 🟨 wartość do odczytania/potwierdzenia · ⬜ opcjonalne/estetyczne

---

## A. MUSISZ dorobić (bez tego brakuje elementu ocenianego)

- 🟥 **Zad 3 — PRIDE:** otwórz akcesję **PXD073999** na PRIDE i potwierdź, że istnieje i dotyczy p53; jeśli nie — podmień na inny projekt (metoda w pliku Zad 3).
- 🟥 **Zad 3 — PaxDb:** zrzut ekranu + odczytaj wartość **ppm** z górnego wiersza posortowanej tabeli.
- 🟥 **Zad 5:** zrzut ekranu z **EMDB/PDB** (EMD-33533 / model 7XZX).
- 🟥 **Zad 11:** zbuduj sieć w **STRING** (TP53, 0.700, ≤50) → zrzut sieci + zapisane parametry (wersja STRING + data).
- 🟥 **Zad 13:** uruchom **AlphaFold** (albo pobierz z AlphaFold DB: `alphafold.ebi.ac.uk/entry/O14717`) → zapisz **model PDB/CIF** + zrzut z legendą **pLDDT**; zaznacz regiony niskiej ufności na SWOIM modelu.
- 🟥 **Zad 15:** pobierz **3 × FASTA** (RPL3 P39023, RPS6 P62753, RPL13A P40429) → uruchom **DeepGOPlus/PANNZER2** (funkcja) i **DeepLoc 2.0** (lokalizacja) → zapisz wyniki.
- 🟥 **Zad 20:** uruchom **cBioPortal** (BRCA PanCancer, TP53, Plots: X=mRNA RSEM, Y=RPPA) → zrzut wykresu rozrzutu.

## B. Do ODCZYTANIA / POTWIERDZENIA (liczby z Twojej sesji — nie wpisuj „z pamięci")

- 🟨 **Zad 7 — PeptideCutter:** dokładna liczba cięć/peptydów trypsyny (mój szacunek ~44 cięć → ~45 peptydów).
- 🟨 **Zad 10 — PhosphoSitePlus:** liczba miejsc fosforylacji (rozdziel pTyr / pSer / pThr). UniProt masz już zrobione (ze zrzutem).
- 🟨 **Zad 12 — STRING:** odczytaj realne stopnie węzłów (huby) ze swojej sieci + kliknij węzły → terminy **GO**.
- 🟨 **Zad 14 — RMSD:** nałóż model na **1G55** (ChimeraX `matchmaker` / PyMOL `align`) → podaj **RMSD + liczbę dopasowanych reszt + zakres**.
- 🟨 **Zad 20 — korelacja:** przepisz **Spearman** i **Pearson** + **n** z wykresu (spodziewaj się słabej dodatniej).

## C. OPCJONALNE (masz gotowe wyniki ode mnie; zrzut tylko dla kompletu)

- ⬜ **Zad 4:** zrzut 3D z RCSB 3KMD (w treści było „miejsce na notatki", zrzut nieobowiązkowy).
- ⬜ **Zad 17/18/19:** możesz wygenerować własne MSA/drzewo/logo w MAFFT/Phylo.io/WebLogo dla zrzutów — liczby i gotowe logo już masz (uwaga: numeracja kolumn może się nieznacznie różnić od mojego FAMSA).
- ⬜ **Zad 16:** porównanie wyników narzędzi z UniProt — zrób po uzyskaniu wyników z Zad 15 (tabelę UniProt masz gotową).

## D. Zadania w pełni gotowe (nic nie robisz)
Zad 6, 8, 9 — kompletne (Zad 9 z wykresem).

## E. Wciąż po MOJEJ stronie (na Twoją prośbę)
- ⬜ **Zad 1 i 2** — jeszcze ich nie zweryfikowałem (przeskoczyliśmy od razu do 3). Mogę sprawdzić — mam już dane UniProt (insulina P01308, hemoglobina β P68871, lizozym P61626, EC 3.2.1.17, wariant HbS).
- ⬜ **Projekty 1–3** — do przeglądu/szablonów.

---

## Końcowa lista kontrolna (z podręcznika — sprawdź przy każdym zadaniu)
- [ ] Każdy zrzut/wykres ma **podpis i źródło**.
- [ ] Wyniki zawierają **identyfikatory** (UniProt/PDB/PXD/ENSP).
- [ ] W obliczeniach podano **wzór i jednostki**.
- [ ] Wnioski oddzielają **obserwację od interpretacji**.
- [ ] Raport projektowy zapisany jako **PDF**.
