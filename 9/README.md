#Gesty

Interesuj¹cym efektem ubocznym posiadania akcelerometru jest detekcja gestów.
Jeœli bêdziesz ruszaæ swoj¹ p³ytkê BBC micro:bit w okreœlony sposób,
MicroPython bêdzie je móg³ rozpoznawaæ.

MicroPython jest zdolny do rozpoznawania nastêpuj¹cych gestów: `up` (do góry),
`down` (do do³u), `left` (w lewo), `right` (w prawo), `face up` (wierzchem do góry),
`face down` (wierzchem do do³u), `freefall` (swobodny spadek), `3g`, `6g`, `8g`.
O ile wiêkszoœæ nazw powinna byæ oczywista, `3g`, `6g` i `8g` maj¹ miejsce gdy
urz¹dzenie spotykaj¹ te poziomy przeci¹¿enia (jak astronaute wysy³anego
w kosmos).

By odczytaæ aktualny gest u¿yj metody `accelerometer.current_gesture`. Jej
wynikiem bêdzie nazwa jednego z wy¿ej wymienionych gestów. Przyk³adowo, ten
program bêdzie czyni³ twoj¹ p³ytkê szczêœliw¹ jedynie gdy zwrócona bêdzie ona
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

Ponownie, poniewa¿ chcemy by p³ytka reagowa³a na zmieniaj¹ce siê okolicznoœci
u¿yjemy pêtli `while` W jej ciele odczytywany jest aktualny gest, po czym
przypisywany jest pod nazw¹ "gesture". Warunek `if` sprawdza czy `gesture`
to `face up` (Python u¿ywa `==` do sprawdzenia zgodnoœci, a pojedyñczy znak
`=` u¿yty jest do przypisywania - tak jak przypisaliœmy odczytany gest do
nazwy `gesture`). Jeœli gest to `face up`, wtedy u¿yj wyœwietlacza by pokazaæ
uœmiechniêt¹ buziê. W przeciwnym wypadku urz¹dzenie przybiera groŸny wygl¹d!


##Magiczna 8

Kula magiczna ósemka to zabawka wynaleziona w latach 50tych XX wieku. Idea
polega na tym by zadaæ pytanie na które mo¿na odpowiedzieæ tak/nie, potrz¹sn¹æ
ni¹ i poczekaæ a¿ ujawni siê prawda. To raczej proste przekszta³ciæ j¹
w program:

```markdown
from microbit import *
import random

answers = [
    "To pewne",
    "Zdecydowanie tak",
    "Pewnie tak",
    "Tak, definitywnie",
    "Mozesz polegaæ na tym",
    "Tak, nawet to widze",
    "Chyba tak",
    "Perspektywy dobre",
    "TAK",
    "Objawy wskazuj¹ na tak",
    "Nie wiem, sprobuj ponownie",
    "Zapytaj potem",
    "Nie chce odpowiadac teraz",
    "Nie mozna przewidziec",
    "Skoncentruj siê i zapytaj raz jeszcze",
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

Wiêkszoœæ programu to lista nazwana "answers" (odpowiedzi). W³aœciwa gra zawiera
siê w pêtli `while` na koñcu.

Domyœlnym stanem gry jest pokazywanie cyfry `8`. Jednak¿e program musi wykrywaæ
¿e urz¹dzenie¹dzenie jest potrz¹sane. Metoda `was_gesture` u¿ywa swojego
argumentu (w tym
wypadk napisu `shake` (potrz¹saæ) poniewa¿ chcemy wykryæ potrz¹sanie) by zwróciæ
`True`/`False` (prawda/fa³sz) w odpowiedzi. Jeœli u¿¹dzenie by³o potrz¹sane,
warunkowy "if" wykona blok kodu który wyczyœci ekran, poczeka sekundê (dziêki
czemu bêdzie wygl¹da³o jakby u¿¹dzenie myœla³o nad odpowiedzi¹ na twoje pytanie)
po czym wyœwietli przypadkowo wybran¹ (ang. `random choice`) odpowiedŸ.

Dlaczego by nie zapytaæ urz¹dzenie czy to nie najwspanialszy program kiedykolwiek
napisany? Co mo¿esz zrobiæ by `oszukiwaæ` i uzyskiwaæ zawsze odpowiedŸ pozytywn¹
lub negatywn¹? (PodpowiedŸ: u¿yj przycisków).