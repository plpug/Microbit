# Ćwiczenia

W trakcie trwania warsztatów poznawałeś różne funkcjonalności urządzenia. Wyświetlałeś obrazki, animacje, dźwięki, a nawet komunikowałeś się z kolegą za pomocą
modułu radia. Nadszedł czas na to, abyś mógł łączyć to czego do tej pory się nauczyłeś, aby stworzyć coś nowego.

No to zaczynamy!


## Ćwiczenie 1 - Wyświetl negatyw serduszka

Tworzyliśmy na zajęciach już swoje obrazki w tym, swoje serduszka. A co by się stało gdybyśmy zrobili odwrótność takiego serduszka?
Wyszedł by nam ciekawy negatyw. I to jest Waszym celem :)

Podpowiedź:
* Pamiętaj, aby użyć `Image()`
* Rozpisz sobie wszystko na kartce (będzie Ci prościej)
* Obiekt `Image` posiada metodę `invert()` która zwróci negatyw obrazka

## Ćwiczenie 2 - Wyświetl zająca

Zbliżają się święta wielkanocne, każdy z nas lubi czekoladowe zające. Spróbujemy stworzyć sobie zająca i wyświetlić go na Micro:bicie. Co więcej spróbujmy sprawić aby nasz zając się ruszał!

Podpowiedź:

* Pamiętaj, aby użyć `Image()`
* Zerknij sobie do rozdziału [piątego](../chapter05) do opisu obrazków DIY.
* Obiekt `Image` posiada metody `shift_right()`, `shift_left()`, `shift_up()` oraz `shift_down()` do przesuwania obrazka w różnych kierunkach


## Ćwiczenie 3

Spróbuj napisać program, który pozwoli nam pokazać jaki przycisk naciskasz.

* Masz tylko 2 przycisku A i B
* spróbuj użyć `if`
* użyj `is_pressed()`

## Ćwiczenie 4 - symulacja bicia serca

Każdy z nas pewnie leżał kiedyś w szpitalu lub oglądał serial o chirurgach. Napiszcie program, który będzie symulował rytm serca.


## Ćwiczenie 5 - wstrząśni i pokaż słowo

Celem tego ćwiczenia jest napisanie programu, który wyświetla jakieś słowo po wstrząśnięciu swojego urządzenia.

Podpowiedź:

* umieść swoje słowa wewnątrz listy(stworzyć listę słów)
* użyj `accelerometer.was_gesture("shake")`
* wybierz przypadkową wiadomość za pomocą komendy random.choice(messages)

## Ćwiczenie 6 - użyj radia

Pobawimy się teraz w wysyłanie microbitowych smsów ;). Wybierz wiadomość i wyślij ją za każdym razem, kiedy naciśniesz przycisk (A lub B).

Podpowiedź:
* Pamiętaj, żeby wywołać radio: `radio.on()`
* Wyświetl na ekranie wiadomość, którą otrzymasz.
* Upraszczając załóżmy, że tylko jeden Micro:bit naraz będzie wysyłał wiadomość
