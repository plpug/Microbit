# Muzyka 

MicroPython na p³ytce BBC micro:bit przychodzi z potê¿nym modu³em
muzyczno-dŸwiêkowym.
Umo¿liwia on w bardzo prosty sposób generowanie pisków i brzdêków z
u¿¹dzenia, jeœli pod³¹czy
siê pod nie g³oœnik. U¿yj krokodylków by podpi¹æ piny 0 i GND do wejœæ g³oœnika.
Nie ma znaczenia kierunek w którym s¹ one pod³¹czone pod g³oœnik.

Uwaga: Nie próbuj tego z piezo elektrycznym brzêczykiem - takie
brzêczyki s¹ przystosowane
do grania jedynie pojedyñczego tonu.

Przyst¹pmy zatem do grania jakiejœ muzyki:
...

Zauwa¿, ¿e zaimportowaliœmy modu³ "music". Zawiera on metody u¿yte do
wytworzenia i kontrolowania dŸwiêku.

MikroPython ma ca³kiem sporo wbudowanych melodii. Ich kompletna lista to:
...

Teraz ponownie weŸ przyk³adowy kod i zmieñ w nim melodiê. Która z nich
jest twoj¹ ulubion¹?
W jaki sposób u¿y³ byœ takich melodyjek by coœ zasygnalizowaæ b¹dŸ wskazaæ?


Wolfgang Amadeusz Microbit

Tworzenie w³asnych melodyjek jest proste!

Ka¿da nuta ma swoj¹ nazwê (jak C#, czy F), oktawê (mówi¹c¹ MicroPythonowi jak
wysoko lub nisko powinien zagraæ t¹ nutê) i okres trwania (jak d³ugo powinna
ona wybrzmiewaæ). Oktawy oznaczone s¹ liczbami - 0 jest najni¿sz¹ oktaw¹,
zawiera œrodkowe C, a 8 jest najwy¿sz¹ jak¹ bêdziesz kiedykolwiek potrzebowaæ,
chyba ¿e tworzysz muzykê dla psów. Okres trwania równie¿ wyra¿ony jest liczbami.
Im wiêksza wartoœæ, tym d³u¿ej bêdzie on trwaæ. Wartoœci te odnosz¹
siê do siebie,
dla przyk³adu okres trwania o wartoœci 4 bêdzie trwaæ dwa razy d³u¿ej ni¿ okres
o wartoœci 2 (i tak dalej...).
Jeœli u¿yjesz nuty nazwanej "R", MicroPython przeczeka (tj. zamilknie) na zadany
okres trwania.

Ka¿da nuta wyra¿ona jest jako ci¹g znaków jak ten:

NUTA[oktawa][:okres trwania]

Dla przyk³adu "A1:4" odnosi siê do nuty nazwanej A w oktawie o numerze 1, granej
przez czas o d³ugoœci 4 jednostek.

Zrób listê nut by zapisaæ melodiê (jest to odpowiednikiem tworzenia animacji
z listy obrazków). Przyk³adowo, w ten sposób MicroPython mo¿e zagraæ
otwarcie "Frere Jaques":
...

Uwaga: MicroPython umo¿liwia uproszczenie takich melodii. Zapamiêta on oktawê
i okres trwania do póki go nie zmienisz nastêpnym razem. W wyniku powy¿szy
przyk³ad mo¿e byæ przepisany tak:
...
Zauwa¿ jak zmieniaj¹ siê wartoœci oktaw i okresów trwania jedynie gdy musz¹.
Zaoszczêdza to sporo pisania jak i u³atwia czytanie.


Efekty dŸwiêkowe

MicroPython pozwala Ci wytwa¿aæ tony który nie s¹ muzycznymi nutami.
Dla przyk³adu,
w ten sposób mo¿esz wytworzyæ sygna³ policyjnej syreny:
...

Zauwa¿ jak w tym przyk³adzie u¿yta jest metoda "music.pitch". Oczekuje
ona czêstotliwoœci.
Dla przyk³adu, czêstotliwoœæ 440 jest takasama jak koncertowy ton A,
u¿ywany do "zgrania siê"
przez orkiestrê filharmonii.

W powy¿szym przyk³adzie funkcja "range" u¿yta jest do wygenerowania przedzia³u
wartoœci liczbowych. Te liczby u¿yte s¹ do zdefiniowania wysokoœci
tonu. Trzy argumenty
funkcji "range" s¹: wartoœci¹ pocz¹tkow¹, koñcow¹ i wartoœci¹ kroku. W
zwi¹zku z tym
pierwsze u¿ycie "range" mówi, w jêzyku polskim: utwó¿ przedzia³
wartoœci pomiêdzy 880 a 1760,
dodaj¹c co krok 16. Trugie u¿ycie "range" mówi: utwó¿ przedzia³
wartoœci pomiêdzy 1760 i 880,
dodaj¹c co krok -16 (czyli odejmuj¹c 16). W ten sposób otrzymujemy
przedzia³ czêstotliwoœci
zmieniaj¹c wysokoœæ tonu tak jak syrena.

Jako ¿e syrena powinna trwaæ bez koñca otacza j¹ nieskoñczona pêtla "while".

Najwa¿niejsze w tym jest wprowadzenie nowego typu pêtli wewn¹trz pêtli
"while" - pêtla "for".
Po polsku powiedzielibyœmy "dla ka¿dego elementu w pewnej kolekcji,
wykonaj z ni¹ pewne dzia³anie".
Po angielsku (na którym bazuje jêzyk Python) brzmi to "for each item
in some collection, do some
activity with it". St¹d mamy "for", "in". W naszym przyk³adzie to "dla
ka¿dej czêstotliwoœci (freq)
w przedziale (range) graj dziêk o tej czêstotliwoœci przez 6 milisekund".
Zauwa¿ ¿e ka¿da akcja do wykonania w pêtli "for" ma wciêcie (zgodnie z
tym o czym rozmawialiœmy
wczeœniej) dziêki czemu Python wie dok³adnie jaki kod wykonaæ dla
poszczególnych elementów kolekcji.