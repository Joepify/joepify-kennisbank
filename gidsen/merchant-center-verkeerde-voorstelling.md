---
title: "Merchant Center geschorst: verkeerde voorstelling oplossen"
canonical: https://www.joepify.nl/kennisbank/merchant-center-verkeerde-voorstelling
updated: 2026-10-14
author: Ayoub Assaidi (Joepify)
license: CC BY 4.0
---

# Merchant Center geschorst: verkeerde voorstelling oplossen

> Origineel en altijd actueel: https://www.joepify.nl/kennisbank/merchant-center-verkeerde-voorstelling  
> Bijgewerkt: 2026-10-14 · Auteur: Ayoub Assaidi, [Joepify](https://www.joepify.nl) (Rotterdam)

**Kort antwoord:** een schorsing wegens "verkeerde voorstelling" (in het Engels: misrepresentation) betekent dat Google je webshop niet genoeg vertrouwt. Bijna altijd zit het in dingen die je zelf kunt herstellen: bedrijfsgegevens die op verschillende pagina's anders zijn, een onduidelijk retour- of verzendbeleid, prijzen die niet overeenkomen tussen je feed en je site, of kosten die pas in de checkout verschijnen. Herstel eerst alles, controleer het nog een keer, en vraag dan pas een nieuwe beoordeling aan.

## Wat bedoelt Google met verkeerde voorstelling?

Het [beleid tegen verkeerde voorstelling](https://support.google.com/merchants/answer/6150127?hl=nl) verbiedt vermeldingen of websites die gebruikers misleiden, door belangrijke informatie weg te laten of door misleidende informatie te geven over producten of over je bedrijf. Google noemt onder andere:

- een valse identiteit, bedrijfsnaam of valse contactgegevens tonen;
- retouren en terugbetalingen weigeren terwijl je een retourbeleid hebt;
- producten als beschikbaar tonen die je niet kunt leveren;
- verbergen waar je producten vandaan worden verzonden.

Google kijkt daarbij niet alleen naar je feed, maar ook naar je website, je accounts en bronnen van derden. Bij ernstige schendingen schorst Google zonder waarschuwing. Bij sommige andere onderdelen van het beleid krijg je eerst een waarschuwing, minstens 7 dagen voor de schorsing.

Het lastige: Google zegt meestal niet precies wat er mis is. Daarom loop je je hele shop na, niet alleen het product dat werd afgekeurd.

## De fouten die het vaakst spelen

### 1. Bedrijfsgegevens kloppen niet overal

Je adres in de footer is anders dan op je contactpagina, in je algemene voorwaarden staat nog een oud adres of zelfs een placeholder als "\[ADRES\]", of je bedrijfsnaam in Merchant Center wijkt af van die op je site. Zet overal dezelfde naam, hetzelfde adres, telefoonnummer, e-mailadres en KvK-nummer. In Nederland moet je die gegevens toch al tonen, zie [KvK-nummer op je website](https://www.joepify.nl/kennisbank/kvk-nummer-op-website).

### 2. Retour- en verzendbeleid ontbreekt of is vaag

Google vraagt om [duidelijke, goed zichtbare informatie over retouren en terugbetalingen](https://support.google.com/merchants/answer/10220642?hl=nl) op je website, en dat beleid moet gelden voor meer dan alleen kapotte producten. Maak een aparte retourpagina en een verzendpagina, link ze in je footer en zorg dat wat erin staat gelijk is aan je instellingen in Merchant Center. Vergeet de wettelijke bedenktijd van 14 dagen en je [herroepingsknop](https://www.joepify.nl/kennisbank/herroepingsknop-webshop) niet.

### 3. Prijs, voorraad of levertijd verschilt

De prijs in je feed, de prijs op je productpagina, de prijs in je gestructureerde data en de prijs in de checkout moeten gelijk zijn. Hetzelfde geldt voor voorraad: een product dat in de feed "op voorraad" is maar op de site "uitverkocht", is een probleem. Kijk ook naar nep-kortingen: een doorgestreepte prijs waarvoor je nooit echt hebt verkocht.

### 4. Kosten die pas in de checkout verschijnen

Verzendkosten, toeslagen voor betaalmethoden of verplichte extra's moeten vooraf duidelijk zijn. Toon verzendkosten op de productpagina of in je winkelwagen, niet pas bij de laatste stap.

### 5. Je site ziet er onaf of onbetrouwbaar uit

Lege pagina's, lorem ipsum, reviews die op elk product hetzelfde zijn, geen "Over ons", een contactformulier zonder andere manier om je te bereiken. Elk los punt is klein, samen maken ze een webshop verdacht.

### 6. Productdata is onvolledig

Ontbrekende of verzonnen GTIN's (barcodes) en een ontbrekend merk zorgen voor minder zichtbaarheid. Google schrijft dat je [geen GTIN moet raden of verzinnen](https://support.google.com/merchants/answer/6324461?hl=nl). Heb je eigen producten zonder barcode, geef dat dan zo aan in je feed.

## Stappenplan voor herstel

1. **Maak een lijst van je bedrijfsgegevens** zoals ze in het Handelsregister staan. Dat is je referentie.
2. **Loop elke pagina langs:** footer, contact, over ons, algemene voorwaarden, privacyverklaring, retour, verzending. Pas alles aan naar dezelfde gegevens.
3. **Controleer Merchant Center**: bedrijfsnaam, adres, telefoonnummer, retourbeleid en verzendinstellingen moeten gelijk zijn aan je site.
4. **Vergelijk vijf producten** van begin tot eind: feed, productpagina, gestructureerde data (test met de [test voor rich results](https://search.google.com/test/rich-results)) en checkout. Prijs, voorraad, levertijd en verzendkosten moeten hetzelfde verhaal vertellen.
5. **Haal wat niet klopt weg:** nep-reviews, onware claims ("de goedkoopste van Nederland"), kortingen zonder echte oude prijs.
6. **Controleer je checkout als gast**: geen verrassende kosten, duidelijk welke betaalmethoden er zijn.
7. **Vraag een beoordeling aan**, pas als alles klopt. Volgens Google worden geschorste accounts alleen hersteld als het bezwaar zeer overtuigend is. Leg kort en eerlijk uit wat je hebt aangepast.

Een herstel kan dagen tot weken duren. Een garantie dat Google je account terugzet, kan niemand je geven, ook ik niet. Wel kun je zorgen dat er niets meer te vinden is waar Google over kan vallen.

## Shopify en WooCommerce

In Shopify koppel je Merchant Center via het Google & YouTube-kanaal. Controleer daar na elke wijziging van je beleidspagina's of de juiste pagina's zijn gekoppeld, en kijk in *Instellingen* en dan *Beleid* of er geen oude teksten staan. In WooCommerce komen feeds vaak uit een plugin: controleer dat die de prijs inclusief btw doorgeeft, net als je site. Je structured data komt meestal uit je SEO-plugin of je thema. Twee bronnen tegelijk geven soms twee verschillende prijzen.

## Wat de website APK hierbij checkt

Het onderdeel Google Shopping van de [website check](https://www.joepify.nl/website-apk#apk-modules) kijkt naar de dingen die Google ook ziet: of je contactgegevens consistent zijn, of retour- en verzendpagina's te vinden zijn, of je productpagina gestructureerde data heeft met prijs, voorraad, merk of GTIN, en of de valuta klopt. Het onderdeel wettelijke plichten controleert KvK-nummer, adres en voorwaarden. Draai je op Shopify, kijk dan ook naar de [Shopify winkel check](https://www.joepify.nl/shopify-winkel-check).

- Gratis tool[Verkoop je via Shopify? Doe ook de gratis Shopify winkel check](https://www.joepify.nl/shopify-winkel-check)
- Liever uitbesteden[Laat je winkel op orde houden met Shopify beheer](https://www.joepify.nl/shopify-beheer)

---
Bron: [Merchant Center geschorst: verkeerde voorstelling oplossen](https://www.joepify.nl/kennisbank/merchant-center-verkeerde-voorstelling) · Licentie: CC BY 4.0, noem Joepify met een link naar de originele pagina.
