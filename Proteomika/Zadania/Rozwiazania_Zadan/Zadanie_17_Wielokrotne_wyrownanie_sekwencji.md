# Zadanie 17. Wielokrotne wyrównanie sekwencji (MSA)

## Treść / cel

Wykonać MSA sekwencji Seq_A–G w MAFFT i wskazać regiony konserwowane (małej zmienności)
oraz zmienne, z przybliżonymi zakresami pozycji w MSA.

## Rozwiązanie

> Wyniki policzone na rzeczywistym MSA 7 sekwencji (długość wyrównania = 142 kolumny,
> 68 kolumn w pełni konserwowanych 7/7). Numeracja kolumn może przesunąć się o kilka
> pozycji zależnie od narzędzia/gapów — motywy są punktem odniesienia.

### Regiony silnie konserwowane (≥ 6/7 identyczne)

- **Kolumny ~1–23:** `MKTAIIGKGGIGRNPTVEVDLST` — N-końcowy motyw typu P-loop/GTPazowy (GxxxxGK[S/T])
- **Kolumny ~47–56:** `(H)GPEFVDITG`
- **Kolumny ~60–72:** `LKQ · x · NVIFADKT` (60–62 i 65–72 w pełni konserwowane; 63–64 zmienne)
- **Kolumny ~93–106:** `GDCPVILVGNKCDL` — drugi silnie konserwowany blok rdzenia

### Regiony zmienne (duża różnorodność)

- **Kolumny ~108–120:** główny region insercyjny — skład bardzo różny w każdej sekwencji:
  - Seq_A `PQQQPPPQPQ` (Q/P), Seq_C `AGGGGSSGGGG` (G/S), Seq_D `SEEEDEDKED` (E/D),
    Seq_E `PNNNNSTNSN` (N/T), Seq_F `PKKKRKKKRKKR` (K/R), Seq_G `PTTTTATATV` (A/T)
- Kolumny ~24–37 (pętla po N-końcowym motywie) — umiarkowanie zmienne
- Kolumny ~57–59, 63–64, 73–75, 82–91 — pojedyncze pozycje zmienne
- **C-koniec ~134–142** — zmienny

### Wniosek

Konserwowany jest **rdzeń enzymatyczny** (bloki 1–23, 47–56, 60–72, 93–106 — motywy wiążące
nukleotyd/kofaktor), natomiast **pętla powierzchniowa 108–120** i końce tolerują insercje oraz
zmiany składu (ładunek/hydrofilowość różne między sekwencjami). To klasyczny wzór:
rdzeń funkcjonalny stały, pętle regulacyjne/lokalizacyjne zmienne.
