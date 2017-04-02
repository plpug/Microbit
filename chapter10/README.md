# Mowa

Komputer i roboty, które mówią czują się bardziej ludzkie. Sprawienie aby micro:bit mówił jest tzw. formą przekazywania informacji w formie zabawy,
w skuteczny i użyteczny sposób. W zwiazku z tym w urządzeniu wbudowany jest syntezator mowy oparty na inżynierii wstecznej wersji syntezatora z 1980 roku.

Brzmi to bardzo fajnie, mając to na uwagę zamierzamy wykorzystać syntezator mowy do stworzenia...

## Dalek Poetry

![robot dalek][dalek]

[dalek]: https://github.com/plpug/Microbit/raw/master/chapter10/img/dalek.jpg "robot dalek"

To bardzo mało znany fakt, że Dalekowie uwielbiają poezje - szczególnie limeryki. Kto by pomyślał, ale fakt jest faktem.
W każdym razie chcielibyśmy aby Dalek nam recytował na żadanie.

## Powiedz coś

Przed umożliwieniem mówienia urządzeniu musimy podłączyć przewody, tak jak na obrazku poniżej:

![plytka][plytka]

[plytka]: https://github.com/plpug/Microbit/raw/master/chapter10/img/speech1.png "obraz plytki"

Najprostszym sposobem na uzyskanie możliwości mówienia jest zaimportowanie `speech` czyli modułu mowy. Użyj tej funkcji np. tak:

```markdown

import speech

speech.say("Hello, World")
```

Chociaż sprawiliśmy, że nasze urządzenie przemówiło i jest to fajne, nie przypomina to robota Dalek. Więc musimy zmienić niektóre parametry.
Aby przystosować syntezator mowy dla naszych potrzeb, syntezator mowy jest bardzo mocny w tym zakresie, ponieważ możemy zmieniać cztery parametry:

* `pitch` - jak wysoki lub niski jest dźwięk głosu (0 = wysoki, 255 = Barry White)
* `speed` - jak szybka jest mowa urządzenia (0 = niemożliwy, 255 = bajka na dobranoc)
* `mouth` - jak wydawać dźwięki z zaciśniętymi lub otwartymi ustami (0 = manekin brzuchomówcy, 255 = Foghorn Leghorn)
* `throat` - jak zrelaksowany lub napięty jest ton głosu(0 = rozstrzęsiony , 255 = totalnie wyluzowany)

Łącznie, paramatry te kontrolują jakość dźwięku (barwa). Mówiąc szczerze to najlepszy sposób, aby uzyskać ton idealny ton głosu. Chcesz eksperytmentować,
śmiało działaj z dźwiękiem i osądzaj jego jakość.

My również ekperymentowaliśmy, i oto nasz przykład:

```markdown
speech.say("I am a Dalek, I'm deadly", speed=120, pitch=100, throat=100, mouth=200)
```

## Poezja

Można również kazać naszemu urządzeniu aby mówił nam limeryki:

```markdown
# DALEK poetry generator, by The Doctor
import speech
from microbit import sleep

poem = [
    "there was a young man from koczala"
    "where he was born",
    "He returned to his hometown dark",
    "he went to the lake",
    "and I have been there forever",
    "EXTERMINATE",
]

# Loop over each line in the poem and use the speech module to recite it.
for line in poem:
    speech.say(line, speed=120, pitch=100, throat=100, mouth=200)
    sleep(500)

```

Python, dla każdego elementu listy wypełnionej strofami poetów, wywołuje w pętli “speech.say” z ustawieniami głosu robota DALEK, który recytuje poemat. Między każdą linią wstawiona jest pauza pół sekundowa, bo nawet DALEK potrzebuje czasu by wziąć oddech.

Możemy również sprawić aby Dalek losowo wypowiadał słowa, które są dostępne w liście:

`dalekWords = ["EXTERMINATE", "WHERE, IS, DOCTOR", "ALARM", "DALEK"]`

Dzięki pętli `while` DALEK będzie wypowiadał w nieskończoność słowa z listy, po każdym słowie następuje pauza 20 sekundowa:


```markdown
# Dalek voice

from microbit import *
import speech
import random


dalekWords = ["EXTERMINATE", "WHERE, IS, DOCTOR", "ALARM", "DALEK"]
numberOfDalekWords = len(dalekWords)

display.show(Image.HAPPY)

while True:
    speech.say(dalekWords[random.randrange(numberOfDalekWords)], pitch=64, speed=192, mouth=200, throat=64)
    sleep(2000)

```

## Zaśpiewaj piosenke

Zmieniając ustawienie `pitch` i wywołanie funkcji `sing` sprawi, że urządzenie nam zaśpiewa (choć pewnie nie wygra eurowizji ;))
Mapowanie numerów tonu do nut znajduje się poniżej:

![nuty][nuty]

[nuty]: https://github.com/plpug/Microbit/raw/master/chapter10/img/speech.png "obraz nut"

```markdown
speech.sing("#115DOWWWW")
```

Zauważ jak wysokość tonu odwzorowującego śpiew jest dołączana przed fonemem wraz ze znakiem “hash” (#). Wysokość tonu pozostanie taka sama dla następujących fonemów dopóki nowa wysokość nie zostanie przypisana.

Poniższy przykład demonstruje jak wszystkie trzy funkcje generujące (“say”, “pronounce” i “sing”) mogą zostać użyte by uzyskać w efekt zbliżony do mowy:

```markdown
import speech
from microbit import sleep

speech.say("I can sing!")
sleep(1000)
speech.say("Listen to me!")
sleep(1000)


speech.pronounce("AEAE/HAEMM", pitch=200, speed=100)  # Ahem
sleep(1000)

solfa = [
    "#115DOWWWWWW",   # Doh
    "#103REYYYYYY",   # Re
    "#94MIYYYYYY",    # Mi
    "#88FAOAOAOAOR",  # Fa
    "#78SOHWWWWW",    # Soh
    "#70LAOAOAOAOR",  # La
    "#62TIYYYYYY",    # Ti
    "#58DOWWWWWW",    # Doh
]

song = ''.join(solfa)
speech.sing(song, speed=100)
solfa.reverse()
song = ''.join(solfa)
speech.sing(song, speed=100)
```

Jak widzimy nasz DALEK jest bardzo uzdolniony, potrafi recytować oraz śpiewać.

## Zadanie

Chce abyście stworzyli swój limeryk i kazali dalkowi go przeczytać. Nie zapominajcie o tym,
że dalek ma to robić z uśmiechem. Pamiętamy chyba jak wywołać uśmiech na urządzeniu :)
Przed zakończeniem swojej pracy DALEK ma nam zaśpiewać na pożegnanie.
