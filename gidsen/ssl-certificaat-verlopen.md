---
title: "SSL-certificaat verlopen? Zo los je het op"
canonical: https://www.joepify.nl/kennisbank/ssl-certificaat-verlopen
updated: 2026-10-22
author: Ayoub Assaidi (Joepify)
license: CC BY 4.0
---

# SSL-certificaat verlopen? Zo los je het op

> Origineel en altijd actueel: https://www.joepify.nl/kennisbank/ssl-certificaat-verlopen  
> Bijgewerkt: 2026-10-22 · Auteur: Ayoub Assaidi, [Joepify](https://www.joepify.nl) (Rotterdam)

**Kort antwoord:** als je SSL-certificaat verloopt, toont de browser een waarschuwing en haken de meeste bezoekers af. Vernieuw het certificaat via je hostingpaneel of laat het automatisch verlengen, bijvoorbeeld met Let's Encrypt. Dat automatisch verlengen wordt belangrijker: sinds 15 maart 2026 is een certificaat maximaal 200 dagen geldig, vanaf 15 maart 2027 maximaal 100 dagen en vanaf 15 maart 2029 maximaal 47 dagen. Met de hand vernieuwen is dan niet meer vol te houden. Let op: volgens Let's Encrypt is een standaardcertificaat 90 dagen geldig, en sinds 4 juni 2025 stuurt Let's Encrypt geen waarschuwingsmail meer als een certificaat bijna verloopt.

## Wat zie je als je SSL-certificaat verlopen is?

Een verlopen SSL-certificaat herken je aan een volledig scherm met een waarschuwing in Chrome, Edge, Safari of Firefox: de verbinding is niet privé of niet veilig. Vaak staat er een foutcode bij, zoals `NET::ERR_CERT_DATE_INVALID`. Een bezoeker moet actief doorklikken om toch verder te gaan. Bijna niemand doet dat, zeker niet in een webshop. Google Chrome toont de fout bijvoorbeeld zodra de vervaldatum voorbij is. Ook betalingen, koppelingen en formulieren kunnen stoppen, omdat andere systemen een verlopen certificaat weigeren.

Zie je in de adresbalk alleen "Niet veilig" naast je adres, dan is er iets anders aan de hand. De pagina laadt dan via http in plaats van https, of er is helemaal geen certificaat. De oplossing lijkt op elkaar, maar de oorzaak verschilt. Een verlopen certificaat geeft een blokkerend scherm, een ontbrekende https-verbinding alleen een melding in de adresbalk. In beide gevallen is de eerste stap een blik op de certificaatgegevens via het slotje of het waarschuwingsicoon in je browser. Sinds 15 maart 2026 is een nieuw certificaat maximaal 200 dagen geldig, dus die controle wordt vaker nodig.

## Waarom wordt de looptijd van een SSL-certificaat steeds korter?

De looptijd van een SSL-certificaat wordt korter omdat browsermakers en certificaatuitgevers in het CA/Browser Forum een strenger schema hebben afgesproken. In 2025 namen ze [ballot SC-081](https://cabforum.org/2025/04/11/ballot-sc081v3-introduce-schedule-of-reducing-validity-and-data-reuse-periods/) aan, met steun van Apple, Google, Microsoft en Mozilla. Volgens de [Baseline Requirements](https://cabforum.org/working-groups/server/baseline-requirements/requirements/) geldt nu deze maximale geldigheid:

- uitgegeven vóór 15 maart 2026: 398 dagen;
- vanaf 15 maart 2026: 200 dagen;
- vanaf 15 maart 2027: 100 dagen;
- vanaf 15 maart 2029: 47 dagen.

Kocht je vorig jaar nog een certificaat voor een jaar en zette je een herinnering in je agenda, dan werkt die aanpak niet meer. Bij 47 dagen moet je acht keer per jaar vernieuwen. Met de hand is zo'n ritme niet vol te houden, zeker niet met meerdere domeinen en subdomeinen. Automatisch verlengen via je hostingpartij of Let's Encrypt wordt daarom de normale situatie.

## Wat zijn de vijf meest voorkomende oorzaken van een verlopen SSL-certificaat?

Een verlopen SSL-certificaat heeft bijna altijd een van deze vijf oorzaken:

1. **Een betaald certificaat dat met de hand geïnstalleerd is.** Niemand kreeg de herinnering, of de mail ging naar een oud adres van de webbouwer.
2. **Automatisch verlengen faalt stil.** Let's Encrypt moet je domein kunnen controleren. Is je DNS verhuisd, staat er een proxy zoals Cloudflare voor, of blokkeert een beveiligingsplugin de map `/.well-known/`, dan mislukt het verlengen zonder melding. Let's Encrypt stuurt sinds [4 juni 2025](https://letsencrypt.org/2025/01/22/ending-expiration-emails/) ook geen waarschuwingsmails meer als een certificaat bijna verloopt.
3. **Het certificaat dekt niet alle adressen.** Het werkt op `jouwdomein.nl` maar niet op `www.jouwdomein.nl`, of andersom.
4. **Je domein of hosting is verhuisd** en het certificaat staat nog bij de oude partij.
5. **Een ander onderdeel heeft een eigen certificaat.** Denk aan je mailserver, een subdomein voor je boekingssysteem of een losse landingspagina. Juist zulke onderdelen vergeet iedereen.

In de praktijk is oorzaak 2 de lastigste, omdat je er niets van merkt tot bezoekers de waarschuwing zien. Volgens Let's Encrypt is een standaardcertificaat 90 dagen geldig en vindt de verlenging rond dag 60 plaats. Mislukt die verlenging, dan heb je dus ongeveer 30 dagen voordat bezoekers de waarschuwing zien.

## Hoe los je een verlopen SSL-certificaat nu op?

De snelste oplossing voor een verlopen SSL-certificaat is een nieuw gratis certificaat via het hostingpaneel. Een gratis Let's Encrypt-certificaat is 90 dagen geldig en meestal is de site binnen een uur weer bereikbaar. Werk de stappen in deze volgorde af:

1. Klik eerst in je browser op het slotje of het waarschuwingsicoon en open de certificaatgegevens. Daar zie je de vervaldatum, voor welke adressen het geldt en wie het uitgaf.
2. Log daarna in bij je hostingpartij. Bijna elk paneel (DirectAdmin, cPanel, Plesk) heeft een onderdeel SSL of Let's Encrypt. Vraag daar een nieuw certificaat aan voor zowel je domein als de www-variant.
3. Gebruik je Cloudflare, kijk dan ook daar bij SSL/TLS. Het certificaat tussen Cloudflare en je server moet ook geldig zijn.
4. Draait je site op WordPress, kijk dan bij Instellingen > Algemeen of het WordPress-adres en het site-adres allebei met `https://` beginnen. Laden afbeeldingen of scripts nog via http, dan klaagt de browser over gemengde inhoud. Een zoek-en-vervang in de database van `http://jouwdomein.nl` naar `https://jouwdomein.nl` lost gemengde inhoud meestal op. Maak eerst een back-up.
5. Leeg tot slot de cache van je site en test in een privévenster.
6. Weet je niet wie je hosting beheert of kom je niet in het paneel, lees dan eerst de guide over [je domeinnaam op eigen naam](https://www.joepify.nl/kennisbank/domeinnaam-op-eigen-naam).

## Hoe controleer je het SSL-certificaat van je mail en subdomeinen?

Het SSL-certificaat van je mail en subdomeinen is een apart certificaat dat je per adres controleert, want een certificaat hoort niet alleen bij je website. Je mailserver gebruikt er ook een, net als subdomeinen als `shop.`, `boeken.` of `mail.`. Verloopt het certificaat van je mailserver, dan krijgen collega's een foutmelding in Outlook of op hun telefoon. Mail van andere servers kan dan soms niet meer veilig worden afgeleverd. Maak daarom een lijstje van al je subdomeinen en kijk per adres wanneer het certificaat verloopt.

Technisch ingesteld? Met OpenSSL zie je van buitenaf de vervaldatum van elk adres:

`openssl s_client -connect jouwdomein.nl:443 -servername jouwdomein.nl </dev/null | openssl x509 -noout -enddate`

De regel `notAfter` is de vervaldatum. Vervang `jouwdomein.nl` door elk subdomein uit je lijstje. Voor een mailserver gebruik je bijvoorbeeld poort 993 (IMAP) of 465 (SMTP) in plaats van 443. Staat de datum binnen 30 dagen, vraag dan nu al een nieuw certificaat aan. Vanaf 15 maart 2027 is de maximale looptijd volgens het CA/Browser Forum 100 dagen.

## Hoe voorkom je dat je SSL-certificaat voortaan verloopt?

Een verlopen SSL-certificaat voorkom je met automatisch verlengen plus een controle die waarschuwt als het verlengen faalt. Concreet komt het neer op vier afspraken:

- **Kies voor automatisch verlengen.** Volgens de [FAQ van Let's Encrypt](https://letsencrypt.org/docs/faq/) is een standaardcertificaat 90 dagen geldig en raadt Let's Encrypt aan om elke 60 dagen te vernieuwen. Bij de meeste hostingpartijen is automatisch verlengen één vinkje.
- **Heb je een betaald certificaat nodig**, bijvoorbeeld voor een koppeling die een betaald certificaat eist, vraag je leverancier dan of automatisch verlengen mogelijk is. Handwerk is vanaf 2027 een risico, met een maximum van 100 dagen.
- **Laat het controleren.** Een dienst of monitoring die je waarschuwt als een certificaat binnen twee weken verloopt, vangt de stille fouten op.
- **Zet HSTS pas aan als het verlengen goed loopt.** Met HSTS kan een bezoeker bij een verlopen certificaat niet meer doorklikken. Meer daarover in de guide over [beveiligingsheaders](https://www.joepify.nl/kennisbank/beveiligingsheaders-website).

## Hoe controleer je of je SSL-certificaat goed staat?

De makkelijkste controle van je SSL-certificaat is een gratis scan met de [website check](https://www.joepify.nl/website-apk#apk-modules) van Joepify. De check leest je certificaat uit, laat zien wanneer het verloopt en door wie het is uitgegeven, en kijkt of http netjes doorverwijst naar https. Wil je dat iemand je certificaten, updates en back-ups voor je bijhoudt, kijk dan bij [WordPress onderhoud](https://www.joepify.nl/wordpress-onderhoud). Staat je site nog bij een oude webbouwer, dan helpt [website overnemen](https://www.joepify.nl/website-overnemen). Meer over goede hosting lees je in [zakelijke hosting in Nederland](https://www.joepify.nl/blog/zakelijke-hosting-nederland). Controleer je certificaat daarnaast elke 30 dagen zolang automatisch verlengen nog niet aantoonbaar werkt.

- Gratis tool[Check ook je vindbaarheid met de gratis SEO check](https://www.joepify.nl/gratis-seo-check)
- Liever uitbesteden[Laat je certificaat en hosting bewaken met WordPress onderhoud](https://www.joepify.nl/wordpress-onderhoud)

---
Bron: [SSL-certificaat verlopen? Zo los je het op](https://www.joepify.nl/kennisbank/ssl-certificaat-verlopen) · Licentie: CC BY 4.0, noem Joepify met een link naar de originele pagina.
