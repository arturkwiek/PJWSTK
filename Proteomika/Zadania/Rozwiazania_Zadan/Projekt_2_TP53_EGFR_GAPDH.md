# Projekt 2 - Przykład: TP53, EGFR i GAPDH

## 1. TP53 (P04637)

### Charakterystyka
- **Lokalizacja:** Jądrowa/cytozosolowa
- **Funkcja:** Wiązanie DNA i regulacja transkrypcji
- **Struktura:** 
  - Uporządkowana domena wiążąca DNA
  - Nieuporządkowane końce

### Wymagania
- Przewidzieć lokaliz ację jądrową/cytozolową
- Opisać strukturę i funkcję
- Porównać z danymi eksperymentalnymi

## 2. EGFR (P00533)

### Charakterystyka
- **Lokalizacja:** Błona komórkowa
- **Typ:** Receptorowa kinaza tyrozynowa
- **Struktura:**
  - Domena zewnątrzkomórkowa
  - Pojedyncza helisa transbłonowa
  - Domena kinazowa
  - Elastyczny ogon C-końcowy

### Ważna uwaga
**Pełna konformacja** zależy od ligandu i dimeryzacji. Model nie będzie zawierać pełnej orientacji domen bez ligandu.

## 3. GAPDH (Gliceraldehyd-3-fosforan dehydrogenaza)

### Charakterystyka
- **Lokalizacja:** Cytozol
- **Funkcja:** Enzym glikolizy
- **Struktura:** Globularna

### Oczekiwane rezultaty
- **Model globularny** o wysokiej ufności
- **Zgodny** ze strukturami PDB

## Porównanie wyników

### Oczekiwania
Predykcje ML będą **najlepiej zgodne dla dobrze scharakteryzowanych białek** (GAPDH).

### Największe niepewności
Dotyczą:
- **Wielolokalizacyjności** (TP53)
- **Regionów nieuporządkowanych** (TP53)
- **Stanów kompleksowych** (EGFR - ligand-bound)

## Wnioski
Modele ML działają dobrze dla:
1. Białek strukturalnie dobrze scharakteryzowanych
2. Białek z wystarczającą liczbą homologów
3. Białek bez dużych regionów nieuporządkowanych
