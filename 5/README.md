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





