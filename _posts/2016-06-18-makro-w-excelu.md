---
published: true
title: Makro w Excelu
layout: post
summary: "Właśnie napisałam swoje pierwsze makro w Excelu. Nie jest zbyt długie, ale jest"
tags: 
  - excel
  - vba
  - makro
---

Właśnie napisałam swoje pierwsze makro w Excelu. Nie jest zbyt długie, ma kilka linijek, a wygląda następująco:

{% highlight vbnet %}
Sub ClearMonthlyExpenses()
    If InStr(1, ActiveSheet.Name, "_M") Then
        ActiveSheet.Range("G62:AM67, G70:AM74, G77:AM84, G87:AM91, G94:AM97, G100:AM104, G107:AM111, G114:AM121, G124:AM131, G134:AM141").ClearContents
        ActiveSheet.Range("D47:D54").Value = 0
        MsgBox "Wyczyszczono arkusz " & ActiveSheet.Name
        
    ElseIf InStr(1, ActiveSheet.Name, "_B") Then
        ActiveSheet.Range("G61:AM66, G69:AM73, G76:AM83, G86:AM90, G93:AM96, G99:AM103, G106:AM110, G113:AM120, G123:AM130, G133:AM140").ClearContents
        ActiveSheet.Range("D47:D53").Value = 0
        MsgBox "Wyczyszczono arkusz " & ActiveSheet.Name
    End If
End Sub
{% endhighlight %}

Tekst poniżej nie będzie jakoś szczególnie redagowany. Chcę napisać cokolwiek :) 

Pomimo, że nie jest szczególnie skomplikowane (jak się okazuje), to bardzo długo bałam się nawet zacząć je pisać. Inne rzeczy mnie pochłonęły - studia, praca i nawet na zapoznanie się z tym jak się pisze makra w Excelu nie było czasu. Ostatnio coraz częściej makrach i visual  basicu słyszałam. Same złe rzeczy oczywiście, typu, że to niegodne programisty (?). W pracy piszemy makra, żeby usprawnić sobie pracę. Ja tego unikałam, bo bałam się zacząć znowu czegoś uczyć i zapamiętywać i bałam się że mi nie wyjdzie. Te lęki przed poznawaniem nowych rzeczy stają się ostatnio coraz bardziej uciążliwe. [Bartek](http://donpiekarz.pl) też co chwilę mówi o makrach, bo on również ich w swojej pracy używa. I zachęcał mnie do tego, żeby takie makro napisać. Nie próbować, tylko napisać. I w końcu, za trzecim albo czwartym podejściem napisałam coś co jest używalne. :) 

Właściwie skąd w ogóle wziął się pomysł napisania tego makra?
Wszystko zaczęło się od tego, że od pewnego czasu prowadzimy wspólny budżet w Excelu. Jest on dość płynny, w związku z czym, nie przygotowaliśmy całego szablonu na rok. Wybraliśmy opcję kopiowania arkusza co miesiąc. Taki skopiowany arkusz niestety trzeba wyczyścić ze starych zapisów i jest to dość czasochłonne. Za każdym razem (raz w miesiącu) jak ręcznie czyściłam te tabelki, to słyszałam "szybciej byś napisała do tego makro". Przy pierwszej takiej uwadze nie wiedziałam nawet czym jest makro. 

Jak patrzę na to teraz, a proces przełamania się trwał naprawdę długo, to myślę, że napisanie makra zajęło mi nieco więcej czasu niż czyszczenie tych tabelek co miesiąc przez rok, ale w dłuższej perspektywie makro wyjdzie na plus. Już teraz bardzo się cieszę, że je napisałam :)  
