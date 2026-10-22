---
title: "PHP 8.1 of ouder? Geen officiële fix voor PHP2Shell"
canonical: https://www.joepify.nl/blog/php-8-1-geen-update
updated: 2026-10-22
author: Ayoub Assaidi (Joepify)
license: CC BY 4.0
---

# PHP 8.1 of ouder? Geen officiële fix voor PHP2Shell

> Origineel en altijd actueel: https://www.joepify.nl/blog/php-8-1-geen-update  
> Bijgewerkt: 2026-10-22 · Auteur: Ayoub Assaidi, [Joepify](https://www.joepify.nl) (Rotterdam)

In het kort

- **PHP 8.1, 8.0 en 7.4** zijn end-of-life. Voor PHP2Shell komt er geen gewone beveiligingsrelease van PHP zelf, alleen een minimale broncode-backport die je host moet toepassen.
- **Op gedeelde hosting** kun je PHP niet zelf updaten. Je host moet het gepatchte pakket installeren of je helpen overstappen.
- **De echte oplossing** is upgraden naar een ondersteunde versie: PHP 8.3 of 8.4, met een back-up en een test van je plugins en thema.
- **Wij kijken gratis** welke PHP-versie je draait en wat je host moet doen. Binnen 24 uur een vrijblijvend voorstel.

Je hoort over een kritiek lek in PHP, je zoekt de update op, en dan blijkt je site op PHP 8.1 of nog ouder te draaien. Je ziet geen nieuwe versie voor jouw PHP langskomen. Dat klopt, en het is precies het probleem van dit artikel.

PHP2Shell is de verzamelnaam voor twee kritieke kwetsbaarheden in PHP zelf, waarmee een aanvaller zonder in te loggen code op je server kan uitvoeren. PHP bracht op 21 oktober 2026 patches uit. Maar die patches zijn er alleen voor de versies die PHP nog ondersteunt. De volledige uitleg staat in onze [hub over PHP2Shell](https://www.joepify.nl/blog/php2shell-php-lek). Hier kijken we naar wat je doet als je op een oude PHP-versie zit.

## Waarom er voor PHP 8.1 en ouder geen officiele fix is

Elke PHP-versie heeft een levenscyclus: ongeveer twee jaar waarin bugs en beveiligingsproblemen worden opgelost, en daarna nog een jaar met alleen beveiligingsupdates. Daarna is een versie end-of-life. Dan komt er niets meer uit, ook niet bij een kritiek lek.

PHP 7.4, 8.0 en 8.1 zitten inmiddels in die end-of-life-fase. Voor PHP2Shell heeft het PHP-securityteam wel minimale broncode-backports voor deze drie versies gepubliceerd, maar geen gewone release die je in een klik installeert. Of jij die backport krijgt, hangt volledig af van je hostingpartij of leverancier. PHP 7.3 en alles daarvoor, terug tot 5.4, zijn al langer end-of-life en krijgen helemaal niets. Volgens Wiz Research is elke PHP-versie terug tot 5.4 door minstens een van beide lekken te raken.

## Welke PHP-versies krijgen wel een patch?

Zoek eerst op welke versie jij draait en leg die naast deze tabel. Zit je in de bovenste rij, dan is er een directe update. Zit je lager, dan heb je je host nodig of moet je upgraden.

| Jouw PHP-versie | Status na PHP2Shell | 
|---|---|
| **8.5, 8.4, 8.3, 8.2** | Gepatcht. Update naar 8.5.12, 8.4.27, 8.3.36 of 8.2.35. | 
| **8.1, 8.0, 7.4** | Geen gewone release. Alleen een minimale broncode-backport, afhankelijk van je host. | 
| **7.3 en ouder (t/m 5.4)** | End-of-life. Geen fix vanuit PHP. Upgraden is de enige weg. | 

De les is simpel: hoe ouder je versie, hoe minder PHP voor je kan doen en hoe meer je zelf moet regelen.

Geen tijd om dit zelf uit te zoeken?

Stuur je websiteadres via WhatsApp of het formulier. Ik kijk gratis welke PHP-versie je draait en wat je host moet doen, en je hoort binnen 24 uur wat er nodig is.

[PHP2Shell-check via WhatsApp](https://wa.me/31687195043?text=PHP2Shell%20check) of [vraag het via het formulier aan](https://www.joepify.nl/?p=website&src=blog-php-8-1-geen-update-top&m=PHP2Shell%20check%20voor%20mijn%20website#contact).

## Optie 1: je host installeert een backport

Draait je site op gedeelde hosting, en dat geldt voor de meeste mkb-websites, dan kun je PHP niet zelf bijwerken. De patch of de backport moet door je hostingbedrijf worden geinstalleerd. Je kunt wel zelf controleren welke versie je draait en vaak ook wisselen naar een ondersteunde versie in je hostingpanel of in WordPress via Gereedschap, Sitediagnose, Info, Server.

Stel je host deze vragen, kort en concreet:

- **Welke PHP-versie draait mijn site nu?**
- **Hebben jullie de PHP2Shell-patch al geinstalleerd** op de servers waar mijn site staat?
- **Draai ik op 8.1 of ouder:** hebben jullie de backport toegepast, of kan ik overstappen naar 8.3 of 8.4?
- **Geldt dit ook voor mijn staging- of testomgeving?** Vergeten test-sites zijn een geliefd doelwit.

## Optie 2: upgraden naar PHP 8.3 of 8.4

Een backport houdt je oude versie net draaiende, maar lost het grotere probleem niet op: je zit op software die geen toekomst meer heeft. De duurzame keuze is upgraden naar een ondersteunde versie. Dat doe je zo:

1. **Maak een volledige back-up** van je bestanden en je database. Dit is je terugweg als er iets niet werkt.
2. **Controleer de compatibiliteit** van je plugins, thema of extensies met PHP 8.3 of 8.4. Oude of niet meer onderhouden onderdelen zijn de meest voorkomende oorzaak van problemen.
3. **Test op een staging-omgeving**, niet live. Klik je belangrijkste pagina's, formulieren en een bestelling of aanvraag door.
4. **Zet de versie om** in je hostingpanel en controleer de site meteen op foutmeldingen.
5. **Houd het een paar dagen in de gaten**, want sommige fouten komen pas bij specifieke acties naar boven.

Een ding is belangrijk: alleen updaten of upgraden is een volledige fix. Een losse fix-plugin of een code-snippet die claimt het lek te dichten, lost PHP2Shell niet op en wordt door PHP en securitypartijen afgeraden. Meer achtergrond over versies lees je in onze kennisbank over [de juiste PHP-versie voor WordPress](https://www.joepify.nl/kennisbank/php-versie-wordpress).

## Wat kost upgraden en hoe lang duurt het?

Een versie-upgrade zelf is vaak een kleine ingreep, maar het testwerk eromheen bepaalt de tijd. Wij geven geen prijs zonder je situatie te kennen, want dat is gokken. Wel dit:

- **Gratis check:** je stuurt je websiteadres door, wij kijken welke PHP-versie draait en wat je host moet doen.
- **Binnen 24 uur een vrijblijvend voorstel** met wat er nodig is en wat het kost.
- **Spoed:** is je site al getroffen of loopt er iets vast, dan is er spoedhulp vanaf 79 euro, met geen fix geen kosten.
- **Doorlopend:** wil je dit niet elke keer zelf, dan houdt een [onderhoudscontract vanaf 35 euro per maand](https://www.joepify.nl/wordpress-onderhoudscontract) je updates, back-ups en monitoring bij.

## Je stappenplan voor een oude PHP-versie

1. **Zoek je PHP-versie op** via je hostingpanel of Sitediagnose in WordPress.
2. **Leg die naast de tabel** hierboven en bepaal of je gepatcht, afhankelijk van een backport, of end-of-life bent.
3. **Mail je host** met de vragen hierboven als je op 8.1 of ouder zit.
4. **Plan de upgrade** naar 8.3 of 8.4 met back-up en een test op staging.
5. **Kun je nu niet updaten** en is de site een hoog risico, zet hem dan tijdelijk in onderhoudsmodus.
6. **Twijfel je ergens over?** Laat ons gratis meekijken voordat je iets omzet.

Zit je webshop op een oude versie, lees dan ook [PHP2Shell en je webshop](https://www.joepify.nl/blog/php2shell-webshop). Gebruik je WordPress, dan is [WordPress en PHP2Shell](https://www.joepify.nl/blog/php2shell-wordpress) de juiste start.

---
Bron: [PHP 8.1 of ouder? Geen officiële fix voor PHP2Shell](https://www.joepify.nl/blog/php-8-1-geen-update) · Licentie: CC BY 4.0, noem Joepify met een link naar de originele pagina.
