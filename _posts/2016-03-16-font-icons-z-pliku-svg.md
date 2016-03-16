---
published: false
title: Generowanie własnych czcionek-ikon w oparciu o pliki SVG
layout: post
summary: "Historia o tym dlaczego zamiast programować zajęłam się tworzeniem icon fonts. Na jakie narzędzia warto zwrócić uwagę, krótki tutorial i zestaw artykułów, z którymi warto się zapoznać. Moja pierwsza &quot;literka&quot; i użycie czcionki na stronie Słoiczków. W tekście znajdziecie nawet kawałek kodu ;)"
tags: 
  - dajsiepoznac
  - bootstrap
  - icon font
  - sloiczki
---

Dziwnie toczą się moje losy, odkąd przystąpiłam do konkursu #dajsiepoznac. Myślałam, że nauczę się programować, że django, python, backend, tym będę się zajmować, to będzie mnie pochłaniać, a tymczasem rzeczywistość pokazuje, że więcej czasu spędzam z kartką i ołówkiem, w programach graficznych i próbując dobrać obrazki i kolory do stron.

Tym razem dopadła mnie potrzeba posiadania ładnych i wyjątkowych ikon. W [poprzednim poście](http://pumiko.pl/2016/03/15/landing-page-poczatki.html), wspominałam o swoich obawach związanych z tym, że gdy zacznę bawić się zamienianiem ikon, które są w szablonie na swoje własne, to będzie się wszystko psuć. Pisząc to myślałam, że własne ikony wstawię jako obrazki. Jednak już raz doświadczyłam tego, jak obrazek potrafi zniszczyć działający projekt. Walczyłam z tym dostosowując bloga. Nie chciałam powtarzać tamtej przygody, więc szukałam rozwiązania i obejścia problemu. Nie pamiętam nawet jak, ale trafiłam na hasła font awesome, glyphicon oraz icon font, a dalej, po nitce do kłębka doszłam do tego, że takie czcionki można stworzyć samemu. Kolejne wielkie odkrycie, które rzeczywiście ułatwiła pracę. 

Nie obyło się jednak bez konieczności doszkolenia się i poznania nowych narzędzi, a i kilka drobnych problemów po drodze się trafiło, o czym przeczytacie poniżej.   

### Poradniki i przydatne linki

Nie będę tworzyć tutaj poradnika mówiącego o tym jaka jest najlepsza platforma do generowania, składania lub pobierania fontów. Na razie udało mi się skorzystać z dwóch generatorów. Najpierw trafiłam na [Fontastic](http://app.fontastic.me/#select/sfjYyA4L3JejdzsTWxdwxc) i poradnik do niego na blogu [Rafała Tomala](http://rafaltomal.com/how-to-create-and-use-your-own-icon-fonts/). Miałam jednak problem z przygotowaniem ikonki kota, tak żeby program poprawnie ją czytał. Pracowałam zgodnie z [instrukcją](http://fontastic.me/faq), jednak cały czas coś było nie tak. Wydaje mi się, że jedyne co robiłam inaczej, to używałam innego programu do grafiki wektorowej. Adobe Illustratora nie posiadam, ale wszystkie te programy powinny mieć podobną funkcjonalność i dawać podobne efekty. 

Wspomniany kłopot sprawił, że postanowiłam poszukać narzędzia, które wygeneruje poprawne plik SVG. Podczas poszukiwań przypadkiem natrafiłam na [IcoMoon](https://icomoon.io/app/). Jest to program bardzo podobny do Fontastic. Jeśli chodzi o generowanie fontów, to funkcjonalność obu stron jest podobna, ale IcoMoon poprawnie otwierał i pokazywał moją ikonkę. Podjęłam jeszcze kilka prób rozwiązania zagadki, czemu tu działa a tam nie. Chciałam wrócić do Fontastic, bo przypadł mi do gustu bardziej niż IcoMoon. Niestety nie udało mi się nic sensownego zrobić z kotem, więc na tę chwilę zostaje IcoMoon. Na oku mam jeszcze jeden czy dwa programy do sprawdzenia, ponieważ chciałabym znaleźć optymalne rozwiązanie. Niestety teraz nie mam na to czasu, bo praca goni, a kod już się niecierpliwi. Jeśli będziecie szukali czegoś dla siebie, to polecam zacząć od przeglądu narzędzi na [Mashable]( http://mashable.com/2014/01/14/icon-font-generators/#m823O3ENGZqu). 

Poradnika o tym jak używać generatorów, z którymi miałam do czynienia, też nie napiszę. Tutoriale do Fontastic są podlinkowane powyżej. Jeśli chcielibyście korzystać z IcoMoon to polecam [bloga Creative Market](creativemarket.com/blog/2015/04/03/how-to-create-a-simple-icon-font) oraz [SitePoint](http://www.sitepoint.com/create-an-icon-font-illustrator-icomoon/). Te dwa poradniki pokazują m.in. jak przygotować grafikę i wygenerować plik SVG, żeby program nie miał z nim problemu.

### Ikona Pumiko na stronie

Użyłam IconMoon. Pobrałam z niego swój plik SVG jako czcionkę. Można na raz pobierać całe zestawy czcionek, ale na próbę wystarczy jedna "literka" 

<img class="ctr" src=" " alt="Pobieranie czcionki z IcoMoon">

Z zestawu plików, który otrzymujemy do zaimplementowania naszej czcionki na stronie potrzebujemy tylko pliku style.css i folderu font.

<img class="ctr" src=" " alt="Pliki pobrane z IcoMoon">

Pliki te dodałam do [repozytorium landing page'a](https://github.com/pumiko/SloiczkiLanding). Czcionki przerzuciłam do istniejącego wcześniej folderu __font__, a plik __style.css__ zmieniłam na __icomoon.css__ i ulokowałam go w folderze __css__. Na początek, przez to, że pliki wrzuciłam tak a nie inaczej należy poprawić ścieżki dostępu do czcionek w pliku icomoon.css. W wersji oryginalnej wygląda to tak:

{% highlight html %}
{% raw %}
@font-face {
  font-family: 'icomoon';
  src:    url('fonts/icomoon.eot?nnmadt');
  src:    url('fonts/icomoon.eot?nnmadt#iefix') format('embedded-opentype'),
    url('fonts/icomoon.ttf?nnmadt') format('truetype'),
    url('fonts/icomoon.woff?nnmadt') format('woff'),
    url('fonts/icomoon.svg?nnmadt#icomoon') format('svg');
  font-weight: normal;
  font-style: normal;
}
{% endraw %}
{% endhighlight %}

A po zmianie...

{% highlight html %}
{% raw %}
@font-face {
  font-family: 'icomoon';
  src:    url('../fonts/icomoon.eot?nnmadt');
  src:    url('../fonts/icomoon.eot?nnmadt#iefix') format('embedded-opentype'),
    url('../fonts/icomoon.ttf?nnmadt') format('truetype'),
    url('../fonts/icomoon.woff?nnmadt') format('woff'),
    url('../fonts/icomoon.svg?nnmadt#icomoon') format('svg');
  font-weight: normal;
  font-style: normal;
}
{% endraw %}
{% endhighlight %}

Kolejna ważna rzecz. Jeśli dodajemy nowy zestaw czcionek to trzeba też head naszej strony uzupełnić o nową ścieżkę, czyli po prostu dodać kolejny link.

{% highlight html %}
{% raw %}
 <!-- Custom Fonts -->
	...
	<link rel="stylesheet" href="css/icomoon.css" type="text/css">
{% endraw %}
{% endhighlight %}

Po dokonaniu tych drobnych zmian można już używać czcionki na stronie. Poszłam na łatwiznę i wykorzystałam istniejący już div. Tzn. zamieniłam telefon, który był w oryginalnym szablonie na kota. Zmieniłam też podpis, podlinkowując swojego bloga.
W oryginale div wyglądał tak:

{% highlight html %}
{% raw %}
  <div class="col-lg-4 col-lg-offset-2 text-center">
    <i class="fa fa-phone fa-3x wow bounceIn"></i>
    <p>123-456-6789</p>
  </div>
{% endraw %}
{% endhighlight%}

Po zmianie ma następującą postać: 

{% highlight html %}
{% raw %}
  <div class="col-lg-4 col-lg-offset-2 text-center">
    <i class="icon-pumiko fa-4x wow bounceIn"></i>
    <p><a href="http://pumiko.pl">pumiko.pl</a></p>
  </div>
{% endraw %}
{% endhighlight %}

W praktyce podmieniłam tylko wcześniejszą ikonkę i zmieniłam styl __fa-3x__ na __fa-4x__. Zmiana ta miała na celu powiększenie kota, bo okazał się zbyt drobny w stosunku do pozostałych ikonek.

Jak wygląda moja pierwsza literka zobaczycie na [Słoiczki.pl](http://xn--soiczki-njb.pl/)

### Na zakończenie

Dzięki wprowadzaniu zmian i pracy z HTMLem i CSSami uczę się używać gita posiłkując się nieco blogiem [Na miękko](http://namiekko.pl/2016/03/05/no-i-git-kontrola-wersji-sluzy-nie-tylko-programistom/). Na razie nauka na poziomie nowicjusza, ale muszę się jeszcze przyzwyczaić do używania nowego narzędzia :)  

Teraz chciałabym jak najszybciej przygotować pozostałe ikonki i dorzucić je na stronę, zmienić teksty na stronie, a w następnej kolejności zająć się formularzem :) 


PS. W międzyczasie sprawdziłam jeszcze jeden generator czcionek - [Fontello](http://fontello.com/). Niestety też nie radzi sobie z kotem :( 
