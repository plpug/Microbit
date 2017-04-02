#Wprowadzenie do micro:bit

BBC Micro:bit to małe, wszechstronne urządzenie, które ma dużą ilość sensorów, wejścia i wyjścia oraz co ciekawe ekranem LED 5x5 i można je programować w Pythonie!
Jak widzicie na poniższym obrazku wygląda bardzo przyjaźnie :)


Oczywiście Python nie jest jedynym językiem, stosowanym do programowania tego urządzenia.
Więcej informacji na temat urządzenia znajdziecie [na stronie](http://www.microbit.org/hardware/).

Poprzednie rozdziały przygotowane zostały w celu przygotowania Was do pracy z urządzeniem, teraz powinno być Wam łatwiej wykorzystać zdobytą wiedzę przy pracy z urządzeniem.

Co nam będzie potrzebne:

* na pewno urządzenie, ale to wiemy
* edytor [MU](https://codewith.mu/) - jest to prosty edytor kodu przeznaczony dla dzieci, nauczycieli oraz początkujących programistów.

No to zaczynamy!

##Przywitaj się z urządzeniem

Zgodnie z tradycją w trakcie startu z nowym językiem programowania, najprotszą instrukcją jest wyświetlenie na ekranie komputera napisu "hello world". Zrób to na naszym urządzeniu, w MicroPythonie na pewno będzie to proste:

```markdown
from microbit import*
display.scroll("Hello World")
```

Zwróćmy uwagę na pierwszą linie kodu:

```markdown
from microbit import*
```

Po co nam ta linia? Czy jest bardzo potrzebna? Tak, nawet bardzo Wszystkie potrzebne rzeczy do naszej pracy znajdują się w module o nazwie microbit (moduł jest biliteką wcześniej istniejącego kodu). Tak więc ten fragment oznacza dosłownie "chcę móc korzystać z wszystkiego od kodu bilioteki microbit).

Linia następna:

```markdown
display.scroll("Hello World")

```

Odpowiada za przewijanie ciągu znaków na wyświetlaczu. Aby móc zobaczyć jakieś znaki na naszym wyświeltaczu musimy wpisać co chcemy, musimy określić to w cudzysłowiu `(")` oraz nawiasie `()`.
Więc `display.scroll("Hello world")` dosłownie "Chce móc skorzystać z wyświetlacza aby móc przewinąć tekst "Hello world"". Skopiuj kod "Hello world" i wklej go w swoim edytorze i wgraj je do urządzenia.

Chcesz zmienić tekst przewijania, tak aby urządzenie przywitało się z Tobą np. " Witaj Dominik"? Niech to będzie zadanie dla Ciebie, wykonaj je samodzielnie :)


##Obrazki

MicroPython jest znakomity w sztuce, jeśli jedyne czego nam potrzeba to siatka 5x5 diod LED. MicroPython daje nam dużo kontroli nad wyświelaczem, dzięki czemu możemy tworzyć różnego rodzaju ciekawe efekty.  Na przykład, żeby wywołać radość w naszym urządzeniu należy wpisać:

```markdown
from microbit import *

display.show(Image.HAPPY)
```
Pewnie pamiętacie co oznacza pierwsza linijka kodu, tak więc nie będę drugi raz przypominać. Druga linia wykorzystuje obiekt do wyświeltenia wbudowanego obrazu. Obraz, który chcemy wyświetlać jest częścią obiektu obrazu o nazwie HAPPY.

Poniżej znajduje się lista wbudowanych obrazów:

```markdown

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
Image.CLOCK12, Image.CLOCK11, Image.CLOCK10, Image.CLOCK9, Image.CLOCK8, Image.CLOCK7, Image.CLOCK6, Image.CLOCK5, Image.CLOCK4, Image.CLOCK3, Image.CLOCK2, Image.CLOCK1
Image.ARROW_N, Image.ARROW_NE, Image.ARROW_E, Image.ARROW_SE, Image.ARROW_S, Image.ARROW_SW, Image.ARROW_W, Image.ARROW_NW
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
```
###Zadanie

Jak widzicie powyżej znajduje się lista wbudowanych obrazów, zadaniem dla Was jest uruchomić każdy z nich. Miłej zabawy :)

##Obrazki DIY

Oczywiście możesz również tworzyć własne obrazki i wyświetlać je na urządeniu. To proste.

Każda dioda LED na urządzeniu może zostać ustawiona w jednym z 10 stanów. Jeśli jest ustawiona na 0 (zero) - jest wyłączona. Dosłownie jej jasność jest zerowa. Jeśli jednak jest ustawiona na 9 - to jej najjaśniejsze ustawienie. Wartości od 1 do 8 reprezentują pośrednie poziomy jasności od wyłączonej (0) do tej w pełni jasności (9).

Będąc uzbrojonym w te informacje, możliwe jest utworzenie obrazka jak ten:

```markdown
from microbit import *

boat = Image("05050:"
             "05050:"
             "05050:"
             "99999:"
             "09990")

display.show(boat)
```

#Animacje

Takie obrazki są zabawne, ale jeszcze więcej zabawy mamy gdy chcemy aby się przesuwały. Jest to proste w MicroPythonie, po prostu musimy użyć listy obrazków. Tutaj jest lista zakupów:

```markdown

Jajka
Becon
Pomidory
```

Tak się tworzy listę w Pythonie:

```markdown
zakupy = ["jajka", "bekon", "pomidory"]
```
Prosto tworzymy listę nazywając ja `zakupy` oraz tworzymy jej trzy elementy. Python wie, że jest to lista ponieważ jest ona umieszczona w nawiasie kwadratowym `[]`. Elementy są oddzielone przecinkami `,`,a w tym przypadku elementy listy są trzema ciągami znaków: `jajka`, `bekon`, `pomidory`.
Wiemy, że są to ciągi znaków ponieważ są one umieszczone w cudzysłowie `""`.

Możemy nawet przechowywać w tej samej liście różne rodzaje rzeczy. Na szczeście mamy kilka list obrazków już wbudowanych są zwane `Image.ALL_CLOCKS` i `Image.ALL_ARROWS`:

```markdown

from microbit import *

display.show(Image.ALL_CLOCKS, loop=True, delay=100)
```

Podobnie jak w przypadku pojedyńczego obrazu używamy `display.SHOW` aby wyświelić go na ekranie urządzenia. Jednak my daliśmy znać MicroPythonowi aby używał `Image.ALL_CLOCKS`	i on rozumie, że musi wyświetlić wszystkie obrazy z listy, jeden po drugim. Powiedzieliśmy również MicroPythonowi aby zachował zapętlenie nad listą obrazów (animacja trwa wiecznie) `loop=true`.
Możemy również dać znać, że chcielibyśmy aby obrazki wyświetlały się z opóźnieniem 100 milisekund `delay=100`.

```markdown
from microbit import *

boat1 = Image("05050:"
              "05050:"
              "05050:"
              "99999:"
              "09990")

boat2 = Image("00000:"
              "05050:"
              "05050:"
              "05050:"
              "99999")

boat3 = Image("00000:"
              "00000:"
              "05050:"
              "05050:"
              "05050")

boat4 = Image("00000:"
              "00000:"
              "00000:"
              "05050:"
              "05050")

boat5 = Image("00000:"
              "00000:"
              "00000:"
              "00000:"
              "05050")

boat6 = Image("00000:"
              "00000:"
              "00000:"
              "00000:"
              "00000")

all_boats = [boat1, boat2, boat3, boat4, boat5, boat6]
display.show(all_boats, delay=200)
```

Jak działa ten kod:

* Tworzymy sześć obrazków łodzi `boat` w taki sam sposób jaki opisaliśmy wyżej.
* Umieszczamy je na liście o nazwie `all_boats`.
* Wreszcie prosimy aby animować tą listę z opóźnieniem 200 milisekund.
* Przez to, że nie została ustawiona pętla, animacja uruchamia się tylko raz.
