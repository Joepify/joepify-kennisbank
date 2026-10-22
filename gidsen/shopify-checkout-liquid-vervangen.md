---
title: "Shopify checkout.liquid vervangen: wat moet nog?"
canonical: https://www.joepify.nl/kennisbank/shopify-checkout-liquid-vervangen
updated: 2026-10-15
author: Ayoub Assaidi (Joepify)
license: CC BY 4.0
---

# Shopify checkout.liquid vervangen: wat moet nog?

> Origineel en altijd actueel: https://www.joepify.nl/kennisbank/shopify-checkout-liquid-vervangen  
> Bijgewerkt: 2026-10-15 · Auteur: Ayoub Assaidi, [Joepify](https://www.joepify.nl) (Rotterdam)

**Kort antwoord:** de deadlines voor `checkout.liquid`, Additional scripts en de Thank you- en Order status-pagina's zijn voorbij: **28 augustus 2025** voor Shopify Plus en **26 augustus 2026** voor alle andere abonnementen. Ook Shopify Scripts is op **30 juni 2026** uitgezet. De enige harde datum die nog komt, is **1 maart 2027**, wanneer script tags in je hele winkel stoppen. Controleer dus nu wat je nog hebt overgezet, niet wat je moet gaan plannen.

## Wat is er al voorbij?

Ik zie veel winkeliers die denken dat dit nog moet komen. Op 15 oktober 2026 is dit de stand volgens Shopify:

- **Informatie-, verzend- en betaalstap met `checkout.liquid`:** volgens [Shopify.dev](https://shopify.dev/docs/storefronts/themes/architecture/layouts/checkout-liquid) "now unsupported". Maatwerk daar loopt via checkout extensions.
- **Thank you- en Order status-pagina, Additional scripts en script tags op die pagina's:** Plus op 28 augustus 2025, niet-Plus op 26 augustus 2026.
- **Shopify Scripts** (kortingen, verzend- en betaalregels voor Plus): sinds [30 juni 2026](https://help.shopify.com/en/manual/checkout-settings/script-editor/migrate-to-functions) gedeactiveerd. Wat nog gepubliceerd stond, werkt niet meer. De vervanger heet Shopify Functions.

## Wat is er nog open?

Eén datum: op **1 maart 2027** stopt Shopify met het inladen van script tags in je storefront, volgens de [changelog](https://shopify.dev/changelog/posts/online-store-script-tags-deprecation). Dat raakt apps die nog zo werken, zoals oudere review-, pop-up- en chatwidgets. Het vervolg staat in [Shopify script tags stoppen op 1 maart 2027](https://www.joepify.nl/kennisbank/shopify-script-tags-2027).

De rest is geen datum maar opruimwerk: wat jij hebt overgezet, werkt het ook echt, en is er niets stilletjes uitgevallen?

## Verschil tussen Plus en niet-Plus

- **Niet-Plus (Basic, Grow, Advanced):** je kon de bedankpagina en de accountpagina's met het checkout- en accounteditor aanpassen. Alleen bij Plus kunnen apps ook de informatie-, verzend- en betaalpagina's aanpassen, en alleen Plus heeft de Checkout Branding API.
- **Plus:** je hebt ook te maken gehad met Shopify Scripts. Die zijn vervangen door Functions.

Wat Shopify per abonnement precies toestaat, kan wijzigen. Het overzicht staat in het [Shopify Help Center](https://help.shopify.com/en/manual/checkout-settings/customize-checkout-configurations/upgrade-guide).

## Stap 1: kijk of je winkel is overgezet

Ga naar **Instellingen > Checkout** en bekijk het kopje Configuraties. Volgens het [Help Center](https://help.shopify.com/en/manual/checkout-settings/checkout-extensibility/checkout-upgrade) zie je daar een upgrademelding als je nog een verouderde versie gebruikt. Let op: pauzeer je je winkel, dan wordt de upgrade automatisch en definitief doorgevoerd.

## Stap 2: ga na wat er vervangen is

Per oud onderdeel is de officiële vervanger:

- **Vrije HTML in de bedankpagina:** blokken in de checkout- en accounteditor.
- **Tracking in Additional scripts:** app pixels of een custom pixel. Het hele herstelplan staat in [Shopify checkout extensibility: tracking herstellen](https://www.joepify.nl/kennisbank/shopify-checkout-extensibility).
- **Shopify Scripts (Plus):** Shopify Functions.
- **Script tags in de rest van de winkel:** app embed blocks of web pixels, vóór 1 maart 2027.

## Stap 3: test met een echte bestelling

Plaats een kleine testbestelling. Controleer dat korting, verzendkosten en betaalmethodes kloppen, dat de bedankpagina de goede inhoud toont en dat je aankoop één keer in je advertentie- en analyticstools verschijnt. Annuleer en restitueer daarna.

## Fouten die ik vaak tegenkom

- Aannemen dat "mijn winkel draait gewoon" betekent dat alles is overgezet. Het gaat vaak om stille uitval: tracking, kortingsregels, een klantreview-verzoek.
- Oude code in Additional scripts laten staan en denken dat die nog draait.
- Plus-winkeliers die Scripts niet hebben vervangen en nu geen kortingsregels meer hebben.
- Alleen de bedankpagina nalopen en script tags voor 1 maart 2027 vergeten.

## Zo controleer je het

Doe de gratis [Shopify winkel check](https://www.joepify.nl/shopify-winkel-check). Die kijkt van buitenaf naar je winkel en laat zien wat verouderd is. Een testbestelling plaats hij niet, dus stap 3 blijft van jou. De [website check](https://www.joepify.nl/website-apk#apk-modules) kijkt in de openbare HTML welke tracking in je thema staat en welke pixels Shopify meldt.

- Gratis tool[Doe de gratis Shopify winkel check](https://www.joepify.nl/shopify-winkel-check)
- Liever uitbesteden[Laat Joepify dit doen: checkout en apps nalopen met Shopify beheer](https://www.joepify.nl/shopify-beheer)

---
Bron: [Shopify checkout.liquid vervangen: wat moet nog?](https://www.joepify.nl/kennisbank/shopify-checkout-liquid-vervangen) · Licentie: CC BY 4.0, noem Joepify met een link naar de originele pagina.
