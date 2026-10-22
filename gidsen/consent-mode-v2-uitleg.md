---
title: "Consent Mode v2 uitgelegd: zo check je het"
canonical: https://www.joepify.nl/kennisbank/consent-mode-v2-uitleg
updated: 2026-10-14
author: Ayoub Assaidi (Joepify)
license: CC BY 4.0
---

# Consent Mode v2 uitgelegd: zo check je het

> Origineel en altijd actueel: https://www.joepify.nl/kennisbank/consent-mode-v2-uitleg  
> Bijgewerkt: 2026-10-14 · Auteur: Ayoub Assaidi, [Joepify](https://www.joepify.nl) (Rotterdam)

**Kort antwoord:** Consent Mode v2 is de manier waarop je website aan Google doorgeeft of een bezoeker toestemming gaf voor cookies en advertenties. Zonder die signalen kun je voor bezoekers uit de EER geen remarketing, gepersonaliseerde advertenties en een deel van je metingen meer gebruiken. Het moet altijd samen met een goede cookiebanner: standaard staat alles op "geweigerd", en pas na een klik op "accepteren" gaat het op "toegestaan".

## Wat doet Consent Mode precies?

Je cookiebanner vraagt toestemming. Consent Mode is het doorgeefluik: het vertelt de tags van Google (Google Ads, GA4, Google Tag Manager) wat de bezoeker koos. De tags passen hun gedrag daarop aan. Consent Mode vervangt je cookiebanner dus niet. De regels voor de banner zelf lees je in de guide over [cookiebanner regels](https://www.joepify.nl/kennisbank/cookiebanner-regels).

Google noemt vier signalen, die je in de [documentatie voor ontwikkelaars](https://developers.google.com/tag-platform/security/concepts/consent-mode) terugvindt:

- `ad_storage`: cookies voor advertenties;
- `analytics_storage`: cookies voor statistieken, zoals bezoekduur;
- `ad_user_data`: toestemming om gebruikersgegevens voor advertenties naar Google te sturen;
- `ad_personalization`: toestemming voor gepersonaliseerde advertenties, zoals remarketing.

De laatste twee zijn het "v2"-deel. Google schrijft in de [uitleg over de EER-updates](https://support.google.com/google-ads/answer/13695607?hl=nl) dat je voor meting, advertentiepersonalisatie en remarketing toestemming moet vragen aan bezoekers uit de EER en die toestemmingssignalen met Google moet delen. Ontbreken ze, dan vallen die functies weg.

## Basic of advanced: wat is het verschil?

- **Basic:** de Google-tags laden pas nadat de bezoeker een keuze maakt. Weigert iemand, dan gaat er niets naar Google. Ook niet dat iemand weigerde.
- **Advanced:** de tags laden meteen, met alles op "geweigerd". Zolang er geen toestemming is, sturen ze alleen metingen zonder cookies. Google gebruikt die om conversies te modelleren, ook voor bezoekers die weigerden.

Advanced levert meer data op, basic is voorzichtiger. Welke past, hangt af van je privacyverklaring en hoe je zelf naar die cookieloze metingen kijkt. Bespreek dat met wie je privacy regelt. Heb je net gewisseld, geef het dan even: volgens [Google Ads Help](https://support.google.com/google-ads/answer/10000067?hl=nl) duurt het minimaal 7 hele dagen voordat Google Ads en Analytics genoeg gegevens hebben om het effect te rapporteren.

## De drie fouten die ik het vaakst zie

1. **De standaard staat op "toegestaan".** Dan meet je alles, maar zonder geldige toestemming. Dat is precies wat de AP niet wil zien.
2. **De standaard wordt te laat gezet.** Google waarschuwt in de [uitleg over debuggen](https://developers.google.com/tag-platform/security/guides/consent-debugging) dat een standaard die pas na de tags wordt ingesteld niet het verwachte effect heeft. De standaardinstelling moet als eerste in de pagina staan, vóór GA4 of de Ads-tag.
3. **Er komt geen update.** De bezoeker klikt op "accepteren", maar de banner geeft dat niet door. Dan blijft alles op "geweigerd" en lijkt het of je advertenties niets opleveren.

Google raadt aan om in Tag Manager een cookiebanner (CMP) te gebruiken die een eigen Tag Manager-template heeft, in plaats van zelfgeschreven HTML-tags. Dat voorkomt de meeste timingfouten.

## Shopify: de Customer Privacy API

Shopify zet in nieuwe winkels [automatisch een cookiebanner aan](https://help.shopify.com/en/manual/privacy-and-security/privacy/customer-privacy-settings/privacy-settings) voor bezoekers uit het VK en de EER. Je mag ook een cookiebanner-app gebruiken. Belangrijk is dat die app de keuze doorgeeft via de [Customer Privacy API](https://shopify.dev/docs/api/customer-privacy). Shopify gebruikt die keuze voor pixels, doelgroepen en de checkout. Een banner die daar niet aan gekoppeld is, kan "geweigerd" tonen terwijl je pixels toch vuren, of andersom.

Een bekend Nederlands probleem: na een iDEAL-betaling komt de klant terug via de bank, en onderweg raakt de toestemming soms kwijt. In de Shopify Community beschreef een Nederlandse winkel in september 2026 dat [een groot deel van de marketingtoestemming verloren ging tussen winkel en checkout](https://community.shopify.com/t/third-party-cookie-banner-server-side-gtm-marketing-consent-gets-lost-in-the-shopify-checkout-ideal-redirect-pixel-sandbox-timing/688673). Zie je na de overstap op Consent Mode ineens veel minder aankopen in Google Ads, controleer dan juist dat stuk. Gebruikte je nog scripts in de oude bestelstatuspagina, lees dan ook de guide over de [Shopify checkout upgrade](https://www.joepify.nl/kennisbank/shopify-checkout-extensibility).

## Gebruik je geen Google Ads?

Dan is Consent Mode minder urgent, maar niet zinloos. Gebruik je GA4, dan bepaalt `analytics_storage` of Analytics cookies mag zetten. Zonder Consent Mode heb je maar twee smaken: GA4 laadt altijd (en dan heb je een probleem met de toestemmingsregels) of GA4 laadt pas na een klik (en dan stuurt Google niets door over wie weigerde). Gebruik je helemaal geen Google-tags, dan heb je Consent Mode niet nodig. Je cookiebanner moet dan nog steeds kloppen voor Meta, TikTok of andere codes.

## Zo check je het zelf in vijf minuten

1. Installeer in Chrome de extensie Tag Assistant Companion en open [Tag Assistant](https://tagassistant.google.com/).
2. Verbind je website. Klik nog niet op de cookiebanner.
3. Kies in Tag Assistant het eerste event en open het tabblad *Consent*. Bij "Default" moeten alle vier de signalen op *Denied* staan.
4. Klik in je banner op "accepteren". Bij het volgende event moet je een *Update* zien met de signalen op *Granted*.
5. Herhaal het met "weigeren". Dan moet alles op *Denied* blijven.

Kijk je liever in het tabblad *Netwerk* van de ontwikkelaarstools, dan zie je in de verzoeken naar Google een parameter `gcd`. Google legt de precieze codering daarvan niet officieel uit, dus Tag Assistant is de betrouwbaarste controle.

## Zo controleer je het

Het onderdeel tracking van de [website check](https://www.joepify.nl/website-apk#apk-modules) laat zien welke meetcodes op je site staan (GA4, Tag Manager, Meta, TikTok) en of er signalen van Consent Mode v2 te zien zijn. Het onderdeel wettelijke plichten kijkt of er trackers laden voordat iemand toestemming geeft. Een klik op je banner doet de APK niet, dus de update na "accepteren" test je zelf met de stappen hierboven. Wil je dat ik banner, Consent Mode en pixels in één keer goed zet, kijk dan bij [Shopify beheer](https://www.joepify.nl/shopify-beheer) of [WordPress onderhoud](https://www.joepify.nl/wordpress-onderhoud).

- Gratis tool[Verkoop je via Shopify? Doe ook de gratis Shopify winkel check](https://www.joepify.nl/shopify-winkel-check)
- Liever uitbesteden[Laat je tracking op orde houden met Shopify beheer](https://www.joepify.nl/shopify-beheer)

---
Bron: [Consent Mode v2 uitgelegd: zo check je het](https://www.joepify.nl/kennisbank/consent-mode-v2-uitleg) · Licentie: CC BY 4.0, noem Joepify met een link naar de originele pagina.
