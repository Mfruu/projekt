# Rozwiązywanie zadań maturalnych z programowania

W tym dokumencie pokażę schematy zadań maturalnych oraz proste sposoby ich rozwiązania - dopracuj ze mną swoje umiejętności!

# SPIS TREŚCI:
* [Polecenie](#polecenie)
* [Rozwiązywanie](#rozwiązywanie)
* [Podsumowanie](#podsumowanie)
* [Źródła](#źródła)

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
  
*Pamiętaj! Zadania maturalne najczęściej wykonuje się w Pythonie, ze względu prostszą od innych języków składnię, np. brak średników na końcu linijek (jak w C++) oraz wiele wbudowanych funkcji. Akceptowane są C++, Java oraz Python.*
  
---
By nauczyć się samemu pisać kody, niezleżnie od języka programowania, warto inspirować się pracą innych by "złapać" schemat jakim pisane są programy na maturze. Polecenie:
<br></br>
  
### - 2.1

> Podaj wszystkie takie napisy z pliku symbole.txt, które są palindromami (czytane od przodu i od tyłu są takie same). Wypisz je po jednym w wierszu, w kolejności takiej jak w pliku symbole.txt. <br></br> Odpowiedź dla pliku symbole_przyklad.txt to <br></br> oooo+**+oooo <br></br> (w tym pliku jest jeden palindrom)
---
Po kolei omówię linijki kodu potrzebnego do realizacji tego zadania:
```python
def is_palindrome(file, line):
```
Wbudowana komenda „def” pozwala nam definiować (tworzyć) nowe funkcje, jak w tym przypadku „is_palindrome”, która pozwala nam zwrócić ilość linijek zawierających palindromy z pliku.
```python
with open(file, 'r') as file:
```
„with open (…) as” pozwala nam dostać się do pliku, a „r” w nawiasie oznacza „read” wyznaczając możliwości tej funkcji pośród „a” jako „append” dodający znaki na końcu pliku oraz „w” jako „write” nadpisujący dane z pliku.
```python
end = len(line)-2
```
Tu użyta jest wbudowana funkcja „len()” zwracająca długość (length) wersu oraz .
```python
while start < end:
```
Pętla „while” polega na wykonywaniu wyznaczonej komendy do czasu spełnienia warunku.
```python
if line[start] != line[end]:
```
Pętla „if” działaja tylko pod danym warunkiem.
```python
for line in open(file):
```
„for line in open(…)” jest kolejną pętlą. Ta pozwala na wykonanie podanego kroku po jeden raz na każdą linijkę pliku. 
```python
print(line)
```
Funkcja „print” wyświetla (drukuje) wskazane dane na konsoli.
```python
while start < end:
```
Pętla „while” polega na wykonywaniu wyznaczonej komendy do czasu spełnienia warunku.

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

---

W dalszych etapach zadania 2 użyte dodatkowo zostały następujące komendy:
```python
for i in range(row-1, row+2):
        for j in range(column-1, column+2):
```
„For i in range” to następna pętla tym razem korzystająca z zmiennej pomocniczej „i” oraz później „j” - powstaje tutaj pętla w pętli.

```phyton
line = line.strip()
```
Funkcja „strip()” pozwala na wyczyszczenie pliku ze znaków białych.

---

### Po poznaniu wszystkich tych funkcji jesteśmy w stanie już dalej samodzielnie robić zadania:
### - 2.2

> Zadanie 2.2. (0–4) <br></br>W pliku symbole.txt szukamy „kwadratów” złożonych z dziewięciu sąsiadujących identycznych symboli: <br></br> + + + o o o * * * <br></br> + + + o o o * * * <br></br> + + + o o o * * * <br></br> Podaj, ile takich kwadratów występuje w pliku symbole.txt. Jeżeli w pliku występuje jeden taki kwadrat, podaj numer wiersza i numer pozycji w wierszu (licząc od 1) jego środkowego pola. Jeżeli jest więcej takich kwadratów, podaj numer wiersza i numer pozycji w wierszu dla środkowego pola każdego z nich. <br></br> Przykład: <br></br> Poniżej podano 6 wierszy przykładowych danych (po 12 znaków w każdym wierszu): <br></br> 1. + * * + o * o + + * o + <br></br> 2. + + + o o o o * o * * * <br></br> 3. + o * o o o o * * + + + <br></br> 4.* + * o o o o o o + + + <br></br> 5. o * * o + + + o + + + + <br></br> 6. o o o o + + * * + * + o <br></br>
Mamy tutaj trzy kwadraty złożone z 9 identycznych symboli: pierwszy ma środek w wierszu <br></br> 3 na pozycji 5, drugi – w wierszu 3 na pozycji 6, a trzeci – w wierszu 4 na pozycji 11. <br></br> Odpowiedź dla pliku symbole_przyklad.txt to <br></br> 1 6 3 <br></br> (jeden kwadrat, który ma środkowe pole w wierszu 6, na pozycji 3).
<br></br>
```python
def is_square(matrix, row, column):
    center = matrix[row][column]

    for i in range(row-1, row+2):
        for j in range(column-1, column+2):
            if matrix[i][j] != center:
                return False
    return True


with open('symbole.txt', 'r') as file:
    matrix = []
    for line in file:
        matrix.append(line.strip())

square_counter = 0
squares = []
for row in range(1, len(matrix)-1):
    for column in range(1, len(matrix[row])-1):
        if is_square(matrix, row, column):
            square_counter += 1
            squares.append([row+1, column+1])

for square in squares:
    row = square[0]
    column = square[1]
    print(row, column)
```

---

### - 2.3
```python
from converting import convert_to_decimal

with open('symbole.txt', 'r') as file:
    max_number = 0
    max_line = ""

    for line in file:
        line = line.strip()
        number = convert_to_decimal(line)
        if number > max_number:
            max_number = number
            max_line = line

    print(max_number)
    print(max_line)
```

---

### - 2.4
```python
from converting import *

with open('symbole.txt', 'r') as file:
    sum = 0
    for line in file:
        number = convert_to_decimal(line.strip())
        sum += number

    trinary_sum = convert_to_trinary(sum)

    print(trinary_sum)
    print(sum)
```

---

### - 2.5
```phyton
def convert_to_decimal(line):
    trinary = ""
    for char in line:
        if char == 'o':
            trinary += '0'
        elif char == '+':
            trinary += '1'
        elif char == '*':
            trinary += '2'

    decimal = 0
    exponent = 1
    for number in reversed(trinary):
        decimal += int(number) * exponent
        exponent *= 3

    return decimal


def convert_to_trinary(number):
    if number == 0:
        return 'o'
    trinary_symbols = ''
    while number > 0:
        rest = number % 3
        if rest == 0:
            trinary_symbols = 'o' + trinary_symbols
        elif rest == 1:
            trinary_symbols = '+' + trinary_symbols
        elif rest == 2:
            trinary_symbols = '*' + trinary_symbols
        number //= 3
    return trinary_symbols
```

Dodatkowo w różnych poleceniach możemy spotkać znaki takie jak:
- == - które sprawdza czy wartości są równe sobie,
- != - sprawdza czy wartości są różne od siebie,
- += - dodający konkretną podaną wartość,
- -= - odejmujący podaną wartość,
- *= - które najłatwiej wytłumaczyć jako (c = a -> c = ca),
- znaki większości i mniejszości,
- % - modulo, wyznaczające resztę z dzielenia,
- //= - dzielenie całkowite.
  
</details>

6. Podsumowanie

## Źródła
[Spis treści - markdown](https://www.devs-mentoring.pl/tworzenie-profesjonalnego-readme/)

[Linki - mark down](https://www.ibm.com/docs/pl/watsonx/saas?topic=projects-markdown-cheatsheet)
