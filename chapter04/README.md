# Funkcje i modu³y

Zastanów siê, ile rzeczy wyrzucasz ka¿dego dnia: butelki po wodzie, torebki po chipsach, pude³ka po lodach, gazety itd. A teraz wyobraŸ sobie, co by siê sta³o, gdyby wszystkie te œmieci l¹dowa³y
po prostu na stosie na podjeŸdzie do Twojego domu, bez segregowania papieru, plastiku i aluminiowych puszek.

Jestem pewna, ¿e w miare mo¿liwoœci segregujesz odpady i to siê chwali, poniewa¿ nikt nie lubi w drodze do szko³y przedzieradŸ siê przez górê œmieci. Znacznie lepiej jest, jeœli te wszystkie
niepotrzebne, szklane pojemniki zostan¹ przetopione na nowe s³oiki czy butelki, jeœli makulatora zostanie przemielona na papier makulatorowy, a plastik na przerobiony na inne wyroby plastikowe.

W ten sposób ponownie wykorzystujemy ró¿ne rzeczy, które w przeciwnym razie l¹dowa³yby na coraz wy¿szym poziomie œmieci. W œwiecie programowania zada powtórnego wykorzystywania jest równie wa¿na.
Oczywiœcie programy nie znikaj¹ pod gór¹ œmieci, ale jeœli nie bêdziemy w jakimœ stopniu wielokrotnie wykorzystywaæ tego, co ju¿ mamy, to od ci¹g³ego
przepisywania kodu zatrzemy sobie palce. Powtórne wykorzystanie kodu to równie¿ krótsze i ³atwiejsze do czytania programy. Jeœli siê wkrótce przekonasz w Pythonie jest kilka sposobów tworzenia kodu
wielokrotnego u¿ytku.

## U¿ywanie funkcji

Jeden ze sposobów na wielokrone u¿ywanie kody Pythona ju¿ znamy. W poprzednim rozdziale u¿yliœmy funkcji `range` i `list`, aby nakazaæ Pythonowi liczenie:

```markdown
>>> list(range(0,5))
[0, 1, 2, 3, 4]
>>>
```

Ka¿dy, kto potrafi liczyæ, poradzi sobie z napisaniem listy zawieraj¹cej kolejne liczby, po prostu je wypisuj¹c, ale im d³u¿sza lista, tym wiêcej pisaniny. Dziêki funkcjom utworzenie
lisy zawieraj¹cej tysi¹ce pozycji nie jest niczym trudnym.
Poni¿ej generujemy listê liczb za pomoc¹ funkcji `list` i `range`:

```markdown
>>> list(range(0,1000))
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28, 29, 30, 31, 3
7, 78, 79, 80, 81, 82, 83, 84, 85, 86, 87, 88, 89, 90, 91, 92, 93, 94, 95, 96, 97, 98, 99, 100, 101, 102, 103, 104, 105,
 142, 143, 144, 145, 146, 147, 148, 149, 150, 151, 152, 153, 154, 155, 156, 157, 158, 159, 160, 161, 162, 163, 164, 165,
 202, 203, 204, 205, 206, 207, 208, 209, 210, 211, 212, 213, 214, 215, 216, 217, 218, 219, 220, 221, 222, 223, 224, 225,
 262, 263, 264, 265, 266, 267, 268, 269, 270, 271, 272, 273, 274, 275, 276, 277, 278, 279, 280, 281, 282, 283, 284, 285,
 322, 323, 324, 325, 326, 327, 328, 329, 330, 331, 332, 333, 334, 335, 336, 337, 338, 339, 340, 341, 342, 343, 344, 345,
 382, 383, 384, 385, 386, 387, 388, 389, 390, 391, 392, 393, 394, 395, 396, 397, 398, 399, 400, 401, 402, 403, 404, 405,
 442, 443, 444, 445, 446, 447, 448, 449, 450, 451, 452, 453, 454, 455, 456, 457, 458, 459, 460, 461, 462, 463, 464, 465,
 502, 503, 504, 505, 506, 507, 508, 509, 510, 511, 512, 513, 514, 515, 516, 517, 518, 519, 520, 521, 522, 523, 524, 525,
 562, 563, 564, 565, 566, 567, 568, 569, 570, 571, 572, 573, 574, 575, 576, 577, 578, 579, 580, 581, 582, 583, 584, 585,
 622, 623, 624, 625, 626, 627, 628, 629, 630, 631, 632, 633, 634, 635, 636, 637, 638, 639, 640, 641, 642, 643, 644, 645,
 682, 683, 684, 685, 686, 687, 688, 689, 690, 691, 692, 693, 694, 695, 696, 697, 698, 699, 700, 701, 702, 703, 704, 705,
 742, 743, 744, 745, 746, 747, 748, 749, 750, 751, 752, 753, 754, 755, 756, 757, 758, 759, 760, 761, 762, 763, 764, 765,
 802, 803, 804, 805, 806, 807, 808, 809, 810, 811, 812, 813, 814, 815, 816, 817, 818, 819, 820, 821, 822, 823, 824, 825,
 862, 863, 864, 865, 866, 867, 868, 869, 870, 871, 872, 873, 874, 875, 876, 877, 878, 879, 880, 881, 882, 883, 884, 885,
 922, 923, 924, 925, 926, 927, 928, 929, 930, 931, 932, 933, 934, 935, 936, 937, 938, 939, 940, 941, 942, 943, 944, 945,
 982, 983, 984, 985, 986, 987, 988, 989, 990, 991, 992, 993, 994, 995, 996, 997, 998, 999]
>>>
```

Funkcje to fragmenty kodu, które nakazuj¹ Pythonowi wykonaæ jakieœ zadanie. Jest to jeden ze sposobów na wielokrotne wykorzystywanie kodu - funkcji mo¿na wielkrotnie u¿ywaæ w ró¿nych programach.
Przydatnoœæ funkcji widaæ ju¿ przy pisaniu prostych programów. Gdy zaczniesz pisaæ d³ugie pisaæ d³ugie, bardziej skomplikowane aplikacje, takie jak gry, przekonasz siê funkcje s¹ niezast¹opione.

## Budowa funkcji

Funkcja sk³ada siê trzech czêœci: nazwy, parametrów i treœci. Oto przyk³ad prostej funkcji:

```markdown
>>>
>>> def funkcjaTestowa(mojeImie):
...     print("Witaj %s" %mojeImie)
```

Nazwa funkcji to `funkcjaTestowa`. Ma ona jeden parametr, `mojeImie`, a jej treœci¹ jest blok kodu znajduj¹cy siê bezpoœrednio pod wierszem zaczynaj¹cym siê od `def`.
Aby wykonaæ funkcjê, nale¿y j¹ wywo³aæ, podaj¹c kolejno jej nazwê i wartoœæ parametru w nawiasach:

```markdown
>>> funkcjaTestowa("Marta")
Witaj Marta
```

Mo¿emy te¿ najpierw utworzyæ kilka zmiennych, a nastêpnie wywo³aæ funkcje, podaj¹c ich nazwy jako parametry:

```markdown
>>> imie = "Robin"
>>> nazwisko= "Hood"
>>> funkcjaTestowa(imie, nazwisko)
Witaj Robin Hood
```

## Zmienne i ich zasiêg

Zmienna, która znajduje siê w treœci funkcji, wystêpuje tylko w tej funkcji i nie mo¿e zostaæ u¿yta po zakoñczeniu wykonywania funkcji.
W œwiecie programowania regu³ê tak¹ nazywamy zasiêgiem. Spójrzmy na funkcje, która nie ma ¿adnych parametrów, ale u¿ywa kilku zmiennych:

```markdown
def testuj_zmienne():
    zmienna_pierwsza = 10
    zmienna_druga = 21
    return zmienna_pierwsza * zmienna_druga
```

W przyk³adzie tym tworzymy funkcje `testuj_zmienne`, która mno¿y dwie zmienne ( zmienna_pierwsza i zmienna_druga) i zwraca wynik w kroku.

```markdown
print(testuj_zmienne())
200
```

Jeœli wywo³amy tê funkcje za pomoc¹ print, uzyskamy wynik 200. Jeœli jednak bêdziemy chcieli wyœwietliæ zawartoœæ `pierwsza_zmienna` poza blokiem kodu funkcji, zobaczymy b³¹d.

Zmienna zdefiniowana poza funkcj¹ ma zupe³nie inny zasiêg.

Aby siê o tym przekonaæ, zdefiniujemy zmienn¹ przed utworzeniem funkcji, a nastêpnie spróbujemy u¿yæ w niej tej zmiennej:

```markdown
kolejna_zmienna = 100
def testuj_zmienne2():
    zmienna_pierwsza = 10
    zmienna_druga = 21
    return zmienna_pierwsza * zmienna_druga * kolejna_zmienna
```
W tym kodzie zmienne `zmienna_pierwsza` i `zmienna_druga` nadal nie mog¹ byæ u¿ywane poa funkcj¹, natomiast zmienna `kolejna_zmienna` mo¿e byæ u¿ywana
na wewn¹trz funkcji. Oto wynik dzia³ania tej funkcji:

```markdown
>>>print(testuj_zmienna2())
2000
```


## U¿ywanie modu³ów

Modu³y s³u¿¹ do organizowania funkcji, zmiennych i innych elementów kodu w wiêksze programy, które daj¹ wiêcej mo¿liwoœci. Niektóre z nich s¹ wbudowane w Pythona, inne z kolei s¹
niezale¿ne i mo¿na je pobraæ. Istniej¹ modu³y pomagaj¹ce w pisaniu gier (np. zewn¹trzny PyGdame), modu³y u³atwiaj¹ce obróbkê obrazków( np. PIL czyli Python Imaging Library) i do rysowania trójwymiarowej grafiki (np. Panda3D).

Modu³y mo¿na u¿ywaæ do ró¿nych zadañ. Przyk³adowo gdybyœmy chcieli zrobiæ jak¹œ symulacje gry, moglibyœmy obliczaæ bie¿¹c¹ date i czas, u¿ywaj¹c wbudowanego modu³u:

```markdown
>>> import time
```
W tym przypadku polecenie `import` informuje Pythona, ¿e chcemy u¿ywaæ modu³u `time`. Od tego momentu za pomoc¹ symbolu `.` (kropki) mo¿emy wywo³ywaæ dostêpne w danym module funkcje.
Oto przyk³adowe wywo³anie funkcji `asctime` w module `time`.

```markdown
>>> print(time.asctime())
Fri Mar  3 17:00:45 2017
>>>
```

Funkcja `asctime` jest czêœci¹ modu³u `time` i zwraca bie¿¹c¹ date i czas pod postaci¹ ³añcuchu znaków.


## Podsumowanie

W tym rozdziale dowiedzieliœmy siê, jak tworzyæ w Pythonie bloki kodu wielokrotnego u¿ytku zwane funkcjami. Wiesz, ¿e od zasiêgu zmiennych zale¿y to, czy mo¿na ich u¿ywaæ wewn¹trz funkcji czy na zewn¹trz i potrafisz tworzyæ funkcje od s³owa kluczowego `def`. Umiesz te¿ importowaæ modu³y, aby wykorzystywaæ to co siê w nich znajduje.





