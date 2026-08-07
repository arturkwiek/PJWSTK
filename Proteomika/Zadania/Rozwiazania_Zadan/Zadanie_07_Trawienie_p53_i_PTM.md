# Zadanie 7. Trawienie p53 i PTM

## Treść / cel

PeptideCutter i PhosphoSitePlus.

## Rozwiązanie

### A. Trawienie trypsyną

Dla kanonicznej sekwencji p53 P04637 (393 aa), przy pełnym trawieniu trypsyną i regule „cięcie po K/R, nie przed P", otrzymuje się **45 fragmentów teoretycznych**.

Liczba w PeptideCutter może różnić się zależnie od ustawień i sposobu liczenia bardzo krótkich peptydów.

### B. Modyfikacje potranslacyjne p53

p53 jest **silnie modyfikowane:**
- **Fosforylacje** głównie w N- i C-końcu
- **Acetylacje lizyn** w domenie wiążącej DNA i C-końcu
- **Ubikwitynacje lizyn** C-końcowych
- **Inne modyfikacje:** metylacja, sumoilacja, neddylacja i inne

### C. Źródła danych

Dane pochodzą z doświadczeń opisanych w literaturze:
- MS/MS
- Immunobloty z przeciwciałami swoistymi dla PTM
- Mutageneza i testy funkcjonalne

**MS wykrywa** przesunięcie masy i fragmenty lokalizujące modyfikację na konkretnym aminokwasie.
