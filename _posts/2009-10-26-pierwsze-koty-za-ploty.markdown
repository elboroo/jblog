---
layout: post
title:  Pierwsze koty za płoty
---

##  1. shell i scaffold
Utworzyłem katalog kontakty - miejsce, gdzie się wszystko rozegra ;) . Następnie za pomocą polecenia rails dostałem szkielet projektu. 
{% highlight bash %}
   rails kontakty 
   cd kontakty 
{% endhighlight %}
Z kolei za pomocą polecenia
{% highlight bash %}
ruby script/generate scaffold Contact first_name:string last_name:string 
email:string homepage:string phone:string city:string street:string post_code:string
{% endhighlight  %}
dodałem rusztowanie (scaffold) projektu kontakty.
W ten sposób można automatycznie wygenerować tabelę, model, a także kontroler z interfejsem do obsługi modelu. W rezultacie otrzymujemy plik migracji, konieczne jest zatem 
{% highlight bash %}
rake db:migrate
{% endhighlight  %}
Odpalam serwer 
{% highlight bash %}
ruby script/server
{% endhighlight  %}
A aplikacja dostępna jest pod adresem: localhost:3000/contacts 
Po odpaleniu widzimy dostępne opcje kontrolera, czyli dodawanie, usuwanie i edycje danych...
A o to przecież chodziło.

Test strony za pomocą YSLOW wypadł pomyślnie.
Obólna ocena to A , punkty 95 

Ponadto oceny cząstkowe miały się następująco: 
<ul>
<li>Add Expires Headers ocena B </li>
<li>Compress components with gzip ocena C </li>
<li>reszta: oceny A  </li>
</ul>

Stworzoną aplikację wrzuciłem na githuba: 
<a href="http://github.com/elboroo/kontakty">github->kontakty</a>

## 2. install_theme

Szablon http://www.oswd.org/design/preview/id/3247 instalujemy za pomocą gemu install_theme.
Wczesniej musimy sie zaopatrzyć w zarówno gem jak i szablon.
W głównym katalogu aplikacji odpalamy polecenie:
{% highlight bash %}
$ install_theme . ~/download/Indigo "#cont:text" --partial "header://div[@class='header']/text()" --partial "sidebar://div[@class='sidenav']/text()" --partial "last:#lastUpdated"
{% endhighlight  %}
Potrzeba jeszcze kilku zmian w plikach projektu, aby można było cieszyć się nowym, ciekawszym widokiem naszej aplikacji.

Ocena Yslow
Po zainstalowaniu schematu Yslow ocenił strone na B i 84 punkty. 
Przy: Compress components with gzip pojawiła sie na przykład ocena C, ale do tego dojdziemy za chwile...

## 3. Gravatar Plugin

Instalacja  ogranicza się do wykonania polecenia:
{% highlight bash %}
./script/plugin install git://github.com/mdeering/gravatar_image_tag.git
{% endhighlight  %}
Koleno dodajemy dwa wpisy do pliku config/initializers/gravatar_defaults.rb 
{% highlight ruby %}
ActionView::Base.default_gravatar_image  = "http://localhost:3000/images/default_avatar.png" 
ActionView::Base.default_gravatar_size  = 30 
{% endhighlight  %}
gdzie pierwszy oznacza domyslny avatar wyswietlany w przypadku gdyby pluginowi nie udało się odnaleźć gravataru, a 
drugi określa domyślny rozmiar avataru.

Avatar przy konkretnym kontakcie wyświetlimy w następujący sposób:
{% highlight erb %}
<%= gravatar_image_tag(contact.email, :alt => default_gravatar_image) %>
{% endhighlight %}
## 4. Geolocation
jak na razie fiasko na całej linii...

## 5. Asset Packager

Zgodnie z tym co jest napisane <a href="http://github.com/sbecker/asset_packager">tutaj</a> wykonujemy instalacje pluginu: 
{% highlight bash %}
./script/plugin install git://github.com/sbecker/asset_packager.git
{% endhighlight  %}
Nastepnie generujemy plik: /config/asset_packages.yml
{% highlight bash %}
rake asset:packager:create_yml
{% endhighlight  %}
Po wykonaniu polecenia
{% highlight bash %}
rake asset:packager:build_all
{% endhighlight  %}
dostajemy pakiet w zależności od zawartości wcześniej wymienionego pliku. 
Użycie skompresowanych JS i CSS jest bardzo proste:
{% highlight erb %}
<%= stylesheet_link_merged :base %>
<%= javascript_include_merged :base %>
{% endhighlight  %}

....
Z tymże trzeba uważać, gdzie umiescic ten drugi wpis, ponieważ Yslow potrafi zrobić awanture, że JS nie znajduje się na koncu pliku. 
Ocena końcowa Yslow nie zmieniła się (nadal B) i sam nie wiem dlaczego...



