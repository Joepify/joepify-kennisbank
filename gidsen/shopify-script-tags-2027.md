---
title: "Shopify script tags stoppen op 1 maart 2027: wat nu?"
canonical: https://www.joepify.nl/kennisbank/shopify-script-tags-2027
updated: 2026-10-15
author: Ayoub Assaidi (Joepify)
license: CC BY 4.0
---

# Shopify script tags stoppen op 1 maart 2027: wat nu?

> Origineel en altijd actueel: https://www.joepify.nl/kennisbank/shopify-script-tags-2027  
> Bijgewerkt: 2026-10-15 · Auteur: Ayoub Assaidi, [Joepify](https://www.joepify.nl) (Rotterdam)

**Kort antwoord:** vanaf **1 maart 2027** laadt Shopify geen script tags meer in je online winkel. Apps die hun code nog op die oude manier in je winkel zetten, zoals sommige review-, pop-up-, A/B-test- en chatwidgets, werken dan niet meer. Je ziet zelf welke apps het zijn: zoek in de paginabron van je homepage naar `asyncLoad`. Vraag die apps of ze een app embed hebben, zet die aan en test het. Of vervang de app.

## Wat zijn script tags?

Een script tag is een oude manier waarop een Shopify-app JavaScript in je winkel laadt. De app registreert een scriptbestand en Shopify laadt dat op elke pagina. Jij ziet er in de thema-editor niets van. Dat is precies waarom Shopify ermee stopt: je hebt als winkeleigenaar geen zicht en geen controle op wat er draait.

De moderne vervangers zijn:

- **App embed blocks**, via een theme app extension. Die zet je zelf aan of uit in de thema-editor onder *App embeds*.
- **Web pixels**, voor analytics en conversiemeting. Die draaien in een afgeschermde sandbox.

## De tijdlijn

Shopify kondigde dit op 24 augustus 2026 aan in de [developer changelog](https://shopify.dev/changelog/posts/online-store-script-tags-deprecation):

- **1 oktober 2026:** apps kunnen geen nieuwe script tags meer aanmaken of bestaande wijzigen. Wat er al staat, draait nog wel.
- **1 maart 2027:** script tags werken helemaal niet meer in de online winkel.

Dit gaat over script tags met het bereik *online store*, dus je gewone winkelpagina's. De bedankpagina na de checkout had een eigen tijdlijn, die al voorbij is (26 augustus 2026 voor winkels zonder Plus). Daarover gaat [Shopify checkout extensibility en je tracking](https://www.joepify.nl/kennisbank/shopify-checkout-extensibility).

## Raakt het jouw winkel?

Grote kans van wel als je winkel al een paar jaar draait en apps gebruikt die je lang geleden installeerde. Nieuwe winkels met recente apps hebben er meestal geen last van. In de Shopify Community wordt er nog weinig over gesproken. De aankondiging stond in de developer changelog, niet in je admin.

### Zelf controleren in twee minuten

1. Open je winkel in Chrome, klik met rechts en kies **Paginabron weergeven**.
2. Zoek (Ctrl+F of Cmd+F) op `asyncLoad`.
3. Daaronder staat een regel `var urls = [ ... ]`. Elke URL in die lijst is een actieve script tag.
4. Kijk naar de domeinnamen in die URL's. Die vertellen meestal van welke app het script is.

Vind je geen `asyncLoad`, of is de lijst leeg, dan draaien er op dat moment geen script tags. Staan er wel URL's, schrijf dan per URL op welke app erbij hoort.

## Wat doe je per app?

Je hebt per app drie mogelijkheden:

1. **De app heeft al een app embed.** Update de app als dat nodig is, zet de embed aan via **Online Store > Thema's > Aanpassen > App embeds** en controleer of de widget dubbel verschijnt. Vraag de app-ontwikkelaar of het oude script daarna wordt verwijderd.
2. **De app heeft geen alternatief en wordt niet meer onderhouden.** Zoek een vervanger in de Shopify App Store. Let op: reviews en andere data moet je vaak exporteren en importeren.
3. **Je gebruikt de app niet meer.** Verwijder hem. Oude apps laten vaak code achter, dus kijk na het verwijderen opnieuw in de paginabron.

Mail de ontwikkelaar gerust zelf. Een korte vraag werkt: "Gebruikt jullie app op mijn winkel nog een ScriptTag, en wanneer stappen jullie over op een app embed?" Een serieuze ontwikkelaar weet hiervan, want sinds 1 oktober 2026 krijgen apps al foutmeldingen als ze nieuwe script tags proberen aan te maken.

## Waarom niet wachten tot februari?

- **Je ziet het niet als het stuk gaat.** Een reviewwidget die niet laadt, geeft geen foutmelding. Je productpagina mist alleen ineens de sterren, en je conversie daalt zonder duidelijke reden.
- **Data verhuizen kost tijd.** Overstappen naar een andere review- of loyaltyapp betekent exporteren, importeren en de opmaak opnieuw instellen.
- **Black Friday.** Je wilt geen apps vervangen vlak voor of tijdens je drukste periode. Plan het daarna, in december of januari.

## Wat het je ook oplevert

Opruimen heeft een prettige bijwerking. Script tags laden op elke pagina, ook van apps die je allang niet meer gebruikt. Minder losse scripts betekent vaak een snellere winkel. En met app embeds zie je voortaan zelf in de thema-editor wat er aan staat.

## Fouten die ik vaak tegenkom

- **Denken dat het alleen developers raakt**, omdat het in de developer changelog stond. Jij merkt het als winkelier, niet de app.
- **De app embed aanzetten terwijl het oude script nog draait.** Dan staat de widget twee keer op de pagina tot 1 maart.
- **Alleen de homepage bekijken.** De lijst in `asyncLoad` is op elke pagina hetzelfde, maar test na de overstap ook een productpagina en je winkelwagen.
- **Gewoon een app verwijderen** zonder te kijken of er reviews of klantdata in zaten die je wilt houden.

## Zo controleer je het

De gratis [website check](https://www.joepify.nl/website-apk) leest de script-tag-lijst van je winkel uit en zet de gevonden apps op een rij, zodat je niet zelf door de paginabron hoeft. Wil je dat ik de overstap regel, inclusief testen en opruimen? Dat valt onder [Shopify beheer](https://www.joepify.nl/shopify-beheer). Voor een snelle blik op je winkel is er ook de [Shopify winkel-check](https://www.joepify.nl/shopify-winkel-check).

## Wat de website APK hierbij checkt

Het onderdeel platform van de [website check](https://www.joepify.nl/website-apk#apk-modules) herkent een Shopify-winkel en leest de lijst met script-tag-URL's uit de openbare HTML van je homepage. Waar het domein bekend is, zie je de naam van de app erbij. De APK kan niet zien of een app al een app embed heeft of wanneer de ontwikkelaar overstapt; dat vraag je bij de app na.

- Gratis tool[Doe ook de gratis Shopify winkel check](https://www.joepify.nl/shopify-winkel-check)
- Liever uitbesteden[Laat je apps nalopen met Shopify beheer](https://www.joepify.nl/shopify-beheer)

---
Bron: [Shopify script tags stoppen op 1 maart 2027: wat nu?](https://www.joepify.nl/kennisbank/shopify-script-tags-2027) · Licentie: CC BY 4.0, noem Joepify met een link naar de originele pagina.
