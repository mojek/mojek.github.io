---
layout: default
title: uczenia maszynowe
categories: [uderzenie]


---
# Notatki Uczenie maszynowe  z użyciem Scikit-Learn TensorFlowe

## Rodział 1

1. Definicja uczenia maszynowego  
   Uczenie maszynowe - dziedzina nauki programowania komputerów w sposób umożliwijajy im uczenie się z danych

2. Cztery rodzaje problemów z których rozwiązaniem najlepiej radzi sobie proces uczenia maszynowego  
   * długa lista regół ifów.
   * złożone problemy których nie da się rozwiązać tradycyjnymi metodami
   * zmienne środowiska - algorytmy potrafią się dostosować do nowych danych
   * pomaga analizować skomplikowane zagadanienia i olbrzymie ilości danych

3. Czym jest oznakowany zbiór danych uczących?  
   Dane mają dołączone rozwiązanie problemu, są oznaczone np. wiadomość jest oznaczona jako spam.

4. Jakie są dwa najczęstsze zastosowania uczenia nadzorowanego?  
   * Klasyfikacja - przypisanie danych do jakiejś grupy.
   * Regresja  - dane są oznaczone wartością numeryczną, która będzie będzie prognozowana dla nowych danych.

5. Wymień cztery najpowszechniejsze zastosowania uczenia nienadzorowanego.  
   * Klastrowanie - analiza skupień określanie grup podobnych użytkowników.
   * Wizualizacja danych
   * Redukcja wymiarowości - celem jest uproszczenie danych bez utraty nadmiernej ilości informacji. Mozna to osiągnąć przez scalenie kilku skorelowanych ze sobą cech. **Wydobywanie cech (ang. feature extraction)**
   * Wykrywanie anomalii (ang. anomaly detection) - np. nietypowe transakcje wykorzystujące kartę kredytową,


6. Jakiego rodzaju algorytmu uczenia maszynowego użyłabyś/użyłbyś w robocie przeznaczonym
do poruszania się po nieznanym terenie?  
   * Uczenie przez wzmacnianie (ang. reinforcement learning)

7. Jakiego rodzaju algorytmu uczenia maszynowego użyłabyś/użyłbyś do rozdzielenia klientów
na kilka różnych grup?  
    * Hierarchiczna analiza skupień
  
8. Czy problem wykrywania spamu stanowi część mechanizmu uczenia nadzorowanego lub
nienadzorowanego?  
   * Nadzorowanego

9. Czym jest system uczenia przyrostowego? online learning 
   System jest trenowany na bieżąco poprzez sekwencyjne dostarczanie danych. System uczy się na bieżąco przy użyciu nowo pojawiających się danych.
    
10. Czym jest uczenie pozakorowe? (ang. out-of-core learning)
    Algroytmy uczenia przyrostowego potrafiące uczyć dane nie mieszczące się w pamięci urządzenia. Wczytania części danych i trenowanie systemu za ich pomocą, po czym cały proces zostanie powtórzony dla całego zbioru danych uczących.???

11. W jakim algorytmie uczenia maszynowego jest wymagana miara podobieństwa do uzyskiwania
prognoz?
Uczenie z modelu

12. Wyjaśnij różnicę pomiędzy parametrem modelu a hiperparametrem algorytmu uczącego.
Parametry algorytmu uczącego, są niezmienne przez cały proces uczenia się

13. Czego poszukują algorytmy uczenia z modelu? Z jakiej strategii najczęściej korzystają? W jaki sposób przeprowadzają prognozy?
