---
title: "PHP 8.2 end of life: wat nu voor je WordPress-site?"
canonical: https://www.joepify.nl/kennisbank/php-8-2-end-of-life
updated: 2026-10-22
author: Ayoub Assaidi (Joepify)
license: CC BY 4.0
---

# PHP 8.2 end of life: wat nu voor je WordPress-site?

> Origineel en altijd actueel: https://www.joepify.nl/kennisbank/php-8-2-end-of-life  
> Bijgewerkt: 2026-10-22 · Auteur: Ayoub Assaidi, [Joepify](https://www.joepify.nl) (Rotterdam)

**Kort antwoord:** PHP 8.2 krijgt volgens php.net na **31 december 2026** geen beveiligingsupdates meer, dat is ruim twee maanden na vandaag. PHP 8.1 en ouder zijn al end of life. PHP 8.3 krijgt beveiligingsupdates tot 31 december 2027 en PHP 8.4 tot 31 december 2028. WordPress raadt PHP 8.3 of hoger aan. Draait je site op 8.2 of ouder, plan dan nu de overstap naar 8.3 of 8.4, met eerst een back-up en een test.

## Welke PHP-versies zijn nog ondersteund?

Op 22 oktober 2026 worden volgens [php.net](https://www.php.net/supported-versions.php) vier PHP-versies nog ondersteund: PHP 8.2, 8.3, 8.4 en 8.5. PHP 8.2 is daarvan de oudste en valt als eerste af.

- **PHP 8.5:** de nieuwste versie, uitgekomen 20 november 2025, beveiligingsupdates tot 31 december 2029. De laatste release is PHP 8.5.12, van 21 oktober 2026.
- **PHP 8.4:** uitgekomen 21 november 2024, bugfixes tot 31 december 2026, beveiligingsupdates tot 31 december 2028.
- **PHP 8.3:** uitgekomen 23 november 2023, beveiligingsupdates tot 31 december 2027.
- **PHP 8.2:** uitgekomen 8 december 2022, alleen nog beveiligingsupdates, tot **31 december 2026**.

Al end of life volgens de [EOL-pagina van php.net](https://www.php.net/eol.php): PHP 8.1 (31 december 2025), PHP 8.0 (26 november 2023) en PHP 7.4 (28 november 2022). Draait je WordPress-site op een van die versies, dan krijgt PHP op je server nu al geen enkele fix meer.

Veilig tegen het PHP2Shell-lek zijn volgens [php.net](https://www.php.net/) alleen de releases van 21 oktober 2026: PHP 8.5.12, 8.4.27, 8.3.36 en 8.2.35. Elke oudere patchversie binnen die reeksen is kwetsbaar, net als PHP 8.1 en ouder, waarvoor geen officiële release meer komt. Kijk dus niet alleen of je op 8.2 of 8.3 zit, maar naar het hele versienummer. Wat je nu doet, lees je in [PHP2Shell: kritiek lek in PHP](https://www.joepify.nl/blog/php2shell-php-lek).

## Wat is end of life, en wat is het risico?

End of life betekent dat een PHP-versie geen fixes meer krijgt, ook niet als er een beveiligingslek wordt gevonden. Volgens php.net krijgt elke PHP-versie twee jaar volledige ondersteuning en daarna twee jaar alleen beveiligingsupdates. Na die vier jaar is de versie end of life. Php.net raadt gebruikers van zo'n versie [dringend aan om te upgraden](https://www.php.net/eol.php), omdat oude versies je kunnen blootstellen aan lekken en bugs die in nieuwere versies al zijn opgelost.

Een WordPress-site op PHP 8.2 stopt niet op 1 januari 2027. Het risico groeit gaandeweg: ontdekte lekken in PHP blijven open. WordPress zegt over versies onder de aanbevolen versie dat ze end of life zijn en [je site kunnen blootstellen aan beveiligingslekken](https://wordpress.org/about/requirements/). Cijfers over hoe vaak dat misgaat, noem ik niet.

## Welke PHP-versie kies ik voor WordPress?

Voor WordPress is PHP 8.3 of hoger de beste keuze, want dat is volgens [WordPress.org](https://wordpress.org/about/requirements/) de aanbevolen versie. Zo verschillen de drie opties:

- **PHP 8.3** is wat WordPress aanbeveelt ("PHP 8.3 of hoger"). Veilig tot eind 2027, en breed getest door plugins.
- **PHP 8.4** geeft je een jaar langer. Controleer eerst of je thema en plugins het ondersteunen.
- **PHP 8.5** is het nieuwste. Pas als alles in je site expliciet compatibel is.

In de praktijk is PHP 8.3 voor de meeste WordPress-sites de veiligste stap. Mijn vuistregel: ga nu van 8.2 of ouder naar 8.3, of naar 8.4 als je plugins het aankunnen. Dan hoef je niet over twee maanden opnieuw te upgraden. Heb je daarnaast een webshop, let dan ook op WooCommerce: versie 11.6, gepland voor februari 2027, vereist volgens de [WooCommerce Developer Blog](https://developer.woocommerce.com/2026/09/29/php-8-1-requirement/) minimaal PHP 8.1.

## Hoe check je welke PHP-versie je WordPress-site draait?

De PHP-versie van een WordPress-site check je op drie manieren: in het WordPress-beheer, in het paneel van je hosting of met een scan van buitenaf.

1. In WordPress: **Extra > Sitestatus > Info > Server**. Daar staat de PHP-versie.
2. In het paneel van je hosting (DirectAdmin, cPanel, Plesk): zoek op "PHP-versie".
3. Of start de gratis [website check](https://www.joepify.nl/website-apk), die let op verouderde PHP.

Noteer de versie die je ziet, bijvoorbeeld 8.2.29. Het eerste deel (8.2) bepaalt hoe lang je nog beveiligingsupdates krijgt. Het laatste getal is de patchversie die je host installeert. Bij sommige hostingpartijen staat de PHP-versie per domein, dus check elk domein apart als je meer sites hebt.

## Hoe upgrade je veilig van PHP 8.2 in vijf stappen?

Veilig upgraden van PHP 8.2 naar 8.3 of 8.4 gaat in vijf stappen: eerst een back-up, daarna updates, vervolgens een test, dan controleren en pas als laatste live omzetten.

1. Back-up van bestanden en database.
2. WordPress, thema en plugins bijwerken. Verwijder wat je niet gebruikt.
3. Op een testomgeving de PHP-versie omzetten.
4. Doorklikken: formulieren, winkelwagen, betaling, inloggen en e-mails.
5. Pas dan live omzetten, en houd het foutlogboek bij het hosting-paneel open. Gaat iets mis? Zet de oude versie terug.

Terugschakelen naar de oude PHP-versie kost in de meeste hostingpanelen ongeveer een minuut, bijvoorbeeld via de PHP-keuze in DirectAdmin of cPanel. Een mislukte test is dus geen ramp. De volledige uitleg met veelvoorkomende problemen staat in [PHP-versie van WordPress updaten](https://www.joepify.nl/kennisbank/php-versie-wordpress).

## Welke fouten kom ik vaak tegen bij een PHP-upgrade?

De fouten die ik bij een upgrade van PHP 8.2 het vaakst tegenkom, gaan over planning en voorbereiding, niet over techniek. Dit zijn de vier die ik in de praktijk het meest zie:

- Denken dat de host het wel doet. Vaak moet jij de versie zelf kiezen.
- Een verlaten plugin die alleen op een oude PHP draait. Zoek een alternatief, want blijven hangen op oude PHP is de reden dat sites kwetsbaar blijven.
- Op PHP 8.2 blijven "omdat het werkt". Dat werkt tot 31 december 2026.
- Upgraden op de live site zonder back-up.

Alle vier zijn te voorkomen met een vaste planning. Zet eerst de PHP-overstap in je agenda of in je onderhoudscontract, ruim vóór de einddatum van je huidige versie. Voor PHP 8.2 betekent dat: vóór december 2026.

## Zo controleer je de PHP-versie van je site

De gratis Website APK van Joepify is een scan van buitenaf die ook de PHP-versie van je site controleert, zonder in te loggen. De [website check](https://www.joepify.nl/website-apk#apk-modules) leest van buitenaf af of je site een verouderde PHP-versie meldt. Verbergt je host de versie, dan zie je hem alleen in WordPress of je hostingpaneel. De APK wijzigt niets aan je site. Krijgt je PHP-versie na 31 december 2026 geen beveiligingsupdates meer, dan zie je dat terug in het onderdeel platform. Wil je de overstap en het bijhouden van plugins liever uitbesteden, kijk dan bij [WordPress onderhoud](https://www.joepify.nl/wordpress-onderhoud).

- Gratis tool[Check je PHP-versie met de gratis website check](https://www.joepify.nl/website-apk)
- Liever uitbesteden[Laat Joepify dit doen: PHP en plugins bijhouden met WordPress onderhoud](https://www.joepify.nl/wordpress-onderhoud)

---
Bron: [PHP 8.2 end of life: wat nu voor je WordPress-site?](https://www.joepify.nl/kennisbank/php-8-2-end-of-life) · Licentie: CC BY 4.0, noem Joepify met een link naar de originele pagina.
