---
layout: page
title: 04 -- A jednak statystyka ?
mathjax: true
---


# Analiza danych

## GIGO (ang. _Garbage In, Garbage Out_)

> Wyniki przetwarzania błędnych danych zawsze będą błędne niezależnie od poprawności procedury ich przetwarzania.

Algorytmy eksploracyjne są bardzo czułe na błędne dane źródłowe. Ponieważ nie istnieje uniwersalne narzędzie do wykrywania błędnych danych, właściwe przygotowanie danych jest warunkiem koniecznym powodzenia całego projektu. 

Zawsze na początku:

1. Oceń przydatność danych w rozwiązaniu postawionego problemu (tutaj jeszcze nie modyfikuj danych)
    - jakie informacje masz w danych ?
    - Czy dane opisujące zależności między zmiennymi objaśniającymi a objaśninymi są kompletne ?
    - Czy te informacje pozwolą uzyskać odpowiedź na postawione pytanie ?
    - Jakich problemów możesz się spodziewać podczas tworzenia modeli ?

2. Wykrte w danych błędy muszą zostać usunięte tak by dopasować ich jakość do technicznych wymogów używanych modeli.

3. Dostosowanie danych do postawionego problemu - wprowadzenie do danych nowych informacji.

## Dane zawsze są błędne

Pomiar oznacza zazwyczaj dysponowanie jakimś urządzeniem pomiarowym. Narzędziem tym może być np. waga (pomiar ciężaru) jak i ankieta (pomiar stopnia zadowolenia studentów z wykładowców). Błędy pomiaru mogą być generowane przez: ograniczoną dokładność przyrządu, złe wykalibrowanie, niewłaściwa skala itp.

Ogólnie wyróżnia się dwa rodzaje błędów pomiaru:

1. _Błąd systematyczny_ (ang. _Bias_) - zawyża bądź zaniża wszystkie otrzymane wyniki. Mały wpływ na Algorytmy eksploracyjne.

2. _Błąd przypadkowy_ (ang. _Noise_) - przypadkowe zmiany otrzymywanych wyników. Duży wpływ na Algorytmy eksploracyjne. Mogą prowadzić do błędnych wniosków i znalezionych zależności.

## Jaką postać danych potrzebujemy

Aby algorytmy eksploracyjne mogły przetworzyć dane musisz sprowadzić je do postaci tabelarycznej. Kolumny takiej tabeli przedstawiają cechy analizowanych obiektów. Nazywane są często atrybutami bądź zmiennymi. Np . kolumna _Income_ zawiera informacje o zarobkach.

Zbiór atrybutów jednego obiektu nazywamy **przypadkiem**. Np. zmierzony w danym czasie zbiór wartości wszystkich atrybutów klienta.

Przykładowe dane w postaci tabelarycznej:

![TablicaDanych](img/rys4.png)

# Podział atrybutów, typy danych

Ze względu na rodzaj mierzonej wielkości atrybuty dzielimy najczęściej na **ciągłe** lub **dyskretne**. Lepszym podziałem danych jest pogrupowanie ich w następujące typy danych:

![TypyDanych](img/rys5.png)

1. **Cechy jakościowe** (_niemierzalne_, _kategoryjne_) to takie, których nie można jednoznacznie scharakteryzować za pomocą lich (czyli mie da się ich zmierzyć). Np. płeć, etykiety, kategorie produktów,grupa krwi, kolor itp.

![jakosc](img/rys6.png)

- Nie można policzyć wartości średniej, min, max.
- Nie można uporządkować wartośći.

2. **Cechy porządkowe**  umożliwiają porządkowanie wszystkich elementów zbioru wyników. Cechy takie najlepiej określa się przymiotnikami i ich stopniowaniem. Np. wzrost (niski, średni, wysoki), wykształcenie (podstawowe, średnie, wyższe), ocena filmu itp.

3. **Cechy ilościowe** (_mierzalne_) dadzą się wyrazić za pomocą jednostek miary w pewnej skali. Np. Wzrost (w cm), waga (w kg), wiek (w latach) itp.

![Ilosc](img/rys7.png)

- Można z nich policzyć wartość średniej, min, max.
- Można uporządkować wartości.

## Ważne

> Wynikiem oceny atrybutów powinno być uzyskanie odpowiedzi na następujące pytania:

1. Czy zakres wartości atrybutów obejmuje wszystkie przypadki będące przedmiotem analizy?
2. Czy częstotliwości występowania poszczególnych wartości atrybutów są zgodne z doświadczeniem i intuicją eksperta dziedzinowego?

