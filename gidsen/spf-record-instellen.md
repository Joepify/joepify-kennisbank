---
title: "SPF record instellen: zo komt je mail niet in spam"
canonical: https://www.joepify.nl/kennisbank/spf-record-instellen
updated: 2026-10-22
author: Ayoub Assaidi (Joepify)
license: CC BY 4.0
---

# SPF record instellen: zo komt je mail niet in spam

> Origineel en altijd actueel: https://www.joepify.nl/kennisbank/spf-record-instellen  
> Bijgewerkt: 2026-10-22 · Auteur: Ayoub Assaidi, [Joepify](https://www.joepify.nl) (Rotterdam)

**Kort antwoord:** een SPF record is één TXT-record in de DNS van je domein dat begint met `v=spf1` en opsomt welke diensten namens jou mogen mailen. Voor alleen Microsoft 365 is dat `v=spf1 include:spf.protection.outlook.com -all`, voor alleen Google Workspace `v=spf1 include:_spf.google.com ~all`. Mail je ook via je webshop, nieuwsbrief of boekhoudpakket, dan voeg je hun include toe aan datzelfde record. Nooit een tweede SPF-record aanmaken, en blijf onder de 10 DNS-lookups. Daarnaast geldt volgens RFC 7208, de SPF-standaard uit 2014, een harde grens: een tweede record of een record met meer dan 10 lookups geeft een permerror. Dan faalt SPF voor al je mail, ook voor je gewone mailbox.

## Wat doet SPF?

SPF (Sender Policy Framework, vastgelegd in [RFC 7208](https://www.rfc-editor.org/rfc/rfc7208)) is een lijst van servers die mail mogen versturen voor jouw domein. De ontvangende mailserver kijkt bij elke mail of de afzender op de lijst staat. Staat de server er niet op, dan telt de mail als verdacht en belandt hij eerder in spam of wordt hij geweigerd.

SPF is één van de drie onderdelen van mailbeveiliging. Samen met [DKIM](https://www.joepify.nl/kennisbank/dkim-instellen) (een digitale handtekening) en DMARC (het beleid erboven) bepaalt SPF of jouw mail vertrouwd wordt. Volgens de [afzenderrichtlijnen van Google](https://support.google.com/a/answer/81126?hl=nl) moet sinds 1 februari 2024 elke afzender naar Gmail minstens SPF of DKIM hebben. Hoe de drie samenwerken, lees je in [DMARC instellen](https://www.joepify.nl/kennisbank/dmarc-instellen). Deze guide gaat alleen over het SPF-record zelf, want daar gaat het in de praktijk het vaakst mis.

## Hoe ziet een SPF record eruit?

Een SPF record is een TXT-record dat begint met `v=spf1` en eindigt met `-all` of `~all`. Een voorbeeld voor een bedrijf dat Microsoft 365 gebruikt en daarnaast mailt vanaf een eigen server:

`v=spf1 ip4:192.0.2.10 include:spf.protection.outlook.com -all`

- `v=spf1`: markeert het record als SPF-record. Altijd vooraan.
- `include:`: neem de lijst van een andere dienst over. Elke maildienst geeft je een eigen include.
- `ip4:` of `ip6:`: een vast IP-adres of een reeks adressen die mag mailen.
- `-all` of `~all`: wat er moet gebeuren met mail van alle andere servers. Staat altijd achteraan.

Het record zet je bij de partij waar je DNS staat, vaak je domeinregistrar of hoster. Je maakt een TXT-record aan op de naam van je domein zelf (vaak aangeduid met `@` of leeg gelaten).

## Hoe stel je een SPF record stap voor stap in?

Een SPF record instellen is een klus van vijf stappen: eerst som je alle verzenders op, daarna maak je één TXT-record met hun includes.

1. **Maak een lijst van alles wat namens je domein mailt.** Denk verder dan je mailbox: je webshop (orderbevestigingen), je contactformulier, je nieuwsbriefdienst, je boekhoud- of factuurpakket, je reserveringssysteem. Juist deze stap slaan mensen over.
2. **Zoek per dienst de juiste include op** in de hulppagina's van de dienst zelf, niet op een forum. Niet elke dienst heeft een SPF-include nodig: sommige versturen met een eigen afzenderdomein en vragen alleen DKIM.
3. **Kijk of er al een SPF-record is.** Vaak heeft je hoster er al één aangemaakt. Pas dat record aan in plaats van er een tweede naast te zetten.
4. **Voeg alles samen in één record**, met `~all` of `-all` aan het eind.
5. **Test het** met de [e-mail check](https://www.joepify.nl/email-check) en stuur een testmail vanuit elke dienst naar een Gmail-adres. Bij "Origineel weergeven" zie je per mail of SPF "PASS" geeft.

Een DNS-wijziging is meestal binnen een uur zichtbaar, maar Google rekent op [tot 48 uur](https://knowledge.workspace.google.com/admin/security/set-up-spf).

## Wat zijn de includes van de grote mailproviders?

De include van een mailprovider is de vaste verwijzing die je in je SPF record zet zodat de servers van de provider namens jou mogen mailen. Voor de drie meest gebruikte situaties in het Nederlandse mkb:

- **Microsoft 365:** `include:spf.protection.outlook.com`. Microsoft adviseert `-all` als je ook DKIM en DMARC hebt ([Microsoft Learn](https://learn.microsoft.com/en-us/defender-office-365/email-authentication-spf-configure)).
- **Google Workspace:** `include:_spf.google.com`. Google adviseert `~all` ([Google Workspace-hulp](https://knowledge.workspace.google.com/admin/security/set-up-spf)).
- **Mail via je hoster** (bijvoorbeeld een pakket bij TransIP, Strato of een andere Nederlandse hoster): gebruik de waarde uit het controlepaneel of de kennisbank van je hoster. De waarden verschillen per pakket en veranderen soms.

Gebruik je Microsoft 365 en Google Workspace niet tegelijk, zet dan ook maar één van beide includes in je record. Elke include telt mee voor de grens van 10 DNS-lookups. Een nieuwsbriefdienst of webshop komt er als extra include bij, in hetzelfde record.

## De vijf fouten die mail in spam laten belanden

### 1. Twee SPF-records

Twee SPF-records op één domein is de meest voorkomende fout. Een typisch voorbeeld: iemand koppelt in 2026 een nieuwe nieuwsbriefdienst en maakt een tweede TXT-record met `v=spf1` aan. Volgens [RFC 7208](https://www.rfc-editor.org/rfc/rfc7208#section-3.2) mag een domein maar één SPF-record hebben. Bij twee records geeft de controle een "permerror", en dan valt SPF voor al je mail om, ook voor je gewone mailbox. Oplossing: voeg de includes samen in één record. Laat je je nieuwsbrief door een specialist versturen, dan regelt de specialist het record voor je. Zo werkt [e-mailmarketing uitbesteden](https://www.joepify.nl/blog/email-marketing-uitbesteden).

### 2. Meer dan 10 lookups

Een SPF record mag maximaal 10 DNS-lookups veroorzaken. Elke `include`, `a`, `mx`, `ptr`, `exists` en `redirect` kost een DNS-opvraging. Volgens [RFC 7208, paragraaf 4.6.4](https://www.rfc-editor.org/rfc/rfc7208#section-4.6.4) mogen er maximaal 10 opvragingen zijn, en includes binnen includes tellen mee. Daarboven is de uitkomst weer "permerror". De mechanismen `ip4`, `ip6` en `all` tellen niet mee. Daarnaast beperkt dezelfde paragraaf de "void lookups", opvragingen zonder antwoord, tot twee. Kom je boven de 10, haal dan ongebruikte diensten weg, of laat een dienst zoals je nieuwsbrief mailen vanaf een subdomein met een eigen SPF-record. Microsoft Learn geeft hetzelfde subdomein-advies.

### 3. Oude diensten, 4. tikfouten en 5. het vergeten contactformulier

**Oude diensten.** Een vergeten include is een stille kostenpost: de include van een nieuwsbriefdienst waar je drie jaar geleden mee gestopt bent, telt nog steeds mee voor de 10 lookups. Ruim op.

**Tikfouten.** Eén tikfout breekt het hele record. Microsoft noemt drie klassiekers: een punt achter de domeinnaam, een is-teken in plaats van een dubbele punt (`include=`) en een spatie na de dubbele punt.

**Het contactformulier.** Ook het formulier op je website wordt vaak vergeten. Een WordPress-site verstuurt formulieren meestal via de webserver van je hoster. Staat die server niet in je SPF-record, dan komen juist de aanvragen van nieuwe klanten in spam. Laat je website liever via een echte mailbox of een maildienst versturen (SMTP) en zet die dienst in je record.

## \~all of -all?

Het verschil tussen `~all` en `-all` is hoe streng de ontvanger omgaat met mail van servers die niet in je SPF record staan. `-all` (hard fail) zegt: mail van andere servers is niet van ons, weiger hem. `~all` (soft fail) zegt: waarschijnlijk niet van ons, accepteer maar markeer. Google adviseert `~all`, Microsoft `-all` als DKIM en DMARC ook staan. Heb je DMARC ingesteld, dan kijkt de ontvanger bovendien naar je [DMARC-beleid](https://www.joepify.nl/onderzoek-webshops-2026).

Mijn advies: begin met `~all` zolang je niet zeker weet of je lijst compleet is, en stap over op `-all` als je DMARC-rapporten een paar weken schoon zijn. Gebruik nooit `+all`: daarmee mag iedereen namens jou mailen. Ook `?all` (neutraal) biedt geen bescherming en is alleen bruikbaar tijdens een korte test.

## Welk SPF record zet je op domeinen die niet mailen?

Het juiste SPF record voor een domein zonder mail is `v=spf1 -all`. Met dat record meld je aan elke ontvanger: vanaf dit domein komt nooit mail. Denk aan extra domeinen voor een doorverwijzing, een oude bedrijfsnaam of een tikfout-domein. Zo kunnen oplichters zulke domeinen niet gebruiken voor nepfacturen of phishing, en weigeren ontvangers zoals Gmail van Google en Outlook van Microsoft vervalste mail eerder. Het record kost geen enkele DNS-lookup, omdat `all` volgens RFC 7208 niet meetelt.

Volgens het [NCSC](https://www.ncsc.nl/phishing/bescherm-domeinnamen-tegen-phishing) verdienen ook domeinen zonder mailverkeer bescherming. Zet daarom naast het SPF record een DMARC-record met `v=DMARC1; p=reject` op het domein. Hoe je dat record aanmaakt, staat in [DMARC instellen](https://www.joepify.nl/kennisbank/dmarc-instellen).

## Hoe controleer je of je SPF record klopt?

Of je SPF record klopt, zie je het snelst met de gratis [e-mail check](https://www.joepify.nl/email-check): vul je domein in en de check laat je SPF-, DKIM- en DMARC-records zien. Controleer daarbij drie dingen: er is precies één record met `v=spf1`, elke dienst uit je lijst staat erin en het record eindigt op `~all` of `-all`. Stuur daarnaast vanuit elke dienst een testmail naar een Gmail-adres en kijk bij "Origineel weergeven" of SPF op PASS staat. Een wijziging kan volgens de hulppagina van Google tot 48 uur nodig hebben voordat elke server het nieuwe record ziet.

Wil je meteen ook je website, beveiliging en wettelijke plichten laten nalopen, doe dan de [website check](https://www.joepify.nl/website-apk). Is SPF in orde, ga dan verder met [DMARC instellen](https://www.joepify.nl/kennisbank/dmarc-instellen).

## Wat de website APK hierbij checkt

De website APK is een gratis scan van Joepify. In het onderdeel e-mail controleert de APK of je SPF-record bestaat en telt de scan dubbele SPF-records. Je ziet het resultaat in de [website check](https://www.joepify.nl/website-apk#apk-modules). Of elke dienst die namens jou mailt in het record staat, kan de APK niet zien: alleen jij weet welke diensten namens je domein mailen. Daarom blijft de inventaris uit stap 1 nodig. Combineer de APK dus met een testmail vanuit elke dienst, bijvoorbeeld je webshop en je nieuwsbrief.

- Gratis tool[Test je SPF, DKIM en DMARC met de gratis e-mail check](https://www.joepify.nl/email-check)
- Liever uitbesteden[Mailt je WordPress-site niet goed? Bekijk WordPress onderhoud](https://www.joepify.nl/wordpress-onderhoud)

---
Bron: [SPF record instellen: zo komt je mail niet in spam](https://www.joepify.nl/kennisbank/spf-record-instellen) · Licentie: CC BY 4.0, noem Joepify met een link naar de originele pagina.
