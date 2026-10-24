# Raport — Laboratorium 03

**Zespół:** MealBrAIn (Patrycja Borkowska, Maria Deperas, Oliwia Partyka) 
**Data:** 22.10.2026

## Środowisko

| Parametr | K1 | K2 | K3 |
|----------|----|----|----|
| Osoba | Patrycja Borkowska| | |
| CPU | Intel Core Ultra 9 275HX, 2,70 GHz| | |
| GPU | NVIDIA GeForce RTX 5070 Ti Laptop GPU — 12 GB VRAM| | |
| RAM | 64 GB| | |
| Model A | gemma3:4b| | |
| Model B | qwen3:4b| | |

Model A i model B oznaczają dwa modele badane na danym komputerze, zgodnie z tabelą powyżej.

Wszystkie komputery korzystają z tego samego zbioru testowego, promptów i ustawień eksperymentów. Czasy odpowiedzi porównujemy przede wszystkim w obrębie jednego komputera; porównanie między komputerami uwzględnia różnice sprzętowe.

| Zbiór danych | Liczba notatek |
|-------------|----------------|
| Zbiór testowy używany w eksperymentach (examples.csv) | 10 |

## EXP-00 — Sposób oceny wyników

Jak oceniamy poprawność odpowiedzi modelu? Jakie metryki przyjmujemy i dlaczego?

| Metryka | Definicja |
|---------|-----------|
| **Floor accuracy** | Trafność rozpoznania numeru piętra. |
| **Elevator accuracy** | Trafność rozpoznania obecności windy. |
| **Exact match** | Odsetek notatek z poprawnym piętrem i windą jednocześnie. |

## EXP-01 — Porównanie modeli

### Komputer K1

| Model | Floor accuracy | Elevator accuracy | Exact match | Średni czas [ms] |
|-------|----------------|-------------------|-------------|------------------|
| model A |90% | 80%| 70%| 2309|
| model B | 100% | 100% |100% | 111451|

### Komputer K2

| Model | Floor accuracy | Elevator accuracy | Exact match | Średni czas [ms] |
|-------|----------------|-------------------|-------------|------------------|
| model A | | | | |
| model B | | | | |

### Komputer K3

| Model | Floor accuracy | Elevator accuracy | Exact match | Średni czas [ms] |
|-------|----------------|-------------------|-------------|------------------|
| model A | | | | |
| model B | | | | |

**Exact match** oznacza odsetek notatek, dla których model poprawnie rozpoznał jednocześnie oba pola: floor i elevator.

**Wnioski (K1, K2, K3 i porównanie):**

## EXP-02 — Prompting

### Komputer K1

| Wariant | Floor accuracy | Elevator accuracy | Exact match |
|---------|----------------|-------------------|-------------|
| zero-shot | 100%| 100%| 100%|
| one-shot | 100%| 100%| 100%|
| few-shot | 100%| 100%| 100%|

### Komputer K2

| Wariant | Floor accuracy | Elevator accuracy | Exact match |
|---------|----------------|-------------------|-------------|
| zero-shot | | | |
| one-shot | | | |
| few-shot | | | |

### Komputer K3

| Wariant | Floor accuracy | Elevator accuracy | Exact match |
|---------|----------------|-------------------|-------------|
| zero-shot | | | |
| one-shot | | | |
| few-shot | | | |

**Wnioski (K1, K2, K3 i porównanie):**

## EXP-03 — Temperature

### Komputer K1

| Temperature | Exact match | Powtarzalne notatki |
|-------------|-------------|---------------------|
| 0.0 | 100%| 10/10 |
| 0.5 |  100%| 10/10 |
| 1.0 |   100%| 10/10 |
### Komputer K2

| Temperature | Exact match | Powtarzalne notatki |
|-------------|-------------|---------------------|
| 0.0 | | |
| 0.5 | | |
| 1.0 | | |

### Komputer K3

| Temperature | Exact match | Powtarzalne notatki |
|-------------|-------------|---------------------|
| 0.0 | | |
| 0.5 | | |
| 1.0 | | |

Powtarzalne notatki to notatki z takim samym wynikiem we wszystkich pięciu powtórzeniach dla danej temperatury. Liczbę przepisujemy z terminala; nie jest zapisywana w results.csv. Powtarzalna odpowiedź może być błędna.

**Wnioski (K1, K2, K3 i porównanie):**

## EXP-04 — Structured output — JSON i walidacja

### Komputer K1

| Wariant | Poprawny JSON | Exact match |
|---------|---------------|-------------|
| prompt | 10/10| 100%|
| json-schema | 10/10| 100%|

### Komputer K2

| Wariant | Poprawny JSON | Exact match |
|---------|---------------|-------------|
| prompt | | |
| json-schema | | |

### Komputer K3

| Wariant | Poprawny JSON | Exact match |
|---------|---------------|-------------|
| prompt | | |
| json-schema | | |

**Wnioski (K1, K2, K3 i porównanie):**

## Najtrudniejsze notatki

Które notatki model najczęściej interpretował błędnie i dlaczego?

## Rekomendacja

Który model i prompt wybieramy do projektu — i jakie mamy dowody, że to dobry wybór?
