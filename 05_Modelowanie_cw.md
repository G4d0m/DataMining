---
layout: page
title: 05 -- Analiza danych
---

## Zbiory danych

Odpowiednie przygotowanie danych to $80%$ czasu pracy nad modelowaniem i wydobywaniem informacji z danych.

### Przykładowe zbiory danych z pakietu scikit-learn

W pakiecie [scikit-learn](http://scikit-learn.org/stable/datasets/index.html) znajduje się moduł z prostymi przykładowymi zbiorami danych. Można je łatwo zaimportować w Pythonie za pomocą instrukcji import. Zbiory te to np. Iris, Boston itp. Są to najczęściej wymieniane zbiory w wielu publikacjach, książkach i kursach.

Zbiory te mają postać obiektów (słowników w Pythonie) i oprócz cech, zmiennych docelowych obejmują kompletny opis oraz objaśnienie kontekstu danych.

Zaczniemy od zbioru **IRIS**.

```python
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
%matplotlib inline


from sklearn import datasets
iris = datasets.load_iris()
```

Wszystkie zbiory z pakietu scikit-learn udostępniają następujące pola:

```python
print(iris.DESCR) # opis danych
print(iris.data)  # features, cechy
print(type(iris.data)) # tablica NumPy ndarray
print(iris.data.shape) # rozmiar tablicy zwraca tuple
print(iris.feature_names) # lista nazw dla iris.data
print(iris.target)  # zmienna celu (target)
print(iris.target.dtype) # tablica NumPy
print(iris.target.shape) # rozmiary tablicy celu
```

> **Zadanie** Wczytaj dane Iris 

łówne struktury danych z obiektu _iris_ to _data_ i _target_.

iris.data zawiera **wartości liczbowe** zmiennych (zgodnie z listą *iris.feature_names*) sepal length, sepal width, petal length, petal width uporządkowane w macierz ($150 \times 4$), gdzie 150 to liczba obserwacji a 4 to liczba cech.

iris.target zawiera wektor wartości całkowitoliczbowych reprezentujących odpowiednie klasy (zgodnie z *iris.target_names*).

Zbiór ten często wykorzystuje się ze względu na łatwość wczytania, obsługi i eksploracji do nauczania nadzorowanego, nienadzorowanego czy graficznej prezentacji danych. Modele na tych danych tworzy się bardzo szybko.

```python
colors = []
palette = {0:"red", 1:"green", 2:"blue"}
for c in np.nditer(iris.target):
    colors.append(palette[int(c)])
df = pd.DataFrame(iris.data, columns=iris.feature_names)
sc = pd.plotting.scatter_matrix(df, alpha=0.3, figsize=(10,10), diagonal="hist", color=colors, marker="o", grid="True")
```

Mimo, iż zbiory te są bardzo przydatne w trakcie nauki bardzo często będziesz musiał zajmować się złożonymi i rzeczywistymi danymi. Stąd potrzebna będzie nam wiedza jak wczytywać dane zewnętrzne.

### Publiczne repozytoria [MLdata.io](MLdata)

Witryna [MLdata.io](MLdata) udostępnia publiczne repozytorium danych do uczenia maszynowego z uczelni TU Berlin University [projekt PASCAL](Pascal).

## Dane z witryn internetowych - format LIBSVM


[LIBSVM Data](Libsvm) to witryna, na której znajduje się wiele różnych kolekcji danych. Dane te zapisane są w formacie LIBSVM. Wczytanie danych odbywa się za pośrednictwem połączenia ze stroną:

```python
from urllib.request import urlopen
target_page = 'http://www.csie.ntu.edu.tw/~cjlin/libsvmtools/datasets/binary/a1a'
result = urlopen(target_page)
from sklearn.datasets import load_svmlight_file
X, y = load_svmlight_file(result)
print(X.shape, y.shape)
```

Mając unixowy system operacyjny możesz pobrać dane z repozytorium bezpośrednio na dysk z użyciem narzędzia *wget*.

### Wczytywanie danych bezpośrednio z plików

Jeżeli dane nad którymi chcesz pracować masz już na swoim komputerze w postaci pliku tekstowego np. _*.csv_ to możesz wczytać ten zbiór na dwa sposoby:

1. funkcja *loadtxt* z pakietu NumPy,
2. funkcja *read_csv* z biblioteki Pandas.

Przykładowy plik możesz znaleźć [tutaj](data/bikes.csv).


Umieść plik gdzieś na swoim dysku, tak by łatwo można było go znaleźć.

Ponieważ wszystkie dane zawarte w pliku csv (w naszym przypadku) są typu numerycznego można posłużyć się pierwszą metodą oraz wczytać wszystko do tablicy NumPy. Ale pamiętaj, że wtedy musisz używać metod (funckji) związanych z tą biblioteką. Metoda ta jest najszybsza i zabiera najmniej pamięci.

```python
housing = np.loadtxt('bikes.csv')
```

[MLdata]:http://mldata.io
[Pascal]:https://www.k4all.org/project/25/
[Libsvm]:http://www.csie.ntu.edu.tw/~cjlin/libsvmtools/datasets/