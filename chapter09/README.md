#Gesty

Interesującym efektem ubocznym posiadania akcelerometru jest detekcja gestów.
Jeśli będziesz ruszać swoją płytkę BBC micro:bit w określony sposób,
MicroPython będzie je mógł rozpoznawać.

MicroPython jest zdolny do rozpoznawania następujących gestów: `up` (do góry),
`down` (do dołu), `left` (w lewo), `right` (w prawo), `face up` (wierzchem do góry),
`face down` (wierzchem do dołu), `freefall` (swobodny spadek), `3g`, `6g`, `8g`.
O ile większość nazw powinna być oczywista, `3g`, `6g` i `8g` mają miejsce gdy
urządzenie spotykają te poziomy przeciążenia (jak astronaute wysyłanego
w kosmos).

By odczytać aktualny gest użyj metody `accelerometer.current_gesture`. Jej
wynikiem będzie nazwa jednego z wyżej wymienionych gestów. Przykładowo, ten
program będzie czynił twoją płytkę szczęśliwą jedynie gdy zwrócona będzie ona
wierzchem do góry.

```markdown
from microbit import *

while True:
    gesture = accelerometer.current_gesture()
    if gesture == "face up":
        display.show(Image.HAPPY)
    else:
        display.show(Image.ANGRY)
```

Ponownie, ponieważ chcemy by płytka reagowała na zmieniające się okoliczności
użyjemy pętli `while` W jej ciele odczytywany jest aktualny gest, po czym
przypisywany jest pod nazwą "gesture". Warunek `if` sprawdza czy `gesture`
to `face up` (Python używa `==` do sprawdzenia zgodności, a pojedyńczy znak
`=` użyty jest do przypisywania - tak jak przypisaliśmy odczytany gest do
nazwy `gesture`). Jeśli gest to `face up`, wtedy użyj wyświetlacza by pokazać
uśmiechniętą buzię. W przeciwnym wypadku urządzenie przybiera groźny wygląd!


##Magiczna 8

Kula magiczna ósemka to zabawka wynaleziona w latach 50tych XX wieku. Idea
polega na tym by zadać pytanie na które można odpowiedzieć tak/nie, potrząsnąć
nią i poczekać aż ujawni się prawda. To raczej proste przekształcić ją
w program:

```markdown
from microbit import *
import random

answers = [
    "To pewne",
    "Zdecydowanie tak",
    "Pewnie tak",
    "Tak, definitywnie",
    "Mozesz polegać na tym",
    "Tak, nawet to widze",
    "Chyba tak",
    "Perspektywy dobre",
    "TAK",
    "Objawy wskazują na tak",
    "Nie wiem, sprobuj ponownie",
    "Zapytaj potem",
    "Nie chce odpowiadac teraz",
    "Nie mozna przewidziec",
    "Skoncentruj się i zapytaj raz jeszcze",
    "Nie licz na to"
    "Nie",
    "Moje dowody mowia nie",
    "Perspektywy kiepskie",
    "Watpliwe",
]

while True:
    display.show("8")
    if accelerometer.was_gesture("shake"):
        display.clear()
        sleep(1000)
        display.scroll(random.choice(answers))

```

Większość programu to lista nazwana "answers" (odpowiedzi). Właściwa gra zawiera
się w pętli `while` na końcu.

Domyślnym stanem gry jest pokazywanie cyfry `8`. Jednakże program musi wykrywać
że urządzenieądzenie jest potrząsane. Metoda `was_gesture` używa swojego
argumentu (w tym
wypadk napisu `shake` (potrząsać) ponieważ chcemy wykryć potrząsanie) by zwrócić
`True`/`False` (prawda/fałsz) w odpowiedzi. Jeśli użądzenie było potrząsane,
warunkowy "if" wykona blok kodu który wyczyści ekran, poczeka sekundę (dzięki
czemu będzie wyglądało jakby użądzenie myślało nad odpowiedzią na twoje pytanie)
po czym wyświetli przypadkowo wybraną (ang. `random choice`) odpowiedź.

Dlaczego by nie zapytać urządzenie czy to nie najwspanialszy program kiedykolwiek
napisany? Co możesz zrobić by `oszukiwać` i uzyskiwać zawsze odpowiedź pozytywną
lub negatywną? (Podpowiedź: użyj przycisków).
