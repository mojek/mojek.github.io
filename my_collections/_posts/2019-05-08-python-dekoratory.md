---
layout: post
title: Python dekoratory
categories: [python]
---


* Jest to funkcja, które bierzę innę funkcję
* Rozszerza jej funkcjonalność
* Robi to bez wyraźnej modyfikacji funkcji.

## 1 Funkcje

### 1.1 Przykłady funkcji
Prosty przykład definiowania funkcji.

```python
def my_func(arg):
    """docstring"""
    my_var = arg + 5
    return my_var

my_func(3)
```
Funkcję w pythone to typ pierwszoklasowy ([wiki](https://pl.wikipedia.org/wiki/Typ_pierwszoklasowy)) first class object


### 1.2 First class object
* może być przechowywany w zmiennej i strukturach danych,
* może być przekazywany jako parametr do procedury/funkcji,
* może być zwracany przez procedury/funkcje,
* może być tworzony na bieżąco,
* posiada tożsamość (niezależną od nazwy),

### 1.3 Inner functions
```python
def parent():
    """docstring"""
    my_var = arg + 5
    def first_child():
        print("print first childe")
    def second_child():
        print("print first childe")    
    

parent()
```
### 1.4 Zwracanie funkcji z funkcji
```python
def parent(num):
    def first_child():
        return "Hi, I am Emma"

    def second_child():
        return "Call me Liam"

    if num == 1:
        return first_child
    else:
        return second_child

>>> first = parent(1)
>>> second = parent(2)

>>> first
<function parent.<locals>.first_child at 0x7f599f1e2e18>

>>> second
<function parent.<locals>.second_child at 0x7f599dad5268>


>>> first()
'Hi, I am Emma'

>>> second()
'Call me Liam'
```

## 2 Dekoratory
 ```python
 def my_decorator(func):
    def wrapper():
        print("Something is happening before the function is called.")
        func()
        print("Something is happening after the function is called.")
    return wrapper

def say_whee():
    print("Whee!")

say_whee = my_decorator(say_whee)
```

```console
>>> say_whee()
Something is happening before the function is called.
Whee!
Something is happening after the function is called.
 ```

## 3 Przykłady
