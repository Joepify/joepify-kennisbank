---
title: "Cookiebanner regels 2026: wat de AP controleert"
canonical: https://www.joepify.nl/kennisbank/cookiebanner-regels
updated: 2026-10-14
author: Ayoub Assaidi (Joepify)
license: CC BY 4.0
---

# Cookiebanner regels 2026: wat de AP controleert

> Origineel en altijd actueel: https://www.joepify.nl/kennisbank/cookiebanner-regels  
> Bijgewerkt: 2026-10-14 · Auteur: Ayoub Assaidi, [Joepify](https://www.joepify.nl) (Rotterdam)

**Kort antwoord:** gebruik je tracking cookies of meetcodes van bijvoorbeeld Google Ads, Meta of TikTok, dan moet je eerst toestemming vragen. Die codes mogen pas laden nadat de bezoeker "ja" zegt, weigeren moet net zo makkelijk zijn als accepteren en vinkjes mogen niet vooraf aanstaan. De Autoriteit Persoonsgegevens (AP) controleert dit sinds april 2025 structureel en heeft al meer dan 200 websites gewaarschuwd.

## Is een cookiebanner verplicht?

Niet altijd. De regel staat in [artikel 11.7a van de Telecommunicatiewet](https://wetten.overheid.nl/jci1.3:c:BWBR0009950&hoofdstuk=11&artikel=11.7a). De AP legt het uit met [drie soorten cookies](https://www.autoriteitpersoonsgegevens.nl/themas/internet-slimme-apparaten/cookies):

- **Functionele cookies**, zoals je winkelmandje of taalkeuze. Daarvoor heb je geen toestemming nodig. Je moet ze wel noemen, bijvoorbeeld in je privacyverklaring.
- **Beperkt analytische cookies** met geen of weinig gevolgen voor de privacy. Ook daarvoor is geen toestemming nodig, als ze echt aan die voorwaarde voldoen.
- **Overige cookies**, waaronder tracking cookies die je over meerdere websites volgen. Daarvoor heb je altijd toestemming nodig.

Gebruik je alleen functionele cookies, dan heb je geen banner nodig die om toestemming vraagt. Zodra er een Meta Pixel, Google Ads-tag, TikTok Pixel of een andere advertentiecode op je site staat, wel. Google Analytics in de standaardinstelling deelt gegevens met Google en valt daarom in de praktijk vaak niet onder "beperkt analytisch". Twijfel je, vraag dan toestemming.

## Wat controleert de AP?

In april 2025 stuurde de AP [de eerste 50 waarschuwingsbrieven](https://www.autoriteitpersoonsgegevens.nl/actueel/ap-waarschuwt-50-organisaties-om-misleidende-cookiebanner), onder meer naar webwinkels. De AP schrijft dat ze 10.000 Nederlandse websites monitort en elk jaar 500 organisaties wil waarschuwen. In november 2025 meldde de AP dat [meer dan 200 websites waren gewaarschuwd](https://www.autoriteitpersoonsgegevens.nl/actueel/ap-driekwart-websites-past-misleidende-cookiebanner-aan-na-waarschuwing-onderzoek-gestart-naar-weigeraars), dat ongeveer driekwart zijn banner had aangepast en dat de AP handhavingsstappen zet tegen de rest.

De fouten die de AP zelf noemt:

- de website plaatst al cookies voordat de bezoeker toestemming geeft;
- de toestemming voor tracking cookies staat al aangevinkt;
- bezoekers komen pas bij de weigerknop als ze doorklikken naar een volgend venster.

Hoe groot is de kans dat jij een brief krijgt? Dat weet niemand. Eerlijk gezegd: voor een kleine website is de kans kleiner dan voor een grote webshop. Maar de controle gaat automatisch, en de fouten zijn meestal in een uur te herstellen. Het is dus vooral een kwestie van het nu goed doen.

## De 9 vuistregels van de AP

Op de pagina [Heldere cookiebanners](https://www.autoriteitpersoonsgegevens.nl/themas/internet-slimme-apparaten/cookies/heldere-cookiebanners) geeft de AP negen vuistregels:

1. Geef informatie over de verwerking van persoonsgegevens en het doel.
2. Zet vinkjes niet automatisch aan.
3. Gebruik duidelijke tekst.
4. Zet verschillende keuzes op één laag.
5. Verberg bepaalde keuzes niet.
6. Laat iemand niet extra klikken.
7. Gebruik geen onopvallende link in de tekst.
8. Maak toestemming intrekken net zo makkelijk als toestemming geven.
9. Verwar toestemming niet met gerechtvaardigd belang.

Concreet betekent dat: een knop "Weigeren" of "Alleen noodzakelijk" naast "Accepteren", in dezelfde laag en even opvallend. Niet een grote groene knop en een grijs linkje.

## Zo test je je eigen cookiebanner in vijf minuten

1. Open je website in een privévenster in Chrome.
2. Klik nog nergens op. Open de ontwikkelaarstools (F12) en ga naar het tabblad *Netwerk*.
3. Herlaad de pagina en typ in het filterveld achter elkaar: `collect`, `facebook`, `tiktok`, `clarity` en `hotjar`.
4. Zie je verzoeken naar die diensten voordat je iets hebt gekozen? Dan laden je trackers te vroeg.
5. Kijk bij *Toepassing* en dan *Cookies* of er al cookies als `_ga`, `_fbp` of `_ttp` staan.
6. Klik daarna op "Weigeren", herlaad en kijk of het stil blijft.

Met Google [Consent Mode](https://www.joepify.nl/kennisbank/consent-mode-v2-uitleg) in de geavanceerde stand stuurt Google bij weigering wel pings zonder cookies. Dat is een bewuste keuze van Google en iets anders dan cookies plaatsen. Zie de [uitleg van Google over de toestemmingsmodus](https://developers.google.com/tag-platform/security/guides/consent?hl=nl).

## Hoe los je het op?

### WordPress en WooCommerce

Gebruik een cookieplugin (een CMP) die scripts echt blokkeert tot er toestemming is, en die Google Consent Mode v2 ondersteunt. Laad je meetcodes daarna via die plugin of via Google Tag Manager met toestemmingsinstellingen. Haal codes weg die rechtstreeks in je thema of in een "header scripts"-plugin staan, want die laden langs de banner heen.

### Shopify

Shopify heeft een eigen privacy- en cookiebanner en een Customer Privacy API waar de apps van Google en Meta op letten. Gebruik je een externe banner, controleer dan dat de toestemming ook doorkomt in de checkout. Pixels die je zelf in `theme.liquid` hebt geplakt, gaan vaak buiten de banner om.

### Alle platformen

- Zet de weigerknop in de eerste laag.
- Geen vooraf aangevinkte vakjes voor statistiek of marketing.
- Zorg voor een vaste link "Cookie-instellingen" in je footer, zodat mensen hun keuze kunnen wijzigen.
- Werk je cookieverklaring bij met welke partijen je gegevens krijgen.

## Waarom dit ook je advertenties raakt

Google verwacht in de Europese Economische Ruimte geldige toestemming voor advertentiemeting. Met [de toestemmingsmodus](https://support.google.com/google-ads/answer/13802165?hl=nl) geef je de keuze van de bezoeker door aan Google. Ontbreekt dat, dan mist Google Ads conversies en doelgroepen. Staat alles standaard op "granted", dan meet je wel, maar zonder geldige toestemming. Een goede banner lost dus twee problemen tegelijk op.

## Wat de website APK hierbij checkt

De [website check](https://www.joepify.nl/website-apk#apk-modules) kijkt of er een cookiebanner op je site staat en of er meetcodes van Google, Meta, TikTok, Hotjar of Clarity in de pagina staan zonder dat een bekende banner ze tegenhoudt. In het onderdeel tracking zie je of er signalen van Consent Mode v2 zijn. De APK klikt niet op je banner, dus een volledige test na weigeren doe je met de stappen hierboven.

Dit artikel is algemene informatie en geen juridisch advies.

- Gratis tool[Check ook je vindbaarheid met de gratis SEO check](https://www.joepify.nl/gratis-seo-check)
- Liever uitbesteden[Laat je WordPress-site bijhouden met WordPress onderhoud](https://www.joepify.nl/wordpress-onderhoud)

---
Bron: [Cookiebanner regels 2026: wat de AP controleert](https://www.joepify.nl/kennisbank/cookiebanner-regels) · Licentie: CC BY 4.0, noem Joepify met een link naar de originele pagina.
