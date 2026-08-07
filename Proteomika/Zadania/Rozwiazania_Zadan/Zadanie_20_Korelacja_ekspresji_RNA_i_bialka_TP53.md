# Zadanie 20. Korelacja ekspresji RNA i białka TP53 w raku piersi

## Treść / cel

W cBioPortal (TCGA Breast Invasive Carcinoma, PanCancer Atlas) sprawdzić korelację
mRNA TP53 (oś X) vs białko TP53 RPPA (oś Y), odczytać współczynniki i zinterpretować.

## Rozwiązanie

### Przeklikanie (kroki 45–50)
1. `cbioportal.org` → wybierz badanie **„Breast Invasive Carcinoma (TCGA, PanCancer Atlas)"** → **Query**.
2. W polu genów wpisz **TP53** → **Submit Query**.
3. Otwórz zakładkę **Plots**.
4. **Oś pozioma (X):** Gene = TP53, Data type = **mRNA expression**, profil = **RNA Seq V2 RSEM**.
5. **Oś pionowa (Y):** Gene = TP53, Data type = **Protein level (RPPA)** → *Protein expression (RPPA)*.
6. Nad wykresem cBioPortal wyświetla **Spearman's** i **Pearson's** oraz **liczbę próbek (n)** — przepisz je do sprawozdania.

### Wynik — czego się spodziewać (a dokładne liczby odczytaj z wykresu)
Korelacja jest zwykle **dodatnia, ale słaba** (typowo |r| rzędu ~0,1–0,3). To znaczy: poziom mRNA
TP53 tłumaczy tylko małą część zmienności poziomu białka. **Nie wpisuj liczby „z pamięci"** —
podaj wartości Spearmana i Pearsona z własnej sesji + n.

### Dlaczego akurat p53 słabo koreluje — przyczyna kluczowa
TP53 to podręcznikowy przykład **rozprzęgnięcia mRNA↔białko**:
- W raku piersi **zmutowane p53 ulega akumulacji/stabilizacji** — traci degradację przez MDM2,
  więc **wysoki poziom białka** może występować przy niezmienionym lub niskim mRNA.
- RPPA mierzy **całkowite** p53 (dziki + zmutowany), więc status mutacji TP53 „miesza" zależność
  mRNA–białko w kohorcie. To główny powód słabej korelacji (potwierdzone w analizach TCGA).

### Pozostałe (ogólne) przyczyny, że mRNA ≠ białko
1. Różna wydajność translacji.
2. Stabilność/degradacja białka (oś MDM2–ubikwitynacja–proteasom; krótki t½ dzikiego p53).
3. Modyfikacje potranslacyjne wpływające na stabilność i wykrywalność.
4. Różny czas życia mRNA i białka.
5. Zmiany liczby kopii i mutacje.
6. Jakość i skład próbki (domieszka komórek nienowotworowych).
7. Różnice techniczne i normalizacja (RNA-Seq V2 RSEM vs przeciwciało RPPA, szum pomiaru).

### Wniosek
Słaba, dodatnia korelacja pokazuje, że poziom białka p53 jest **regulowany głównie
potranskrypcyjnie** (stabilność, degradacja, mutacje), a nie samą ilością mRNA. Oceniaj
**wielkość |r|**, nie tylko znak; korelacja **nie jest dowodem przyczynowości**.

## Do oddania (checklista)
- [ ] Wykres rozrzutu (zrzut z cBioPortal)
- [ ] Wartości Spearmana i Pearsona + n (z sesji)
- [ ] Interpretacja biologiczna (jak wyżej)
