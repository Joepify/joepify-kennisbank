---
title: "Shopify checkout upgrade: tracking kwijt? Zo herstel je het"
canonical: https://www.joepify.nl/kennisbank/shopify-checkout-extensibility
updated: 2026-10-15
author: Ayoub Assaidi (Joepify)
license: CC BY 4.0
---

# Shopify checkout upgrade: tracking kwijt? Zo herstel je het

> Origineel en altijd actueel: https://www.joepify.nl/kennisbank/shopify-checkout-extensibility  
> Bijgewerkt: 2026-10-15 · Auteur: Ayoub Assaidi, [Joepify](https://www.joepify.nl) (Rotterdam)

**Kort antwoord:** sinds 26 augustus 2026 draaien ook winkels zonder Shopify Plus op de nieuwe Thank you- en Order status-pagina's. Code die je ooit in *Additional scripts* plakte of die een app via een script tag op de bedankpagina zette, werkt daar niet meer. Het gevolg: Google Ads-, Meta- en affiliate-aankopen worden vaak niet meer gemeten. Je herstelt dat met app pixels (de officiële apps van Google en Meta) of een custom pixel op het `checkout_completed`-event, en daarna een testbestelling.

## Wat is er veranderd?

Shopify heeft de oude checkout, gebouwd op `checkout.liquid`, stap voor stap uitgezet. De stappen informatie, verzending en betaling gingen eerst. Daarna volgden de pagina's ná de betaling. Volgens de [documentatie van Shopify](https://shopify.dev/docs/storefronts/themes/architecture/layouts/checkout-liquid):

- **Shopify Plus:** Thank you- en Order status-pagina's en script tags daarop stopten op **28 augustus 2025**.
- **Alle andere abonnementen** (Basic, Grow, Advanced): deadline **26 augustus 2026**.
- **Additional scripts** is sinds 28 augustus 2025 voor iedereen alleen nog leesbaar. Je kunt die code dus niet meer aanpassen ([Shopify Help Center](https://help.shopify.com/en/manual/checkout-settings/checkout-extensibility/checkout-upgrade/thank-you-order-status)).

Bij de upgrade worden je bestaande bedankpagina en alle maatwerk daarop vervangen door de nieuwe versie. De nieuwe pagina's heten samen *checkout extensibility*: maatwerk loopt via blokken, apps en pixels in plaats van vrije HTML en JavaScript.

## Hoe merk je dat je tracking kapot is?

Het lastige is dat het niet als een storing aanvoelt. Het voelt als een slechte maand. In de Shopify Community beschrijven winkeliers precies dat: na 26 augustus daalden de aankopen in Google Ads en Meta, terwijl de bestellingen in Shopify gewoon doorliepen. Signalen:

- Google Ads of Meta toont sinds eind augustus veel minder aankopen dan je Shopify-admin.
- Slimme biedstrategieën (doel-ROAS, maximale conversiewaarde) presteren ineens slechter, omdat ze op minder conversies sturen.
- Affiliatepartners melden geen of minder sales.
- De opt-in van Google Klantenreviews op de bedankpagina is verdwenen.
- In **Instellingen > Checkout** staat nog oude code in Additional scripts. Dat is een sterke aanwijzing dat daar tracking stond die nu niet meer draait.

## Zo herstel je je aankoopmeting

### 1. Inventariseer wat er in Additional scripts stond

Open **Instellingen > Checkout** en kopieer de (alleen-lezen) code naar een tekstbestand. Zoek naar herkenbare stukken: `AW-` (Google Ads), `gtag` of `G-` (GA4), `fbq` (Meta), `GTM-` (Tag Manager), en scripts van affiliate- of reviewdiensten. Dat is je takenlijst.

### 2. Gebruik eerst de officiële apps

Voor Google en Meta is de makkelijkste route de officiële Shopify-app: Google & YouTube en Facebook & Instagram. Die installeren een **app pixel** die de aankoop meet op de nieuwe pagina's. Shopify raadt zelf aan om [app pixels te gebruiken om klantevents te blijven meten](https://help.shopify.com/en/manual/checkout-settings/checkout-extensibility/checkout-upgrade). Voor affiliate- en reviewdiensten: kijk of de dienst een Shopify-app met pixel heeft.

### 3. Wat er geen app voor is: een custom pixel

Onder **Instellingen > Klantevents** voeg je een custom pixel toe. Daarin luister je naar het standaardevent [`checkout_completed`](https://shopify.dev/docs/api/web-pixels-api/standard-events/checkout_completed). Dat event vuurt één keer per checkout, meestal op de Thank you-pagina. Gebruik je een upsell-app na de betaling, dan vuurt het op de eerste upsellpagina en niet nog een keer op de bedankpagina.

Twee dingen om te weten:

- Custom pixels draaien in een [sandbox](https://help.shopify.com/en/manual/promoting-marketing/pixels/custom-pixels). Niet alle code van derden werkt daarin, dus test altijd.
- Shopify ondersteunt custom pixels niet zelf. Jij bent verantwoordelijk voor de code en voor toestemming van de bezoeker.

### 4. Voorkom dubbele metingen

Een veelgemaakte fout na het herstellen: de Google-app meet de aankoop én een custom pixel of GTM-container meet hem nog een keer. Dan zie je ineens twee keer zoveel conversies. Kies per platform één bron en zet de andere uit.

### 5. Let op toestemming

App pixels en custom pixels houden rekening met de privacyinstellingen van je winkel. Werk je met een externe cookiebanner, controleer dan of de toestemming goed wordt doorgegeven. Vooral bij iDEAL, waar de klant even naar de bank gaat en terugkomt, raakt de toestemming soms kwijt. Lees ook [de regels voor je cookiebanner](https://www.joepify.nl/kennisbank/cookiebanner-regels).

### 6. Test met een echte bestelling

Plaats een kleine testbestelling en kijk in Google Ads (Doelen > Conversies, diagnose), Meta Events Manager en GA4 Realtime of de aankoop binnenkomt, één keer, met het juiste bedrag. Annuleer en restitueer de bestelling daarna.

## Wat blijft er nog over?

De bedankpagina is klaar, maar de volgende deadline komt eraan. Op **1 maart 2027** stoppen script tags ook in de rest van je winkel: productpagina's, collecties, homepage. Oudere review-, pop-up- en chatapps die nog zo werken, vallen dan stil. Dat lees je in [Shopify script tags stoppen op 1 maart 2027](https://www.joepify.nl/kennisbank/shopify-script-tags-2027).

## Fouten die ik vaak tegenkom

- **Denken dat de omzet daalt** en het advertentiebudget verlagen, terwijl alleen de meting kapot is.
- **De Google-app geïnstalleerd, maar het conversiedoel niet gekoppeld** in Google Ads, zodat de oude (dode) conversieactie nog primair staat.
- **GTM in het thema laten staan** en denken dat die ook de checkout meet. GTM in je `theme.liquid` komt niet op de bedankpagina.
- **Geen testbestelling doen.** Een pixel die er goed uitziet, kan in de sandbox alsnog falen.

## Zo controleer je het

Doe de gratis [website check](https://www.joepify.nl/website-apk) op je winkel. Die laat zien welke trackingcode in je thema staat en welke pixels Shopify meldt, zodat je ziet of je aankoopmeting via de nieuwe route loopt. Wil je dat iemand je tracking herstelt en test? Dat doe ik als onderdeel van [Shopify beheer](https://www.joepify.nl/shopify-beheer). Je kunt ook eerst de [Shopify winkel-check](https://www.joepify.nl/shopify-winkel-check) doen.

## Wat de website APK hierbij checkt

Het onderdeel platform en advertenties van de [website check](https://www.joepify.nl/website-apk#apk-modules) herkent een Shopify-winkel en kijkt in de openbare HTML welke tags in je thema staan (Google Ads, GA4, Meta, GTM) en welke app pixels en custom pixels Shopify laadt. Staat er een Google Ads-tag in je thema maar geen bijbehorende pixel, dan krijg je een waarschuwing. De APK plaatst geen testbestelling, dus of de aankoop echt binnenkomt, zie je alleen met stap 6 hierboven.

- Gratis tool[Doe ook de gratis Shopify winkel check](https://www.joepify.nl/shopify-winkel-check)
- Liever uitbesteden[Laat je tracking en apps bijhouden met Shopify beheer](https://www.joepify.nl/shopify-beheer)

---
Bron: [Shopify checkout upgrade: tracking kwijt? Zo herstel je het](https://www.joepify.nl/kennisbank/shopify-checkout-extensibility) · Licentie: CC BY 4.0, noem Joepify met een link naar de originele pagina.
