# Radio

Wewn¹trz ka¿dego Micro:bita znajduje siê bardzo przydatna funkcjonalnoœci, a mianowicie Radio. Dziêki tej funkcjonalnoœci mo¿emy przesy³aæ i odbieraæ wiadomoœci.
W ka¿dym Micro:bicie znajduje siê ciekawa oraz przydatna funkcjonalnoœæ, a mianowicie `Radio`. Modu³ radio pozwala nam
na przesy³anie oraz odbieranie wiadomoœci.

Po pierwsze musimy zaimportowaæ modu³ radia `import radio`, aby udostêpniæ funkcje naszemu programowi. Nastêpnie musimy uruchomiæ radio, za pomoc¹ `radio.on()`.

W tym momencie modu³ radiowy jest skonfigurowany do rozs¹dnych wartoœæ domyœlnych, sprawiaj¹ one ¿e jest kompatybilny z innymi platformami, które s¹ zgodne z BBC micro:bit.
Mo¿liwe jest sterowanie z omówionymi powy¿ej funkcjami, jak równie¿ iloœæ wykorzystywana transmijsi wiadomoœci i iloœci pamiêci RAM. Zak³adaj¹c, ¿e jesteœmy zadowoleni z ustawieñ
domyœlnych, najprostszy sposób wysy³ania wiadomoœci jest nastêpuj¹cy:

`radio.send("wiadomoœæ")`

W przyk³adzie u¿yliœmy funkcji wysy³ania, aby po prostu nadaæ ci¹g znaków "wiadomoœæ". Otrzymywanie wiadomoœci jest jeszcze prostsze:

```markdown
new_message = radio.receive()
```

Po otrzymaniu wiadomoœci s¹ one umieszczane w kolejce wiadomoœci. Funkcja `receive` (odbierania) zwraca najstarsz¹ wiadomoœæ z kolejki jako ci¹g znaków, co umo¿liwia utworzenie nowej wiadomoœci przychodz¹cej. Jeœli wype³ni siê kolejka komunikatów, nowe przychodz¹ce wiadomoœci s¹ ignorowane.

Posiadaj¹c tak¹ wiedzê, mo¿emy stworzyæ swój pierwszy projekt:

```markdown
from microbit import display, button_a, Image
import radio
radio.on()
while True:
    message = radio.receive()
    if message:
        display.show(Image.DUCK)
    if button_a.was_pressed():
        display.clear()
        radio.send("hello")

```

Kluczowa czêœæ zawiera siê w pêtli zdarzeñ. Po pierwsze, sprawdza ona czy przycisk A zosta³ wciœniêty, i jeœli tak - u¿ywa radia by by wys³aæ wiadomoœæ "hello" (ang. czeœæ). Nastêpnie czyta wszelkie wiadomoœci z kolejki wiadomoœci z u¿yciem radio.receive(). Po czym u¿ywa display.show() by pokazaæ obrazek kaczki.

## Æwiczenie

Dobieramy siê w dwu osobowe zespo³y. Staramy siê przeæwiczyæ w parach dzia³anie powy¿szego przyk³adu. Po przeæwiczeniu, zadaniem Waszym jest
na podstawie przyk³adu stworzyæ w³asny program. Program musi dzia³aæ, zgodnie z poni¿szymi instrukcjami:

* Zaimportowaæ modu³ radio
* W³¹czyæ radio
* Wysy³aæ albo otrzymywaæ wiadomoœci
* Wyœwietliæ animacje
