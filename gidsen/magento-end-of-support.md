---
title: "Magento 2.4 end of support: welke versies nog veilig zijn"
canonical: https://www.joepify.nl/kennisbank/magento-end-of-support
updated: 2026-10-14
author: Ayoub Assaidi (Joepify)
license: CC BY 4.0
---

# Magento 2.4 end of support: welke versies nog veilig zijn

> Origineel en altijd actueel: https://www.joepify.nl/kennisbank/magento-end-of-support  
> Bijgewerkt: 2026-10-14 · Auteur: Ayoub Assaidi, [Joepify](https://www.joepify.nl) (Rotterdam)

**Kort antwoord:** Magento 2.4.4 en 2.4.5 krijgen van Adobe geen enkele patch meer. Bij 2.4.6 is de gewone support op 11 augustus 2026 gestopt en loopt alleen nog extended support tot 31 augustus 2027. 2.4.7 wordt ondersteund tot 31 mei 2027, 2.4.8 tot 31 mei 2028 en 2.4.9 tot 31 mei 2029. Draait je webshop op 2.4.5 of ouder, dan zit je zonder beveiligingsupdates. Dan heb je twee echte opties: upgraden naar een ondersteunde versie of overstappen naar een ander platform.

## Welke Magento-versie wordt tot wanneer ondersteund?

Adobe publiceert de data in de [lifecycle policy van Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-operations/release/planning/lifecycle-policy). Dit is de stand op 14 oktober 2026:

| Versie | Uitgebracht | Gewone support tot | Extended support tot | 
|---|---|---|---|
| 2.4.4 | 12 april 2022 | 12 april 2025 | 14 april 2026 (voorbij) | 
| 2.4.5 | 9 augustus 2022 | 12 augustus 2025 | 11 augustus 2026 (voorbij) | 
| 2.4.6 | 14 maart 2023 | 11 augustus 2026 (voorbij) | 31 augustus 2027 | 
| 2.4.7 | 9 april 2024 | 31 mei 2027 | 31 mei 2028 | 
| 2.4.8 | 8 april 2025 | 31 mei 2028 | nog niet bekend | 
| 2.4.9 | 12 mei 2026 | 31 mei 2029 | nog niet bekend | 

Gewone support betekent kwaliteitsfixes, beveiligingspatches en ondersteuning van Adobe. Extended support is een extra periode met alleen kwaliteits- en beveiligingspatches. Let op: de lifecyclepagina gaat over Adobe Commerce, de betaalde versie. Draai je Magento Open Source, de gratis versie die de meeste Nederlandse webshops gebruiken, ga er dan niet van uit dat je die extended jaren ook krijgt. Reken voor Open Source met de datum van de gewone support.

Magento 1 krijgt al jaren helemaal geen support meer. Draait je shop daar nog op, dan is dit artikel voor jou eigenlijk al te laat: plan direct een overstap.

## Waarom dit nu echt uitmaakt: SessionReaper

"Geen patches meer" klinkt abstract tot er een lek komt. Dat gebeurde in 2025 met SessionReaper ([CVE-2025-54236](https://nvd.nist.gov/vuln/detail/CVE-2025-54236)). Adobe bracht op 9 september 2025 een noodpatch uit (bulletin [APSB25-88](https://helpx.adobe.com/security/products/magento/apsb25-88.html)). Het lek kreeg een CVSS-score van 9.1, "kritiek", en werkt zonder inloggen. Kwetsbaar waren onder meer 2.4.8-p2, 2.4.7-p7, 2.4.6-p12, 2.4.5-p14 en 2.4.4-p15 en alles daarvoor.

Volgens beveiligingsbedrijf [Sansec](https://sansec.io/research/sessionreaper) begonnen de massale aanvallen op 22 oktober 2025. Een dag later was pas 38% van de winkels gepatcht. Op 1 november 2025 was 81% van alle Magento-winkels aangevallen. De Amerikaanse CISA zette het lek op 24 oktober 2025 op de lijst van actief misbruikte kwetsbaarheden.

Het punt: toen werd 2.4.4 nog net gepatcht. Komt er nu een vergelijkbaar lek, dan krijgen 2.4.4 en 2.4.5 die patch niet meer. Je bent dan afhankelijk van een developer die de fix zelf terugzet, als dat al kan.

## Hoe weet je welke versie je draait?

- **In de admin:** onderaan elke pagina van het Magento-beheer staat "Magento ver. 2.4.x". Let ook op het patchnummer (bijvoorbeeld -p12).
- **Via de command line:** `bin/magento --version` op de server.
- **Vraag het je bureau:** en vraag meteen wanneer de laatste beveiligingspatch is geïnstalleerd. Een eerlijk bureau heeft dat antwoord direct.

Van buitenaf is het exacte versienummer meestal niet te zien. Wel te zien is dat een site op Magento 2 draait, en grofweg of het 2.4.3 of nieuwer is.

## Je opties

### 1. Upgraden binnen Magento

Van 2.4.5 of 2.4.6 naar 2.4.8 of 2.4.9. Dat is geen klik op een knop. Elke grote versie vraagt nieuwere PHP-, MySQL- en zoekmachineversies, en extensies en maatwerk moeten mee. Bij shops die jaren niet zijn bijgewerkt is een upgrade in de praktijk een klein project, met een testomgeving en een testronde. Daarna begint de klok opnieuw: binnen drie jaar sta je weer voor dezelfde keuze.

### 2. Overstappen naar een ander platform

Voor veel middelgrote shops is dit het moment om te kijken of Magento nog past. Een gehost platform zoals Shopify regelt de beveiligingsupdates zelf, je hoeft geen server en PHP-versies meer te beheren. Wat je wel moet regelen bij een migratie: producten en varianten, klanten, bestelhistorie, en vooral 301-redirects van alle oude URL's, zodat je Google-posities niet verliest.

### 3. Niets doen (eerlijk gezegd: geen optie)

Een webshop zonder beveiligingspatches die klantgegevens en betalingen verwerkt, is een risico voor je klanten en voor jou. Je betaalprovider en je verzekeraar kunnen daar ook vragen over stellen.

## Welke keuze past bij jou?

- **Upgraden** als je zware maatwerkkoppelingen hebt (ERP, B2B-prijslogica) en een bureau dat de shop goed kent.
- **Migreren** als je shop vooral standaard verkoopt, je weinig mensen hebt die Magento kunnen onderhouden, of de upgrade bijna een herbouw is.

Twijfel je, laat dan eerst een inventarisatie maken: welke extensies, welk maatwerk, welke koppelingen. Dat bepaalt de omvang van beide routes.

## Vragen die je je bureau of developer stelt

- Op welke versie en welk patchniveau draait mijn shop precies?
- Wanneer is de laatste beveiligingspatch geïnstalleerd, en is de SessionReaper-fix erin meegenomen?
- Welke PHP-versie draait de server, en wordt die zelf nog ondersteund?
- Welke extensies gebruik ik, en zijn die er ook voor 2.4.8 of 2.4.9?
- Wat is het plan voor de komende twee jaar: upgraden, of iets anders?

Krijg je op deze vragen geen duidelijk antwoord, dan is dat zelf ook een antwoord. Een shop zonder onderhoudsplan loopt bij het volgende lek het meeste risico.

## Zo controleer je het

Doe de gratis [website check](https://www.joepify.nl/website-apk): die ziet of je webshop op Magento draait en geeft een waarschuwing als het platform verouderd lijkt. Wil je weten wat een overstap inhoudt, lees dan hoe een [migratie van Magento naar Shopify](https://www.joepify.nl/shopify-migratie/magento) verloopt.

## Wat de website APK hierbij checkt

Het onderdeel platform van de [website check](https://www.joepify.nl/website-apk#apk-modules) herkent Magento 2 aan vaste kenmerken in de HTML, zoals `/static/version.../frontend/` en de Magento-modules, en herkent Magento 1 aan oude paden. Het exacte versienummer kan de APK meestal niet zien, want Magento verbergt dat van buitenaf. De melding is daarom een signaal om je versie in de admin na te kijken, geen vonnis.

- Gratis tool[Check ook je vindbaarheid met de gratis SEO check](https://www.joepify.nl/gratis-seo-check)
- Liever uitbesteden[Overstappen van Magento naar Shopify](https://www.joepify.nl/shopify-migratie/magento)

---
Bron: [Magento 2.4 end of support: welke versies nog veilig zijn](https://www.joepify.nl/kennisbank/magento-end-of-support) · Licentie: CC BY 4.0, noem Joepify met een link naar de originele pagina.
