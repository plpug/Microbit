# Muzyka 

MicroPython na płytce BBC micro:bit przychodzi z potężnym modułem
muzyczno-dźwiękowym.
Umożliwia on w bardzo prosty sposób generowanie pisków i brzdęków z
użądzenia, jeśli podłączy
się pod nie głośnik. Użyj krokodylków by podpiąć piny 0 i GND do wejść głośnika.
Nie ma znaczenia kierunek w którym są one podłączone pod głośnik.

Uwaga: Nie próbuj tego z piezo elektrycznym brzęczykiem - takie
brzęczyki są przystosowane
do grania jedynie pojedyńczego tonu.

Przystąpmy zatem do grania jakiejś muzyki:
...

Zauważ, że zaimportowaliśmy moduł "music". Zawiera on metody użyte do
wytworzenia i kontrolowania dźwięku.

MikroPython ma całkiem sporo wbudowanych melodii. Ich kompletna lista to:
...

Teraz ponownie weź przykładowy kod i zmień w nim melodię. Która z nich
jest twoją ulubioną?
W jaki sposób użył byś takich melodyjek by coś zasygnalizować bądź wskazać?


Wolfgang Amadeusz Microbit

Tworzenie własnych melodyjek jest proste!

Każda nuta ma swoją nazwę (jak C#, czy F), oktawę (mówiącą MicroPythonowi jak
wysoko lub nisko powinien zagrać tą nutę) i okres trwania (jak długo powinna
ona wybrzmiewać). Oktawy oznaczone są liczbami - 0 jest najniższą oktawą,
zawiera środkowe C, a 8 jest najwyższą jaką będziesz kiedykolwiek potrzebować,
chyba że tworzysz muzykę dla psów. Okres trwania również wyrażony jest liczbami.
Im większa wartość, tym dłużej będzie on trwać. Wartości te odnoszą
się do siebie,
dla przykładu okres trwania o wartości 4 będzie trwać dwa razy dłużej niż okres
o wartości 2 (i tak dalej...).
Jeśli użyjesz nuty nazwanej "R", MicroPython przeczeka (tj. zamilknie) na zadany
okres trwania.

Każda nuta wyrażona jest jako ciąg znaków jak ten:

NUTA[oktawa][:okres trwania]

Dla przykładu "A1:4" odnosi się do nuty nazwanej A w oktawie o numerze 1, granej
przez czas o długości 4 jednostek.

Zrób listę nut by zapisać melodię (jest to odpowiednikiem tworzenia animacji
z listy obrazków). Przykładowo, w ten sposób MicroPython może zagrać
otwarcie "Frere Jaques":
```markdown
import music

tune = ["C4:4", "D4:4", "E4:4", "C4:4", "C4:4", "D4:4", "E4:4", "C4:4",
        "E4:4", "F4:4", "G4:8", "E4:4", "F4:4", "G4:8"]
music.play(tune)
```

Uwaga: MicroPython umożliwia uproszczenie takich melodii. Zapamięta on oktawę
i okres trwania do póki go nie zmienisz następnym razem. W wyniku powyższy
przykład może być przepisany tak:
...
Zauważ jak zmieniają się wartości oktaw i okresów trwania jedynie gdy muszą.
Zaoszczędza to sporo pisania jak i ułatwia czytanie.


Efekty dźwiękowe

MicroPython pozwala Ci wytważać tony który nie są muzycznymi nutami.
Dla przykładu,
w ten sposób możesz wytworzyć sygnał policyjnej syreny:
...

Zauważ jak w tym przykładzie użyta jest metoda "music.pitch". Oczekuje
ona częstotliwości.
Dla przykładu, częstotliwość 440 jest takasama jak koncertowy ton A,
używany do "zgrania się"
przez orkiestrę filharmonii.

W powyższym przykładzie funkcja "range" użyta jest do wygenerowania przedziału
wartości liczbowych. Te liczby użyte są do zdefiniowania wysokości
tonu. Trzy argumenty
funkcji "range" są: wartością początkową, końcową i wartością kroku. W
związku z tym
pierwsze użycie "range" mówi, w języku polskim: utwóż przedział
wartości pomiędzy 880 a 1760,
dodając co krok 16. Trugie użycie "range" mówi: utwóż przedział
wartości pomiędzy 1760 i 880,
dodając co krok -16 (czyli odejmując 16). W ten sposób otrzymujemy
przedział częstotliwości
zmieniając wysokość tonu tak jak syrena.

Jako że syrena powinna trwać bez końca otacza ją nieskończona pętla "while".

Najważniejsze w tym jest wprowadzenie nowego typu pętli wewnątrz pętli
"while" - pętla "for".
Po polsku powiedzielibyśmy "dla każdego elementu w pewnej kolekcji,
wykonaj z nią pewne działanie".
Po angielsku (na którym bazuje język Python) brzmi to "for each item
in some collection, do some
activity with it". Stąd mamy "for", "in". W naszym przykładzie to "dla
każdej częstotliwości (freq)
w przedziale (range) graj dzięk o tej częstotliwości przez 6 milisekund".
Zauważ że każda akcja do wykonania w pętli "for" ma wcięcie (zgodnie z
tym o czym rozmawialiśmy
wcześniej) dzięki czemu Python wie dokładnie jaki kod wykonać dla
poszczególnych elementów kolekcji.
