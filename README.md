# Rozwiązywanie zadań maturalnych z programowania

W tym dokumencie pokażę schematy zadań maturalnych oraz proste sposoby ich rozwiązania - dopracuj ze mną swoje umiejętności!

# SPIS TREŚCI:
* [Polecenie](#polecenie)
* [Technologies](#technologies)
* [More detailed information about modules](#more-detailed-information-about-modules)
* [Application view](#application-view)

## Polecenie

<details>
<summary>Dowiedz się więcej o poleceniu do zadania maturalnego!</summary>
  
**a) Plik tekstowy i dane**

Polecenie zadania odowołuje się zwykle do konkretnego **pliku tekstowego**, w którym to zapisane są **dane**, najczęściej w osobnych wierszach. Przykładowo:

> Zadanie 2. Zapis symboliczny (matura maj 2025) W pliku symbole.txt zapisano 2000 napisów. Każdy z nich jest zapisany w osobnym wierszu i składa się z dokładnie 12 znaków spośród: o, +, *.
---
**b) Zapisanie odpowiedzi**        

Dalej ściśle wytłumaczone jest nam jak można zapisać odpowiedzi do zadań (bez poprawności w tej części, zadanie nie zostanie ocenione!):

> Napisz program (lub kilka programów) znajdujący(-ch) odpowiedzi do podanych zadań. Każdą odpowiedź zapisz w pliku wyniki2.txt i poprzedź ją numerem oznaczającym zadanie.

**c) Plik uproszczony**

Dla ułatwienia sprawdzania poprawności działania kodu, zdającym dany jest również plik przykładowy. Plik ten najczęściej zawiera w sobie z mniej danych.

> Do Twojej dyspozycji jest plik symbole_przyklad.txt, który zawiera 20 wierszy danych spełniających warunki zadania. Odpowiedzi dla pliku symbole_przyklad.txt są podane pod każdym zadaniem. Pamiętaj, że Twój program musi ostatecznie zadziałać na pliku symbole.txt zawierającym 2000 napisów.
</details>

```python
class ReportGenerator:
    def generate(self, data):
        return f"Report: {data}"

class ReportPrinter:
    def print(self, report):
        print(report)
```

Błędne podejście:

```python
class Bird:
    def fly(self):
        return "Flying"

class Penguin(Bird):
    def fly(self):
        raise Exception("Penguins cannot fly")
```

Właściwe podejście:

```python
class Bird:
    def move(self):
        return "Moving"

class FlyingBird(Bird):
    def move(self):
        return "Flying"

class WalkingBird(Bird):
    def move(self):
        return "Walking"
```

Interface Segregation Principle (ISP) – podział interfejsów na mniejsze:

```python
class Scanner:
    def scan(self):
        pass

class Printer:
    def print(self):
        pass

class MultiFunctionDevice(Scanner, Printer):
    def scan(self):
        return "Scanning..."
    def print(self):
        return "Printing..."
```

Dependency Inversion Principle (DIP) – wysokopoziomowe moduły nie zależą od niskopoziomowych:

```python
from abc import ABC, abstractmethod

class Database(ABC):
    @abstractmethod
    def connect(self):
        pass

class MySQLDatabase(Database):
    def connect(self):
        return "Connecting to MySQL"

class Application:
    def __init__(self, database: Database):
        self.database = database
    
    def start(self):
        print(self.database.connect())

# Przykład użycia
mysql_db = MySQLDatabase()
app = Application(mysql_db)
app.start()
```


Wzorce projektowe w automatyce:

**Singleton** – np. zarządzanie połączeniem z urządzeniem

```python
class Singleton:
    _instance = None
    
    def __new__(cls):
        if cls._instance is None:
            cls._instance = super(Singleton, cls).__new__(cls)
        return cls._instance

if __name__ == "__main__":
    # Przykład użycia
    s1 = Singleton()
    s2 = Singleton()
    print(s1 is s2)  # True
```

**Fabryka** – dynamiczne tworzenie obiektów

```python
class Sensor:
    def read(self):
        pass

class TemperatureSensor(Sensor):
    def read(self):
        return "Temperature: 25°C"

class SensorFactory:
    @staticmethod
    def create_sensor(sensor_type):
        if sensor_type == "temperature":
            return TemperatureSensor()
        raise ValueError("Unknown sensor type")
if __name__ == "__main__":
    # Przykład użyciac
    sensor = SensorFactory.create_sensor("temperature")
    print(sensor.read())
```

**Obserwator** – np. monitorowanie wartości czujnika

```python
class Observer:
    def update(self, value):
        pass

class Sensor:
    def __init__(self):
        self.observers = []
        self.value = None

    def add_observer(self, observer):
        self.observers.append(observer)

    def notify_observers(self):
        for observer in self.observers:
            observer.update(self.value)

    def set_value(self, value):
        self.value = value
        self.notify_observers()

class Display(Observer):
    def update(self, value):
        print(f"New sensor value: {value}")

if __name__ == "__main__":        
    # Przykład użycia
    sensor = Sensor()
    display = Display()
    sensor.add_observer(display)
    sensor.set_value(42)
```

## 3. Wprowadzenie do Qt w kontekście automatyki

Qt: Framework dla C++ (GUI, komunikacja, sterowanie urządzeniami)

Signal-Slot Mechanism – podstawowa metoda komunikacji wewnątrz aplikacji

Qt Designer – narzędzie do tworzenia GUI

## 4. Tworzenie aplikacji w Qt (C++)

Struktura aplikacji Qt:

QMainWindow – główne okno aplikacji

QWidget – komponenty interfejsu

QSerialPort – obsługa portów szeregowych

Przykład aplikacji:

```
#include <QApplication>
#include <QPushButton>

int main(int argc, char *argv[]) {
    QApplication app(argc, argv);
    QPushButton button("Kliknij mnie");
    button.show();
    return app.exec();
}
```

## 5. Wykorzystanie Python + Qt (PyQt/PySide)

Zalety: Prostota Pythona + wydajność Qt

Przykładowe zastosowania: Modbus, MQTT, OPC UA

6. Podsumowanie 

## Źródła
[link text](https://www.devs-mentoring.pl/tworzenie-profesjonalnego-readme/)
