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

1. Funkcja `sleep` sprawia, że micro:bit jest uśpiony dla pewnej liczby milisekund. Jeśli chcesz pauze w swoim programie, właśnie w taki sposób się robi. Funkcja jest jak metoda, ale nie jest zamocowana do punktu obiektu. 
2. Jest to obiekt nazwany `button_a` i pozwala uzyskać ile razy został naciśnięty metodą `get_presses`.

Ponieważ `get_presses` daje wartość liczbową i `display.scroll` wyświetla tylko znaki, musimy przekonwertować wartość numeryczną na łańcuch znaków. Robimy to za pomocą funkcji str ( skrót od string ~ konwertuje rzeczy na ciągi znaków). 

Jeśli spojrzysz na te zagnieżdzone nawiasy, zauważysz ze display.scroll zawiera obiekt typu str (tekst) który to zawiera button_a.get_presses.
Python rozpoczyna od wykonywania najbardziej wewnętrznie zagnieżdżonej części, zanim jej wynik przekaże do kolejnej warstwy. 
Taki sposób programowania nazywa się zagnieżdżaniem - w programowaniu jest on odpowiednikiem rosyjskiej lalki Matrioszki.

![babki][logo]
[logo]: https://github.com/plpug/Microbit/blob/master/6/img/1.jpg "matrioszka"

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

##Pętle zdarzeń

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
	
