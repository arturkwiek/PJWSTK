# Projekt 3 - Przykład: Receptor EGFR (P00533)

## Motywacja

Białko o **znaczeniu onkologicznym**, z licznymi strukturami eksperymentalnymi i bogatymi danymi proteomicznymi.

## Parametry białka

- **Liczba aminokwasów:** 1210 aa
- **Topologia:** Receptor jednoprzejściowy
- **Strukturalne domeny:**
  - Domena zewnątrzcomórkowa
  - Helisa 646-668 (transbłonowa)
  - Cytoplazmatyczna domena kinazowa 712-979
  - Elastyczny ogon C-końcowy

## AlphaFold vs PDB

### Przewidywanego struktury
- **Domeny lokalne** powinny być wiarygodne

### Wymagająca walidacji
- **Wzajemna orientacja domen** - może być niepewna
- **Ogon C-końcowy** - elastyczny, trudny do przewidzenia

### Struktury eksperymentalne
- Czasami obejmują tylko fragmenty
- Określają tylko wybrane stany aktywacji

## Interaktom EGFR

### Partnerzy interakcji
- ERBB2/3
- GRB2
- SHC1
- CBL
- PLCG1
- PIK3R1
- STAT3
- SRC
- Regulatory endocytozy

### Podział funkcjonalny sieci
- **Sygnalizacja**
- **Internalizacja/degradacja**
- **Regulacja transkrypcji**

## Ekspresja

### Human Protein Atlas (HPA)
- Szeroka ekspresja
- Profil podwyższony m.in. w łożysku

### W nowotworach
- Amplifikacja/aktywacja EGFR jest zależna od typu guza
- Wymaga pobrania z konkretnego datasetu

## Predykcje ML

### Lokalizacja
Powinna wskazać **błonę komórkową**

### Funkcja
- Receptorowa aktywność kinazy tyrozynowej
- Sygnalizacja wzrostowa

## Wymagania sprawozdania

Należy:
1. **Pobrać dane MS** z konkretnego datasetu i opisać warunki
2. **Porównać wyniki** z:
   - UniProt
   - PDB
   - HPA
3. **Dołączyć:**
   - Model struktury
   - Zrzuty ekranów
   - Tabelę interaktorów

## Podsumowanie

Projekt obejmuje kompleksową analizę:
- Struktury białka (teoretycznej i eksperymentalnej)
- Funkcji (wiązanie ligandu, sygnalizacja)
- Lokalizacji i ekspresji
- Interakcji i regulacji
