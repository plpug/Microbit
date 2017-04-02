# Instalacja

Do warsztatów będziemy potrzebować wersji Pythona 3.4. Poniżej znajdują się wskazówki do tego, jak zainstalować środowisko oraz inne potrzebne narzędzia.

## Windows

Możesz ściągnąć Pythona pod Windows [z tej strony](https://www.python.org/downloads/). Po pobraniu pliku `*.msi`, uruchom go (klikając dwukrotnie na niego) i postępuj według wyświetlanych instrukcji. Koniecznie zapamiętaj ścieżkę (katalog), w którym zainstalowałaś Pythona. Będzie Ci niebawem potrzebna!

Należy zwrócić uwagę na jedno: na drugiej stronie instalatora nazwanej "Customize" ("Dostosuj do potrzeb") przewiń na sam dół i wybierz "Add python.exe to the Path" ("Dodaj python.exe do ścieżki systemowej"), tak jak na poniższym obrazku:

![zrzut ekranu][zrzut]

[zrzut]: https://github.com/plpug/Microbit/raw/master/chapter00/img/1.png "zrzut ekranu"

## Linux
Jest bardzo prawdopodobne, że masz już zainstalowanego Pythona wraz z systemem. Aby się upewnić (a także sprawdzić jego wersję) otwórz konsolę i wpisz następujące polecenie:
```markdown
$ python3 --version
Python 3.4.3
```
Nie masz Pythona? A może chciałbyś zainstalować inną jego wersje, w tej sytuacji skorzstaj z poniższych sposobów:

### Debian lub Ubuntu

Wpisz w konsoli poniższe polecenie:
```markdown
$ sudo apt-get install python3.4
```

### Fedora (do 21)

Użyj następującego polecenia w konsoli:
```markdown
$ sudo yum install python3.4
```
### Fedora (22+)

Użyj następującego polecenia w konsoli:
```markdown
$ sudo dnf install python3.4
```
### openSUSE

Użyj następującego polecenia w konsoli:
```markdown
$ sudo zypper install python3
```
### OS X

Przejdź na stronę https://www.python.org/downloads/release/python-343/ i pobierz instalator Pythona:

1. Pobierz plik o nazwie Mac OS X 64-bit/32-bit installer,
2. Kliknij dwukrotnie na python-3.4.3-macosx10.6.pkg, by uruchomić instalator.

Sprawdź, czy instalacja zakończyła się pomyślnie - otwórz aplikację Terminal i uruchom polecenie python3:
```markdown
$ python3 --version
Python 3.4.3
```
W razie jakichkolwiek wątpliwości albo jeśli coś poszło nie tak i nie wiesz, co dalej robić - po prostu zapytaj osobę prowadzącą kurs. Czasami nie wszystko idzie tak, jak powinno i najlepszym wyjściem z sytuacji jest poprosić o pomoc kogoś bardziej doświadczonego.
