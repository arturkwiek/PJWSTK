# Zadanie 12. Eksploracja sieci TP53

## Treść / cel

W zbudowanej sieci: wskazać 3 białka o największej liczbie interakcji (huby),
dwa białka związane z nowotworami, moduły funkcjonalne oraz funkcje/terminy GO wybranych węzłów.

## Rozwiązanie

### Huby (białka o największej liczbie połączeń)
Centralnym węzłem jest **TP53**. Wśród interaktorów najwięcej połączeń mają zwykle
koaktywatory transkrypcyjne i główne regulatory, które łączą się także między sobą:
- **EP300**
- **CREBBP**
- **MDM2**
(w dalszej kolejności ATM, MYC).

> Jak zweryfikować degree: w STRING najedź na węzeł (pokazuje liczbę krawędzi) lub użyj zakładki
> **Analysis** — odczytaj realne stopnie z własnej sieci i podaj trzy o najwyższym stopniu.

### Dwa białka związane z nowotworami (obecne w sieci)
- **MDM2** (0.999) — ujemny regulator p53, ligaza E3 kierująca p53 do ubikwitynacji i degradacji; **onkogen**, często amplifikowany.
- **BRCA1** (0.999) — naprawa DNA i kontrola cyklu; **gen supresorowy** (rak piersi/jajnika).

(Alternatywnie również obecne: **MYC** — onkogen; **PTEN**, **CDKN2A/p16**, **ATM** — supresory.)

### Moduły funkcjonalne (tylko węzły faktycznie obecne w sieci)

**Odpowiedź na uszkodzenia DNA i naprawa**
- ATM, CHEK2, CHEK1, BRCA1, RAD51, RPA1, TP53BP1, PRKDC

**Cykl komórkowy / zatrzymanie i proliferacja**
- CDKN1A (p21), CDKN2A (p16), CCNG1, CCNA2, AURKA, MYC

**Apoptoza**
- BCL2, BCL2L1, BAK1, TP53BP2, PPP1R13L (iASPP), DAXX

**Regulacja stabilności p53 (ubikwitynacja/deubikwitynacja)**
- MDM2, MDM4, USP7, RCHY1, UBE3A

**Koaktywatory / modyfikacje chromatyny i transkrypcja**
- EP300, CREBBP, HDAC1, SIRT1, KAT5/Tip60, DNMT1, TBP, JUN, CREB1

### Przykładowe terminy GO (do odczytania po kliknięciu węzła / w zakładce Analysis)
- „DNA damage response" (GO:0006974)
- „regulation of apoptotic process" (GO:0042981)
- „cell cycle arrest" (GO:0007050)
- „negative regulation of cell population proliferation" (GO:0008285)
- „positive regulation of transcription by RNA polymerase II" (GO:0045944)

### Wniosek
Sieć pokazuje, że TP53 integruje: (1) wykrywanie uszkodzeń DNA, (2) zatrzymanie cyklu,
(3) naprawę DNA, (4) kontrolę stabilności własnego poziomu (MDM2/USP7),
oraz (5) decyzję o apoptozie — spójnie z rolą p53 jako węzła sieci nadzoru genomu.

> ⚠️ Anty-bzdura: klasyczne efektory apoptozy p53 (BAX, PUMA, NOXA, CASP3) oraz GADD45A/CCND1/CDK2/ATR
> są prawdziwe biologicznie, ale **nie występują** w tej sieci high-confidence (0,700) — nie opisuj ich jako węzłów grafu.
