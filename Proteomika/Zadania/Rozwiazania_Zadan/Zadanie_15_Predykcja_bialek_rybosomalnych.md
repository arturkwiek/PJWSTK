# Zadanie 15. Predykcja białek rybosomalnych

## Treść / cel

Przykład: RPL3, RPS6, RPL13A.

## Rozwiązanie

### Modelowy zestaw wyników

*(Nazwy predykcji mogą różnić się w zależności od wersji modeli)*

#### RPL3 (P39023)
- **Funkcja:** Składnik dużej podjednostki 60S, udział w translacji i centrum peptydylotransferazowym
- **Lokalizacja:** Jądro/jąderko oraz cytozol

#### RPS6 (P62753)
- **Funkcja:** Składnik małej podjednostki 40S, wiązanie RNA i regulacja translacji
- **Lokalizacja:** Jądro/jąderko oraz cytozol

#### RPL13A (P40429)
- **Funkcja:** Składnik 60S, wiązanie rRNA; dodatkowo udział w kompleksie GAIT
- **Lokalizacja:** Jąderko/cytozol

### Oczekiwane wyniki narzędzi

#### DeepLoc
Powinien wskazywać **lokalizację wewnątrzkomórkową**, bez peptydu sygnałowego i domen transbłonowych.

#### AlphaFold
- Powinien przewidzieć **uporządkowane rdzenie**
- Dodatnio naładowane ogony wiążące rRNA mogą mieć **niższą ufność**
