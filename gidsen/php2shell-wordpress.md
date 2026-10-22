---
title: "WordPress en PHP2Shell: loopt jouw site risico?"
canonical: https://www.joepify.nl/blog/php2shell-wordpress
updated: 2026-10-22
author: Ayoub Assaidi (Joepify)
license: CC BY 4.0
---

# WordPress en PHP2Shell: loopt jouw site risico?

> Origineel en altijd actueel: https://www.joepify.nl/blog/php2shell-wordpress  
> Bijgewerkt: 2026-10-22 · Auteur: Ayoub Assaidi, [Joepify](https://www.joepify.nl) (Rotterdam)

In het kort

- **Ja, WordPress loopt risico.** PHP2Shell zit in PHP, de laag onder WordPress. Een site met alle plugins up-to-date kan nog steeds worden overgenomen.
- **Check je versie** in Gereedschap > Sitediagnose > Info > Server. Veilig: 8.5.12, 8.4.27, 8.3.36 of 8.2.35.
- **Je host patcht**, niet jij. Vraag of de update van 21 oktober is geplaatst.
- **Daarna:** wachtwoorden en sleutels vervangen als je twijfelt, en een schone back-up klaarzetten.

Je hebt je WordPress-site netjes bijgehouden. Automatische updates aan, een beveiligingsplugin, sterke wachtwoorden. En toch staat er deze week een lek open waar je zelf niets aan kunt doen vanuit wp-admin. Dat voelt oneerlijk, maar het is goed te regelen als je weet waar je moet kijken.

## Wat PHP2Shell betekent voor WordPress

PHP2Shell zijn twee kritieke lekken in PHP zelf, op 21 oktober 2026 gedicht in nieuwe PHP-versies. Een aanvaller heeft geen account op je site nodig. Onderzoekers van Wiz lieten een werkende aanval zien op een standaard WordPress-installatie. De volledige uitleg, tijdlijn en versietabel staan in ons hoofdartikel [PHP2Shell: kritiek lek in PHP](https://www.joepify.nl/blog/php2shell-php-lek).

Voor jou als site-eigenaar komt het neer op één vraag: draait mijn hosting al een gepatchte PHP-versie?

## Waarom plugin-updates je hier niet beschermen

Bij de meeste WordPress-lekken zit het probleem in een plugin of thema. Je klikt op bijwerken en het gat is dicht. Bij PHP2Shell werkt dat niet, omdat de fout een laag dieper zit.

| Laag | Wie werkt het bij | Helpt tegen PHP2Shell? | 
|---|---|---|
| Plugins en thema | Jij of je webbeheerder, in wp-admin | Nee | 
| WordPress-kern | Jij, of automatisch | Nee | 
| Beveiligingsplugin | Jij | Nee, die draait zelf op PHP | 
| PHP op de server | Je hostingbedrijf, of jij bij een eigen server | Ja, dit is de enige echte fix | 

Bij Apache mod\_php kan de aanval zelfs afgaan voordat WordPress geladen is. Een beveiligingsplugin krijgt dan geen kans om iets te blokkeren.

Geen tijd om dit zelf uit te zoeken?

Stuur me je websiteadres. Ik kijk gratis welke PHP-versie je WordPress-site draait en vertel je wat je host moet doen. Binnen 24 uur heb je antwoord.

## Zo zie je je PHP-versie in WordPress

1. Log in op wp-admin met een beheerdersaccount.
2. Ga naar **Gereedschap > Sitediagnose**. In sommige vertalingen heet het menu Hulpmiddelen.
3. Klik bovenaan op het tabblad **Info**.
4. Open het blok **Server** en lees de regel PHP-versie.

Staat daar 8.2.35, 8.3.36, 8.4.27, 8.5.12 of hoger in dezelfde reeks? Dan is PHP2Shell gedicht. Staat er een lager nummer, of 8.1 en ouder, dan moet er iets gebeuren. Voor die oude versies is er geen gewone update, lees daarvoor [PHP 8.1 of ouder](https://www.joepify.nl/blog/php-8-1-geen-update). Hoe je zonder kapotte plugins overstapt naar een nieuwere versie, lees je in [PHP-versie van WordPress updaten](https://www.joepify.nl/kennisbank/php-versie-wordpress).

Kom je niet in wp-admin? De gratis [WordPress check](https://www.joepify.nl/wordpress-check) laat van buitenaf zien of je PHP-versie nog updates krijgt, als je server die versie meestuurt.

## Wat je je hostingbedrijf vraagt

Op gedeelde hosting, zoals bij de meeste mkb-sites, kun je PHP niet zelf patchen. Je host moet de nieuwe pakketten installeren. Stuur een kort bericht met deze vragen:

- Zijn de PHP-releases van 21 oktober 2026 tegen PHP2Shell (CVE-2026-109618 en CVE-2026-109619) op mijn server geïnstalleerd?
- Geldt dat voor alle PHP-versies die ik in het paneel kan kiezen?
- Ik draai PHP 8.1 of ouder: leveren jullie een backport, of moet ik overstappen?
- Hebben jullie op mijn account vreemde activiteit gezien sinds 20 oktober?

Krijg je geen helder antwoord, of blijft je host op een oude versie hangen, dan is [verhuizen naar andere hosting](https://www.joepify.nl/blog/website-verhuizen-andere-hosting) een serieuze optie.

## Draai je WordPress op een eigen server of VPS?

Dan ben jij, of je developer, zelf verantwoordelijk. Installeer de gepatchte PHP-pakketten van je distributie of leverancier en herstart daarna PHP-FPM of Apache. Zonder herstart blijven de oude workers met de kwetsbare code draaien. Controleer na afloop in Sitediagnose of de nieuwe versie zichtbaar is.

Lukt patchen vandaag niet, dan zijn er tijdelijke instellingen die het risico verkleinen, zoals `session.upload_progress.enabled=0` in php.ini. Die staan in het [hoofdartikel](https://www.joepify.nl/blog/php2shell-php-lek). Ze maken je server niet veilig, ze kopen alleen tijd. Draait er een webshop op dezelfde server, lees dan ook [PHP2Shell en je webshop](https://www.joepify.nl/blog/php2shell-webshop).

## Nazorg: wachtwoorden, sleutels en back-ups

Eén van de twee lekken kan geheugen laten uitlekken. Bij WordPress kan daar gevoelige informatie in staan. Was je site kwetsbaar en twijfel je, vervang dan:

- Het **database-wachtwoord**, en pas het daarna aan in wp-config.php.
- De **beveiligingssleutels (salts)** in wp-config.php. Daarmee worden alle ingelogde gebruikers uitgelogd.
- **API-sleutels** van plugins, zoals betaal-, mail- of SMTP-koppelingen.
- **Wachtwoorden** van beheerders, FTP en de mailboxen van je domein.

Zet ook een recente back-up apart van vóór 20 oktober, buiten je hosting. Mocht er later iets blijken, dan heb je een schone versie om op terug te vallen.

## Wanneer bel je spoedhulp?

Zie je onbekende beheerders, bestanden die je niet kent, doorsturingen naar vreemde sites of spam in Google? Dan is updaten niet meer genoeg en moet de site worden schoongemaakt. De signalen staan in [website gehackt: de signalen](https://www.joepify.nl/blog/website-gehackt-signalen). Voor WordPress lees je wat je meteen doet in [WordPress gehackt? Spoedhulp](https://www.joepify.nl/blog/wordpress-gehackt-spoedhulp).

Wil je het niet zelf doen, dan is er [WordPress spoedhulp](https://www.joepify.nl/wordpress-problemen-oplossen): vanaf €79, reactie binnen 2 uur, en geen fix, geen kosten. Wil je dit soort updates voortaan niet meer zelf volgen? Met een [onderhoudscontract vanaf €35 per maand](https://www.joepify.nl/wordpress-onderhoudscontract) houd ik WordPress, plugins en PHP bij, met een back-up vóór elke update.

---
Bron: [WordPress en PHP2Shell: loopt jouw site risico?](https://www.joepify.nl/blog/php2shell-wordpress) · Licentie: CC BY 4.0, noem Joepify met een link naar de originele pagina.
