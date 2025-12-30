Poniżej masz **CAŁY instruktaż CONT_1**, identyczny stylistycznie do oryginału, ale:

* ✔️ dopasowany do Twojego środowiska
* ✔️ z użyciem `PID=$!`
* ✔️ gotowy do oddania / wklejenia

---

# 📘 Przykład do samodzielnego wykonania (CONT_1) – wersja poprawiona

## Cel zadania

Celem zadania jest stworzenie prostej grupy kontrolnej cgroup oraz przypisanie do niej procesu, aby zrozumieć podstawy ograniczania wykorzystania zasobów CPU w systemie Linux.

---

## Instrukcja

### 1️⃣ Utwórz nową grupę kontrolną CPU o nazwie `test_group`

```bash
sudo mkdir /sys/fs/cgroup/cpu/test_group
```

---

### 2️⃣ Ustaw limit zużycia CPU dla tej grupy na 20%

Poniższe polecenia ustawią limit czasowy procesora na poziomie 20% dla procesów przypisanych do grupy `test_group`.

```bash
echo 100000 | sudo tee /sys/fs/cgroup/cpu/test_group/cpu.cfs_period_us
echo 20000  | sudo tee /sys/fs/cgroup/cpu/test_group/cpu.cfs_quota_us
```

---

### 3️⃣ Utwórz proces obciążający CPU

```bash
while :; do :; done &
PID=$!
echo "PID=$PID"
```

Na ekranie wyświetli się numer PID uruchomionego procesu.

---

### 4️⃣ Przypisz proces do grupy `test_group`

W poleceniu wykorzystaj numer PID uzyskany w poprzednim kroku.

```bash
echo $PID | sudo tee /sys/fs/cgroup/cpu/test_group/tasks
```

---

### 5️⃣ Upewnij się, że proces został przypisany do grupy

```bash
cat /sys/fs/cgroup/cpu/test_group/tasks
```

---

### 6️⃣ Obserwuj zużycie CPU

Uruchom narzędzie monitorujące:

```bash
htop
```

Wyszukaj proces po numerze PID i zaobserwuj ograniczone wykorzystanie CPU (około 20%).
Wykonaj zrzut ekranu.

---

### 7️⃣ Zatrzymaj działający proces

```bash
kill $PID
```

---

### 8️⃣ Usuń utworzoną grupę kontrolną

Po zakończeniu ćwiczenia usuń grupę kontrolną:

```bash
sudo rmdir /sys/fs/cgroup/cpu/test_group
```

---

### 9️⃣ Zakończenie zadania

Przejdź do MS Teams i wykonaj zadanie **CONT_1** z zakładki **Zadania (Assignments)**.
