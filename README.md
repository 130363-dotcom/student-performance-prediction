# Student Performance Prediction

## Opis projektu

Celem projektu jest przewidywanie wartości `Performance Index` uczniów na podstawie wybranych cech związanych z nauką i stylem życia. Projekt dotyczy zadania regresji, ponieważ zmienna docelowa ma charakter liczbowy.

W analizie wykorzystano dataset `Student_Performance.csv`, który zawiera informacje takie jak liczba godzin nauki, wcześniejsze wyniki, długość snu, udział w aktywnościach pozalekcyjnych oraz liczba rozwiązanych arkuszy.

## Zmienna docelowa

Zmienną przewidywaną jest:

- `Performance Index`

## Wykorzystane cechy

W modelowaniu wykorzystano następujące zmienne:

- `Hours Studied`
- `Previous Scores`
- `Extracurricular Activities`
- `Sleep Hours`
- `Sample Question Papers Practiced`

## Etapy projektu

Projekt obejmuje:

1. Wczytanie danych.
2. Wstępną eksplorację danych.
3. Sprawdzenie braków danych.
4. Usunięcie duplikatów.
5. Zakodowanie zmiennej tekstowej `Extracurricular Activities`.
6. Analizę korelacji między zmiennymi.
7. Wizualizacje danych.
8. Podział danych na zbiór treningowy i testowy.
9. Standaryzację danych za pomocą `StandardScaler` w `Pipeline`.
10. Porównanie modeli za pomocą walidacji krzyżowej na zbiorze treningowym.
11. Tuning hiperparametrów modelu Random Forest za pomocą `GridSearchCV`.
12. Końcową ocenę najlepszego modelu na zbiorze testowym.

## Modele

W projekcie porównano trzy modele regresyjne:

- Linear Regression
- Decision Tree Regressor
- Random Forest Regressor

Dodatkowo dla modelu Random Forest przeprowadzono tuning hiperparametrów z użyciem `GridSearchCV`.

## Metodologia oceny

Modele zostały porównane za pomocą walidacji krzyżowej na zbiorze treningowym. Zbiór testowy nie był wykorzystywany podczas wyboru modelu. Został użyty dopiero na końcu do ostatecznej oceny najlepszego modelu.

Takie podejście pozwala uniknąć sytuacji, w której model jest wybierany na podstawie wyników ze zbioru testowego.

## Wyniki

Najlepszym modelem na podstawie wyników walidacji krzyżowej okazała się regresja liniowa.

Końcowe wyniki na zbiorze testowym:

- RMSE: około 2.08
- R²: około 0.988

Oznacza to, że przeciętny błąd predykcji modelu wynosi około 2 punkty w skali `Performance Index`, a model wyjaśnia bardzo dużą część zróżnicowania wyników.

## Wnioski

Najsilniej związane z wynikiem `Performance Index` okazały się zmienne `Previous Scores` oraz `Hours Studied`. Oznacza to, że wcześniejsze wyniki ucznia oraz liczba godzin nauki mają największe znaczenie dla przewidywania końcowego wyniku.

Pomimo przeprowadzenia tuningu Random Forest, najlepszy wynik uzyskała regresja liniowa. Może to sugerować, że zależności w danych mają w dużej mierze charakter liniowy.

## Wykorzystane biblioteki

- pandas
- numpy
- matplotlib
- seaborn
- scikit-learn

## Autor

Projekt wykonany w ramach zajęć z Programowania 2.
