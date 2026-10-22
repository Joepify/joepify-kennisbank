---
title: "PHP2Shell: kritiek lek in PHP, dit moet je nu doen"
canonical: https://www.joepify.nl/blog/php2shell-php-lek
updated: 2026-10-22
author: Ayoub Assaidi (Joepify)
license: CC BY 4.0
---

# PHP2Shell: kritiek lek in PHP, dit moet je nu doen

> Origineel en altijd actueel: https://www.joepify.nl/blog/php2shell-php-lek  
> Bijgewerkt: 2026-10-22 · Auteur: Ayoub Assaidi, [Joepify](https://www.joepify.nl) (Rotterdam)

In het kort

- **PHP2Shell** zijn twee kritieke lekken in PHP zelf (CVE-2026-109618 en CVE-2026-109619, CVSS 9.2). Een aanvaller heeft geen login nodig.
- **Veilige versies:** PHP 8.5.12, 8.4.27, 8.3.36 en 8.2.35, uitgebracht op 21 oktober 2026.
- **Wie:** elke website of webshop op PHP, dus ook WordPress, WooCommerce, Magento en Laravel. Plugin-updates helpen hier niet.
- **Vandaag doen:** PHP-versie checken, je host laten patchen en bij twijfel je wachtwoorden en sleutels vervangen.

Op 21 oktober 2026 zette php.net een ongewoon duidelijke melding op de voorpagina: kritieke lekken waarmee code op afstand kan worden uitgevoerd, update nu. Dat raakt bijna iedereen met een website. PHP draait volgens W3Techs op ongeveer 69% van de websites waarvan de servertaal bekend is.

Op deze pagina lees je rustig wat er aan de hand is, of jouw site geraakt wordt en wat je vandaag doet. Voor specifieke situaties zijn er aparte artikelen over [WordPress](https://www.joepify.nl/blog/php2shell-wordpress), [webshops](https://www.joepify.nl/blog/php2shell-webshop), [PHP 8.1 en ouder](https://www.joepify.nl/blog/php-8-1-geen-update) en [signalen van een hack](https://www.joepify.nl/blog/website-gehackt-signalen).

## Wat is PHP2Shell?

**PHP2Shell** is de naam voor twee kritieke kwetsbaarheden in de PHP-interpreter, het programma op de server dat PHP-code uitvoert. Het lek zit dus niet in één plugin of CMS, maar onder alles wat op PHP draait. Een aanvaller kan zonder in te loggen eigen code uitvoeren op een server met een ongepatchte versie.

Het gaat om twee fouten in hoe PHP met geheugen omgaat:

- **CVE-2026-109618:** als PHP tegen een geheugentekort aanloopt, kan de afhandeling daarvan PHP onderbreken terwijl de gegevens van een verzoek nog maar half zijn klaargezet. Dat geheugen kan daarna misbruikt worden.
- **CVE-2026-109619:** gegevens van een verzoek blijven bestaan nadat het bijbehorende geheugen al is vrijgegeven. Ook dat leidt tot het uitvoeren van code, en daarnaast kan er geheugen uitlekken. Daarin kunnen wachtwoorden en API-sleutels staan.

Het PHP-beveiligingsteam geeft het een score van 9.2 op CVSS v4.0: kritiek.

## Tijdlijn: van uitgelekt lek tot patch

- **20 oktober 2026:** details over de lekken komen naar buiten voordat de gecoördineerde bekendmaking klaar is.
- **21 oktober 2026:** PHP haalt de releases naar voren en brengt patches uit. php.net schrijft: "All PHP users are strongly encouraged to update immediately."
- **21 oktober 2026:** Cloudflare meldt de eerste aanvallen. watchTowr reproduceert beide lekken en ziet pogingen tot misbruik.

Omdat de details eerder uitlekten, hadden aanvallers en verdedigers dezelfde startpositie. Dat maakt snel patchen belangrijker dan normaal.

Geen tijd om dit zelf uit te zoeken?

Stuur me je websiteadres. Ik kijk gratis welke PHP-versie je site draait en zet op een rij wat je host moet doen. Je krijgt binnen 24 uur antwoord.

## Wie loopt risico?

Iedereen met PHP dat webverzoeken afhandelt en nog niet is bijgewerkt. Dat geldt voor alle gangbare manieren waarop PHP draait: PHP-FPM, Apache mod\_php, php-cgi, FrankenPHP en LiteSpeed. Bij **Apache mod\_php** is het risico het grootst, omdat de aanval daar kan afgaan voordat er ook maar één regel van je eigen website wordt uitgevoerd.

Onderzoekers lieten werkende aanvallen zonder login zien tegen WordPress, Drupal en Joomla (Wiz, op de nieuwste containerimages) en tegen specifieke versies van Magento (Calif). Volgens Wiz Research is elke PHP-versie vanaf 5.4 gevoelig voor minstens één van de twee lekken. Silas Cutler schatte het aantal mogelijk kwetsbare servers op meer dan 1,3 miljoen.

Heb je een webshop op **Shopify**? Dan draai je zelf geen PHP-server. Dit lek gaat over servers waarop PHP draait.

## Welke PHP-versies zijn veilig?

| Jouw versie | Status | Wat je doet | 
|---|---|---|
| PHP 8.5 | Gepatcht in 8.5.12 | Bijwerken naar 8.5.12 | 
| PHP 8.4 | Gepatcht in 8.4.27 | Bijwerken naar 8.4.27 | 
| PHP 8.3 | Gepatcht in 8.3.36 | Bijwerken naar 8.3.36 | 
| PHP 8.2 | Gepatcht in 8.2.35 | Bijwerken naar 8.2.35 | 
| PHP 7.4, 8.0, 8.1 | Geen officiële release, alleen een minimale backport in de broncode | Backport via je host of leverancier, of overstappen naar 8.3 of 8.4 | 
| PHP 5.4 tot en met 7.3 | End-of-life, geen fix van PHP | Zo snel mogelijk overstappen | 

Zit je op 8.1 of ouder, lees dan [PHP 8.1 of ouder: geen officiële fix](https://www.joepify.nl/blog/php-8-1-geen-update). Hoe je veilig naar een nieuwere versie gaat, staat in de kennisbank bij [PHP-versie van WordPress updaten](https://www.joepify.nl/kennisbank/php-versie-wordpress).

## Stappenplan: dit doe je vandaag

1. **Maak een lijst van al je PHP-installaties.** Niet alleen je hoofdsite, ook staging- en testsites, oude subdomeinen en die ene microsite van een campagne. Een vergeten testsite is net zo goed een ingang.
2. **Check per site de PHP-versie.** In je hostingpaneel, of in WordPress onder Gereedschap > Sitediagnose > Info > Server. Onze gratis [WordPress check](https://www.joepify.nl/wordpress-check) toont de PHP-versie als je server die meestuurt.
3. **Laat patchen.** Op gedeelde hosting kun je PHP niet zelf updaten. Vraag je host of de versies van 21 oktober zijn geïnstalleerd en kies in je paneel een ondersteunde versie. Heb je een eigen server, installeer dan zelf de nieuwe pakketten en herstart PHP-FPM of Apache.
4. **Kan het niet direct?** Is je site belangrijk of gevoelig en lukt patchen vandaag niet, zet de site dan tijdelijk in onderhoudsmodus of offline. Installeer geen onofficiële fix-plugins of snippets.
5. **Zie je signalen van misbruik?** Behandel de server dan als gecompromitteerd. Vervang je database-wachtwoord, API-sleutels en mailwachtwoorden, want die kunnen uit het geheugen zijn gelekt. Wat je verder doet, lees je in [website gehackt: signalen en eerste stappen](https://www.joepify.nl/blog/website-gehackt-signalen).

## Tijdelijke maatregelen voor hosts en developers

Deze maatregelen verkleinen de kans op misbruik zolang patchen nog niet kan. Ze maken je server **niet** veilig.

- `session.upload_progress.enabled=0` in php.ini of de FPM-pool, niet via .user.ini of ini\_set, en daarna de workers herstarten.
- `memory_limit=-1` zo instellen dat een applicatie het niet kan overschrijven.
- Een strakkere `post_max_size`.
- WAF-regels van Cloudflare, maar alleen als echt al het verkeer via Cloudflare loopt en je server niet direct bereikbaar is.

Wiz noemt een paar aanwijzingen dat iemand je server probeert: ongewone multipart-verzoeken gevolgd door memory-limit-fouten of herhaalde HTTP 500-fouten, heel grote of vreemd opgebouwde PHPSESSID-cookies en PHP-workers die zonder duidelijke reden herstarten. Dat is geen bewijs van een hack, wel een reden om beter te kijken.

## Wat ik voor je kan doen

Je hoeft dit niet alleen uit te zoeken. Stuur je websiteadres en ik kijk gratis welke PHP-versie draait en wat je host moet regelen. Heb je vandaag hulp nodig, dan is er [spoedhulp vanaf €79](https://www.joepify.nl/wordpress-problemen-oplossen) met reactie binnen 2 uur. Wil je dit soort updates voortaan niet meer zelf bijhouden, kijk dan naar een [onderhoudscontract vanaf €35 per maand](https://www.joepify.nl/wordpress-onderhoudscontract). Twijfel je over een oude webshop, dan is een [overstap naar Shopify](https://www.joepify.nl/shopify-migratie) ook een optie, omdat je dan zelf geen PHP-server beheert.

---
Bron: [PHP2Shell: kritiek lek in PHP, dit moet je nu doen](https://www.joepify.nl/blog/php2shell-php-lek) · Licentie: CC BY 4.0, noem Joepify met een link naar de originele pagina.
