# Pętle

Nie ma nic gorszego niż konieczność wielokrotnego wykonywania tej samej czynności. Pewnie dlatego prawdopodobnie wiele osób mając problem z zaśnięciem liczy barany. Nie ma to nic wspólnego z cudownymi właściwościami usapiającymi tych uroczych ssaków - powodem jest to, że ciągłe powatarzanie czegoś jest nużące, a umysłowi łatwiej się wyłączyć, jeśli tylko nie jest skupiony na czymś interesującym.

Ci programiści, którzy nie mają problemów z zaśnieciem również nieszczególnie przepadaja za powtarzaniem się. Dużym szczęściem jest, występowanie w większości języków programowania pętli for. Służy ona do automatycznego powtarzania innych instrukcji programistycznych i bloków kodu.

W tym rozdziale przyjrzymy się pętlom for, jak również innemu typowi pętli dostępnemu w języku Python: pętli while.

## Używanie pętli for

Aby pięciokrotnie wyświetlić słowo cześć w Pythonie, możemy napisać:

```markdown
>>>print("cześć")
cześć
>>>print("cześć")
cześć
>>>print("cześć")
cześć
>>>print("cześć")
cześć
>>>print("cześć")
cześć
```

Ale jest to raczej męczące. Aby się nie męczyć, możemy użyć pętli for, aby zmniejszyć ilość pisania oraz powtarzania:
```markdown
>>> for x in range (0,5):
...     print("cześć")
...
cześć
cześć
cześć
cześć
cześć
```
Jak widzicie użyliśmy funkcji range, można jej użyć do utworzenia listy liczb z przedziału od liczby początkowej do liczby o 1 mniejszej od liczby końcowej. Zdaję sobie sprawę z tego, że może brzmieć to trochę niejasno, więc połączmy funkcję range z funkcją list, aby dowiedzieć się, jak to działa. Funkcja range w zasadzie nie tworzy listy liczb, ale zwraca tzw. iterator, czyli typ obiektu w języku Python, który został zaprojektowany z myślą o pętlach.

Gdy jednak połączymy funkcję range z funkcją list, uzyskamy listę z liczbami:
```
>>> print(list(range(10,20)))
[10, 11, 12, 13, 14, 15, 16, 17, 18, 19]
>>>
```
W przypadki pętli for, kod tak naprawdę nakazuje Pythonowi wykonać pewne zadania:
* Rozpocząc odliczanie od 0 i zakończyć przed dotarciem do 5
* Wartość każdej kolejnej wyliczanej liczby zapisywać w zmiennej x.

Następnie Python wykonuje blok kodu. Zwróc uwagę, że na początku tego wiersza znajdują się cztery dodatkowe spacje. Gdybyśmy wpisali kod w środowisku programistycznym (IDLE), wcięcia wykonywane byłyby automatycznie.

Gdy wciśniemy ENTER po wpisaniu drugiego wiersza, program pięć razy wyświetli nam "cześć". Możemy nawet zliczyć, używając x w naszej instrukcji print:
```markdown
>>> for x in range(0,5):
...     print("cześć %s" %x)
...
cześć 0
cześć 1
cześć 2
cześć 3
cześć 4
```

Dla porównania zauważmy, jeżeli znów pozbędziemy się pętli for, nasz kod może wyglądać mniej więcej tak:

```markdown
>>> x=0
>>> print("cześć %s" %x)
cześć 0
>>> x=1
>>> print("cześć %s" %x)
cześć 1
>>> x=2
>>> print("cześć %s" %x)
cześć 2
>>> x=3
>>> print("cześć %s" %x)
cześć 3
>>> x=4
>>> print("cześć %s" %x)
cześć 4
>>>
```
W ten sposób użycie pętli uchroniło nas tak naprawdę przed pisaniem ośmiu dodatkowych wierszy kodu. Programiści nie cierpią się powtarzać, dlatego pętla for należy do najpopularniejszych instrukcji w językach programowania.

## Choinka

Zbliżają się Święta, czas na prezenty ;) A przynajmniej na drzweka iglaste
w każdym centrum handlowym. W ramach ćwiczenia spróbujemy narysować
takie drzewko w konsoli.

Zaczniemy od najprostszej możliwej wersji zadania, aby później rozszerzyć
je do bardziej funkcjonalnej. Tak więc na zachętę, pół choinki:


    print("*")
    print("**")
    print("***")
    print("*")
    print("**")
    print("***")
    print("****")
    print("*")
    print("**")
    print("***")
    print("****")
    print("*****")
    print("******")

Nasza choinka wygląda tak:

    *
    **
    ***
    *
    **
    ***
    ****
    *
    **
    ***
    ****
    *****
    ******

Nie wygląda to najgorzej, ale trochę pisania było. A co gdybyśmy chcieli
mniejszą choinkę ? Albo większą, złożoną z setek elementów do wydrukowania
na papierze A0 ? To stanowczo zbyt dużo pisania, nawet gdyby robić to
przy użyciu mnożenia napisów (``"*" * 100``, itd.). Ewidentnie jest to
czynność tak powtarzalna, że program może to zrobić za nas.


## Listy i pętla ``for``


Do wykonywania takich powtarzalnych czynności będą służyły nam pętle.
Pozostając w konwencji świątecznej, wyobraźmy sobie na chwilę, że
jesteśmy Świętym Mikołajem, który ma za zadanie dostarczyć wszystkim
prezenty.

Jak wiadomo, Mikołaj posiada listę osób, którym prezenty
się należa. Najprostszym podejściem, które gwarantuję, że nikogo nie
pominiemy będzie przechodzenie po kolei po liście i dostarczanie kolejnym
osobom ich prezentów. Abstrahując od fizycznych aspektów zadania [#speed]_,
procedura dostarczania prezentów mogłaby wygląć tak:

    Niech ListaOsób zawiera osoby którym należy się prezent.

    Dla każdej osoby (dalej znanej jako Osoba), będącej na ListaOsób:
        Dostarcz prezent do Osoba

Formatowanie powyższego tekstu nie jest przypadkowe. Właściwie jest
to zamaskowany program w Pythonie:

    gift_list = people_who_deserve_gifts()

    for person in gift_list:
        deliver_gift(person)
        print("Dostarczono prezent dla:", person)
    print("Dostarczono wszystkie prezenty")

Większość rzeczy powinna już wyglądać znajomo. Wywołujemy tutaj dwie funkcje:
`people_who_deserve_gifts` i `deliver_gift` - jak one działają,
wie tylko Mikołaj. Wynikowi wywołania pierwszej z nich nadajemy nazwę
`gift_list`, aby móc się później do tej wartości odwołać (tak samo jak w opisie powyżej).

Nowym elementem jest sama pętla, która składa się z:

* Słowa`for`
* Nazwy którą chcemy nadawać kolejnym elementom.
* Słowa`in`
* Wartości będącej listą lub nazwy która się do takiej odwołuje.
* Treści wciętej o jeden poziom (dokładnie tak samo jak to było w przypadku`if`)

No tak, ale jeszcze nic nie powiedzieliśmy o listach. To dlatego, że
nie różnią się one zbytnio od ich intuicyjnego pojmowania w życiu
codziennym. Spokojnie możemy myśleć o listach w Pythonie myśleć tak samo,
jak o każdej innej liście (zakupów, gości na impreze, wyników z kolokwium, itd.)
zapisanej na kartce i ponumerowanej.

Tak więc zacznijmy od pustej kartki (włącz tryb interaktywny):

    >>> L = []
    >>> L
    []

W każdym momencie możemy sprawdzić ile mamy zapisanych elementów
na naszej liście za pomocą funkcji:`len`.

    >>> len(L)
    0

Stwórzmy inną listę (może być pod tą samą nazwą lub inną):

    >>> L = ["Ala", "Ola", "Jacek"]
    >>> len(L)
    3

Podobnie jak w przypadku krotek, kolejne elementy listy rozdzielamy
przecinkami. W przeciwieństwie do krotek, nawiasy ``[`` i ``]`` są obowiązkowe.

Aby podejrzeć jaki element znajduje się na konkretnej pozycji na
liście (pamiętaj, że liczymy pozycje od 0):

    >>> L[0]
    'Ala'
    >>> L[1]
    'Ola'
    >>> L[2]
    'Jacek'
    >>> L[3]
    Traceback (most recent call last):
     File "<stdin>", line 1, in <module>
    IndexError: list index out of range

Możemy też wykorzystać pętle `for`, aby wykonać jakieś
instrukcje dla każdej jej elementu:

    >>> for name in L:
    ...     print("Imie:", name)
    ...
    Imie: Ala
    Imie: Ola
    Imie: Jacek

W ten sam sposób możemy wydrukować pierwszą cześć naszej pół-choinki:

    >>> lst = [1, 2, 3]
    >>> for n in lst:
    ...     print("*"*n)
    ...
    *
    **
    ***

No tak, ale nadal musieliśmy ręcznie wypisać zawartość całej listy.
Problem ten rozwiąże nam funkcja `range` (czyli zakres, przedział).
Jeśli opis podany przez ``help(range)`` wyda ci się zbyt skomplikowany, oto
kilka przykładów:

    >>> list(range(2, 5, 1))
    [2, 3, 4]
    >>> list(range(1, 11, 2))
    [1, 3, 5, 7, 9]
    >>> list(range(1, 11))
    [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
    >>> list(range(1, 2))
    [1]
    >>> list(range(2))
    [0, 1]

Funkcja `range` nie tworzy bezpośrednio listy, ale zwraca generator.
Generatory pozwalają tworzyć sekwencje wartości, nie zajmując nipotrzebnie
pamięci. Aby otrzymać listę z takiej sekwencji musimy użyć funkcji`list`.

Funkcja`range` ma trzy formy. Najprostrza (i najczęściej używana),
tworzy sekwencję od 0 do podanej liczby. Pozostałe formy pozwalają podać
początek zakresu oraz krok. Utworzona sekwencja nigdy nie zawiera końca
podanego zakresu.

Wydrukujmy więc większą choinkę:

    >>> lst = list(range(1, 11))
    >>> lst
    [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
    >>> for i in lst:
    ...     print("*"*i)
    *
    **
    ***
    ****
    *****
    ******
    *******
    ********
    *********
    **********

`range` zaoczszędziło nam sporo pisania. Możemy zaoszczędzić
jeszcze więcej pomijając nazywanie samej listy:

    >>> for i in list(range(1, 5)):
    ...     print(i*"#")
    #
    ##
    ###
    ####

Gdy używamy słowa kluczowego`for`, nie musimy używać funkcji
`list`. `for` potrafi poradzić sobie z funkcją `range`, więc
można nasz program jeszcze uprościć:

    >>> for i in range(1, 5):
    ...     print(i*"#")
    #
    ##
    ###
    ####


Nic nie stoi na przeszkodzie aby pętla nie mogła się znajdować
w innej pętli. Należy jedynie pamiętać o odpowiednich wcięciach i
użyciu innych nazw, np. ``i`` i ``j`` (lub też bardziej adekwatnych do
zawartości listy):

    >>> for i in range(1, 3):
    ...    for j in range(2, 4):
    ...        print(i, j)
    1 2
    1 3
    2 2
    2 3

Korzystając z tej techniki możemy powtarzać nasz kawałek choinki:

    >>> for i in range(3): # powtórz 3 razy
    ...    for size in range(1, 4):
    ...        print(size*"*")
    *
    **
    ***
    *
    **
    ***
    *
    **
    ***

### Zadanie 
Zanim przejdziesz do kolejnego punktu, stwórz plik ``xmas.py`` z
tym programem i spróbuj go przerobić tak aby przy każdym z trzech powtórzeń
pierwszej (zewnętrznej) pętli, druga wykonywała się raz więcej. W ten sposób
powinniśmy otrzymać naszą pół-choinkę z początku rozdziału.


## Skoro już omawiamy pętle

Pętla `for` nie jest jedyną pętlą dostępną w Pythonie, jest tu też `while`. Pętla `for` to pętla o określonej długości, natomiast pętli `while` używa się, gdy nie wiadomo zawczasu, kiedy trzeba będzie przestać wykonywać pętle.

Wyobraźcie sobie schody z 20 stopniami. Schody znajdują się wewnątrz budynku, Ty wiesz że na nie się wespniesz. Tak właśnie działa pętla for:
```markdown
>>> for stopien in range (0,20):
...     print(stopien)
```

A teraz wyobraź sobie schody prowadzące zboczem jakiejś wielkiej góry, wiesz, że w trakcie wspinania się możesz opaść z sił lub pogoda się nagle popsuje. Tak właśnie wygląda pętla `while`.

``` markdown
stopień = 0
while stopień <10000:
    print(stopień)

if zmęczenie == True:
    break
elif brzydkaPogoda == True:
    break
else:
    stopień = stopień +1
```

Jeśli przepiszesz i spróbujesz uruchomić ten kod, pojawi Ci się błąd. Wiesz dlaczego? Przyczyną jest to, że nie utworzyliśmy zmiennych zmęczenie i brzydkaPogoda. Ale pomimo braków w kodzie, uniemożliwiając jego wykonanie podstawowa zasada działania pętli while została zaprezentowana.

Zacznamy od stworzenia zmiennej `stopień`, za pomocą instrukcji `stopień = 0`. Następnie tworzymy pętle `while`, która sprawdza czy wartość zmiennej `stopień` jest mniejsza niż 10 000 ( `stopień < 10000`). 10 000 to całkowita liczba stopni od podnóża do wierzchołka góry. Python będzie wykonywać pozostałą część kodu tak długo, jak długo wartość zmiennej `stopień` będzie mniejsza niż 10 000.

Za pomocą instrukcji `print(stopień)` wyświetlamy wartość zmiennej, a następnie za pomocą `if zmęczenie == True` sprawdzamy czy wartość zmiennej zmęczenie to true. Jeśli tak, to używając słowa kluczowego `break`, wychodzimy z pętli. Słowo kluczowe `break` jest sposobem na natychmiastowe przerwanie pętli.

## Zadanie
Napisz pętle, która wyświetla wszystkie liczby parzyste mniejsze i równe Twojemu wiekowi (jeśli Twój wiek to liczba nieparzysta, wszystkie liczby nieparzyste mniejsze niż Twój wiek).

# Podsumowanie

W tym rozdziale używaliśmy pętli, aby uniknąć znudzenia w trakci wykonywania monotonnych zadań: zapisaliśmy je w blokach i kazaliśmy Pythonowi je wykonywać wielokrotnie. Poznaliśmy dwa typy pętli `for` i `while`. Są one do siebie podobne, lecz można ich używać w różny sposób.
