---
title: "Security headers instellen: HSTS en meer voor je site"
canonical: https://www.joepify.nl/kennisbank/beveiligingsheaders-website
updated: 2026-10-14
author: Ayoub Assaidi (Joepify)
license: CC BY 4.0
---

# Security headers instellen: HSTS en meer voor je site

> Origineel en altijd actueel: https://www.joepify.nl/kennisbank/beveiligingsheaders-website  
> Bijgewerkt: 2026-10-14 · Auteur: Ayoub Assaidi, [Joepify](https://www.joepify.nl) (Rotterdam)

**Kort antwoord:** security headers zijn korte instructies die je server met elke pagina meestuurt, zodat de browser je bezoekers beter beschermt. Zes zijn de moeite waard: **Strict-Transport-Security** (HSTS), **X-Content-Type-Options**, **X-Frame-Options** of de CSP-regel frame-ancestors, **Referrer-Policy**, **Permissions-Policy** en **Content-Security-Policy**. De eerste vijf zet je in een kwartier aan. Met CSP en met de preload-optie van HSTS ben je voorzichtig, want die kunnen je site breken.

## Wat zijn security headers?

Als een browser een pagina opvraagt, stuurt je server niet alleen de HTML terug, maar ook "headers": regels met extra informatie. Een paar van die regels zijn bedoeld voor beveiliging. Ze vertellen de browser bijvoorbeeld: "laad deze site alleen via https" of "laat deze site niet in een frame op een andere site zien". Ze kosten niets, maken je site niet trager en worden door alle moderne browsers ondersteund.

Eerlijk is eerlijk: headers maken een lekke plugin niet veilig. Ze beperken wel de schade van een aantal veelvoorkomende aanvallen, en ontbrekende headers zijn vaak een teken dat er verder ook weinig aandacht naar de server gaat.

## De zes headers en wat ze doen

De aanbevolen waarden hieronder komen uit de [HTTP Headers Cheat Sheet van OWASP](https://cheatsheetseries.owasp.org/cheatsheets/HTTP_Headers_Cheat_Sheet.html), de internationale standaard voor webbeveiliging.

### 1. Strict-Transport-Security (HSTS)

Vertelt de browser dat je site alleen via https mag laden, ook als iemand een oude http-link aanklikt. Dat voorkomt dat iemand op een openbaar wifinetwerk het verkeer onderschept voordat de doorverwijzing naar https plaatsvindt. Een veelgebruikte waarde is `max-age=63072000; includeSubDomains` (twee jaar). De browser negeert de header als hij via gewone http binnenkomt, [schrijft MDN](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Strict-Transport-Security), dus zet hem op je https-versie.

### 2. X-Content-Type-Options

Waarde: `nosniff`. Voorkomt dat de browser gaat "raden" wat voor bestand iets is. Zonder deze header kan een geüpload bestand dat eruitziet als een plaatje toch als script worden uitgevoerd. Er is geen reden om hem niet aan te zetten.

### 3. X-Frame-Options of frame-ancestors

Waarde: `DENY` of `SAMEORIGIN`. Voorkomt dat een andere site jouw pagina onzichtbaar in een frame laadt en bezoekers laat klikken op knoppen die ze niet zien (clickjacking). Moderne browsers gebruiken liever de CSP-regel `frame-ancestors`, maar X-Frame-Options blijft nuttig voor oudere browsers. Kies `SAMEORIGIN` als je eigen site pagina's in frames toont, bijvoorbeeld in de WordPress-editor.

### 4. Referrer-Policy

Waarde: `strict-origin-when-cross-origin`. Bepaalt hoeveel van je URL je doorgeeft als iemand naar een andere site klikt. Met deze waarde ziet de andere site alleen je domeinnaam, niet de volledige pagina met eventuele gegevens in de URL. Je statistieken blijven gewoon werken.

### 5. Permissions-Policy

Bijvoorbeeld: `geolocation=(), camera=(), microphone=()`. Zet browserfuncties uit die je site niet gebruikt. Als er ooit kwaadaardige code op je site belandt, kan die dan niet om de camera of locatie van je bezoeker vragen. Gebruik je wel een functie, zoals locatie in een winkelzoeker, laat die dan weg uit de lijst.

### 6. Content-Security-Policy (CSP)

De sterkste en lastigste. Met CSP geef je een lijst van bronnen waar scripts, stijlen en plaatjes vandaan mogen komen. Alles wat niet op de lijst staat, blokkeert de browser. Dat stopt veel geïnjecteerde scripts, zoals de skimmers die betaalgegevens stelen. Maar een webshop laadt scripts van tientallen partijen: Google, Meta, je betaalprovider, je chat, je reviews. Vergeet je er één, dan werkt je checkout of je tracking niet meer.

Begin daarom met `Content-Security-Policy-Report-Only`. Dan blokkeert de browser niets, maar zie je in de console wat hij zou blokkeren. Pas als die lijst leeg is, zet je de echte header aan.

## En wat je juist weghaalt

- **X-Powered-By** (bijvoorbeeld "PHP/7.4"): vertelt aanvallers welke software en versie je draait. OWASP adviseert hem te verwijderen.
- **Server** met versienummer, zoals "Apache/2.4.41": zet de versie uit.
- **X-XSS-Protection**: verouderd. OWASP raadt aan hem weg te laten of op `0` te zetten.

## Zo zet je ze aan

### Apache (.htaccess, bij de meeste Nederlandse hostingpakketten)

```
<IfModule mod_headers.c>
  Header always set Strict-Transport-Security "max-age=63072000; includeSubDomains"
  Header always set X-Content-Type-Options "nosniff"
  Header always set X-Frame-Options "SAMEORIGIN"
  Header always set Referrer-Policy "strict-origin-when-cross-origin"
  Header always set Permissions-Policy "geolocation=(), camera=(), microphone=()"
  Header unset X-Powered-By
</IfModule>
```
Maak eerst een kopie van je .htaccess. Een tikfout geeft een foutmelding op je hele site.

### Nginx

In het server-blok: `add_header Strict-Transport-Security "max-age=63072000; includeSubDomains" always;` en zo verder voor de andere headers. Let op: zet je ergens in een location-blok ook een add\_header, dan vervallen daar de headers uit het server-blok.

### Cloudflare

HSTS zet je aan onder SSL/TLS, Edge Certificates. De andere headers voeg je toe met een Transform Rule (Modify Response Header). Handig als je geen toegang tot de server hebt.

### Shopify en andere gehoste platforms

Daar regelt het platform de headers zelf en kun je ze meestal niet aanpassen. Dat is geen probleem: dan ben je er niet verantwoordelijk voor.

## Voorzichtig met HSTS preload

Je kunt je domein laten opnemen in de preload-lijst die in browsers zit ingebakken. Daarvoor vraagt [hstspreload.org](https://hstspreload.org/) een max-age van minstens 31536000 seconden (een jaar), plus `includeSubDomains` en `preload`. Dan moet echt elk subdomein https hebben, ook een oud mail- of testsubdomein. Weghalen uit de lijst kan, maar het duurt volgens de site zelf maanden voordat dat bij gebruikers is. hstspreload.org raadt aan om op te bouwen: eerst vijf minuten, dan een week, dan een maand. Voor de meeste mkb-sites is HSTS zonder preload ruim voldoende.

## Zo controleer je het

Doe de gratis [website check](https://www.joepify.nl/website-apk): die toont welke headers je site meestuurt en welke ontbreken. Draai je WordPress en wil je dit (en de updates eromheen) uit handen geven, kijk dan bij [WordPress onderhoud](https://www.joepify.nl/wordpress-onderhoud).

## Wat de website APK hierbij checkt

Het onderdeel beveiliging van de [website check](https://www.joepify.nl/website-apk#apk-modules) doet één gewone aanvraag naar je homepage en leest de headers die terugkomen: HSTS (en of de max-age lang genoeg is), X-Content-Type-Options, X-Frame-Options of frame-ancestors, Referrer-Policy, Permissions-Policy en CSP. Hij meldt ook als X-Powered-By of een Server-header met versienummer je software verraadt. De APK test niet of een CSP goed werkt, alleen of hij er is.

- Gratis tool[Check ook je vindbaarheid met de gratis SEO check](https://www.joepify.nl/gratis-seo-check)
- Liever uitbesteden[Laat je WordPress-site veilig houden met WordPress onderhoud](https://www.joepify.nl/wordpress-onderhoud)

---
Bron: [Security headers instellen: HSTS en meer voor je site](https://www.joepify.nl/kennisbank/beveiligingsheaders-website) · Licentie: CC BY 4.0, noem Joepify met een link naar de originele pagina.
