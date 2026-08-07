# Zadanie 6. Identyfikacja białka metodą MS

## Treść / cel

Opisz drogę od białka do identyfikacji.

## Rozwiązanie

Białka z próbki są najpierw rozcinane proteazą, najczęściej **trypsyną**, na krótsze peptydy.

**Spektrometr mierzy** stosunek masy do ładunku (m/z) jonów peptydowych.

**Wybrany jon** jest następnie fragmentowany, a widmo MS/MS zawiera serię fragmentów, z których można odtworzyć lub potwierdzić sekwencję peptydu.

**Program porównuje** widma eksperymentalne z widmami teoretycznymi wygenerowanymi z bazy sekwencji, np. UniProt/FASTA.

**Zestaw wiarygodnie dopasowanych peptydów** pozwala wnioskować, które białka były obecne w próbce.

**Wyniki filtruje się** statystycznie, np. kontrolując FDR (False Discovery Rate).
