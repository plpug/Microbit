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

Po co nam ta linia? Czy jest bardzo potrzebna? Oh tak, jest potrzebna, a nawet bardzo potrzebna. Dzięki temu kawałkowi kodu 

