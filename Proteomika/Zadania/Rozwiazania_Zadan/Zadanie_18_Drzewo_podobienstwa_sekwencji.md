# Zadanie 18. Drzewo podobieństwa sekwencji

## Treść / cel

Zbudować drzewo (MAFFT → Tree / Phylo.io) i wskazać klastry oraz pary/grupy
najbardziej podobnych sekwencji.

## Rozwiązanie

> Wartości policzone z rzeczywistego MSA (identyczność liczona po kolumnach bez luk).

### Macierz podobieństwa — najważniejsze pary (% identyczności)

| Para | % ident. |
|---|---|
| **Seq_A – Seq_B** | **91,1%** (najbliższa para) |
| Seq_A – Seq_C | 75,0% |
| Seq_A – Seq_F | 73,3% |
| Seq_B – Seq_F | 72,9% |
| Seq_B – Seq_C | 72,4% |
| Seq_C – Seq_F | 68,9% |
| Seq_C – Seq_G | 67,2% |
| Seq_E – Seq_G | 63,0% |
| Seq_D – Seq_G | 61,6% |
| Seq_D – Seq_E | 60,0% |

(Najniższe: Seq_B–Seq_E 54,5%, Seq_A–Seq_E 55,1%.)

### Klastry (topologia drzewa NJ)

- **Klaster główny {A, B, F, C}:** rdzeń stanowią **A i B** (91,1% — siostrzane), do nich
  dołącza **F**, a następnie **C** (~73–75%).
- **Grupa rozbieżna:** **D i E** tworzą osobną parę (60%), a **G** odgałęzia się najwcześniej
  (najbardziej bazalna/odrębna sekwencja).

Szkic drzewa:
```
        ┌─ Seq_A
     ┌──┤        (A,B = 91%)
  ┌──┤  └─ Seq_B
  │  └──── Seq_F
──┤─────── Seq_C
  │  ┌───── Seq_E
  ├──┤      (D,E)
  │  └───── Seq_D
  └──────── Seq_G   (najbardziej odległa)
```

### Wniosek

Konserwowany rdzeń (Zad. 17) daje wspólną funkcję całej rodziny, ale rozbieżne pętle/ogony
(region 108–120) rozdzielają sekwencje: blisko spokrewnione A/B/F/C kontra rozproszone D/E/G.
Różnice ładunku ogona (K/R w F, E/D w D, N/T w E) mogą odpowiadać za różnice w regulacji,
lokalizacji lub oddziaływaniach specyficznych dla linii.

> Uwaga: to drzewo **podobieństwa** krótkiego zestawu fragmentów, nie pełna filogeneza gatunków.
