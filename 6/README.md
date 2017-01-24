#Pobawmy się przyciskami

Do tej pory stworzylismy kod powodujacy ze urzadzenie robi "coś". To coś - nazywamy "wyjściem" (efektem). Jednakze nasze urzadzenie powinno reagowac na "coś". Tym razem "coś" - nazywamy "wejściem".

To jest latwe do zapamiętania: wyjściem jest to, co urządzenie z siebie daje. Wejściem jest za to, to, co urządzenie przyjmuje do wykorzystania/przetworzenia.

Najbardziej oczywistym znaczeniem "wejścia" na micro:bit są dwa przyciski, opisane jako A i B. Naszym zadaniem jest zareagowanie z MicroPythona na ich przyciskanie.

Jest to niezbyt trudne:

```markdawn
from microbit import *

sleep(10000)
display.scroll(str(button_a.get_presses()))
```

Powyższy skrypt pokazuje: urządzenie jest uśpione przez dziesięć tysięcy sekund, po czym przewija tyle razy ile razy został naciśnięty przycisk. 

Choć jest dość bezużyteczny skrypt, wprowadza kilka ciekawych pomysłów:

Funkcja `sleep` sprawia, że micro:bit jest uśpiony dla pewnej liczby milisekund. Jeśli chcesz pauze w swoim programie, właśnie w taki sposób się robi. Funkcja jest jak metoda, ale nie jest zamocowana do punktu obiektu. Jest to obiekt nazwany `button_a` i pozwala uzyskać ile razy został naciśnięty metodą `get_presses`.
