Uporaba GIT-a
=============
Kaj je git?
-----------
Git je sistem za kontrolo verzij. Namenjen je za shranjevanje kode, skript dokumentcaije... Prednost GIT-a je deljenje vsebine. Z GIT-om lahko svojo kodo, dokumentacijo delimo s komerkoli, odvisno od pravic, pa lahko dokumente vsak kopira spremeni in nato tudi predlaga spremembe.

Standardna oblika zapisa je MerdownLanguage, ki je enostaven za uporabo in s katerim lahko hitro dosežemo želeni efekt.

*****

Zahteve gostujočega sistema
---------------------------
*   Git konzola

    Linux: sudo apt-get install git / git-core

    Windows: [Prenos](https://windows.github.com/) konzole in GUI

*****


*****
Sintaksa MarkDown
-----------------
Markdown sintaksa je uporabljena za pisanje dokumentacije na GIT-u. PIsanje v njej je enostavno, sintaksa pa je na spodnjem linku.

[Sintaksa](https://github.com/fletcher/MultiMarkdown/blob/master/Documentation/Markdown%20Syntax.md)

Primeri spletnih urejevalnikov:

*   Spletni urejevalnik [Dillinger](http://dillinger.io/)
*   Spletni urejevalnik [StackEdit](https://stackedit.io/)
*   Spletni urejevalnik [Joncom Markdown editor](http://joncom.be/experiments/markdown-editor/edit/)

*******

***Opozorilo***
Za shranjevanje sprememb je potrebno imeti nastavljeno ime in email na našem računalniku. To lahko storimo z ukazoma

        $ git config --global user.name "John Doe"
        $ git config --global user.email johndoe@example.com

****

Osnovna inicializacija projekta
----------------
Ustvarimo novo mapo, v kateri bo bival naš git projekt in se premaknemo vanjo:

        mkdir -p <repoziroriji>/<ime_projekta>
        $mkdir -p repos/HelloWorld
        $cd repos/HelloWorld
        
Inicializiramo projekt in preverimo obstoj:

        $git init
        $git status

Git status nam pove tudi če so v lokalnem repozitoriju nove ali spremenjene datoteke

Nato ustvatimo novo datoteko in jo dodamo v repozitorij:

        $touch HelloWorld.txt
        Po želji lahko notri dodamo vsebino
        $git add HelloWorld.txt
        Če je datotek več lahko tudi 
        $git add *

V repozitorij shranimo spremembe:  

        git commit <branch>
        $git commit master
        masterj je naš osnoven branch
Po želji lahko dodamo krajši opis, v nasprotnem primeru bo odprl novo datoteko, v katero moramo obvezno vpisati opis sprememb

Branch
------
Branch je veja našega programa.

Primer:

*   Delamo spletno stran
*   Za nov del strani odpremo nov Branch, saj še ni prilagojena za produkcijo
*   Razvijamo na našem novem Branchu

Primer 2.0:

*   Nekdo prijavi napako na našem "master" Branchu
*   Ustvarimo nov Branch in v njem popravimo napako
*   Ko je nov Branch stestiran ga zdužimo v naš "master" Branch

Kreiranje Brancha
        
        git branch <ime_brancha>
        $git branch testni_branch
Prestavimo se v nov Branch
        
        git checkout <ime_brancha>
        $git checkout testni_branch
        
**! Ko commitamo spremembe jih commitamo v trenutni branch**

Preverimo, v katerem Branchu smo:

        $git status
        
Več o branchih si lahko preberete na [linku](http://git-scm.com/book/en/Git-Branching-Basic-Branching-and-Merging).

*****

Keiranje novega projekta na spletu
--------
Najprej se registrirajte na [github.com](http://github.com/).
Ko pridete na stran v zgornji navigacijski vrstici izberite ikono +. Nastavite osnovne lastnosti projekta (ime, opis).

***Zasebnost***

Pozamo tri osnovne vrste nastavitev zasebnosti:

*   Public (Na voljo komurkoli)
*   Internal (Na voljo samo registriranim uporabnikom)
*   Zasebno (Na voljo samo vam in uporabnikom, ki jih dodate v skupino)

Ko je projekt kreiran lahko že inicializiranjega prenesete v lokalno mapo ali pa naložite datoteke iz lokalnega projekta v globalni repozitorij.

******

***Opozorilo***
-----
Ker je strežnik git.smartis.si le za notranjo uporabo nima ustreznih ssl certifikatov, zato je potrebno onemogočiti preverjanje varnostnih certifikatov. To lahko storimo z ukazom:

        git config -–global http.sslVerify false

******       

Clone
--------
Ukaz se uporablja za prenašanje projektov iz serverja

        git clone <url_projekta>
        $git clone http://git.smartis.si/kkogovsek/hello-world-project.git
        
Url projekta dobimo v osnovnem pregledu projekta

********

Push
--------
Ukaz push se uporablja za uploadanje projekta (nazaj) v globalni repozitorij

Najprej je potrebno nastaviti glavni url za repozitorij. To storimo z ukazom:

        git remote add <alias_remote> <Spletna_lokacija_repozitorija>
        git remote add origin http://git.smartis.si/kkogovsek/dokumentacija.git

Če hočemo videti shranjene remote strežnike lahko uporabimo ukaza:

        $git remote
        $git remote --verbose / git remote -v

Nato lahko pošljemo spremembe nazaj na spletni repozitorij

        git push <alias_remote> <ime_brancha>
        git push origin master
        
**********

Spletne storitve
===============
Datoteke
---------
Navigiramo se na projekt in v zavihku files izberemo želeno datoteko.
Pregledu lahko v zavihku *Blame* vidimo s za vsako vrstico, kdaj je bila spremenjena in popravljena. V zavihku *History* pa lahko vidimo vse popravke.

*****************

Labele
----------
Po internem dogovoru bomo labele za projekt uporabljali:

*	Ime stranke (npr. ELES)
*	Ime platforme (npr. MAXIMO)

**Za preprečevanje napak uporabljaj le velike tiskane črke**

Za prijavo v ISSUES se uporabljajo:

*	BUG -> Prijava napake
*	QUESTION -> Vprašanje
*	REQUEST -> Prošnja
*	IDEA -> Predstavitev ideje
*	OTHR -> Ostalo

***************
Network
--------
V tem zavihku lahko vidimo zgodovino sprememb, po datumih in kratke opise.

*************

Prijava in odpravljanje težav
---------

Navigiramo se na želen projekt, in pod zavihkom ISSUES pritisnemo gumb ADD Issue.

Izberemo naslov in opišemo problem. Težavo lahko prijavimo točno določenemu uporabniku, ki je v zato namenjeni skupini.

Na težavo se lahko odzovemo s komentarjem, ko pa težavo s skupnimi močmi odpravimo lahko težavo zapremo, npr. kot rešeno, lahko pa jo naknadno spet odpremo, če se za to izkaže potreba.

Parametri pri dodajanju novega vnosa v ISSUE:

*   Title: Kratek povzetek problema ali naloge
*   Description: Podroben opis problema ali naloge
*   Asign to: Uporabi predvsem pri dodeljevanju nalog
*   Milestone: Uporablja se za določanje ciljne verzije in datuma (Za kreiranje novega je potrebno biti MASTER projekta)
*   Label: Uporabi za dodajanje vrste (bug, idea, future...). Če aktivno uporabljamo Labele, nam to skrajša čas filtriranja in iskanje prioritet za določen problem.
*******

Fork in Merge projekta
--------------
Če vidimo projekt na katerem želimo delati in je public lahko pritisnemo **fork**, s čimer skopiramo projekt k sebi. Na novem projektu lahko nemoteno nadaljujemo delo in ga prilagodimo zase. Če popravimo kodo za boljše delovanje jo lahko vrnemo nazaj k avtorju, v zavihku merge request.

Ko imamo nekaj popravkov jih pushamo na server in potem na novem projektu ustvatrimo merge request s:

*   Source: Naš projekt, Naš branch

*   Destination: Projekt na katerega ciljamo, Branch na katerega ciljamo
    


******

Wiki
-----
Wiki uporabljamo za razširjeno dokumetacijo in prav tako uporablja Markdown language.

Najprej uredimo INDEX stran, ki vsebuje osnovne podatke in linke na ostale strani, nato pa v zavihku pages dodamo novo stran.

************

Snippets
----------
V zavihku snippets lahko dodajamo manjše koščke kode, ki lahko služijo kot smernice in pokazatelji. Snippet uporabimo zato, da nam ni potrebno pisati celega programa, ampak lahko vanj zapišemo le nekaj vrstic.


***********

Ekipa projekta
--------------
V zavihku *Settings* lahko v kategoriji ekipa dodamo uporabnike v ekipo in jim dodelimo status. Tako lahko dodamo kot člana ekipe npr. Janeza Novaka, ki bo imel določeno vlogo:

*   Guest: ima manj pravic kot public uporabnik, in pride v poštev pri zasenih projektih, Ne more kopirati projekta, niti downloadati le tega.
*   Reporter: lako downloada in kopira projekt in napiše snippet
*   Developer: je član ekipe, ki lahko poleg naštetega ureje wiki, in poda merge zahtevek, in pusha kodo nazaj v repozitorij.

************
SSH ključi
---------------
Uporabljajo se za olajšan dostop iz konzole. Na PC si zgeneriramo RSA ključ, in potem lahko nalagamo na server brez uporabniškega imena in gesla.
Primer kreacije ključa:

        ssh-keygen -t rsa -C "<email_naslov>"
        $ssh-keygen -t rsa -C "jenez.novak@smartis.si"

Iz datoteke *.rsa.pub kopiramo vsebino v spletni obrazec. Nato lahko vse zahtevke iz konzole namesto z http urljem zaganjamo z ssh requestom.
**************
Services
----------
Povežemo zunanje servise z gitlabom, npr. instant messenger spletne aplikacije...

***********

Protected Branches
-------------------
Tukaj lahko zaščitimo svoj branch, da lahko vanj piše samo član skupine z vlogo *master*
******************
Logi
-------------
Git nam omogoča enostavno beleženje dela z logi. Za vsak commit se shrani komentar, identifikator, čas commita, spremembe...

Osnovni pregled (id, uporabnik, čas in sporočilo) lahko vidimo z ukazom:

        $git log

Če hočemo videti enostavno verzijo (skrajšan id, komentar) lahko uporabimo:

        $git log --oneline

Če pa hočemo poleg osnovnega pregleda videti tudi spremembe datotek pa uporabimo:

        $git log --stat

Če hočemo videti natančno zgodovino sprememb (Za vsako vrstico) uporabimo:

        $git log --patch

Ukaze lahko tudi kombiniramo, in tako za ukaz graph (ki nam prikaže zgodovino v obliki toka) dobimo uporaben izpis:

        $git log --graph --all --decorate --oneline

Seveda so vsi tej pregledi vidni tudi na spletnem portalu
**************
Izdelava poročil dela z LOG-i
-------------------------------
Za uporabna poročila je potrebna aktivna uporaba commita.

Primer takega loga s časovno selekcijo:

        git log --author=<Ime> --since=<od> --until=<do> --format
        za časovno selekcijo se lahko uporabi tudi npr. '1 monday ago' ali 'last monday' --format=<format> --no-merges
        $git log --author=Klemen --since='2 sunday ago' --until='now' --format='%Cgreen%ci%Creset %s%Creset' --no-merges

Lahko si nastavimo presete, ki nam potem služijo za enostaven prikaz (uredi datoteko .git/config):

        [alias]

        <ime_komande>=<komanda>
        report-2-weeks="log --author=Klemen --since='2 sunday ago' --until='now' --format='%Cgreen%ci%Creset %s%Creset' --no-merges"

**Pazi na gnezdenje narekovajev**

Poročilo lahko zapišemo v datoteko enostavno z:

        $git report-2-weeks > porocilo.txt

Več o formatiranju na [povezavi](https://www.kernel.org/pub/software/scm/git/docs/git-log.html).
**************

**! Pred zagonom se prepričajte, da so programi, ki jih želite nameščeni na runner računalniku. Za namestitev sem na voljo preko emaila.**

*************

**Dokumentacijo pripravil Klemen Kogovšek, klemen.kogovsek@smartis.si**

Več informacij lahko dobite v brezplačni knjigi, ki se nahaja na [tem](http://git-scm.com/book/en/) spletnem naslovu.
