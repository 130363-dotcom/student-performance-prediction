# student-performance-prediction
Projekt z Programowania 2 dotyczący przewidywania wyników edukacyjnych z wykorzystaniem modeli uczenia maszynowego.
# Student Performance Prediction

## Cel projektu

Celem projektu jest przewidywanie wartości `Performance Index` na podstawie wybranych czynników związanych z nauką i codziennym funkcjonowaniem ucznia.

Analizowane zmienne obejmują:

* liczbę godzin nauki,
* wcześniejsze wyniki,
* udział w aktywnościach pozalekcyjnych,
* liczbę godzin snu,
* liczbę przećwiczonych przykładowych arkuszy.

Jest to zadanie regresji, ponieważ zmienna docelowa `Performance Index` ma charakter liczbowy.

## Zbiór danych

W projekcie wykorzystano zbiór danych `Student Performance` pobrany z platformy Kaggle.

Początkowo zbiór zawierał:

* 10 000 obserwacji,
* 6 kolumn.

W trakcie przygotowania danych wykryto i usunięto 127 zduplikowanych wierszy. Po oczyszczeniu zbiór zawierał 9873 obserwacje.

W danych nie występowały braki wartości.

Zmienna `Extracurricular Activities`, zawierająca początkowo wartości `Yes` i `No`, została zakodowana liczbowo:

* `Yes` → `1`,
* `No` → `0`.

## Analiza danych

W ramach analizy eksploracyjnej wykonano:

* sprawdzenie struktury i typów danych,
* analizę brakujących wartości,
* sprawdzenie i usunięcie duplikatów,
* wizualizację zależności między cechami a `Performance Index`,
* analizę korelacji,
* analizę ważności cech.

Najsilniejszą korelację z `Performance Index` miała zmienna `Previous Scores`. Drugą istotną zmienną była liczba godzin nauki, czyli `Hours Studied`.

## Wykorzystane modele

W projekcie porównano trzy modele regresyjne:

1. Linear Regression
2. Decision Tree Regressor
3. Random Forest Regressor

Dodatkowo dla modelu Random Forest zastosowano `GridSearchCV`, aby automatycznie dobrać najlepsze hiperparametry.

## Ocena modeli

Modele oceniono za pomocą metryki RMSE. Im niższa wartość RMSE, tym lepsza jakość predykcji.

| Model                         |       RMSE |
| ----------------------------- | ---------: |
| Linear Regression             | około 2,08 |
| Random Forest po GridSearchCV | około 2,27 |
| Random Forest Regressor       | około 2,37 |
| Decision Tree Regressor       | około 3,03 |

Najlepszy wynik uzyskała regresja liniowa.

Dla regresji liniowej współczynnik R² wyniósł około 0,988, co oznacza, że model wyjaśnia około 98,8% zróżnicowania wartości `Performance Index`.

## Tuning hiperparametrów

Do strojenia modelu Random Forest wykorzystano `GridSearchCV` z pięciokrotną walidacją krzyżową.

Najlepsze znalezione parametry:

```python
{
    "max_depth": 10,
    "min_samples_leaf": 2,
    "min_samples_split": 5,
    "n_estimators": 200
}
```

Po tuningu RMSE modelu Random Forest poprawiło się z około 2,37 do około 2,27.

## Wnioski

Najlepszym modelem okazała się regresja liniowa. Sugeruje to, że zależności w analizowanym zbiorze danych są w dużej mierze liniowe.

Największe znaczenie dla przewidywania wyników miały wcześniejsze osiągnięcia oraz liczba godzin nauki. Pozostałe zmienne miały znacznie mniejszy wpływ na predykcje modelu Random Forest.

Wyniki dotyczą wyłącznie analizowanego zbioru danych i nie pozwalają na formułowanie wniosków przyczynowo-skutkowych.

## Technologie

W projekcie wykorzystano:

* Python
* pandas
* NumPy
* matplotlib
* seaborn
* scikit-learn
* Google Colab

## Zawartość repozytorium

* `projekt_student_performance.ipynb` - notebook z analizą i modelami,
* `Student_Performance.csv` - zbiór danych,
* `README.md` - opis projektu.
