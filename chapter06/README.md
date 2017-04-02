# Pobawmy się przyciskami

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

1. Funkcja `sleep` sprawia, że micro:bit jest uśpiony dla pewnej liczby milisekund. Jeśli chcesz pauze w swoim programie, właśnie w taki sposób się robi. Funkcja jest jak metoda, ale nie jest zamocowana do punktu obiektu.
1. Jest to obiekt nazwany `button_a` i pozwala uzyskać ile razy został naciśnięty metodą `get_presses`.

Ponieważ `get_presses` daje wartość liczbową i `display.scroll` wyświetla tylko znaki, musimy przekonwertować wartość numeryczną na łańcuch znaków. Robimy to za pomocą funkcji str ( skrót od string ~ konwertuje rzeczy na ciągi znaków).

Jeśli spojrzysz na te zagnieżdzone nawiasy, zauważysz ze display.scroll zawiera obiekt typu str (tekst) który to zawiera `button_a.get_presses`.
Python rozpoczyna od wykonywania najbardziej wewnętrznie zagnieżdżonej części, zanim jej wynik przekaże do kolejnej warstwy.
Taki sposób programowania nazywa się zagnieżdżaniem - w programowaniu jest on odpowiednikiem rosyjskiej lalki Matrioszki.

![matrioszka][matrioszka]

[matrioszka]: https://github.com/plpug/Microbit/raw/master/chapter06/img/1.jpg "matrioszka"

Załóżmy, że masz wciśnięty przycisk 10 razy, oto jak Python działa. Co się dzieje w ostatnim wierszu kodu:

Python widzi kompletną linie i pobiera wartość `get_presses`:

```markdown
display.scroll(str(button_a.get_presses()))
```

Teraz gdy wie ile razy został naciśnięty przycisk, to konwertuje wartość liczbową w ciąg znaków:

``` markdown
display.scroll(str(10))
```
Wreszcie Python wie co jest przewijane w wyświetlaczu:

```markdown
display.scroll("10")
```

## Pętle zdarzeń

Często potrzebujesz by Twój program poczekał aż coś się wydarzy. Robi się to tworząc pętlę w koło kawałka kodu, który definiuje jak zareagować na różne spodziewane zdarzenia takie jak przyciśnięcie przycisku.
By stworzyć pętlę w Pythonie, użyj słowa kluczowego "while" (oznaczającego "do kiedy"). Sprawdza ono czy coś zwraca wartość True (prawdę).
Jeśli tak jest, wykonuje ono blok kodu zwany "ciałem pętli". Jeśli tak nie jest, przerywa ono pętlę (ignorując jej ciało) po czym przechodzi do kontynuacji wykonywania następującej po nim reszty programu.

W Pythonie można prosto zdefiniować blok kodu. Powiedzmy, że mam do zrobienia rzeczy - zanotowałam to sobie na kartce papieru.Prawdopodobnie wygląda to tak:

```markdown
Zakupy
Wyczyścić lodówkę
Skosić trawnik
```

Jeżeli potrzebowałabym dokładniejszej listy, zrobiłabym tak:

```markdown
Zakupy
	Jajka
	Becon
	Masło

Wyczyścić lodówke
	Znaleźć nową ścierkę
	Wyciągnąć produkty
	Wyciągnąć szuflady

Skosić trawnik
	Sprawdzić trawnik
	Sprawdzić poziom oleju w kosiarce
```

Oczywiste jest, że główne zadania są podzielone na podzadania, które są wciętę pod głównym zadaniem, z którym są związane. Więc jajka, boczek oraz masło są związane z `zakupy`.

Przez wcięcia widać, że zadania są ze sobą powiązane. Nazywa się to zagnieżdżeniem, użyjemy go do zdefiniowania bloku kodu, jak w przykładzie poniżej:

```markdown
from microbit import *

while running_time() < 10000:
    display.show(Image.ASLEEP)

display.show(Image.SURPRISED)
```
Linia `while running_time() < 10000:` sprawdza czy program działa krócej niż 10000 milisekund, czyli 10 sekund. Jeśli tak jest, i tu właśnie widzimy zakres działania, wtedy wyświetla obrazek `Image.ASLEEP` (śpię). Zauważ jak to jest wysunięte (wcięcie) przez co wygląda jak lista rzeczy do zrobienia.

Oczywiście jeśli czas pracy jest równy lub większy niż 1000 milisekund, wówczas na wyświetlaczu pojawi się `Image.SURPRISED.` Dlaczego? Ponieważ pętla jest zakończona
i program będzie kontynuowany po bloku kodu pętli `while`. Wygląda na to, że urządzenie śpi przez 10 sekund, zanim obudzi się z zaskoczeniem.

Spróbuj!

## Obsługa zdarzeń

Jeśli chcemy aby MicroPython reagował na zdarzenia związane z naciśnięciem przycisku, powinniśmy umieścić kod w pętli `while` (pętla nieskończona) i sprawdzić
czy przycisk jest naciskany.

```markdown
while True:
    # robić coś
```
Zróbmy sobie bardzo prosty projekt - zwierzak. Jest to on zawsze smutny, aby go rozweselić naciskamy przycisk A, gdy naciskamy przycisk B nasz zwierzak umiera:

```markdown
from microbit import *

while True:
    if button_a.is_pressed():
        display.show(Image.HAPPY)
    elif button_b.is_pressed():
        break
    else:
        display.show(Image.SAD)

display.clear()

```

Wiemy, że nie jest to przyjemna gra, ale na jej podstawie możesz zrozumieć działanie obsługi zdarzeń i stworzyć z tego przykładu swój projekt.
