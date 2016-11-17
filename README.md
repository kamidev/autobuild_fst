[![Build Status](https://travis-ci.org/rinfo/fst.svg?branch=develop)](https://travis-ci.org/rinfo/fst) _Källkoden byggs och testas varje natt_

##FST (Föreskriftshantering som tjänst)##

FST är en webbtjänst för att publicera rättsinformationsdokument och dess metadata. Tjänsten har utvecklats för svenska myndigheter som vill publicera föreskrifter och andra dokument som öppna data. 

FST är ett komplement till befintliga IT-lösningar: användare laddar upp befintliga dokument och tillhörande metadata i ett enkelt webbgränssnitt. Den inmatade informationen omvandlas automatiskt till ett strukturerat format och publiceras via ett ATOM/RSS-nyhetsflöde.


###Att komma igång och använda FST###

Här finns en kort guide som beskriver hur du installerar FST på din egen dator för att provköra eller kanske göra en demo. _Text på engelska_ 

[[Installera FST på en utvecklingsmaskin |Install on development machine]]

Användarhandledningen är till för dig som vill använda FST när tjänsten är installerad. 
Texten är på svenska och riktar sig till handläggare och jurister. 

[Användarhandledning](https://github.com/rinfo/fst/blob/develop/doc/anvandarhandledning_fst.pdf)

Det finns också en detaljerad guide som beskriver hur du installerar FST som tjänst på en publik server. _Text på engelska_ 

[[Installera FST som tjänst på en server |Server installation FST]]

###Mer information###

_For more detailed technical information in English, see [here](https://github.com/rinfo/fst/wiki)_

FST är implementerat med programspråket Python och webbramverket Django. Django är öppen källkod och har en stark community och utmärkt dokumentation.

Working through this tutorial will help you understand how the code works. In particular, pay attention to the parts about the Django admin interface.

De tekniska specifikationerna bakom FST finns beskrivna här: http://dev.lagrummet.se/dokumentation/#specifikationer (text in Swedish). 
Notera särskilt ([begreppsmodellen för svensk rättsinformation](http://dev.lagrummet.se/dokumentation/model.pdf)), [användandet av nyhetsflöden för publicering](http://dev.lagrummet.se/dokumentation/system/atom-insamling.pdf) och [principer för att skapa persistenta identifierare (URI:er)](http://dev.lagrummet.se/dokumentation/system/uri-principer.pdf), som är den tekniska grunden för FST. 

_Obs! Delar av den icke-tekniska projektdokumentation kan vara föråldrad._

 Rättsinformationsprojektet may be outdated.
FST development


###Nästa steg###

Arbeta med testdatabasen

Lägga upp egen myndighet

###Tjänstens delar###

Några saker att utgå från:

1. Filen urls.py visar vilka olika typer av länkar som webbplatsen
hanterar.  Varje länkformat är kopplat till en metod i rinfo/views.py.

2. I fst_web/models.py hittar du klasserna för de olika
informationsobjekten.  Klassen Myndighetsforeskrift visar några olika
typer av metadata och relationer till andra objekt.

3. Atomfeeden berättar om förändringar som skett med poster i
samlingen. Feeden finns på adressen http://127.0.0.1:8000/feed/. När man publicerar ett dokument skapas AtomEntry-objekt.  Dessa sammanställs i en feed i fst_web/templates/atomfeed.xml, som i sin tur
använder fst_web/templates/foreskrift_entry.xml .

Eftersom applikationen är baserad på ramverket Django kan det vara bra
att känna till grunderna om detta. Mer information om Django hittar du
här: http://docs.djangoproject.com/en/dev/intro/overview/

###Licens###
 
FST ges ut under BSD-licensen. Det betyder att du får
använda och vidareutveckla koden om du vill, även i kommersiella
sammanhang, men att den inte kommer med några garantier för funktion
eller lämplighet. Se BSD-licensen för mer information om möjligheter
att använda dig av programkoden.

