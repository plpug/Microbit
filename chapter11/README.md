# Kierunek

W urządzeniu BBC micro:bit jest wbudowany kompas. Jeżeli kiedykolwiek zbudujesz stacje meteorologiczną użyj tego urządzenia do pracy nad kierunkiem wiatru.

## Kompas

Tak można wskazać kierunek północy:
``markdown
from microbit import *

compass.calibrate()

while True:
    needle = ((15 - compass.heading()) // 30) % 12
    display.show(Image.ALL_CLOCKS[needle])
```


# Ruch

BBC Micro:bit ma wbudowany akcelerometr. Pomiar ruchu wobec trzech osi:

* X - przechylenie od lewej do prawej
* Y - przechylenie od przodu do tyłu
* Z - poruszanie się w góre i w dół

Istnieje metoda każdej osi, która zwraca dodatnią lub ujemną liczbę wskazującą pomiar w mili-g. Gdy odczyt to 0 to jesteśmy na "poziomie" wzdłuż konretnej osi.
Dla przykładu, tutaj mamy bardzo prosty poziom, który używa `get_x` do mierzenia jak poziom urządzenia leży wzdłóż osi X:
```markdown
from microbit import *

while True:
    reading = accelerometer.get_x()
    if reading > 20:
        display.show("R")
    elif reading < -20:
        display.show("L")
    else:
        display.show("-")
```
Jeżeli urządzenie jest płaskie to powinno się wyświetlać. Obróć go w lewo lub w prawo i pokaże L i R odpowiednio. Urządzenie nasze ma reagować na zmiane stale,
więc używamy do tego pętle `while`. Pierwszą rzeczą, która się dzieje w ciale pętli to pomiar wzdłóż osi X, zwany czytaniem. Ponieważ akcelerometr jest wrażliwy
osiągnięty został poziom +/-20 w zasięgu.
To dlatego warunek `if` i `elif` sprawdza dla `>20` i `<-20`. Instrukcja `else` oznacza, że jeśli odczyt wynosi od -20 do 20, to uważamy go za poziom. Dla każdego
z tych warunków używamy wyświetlacza, aby pokazać odpowiedni znak.
Istnieje również metoda `get_y` dla osi Y oraz `get_z` dla osi Z.

# Instrument muzyczny

Jednym z świetnych apsektów MicrPythona BBC micro:bit jest to, jak łatwo pozwala połączyć różne możliwości urządzenia razem. Przykładowo zamieńmy się w instrument
muzyczny. Podłączamy głośnik tak samo jak w rozdziale myzycznym. Użyjmy klipsów krokodylkowych aby przymocować pin 0 i GND do dodatnich i ujemnych wejść w głośniku - nie ma
znaczenia, w jakim kierunku są połączone one do głośnika.

![microbit][microbit]

[microbit]: https://github.com/plpug/Microbit/raw/master/chapter08/img/pin0-gnd.png "microbit"

Co się stanie gdy weźmiemy odczyty z akcelerometra i przy każdym zakręcie odtworzymy dżwięk? Przekonacie się sami:
```markdown
from microbit import *
import music

while True:
    music.pitch(accelerometer.get_y(), 10)
```
Kluczowa linia jest niesłychanie prosta. Zagnieżdzamy odczyty z osi Y jako częstotliwość którą podajemy do metody `music.pitch`. Pozwalamy jej wybrzmiewać jedynie przez 10 milisekund, dlatego bo chcemy by wysokość tonu zmieniała się dynamicznie w czasie gdy urządzenie jest przechylane. Jako, że urządzenie wykonuje nieskończoną pętle `while`, reaguje ono ciągle na zmiany mierzone w osi Y.

To wszystko!

