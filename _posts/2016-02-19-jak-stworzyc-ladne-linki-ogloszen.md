---
published: true
title: "Jak stworzyć ładne linki ogłoszeń?"
layout: post
summary: "O tym jak w dość prosty sposób utworzyć czytelne linki na podstawie id i tytułu ogłoszenia."
tags: 
  - dajsiepoznac
  - projekt
  - słoiczki
  - django
---

Jednym z już zrealizowanych zadań w ramach pracy nad Słoiczkami było utworzenie czytelnych linków do poszczególnych ogłoszeń, które będą przede wszystkim przydatne użytkownikom. Najprościej to osiągnąć tworząc link z tytułu ogłoszenia, z uwzględnieniem tego, że tytuły nie muszą być unikalne, bo np. "dżem truskawkowy" jest dość popularnym przetworem. W takim przypadku z pomocą przychodzi chociażby id ogłoszenia.

Chciałam, aby docelowo linki wyglądały następująco: <i>/id-tytul.html/</i>. Ostatecznie uzyskały postać: <i>/id/tytul.html</i>.

Odpowiedzią na tę potrzebę okazało się pole "slug", jednak znalezienie optymalnego rozwiązania sporo zajęło, zwłaszcza, że z punktu widzenia osoby początkującej każda ze znalezionych odpowiedzi wydawała się niepełna, urwana w połowie i nie byłam w stanie zgadnąć co należy dalej zrobić oraz zrozumieć co dokładnie mówiły błędy, bo "przecież wszystko ładnie skopiowałam".

W związku z tym, pomyślałam, że dla usystematyzowania zdobytej wiedzy warto samodzielnie zapisać pełne rozwiązanie. Możliwe, że przyda się ono w przypadku kolejnych napotkanych problemów.

<h3>Rozwiązanie dla Django 1.8</h3>

<h4>1. Zaimportowanie filtru slugify, dodanie pola slug do modelu ogłoszenia (Ad) i zdefiniowanie funkcji save, zamieniającej tutuł na slug w <i>website\models.py</i>.</h4>

{% highlight python %}
from django.db import models
from django.template.defaultfilters import slugify
  
class Ad(models.Model):
    slug = models.SlugField(max_length=100)
	
    def save(self):
	slug = slugify(self.title)
        if self.slug != slug:
            self.slug = slug
        return super(Ad, self).save()
{% endhighlight %}

<h4>2. Utworzenie widoku pojedynczego ogłoszenia w <i>website\views.py</i>.</h4>

{% highlight python %}
from django.shortcuts import render, get_object_or_404
from .models import Ad

def ad_detail(request, id, slug=None):
    ad = get_object_or_404(Ad, id=id)
    return render(request, 'website/ad_detail.html', {'ad': ad})
{% endhighlight %}

<h4>3. Utworzenie szablonu HTML dla widoku pojedynczego ogłoszenia <i>website\templates\website\ad_detail.html</i>.</h4>

{% highlight html %}
{% raw %}
<body>
    {% block content %}
        {% if ad.published_date %}
             <div class="date">
                {{ ad.published_date }}
            </div>
         {% endif %}
         <h1>{{ ad.title }}</h1>
         <p>{{ ad.text|linebreaks }}</p>
    {% endblock %}
</body>
{% endraw %}
{% endhighlight %}

<h4>4. Dodanie wzoru adresu url wykorzystującego id oraz slug w <i>website\urls.py</i>.</h4>

{% highlight python %}
from django.conf.urls import url
from . import views

urlpatterns = [
    ...
    url(r'^ad/(?P<id>[\d]+)/(?P<slug>[-\w\d]+)/$', views.ad_detail, name='ad_detail'),
]
{% endhighlight %}

Konieczne stało się również uzupełnienie innych widoków i poprawki w odnośnikach, tak żeby można było logicznie poruszać się po stronie. 

<h4>5. Zwrócenie odpowiedzi w postaci strony z nowym ogłoszeniem po jego dodaniu. Uzupełnienie widoku <i>ad_new</i> w <i>website\views.py</i>.</h4>

{% highlight python %}
from django.shortcuts import render, redirect
from .models import Ad

def ad_new(request):
    if request.method == "POST":
        form = AdsForm(request.POST)
        if form.is_valid():
            ad = form.save(commit=False)
            ad.save()
            form = AdsForm()
            return redirect(ad_detail, ad.id, ad.slug)
    else:
        form = AdsForm()

    return render(request, 'website/ad_new.html', {'form': form})
{% endhighlight %}

<h4>6. Utworzenie odnośnika ze strony listy ogłoszeń do ogłoszenia.</h4>

{% highlight html %}
{% raw %}
<body>
    <h1>Lista ogłoszeń</h1>
    {% for ad in ads %}
        <div>
            <p>published: {{ ad.published_date }}</p>
            <h1><a href='{% url 'ad_detail' ad.id ad.slug  %}'>{{ ad.title }}</h1>
            <p>{{ ad.text|linebreaks }}</p>
        </div>
    {% endfor %}
</body>
{% endraw %}
{% endhighlight %}

Mam nadzieję, że o niczym nie zapomniałam :)
