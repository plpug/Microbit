# Funkcje i moduły

Zastanów się, ile rzeczy wyrzucasz każdego dnia: butelki po wodzie, torebki po chipsach, pudełka po lodach, gazety itd. A teraz wyobraź sobie, co by się stało, gdyby wszystkie te śmieci lądowały
po prostu na stosie na podjeździe do Twojego domu, bez segregowania papieru, plastiku i aluminiowych puszek.

Jestem pewna, że w miare możliwości segregujesz odpady i to się chwali, ponieważ nikt nie lubi w drodze do szkoły przedzieradź się przez górę śmieci. Znacznie lepiej jest, jeśli te wszystkie
niepotrzebne, szklane pojemniki zostaną przetopione na nowe słoiki czy butelki, jeśli makulatora zostanie przemielona na papier makulatorowy, a plastik na przerobiony na inne wyroby plastikowe.

W ten sposób ponownie wykorzystujemy różne rzeczy, które w przeciwnym razie lądowałyby na coraz wyższym poziomie śmieci. W świecie programowania zada powtórnego wykorzystywania jest równie ważna.
Oczywiście programy nie znikają pod górą śmieci, ale jeśli nie będziemy w jakimś stopniu wielokrotnie wykorzystywać tego, co już mamy, to od ciągłego
przepisywania kodu zatrzemy sobie palce. Powtórne wykorzystanie kodu to również krótsze i łatwiejsze do czytania programy. Jeśli się wkrótce przekonasz w Pythonie jest kilka sposobów tworzenia kodu
wielokrotnego użytku.

## Używanie funkcji

Jeden ze sposobów na wielokrone używanie kody Pythona już znamy. W poprzednim rozdziale użyliśmy funkcji `range` i `list`, aby nakazać Pythonowi liczenie:

```python
>>> list(range(0,5))
[0, 1, 2, 3, 4]
>>>
```

Każdy, kto potrafi liczyć, poradzi sobie z napisaniem listy zawierającej kolejne liczby, po prostu je wypisując, ale im dłuższa lista, tym więcej pisaniny. Dzięki funkcjom utworzenie
lisy zawierającej tysiące pozycji nie jest niczym trudnym.
Poniżej generujemy listę liczb za pomocą funkcji `list` i `range`:

```python
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

Funkcje to fragmenty kodu, które nakazują Pythonowi wykonać jakieś zadanie. Jest to jeden ze sposobów na wielokrotne wykorzystywanie kodu - funkcji można wielkrotnie używać w różnych programach.
Przydatność funkcji widać już przy pisaniu prostych programów. Gdy zaczniesz pisać długie pisać długie, bardziej skomplikowane aplikacje, takie jak gry, przekonasz się funkcje są niezastąopione.

## Budowa funkcji

Funkcja składa się trzech części: nazwy, parametrów i treści. Oto przykład prostej funkcji:

```python
>>>
>>> def funkcjaTestowa(mojeImie):
...     print("Witaj %s" %mojeImie)
```

Nazwa funkcji to `funkcjaTestowa`. Ma ona jeden parametr, `mojeImie`, a jej treścią jest blok kodu znajdujący się bezpośrednio pod wierszem zaczynającym się od `def`.
Aby wykonać funkcję, należy ją wywołać, podając kolejno jej nazwę i wartość parametru w nawiasach:

```python
>>> funkcjaTestowa("Marta")
Witaj Marta
```

Możemy też najpierw utworzyć kilka zmiennych, a następnie wywołać funkcje, podając ich nazwy jako parametry:

```python
>>> imie = "Robin"
>>> nazwisko= "Hood"
>>> funkcjaTestowa(imie, nazwisko)
Witaj Robin Hood
```

## Zmienne i ich zasięg

Zmienna, która znajduje się w treści funkcji, występuje tylko w tej funkcji i nie może zostać użyta po zakończeniu wykonywania funkcji.
W świecie programowania regułę taką nazywamy zasięgiem. Spójrzmy na funkcje, która nie ma żadnych parametrów, ale używa kilku zmiennych:

```python
def testuj_zmienne():
    zmienna_pierwsza = 10
    zmienna_druga = 21
    return zmienna_pierwsza * zmienna_druga
```

W przykładzie tym tworzymy funkcje `testuj_zmienne`, która mnoży dwie zmienne ( zmienna_pierwsza i zmienna_druga) i zwraca wynik w kroku.

```python
print(testuj_zmienne())
200
```

Jeśli wywołamy tę funkcje za pomocą print, uzyskamy wynik 200. Jeśli jednak będziemy chcieli wyświetlić zawartość `pierwsza_zmienna` poza blokiem kodu funkcji, zobaczymy błąd.

Zmienna zdefiniowana poza funkcją ma zupełnie inny zasięg.

Aby się o tym przekonać, zdefiniujemy zmienną przed utworzeniem funkcji, a następnie spróbujemy użyć w niej tej zmiennej:

```python
kolejna_zmienna = 100
def testuj_zmienne2():
    zmienna_pierwsza = 10
    zmienna_druga = 21
    return zmienna_pierwsza * zmienna_druga * kolejna_zmienna
```
W tym kodzie zmienne `zmienna_pierwsza` i `zmienna_druga` nadal nie mogą być używane poa funkcją, natomiast zmienna `kolejna_zmienna` może być używana
na wewnątrz funkcji. Oto wynik działania tej funkcji:

```python
>>>print(testuj_zmienna2())
2000
```

## Używanie modułów

Moduły służą do organizowania funkcji, zmiennych i innych elementów kodu w większe programy, które dają więcej możliwości. Niektóre z nich są wbudowane w Pythona, inne z kolei są
niezależne i można je pobrać. Istnieją moduły pomagające w pisaniu gier (np. zewnątrzny PyGdame), moduły ułatwiające obróbkę obrazków( np. PIL czyli Python Imaging Library) i do rysowania trójwymiarowej grafiki (np. Panda3D).

Moduły można używać do różnych zadań. Przykładowo gdybyśmy chcieli zrobić jakąś symulacje gry, moglibyśmy obliczać bieżącą date i czas, używając wbudowanego modułu:

```python
>>> import time
```
W tym przypadku polecenie `import` informuje Pythona, że chcemy używać modułu `time`. Od tego momentu za pomocą symbolu `.` (kropki) możemy wywoływać dostępne w danym module funkcje.
Oto przykładowe wywołanie funkcji `asctime` w module `time`.

```python
>>> print(time.asctime())
Fri Mar  3 17:00:45 2017
>>>
```

Funkcja `asctime` jest częścią modułu `time` i zwraca bieżącą date i czas pod postacią łańcuchu znaków.

# Obiekty i klasy

Właściwie ten rozdział mógłby być tematem całej serii zajęć, my jednak
skupimy się na absolutnych podstawach.

## Wartości to obiekty
Wszystko co do tej pory nazywaliśmy wartością możemy nazwać też obiektem.
Widzieliśmy to na przykładzie liczb całkowitych, gdy `help` wypisało
nam dziesiątki linii dodatkowych informacji na temat `int`.

## Każdy obiekt ma klasę
Aby się dowiedzieć jaką wystarczy użyć funkcji`type`:

    >>> type(2)
    <type 'int'>
    >>> type(2.0)
    <type 'float'>
    >>> type("Gżegżółka")
    <type 'str'>
    >>> x = 1, 2
    >>> type(x)
    <type 'tuple'>
    >>> type([])
    <type 'list'>

Gdy używamy w naszym programie liczby, spodziewamy się, że będzie się
ona zachowywać tak jak liczba - bazujemy na naszej intuicji.

Jednak Python musi dokładnie wiedzieć co znaczy być liczbą całkowitą,
np. co ma się stać gdy dodajemy dwie liczby, a co gdy je dzielimy.
Klasa dostarcza tych wszystkich informacji i więcej.

Sprawdź co oferuje nam klasa ``str`` za pomocą`help`.
Zacytujemy tutaj jedynie kilka ciekawszych funkcji:

    >>> help(str.lower)
    Help on method_descriptor:
    <BLANKLINE>
    lower(...)
        S.lower() -> str
    <BLANKLINE>
        Return a copy of the string S converted to lowercase.
    <BLANKLINE>
    >>> help(str.upper)
    Help on method_descriptor:
    <BLANKLINE>
    upper(...)
        S.upper() -> str
    <BLANKLINE>
        Return a copy of S converted to uppercase.
    <BLANKLINE>
    >>> help(str.ljust)
    Help on method_descriptor:
    <BLANKLINE>
    ljust(...)
        S.ljust(width[, fillchar]) -> int
    <BLANKLINE>
        Return S left-justified in a Unicode string of length width. Padding is
        done using the specified fill character (default is a space).
    <BLANKLINE>
    >>> help(str.center)
    Help on method_descriptor:
    <BLANKLINE>
    center(...)
        S.center(width[, fillchar]) -> str
    <BLANKLINE>
        Return S centered in a Unicode string of length width. Padding is
        done using the specified fill character (default is a space)
    <BLANKLINE>

Wszystko to są operacje, które każdy napis potrafi wykonać. Możemy
się do nich dostać używając kropki i wywołując jak funkcję:

    >>> x = "Ala"
    >>> x.upper()
    u'ALA'
    >>> x.lower()
    u'ala'
    >>> x.center(9)
    u'   Ala   '

I jeszcze jedna istotna funkcjonalność każdej klasy - potrafi ona
stworzyć obiekt mający jej cechy (tzw. swoją instancję):

    >>> int()
    0
    >>> str()
    ''
    >>> list()
    []
    >>> tuple()
    ()

Podsumowując, poznaliśmy już klasy`int`,`str`,`tuple`,
`list`. Aby sprawdzić jakiej klasy jest wartość (obiekt) używamy funkcji
`type`. Aby stworzyć instancję klasy (czyli nowy obiekt) wywołujemy
klasę podobnie jak wywoływaliśmy funkcję, dopisując nawiasy ``()``, na przykład
``int()``.

## Definiowanie klass

Podobnie jak możemy tworzyć własne funkcje, tak i możemy tworzyć
własne klasy. W gruncie rzeczy, klasa to nic innego jak zgrupowane
funkcje:


    class Dog(object):

        def bark(self):
            print(u"Woof! Woof!")

::

    class Dog(object):

        def bark(self):
            print(u"Woof! Woof!")

Klasy rozpoczynają się od słowa`class`, po którym podajemy
nazwę nowej klasy. Czym jest ``(object)`` wyjaśni się później, gdy
będziemy chcieli stworzyć bardziej skomplikowane klasy.

Warto natomiast zwrócić uwagę na fakt, że każda funkcja w klasie musi mieć
conajmniej jeden argument. Jego wartością będzie obiekt z którego wywołaliśmy
tą funkcję (czyli to co przed kropką):

    burek = Dog()
    burek.bark()

Wynik:

    Woof! Woof!

Argument ten może nazywać się dowolnie, ale intuicyjne jest aby nazwać go ``self``.

## Atrybuty obiektów
Obiekty poza metodami (funckjami), mogą posiadać też atrybuty:

    burek = Dog()
    burek.name = "Burek"

    print(burek.name)

Wynik:

    Burek

Czasami chcemy aby każdy obiekt danej klasy miał jakiś atrybut, np. każdy
pies powinien mieć imię. Możemy dodać takie wymaganie definiując funkcję
o specjalnej nazwie ``__init__``:



    class Dog(object):

        def __init__(self, name):
            self.name = name

        def bark(self):
            return "Woof! %s! Woof!" % (self.name,)

    burek = Dog(u"Burek")
    pluto = Dog(u"Pluto")
    print(burek.bark())
    print(pluto.bark())

Wynik:

    Woof! Burek! Woof!
    Woof! Pluto! Woof!


## Zadania 

1. Napisz prostą grę, w której przeciwnikiem jest komputer,  która pozwala wybrać numer z zakresu:
* od 1 do 100 w pięciu próbach,
* od 1 do 7000 w siedmiu próbach,
* użytkownik może wybrać podpunkt a) lub b) , kiedy zacznie grę. 
Po zakończeniu gry powinna być informacja ile rozgrywek było rozegranych, ile wygranych, a ile przegranych.

2. Napisz prosty program który pozwoli uczyć się prostych japońskich słów. Dostarczamy plik jap_dict.txt (plik dostaniecie od mentora). 
Twoim zadaniem jest:

* użyć kopiuj+wklej na tekście z tego pliku, lub użyć funkcję open(file_name) aby pobrać dane, 
* przekształcić tekst na strukturę danych,
* zadać pytanie o tłumaczenie z angielskiego na japoński słowa lub frazy, 
* sprawdzić czy tłumaczenie zostało wykonane poprawnie, jeśli tak - nie pokazywać więcej już tego słowa, 
* poinformować ile słów jest odgadniętych i ile pozostało,
* opcjonalnie na końcu pogratulować, 
* wskazać różnice w pisowni.


