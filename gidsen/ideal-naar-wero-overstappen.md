---
title: "iDEAL naar Wero overstappen: stappenplan webshop"
canonical: https://www.joepify.nl/kennisbank/ideal-naar-wero-overstappen
updated: 2026-10-15
author: Ayoub Assaidi (Joepify)
license: CC BY 4.0
---

# iDEAL naar Wero overstappen: stappenplan webshop

> Origineel en altijd actueel: https://www.joepify.nl/kennisbank/ideal-naar-wero-overstappen  
> Bijgewerkt: 2026-10-15 · Auteur: Ayoub Assaidi, [Joepify](https://www.joepify.nl) (Rotterdam)

**Kort antwoord:** bij de meeste webshops regelt je betaalprovider (PSP) de overstap van iDEAL naar Wero, en hoef je zelf weinig te doen. Stripe is een uitzondering: daar voeg je Wero in de loop van 2026 en 2027 zelf toe in het dashboard. Wat je altijd doet: uitzoeken welke route jouw webshop heeft, het logo "iDEAL | Wero" controleren, je betaalplugin bijwerken en een testbetaling doen. Uiterlijk eind 2027 moet iedere webshop met iDEAL zijn overgestapt.

## Wat doe je zelf en wat doet je PSP?

Dit is de stap-voor-stap gids. Wil je eerst begrijpen *wat* er verandert, aan kosten, logo en tijdlijn, lees dan [iDEAL Wero: wat er verandert voor je webshop](https://www.joepify.nl/kennisbank/ideal-wero-webshop). Hier gaat het erom wat je doet.

iDEAL zelf schrijft op [de pagina naar Wero](https://ideal.nl/naar-wero) dat je checkout blijft werken, je PSP hetzelfde blijft en je in fase 1 niets hoeft aan te passen. Je PSP zorgt voor de updates en het nieuwe logo. Dat klopt voor een webshop die via een geïntegreerde plugin of app van haar PSP betaalt. Het klopt minder als je zelf een koppeling of eigen betaalscherm hebt, en niet voor elke provider hetzelfde. Daarom eerst uitzoeken waar jij staat.

## Stap 1: zoek uit welke route jouw webshop heeft

Open de instellingen van je webshop en kijk bij betaalmethodes:

- **Via Shopify Payments:** Shopify noemt de betaalmethode al ["iDEAL | Wero"](https://help.shopify.com/en/manual/payments/shopify-payments/local-payment-methods/ideal). Een migratiestap voor winkeliers staat niet in die handleiding. Ik zou er niets op aanpassen en alleen de testlijst hieronder doen.
- **Via een PSP met plugin of app** (Mollie, Stripe, Adyen, Buckaroo, MultiSafepay, Pay.nl en anderen): de plugin of app toont de betaalmethode en het logo. Jouw taak is de plugin actueel houden.
- **Eigen koppeling of eigen betaalscherm:** dan laat je zelf logo's en teksten staan, en ben jij of je bouwer verantwoordelijk voor de aanpassing.

Weet je het niet? Vraag je webbouwer of PSP: "Draait onze iDEAL via een standaardplugin of via een eigen koppeling?" Dat antwoord bepaalt hoeveel werk dit is.

## Stap 2: wat zeggen de PSP's zelf?

Ik heb de officiële documentatie van een paar providers bekeken. Dit is wat daar op 15 oktober 2026 staat, niet meer.

- **Stripe:** de [migratiepagina van Stripe](https://support.stripe.com/questions/ideal-to-wero-migration) beschrijft drie fasen. Eerst de co-branding "iDEAL | Wero" (29 januari tot 31 maart 2026). Die was automatisch voor Stripe's eigen schermen (Payment Element, Hosted Checkout, Hosted Invoices) en handwerk voor maatwerk-koppelingen. Daarna volgt vanaf het vierde kwartaal van 2026 de volledige migratie: Wero toevoegen als betaalmethode en iDEAL uitzetten, via het dashboard. Stripe raadt aan Wero eerst met een A/B-test in Nederlandse checkouts uit te proberen. Let op: op de [Wero-pagina van Stripe](https://docs.stripe.com/payments/wero) staan als klantlocaties nu alleen België, Frankrijk en Duitsland. Kijk in je dashboard of Wero voor Nederlandse klanten al beschikbaar is voordat je iDEAL uitzet.
- **Mollie:** de [Wero-pagina van Mollie](https://docs.mollie.com/docs/wero) noemt Wero als eigen betaalmethode in de Payments API (methodenaam `wero`). Een migratiehandleiding van iDEAL naar Wero heb ik in de documentatie niet gevonden. Kom je via de Mollie-plugin, dan kies je je methodes in het Mollie-dashboard en laat je de plugin bijwerken.
- **Adyen:** de iDEAL-pagina in de Adyen-documentatie heet inmiddels ["iDEAL | Wero"](https://docs.adyen.com/payment-methods/ideal/). Welke stappen je account precies nodig heeft, kon ik daar niet afleiden. Vraag het je accountmanager.
- **Buckaroo en MultiSafepay:** Buckaroo heeft in de documentatie een aparte [Wero-pagina](https://docs.buckaroo.io/docs/wero), maar daar staat geen migratiedatum voor iDEAL-webshops. Voor MultiSafepay heb ik geen officiële Wero-migratiepagina kunnen vinden. Vraag het in beide gevallen je contactpersoon bij de provider.

Het verschil tussen Stripe en de rest is dus niet dat Stripe strenger is. Stripe publiceert simpelweg een duidelijk stappenplan met data. Bij de anderen heb ik dat niet kunnen bevestigen, en dan verzin ik niets.

## Stap 3: controleer je logo en je teksten

De brandingronde van iDEAL liep van 29 januari tot **31 maart 2026** en is dus voorbij. Volgens de [brandingrichtlijnen](https://ideal.nl/ideal-wero-branding) moet het oude logo overal zijn vervangen: checkout, betaalpagina, hulpteksten, e-mailsjablonen en in-app flows. Stripe waarschuwt zelfs dat iDEAL op je account kan worden gedeactiveerd als je de branding niet op tijd hebt bijgewerkt. Loop dus na:

- je checkout en betaalpagina, op desktop en telefoon;
- footer, veelgestelde vragen en pagina's over betalen of verzenden;
- bevestigingsmails en facturen;
- eigen afbeeldingen van betaallogo's in je thema (een veelgemaakte fout: plugin bijgewerkt, maar het logo in de footer is een eigen plaatje).

## Stap 4: werk je platform en plugin bij

- **Shopify:** geen apart migratiewerk bekend. Wel handig: controleer of je winkel openbaar is, euro als valuta heeft en een juridische kennisgeving met bedrijfsgegevens, die Shopify voor iDEAL | Wero vraagt.
- **WooCommerce:** betalen loopt via de plugin van je PSP. Maak eerst een back-up, werk de plugin bij in een testomgeving en test daar een betaling. Pas daarna live.
- **Lightspeed en andere hosted platformen:** hier heb ik geen officiële migratiepagina gevonden. De betaalkoppeling wordt daar meestal door het platform of je PSP beheerd. Vraag beiden schriftelijk of er iets van jou nodig is.

## Stap 5: de vragen voor je PSP

Mail je PSP en vraag dit, zodat je het zwart op wit hebt:

1. Wanneer wordt mijn account op Wero gezet, en moet ik daar zelf iets voor aanzetten?
2. Vanaf welke pluginversie werkt het, en welke versie draai ik nu?
3. Wat worden mijn tarieven per betaling en wanneer gaan ze in?
4. Blijft iDEAL tijdens de overgang gewoon naast Wero werken?
5. Hoe werken terugbetalingen? Stripe noemt voor iDEAL | Wero een termijn van 180 dagen en voor Wero 730 dagen, dus dat verschilt per product.

## Stap 6: test voordat het live gaat

1. Doe een echte kleine betaling met iDEAL op je telefoon, vanuit je bankapp.
2. Kijk of je terugkomt op je bedankpagina en of de bevestigingsmail binnenkomt.
3. Kijk of de bestelling in je beheer op "betaald" staat.
4. Doe een terugbetaling en controleer dat die goed doorkomt.
5. Controleer je aankoopmeting. Verloopt die via de bedankpagina, lees dan [wat er na de Shopify checkout upgrade verviel](https://www.joepify.nl/kennisbank/shopify-checkout-extensibility).

## Welke data gelden er?

- **29 januari tot 31 maart 2026:** nieuw logo "iDEAL | Wero" invoeren (voorbij).
- **Vanaf Q4 2026:** bij Stripe de volledige migratie: Wero toevoegen, iDEAL uitzetten.
- **Eind oktober 2026:** eerste volledige Wero-betalingen in Nederland gepland, volgens [Thuiswinkel.org](https://www.thuiswinkel.org/nieuws/informatiesessie-betalingsverkeer-een-terugkoppeling/).
- **Uiterlijk eind 2027:** iedere webshop met iDEAL is overgestapt.

Data kunnen schuiven. Hou de pagina van je eigen PSP in de gaten, want die is leidend voor jouw account.

## Fouten die ik vaak tegenkom

- Wachten tot "het vanzelf gaat" en niet weten of je een standaardplugin of eigen koppeling hebt.
- Bij Stripe iDEAL uitzetten voordat Wero voor Nederlandse klanten werkt.
- Een oud betaallogo in footer of mail laten staan.
- Plugin bijwerken op de live winkel zonder testbetaling.

## Zo controleer je het

Loop je checkout door tot de betaalstap en kijk welk logo je ziet. De [website check](https://www.joepify.nl/website-apk#apk-modules) ziet of iDEAL op je site staat en geeft een seintje over de overstap naar Wero. Het logo in je checkout controleert hij niet, en hij rekent nooit af. Heb je een Shopify-winkel, doe dan ook de [Shopify winkel check](https://www.joepify.nl/shopify-winkel-check). Wil je dat ik de plugins, het logo en een testbetaling nalopen? Dat doe ik via [Shopify beheer](https://www.joepify.nl/shopify-beheer) of [WooCommerce webshop](https://www.joepify.nl/woocommerce-webshop-laten-maken).

- Gratis tool[Heb je een Shopify-winkel? Doe ook de gratis Shopify winkel check](https://www.joepify.nl/shopify-winkel-check)
- Liever uitbesteden[Laat Joepify dit doen: betaalmethodes en logo nalopen met Shopify beheer](https://www.joepify.nl/shopify-beheer)

---
Bron: [iDEAL naar Wero overstappen: stappenplan webshop](https://www.joepify.nl/kennisbank/ideal-naar-wero-overstappen) · Licentie: CC BY 4.0, noem Joepify met een link naar de originele pagina.
