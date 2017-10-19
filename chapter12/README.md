# Radio

W każdym Micro:bicie znajduje się ciekawa oraz przydatna funkcjonalność, a mianowicie `Radio`. Moduł radio pozwala nam
na przesyłanie oraz odbieranie wiadomości.

Po pierwsze musimy zaimportować moduł radia `import radio`, aby udostępnić funkcje naszemu programowi. Następnie musimy uruchomić radio, za pomocą `radio.on()`.

W tym momencie moduł radiowy jest skonfigurowany do rozsądnych wartość domyślnych, sprawiają one że jest kompatybilny z innymi platformami, które są zgodne z BBC micro:bit.
Możliwe jest sterowanie z omówionymi powyżej funkcjami, jak również ilość wykorzystywana transmijsi wiadomości i ilości pamięci RAM. Zakładając, że jesteśmy zadowoleni z ustawień
domyślnych, najprostszy sposób wysyłania wiadomości jest następujący:

`radio.send("wiadomość")`

W przykładzie użyliśmy funkcji wysyłania, aby po prostu nadać ciąg znaków "wiadomość". Otrzymywanie wiadomości jest jeszcze prostsze:

```python
new_message = radio.receive()
```

Po otrzymaniu wiadomości są one umieszczane w kolejce wiadomości. Funkcja `receive` (odbierania) zwraca najstarszą wiadomość z kolejki jako ciąg znaków, co umożliwia utworzenie nowej wiadomości przychodzącej. Jeśli wypełni się kolejka komunikatów, nowe przychodzące wiadomości są ignorowane.

Posiadając taką wiedzę, możemy stworzyć swój pierwszy projekt:

```python
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

Kluczowa część zawiera się w pętli zdarzeń. Po pierwsze, sprawdza ona czy przycisk A został wciśnięty, i jeśli tak - używa radia by by wysłać wiadomość "hello" (ang. cześć). Następnie czyta wszelkie wiadomości z kolejki wiadomości z użyciem radio.receive(). Po czym używa display.show() by pokazać obrazek kaczki.

## Ćwiczenie

Dobieramy się w dwu osobowe zespoły. Staramy się przećwiczyć w parach działanie powyższego przykładu. Po przećwiczeniu, zadaniem Waszym jest
na podstawie przykładu stworzyć własny program. Program musi działać, zgodnie z poniższymi instrukcjami:

* Zaimportować moduł radio
* Włączyć radio
* Wysyłać albo otrzymywać wiadomości
* Wyświetlić animacje
