---
title: "Wettelijke garantie webshop: de nieuwe EU-melding"
canonical: https://www.joepify.nl/kennisbank/garantiekennisgeving-webshop
updated: 2026-10-14
author: Ayoub Assaidi (Joepify)
license: CC BY 4.0
---

# Wettelijke garantie webshop: de nieuwe EU-melding

> Origineel en altijd actueel: https://www.joepify.nl/kennisbank/garantiekennisgeving-webshop  
> Bijgewerkt: 2026-10-14 · Auteur: Ayoub Assaidi, [Joepify](https://www.joepify.nl) (Rotterdam)

**Kort antwoord:** sinds 27 september 2026 moet iedereen die goederen verkoopt de Europese kennisgeving over de wettelijke garantie duidelijk tonen. Online betekent dat: de volledige kennisgeving in kleur, met een QR-code en een klikbare link, op een plek die je bezoeker niet mist, zoals de header, je productoverzicht of de checkout. Geeft de fabrikant van een product een gratis levensduurgarantie van meer dan twee jaar, dan moet je bij dat product ook het EU GARAN-label laten zien. Beide horen ook in je orderbevestiging.

## Wat is de garantiekennisgeving?

Het is een vaste afbeelding die de EU heeft ontworpen. Er staat in het kort op wat de wettelijke garantie is: als een product niet goed is, heeft de klant recht op herstel, vervanging, prijsverlaging of geld terug. De QR-code leidt naar de uitleg op Your Europe, in het Nederlands op [europa.eu/youreurope/garantie](https://europa.eu/youreurope/garantie).

De verplichting komt uit [Richtlijn (EU) 2024/825](https://eur-lex.europa.eu/eli/dir/2024/825/oj). Het ontwerp en de inhoud staan in [Uitvoeringsverordening (EU) 2025/1960](https://eur-lex.europa.eu/eli/reg_impl/2025/1960/oj). De Europese Commissie heeft [praktische richtlijnen en de bestanden](https://commission.europa.eu/publications/practical-guidelines-and-high-resolution-vector-files-eu-notice-and-label-product-guarantees_en) gepubliceerd, in 24 talen, als PDF, PNG, JPG en SVG.

Let op het verschil met wat veel webshops nu op hun site zetten, zoals "2 jaar garantie". In Nederland heeft de wettelijke garantie [geen vaste termijn](https://consument.acm.nl/garantie-reparatie-geld-terug/garantie): het gaat om hoe lang een klant mag verwachten dat een product meegaat. Gaat een product binnen een jaar kapot, dan gaat de wet ervan uit dat het al bij aflevering niet goed was en moet jij het tegendeel bewijzen, aldus de [ACM](https://consument.acm.nl/garantie-reparatie-geld-terug/bewijslast-bij-kapot-product). De kennisgeving maakt die rechten zichtbaar. Een tekst als "2 jaar garantie" naast de kennisgeving kan dus verwarrend zijn. Kijk die teksten meteen na.

## Voor wie geldt het?

Voor elke verkoper van goederen aan consumenten, online en in een fysieke winkel. De richtlijnen van de Commissie noemen geen uitzondering voor kleine bedrijven. Verkoop je alleen diensten of alleen aan bedrijven, dan geldt deze kennisgeving niet voor jou.

## Waar moet de kennisgeving op je webshop staan?

De regel is dat de kennisgeving "prominent" moet staan. De Commissie geeft in haar richtlijnen drie voorbeelden voor webshops. Je zet steeds een korte zin neer, zoals "Je wettelijke garantierechten", en bij de eerste klik of muisbeweging verschijnt de volledige kennisgeving:

- in de **header** van je website;
- op de **productoverzichtspagina** (je collectie of categorie);
- op de **checkoutpagina**.

Verder vraagt de Commissie om de kennisgeving ook in de **bevestigingsmail** op te nemen. Een paar regels voor de weergave: gebruik de kleurenversie (zwart-wit is alleen voor fysieke winkels), zorg dat hij leesbaar is op normale grootte, pas de kleuren en de QR-code niet aan en zet er altijd een klikbare link bij naar dezelfde pagina als de QR-code.

Thuiswinkel.org schrijft dat ze [met de ACM in gesprek is over de praktische invulling](https://www.thuiswinkel.org/kennisbank/kennisartikelen/nieuwe-eu-labels-voor-garanties-wat-moeten-webshops-vanaf-27-september-2026-doen/), onder meer of de kennisgeving ook verplicht in de checkout moet. Tot daar duidelijkheid over is, is de veilige keuze: header of productoverzicht, plus checkout, plus orderbevestiging.

## Het EU GARAN-label: alleen als de fabrikant het levert

Het GARAN-label is iets anders. Een fabrikant mag vrijwillig een commerciële duurzaamheidsgarantie geven: gratis, voor het hele product en langer dan twee jaar. Doet hij dat en geeft hij die informatie aan jou door, dan moet jij het label tonen bij dat specifieke product. Je hoeft er niet zelf naar te zoeken op sites van fabrikanten.

Volgens de Commissie hoort het label op de **productpagina** (in een productfoto, als losse afbeelding in de galerij, in de beschrijving of als klein "genest" label met het aantal jaren dat bij een klik uitklapt), **vlak voor het bestellen** in de checkout en in de **bevestigingsmail**. Alleen een algemene garantiepagina is niet genoeg, schrijft Thuiswinkel.

## Zo regel je het in Shopify

- Download de Nederlandse kleurenversie bij de Commissie en upload hem bij Content > Bestanden.
- Zet in je thema-editor een link "Je wettelijke garantierechten" in de aankondigingsbalk of header, die de afbeelding in een pop-up of op een eigen pagina toont, met de link naar Your Europe eronder.
- Voeg de afbeelding en de link toe aan de meldingssjabloon voor de orderbevestiging (Instellingen > Meldingen).
- Voor het GARAN-label: maak een productmetaveld, bijvoorbeeld "garan\_jaren", en laat je productsjabloon het label alleen tonen als dat veld gevuld is.
- Wat je in de checkout zelf kunt toevoegen, hangt af van je abonnement en je apps. Lukt het daar niet, zet het dan in elk geval op de winkelwagenpagina, vlak voor de checkout.

## Zo regel je het in WooCommerce

- Plaats de link in je header of bovenbalk via je thema of een blok in de site-editor.
- Toon de kennisgeving op de afrekenpagina, bijvoorbeeld als blok boven de knop "Bestelling plaatsen".
- Pas de e-mail "Verwerkte bestelling" aan (WooCommerce > Instellingen > E-mails) of gebruik een e-mailsjabloonplugin.
- Voor het GARAN-label: een eigen veld of attribuut per product, en een blok op de productpagina dat alleen verschijnt als het veld gevuld is.

## Zo controleer je het

Open je webshop op je telefoon en kijk of je zonder te zoeken bij de kennisgeving komt. Doe een testbestelling en kijk of hij in de bevestigingsmail staat. De [website check](https://www.joepify.nl/website-apk#apk-modules) zoekt op je webshop naar tekst over de wettelijke garantie of een GARAN-label en waarschuwt als hij niets vindt. Dat is een aanwijzing: of de kennisgeving ook in je orderbevestiging staat, kan de APK niet zien. Daarnaast kijkt het onderdeel wettelijke plichten naar je bedrijfsgegevens, je herroepingsknop en je cookiebanner. Wil je dat ik de kennisgeving en het GARAN-veld in je Shopify-thema inbouw, kijk dan bij [Shopify beheer](https://www.joepify.nl/shopify-beheer). Lees ook de guides over de [herroepingsknop](https://www.joepify.nl/kennisbank/herroepingsknop-webshop) en [GPSR op je productpagina](https://www.joepify.nl/kennisbank/gpsr-webshop).

Dit artikel is algemene informatie en geen juridisch advies. Twijfel je over jouw situatie, vraag het je branchevereniging of een jurist.

- Gratis tool[Heb je een Shopify-winkel? Doe ook de gratis Shopify winkel check](https://www.joepify.nl/shopify-winkel-check)
- Liever uitbesteden[Laat de kennisgeving plaatsen met Shopify beheer](https://www.joepify.nl/shopify-beheer)

---
Bron: [Wettelijke garantie webshop: de nieuwe EU-melding](https://www.joepify.nl/kennisbank/garantiekennisgeving-webshop) · Licentie: CC BY 4.0, noem Joepify met een link naar de originele pagina.
