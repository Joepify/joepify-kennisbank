---
title: "WooCommerce sneller maken: oorzaken en oplossingen"
canonical: https://www.joepify.nl/blog/woocommerce-sneller-maken
updated: 2026-10-16
author: Ayoub Assaidi (Joepify)
license: CC BY 4.0
---

# WooCommerce sneller maken: oorzaken en oplossingen

> Origineel en altijd actueel: https://www.joepify.nl/blog/woocommerce-sneller-maken  
> Bijgewerkt: 2026-10-16 · Auteur: Ayoub Assaidi, [Joepify](https://www.joepify.nl) (Rotterdam)

In het kort

Om WooCommerce sneller te maken meet u eerst de oorzaak. Meestal is dat te zwakke hosting, zware plugins, een opgezwollen database of afrekenpagina's die niet uit de cache kunnen komen.

- **Snelle winst:** afbeeldingen verkleinen, ongebruikte plugins verwijderen, caching goed instellen en PHP bijwerken.
- **Structureel:** hosting voor webshops met object caching, de database opschonen en cron op serverniveau.
- **Volgende stap:** binnen 24 uur een voorstel met een vaste prijs vooraf.

Wilt u **WooCommerce sneller maken**, begin dan niet bij een cachingplugin maar bij het meten van de oorzaak. In vrijwel alle trage shops zit de vertraging in een combinatie van te zwakke hosting, te veel of te zware plugins, een opgezwollen database en winkelwagen- of afrekenpagina's die niet uit de cache kunnen komen. Dit artikel laat zien hoe u dat zelf kunt vaststellen, wat u direct kunt verbeteren en wanneer het slimmer is om structureel te verhuizen.

## Waarom WooCommerce vanzelf trager wordt

WooCommerce is een plugin bovenop WordPress. Dat is een groot voordeel, want u kunt bijna alles aanpassen. Het nadeel is dat elke pagina in een webshop meer werk vraagt dan een gewone informatieve pagina. Prijzen, voorraad, verzendkosten, kortingen en de inhoud van de winkelwagen worden per bezoeker berekend. Een brochuresite kan een pagina één keer opbouwen en daarna honderden keren tonen. Een webshop kan dat maar gedeeltelijk.

Daarbij komt dat een shop in de loop van de tijd groeit. Er komen producten bij, bestellingen stapelen zich op, er wordt een plugin voor een actie geïnstalleerd en een andere voor een koppeling met de boekhouding. Elk onderdeel is op zichzelf redelijk, maar samen maken ze de shop zwaarder. Een shop die bij de oplevering snel was, kan na twee jaar zonder onderhoud merkbaar trager zijn.

De meest voorkomende oorzaken, grofweg in volgorde van hoe vaak wij ze tegenkomen:

- Hosting die voor een gewone website is bedoeld, niet voor een webshop met actieve bezoekers.
- Te veel plugins, of een paar plugins die bij elke paginalading zware taken uitvoeren.
- Een database vol oude gegevens zoals revisies, verlopen sessies en logbestanden.
- Afbeeldingen die veel te groot zijn voor de plek waar ze getoond worden.
- Pagina's die niet gecachet worden, of juist pagina's die verkeerd gecachet worden.
- Geplande taken (cron) die vastlopen of zich opstapelen.

Het loont om dit in deze volgorde na te lopen, want de eerste punten leveren meestal het meeste op.

### Eerst meten, dan pas aanpassen

Gokken kost tijd en geld. Meet daarom eerst een paar vaste pagina's: de homepage, een categoriepagina, een productpagina, de winkelwagen en de afrekenpagina. Gebruik hiervoor een gratis tool zoals PageSpeed Insights en let op twee dingen: hoe lang de server nodig heeft om te antwoorden (de eerste reactie) en hoe lang het duurt voordat de pagina zichtbaar en bruikbaar is. Is al de eerste reactie van de server traag, dan zit het probleem in hosting, plugins of database. Komt de server snel terug maar voelt de pagina toch traag, dan zijn het meestal afbeeldingen, lettertypen en scripts.

Meet ook op een telefoon met een gewone mobiele verbinding. De meeste bezoekers komen via de telefoon en daar merkt u een trage shop het eerst.

## Hosting: de basis waar alles op rust

Goedkope gedeelde hosting is de meest voorkomende reden dat een WooCommerce-shop traag is. Op zo'n server delen tientallen of honderden websites dezelfde processorkracht en hetzelfde geheugen. Zodra een andere site op die server drukte krijgt, merkt uw shop dat. En een webshop vraagt per bezoeker meer rekenwerk dan een gewone website.

Waar u op let bij hosting voor een webshop:

- **Actuele PHP-versie.** Nieuwere PHP-versies zijn merkbaar sneller dan oude. Draait uw shop nog op een verouderde versie, dan is dit de goedkoopste winst, mits uw plugins en thema compatibel zijn. Test dat eerst op een kopie.
- **Voldoende geheugen en processorkracht** die niet met honderden andere sites gedeeld worden.
- **Snelle opslag** en een server in Nederland of de EU als uw klanten daar zitten.
- **Serverside caching** en een object cache, zodat veelgebruikte databasegegevens niet telkens opnieuw worden opgehaald.
- **Een omgeving om te testen**, zodat u wijzigingen niet op de live shop uitprobeert.

Een lastige maar belangrijke vraag is of de trage shop echt een hostingprobleem heeft of een softwareprobleem. Als de shop 's nachts snel is en overdag traag, wijst dat op een tekort aan serverkracht. Als hij altijd traag is, ook als er niemand op zit, ligt de oorzaak vaker in plugins of database. Een nieuwe, betere server lost een softwareprobleem alleen tijdelijk op: u betaalt dan meer voor hetzelfde probleem.

Hoe hosting bij ons werkt en wat zakelijke hosting inhoudt, leest u in ons artikel over [zakelijke hosting in Nederland](https://www.joepify.nl/blog/zakelijke-hosting-nederland).

## Plugins en thema: minder is bijna altijd sneller

Het aantal plugins zegt minder dan wat ze doen. Vijf lichte plugins kunnen sneller zijn dan één zware. Toch is het een goede vuistregel dat elke plugin een reden moet hebben. Staat er een plugin op die niemand meer gebruikt, dan hoort die weg.

Zo gaat u systematisch te werk:

1. Maak een lijst van alle actieve plugins en zet erbij waarvoor ze dienen en wie ze gebruikt.
2. Verwijder plugins die niet meer nodig zijn. Deactiveren is niet genoeg, ook ongebruikte plugins moeten bijgewerkt worden en vormen een beveiligingsrisico.
3. Zoek naar plugins met dubbele functies, bijvoorbeeld twee plugins voor beveiliging of twee voor cachen.
4. Test op een kopie van de shop wat er gebeurt als u een verdachte plugin uitzet. Zakt de laadtijd flink, dan weet u genoeg.
5. Vervang zware plugins door een lichter alternatief of door een kleine aanpassing op maat.

Veelvoorkomende boosdoeners zijn paginabouwers die veel extra code laden op elke pagina, plugins voor sliders en pop-ups, statistiekplugins die elk bezoek in de eigen database schrijven, en plugins voor gerelateerde producten die bij elke paginalading grote zoekopdrachten uitvoeren. Ook een thema met veel ingebouwde functies kan de shop vertragen als u maar een klein deel ervan gebruikt.

Let ook op scripts van buitenaf: chatwidgets, advertentiepixels, reviewwidgets en lettertypen die van externe servers komen. Elk daarvan voegt een extra verzoek toe. Vraag uzelf bij elk script af of het geld oplevert. Zo niet, dan kan het weg.

## Database en cron: de verborgen vertragers

De database van WooCommerce groeit mee met uw shop. Dat is normaal, maar sommige onderdelen groeien zonder dat iemand het merkt.

### Wat zich ophoopt in de database

- **Berichtrevisies:** WordPress bewaart standaard elke opgeslagen versie van een product of pagina.
- **Verlopen sessies en tijdelijke gegevens** (transients) van plugins die nooit worden opgeruimd.
- **Logbestanden** van plugins, betaalmodules en e-mailmodules.
- **Oude concept-bestellingen** en mislukte betalingen.
- **Verweesde gegevens** van plugins die lang geleden zijn verwijderd.
- **De opties-tabel** die bij elke paginalading wordt ingelezen en door oude plugins vol kan staan met gegevens die automatisch worden geladen.

Maak altijd eerst een volledige back-up en doe het liefst eerst een proef op een kopie. Verwijder niet blind alles wat een opruimplugin voorstelt. Een goed onderhouden database is vaak kleiner, sneller te doorzoeken en sneller te back-uppen.

### Geplande taken (cron)

WordPress voert geplande taken uit via een eigen systeem: het wp-cron. Dat wordt standaard wakker gemaakt door bezoekers. In een drukke shop betekent dat dat een bezoeker soms net die taak triggert en daardoor een trage pagina krijgt. Zijn er veel taken opgestapeld, bijvoorbeeld mails, synchronisaties of voorraadupdates, dan loopt het systeem vast of gaat het steeds opnieuw proberen.

De structurele oplossing is om cron los te koppelen van bezoekers en door de server op vaste tijden te laten uitvoeren. Controleer daarnaast of er taken tussen zitten die falen en zichzelf blijven herhalen. Dat ziet u in het takenoverzicht van WordPress en in de logboeken van de shop.

## Afbeeldingen en caching: waar de meeste winst zit

Afbeeldingen zijn in een webshop bijna altijd het grootste deel van een pagina. Een productfoto rechtstreeks van een telefoon of fotograaf kan enkele megabytes groot zijn, terwijl een webshop er op het scherm maar een paar honderd pixels van toont.

### Afbeeldingen goed instellen

- Gebruik een moderne bestandsindeling zoals WebP of AVIF, die kleiner is bij gelijke kwaliteit.
- Upload geen foto's die groter zijn dan nodig. Een breedte van 1.600 tot 2.000 pixels is voor de meeste productfoto's ruim voldoende.
- Laat afbeeldingen onder het scherm pas laden als de bezoeker erheen scrolt (lazy loading), maar laad de grote afbeelding bovenaan de pagina juist meteen.
- Geef elke afbeelding vaste afmetingen, zodat de pagina niet verspringt tijdens het laden.
- Controleer of alle formaten die WooCommerce automatisch maakt ook echt gebruikt worden. Overbodige formaten kosten opslagruimte en uploadtijd.

### Caching: wat wel en niet

Caching betekent dat een kant-en-klare versie van een pagina wordt getoond in plaats van dat die opnieuw wordt opgebouwd. Voor categoriepagina's, productpagina's en informatieve pagina's werkt dat uitstekend. Maar niet alles mag in de cache.

Dit mag **niet** gecachet worden:

- De winkelwagen.
- De afrekenpagina.
- Het account van de klant en de bestelhistorie.
- Pagina's met persoonlijke inhoud of een persoonlijke prijs.

Een veelgemaakte fout is een cachingplugin die deze pagina's per ongeluk wel bewaart. Het gevolg is dat klanten de winkelwagen van iemand anders zien of dat een product niet in de winkelwagen verschijnt. Goede cachingplugins sluiten deze pagina's standaard uit, maar controleer het altijd door zelf een bestelling te plaatsen met een gewoon en een privévenster.

Omdat winkelwagen en afrekenen niet gecachet kunnen worden, zijn ze de zwakste plek van een WooCommerce-shop. Daar gaat het dus om efficiënte code, een snelle server en weinig plugins die zich in het afrekenproces mengen. Wie hier tijd in steekt, merkt het direct in het aantal afgebroken bestellingen.

## Snelle winst versus structurele oplossingen

Niet elke verbetering kost evenveel moeite en niet elke verbetering blijft werken. Dit onderscheid helpt u bepalen waar u begint.

### Snelle winst, vaak binnen een dag te regelen

- Afbeeldingen verkleinen en omzetten naar een moderne indeling.
- Ongebruikte plugins verwijderen en overbodige scripts van buitenaf uitzetten.
- Een goede cachingplugin instellen, met winkelwagen en afrekenpagina uitgesloten.
- PHP bijwerken naar een ondersteunde versie, na een test op een kopie.
- WordPress, WooCommerce, thema en plugins bijwerken.

### Structurele oplossingen, meer werk maar duurzaam

- Overstappen naar hosting die voor webshops is ingericht, met object caching.
- De database opschonen en lange, trage queries laten analyseren.
- Zware plugins vervangen door lichte maatwerkcode.
- Cron op serverniveau laten draaien.
- Een staging-omgeving en vast onderhoud, zodat de shop niet opnieuw langzaam wordt.

Het laatste punt wordt vaak vergeten. Een shop die eenmalig wordt versneld, maar daarna niet wordt onderhouden, is na een jaar weer trager. Updates, controles op trage plugins en regelmatig opschonen horen bij een gezonde shop. Daarom bieden wij dit aan als onderdeel van [WordPress-onderhoud](https://www.joepify.nl/wordpress-onderhoud).

Wilt u eerst weten waar u staat? Een [website check](https://www.joepify.nl/website-apk) geeft een overzicht van snelheid, beveiliging, updates en technische gezondheid, met een lijst van wat als eerste moet gebeuren.

## Wanneer beter hosten, wanneer opschonen en wanneer naar Shopify?

Soms is de eerlijke conclusie dat versnellen niet de beste route is. Dit zijn de afwegingen die wij met ondernemers doorlopen.

### Blijf op WooCommerce en verbeter de basis als

- uw shop veel maatwerk bevat dat u niet kwijt wilt, zoals eigen prijsregels, koppelingen of een bijzondere checkout;
- u de volledige controle over uw data en uw omgeving wilt houden;
- de trage shop een duidelijke oorzaak heeft die oplosbaar is, zoals verouderde hosting of een paar zware plugins.

In dat geval is een goede hostingomgeving, een opgeschoonde installatie en vast onderhoud meestal voldoende. Wilt u een nieuwe shop op deze basis, kijk dan naar onze aanpak voor het [laten maken van een WooCommerce-webshop](https://www.joepify.nl/woocommerce-webshop-laten-maken).

### Overweeg Shopify als

- u weinig tijd hebt voor technisch beheer en liever geen eigen server en updates wilt;
- uw catalogus groot is of snel groeit en de shop bij drukte blijft haperen;
- u veel pieken hebt, bijvoorbeeld door acties of seizoenen;
- u uw plugins steeds opnieuw moet bijwerken en dat steeds meer tijd kost.

Bij Shopify zijn hosting, beveiliging en snelheid van het platform onderdeel van het abonnement. Daar staat tegenover dat u minder vrijheid hebt op het gebied van diepe aanpassing en dat u de kosten per maand en per app moet afwegen. Een eerlijke vergelijking vindt u in ons artikel [Shopify of WooCommerce](https://www.joepify.nl/blog/shopify-vs-woocommerce). Ervaring met een grote overstap hebben wij onder meer opgedaan bij Sneakers Enzo, waar wij een Magento-shop met meer dan 5.000 producten naar Shopify hebben gebracht.

Besluit u te verhuizen, dan is een zorgvuldige migratie van producten, klanten, bestellingen en URL's belangrijk, zodat u geen positie in Google verliest. Hoe dat werkt, staat op onze pagina over [Shopify-migratie](https://www.joepify.nl/shopify-migratie).

Een nuchtere vuistregel: lost een paar uur gericht werk het probleem op, ga dan niet verhuizen. Zit het probleem diep in de opbouw, de plugins en het onderhoud, en kost verbeteren steeds meer dan het oplevert, dan is een overstap het overwegen waard.

## Hoe Joepify uw WooCommerce-shop sneller maakt

Joepify is een webbureau uit Rotterdam. U werkt direct met een senior developer, geen tussenlaag van accountmanagers. Wij beoordelen uw shop eerst, voordat wij iets voorstellen.

1. **Meten:** wij testen de belangrijkste pagina's en kijken naar server, plugins, database en cron.
2. **Voorstel binnen 24 uur:** u krijgt een duidelijke lijst van wat wij aanpakken, in welke volgorde en wat het oplevert, tegen een vaste prijs vooraf.
3. **Uitvoeren op een kopie:** wij testen eerst op een staging-omgeving en zetten wijzigingen pas live als alles werkt, inclusief een testbestelling.
4. **Vast onderhoud:** updates, back-ups en controles, zodat de shop snel blijft.

Wij bouwen en onderhouden WooCommerce-shops, zoals voor Holland Machinery, een machinehandelaar waarvoor wij WordPress en WooCommerce beheren en beveiligen. En als verhuizen de betere keuze blijkt, zeggen wij dat ook eerlijk, omdat wij ook Shopify bouwen.

Stuur ons de link naar uw shop via het formulier hieronder, of bel of app naar 06 87 19 50 43. U hoort binnen 24 uur wat wij zien en wat wij aanraden.

---
Bron: [WooCommerce sneller maken: oorzaken en oplossingen](https://www.joepify.nl/blog/woocommerce-sneller-maken) · Licentie: CC BY 4.0, noem Joepify met een link naar de originele pagina.
