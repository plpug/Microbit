# Kurs 1

## Zadanie 1

Wyświetl napis "Hello Python"

Najpierw zaimportuj biblioteki, one zawsze będą na potrzebne.

```python
from microbit import *
```

Teraz wyświetl napis

```python
while True:
    display.scroll('Hello Python')
    sleep(1000)
```

Zrób to samo, ale przypisz napis do jakiejś zmiennej np. `words`

```python
words = 'Hello Python'
```

Zmienna ustawiona. A teraz wyświetlaj to co przypisałeś.

```python
while True:
    display.scroll(words)
    sleep(1000)
```
Gotowe!

## Zadanie 2

Biblioteka microbit zawiera listę zdefiniowanych obrazków:

    Image.HEART
    Image.HEART_SMALL
    Image.HAPPY
    Image.SMILE
    Image.SAD
    Image.CONFUSED
    Image.ANGRY
    Image.ASLEEP
    Image.SURPRISED
    Image.SILLY
    Image.FABULOUS
    Image.MEH
    Image.YES
    Image.NO
    Image.CLOCK12, Image.CLOCK11, Image.CLOCK10, Image.CLOCK9, Image.CLOCK8, Image.CLOCK7,
    Image.CLOCK6, Image.CLOCK5, Image.CLOCK4, Image.CLOCK3, Image.CLOCK2, Image.CLOCK1
    Image.ARROW_N, Image.ARROW_NE, Image.ARROW_E, Image.ARROW_SE, Image.ARROW_S, Image.ARROW_SW,
    Image.ARROW_W, Image.ARROW_NW
    Image.TRIANGLE
    Image.TRIANGLE_LEFT
    Image.CHESSBOARD
    Image.DIAMOND
    Image.DIAMOND_SMALL
    Image.SQUARE
    Image.SQUARE_SMALL
    Image.RABBIT
    Image.COW
    Image.MUSIC_CROTCHET
    Image.MUSIC_QUAVER
    Image.MUSIC_QUAVERS
    Image.PITCHFORK
    Image.XMAS
    Image.PACMAN
    Image.TARGET
    Image.TSHIRT
    Image.ROLLERSKATE
    Image.DUCK
    Image.HOUSE
    Image.TORTOISE
    Image.BUTTERFLY
    Image.STICKFIGURE
    Image.GHOST
    Image.SWORD
    Image.GIRAFFE
    Image.SKULL
    Image.UMBRELLA
    Image.SNAKE

Wyświetl jeden z nich:

```python
display.show(Image.SMILE)
```

A teraz wybierz 5 z nich i wyświetlaj je na przemian co 3 sekundy:

Ja mam taką listę z moimi obrazkami: smutny, trójkąt, kwadrat, królik, szczęśliwy ;)

```python
my_images = (Image.SAD, Image.TRIANGLE, Image.SQUARE, Image.RABBIT, Image.HAPPY)
```

Wyświetlam w pętli każdy obrazek z listy:

```python
for image in my_images:
    display.show(image)
    sleep(3000)
```

## Zadanie 3

Zaprojektuj obrazek flagi:

```python
flag = Image("97777:"
              "95557:"
              "97777:"
              "90000:"
              "90000")
```

Obrazek jest gotowy i znajduje się pod zmienną `flag`, teraz należy go wyświetlić:

```python
display.show(flag)
```

A teraz z dodaj drugą flagę i wyświetlaj je na przemian co sekundę.


```python
flag2 = Image("97777:"
              "90007:"
              "97777:"
              "90000:"
              "90000")
```

Druga flaga gotowa, to wyświetlamy:

```python
while True:
    display.show(flag)
    sleep(1000)
    display.show(flag2)
    sleep(1000)
```

Jest prostszy sposób na wyświetlanie obrazków na przemian. Utwórz listę obrazków i zamień
 nieskończoną pętlę `while True` na metodę `show` z parametrem `delay`:

```python
all_flags = [flag, flag2]
display.show(all_flags, delay=1000)
```

## Zadanie 4

Zasymuluj zegara. Przesuwaj jedną wskazówkę co 1 sekundę. Wykorzystaj strzałki z biblioteki Image:

```python
arrows = [Image.ARROW_N, Image.ARROW_NE, Image.ARROW_E,
        Image.ARROW_SE, Image.ARROW_S, Image.ARROW_SW,
        Image.ARROW_W, Image.ARROW_NW]

display.show(arrows, delay=1000, loop=True)
```

## Zadanie 5

Wykorzystaj przycisk do wyłaczenia symulacji zegara

Najpierw tworzym sobie funkcję o nazwie rotate:

```python
def rotate():
    while True:
        display.show(Image.ALL_ARROWS, delay=100, loop=False)
        if button_a.was_pressed():
            display.show(Image.SMILE)
            break
```

A teraz uruchamianie funkcji:

```python
while True:
    if button_b.was_pressed():
        rotate()
    sleep(3000)
```

## Zadanie 6

Utwórz kompas, wykorzystaj  bibliotekę compass

```python
# Start calibrating
compass.calibrate()
```

```python
# Try to keep the needle pointed in (roughly) the correct direction
while True:
    sleep(100)
    needle = ((15 - compass.heading()) // 30) % 12
    display.show(Image.ALL_CLOCKS[needle])

```

## Zadanie 7

Powiedz "Hello, Python"

```python
import speech
```

```python
speech.say("Hello, Python")

```

## Zadanie 8

Wyślij wiadomość do innych uczniów. Niech Twoją wiadomością będzie pierwsza litera Twojego imienia.

```python
from microbit import display, button_a, Image
import radio

```

Włączamy radio odbiornik, przyciśnięcie jednego przycisku czyści ekran z diodami i wysyła wiadomość do innych. Jeżeli wiadomość zostanie odebrana, to zostanie wyświetlona na ekranie z diodami.

```python
radio.on()
while True:
    message = radio.receive()
    if message:
        display.show(message)
    if button_a.was_pressed():
        display.clear()
        radio.send("W")

```
