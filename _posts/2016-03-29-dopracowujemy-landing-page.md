---
published: true
title: Dopracowujemy Landing Page
layout: post
summary: "Krótkie podsumowanie stanu prac nad Landigiem dla Słoiczków"
tags: 
  - dajsiepoznac
  - bootstrap
  - sloiczki
---

Nie chcę przedłużać dzisiejszego wpisu, rozwinę tylko kilka haseł, odpowiadających zadaniom, które zrealizowałam.

### Polskie znaki w czcionkach

Czy też zwracacie uwagę na to, że czcionki stosowane na polskojęzycznych stronach czasami mają problem z wyświetleniem naszych "ogonków", "kropek" i "kresek"? Czasami nie razi to w oczy (aż tak bardzo), a czasem wręcz odrzuca. Na Słoiczkach czcionka szeryfowa stawała się przy polskich znakach bezszeryfowa i pogrubiona. Żeby to ominąć, [Bartek](http://donpiekarz.pl) polecił zastosować rozwiązanie, którego użyliśmy na naszych blogach, tj. po linku czytającym czcionkę dodać **&subset=latin,latin-ext**. W kodzie wygląda to następująco:

Przed:

{% highlight html %}
{% raw %}
<head>
  ...
  <!-- Custom Fonts -->
  <link href='http://fonts.googleapis.com/css?family=Open+Sans:300italic,400italic,600italic,700italic,800italic,400,300,600,700,800' rel='stylesheet' type='text/css'>
  <link href='http://fonts.googleapis.com/css?family=Merriweather:400,300,300italic,400italic,700,700italic,900,900italic' rel='stylesheet' type='text/css'>
</head>
{% endraw %}
{% endhighlight %}

Po:

{% highlight html %}
{% raw %}
<head>
  ...
  <!-- Custom Fonts -->
  <link href='http://fonts.googleapis.com/css?family=Open+Sans:300italic,400italic,600italic,700italic,800italic,400,300,600,700,800&subset=latin,latin-ext' rel='stylesheet' type='text/css'>
  <link href='http://fonts.googleapis.com/css?family=Merriweather:400,300,300italic,400italic,700,700italic,900,900italic&subset=latin,latin-ext' rel='stylesheet' type='text/css'>
</head>
{% endraw %}
{% endhighlight %}


Jeśli jednak szukacie czcionek i chcecie się upewnić, że one działają, to znalazłam [zestawienie google fonts z polskimi znakami](http://netwizards.com.pl/zasoby/darmowe-polskie-czcionki-google-fonts-z-polskimi-znakami/). Na tej stronie, poza tym jak w poszczególnych czcionkach wyglądają polskie literki, znajdziecie też kod, który należy umieścić na stronie pomiędzy znacznikami <head> oraz w CSS. 

### Favicon

Stworzenie go tak, żeby po zmniejszeniu do 16 x 16 px cokolwiek przypominał było wyzwaniem. Przygotowywanie pliku w więcej niż jednym programie zawsze jest w jakiś sposób uciążliwe. Ostatecznie udało się jakąś ikonkę stworzyć i dodać ją w html'u w następujący sposób:

{% highlight html %}
{% raw %}
<head>
  ...
  <link rel="shortcut icon" href="favicon.ico" type="image/x-icon">

</head>
{% endraw %}
{% endhighlight %}

### Nowe font-icony

Dodałam trzy nowe "literki", zgodnie z opisem z poprzedniego [posta](http://pumiko.pl/2016/03/16/font-icons-z-pliku-svg.html). Zabawa o wiele przyjemniejsza niż favicon. Przy okazji nauczyłam się nowej funkcji w Corelu: Ctrl+Shift+Q, która służy do przekształcania zwykłej linii na jej obrys wraz z wypełnieniem (convert outline to object). Teraz ta nazwa wydaje mi się logiczna, ale gdybym miała tę funkcję odszukać bez googli, to zajęłoby to sporo czasu. W Adobe Illustrator ta funkcja nosi nazwę *Expand*, a w Ink Scape *Stroke to Path*.

### Podsumowanie

Teraz trochę żałuję, że nie postawiłam przed sobą większego wyzwania, jakim byłoby stworzenie takiej strony od podstaw. Jednak wydaje mi się, że gdybym chciała tak z marszu to zrobić, bardzo szybko bym się poddała i stwierdziła, że to nie dla mnie. Może jednak lepiej uczyć się małymi kroczkami, ciągle mając apetyt na więcej, niż od razu porywać się na coś wielkiego. W sumie i tak budowanie strony od podstaw nie ominie mnie przy tworzeniu Słoiczków. 

Przemyślenia dotyczące nauki i rzucania się na głęboką wodę świetnie obrazuje metodyka MVP. Na kilku blogach z #dajsiepoznac widziałam już obrazki dotyczące tej metodyki. Zazwyczaj było to coś w stylu:

<img class="ctr" src="https://dl.dropbox.com/s/tla7kz3earzc8dk/MVP_1.png" alt="Metodyka minimum viable product - wersja 1">
Obrazek zaczerpnięty z [tej](http://www.slideshare.net/5throck/biz-plan-55809179) prezentacji.

W moim odczuciu zdecydowanie lepsza jest jednak ta grafika:
<img class="ctr" src="https://dl.dropbox.com/s/h6m2my1oi5dguhe/MVP_2.jpg" alt="Metodyka minimum viable product - wersja 2">
Obrazek pochodzi z [tego](https://boagworld.com/digital-strategy/how-to-build-a-digital-service-when-under-intense-scrutiny/) artykułu. 

Podoba mi się bardziej, bo jest zgodna z moimi odczuciami. Nie jestem teraz zadowolona z tego, w jaki sposób podeszłam do nauki, podobnie nie będę zadowolona z pierwszej wersji Słoiczków. Wątpię też w to czy uda mi się dojść do stadium "samochodu", zarówno w zdobywaniu wiedzy (ten proces nigdy się na szczęście nie kończy ;) ) jak i w aplikacji. Możliwe, że sporo funkcjonalności, które teraz wydają mi się fajne nigdy nie ujrzą światła dziennego, bo nikt ich zwyczajnie nie będzie potrzebował, ale to już pozostawiam do późniejszych przemyśleń.
