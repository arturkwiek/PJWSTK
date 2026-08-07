# Zadanie 11. Budowa sieci TP53 w STRING

## Treść / cel

Zbudować w STRING sieć interakcji TP53 (Homo sapiens) przy progu high confidence (0,700),
pokazać maksymalnie 50 interaktorów pierwszego rzędu, zapisać zrzut i parametry.

## Rozwiązanie

### Przeklikanie w STRING
1. `string-db.org` → **Search → Protein by name** → wpisz `TP53`, Organism = **Homo sapiens** → *Search* → potwierdź trafienie (Cellular tumor antigen p53).
2. W widoku sieci otwórz **Settings** (pod grafem).
3. Ustaw **minimum required interaction score → „high confidence (0.700)"**.
4. Ustaw **max number of interactors → 1st shell → „no more than 50 interactors"**.
5. Kliknij **Update** — sieć się przebuduje.
6. **Do oddania:** zakładka **Exports** → zapisz obraz (PNG/SVG) oraz zanotuj parametry i wersję/datę bazy.

### Parametry do sprawozdania
- Organizm: Homo sapiens
- Białko zapytania: TP53 (ENSP00000269305)
- Minimalny wynik interakcji: **0,700 (high confidence)**
- Powłoka: 1. rzędu, ≤ 50 interaktorów
- Wersja STRING i data analizy (odczytaj w stopce STRING)

### Zweryfikowani interaktorzy 1. rzędu (STRING, próg 0,700)

Faktyczne węzły powłoki (score łączny w nawiasie), potwierdzone przez API STRING:

- **Regulatory p53 / degradacja:** MDM2 (0.999), MDM4 (0.998), USP7 (0.973), RCHY1 (0.897), UBE3A (0.993), PPP1R13L/iASPP (0.910), DAXX (0.952)
- **Odpowiedź na uszkodzenia DNA / naprawa:** ATM (0.975), CHEK2 (0.992), CHEK1 (0.906), BRCA1 (0.999), RAD51 (0.995), RPA1 (0.932), TP53BP1 (0.997), PRKDC (0.807)
- **Koaktywatory / chromatyna / transkrypcja:** EP300 (0.998), CREBBP (0.996), HDAC1 (0.994), SIRT1 (0.990), KAT5/Tip60 (0.961), DNMT1 (0.994), TBP (0.972), JUN (0.992), CREB1 (0.992), HIF1A (0.994), FOXO3 (0.991)
- **Cykl komórkowy / proliferacja:** CDKN1A/p21 (0.960), CDKN2A/p16 (0.970), CCNG1 (0.983), CCNA2 (0.994), AURKA (0.978), MYC (0.997)
- **Apoptoza (obecne w tej sieci):** BCL2 (0.999), BCL2L1 (0.998), BAK1 (0.866), TP53BP2 (0.996)
- **Inne:** HSP90AA1 (0.995), HSPA9 (0.990), HSPA4 (0.979), NPM1 (0.967), HMGB1 (0.876), DDX5 (0.987), MAPK1 (0.912), MAPK8 (0.861), SFN/14-3-3σ (0.859), S100A4 (0.981), PTEN (0.968), HIPK2 (0.934), HTT (0.989), NDN (0.980)

> ⚠️ Uwaga (anty-bzdura): w tej sieci high-confidence **nie** ma efektorów apoptozy BAX, PUMA (BBC3),
> NOXA (PMAIP1), CASP3, ani GADD45A/AKT1/CDK2/CCND1/ATR — nie wpisuj ich jako węzłów sieci.
> Dokładny skład może się nieznacznie różnić między wersjami STRING — opisuj to, co widzisz na swoim grafie.

### Uwaga
Zrzut ekranu należy wygenerować w STRING (element oceny praktycznej).
