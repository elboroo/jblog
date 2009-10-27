---
layout: post
title:  Pierwsze koty za płoty
---

##  1. Shell and Scaffold
Utworzyłem katalog kontakty - miejsce, gdzie się wszystko rozegra ;) . Następnie za pomocą polecenia rails dostałem szkielet projektu. <br />

<div class="console">
   rails kontakty <br />
   cd kontakty <br />
   rake db:create:all <br />
</div>
<br />
Z kolei za pomocą polecenia

<div class="console">
ruby script/generate scaffold Contact first_name:string last_name:string 
   email:string homepage:string phone:string city:string street:string post_code:string
</div>
<br />
dodałem rusztowanie (scaffold) projektu kontakty.<br />
W ten sposób można automatycznie wygenerować tabelę, model, a także kontroler z interfejsem do obsługi modelu. W rezultacie otrzymujemy plik migracji, konieczne jest zatem <br />

<div class="console">
rake db:migrate
</div>
<br />
Odpalam serwer <br />
<div class="console">ruby script/server</div>
<br />
A aplikacja dostępna jest pod adresem: localhost:3000/contacts <br />
Po odpaleniu widzimy dostępne opcje kontrolera, czyli dodawanie, usuwanie i edycje danych...
A o to przecież chodziło.

<br /><br />
Test strony za pomocą YSLOW wypadł pomyślnie.<br />
Obólna ocena to A , punkty 95 <br />

Ponadto oceny cząstkowe miały się następująco: <br />
<ul>
<li>Add Expires Headers ocena B </li>
<li>Compress components with gzip ocena C </li>
<li>reszta: oceny A  </li>
</ul>

## 2