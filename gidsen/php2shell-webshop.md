---
title: "PHP2Shell en je webshop: WooCommerce en Magento"
canonical: https://www.joepify.nl/blog/php2shell-webshop
updated: 2026-10-22
author: Ayoub Assaidi (Joepify)
license: CC BY 4.0
---

# PHP2Shell en je webshop: WooCommerce en Magento

> Origineel en altijd actueel: https://www.joepify.nl/blog/php2shell-webshop  
> Bijgewerkt: 2026-10-22 · Auteur: Ayoub Assaidi, [Joepify](https://www.joepify.nl) (Rotterdam)

In het kort

- **Je webshop draait op PHP:** WooCommerce via WordPress, Magento en Adobe Commerce rechtstreeks. PHP2Shell zit in PHP zelf, dus een aanvaller kan je shop raken zonder in te loggen, los van je plugins.
- **Het risico is groter voor een shop:** er staan klantgegevens, bestellingen en inloggegevens in, en betaal- en verzendkoppelingen lopen via je server.
- **Updaten is de enige echte fix.** Je host moet PHP patchen, of je gaat naar een ondersteunde versie. Oude PHP of oude Magento betekent werk aan de winkel.
- **Wil je dit onderhoud kwijt?** Een gehost platform zoals Shopify draai je niet zelf op PHP. Wij kijken gratis mee en maken binnen 24 uur een voorstel.

Een webshop is geen gewone website. Er lopen betalingen doorheen, er staan klantgegevens in en hij moet dag en nacht open zijn. Juist daarom raakt een lek als PHP2Shell een shop harder dan een brochuresite. Een aanvaller die binnenkomt, komt bij veel meer dan een paar pagina's.

PHP2Shell is de verzamelnaam voor twee kritieke kwetsbaarheden in PHP, de taal waarin WooCommerce en Magento draaien. Een aanvaller kan er zonder account code mee uitvoeren op je server. PHP bracht op 21 oktober 2026 patches uit voor de ondersteunde versies. De volledige uitleg staat in onze [hub over PHP2Shell](https://www.joepify.nl/blog/php2shell-php-lek). Hier kijken we naar wat dit voor jouw webshop betekent.

## Waarom PHP2Shell juist voor webshops gevaarlijk is

Het lek zit niet in je webshopsoftware, maar in de laag eronder: PHP. Dat betekent dat een aanvaller je shop kan aanvallen voordat er ook maar een stukje van je eigen code of een plugin draait. Je mag al je extensies bijwerken, dat helpt hier niet.

Voor een shop telt bovendien wat er te halen valt. In en rond je shop staan klantgegevens, bestelhistorie, accounts en koppelingen naar betaal-, verzend- en boekhoudpartijen. Een van de twee kwetsbaarheden kan daarnaast geheugen prijsgeven, waardoor gegevens die op dat moment in het werkgeheugen staan, zoals wachtwoorden of API-sleutels, kunnen uitlekken. We zeggen bewust niets over waar jouw shop welke gegevens precies bewaart, maar de kern is: een shop op een niet-gepatchte server is een aantrekkelijk doelwit.

## Loopt jouw WooCommerce-shop risico?

WooCommerce is een plugin op WordPress, en WordPress draait op PHP. Onderzoekers demonstreerden pre-auth code-uitvoering tegen actuele WordPress-omgevingen. Dus ja, een WooCommerce-shop op een niet-gepatchte PHP-versie is kwetsbaar, hoe netjes je plugins ook bijgewerkt zijn.

Wat je doet: controleer je PHP-versie via Gereedschap, dan Sitediagnose, dan Info, dan Server. Vraag je host of de PHP2Shell-patch is geinstalleerd. Zit je op PHP 8.1 of ouder, dan is er geen gewone fix en moet je upgraden; dat leggen we uit in [PHP 8.1 of ouder, geen officiele fix](https://www.joepify.nl/blog/php-8-1-geen-update). Een bredere uitleg voor WordPress staat in [WordPress en PHP2Shell](https://www.joepify.nl/blog/php2shell-wordpress).

Geen tijd om dit zelf uit te zoeken?

Stuur je websiteadres via WhatsApp of het formulier. Ik kijk gratis welke PHP-versie je draait en wat je host moet doen, en je hoort binnen 24 uur wat er nodig is.

[PHP2Shell-check via WhatsApp](https://wa.me/31687195043?text=PHP2Shell%20check) of [vraag het via het formulier aan](https://www.joepify.nl/?p=website&src=blog-php2shell-webshop-top&m=PHP2Shell%20check%20voor%20mijn%20website#contact).

## Magento en Adobe Commerce

Magento en Adobe Commerce zijn volledig op PHP gebouwd, dus dezelfde regel geldt: op een niet-gepatchte PHP-versie ben je kwetsbaar. Onderzoek liet pre-auth code-uitvoering tegen specifieke Magento-versies zien. Magento-omgevingen draaien vaak op een vaste, soms oudere PHP-versie omdat extensies anders breken, en dat maakt snel patchen lastiger dan bij een eenvoudige site.

Draai je nog Magento 1, dan is er een extra probleem. Magento 1 wordt sinds 30 juni 2020 niet meer ondersteund. Er komen geen officiele patches meer voor het platform, en de PHP-versies eronder zijn vrijwel zeker ook end-of-life. Een Magento 1-shop op het open internet is in deze situatie een serieus risico. Upgraden naar een ondersteunde Magento-versie met een gepatchte PHP, of migreren naar een ander platform, is dan de enige veilige route.

## Wat je vandaag doet voor je webshop

1. **Zoek je PHP-versie op** en controleer of die gepatcht is (8.5.12, 8.4.27, 8.3.36 of 8.2.35) of nog moet.
2. **Vraag je host om te patchen** of om je naar een ondersteunde versie te helpen. Op gedeelde hosting kun je dit niet zelf.
3. **Maak een back-up** van bestanden en database voordat er iets verandert.
4. **Zie je tekenen van misbruik,** roteer dan je wachtwoorden en sleutels: database, betaal- en verzendkoppelingen, mail en beheerdersaccounts. Omdat geheugen kan uitlekken, is dat een verstandige voorzorg.
5. **Let op signalen** zoals onverklaarbare 500-fouten, vreemde of heel grote sessiecookies en PHP-processen die blijven herstarten. Dat is geen bewijs, wel reden om goed te kijken.

Vermoed je dat er al iets mis is? Lees dan [Website gehackt? Signalen na PHP2Shell](https://www.joepify.nl/blog/website-gehackt-signalen) en handel snel.

## De strategische optie: een gehost platform

Patchen, versies bijhouden, extensies testen: bij een zelf gehoste webshop blijft dat jouw verantwoordelijkheid, bij elk nieuw lek opnieuw. Voor veel ondernemers is dat niet de business waar ze in willen zitten.

Een gehost platform werkt anders. Bij Shopify draai je geen eigen PHP-server, dus deze serverkwetsbaarheid is niet iets dat jij op jouw shop moet patchen. Dat is het enige wat we over PHP2Shell en Shopify zeggen. Maar het is wel het bredere punt: je ruilt het serveronderhoud in voor een platform dat dat voor je draagt. Overweeg je die stap, dan helpen we met een [migratie van WooCommerce naar Shopify](https://www.joepify.nl/shopify-migratie/woocommerce) of een [migratie van Magento naar Shopify](https://www.joepify.nl/shopify-migratie/magento), met behoud van je producten, klanten en bestellingen.

## Hulp bij je webshop

Je hoeft dit niet alleen uit te zoeken. Zo pakken we het aan:

- **Gratis check:** je stuurt je websiteadres door, wij kijken welke PHP-versie je shop draait en wat er moet gebeuren.
- **Binnen 24 uur een vrijblijvend voorstel** met de stappen en de kosten.
- **Spoed:** is er iets misgegaan met je shop, dan is er spoedhulp vanaf 79 euro, met geen fix geen kosten.
- **Strategisch:** wil je van het serveronderhoud af, dan bekijken we samen of een [migratie naar Shopify](https://www.joepify.nl/shopify-migratie) bij je past.

---
Bron: [PHP2Shell en je webshop: WooCommerce en Magento](https://www.joepify.nl/blog/php2shell-webshop) · Licentie: CC BY 4.0, noem Joepify met een link naar de originele pagina.
