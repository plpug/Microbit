# Wejście/Wyjście

Na dole płytki BBC micro:bit znajdują się metalowe paski, dzięki
którym urządzenie wygląda jakby miało zęby.
Są one pinami wejścia/wyjścia (z angielskiego - I/O pins).

Niektóre z pinów są większe niż pozostłe, dlatego też możliwe jest
podpięcie pod nie "krokodylków".
Piny te oznaczone są jako 0, 1, 2, 3V i GND (komputery zawsze
zaczynają liczenie od zera).
Jeśli podłączysz do urządzenia dodatkową płytkę krawędziową, możliwe
będzie podpięcie się
do pozostałych (mniejszych) pinów.

Każdy pin urządzenia BBC micro:bit reprezentowany jest obiektem
nazywanym pinN, gdzie N jest numerem pina.
Przykładowo, jeśli chcesz zrobić coś używając pinu oznaczonego 0
(zerem), użyj obiektu nazwanego jako pin0.

Proste!

Te obiekty mają wiele powiązanych z nimi metod, w zależności od
możliwości danego pina.

## Łaskotliwy Python

Najprostrzym przykładem użycia pinów jako wejść jest sprawdzanie czy
są one dotykane.
Tak więc możesz połaskotać płytkę by zaśmiała się w ten sposób:

```python
from microbit import *

while True:
    if pin0.is_touched():
        display.show(Image.HAPPY)
    else:
        display.show(Image.SAD)
```

Jedną ręką przytrzymaj płytkę za pin GND. Następnie, drugą rękął
dotknij (lub połaskocz) pin 0.
Powinieneś zobaczyć że wyświetlana mina zmienia się z nieszczęśliwej na radosną.

To jest forma bardzo prostego sprawdzania wejścia, ale zabawa zaczyna
się dopiero przy podłączaniu
do płytki innych układów z użyciem pinów.

## Brzdęk i Brzdąk

Najprostrzym elementem jakie możemy podpiąć pod płytkę jest piezo
elektryczny brzęczyk.  Użyjemy go jako wyjście.

Ten malutki element wytwarza wysokiej częstotliwości pisk, po
podłączeniu do układu.
By podpiąć go pod twoją płytkę BBC micro:bit powinieneś podpiąć
krokodylki do pinów 0 i GND (jak pokazane poniżej).

![microbit][microbit]

[microbit]: https://github.com/plpug/Microbit/raw/master/chapter08/img/pin0-gnd.png "microbit"

Przewód od pina 0 powinien być podpięty do oznaczonego plusem złącza
brzęczyka, a przewód od GND - do złącza oznaczonego minusem.

Poniższy program spowoduje że brzęczyk wydobędzie z siebie dźwięk:

```python
from microbit import *

pin0.write_digital(1)
```

To jest zabawne przez około 5 sekund, po których chcesz by ten
przeraźliwy pisk zakończył się.
Polepszmy nasz przykład by wydał inny dźwięk:

```python
from microbit import *

while True:
    pin0.write_digital(1)
    sleep(20)
    pin0.write_digital(0)
    sleep(480)

```

Możesz domyślić się jak ten skrypt działa? Pamiętaj że "1" oznacza
"włączony" a "0" to "wyłączony" w cyfrowym świecie.

Płytka pworadzona jest w tryb nieskończonego zapętlenia (wykonywania w
kółko tych samych operacji).
Zaczyna od niezwłocznego ustawienia pinu 0 w stan włączony.  Wymusza
to na brzęczyku jego brzęczenie.
W trakcie gdy brzęczyk wydaje dźwięk, płytka "zasypia" na 20
milisekund, po czym ustawia pin 0 w stan
wyłączony (wyłączając brzęczyk). To daje efekt krótkiego pisknięcia.
Następnie płytka ponownie zasypia
na 480 mili sekund, zanim ponownie rozpocznie instrukcje od początku
pętli. Oznacza to że uzyskamy dwa pisknięcia
w każdej sekundzie (jedno co 500 mili sekund - czyli co pół sekundy).

W ten sposób zrobiliśmy bardzo prosty metronom!
