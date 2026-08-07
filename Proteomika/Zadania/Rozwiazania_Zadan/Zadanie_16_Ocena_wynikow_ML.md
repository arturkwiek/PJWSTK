# Zadanie 16. Ocena wyników ML

## Treść / cel

Porównaj z UniProt.

## Rozwiązanie

### Biologiczna sensowność predykcji

Predykcje są biologicznie sensowne, jeśli wskazują:
1. Udział w **rybosomie/translacji**
2. **Lokalizację jądrowo-jąderkową** i cytoplazmatyczną

### Interpretacja lokalizacji

Białka rybosomalne są:
1. **Syntetyzowane** w cytozolu
2. **Importowane do jądra/jąderka** w celu składania podjednostek
3. **Wracają** w dojrzałych podjednostkach do cytoplazmy

### Rozbieżności między narzędziami

Rozbieżność między przewidywaniami a danymi z UniProt **nie musi oznaczać błędu** ponieważ:
- Modele zwykle zwracają **jedną dominującą lokalizację**
- W rzeczywistości białko **przechodzi między przedziałami**
- **UniProt** ma pierwszeństwo jako źródło ręcznie kuratorowanych danych eksperymentalnych

### Wniosek

Dane z UniProt powinny być traktowane jako złoty standard porównania.
