# Instalacja

Do warsztatów będziemy potrzebować wersji Pythona 3. Poniżej znajdują się wskazówki do tego, jak zainstalować środowisko oraz inne potrzebne narzędzia.

## Windows

Możesz ściągnąć Pythona pod Windows [z tej strony](https://www.python.org/downloads/). Po pobraniu pliku, uruchom go (klikając dwukrotnie na niego) i postępuj według wyświetlanych instrukcji.

Należy zwrócić uwagę żeby zaznaczyć opcję "Add python.exe to PATH" ("Dodaj python.exe do ścieżki systemowej"), tak jak na poniższym obrazku:

![zrzut ekranu][zrzut]

[zrzut]: https://github.com/plpug/Microbit/raw/master/chapter00/img/1.png "zrzut ekranu"

Następnie należy pobrać sterownik do portu szeregowego z https://os.mbed.com/handbook/Windows-serial-configuration klikając w link "Download latest driver" 

## Linux
Jest bardzo prawdopodobne, że masz już zainstalowanego Pythona wraz z systemem. Aby się upewnić (a także sprawdzić jego wersję) otwórz konsolę i wpisz następujące polecenie:
```sh
$ python3 --version
Python 3.4.3
```

Każda wersja większa lub równa 3.4 jest akceptowana.
Nie masz Pythona? A może chciałbyś zainstalować inną jego wersje, w tej sytuacji skorzstaj z poniższych sposobów:

### Debian lub Ubuntu

Wpisz w konsoli poniższe polecenie:
```sh
$ sudo apt-get install python3.4
```

### Fedora (do 21)

Użyj następującego polecenia w konsoli:
```sh
$ sudo yum install python3.4
```
### Fedora (22+)

Użyj następującego polecenia w konsoli:
```sh
$ sudo dnf install python3.4
```
### openSUSE

Użyj następującego polecenia w konsoli:
```sh
$ sudo zypper install python3
```
### OS X

Przejdź na stronę https://www.python.org/downloads/release/python-343/ i pobierz instalator Pythona:

1. Pobierz plik o nazwie Mac OS X 64-bit/32-bit installer,
2. Kliknij dwukrotnie na python-3.4.3-macosx10.6.pkg, by uruchomić instalator.

Sprawdź, czy instalacja zakończyła się pomyślnie - otwórz aplikację Terminal i uruchom polecenie python3:
```sh
$ python3 --version
Python 3.4.3
```
W razie jakichkolwiek wątpliwości albo jeśli coś poszło nie tak i nie wiesz, co dalej robić - po prostu zapytaj osobę prowadzącą kurs. Czasami nie wszystko idzie tak, jak powinno i najlepszym wyjściem z sytuacji jest poprosić o pomoc kogoś bardziej doświadczonego.

# Instalacja jupyter'a

Uruchum konsolę i wykonaj następujące komendy(na Linuksie w zależności od dystrybucji komenda python może być zastąpiona komendą python3)
```sh
python -m venv lab
pip install jupyterlab
pip install ubit_kernel
python -m ubit_kernel.install
```

## Uruchomienie

Przejdź do głównego katalogu kursu i uruchom środowisko.
```sh
jupyter lab
```