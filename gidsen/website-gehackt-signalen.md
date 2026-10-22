---
title: "Website gehackt? Signalen na PHP2Shell en wat je doet"
canonical: https://www.joepify.nl/blog/website-gehackt-signalen
updated: 2026-10-22
author: Ayoub Assaidi (Joepify)
license: CC BY 4.0
---

# Website gehackt? Signalen na PHP2Shell en wat je doet

> Origineel en altijd actueel: https://www.joepify.nl/blog/website-gehackt-signalen  
> Bijgewerkt: 2026-10-22 · Auteur: Ayoub Assaidi, [Joepify](https://www.joepify.nl) (Rotterdam)

In het kort

- **Gehackt zijn herken je** aan een combinatie van signalen: onbekende beheerders, vreemde bestanden, doorverwijzingen, spam in Google en fouten in je serverlogs.
- **De eerste 60 minuten:** offline zetten, kopie maken, logs veiligstellen, daarna pas wachtwoorden en sleutels vernieuwen.
- **Update PHP eerst.** PHP2Shell kan geheugen blootleggen, dus nieuwe wachtwoorden zijn pas veilig op een gepatchte server.
- **Herstellen of opschonen** hangt af van je back-up. Je leest hieronder hoe je kiest.

Je site doet iets vreemds en je vraagt je af: is mijn website gehackt? Sinds 21 oktober 2026 zijn er twee kritieke lekken in PHP zelf bekend, **PHP2Shell**. Een aanvaller hoeft er niet voor in te loggen. Er wordt al actief naar kwetsbare servers gezocht.

Dit artikel gaat over het herkennen en afhandelen van een hack, voor elke PHP-site. Wat het lek precies is lees je in [ons overzicht over PHP2Shell](https://www.joepify.nl/blog/php2shell-php-lek).

## Is mijn website gehackt? Zo herken je het

Eén vreemd verschijnsel bewijst weinig. Meerdere tegelijk wel. Loop deze lijst af:

| Waar kijk je | Dit wijst op een probleem | 
|---|---|
| Serverlogs | Ongewone multipart-verzoeken, gevolgd door geheugenfouten of herhaalde HTTP 500 | 
| PHP-processen | Herstarts die je niet kunt verklaren | 
| Cookies in verzoeken | Zeer grote of misvormde PHPSESSID-waarden | 
| Gebruikers | Beheerders die je niet zelf hebt aangemaakt | 
| Bestanden | PHP-bestanden in uploadmappen of recent gewijzigde bestanden die je niet kent | 
| Bezoekers | Doorverwijzingen, vooral op mobiel of vanuit Google | 
|  | Pagina's of titels over onderwerpen die je niet hebt geschreven | 
|  | Post van jouw domein komt niet meer aan | 

De eerste drie rijen noemt het onderzoeksteam van Wiz als mogelijke aanwijzingen voor een poging. Ze zijn geen bewijs. Een rustige log betekent ook niet dat je veilig bent, want een geslaagde aanval kan sporen wissen.

Gebruik je WordPress? Dan zoekt de [gratis WordPress check](https://www.joepify.nl/wordpress-check) onder meer naar spam, verborgen links en verdachte scripts, en toont hij of je PHP-versie nog updates krijgt.

## Geen tijd om dit zelf uit te zoeken?

**Geen tijd om dit zelf uit te zoeken?** Stuur je websiteadres. Ik kijk gratis welke PHP-versie draait en wat je host moet doen. Binnen 24 uur antwoord.

## De eerste 60 minuten: een checklist

Volgorde telt. Wie meteen wachtwoorden wijzigt op een nog kwetsbare server, geeft ze mogelijk opnieuw weg.

1. **Haal de site van het net.** Onderhoudsmodus, of een tijdelijke blokkade op serverniveau. Zo stopt schade aan bezoekers.
2. **Maak een kopie van de huidige staat.** Bestanden en database, gehackt of niet. Je hebt die later nodig om te zien hoe de aanvaller binnenkwam.
3. **Vraag logbestanden op** bij je hostingbedrijf: toegangslogs, foutlogs en PHP-logs, over de afgelopen dagen.
4. **Laat PHP bijwerken.** Gepatchte versies zijn 8.5.12, 8.4.27, 8.3.36 en 8.2.35. Heb je PHP 8.1 of ouder, vraag dan naar een backport of een upgrade. Meer daarover staat in [PHP 8.1 of ouder: geen officiële fix](https://www.joepify.nl/blog/php-8-1-geen-update).
5. **Vernieuw daarna alle toegang.** Zie het volgende onderdeel.
6. **Noteer wat je ziet,** met tijdstippen. Dat helpt bij de keuze tussen opschonen en herstellen.

## Welke wachtwoorden en sleutels vernieuw je?

PHP2Shell kan ook geheugen blootleggen. Dat betekent dat wat een draaiend PHP-proces vasthield, zoals databasewachtwoorden of API-sleutels, kan zijn gelekt. Behandel de server dus als gecompromitteerd en vernieuw, in deze volgorde:

- **Hosting- en FTP/SFTP-accounts** en SSH-sleutels die je niet herkent.
- **Het databasewachtwoord**, en pas daarna het configuratiebestand van je site.
- **API-sleutels** voor betalingen, e-mailverzending, bezorgdiensten en andere koppelingen.
- **Mailaccounts** en SMTP-wachtwoorden.
- **Beheeraccounts van je site**, en sessies van alle gebruikers beëindigen.
- **Beveiligingssleutels van je CMS,** bij WordPress de salts in wp-config.php.

Gebruik voor elk account een uniek wachtwoord uit een wachtwoordmanager en zet waar het kan tweestapsverificatie aan.

## Opschonen of herstellen?

Dit is de keuze waar de meeste eigenaren mee worstelen. Een korte afweging:

| Situatie | Meestal de beste route | 
|---|---|
| Schone back-up van vóór de hack, weinig nieuwe gegevens sindsdien | Herstellen op een gepatchte server | 
| Veel nieuwe bestellingen of berichten sinds de back-up | Gegevens veiligstellen, bestanden vers opbouwen, gegevens terugzetten | 
| Geen betrouwbare back-up | Opschonen door iemand die bestanden handmatig controleert | 
| Je weet niet wanneer de hack begon | Verse installatie, gegevens kritisch nalopen | 

Wat je ook kiest, de oorzaak moet weg. Een site die je terugzet op dezelfde kwetsbare PHP-versie, is binnen korte tijd opnieuw te raken. Voor WordPress staat de volledige aanpak in [WordPress gehackt: spoedhulp](https://www.joepify.nl/blog/wordpress-gehackt-spoedhulp).

## Controles na de schoonmaak

- Zoek in Google op *site:jouwdomein.nl* en kijk of er pagina's staan die je niet kent.
- Controleer geplande taken (cron) en de lijst met gebruikers.
- Test of mail van je domein weer aankomt.
- Bekijk de logs na een paar dagen opnieuw op dezelfde patronen.
- Meld de hack bij je klanten als hun gegevens mogelijk zijn blootgesteld. Bij persoonsgegevens kan een meldplicht gelden, vraag daarover advies.

## Wat je beter niet doet

- **Direct alles verwijderen.** Je wist dan het bewijs waarmee je de oorzaak vindt.
- **Alleen de zichtbare rommel opruimen.** Aanvallers laten vaak een tweede toegang achter, zodat ze later terug kunnen komen.
- **Wachtwoorden wijzigen op een nog kwetsbare server.** Eerst PHP bijwerken, dan pas vernieuwen.
- **Een willekeurige beveiligingsplugin installeren** en de melding "geen problemen gevonden" als eindoordeel nemen. Zo'n scan ziet niet alles.
- **Wachten tot het vanzelf overgaat.** Een gehackte site kan intussen spam versturen of bezoekers doorsturen, wat je reputatie bij Google en bij mailproviders schaadt.

## Voorkomen dat het opnieuw gebeurt

Alleen updaten is de volledige oplossing voor PHP2Shell. Tijdelijke instellingen van je host verkleinen het risico, maar maken je niet veilig. Daarnaast helpt dit:

- Weet welke PHP-versie je draait en wie die bijwerkt.
- Houd een externe back-up aan die je regelmatig terugzet in een test.
- Laat updates en monitoring door iemand bewaken. Dat kan met een [WordPress onderhoudscontract](https://www.joepify.nl/wordpress-onderhoudscontract) vanaf €35 per maand.
- Vermijd onofficiële fix-plugins of snippets die beloven PHP2Shell te verhelpen.

## Bronnen

- [PHP.net, beveiligingsbericht van 21 oktober 2026](https://www.php.net/)
- [UK NCSC, Critical security issue affecting PHP](https://www.ncsc.gov.uk/news/critical-security-issue-affecting-php)
- [Patchstack, PHP major vulnerability alert](https://patchstack.com/articles/php-major-vulnerability-alert-10-2026/)
- [Sansec, onderzoek naar PHP2Shell](https://sansec.io/research/php2shell)

Heb je een webshop? Lees dan ook [PHP2Shell en je webshop](https://www.joepify.nl/blog/php2shell-webshop), en voor WordPress [loopt jouw site risico?](https://www.joepify.nl/blog/php2shell-wordpress)

---
Bron: [Website gehackt? Signalen na PHP2Shell en wat je doet](https://www.joepify.nl/blog/website-gehackt-signalen) · Licentie: CC BY 4.0, noem Joepify met een link naar de originele pagina.
