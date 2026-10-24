# Raport — Laboratorium 03

**Zespół:** MealBrAIn (Patrycja Borkowska, Maria Deperas, Oliwia Partyka) 
**Data:** 22.10.2026

## Środowisko

| Parametr | K1 | K2 | K3 |
|----------|----|----|----|
| Osoba | | | |
| Wersja Ollama | | | |
| CPU | | | |
| GPU | | | |
| RAM | | | |
| Model A (pełna nazwa i wariant) | | | |
| Model B (pełna nazwa i wariant) | | | |

Model A i model B oznaczają dwa modele badane na danym komputerze, zgodnie z tabelą powyżej.

Wszystkie komputery korzystają z tego samego zbioru testowego, promptów i ustawień eksperymentów. Czasy odpowiedzi porównujemy przede wszystkim w obrębie jednego komputera; porównanie między komputerami uwzględnia różnice sprzętowe.

| Zbiór danych | Liczba notatek |
|-------------|----------------|
| Dostępne notatki rzeczywiste (notes.csv) | 172 |
| Zbiór testowy używany w eksperymentach (examples.csv) | 10 |

## EXP-00 — Sposób oceny wyników

Jak oceniamy poprawność odpowiedzi modelu? Jakie metryki przyjmujemy i dlaczego?

| Metryka | Definicja |
|---------|-----------|
| | |

## EXP-01 — Porównanie modeli

### Komputer K1

| Model | Floor accuracy | Elevator accuracy | Exact match | Średni czas [ms] |
|-------|----------------|-------------------|-------------|------------------|
| model A | | | | |
| model B | | | | |

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

| Model | Wariant | Floor accuracy | Elevator accuracy | Exact match |
|-------|---------|----------------|-------------------|-------------|
| model A | zero-shot | | | |
| model A | one-shot | | | |
| model A | few-shot | | | |
| model B | zero-shot | | | |
| model B | one-shot | | | |
| model B | few-shot | | | |

### Komputer K2

| Model | Wariant | Floor accuracy | Elevator accuracy | Exact match |
|-------|---------|----------------|-------------------|-------------|
| model A | zero-shot | | | |
| model A | one-shot | | | |
| model A | few-shot | | | |
| model B | zero-shot | | | |
| model B | one-shot | | | |
| model B | few-shot | | | |

### Komputer K3

| Model | Wariant | Floor accuracy | Elevator accuracy | Exact match |
|-------|---------|----------------|-------------------|-------------|
| model A | zero-shot | | | |
| model A | one-shot | | | |
| model A | few-shot | | | |
| model B | zero-shot | | | |
| model B | one-shot | | | |
| model B | few-shot | | | |

**Wnioski (K1, K2, K3 i porównanie):**

## EXP-03 — Temperature

### Komputer K1

| Model | Temperature | Exact match | Powtarzalne notatki [x/10] |
|-------|-------------|-------------|---------------------------|
| model A | 0.0 | | |
| model A | 0.5 | | |
| model A | 1.0 | | |
| model B | 0.0 | | |
| model B | 0.5 | | |
| model B | 1.0 | | |

### Komputer K2

| Model | Temperature | Exact match | Powtarzalne notatki [x/10] |
|-------|-------------|-------------|---------------------------|
| model A | 0.0 | | |
| model A | 0.5 | | |
| model A | 1.0 | | |
| model B | 0.0 | | |
| model B | 0.5 | | |
| model B | 1.0 | | |

### Komputer K3

| Model | Temperature | Exact match | Powtarzalne notatki [x/10] |
|-------|-------------|-------------|---------------------------|
| model A | 0.0 | | |
| model A | 0.5 | | |
| model A | 1.0 | | |
| model B | 0.0 | | |
| model B | 0.5 | | |
| model B | 1.0 | | |

Powtarzalne notatki to notatki z takim samym wynikiem we wszystkich pięciu powtórzeniach dla danej temperatury. Liczbę przepisujemy z terminala; nie jest zapisywana w results.csv. Powtarzalna odpowiedź może być błędna.

**Wnioski (K1, K2, K3 i porównanie):**

## EXP-04 — Structured output — JSON i walidacja

### Komputer K1

| Model | Wariant | Poprawny JSON [x/10] | Exact match |
|-------|---------|---------------------|-------------|
| model A | prompt | | |
| model A | json-schema | | |
| model B | prompt | | |
| model B | json-schema | | |

### Komputer K2

| Model | Wariant | Poprawny JSON [x/10] | Exact match |
|-------|---------|---------------------|-------------|
| model A | prompt | | |
| model A | json-schema | | |
| model B | prompt | | |
| model B | json-schema | | |

### Komputer K3

| Model | Wariant | Poprawny JSON [x/10] | Exact match |
|-------|---------|---------------------|-------------|
| model A | prompt | | |
| model A | json-schema | | |
| model B | prompt | | |
| model B | json-schema | | |

**Wnioski (K1, K2, K3 i porównanie):**

## Najtrudniejsze notatki

Które notatki model najczęściej interpretował błędnie i dlaczego?

## Rekomendacja

Który model i prompt wybieramy do projektu — i jakie mamy dowody, że to dobry wybór?
