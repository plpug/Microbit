#Pętle

Nie ma nic gorszego niż konieczność wielokrotnego wykonywania tej samej czynności. Pewnie dlatego prawdopodobnie wiele osób mając problem z zaśnięciem liczy barany. Nie ma to nic wspólnego z cudownymi właściwościami usapiającymi tych uroczych ssaków - powodem jest to, że ciągłe powatarzanie czegoś jest nużące, a umysłowi łatwiej się wyłączyć, jeśli tylko nie jest skupiony na czymś interesującym.

Ci programiści, którzy nie mają problemów z zaśnieciem również nieszczególnie przepadaja za powtarzaniem się. Dużym szczęściem jest, występowanie w większości języków programowania pętli for. Służy ona do automatycznego powtarzania innych instrukcji programistycznych i bloków kodu.

W tym rozdziale przyjrzymy się pętlom for, jak również innemu typowi pętli dostępnemu w języku Python: pętli while.

##Używanie pętli for

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

##Skoro już omawiamy pętle

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

#Podsumowanie

W tym rozdziale używaliśmy pętli, aby uniknąć znudzenia w trakci wykonywania monotonnych zadań: zapisaliśmy je w blokach i kazaliśmy Pythonowi je wykonywać wielokrotnie. Poznaliśmy dwa typy pętli `for` i `while`. Są one do siebie podobne, lecz można ich używać w różny sposób.



