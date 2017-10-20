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

## Zadanie 9

Obracaj strzałki, a gdy naciśniesz przycisk, to wskaż który:

```python
arrows = [Image.ARROW_N, Image.ARROW_NE, Image.ARROW_E,
        Image.ARROW_SE, Image.ARROW_S, Image.ARROW_SW,
        Image.ARROW_W, Image.ARROW_NW]

def check_status():
    if button_b.was_pressed():
        display.show(Image.ARROW_E)
        sleep(3000)
    if button_a.was_pressed():
        display.show(Image.ARROW_W)
        sleep(3000)
    if pin2.is_touched():
        display.show(Image.ARROW_S)
        sleep(3000)

while True:
    for arrow in arrows:
        display.show(arrow)
        sleep(500)
        check_status()

```

## Zadanie 10

Wróżka - Gdy potrząśniesz urządzeniem losuje się jeden obrazek z listy

Potrzebujesz dodać bibliotekę do losowania

```python
import random
```

Lista obrazków oraz losowanie:

```python
images = [Image.SKULL, Image.SMAIL, Image.HAPPY, Image.CONFUSED, Image.ASLEEP]

while True:
    display.show('?')
    if accelerometer.was_gesture('shake'):
        display.clear()
        sleep(1000)
        display.show(random.choice(images))
        sleep(5000)
    sleep(10)

```

## Zadanie 11

Zdefiniuj 3 listy i zmieniaj ich wyświetlanie po naciśnięciu przycisku A, B lub pin 2. 

```python
from microbit import *
import random

my_images = [Image.HEART, Image.HEART_SMALL, Image.HAPPY, Image.SMILE,
            Image.SAD, Image.CONFUSED, Image.ANGRY, Image.ASLEEP, 
            Image.SURPRISED, Image.SILLY, Image.FABULOUS, Image.MEH, 
            Image.YES, Image.NO]

my_letters = list('abcdefghijklmnopqrstuvwxyz')

to_show = Image.ALL_ARROWS

while True:
    display.show(random.choice(to_show))
    sleep(300)
    if button_a.is_pressed():
        to_show = my_letters
    if button_b.is_pressed():
        to_show = my_images
    if pin2.is_touched():
        to_show = Image.ALL_ARROWS

```

## Zadanie 12

Wysyłanie wiadomości do innego microbita. Przycisk A zmienia obrazki, przycisk B wysyła numer
wybranego obrazka. Drugie urządzenie po otrzymaniu numeru wyświetla przypisany do niego obrazek

```python
from microbit import *
import radio

my_images = [Image.HEART, Image.HEART_SMALL, Image.HAPPY, Image.SMILE,
            Image.SAD, Image.CONFUSED, Image.ANGRY, Image.ASLEEP, 
            Image.SURPRISED, Image.SILLY, Image.FABULOUS, Image.MEH, 
            Image.YES, Image.NO]

nr = 0
radio.on()

display.show(Image.YES)

while True:
    nr_str = radio.receive()
    if nr_str:
        try:
            nr = int(nr_str)
            display.show(my_images[nr])
        except ValueError:
            display.scroll(nr_str)
        except:
            pass
    if button_a.is_pressed():
        nr += 1
        nr = nr % 14
        display.show(my_images[nr])
        sleep(500)
    if button_b.is_pressed():
        radio.send(str(nr))
        sleep(500)

```
## Zadanie 13

Używanie modułu radio jest bardzo proste. Przy uruchamianiu microbitów wyświetla się animacja. Przycisk A zmienia obrazki. Drugie urządzenie po otrzymaniu numeru wyświetla przypisany do niego obrazek. 

```python
import radio
import random
from microbit import display, Image, button_a, sleep

very_small_square = Image(
             "00000:"
             "00000:"
             "00900:"
             "00000:"
             "00000")

small_square = Image(
             "00000:"
             "09990:"
             "09990:"
             "09990:"
             "00000")

square = Image(
             "99999:"
             "99999:"
             "99999:"
             "99999:"
             "99999")

radio.on()

while True:
    display.show([very_small_square, small_square, square], delay=200)
    
    if button_a.was_pressed():
        radio.send('flash')

    incoming = radio.receive()
    
    if incoming == 'flash':
        sleep(random.randint(50, 350))
        display.show(Image.HAPPY)
        sleep(random.randint(1, 10)*1000)
  ```
