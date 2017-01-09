# Instrukcje warunkowe IF i ELSE

W poprzednim rozdziale, robiliśmy kalkulator BMI. Gdzie już używaliśmy IF i ELSE, pewnie pamiętacie. Chcielibyśmy abyście je bliżej poznali. 
W programowaniu często zadajemy pytania rostrzygające (na tak lub nie) i na podstawie odpowiedzi, podejmujemy decyzji co robić. Możemy na przykład zapytać: "Czy masz więcej niż 15 lat?" i jeśli odpowiedź brzmi "tak", i odpowiedzieć "O jezu ale jesteś stary".
Tego rodzaju pytania są nazywane `warunkami`, łączymy wraz z odpowiedziami w instrukcje `if`(jeżeli).

Warunki mogą składać się z wielu pytań, a instrukcje `if` można konstruować na podstawie różnych odpowiedzi na te pytania. W tym rozdziale dowiesz się jak używać instrukcji `if` do pisania programów.

## Instrukcje IF

```markdown
wiek = 23
if wiek >20:
    print("Jesteś za stary!")
```

Instrukcja if składa się ze słowa kluczowego `if`, po którym podajemy warunek oraz dwukropek (:), tak jak wiek >20:. WIersze po dwukropku muszą znajdować się w bloku, a jeśli odpowiedź na pytanie to tak, polecenia w bloku zostaną wykonane. Dowiedzmy się teraz jak pisać bloki i warunki.

Blok kodu to w programowaniu celowo oddzielny zbiór instrukcji. Jeśli przykładowo warunek `if wiek >10: jest prawdziwy, możemy wyświetlić informacje ale i nawet kilka innych zdań:

```markdown
wiek = 23
if wiek > 20:
    print("Jesteś za stary!")
    print("Pomóż ojcu w pracach domowych")
	
```

Powyższy blok składa się z dwóch instrukcji `print`, które są wykonywane tylko wtedy, gdy warunek `wiek > 20` okaże się prawdziwy. Każdy wiersz w bloku ma o cztery spacje więcej niż znajdująca się powyżej instrukcja `if`.
W Pythonie odstęp taki jak np. tabulacja (wstawiana przez naciśnięciu tabulatora) albo spacja (wstawiana po naciśnięciu spacji) jest bardzo ważny. 

Symbole używane w instrukcjach warunkowych:

| Symbol        | Definicja         | 
| ------------- |:-----------------:|
|==      	    | równa się         | 
|!=  		    | różny od          |  
|>              | większy niż       |
|<				| mniejszy niż	    |
|>=				| większy lub równy |
|<=				| mniejszy lub równy|

Jeżeli na przykład masz 10 lat, warunek `wiek == 10 ` zwróci `True`. Jeśli jest inaczej zwróci `False`. Jeśli masz lat 13, warunek wiek > 10 zwróci `True`. 



