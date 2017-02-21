#Mowa

Komputer i roboty, które mówi¹ czuj¹ siê bardziej ludzkie. Sprawienie aby micro:bit mówi³ jest tzw. form¹ przekazywania informacji w formie zabawy, 
w skuteczny i u¿yteczny sposób. W zwiazku z tym w urz¹dzeniu wbudowany jest syntezator mowy oparty na in¿ynierii wstecznej wersji syntezatora z 1980 roku.

Brzmi to bardzo fajnie, maj¹c to na uwagê zamierzamy wykorzystaæ syntezator mowy do stworzenia...

##Dalek Poetry

![dalek][logo]

[logo]: https://github.com/plpug/Microbit/blob/master/10/img/dalek.jpg "robot dalek"

To bardzo ma³o znany fakt, ¿e Dalekowie uwielbiaj¹ poezje - szczególnie limeryki. Kto by pomyœla³, ale fakt jest faktem. 
W ka¿dym razie chcielibyœmy aby Dalek nam recytowa³ na ¿adanie.

##Powiedz coœ

Przed umo¿liwieniem mówienia urz¹dzeniu musimy pod³¹czyæ przewody, tak jak na obrazku poni¿ej:

![plytka][logo]

[logo]: https://github.com/plpug/Microbit/blob/master/10/img/speech1.png "obraz plytki"

Najprostszym sposobem na uzyskanie mo¿liwoœci mówienia jest zaimportowanie `speech` czyli modu³u mowy. U¿yj tej funkcji np. tak:

```markdown

import speech

speech.say("Hello, World")
```

Chocia¿ sprawiliœmy, ¿e nasze urz¹dzenie przemówi³o i jest to fajne, nie przypomina to robota Dalek. Wiêc musimy zmieniæ niektóre parametry.
Aby przystosowaæ syntezator mowy dla naszych potrzeb, syntezator mowy jest bardzo mocny w tym zakresie, poniewa¿ mo¿emy zmieniaæ cztery parametry:

*`pitch` - jak wysoki lub niski jest dŸwiêk g³osu (0 = wysoki, 255 = Barry White)
*`speed` - jak szybka jest mowa urz¹dzenia (0 = niemo¿liwy, 255 = bajka na dobranoc)
*`mouth` - jak wydawaæ dŸwiêki z zaciœniêtymi lub otwartymi ustami (0 = manekin brzuchomówcy, 255 = Foghorn Leghorn)
*`throat` - jak zrelaksowany lub napiêty jest ton g³osu(0 = rozstrzêsiony , 255 = totalnie wyluzowany)

£¹cznie, paramatry te kontroluj¹ jakoœæ dŸwiêku (barwa). Mówi¹c szczerze to najlepszy sposób, aby uzyskaæ ton idealny ton g³osu. Chcesz eksperytmentowaæ, 
œmia³o dzia³aj z dŸwiêkiem i os¹dzaj jego jakoœæ. 

My równie¿ ekperymentowaliœmy, i oto nasz przyk³ad: 

```markdown
speech.say(" I am a Dalek, I'm deadly", speed=120, pitch=150, throat=100, mouth=230)
```

##Poezja

Mo¿na równie¿ kazaæ naszemu urz¹dzeniu aby mówi³ nam limeryki:

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

Jak widaæ mamy ustawienia mowy 

##Zaœpiewaj piosenke

Zmieniaj¹c ustawienie `pitch` i wywo³anie funkcji `sing` sprawi, ¿e urz¹dzenie nam zaœpiewa (choæ pewnie nie wygra eurowizji ;))
Mapowanie numerów skoku do nut znajduje siê poni¿ej:

![nuty][logo]

[logo]: https://github.com/plpug/Microbit/blob/master/10/img/speech.png "obraz nut"

```markdown
speech.sing("#115DOWWWW")
```

```markdown
import speech
from microbit import sleep

# The say method attempts to convert English into phonemes.
speech.say("I can sing!")
sleep(1000)
speech.say("Listen to me!")
sleep(1000)

# Clearing the throat requires the use of phonemes. Changing
# the pitch and speed also helps create the right effect.
speech.pronounce("AEAE/HAEMM", pitch=200, speed=100)  # Ahem
sleep(1000)

# Singing requires a phoneme with an annotated pitch for each syllable.
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

# Sing the scale ascending in pitch.
song = ''.join(solfa)
speech.sing(song, speed=100)
# Reverse the list of syllables.
solfa.reverse()
song = ''.join(solfa)
# Sing the scale descending in pitch.
speech.sing(song, speed=100)
```






