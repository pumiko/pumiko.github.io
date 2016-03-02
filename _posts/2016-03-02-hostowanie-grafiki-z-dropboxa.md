---
published: false
title: Hostowanie grafiki z Dropboxa
layout: post
summary: "Ostatnio zmierzyłam się z dodawania obrazków do postów. Wynikiem tej przygody jest krótki poradnik o tym, jak korzystać z grafik udostępnionych z Dropboxa na swojej stronie. Kilka ważnych informacji, zwłaszcza dla nowych użytkowników."
tags: 
  - dajsiepoznac
  - dropbox
  - sloiczki
---

Temat hostowania grafiki może się wydawać całkiem proste, bo przecież możliwości przechowywania zdjęć w internecie jest dużo. Ponieważ w najbliższym czasie chcę spróbować swoich sił z bootstrapem, w celu stworzenia landing page dla Słoiczków, to potrzebne mi było łatwe i sprawdzone rozwiązanie. Nie wiem niestety jaki sposób jest teraz polecany. Dawno dawno temu korzystałam z [Photobucket](http://s5.photobucket.com/), jednak nie chciałam do tego wracać, nie miałam też ochoty zakładać nigdzie nowego konta. 
Idąc za radą [Bartka](http://donpiekarz.pl/) postanowiłam skorzystać z Dropboxa. Wydawało mi się, że to będzie proste, w końcu już nie raz korzystałam z Dropboxa, wydaje się bardzo przyjazny, więc czemu nie spróbować? 

Zaczęłam jak typowy laik, po prostu wklejając link udostępnienia, ale po chwili zrozumiałam, że to bez sensu, bo przecież to link do podglądu obrazka a nie do obrazka. Postanowiłam poszukać właściwego adresu na własną rękę, jednak nie byłam w stanie dotrzeć do żadnej działającej wersji. Ciągle coś było nie tak. Tutoriale znalezione w internecie też z jakiegoś dziwnego powodu się nie sprawdzały. 
W końcu doszłam do wniosku, że prawdopodobnie chodziło o to, że na swoim koncie nie mam [folderu publicznego](https://www.dropbox.com/pl/help/16). Nowsze konta, to znaczy utworzone po 4 października 2012 roku, takiej funkcjonalności nie posiadają. Trudno powiedzieć czy to dobrze czy źle, skoro obecnie można udostępniać pliki z dowolnego folderu. Jednak w obliczu tego, że konieczne jest wykonanie dodatkowych operacji, aby poprawnie umieścić obrazek w HTMLu, to jest to mało wygodne. Co ciekawe, nadal istnieje możliwość [aktywacji folderu Publicznego](https://www.dropbox.com/enable_public_folder) ale tylko, jeśli mamy płatne konto.
Ostatecznie udało się znaleźć dość proste rozwiązanie problemu, uciążliwe jest jednak to, że za każdym razem trzeba będzie pamiętać o jego zastosowaniu. W chwili obecnej jest ono wystarczające, w przyszłości pewnie poszukam innej formy.

Wynikiem opisanych wyżej przygód jest (kolejny) krótki poradnik dla osób niewprawionych w bojach z Dropboxem. 

<h2>Jak używać na stronie grafiki udostępnianej z Dropboxa?</h2>

<h3>Krok 1. Udostępnij obrazek!</h3> 

Inni też muszą mieć do niego dostęp. Pliki można udostępnić na [kilka sposobów](https://www.dropbox.com/help/167). Tu dwa przykłady: 

<h4>1. Ze strony internetowej</h4>

Po zalogowaniu na swoje konto i upewnieniu się, że mamy tam obrazek, który chcemy udostępnić klikamy na przycisk "Udostępnij".

<img class="center" src="https://dl.dropboxusercontent.com/s/8je67noj5bhixhw/dropbox_img_3.jpg" alt="Udostępnianie pliku z klienta webowego Dropboxa" >

Potwierdzeniem udostępnienia pliku jest okienko, w którym możemy poinformować innych o tym, że udostępniliśmy plik, a także skopiować adres.

<img class="center" src="https://dl.dropboxusercontent.com/s/gfjf0razfs4d9ew/dropbox_img_4.jpg" alt="Potwierdzenie udostępnienia pliku z linkiem do skopiowania" >

<h4>2. Z aplikacji desktopowej</h4> 

Jeśli nie macie jej na komputerze, to można ją pobrać [tutaj](https://www.dropbox.com/downloading)).
Po przerzuceniu plików do folderu dropboxa na komputerze, klikamy prawym przyciskiem w nieszczególnie intuicyjną opcję "kopiuj łącze do Dropbox".

<img class="center" src="https://dl.dropboxusercontent.com/s/ms8rjz60u4nri5x/dropbox_img_1.jpg" alt="Udostępnianie pliku z klienta desktopowego Dropboxa" >

Jeśli wszystko poszło dobrze, otrzymujemy wiadomość: 

<img class="center" src="https://dl.dropboxusercontent.com/s/kj9jzeq3jgpz97e/dropbox_img_2.jpg" alt="Potwierdzenie udostępnienia pliku" >

zgodnie z informacją link macie skopiowany i możecie go wkleić w dowolne miejsce.

<h3>Krok 2. Zmień ścieżkę dostępu!</h3>
Niezależnie w jaki sposób wykonacie krok pierwszy, link do udostępnionego obrazka będzie wyglądał w następujący sposób:

{% highlight %}
www.dropbox.com/u/\<indeks\>/\<nazwapliku\>?dl=0
{% endhighlight %}

Nie jest to jednak link do pliku, a jedynie do jego podglądu. Żeby uzyskać z tego ścieżkę do obrazka musimy podmienić www.dropbox.com na {% highlight %}dl.dropboxusercontent.com{% endhighlight %} oraz usunąć {% highlight %}'?dl=0'{% endhighlight %}

Otrzymamy zatem link do rzeczywistego pliku, który będzie wyglądał następująco:

{% highlight %}
www.dropboxusercontent.com/u/\<indeks\>/\<nazwapliku\>
{% endhighlight %}

I w takiej formie możemy go już wykorzystać na naszej stronie, blogu lub forum.

Na koniec jeszcze ważna informacja.
Hostowanie plików z Dropboxa opłaca się jedynie, jeśli nasza strona ma mało wyświetleń a pliki, które udostępniamy są lekkie. Dzienny limit transferu dla podstawowego konta Dropbox to 20GB dla wszystkich udostępnianych łączy. A maksymalna liczba pobrań dziennie to 100 tys. Więcej o tym w [pomocy Dropboxa](https://www.dropbox.com/help/4204). 
