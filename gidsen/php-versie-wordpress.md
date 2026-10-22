---
title: "PHP-versie WordPress updaten: zo doe je het veilig"
canonical: https://www.joepify.nl/kennisbank/php-versie-wordpress
updated: 2026-10-22
author: Ayoub Assaidi (Joepify)
license: CC BY 4.0
---

# PHP-versie WordPress updaten: zo doe je het veilig

> Origineel en altijd actueel: https://www.joepify.nl/kennisbank/php-versie-wordpress  
> Bijgewerkt: 2026-10-22 · Auteur: Ayoub Assaidi, [Joepify](https://www.joepify.nl) (Rotterdam)

**Actueel (22 oktober 2026):** voor PHP2Shell, een kritiek lek in PHP, zijn alleen PHP 8.2.35, 8.3.36, 8.4.27 en 8.5.12 gepatcht. Check dus niet alleen je versie, maar ook of je host al heeft bijgewerkt. [Lees wat je nu moet doen](https://www.joepify.nl/blog/php2shell-php-lek)

**Kort antwoord:** PHP 8.2 krijgt na 31 december 2026 geen beveiligingsupdates meer. Versies 8.1 en ouder krijgen die al niet meer. WordPress raadt PHP 8.3 of hoger aan, en WooCommerce 11.6 (gepland voor februari 2027) werkt niet meer op PHP 7.4 en 8.0. Je ziet je versie in WordPress onder Hulpmiddelen > Sitediagnose > Info > Server. Update op een testomgeving, controleer je plugins en zet dan pas je live site over.

## Waarom doet de PHP-versie van je WordPress-site ertoe?

De PHP-versie van je WordPress-site bepaalt of de basis onder je site nog beveiligingsupdates krijgt. PHP is de programmeertaal waarin WordPress, je thema en je plugins draaien. Je hostingpartij bepaalt welke versie je server gebruikt, maar vaak moet je die keuze zelf maken in je hostingpaneel. Draait je site op een versie zonder beveiligingsupdates, dan worden lekken in PHP zelf niet meer gedicht. Daarnaast stoppen plugins één voor één met ondersteuning voor oude versies, waardoor je updates gaat missen.

Volgens de officiële tabel op [php.net](https://www.php.net/supported-versions.php) gelden deze einddata:

- **PHP 8.2:** beveiligingsupdates tot 31 december 2026;
- **PHP 8.3:** beveiligingsupdates tot 31 december 2027;
- **PHP 8.4:** beveiligingsupdates tot 31 december 2028;
- **PHP 8.5:** beveiligingsupdates tot 31 december 2029.

Elke PHP-versie krijgt volgens php.net twee jaar volledige ondersteuning en daarna nog twee jaar alleen kritieke beveiligingsfixes. Alles onder 8.2 staat niet meer in de tabel en krijgt dus niets meer.

WordPress zelf [raadt PHP 8.3 of hoger aan](https://wordpress.org/about/requirements/). Het werkt nog op PHP 7.4, maar WordPress schrijft er zelf bij dat die oude versies je site kwetsbaar kunnen maken.

## Wat verandert WooCommerce aan de PHP-versie die je nodig hebt?

WooCommerce 11.6 vereist PHP 8.1 of hoger. Volgens de [WooCommerce Developer Blog (29 september 2026)](https://developer.woocommerce.com/2026/09/29/php-8-1-requirement/) staat die versie gepland voor februari 2027. Versie 11.5 is de laatste die nog op PHP 7.4 en 8.0 werkt, en vanaf 11.3 zien winkels op die versies een melding in het beheer. Volgens WooCommerce draait ongeveer 7% van de gemeten winkels nog op PHP 7.4 en 2% op PHP 8.0. Die cijfers komen alleen van winkels die gebruiksgegevens delen, dus het echte aandeel kan anders liggen. Zit jij daarbij, dan kun je na februari 2027 geen WooCommerce-updates meer installeren. Ook geen beveiligingsupdates.

Mijn advies: spring niet naar 8.1 maar meteen naar 8.3 of 8.4. PHP 8.1 staat al niet meer in de ondersteuningstabel van php.net. Met 8.1 voldoe je dus wel aan de eis van WooCommerce, maar krijg je geen beveiligingsupdates. Met PHP 8.3 zit je tot eind 2027 goed, met PHP 8.4 tot eind 2028.

## Stap 1: hoe zie je welke PHP-versie je WordPress-site draait?

De PHP-versie van een WordPress-site vind je op drie plekken: in het WordPress-beheer, in je hostingpaneel en soms van buitenaf. De snelste route is Sitediagnose, een standaardonderdeel van WordPress dat volgens de [documentatie van WordPress.org](https://wordpress.org/documentation/article/site-health-screen/) informatie over je server en aanbevelingen voor je site toont. Draait je site bijvoorbeeld nog op PHP 8.2, dan plan je de overstap vóór 31 december 2026.

- **In WordPress:** ga naar Hulpmiddelen > Sitediagnose > Info en open het blok Server. Daar staat de PHP-versie. Draait je site op een verouderde versie, dan toont het tabblad Status vaak al een melding.
- **In je hostingpaneel:** in DirectAdmin, cPanel of Plesk heet het meestal "PHP-versie" of "Select PHP version". Bij sommige partijen staat het per domein.
- **Van buitenaf:** sommige servers sturen de versie mee in de header `X-Powered-By`. Dat is handig voor een check, maar vertelt ook aanvallers welke versie je draait. Vraag je host om die header uit te zetten (`expose_php = Off`).

## Stap 2: hoe maak je een back-up en een testomgeving?

Een back-up voor een PHP-update bestaat uit twee delen: alle bestanden van je site (WordPress, thema's, plugins en uploads) en de database met je pagina's, bestellingen en instellingen. Maak eerst een volledige back-up van bestanden en database, en controleer dat je hem kunt terugzetten. Een back-up die nooit is teruggezet, blijkt in de praktijk regelmatig onvolledig.

Veel hostingpartijen bieden een staging-omgeving: een kopie van je site op een apart adres, bijvoorbeeld staging.jouwdomein.nl. Zet daar de nieuwe PHP-versie aan en test eerst alles op die kopie. Bezoekers en klanten merken er dan niets van. Heb je geen staging, kies dan een rustig moment en houd de oude versie bij de hand om terug te schakelen. Schrijf vooraf op welke PHP-versie je nu draait, zodat je weet waarnaar je terug moet.

## Stap 3: waarom update je alles voordat je PHP verandert?

Alles updaten vóór de PHP-overstap voorkomt de meeste fouten, omdat problemen na een PHP-update bijna altijd uit verouderde plugins, thema's of eigen code komen. Recente versies van plugins zijn meestal al aangepast aan nieuwe PHP-versies. Oude versies vaak niet. Werk dus eerst alles bij en wacht daarna een dag met de PHP-overstap, zodat je ziet of de updates zelf goed gaan.

1. Update WordPress, je thema en al je plugins naar de nieuwste versie.
2. Kijk per plugin op de pluginpagina of hij recent is bijgewerkt. Een plugin die al jaren geen update kreeg, is het grootste risico. Zoek dan een vervanger.
3. Verwijder plugins en thema's die je niet gebruikt. Wat er niet staat, kan ook niet stukgaan.
4. Heb je een maatwerkthema of eigen code laten maken, vraag de bouwer dan of die getest is op PHP 8.3 of 8.4.

## Stap 4: hoe update je PHP in WordPress en test je de nieuwe versie?

PHP updaten voor WordPress doe je niet in WordPress zelf, maar in je hostingpaneel: in DirectAdmin, cPanel of Plesk kies je daar de nieuwe PHP-versie. Daarna test je de onderdelen van je WordPress-site die bezoekers en klanten het meest gebruiken.

1. Zet de nieuwe PHP-versie aan in je hostingpaneel (eerst op staging).
2. Loop je belangrijkste pagina's door: home, een productpagina, het contactformulier.
3. Doe bij een webshop een testbestelling tot en met de betaling en de bevestigingsmail.
4. Log in als beheerder en open een paar pagina's in de editor.
5. Kijk in de foutlog van je hosting of in `wp-content/debug.log` (als je debuglog aanstaat) naar nieuwe fouten.

Gaat er iets mis, zet dan de oude versie terug in je hostingpaneel. Dat kost een minuut. Zoek daarna rustig uit welke plugin de fout geeft.

## Veelvoorkomende problemen na een PHP-update: wat doe je eraan?

De drie problemen die na een PHP-update van WordPress het vaakst voorkomen, zijn een kritieke fout, zichtbare waarschuwingen en een host die geen nieuwe versie aanbiedt.

- **Een wit scherm of "Er is een kritieke fout op deze website".** Meestal een verouderde plugin. WordPress stuurt dan vaak een mail naar het beheerdersadres met de naam van de plugin.
- **Waarschuwingen bovenaan de pagina.** Dat zijn vaak "deprecated"-meldingen. Ze zijn niet direct gevaarlijk, maar horen niet zichtbaar te zijn voor bezoekers. Zet het tonen van fouten uit en los ze daarna op.
- **De host biedt geen nieuwe versie.** Dan is het tijd om te verhuizen. Lees [website verhuizen naar andere hosting](https://www.joepify.nl/blog/website-verhuizen-andere-hosting).

Een kritieke fout na een PHP-update is bijna altijd terug te draaien. Zet eerst de vorige PHP-versie terug in je hostingpaneel. Werk daarna de plugin uit de foutmail bij of vervang hem, en probeer de overstap opnieuw op staging.

## Hoe vaak moet je de PHP-versie van WordPress updaten?

De PHP-versie van een WordPress-site update je ongeveer eens per twee jaar. Volgens [php.net](https://www.php.net/supported-versions.php) verschijnt er elk jaar in november of december een nieuwe PHP-versie, en elke versie krijgt vier jaar ondersteuning: twee jaar volledig en twee jaar alleen voor beveiliging. Ga je nu naar PHP 8.3, dan staat de volgende overstap voor eind 2027 op de planning. Kies je 8.4, dan heb je tot eind 2028. Daarna volgt bijvoorbeeld PHP 8.5, dat volgens php.net tot 31 december 2029 beveiligingsupdates krijgt. Zet die datum meteen in je agenda of in je onderhoudscontract, dan sta je niet weer onder tijdsdruk. Een site die bij elke update netjes is bijgehouden, gaat bij een PHP-overstap zelden stuk. Een site die jaren stilstond, vaak wel.

## Zo controleer je de PHP-versie van je site

De gratis Website APK van Joepify controleert de PHP-versie van je site van buitenaf. Het onderdeel platform van de [website check](https://www.joepify.nl/website-apk#apk-modules) leest de PHP-versie als je server die meestuurt, en laat zien of die nog beveiligingsupdates krijgt. Ziet de APK geen versie, dan is dat goed nieuws voor je beveiliging, maar check hem dan zelf via Sitediagnose. Wil je de update niet zelf doen, of wil je dat iemand je plugins elke maand bijhoudt, kijk dan bij [WordPress onderhoud](https://www.joepify.nl/wordpress-onderhoud). Zie ook de guides over [beveiligingsheaders](https://www.joepify.nl/kennisbank/beveiligingsheaders-website) en een [verlopen SSL-certificaat](https://www.joepify.nl/kennisbank/ssl-certificaat-verlopen).

- Gratis tool[Check ook je vindbaarheid met de gratis SEO check](https://www.joepify.nl/gratis-seo-check)
- Liever uitbesteden[Laat PHP en plugins bijhouden met WordPress onderhoud](https://www.joepify.nl/wordpress-onderhoud)

---
Bron: [PHP-versie WordPress updaten: zo doe je het veilig](https://www.joepify.nl/kennisbank/php-versie-wordpress) · Licentie: CC BY 4.0, noem Joepify met een link naar de originele pagina.
