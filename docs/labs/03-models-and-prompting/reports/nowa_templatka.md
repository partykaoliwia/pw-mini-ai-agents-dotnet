# Raport — Laboratorium 03

**Zespół:** MealBrAIn (Patrycja Borkowska, Maria Deperas, Oliwia Partyka) 

**Data:** 22.10.2026

## Środowisko

| Parametr | K1 | K2 | K3 |
|----------|----|----|----|
| Osoba | | | Oliwia |
| CPU | | | AMD Ryzen 7 8840HS |
| GPU | | | AMD Radeon 780M |
| RAM | | | 16 GB |
| Model A | | | phi4-mini |
| Model B | | | llama3.2 |

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
| phi4-mini | 80% | 90% | 70% | 2168 |
| llama3.2 | 80% | 50% | 40% | 1715 |

**Exact match** oznacza odsetek notatek, dla których model poprawnie rozpoznał jednocześnie oba pola: floor i elevator.

**Wnioski (K1, K2, K3 i porównanie):**

K3: Na badanym zbiorze 10 notatek model phi4-mini uzyskał lepsze wyniki niż llama3.2. Oba modele poprawnie rozpoznały piętro w 80% przypadków, ale phi4-mini znacznie lepiej rozpoznawał informację o windzie — 90% wobec 50%. Dzięki temu poprawnie określił oba pola jednocześnie w 70% notatek, a llama3.2 w 40%. Phi4-mini odpowiadał średnio o 453 ms wolniej, jednak większa poprawność uzasadnia wybór tego modelu do dalszych eksperymentów EXP-02–04. Wyniki dotyczą niewielkiego zbioru testowego.

## EXP-02 — Prompting

### Komputer K1

| Wariant | Floor accuracy | Elevator accuracy | Exact match |
|---------|----------------|-------------------|-------------|
| zero-shot | | | |
| one-shot | | | |
| few-shot | | | |

### Komputer K2

| Wariant | Floor accuracy | Elevator accuracy | Exact match |
|---------|----------------|-------------------|-------------|
| zero-shot | | | |
| one-shot | | | |
| few-shot | | | |

### Komputer K3

Model: phi4-mini

| Wariant | Floor accuracy | Elevator accuracy | Exact match |
|---------|----------------|-------------------|-------------|
| zero-shot | 80% | 90% | 70% |
| one-shot | 80% | 80% | 60% |
| few-shot | 80% | 60% | 40% |

**Wnioski (K1, K2, K3 i porównanie):**

K3: W badanym zbiorze najlepszy wynik uzyskał wariant zero-shot — Exact match wyniósł 70%. Dodanie jednego przykładu obniżyło wynik do 60%, a kilku przykładów do 40%. Poprawność rozpoznawania piętra pozostała na poziomie 80%, natomiast poprawność informacji o windzie spadała wraz z dodawaniem przykładów.
Wariant few-shot poprawił interpretację notatki „Mieszkanie 15, domofon 15” — model przestał traktować numer mieszkania jako piętro. Jednocześnie pojawiły się nowe błędy: model pomijał wyraźne informacje o windzie oraz pomylił piętro dostawy z piętrem, do którego dojeżdża winda. Dodanie przykładów nie gwarantuje więc poprawy; znaczenie ma ich dobór.

## EXP-03 — Temperature

### Komputer K1

| Temperature | Exact match | Powtarzalne notatki |
|-------------|-------------|---------------------|
| 0.0 | | |
| 0.5 | | |
| 1.0 | | |

### Komputer K2

| Temperature | Exact match | Powtarzalne notatki |
|-------------|-------------|---------------------|
| 0.0 | | |
| 0.5 | | |
| 1.0 | | |

### Komputer K3

Model: phi4-mini

| Temperature | Exact match | Powtarzalne notatki |
|-------------|-------------|---------------------|
| 0.0 | 70% | 10/10 |
| 0.5 | 68% | 8/10 |
| 1.0 | 64% | 7/10 |

Powtarzalne notatki to notatki z takim samym wynikiem we wszystkich pięciu powtórzeniach dla danej temperatury. Liczbę przepisujemy z terminala; nie jest zapisywana w results.csv. Powtarzalna odpowiedź może być błędna.

**Wnioski (K1, K2, K3 i porównanie):**

K3: W badaniu modelu phi4-mini wzrost temperatury zmniejszał powtarzalność odpowiedzi oraz ich poprawność.Do ekstrakcji danych wybieramy temperaturę 0, która w tym eksperymencie zapewniła najwyższą poprawność i powtarzalność.
Powtarzalność nie gwarantuje jednak poprawności. Przy temperaturze 0 model konsekwentnie uznawał numer mieszkania 15 za piętro, wybierał piętro 2 z niejednoznacznej informacji „drugie lub trzecie” oraz traktował niedziałającą windę jako jej brak.

## EXP-04 — Structured output — JSON i walidacja

### Komputer K1

| Wariant | Poprawny JSON | Exact match |
|---------|---------------|-------------|
| prompt | | |
| json-schema | | |

### Komputer K2

| Wariant | Poprawny JSON | Exact match |
|---------|---------------|-------------|
| prompt | | |
| json-schema | | |

### Komputer K3

Model: phi4-mini

| Wariant | Poprawny JSON | Exact match |
|---------|---------------|-------------|
| prompt | 10/10 | 70% |
| json-schema | 10/10 | 60% |

**Wnioski (K1, K2, K3 i porównanie):**

K3: Oba warianty zwróciły poprawny JSON w 10/10 przypadków, jednak prompt uzyskał wyższy Exact match: 70% wobec 60%. Wariant json-schema był szybszy, ale nie poprawił trafności odpowiedzi. Poprawny format JSON nie gwarantuje poprawności zawartych w nim danych.

## Najtrudniejsze notatki

Które notatki model najczęściej interpretował błędnie i dlaczego?

K3: Najczęściej błędnie interpretowane były trzy notatki. W NOTE-009 („Drugie lub trzecie piętro”) model wybierał piętro 2, zamiast zwrócić `null`, ponieważ nie można jednoznacznie ustalić piętra dostawy. W NOTE-010 („Winda nie działa, dostawa na 5p”) zwracał `elevator: false` lub `null`, myląc niesprawność windy z jej brakiem. Obie notatki zostały błędnie rozpoznane we wszystkich 21 odpowiedziach modelu phi4-mini, licząc warianty i powtórzenia eksperymentów.
Problematyczna była również NOTE-006 („Mieszkanie 15, domofon 15”). Model uznawał numer mieszkania za piętro, mimo że notatka nie zawierała informacji o piętrze. Błąd wystąpił w 20 z 21 odpowiedzi; poprawny wynik uzyskano jedynie w wariancie few-shot.
Rzadziej pojawiały się błędy przy NOTE-007 („4 piętro, winda tylko do 3”), gdzie model w wariancie few-shot pomylił piętro docelowe z zasięgiem windy, oraz przy NOTE-003 („Parter, wejście od podwórza”), gdzie dopowiadał informację o windzie. Główne trudności dotyczyły więc rozróżniania znaczenia liczb, interpretowania niejednoznaczności i niedopowiadania brakujących danych.
