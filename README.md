# Rozwiązywanie zadań maturalnych z programowania

W tym dokumencie pokażę schematy zadań maturalnych oraz proste sposoby ich rozwiązania - dopracuj ze mną swoje umiejętności!

# SPIS TREŚCI:
* [Polecenie](#polecenie)
* [Rozwiązywanie](#rozwiązywanie)
* [General info](#general-info)
* [Application view](#application-view)

## Polecenie

<details>
  
<summary>Dowiedz się więcej o POLECENIU do zadania maturalnego!</summary>
  
### **a) Plik tekstowy i dane**

Polecenie zadania odowołuje się zwykle do konkretnego **pliku tekstowego**, w którym to zapisane są **dane**, najczęściej w osobnych wierszach. Przykładowo:
<br></br>
> Zadanie 2. Zapis symboliczny (matura maj 2025) W pliku symbole.txt zapisano 2000 napisów. Każdy z nich jest zapisany w osobnym wierszu i składa się z dokładnie 12 znaków spośród: o, +, *.

<br></br>
### **b) Zapisanie odpowiedzi**        

Dalej ściśle wytłumaczone jest nam jak można zapisać odpowiedzi do zadań (bez poprawności w tej części, zadanie nie zostanie ocenione!):
<br></br>
> Napisz program (lub kilka programów) znajdujący(-ch) odpowiedzi do podanych zadań. Każdą odpowiedź zapisz w pliku wyniki2.txt i poprzedź ją numerem oznaczającym zadanie.

<br></br>
### **c) Plik uproszczony**

Dla ułatwienia sprawdzania poprawności działania kodu, zdającym dany jest również plik przykładowy. Plik ten najczęściej zawiera w sobie z mniej danych.
<br></br>
> Do Twojej dyspozycji jest plik symbole_przyklad.txt, który zawiera 20 wierszy danych spełniających warunki zadania. Odpowiedzi dla pliku symbole_przyklad.txt są podane pod każdym zadaniem. Pamiętaj, że Twój program musi ostatecznie zadziałać na pliku symbole.txt zawierającym 2000 napisów.

<br></br>
</details>

## Rozwiązywanie
<details>
<summary>Dowiedz się więcej o ROZWIĄZYWANIU zadania maturalnego!</summary>
<br></br>
By nauczyć się samemu pisać kody, niezleżnie od języka programowania, warto inspirować się pracą innych by "złapać" schemat jakim pisane są programy na maturze. Zatem dla polecenia:
<br></br>
  
- Zadanie 2.1.
> Podaj wszystkie takie napisy z pliku symbole.txt, które są palindromami (czytane od przodu i od tyłu są takie same). Wypisz je po jednym w wierszu, w kolejności takiej jak w pliku symbole.txt. <br></br> Odpowiedź dla pliku symbole_przyklad.txt to <br></br> oooo+**+oooo <br></br> (w tym pliku jest jeden palindrom)

Tworzymy następujący kod:
```python
def is_palindrome(file, line):
    with open(file, 'r') as file:
        start = 0
        end = len(line)-2
        while start < end:
            if line[start] != line[end]:
                return False
            else:
                start += 1
                end -= 1
        return True


file = 'symbole.txt'

for line in open(file):
    if is_palindrome(file, line) == True:
        print(line)
```
</details>

## Komendy
Do rozwiązania zadań maturalnych potrzebna jest znajomość wielu komend, a 



6. Podsumowanie 

## Źródła
[Spis treści - markdown](https://www.devs-mentoring.pl/tworzenie-profesjonalnego-readme/)

[Linki - mark down](https://www.ibm.com/docs/pl/watsonx/saas?topic=projects-markdown-cheatsheet)
