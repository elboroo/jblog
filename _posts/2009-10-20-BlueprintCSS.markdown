---
layout: post
title:  BlueprintCSS
---
## 1.
Strona korzystaca z arkuszy CSS wygenerowanych za pomoca narzedzia compress.rb: 
<a href="/~brozek/rails3/project1.html">projekt1</a>


Szału nie ma, ale na razie nie musi być. A oto w kilku zdaniach jak powstała ta stronka.
Po zaopatrzeniu się w Blueprint'a, przyszła pora na zapoznanie się z narzędziem o nazwie compress.rb.
Jak widać na załączonym obrazku <br/> 
( <a href="http://jdclayton.com/blueprints_compress_a_walkthrough.html">http://jdclayton.com/blueprints_compress_a_walkthrough.html</a> ) jego użycie nie (?) jest trudne. Tak więc moj plik settings.yml wyglada nastepująco:

{% highlight text %}


project1:
  path: /home/studinf/brozek/public_git/rails3/css/project1/
  custom_layout: 
    column_count: 3
    column_width: 292
    gutter_width: 12
  plugins:
    - fancy-type
    - buttons

{% endhighlight %}

To co najważniejsze to: 
<object>
<ul>
<li>nazwa projektu - project1</li>
<li>scieżka (path) - miejsce gdzie Blueprint wrzuci wygenerowane CSS'y</li>
<li>column_count - ilość generowanych kolumn</li>
<li>column_width - szerokość generowanych kolumn</li>
<li>gutter_width - domyślna odległość między kolumnami</li>
</ul>
</object>


Z grubsza wiadomo o co chodzi, więc odpalamy skrypt: <br />

<div class="console">ruby compress.rb -p project1</div>

Ufff, po tym całym trudzie możemy zajrzeć do katalogu podanym w settings.yml i radować oko gotowcami CSS na naszą stronke ;)


##2.
Rezultat działania Dust-Me Selectors: <br />
<img src="../../../../images/dust.jpg" alt="[dust]" />
<br /><br />
Po usunięciu nieużywanych selektorów sprawa wyglądała tak:
<img src="../../../../images/dustPo.jpg" alt="[dustPo]" />


##3.
Walidacja HTML i CSS poszła (prawie) bezproblemowo: <br />
<a href ="http://validator.w3.org/check?uri=http%3A%2F%2Fsigma.ug.edu.pl%2F~brozek%2Frails3%2Fproject1.html;accept=text%2Fhtml%2Capplication%2Fxhtml%2Bxml%2Capplication%2Fxml%3Bq%3D0.9%2C*%2F*%3Bq%3D0.8;accept-language=pl%2Cen%3Bq%3D0.7%2Cen-us%3Bq%3D0.3;accept-charset=ISO-8859-2%2Cutf-8%3Bq%3D0.7%2C*%3Bq%3D0.7"><img src="../../../../images/valid-xhtml10-blue.png" alt="[xhtml]" /></a>

<a href="http://jigsaw.w3.org/css-validator/validator?uri=http%3A%2F%2Fsigma.ug.edu.pl%2F%7Ebrozek%2Frails3%2Fproject1.html&profile=css21&usermedium=all&war"><img src="../../../../images/vcss-blue.gif" alt="[css]" /></a>

##4.
YSlow ocenił przykładową stronkę z punktu 1 na B. <br />
<div class="notice">Overall performance score 89</div>
Sugestia programu wyglądała tak: <br />
This page has 3 external stylesheets. Try combining them into one.
Póki co zostawiam tak jak jest.
<br /><br />
Tak na marginesie: blog dostał również ocene B. Z tym, że wynik całościowy wyniósł 84 punkty.
<br /><br />



