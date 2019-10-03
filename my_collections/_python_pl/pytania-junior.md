---
layout: default
title: Python pytania rekrutacyjne
categories: [uderzenie]


---
## Co to jest Python?
https://app.getpocket.com/read/2432887461

Język programowania wysokiego poziomu z rozbudowanym pakietem bibliotek standardowych. Główna ideą jest czytelność i przejrzystość kodu źródłowego.

Wspiera różne pradymaty programowania objektowy, imperatywny.

Open source.


## Czym jest lambda w Pythonie.

Lambda w pytonie to funkcjie anonimowe

```python
x = lambda a : a + 10
print(x(5))

```

Siła labday tkwi gdy jest używana w innej funkcji.

```python
def myfunc(n):
  return lambda a : a * n

mydoubler = myfunc(2)

print(mydoubler(11))

```

## Czym jest pass w Pytonie?

Wypełniacz, nie jest związana z tym żadna operacja.

Tworzenie pustej funkcji.


## Czym jest  *args, **kwargs?

*args przekazuje wszystkie argumenty jako tablicę.

**kwargs przekazuje wszystkie argumenty jako słownik.


## docstring

"""dokumentacja """

## Wbudowanye typy danych

* Niemutowanle
    * string
    * numeryczne
    * tuple
    * logiczny
  
* mutowalne
  * tablice
  * słowniki
  * zbiory

# Różnica pomiędzy tuple i listą

Tuple jest niemutowalna lista jest mutowalna.

#Jakie słowa kluczowe mogą być uzwyane ze słowem kluczowym For

in

# Co może być kluczem w dictionary?

Wszystkie niemutowalne typy. A dokładnie hashowalne

# Co to są zmienne globalne i lokalne

rodzaj zmiennych i dostęp do nich.

# pep 8

Przewodnik jak pisac foramtować kod w pytonie, zęby był jak najbardziej czytelny. 

# W pytonie co to jest slicing
 Przycinanie tablic lub ciągów znaków.

# Co to jest negatywnu index w Pythonie.

Mozemy się dobrac do elementów w tablicy od końca -1 to ostatni element

# Co to jest __init__ ?
Init definiujemy ze dany katalog jest paczką


# jak zamienić dwie wartości w zmiennych 
a,b=b,a

# jak sprawdzic jakie metody można wykonac na objekcie
dir(object)

# moduł python a paczka
Paczka to kolekcja modułow,
Modoł to pojedynczy plik, Paczka to folder w którym znajdują się moduły oraz plik __init__

# jak wyświetlić dokumentacje objektu

help(object)

# dekoratory doczytać

# @classmethod, @staticmethod, @property?