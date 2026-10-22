---
title: "GPSR voor je webshop: wat moet op je productpagina?"
canonical: https://www.joepify.nl/kennisbank/gpsr-webshop
updated: 2026-10-14
author: Ayoub Assaidi (Joepify)
license: CC BY 4.0
---

# GPSR voor je webshop: wat moet op je productpagina?

> Origineel en altijd actueel: https://www.joepify.nl/kennisbank/gpsr-webshop  
> Bijgewerkt: 2026-10-14 · Auteur: Ayoub Assaidi, [Joepify](https://www.joepify.nl) (Rotterdam)

**Kort antwoord:** sinds 13 december 2024 geldt de Europese productveiligheidsverordening, de GPSR ([Verordening (EU) 2023/988](https://eur-lex.europa.eu/eli/reg/2023/988/oj/nld)). Verkoop je fysieke consumentenproducten online, dan moet volgens artikel 19 op elke productpagina staan: de naam en het post- en e-mailadres van de fabrikant, bij een fabrikant buiten de EU ook de verantwoordelijke persoon in de EU, gegevens waarmee je het product herkent (afbeelding, type, eventueel ander identificatienummer) en alle waarschuwingen en veiligheidsinformatie in het Nederlands. Bol eist deze gegevens sinds 5 maart en 1 april 2026 bij elk artikel.

## Wat is de GPSR en geldt hij voor jou?

De GPSR (General Product Safety Regulation) vervangt de oude richtlijn algemene productveiligheid. Het is een verordening, dus hij geldt rechtstreeks in Nederland zonder aparte Nederlandse wet. Volgens [artikel 52](https://eur-lex.europa.eu/eli/reg/2023/988/oj/nld) is hij van toepassing met ingang van 13 december 2024. In Nederland houdt de [NVWA](https://www.nvwa.nl/onderwerpen/productveiligheid/gpsr-productveiligheidsverordening) toezicht.

Hij geldt voor bijna alle fysieke producten die bij consumenten terecht kunnen komen: kleding, speelgoed, cosmetica-accessoires, meubels, sieraden, elektronica, sportartikelen. Ook tweedehands, gerepareerde en gereviseerde producten vallen eronder (artikel 2, lid 3). Uitgezonderd zijn onder meer levensmiddelen, geneesmiddelen, diervoeder, levende planten en dieren, gewasbeschermingsmiddelen en antiek (artikel 2, lid 2).

Geldt er voor jouw product al specifieke Europese wetgeving, zoals de speelgoedrichtlijn of CE-regels voor elektronica? Dan vult de GPSR die aan voor de risico's die daar niet onder vallen. De informatieplicht voor online verkoop geldt in de praktijk voor vrijwel elke webshop met fysieke producten.

Verkoop je alleen diensten of digitale producten, dan heb je met de GPSR weinig te maken.

## Wat moet er op elke productpagina?

Artikel 19 zegt dat bij online verkoop "ten minste de volgende informatie duidelijk en zichtbaar" in het aanbod staat:

1. **De fabrikant:** naam, geregistreerde handelsnaam of handelsmerk, plus het postadres en het elektronische adres (meestal een e-mailadres) waarop hij bereikbaar is.
2. **De verantwoordelijke persoon in de EU**, als de fabrikant niet in de EU gevestigd is: naam, postadres en elektronisch adres. Dat is bijvoorbeeld de importeur of een gemachtigde.
3. **Productidentificatie:** een afbeelding van het product, het type en eventuele andere identificatie, zoals een model-, partij- of serienummer of EAN.
4. **Waarschuwingen en veiligheidsinformatie** die op het product, de verpakking of de bijsluiter moeten staan, in een taal die de consument makkelijk begrijpt. Voor Nederland is dat Nederlands.

Let op het woord "aanbod": het gaat om de productpagina zelf, niet om een algemene pagina ergens in je footer. Een link "veiligheidsinformatie" die op de productpagina naar het juiste document leidt, kan, zolang het per product klopt en goed te vinden is.

## Wie is de fabrikant als je zelf inkoopt?

Dit is het lastigste deel voor veel webshops. Drie situaties:

- **Je verkoopt A-merken uit de EU.** Dan is het merk de fabrikant. Vraag je leverancier om de officiële naam, het adres en het contactadres van de fabrikant en zet die per merk in je productdata.
- **Je importeert zelf van buiten de EU**, bijvoorbeeld uit China. Dan ben jij vaak de importeur. Er moet een in de EU gevestigde marktdeelnemer zijn die verantwoordelijk is voor het product (artikel 16). Als jij dat bent, staat jouw bedrijf als verantwoordelijke op de pagina, naast de fabrikant.
- **Je verkoopt onder je eigen merknaam** (private label). Dan geldt jij in de regel als fabrikant, met alle plichten die daarbij horen, zoals een risicoanalyse en technische documentatie (artikel 9).

Dropshipping uit een land buiten de EU zonder dat iemand in de EU verantwoordelijk is, mag niet meer: artikel 16 zegt dat zo'n product dan niet in de handel gebracht wordt.

## Wat eist bol?

Verkoop je ook via bol, dan heb je met de strengste handhaving te maken. Volgens het [partnerplatform van bol](https://partnerplatform.bol.com/nl/idp/gpsr) gaat nieuw aanbod zonder fabrikantgegevens sinds 5 maart 2026 niet meer online, en sinds 1 april 2026 ook niet zonder gegevens van de verantwoordelijke marktdeelnemer. Bestaand aanbod zonder fabrikantgegevens haalt bol vanaf 1 april 2026 stapsgewijs offline; bol zegt dat je per mail hoort wanneer dat voor jouw assortiment gebeurt.

Gebruik dezelfde gegevens in je eigen webshop. Dan heb je het één keer goed en voorkom je dat je op twee plekken verschillende adressen hebt staan.

## Zo zet je het in Shopify en WooCommerce

De gegevens zijn per merk of leverancier meestal gelijk. Daarom werk je het handigst met een vaste set velden die je aan producten koppelt:

- **Shopify:** maak productmetavelden aan, bijvoorbeeld "Fabrikant", "Adres fabrikant", "Contact fabrikant", "Verantwoordelijke in de EU" en "Veiligheidsinformatie". Toon ze in je productsjabloon via een blok in de thema-editor, bijvoorbeeld in een uitklapblok "Productveiligheid". Een metaobject per fabrikant voorkomt dat je hetzelfde adres honderd keer typt.
- **WooCommerce:** gebruik productattributen of eigen velden en laat je thema ze op de productpagina tonen, bijvoorbeeld in een extra tabblad. Er zijn plugins voor GPSR-velden, maar controleer of ze echt op de productpagina zichtbaar worden.
- **Bulk vullen:** exporteer je producten als CSV, vul de velden per merk en importeer opnieuw. Voor feeds naar bol of andere marktplaatsen gebruik je dezelfde velden.

Waarschuwingen horen in gewone, leesbare tekst. Een foto van de achterkant van de verpakking is voor een schermlezer niet te lezen en is in het Engels of Chinees niet genoeg.

## Wat als het misgaat?

De GPSR laat de boetes aan de lidstaten over (artikel 44): ze moeten "doeltreffend, evenredig en afschrikkend" zijn. Het directe risico voor de meeste webshops is minder dramatisch maar wel vervelend: een marktplaats die je aanbod offline haalt, een vraag van de NVWA, of een klant die na een ongeluk niet weet wie de fabrikant is. Bij een gevaarlijk product moet je samen met de fabrikant of importeur kunnen handelen, inclusief een terugroepactie.

## Fouten die ik vaak tegenkom

- **Alleen je eigen bedrijfsgegevens** in de footer, maar nergens de fabrikant. Je eigen KvK-gegevens zijn een aparte plicht (zie [KvK-nummer op je website](https://www.joepify.nl/kennisbank/kvk-nummer-op-website)).
- **Een fabrikant zonder adres**, alleen een merknaam of een webadres.
- **Geen EU-verantwoordelijke** bij producten van een fabrikant buiten de EU.
- **Waarschuwingen alleen op de verpakking**, niet online. De klant moet ze vóór de aankoop kunnen lezen.
- **Gegevens alleen in de feed** voor bol, maar niet op je eigen productpagina's.

## Zo controleer je het

Open drie willekeurige productpagina's op je telefoon en zoek de fabrikant, het adres, het contactadres en de waarschuwingen op. Kun je ze niet binnen een paar tellen vinden, dan vindt je klant of de toezichthouder ze ook niet. Doe daarna de gratis [website check](https://www.joepify.nl/website-apk) voor de andere wettelijke plichten van je webshop, zoals je bedrijfsgegevens en de [herroepingsknop](https://www.joepify.nl/kennisbank/herroepingsknop-webshop). Wil je dat iemand de velden in je Shopify-thema inbouwt en vult, kijk dan bij [Shopify beheer](https://www.joepify.nl/shopify-beheer).

## Wat de website APK hierbij checkt

De website APK zoekt op een productpagina van je webshop naar fabrikant- of verantwoordelijkengegevens. Vindt hij die niet, dan krijg je een waarschuwing. Het is een aanwijzing, geen volledige controle: de APK bekijkt één productpagina en kan niet beoordelen of je waarschuwingen en veiligheidsinformatie compleet zijn. Daarnaast checkt het onderdeel wettelijke plichten je bedrijfsgegevens (KvK, btw-id, adres, e-mail, telefoon) en of er een herroepingsknop is. Loop de fabrikantgegevens per product dus ook zelf na met de stappen hierboven.

Dit artikel is algemene informatie en geen juridisch advies. Twijfel je wie in jouw keten de fabrikant of importeur is, vraag het je branchevereniging of een jurist.

- Gratis tool[Heb je een Shopify-winkel? Doe ook de gratis Shopify winkel check](https://www.joepify.nl/shopify-winkel-check)
- Liever uitbesteden[Laat je productpagina's bijwerken met Shopify beheer](https://www.joepify.nl/shopify-beheer)

---
Bron: [GPSR voor je webshop: wat moet op je productpagina?](https://www.joepify.nl/kennisbank/gpsr-webshop) · Licentie: CC BY 4.0, noem Joepify met een link naar de originele pagina.
