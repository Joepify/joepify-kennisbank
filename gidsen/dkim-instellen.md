---
title: "DKIM instellen en checken: zo werkt het"
canonical: https://www.joepify.nl/kennisbank/dkim-instellen
updated: 2026-10-14
author: Ayoub Assaidi (Joepify)
license: CC BY 4.0
---

# DKIM instellen en checken: zo werkt het

> Origineel en altijd actueel: https://www.joepify.nl/kennisbank/dkim-instellen  
> Bijgewerkt: 2026-10-14 · Auteur: Ayoub Assaidi, [Joepify](https://www.joepify.nl) (Rotterdam)

**Kort antwoord:** DKIM zet een digitale handtekening op elke mail die je verstuurt. De ontvanger controleert die handtekening met een publieke sleutel in de DNS van je domein, op de naam `selector._domainkey.jouwdomein.nl`. Je stelt DKIM in per dienst die namens jou mailt: bij Microsoft 365 met twee CNAME-records, bij Google Workspace met één TXT-record, bij je hosting vaak met één klik in het mailpaneel. Daarna doe je een DKIM check, bijvoorbeeld met de gratis [e-mail check](https://www.joepify.nl/email-check), en kijk je in een ontvangen mail of er `dkim=pass` staat.

## Wat doet DKIM precies?

DKIM staat voor DomainKeys Identified Mail en is vastgelegd in [RFC 6376](https://www.rfc-editor.org/rfc/rfc6376.html). Je mailserver tekent elke uitgaande mail met een geheime sleutel. In de mail komt een kopregel `DKIM-Signature` met onder meer twee waarden:

- **d=** het domein dat voor de mail tekent, bijvoorbeeld `jouwdomein.nl`;
- **s=** de selector, de naam van de sleutel, bijvoorbeeld `google` of `selector1`.

De ontvanger plakt die twee aan elkaar en zoekt de publieke sleutel op in DNS. Bij `s=google` en `d=jouwdomein.nl` is dat `google._domainkey.jouwdomein.nl`. Klopt de handtekening, dan weet de ontvanger dat de mail echt van dat domein komt en onderweg niet is aangepast.

Een domein kan meerdere DKIM-sleutels hebben, één per selector. Zo kunnen je mailbox, je nieuwsbrief en je webshop elk hun eigen sleutel gebruiken zonder elkaar in de weg te zitten. Dat is een belangrijk verschil met SPF, waar je maar één record mag hebben.

## Waarom DKIM instellen?

Gmail eist sinds 1 februari 2024 dat [iedereen die mailt minstens SPF of DKIM heeft](https://support.google.com/a/answer/81126?hl=nl). Wie meer dan 5.000 mails per dag naar Gmail stuurt, heeft SPF, DKIM en [DMARC](https://www.joepify.nl/onderzoek-webshops-2026) nodig. Google schrijft er ook bij dat je DKIM-sleutel minstens 1024 bits moet zijn en raadt 2048 bits aan als je DNS-provider dat ondersteunt.

Daarnaast is DKIM de sterkste basis voor DMARC. Een doorgestuurde mail faalt vaak op SPF, omdat hij dan via een andere server gaat. De DKIM-handtekening zit in de mail zelf en blijft meestal gewoon geldig. In Nederland is DKIM voor de overheid verplicht via de lijst ['pas toe of leg uit' van het Forum Standaardisatie](https://www.forumstandaardisatie.nl/open-standaarden/dkim). Voor andere organisaties is het daar aanbevolen.

## DKIM instellen per dienst

Begin met een lijstje van alles wat namens jouw domein mailt: je mailbox, je website of webshop, je nieuwsbrief en je boekhoudpakket. Elke dienst tekent met zijn eigen sleutel, dus elke dienst heeft zijn eigen DKIM-record nodig. Wil je je nieuwsbrief liever helemaal niet zelf regelen, dan kun je ook [e-mailmarketing uitbesteden](https://www.joepify.nl/blog/email-marketing-uitbesteden).

### Microsoft 365

Voor je eigen domein tekent Microsoft 365 pas met DKIM als je het zelf aanzet. Je maakt twee CNAME-records aan, `selector1._domainkey` en `selector2._domainkey`. De waarden verschillen per organisatie. Bij domeinen die je sinds mei 2025 toevoegt eindigen ze op `dkim.mail.microsoft`, bij oudere domeinen op `onmicrosoft.com`. Neem ze dus over uit je eigen omgeving en niet uit een voorbeeld.

Volgens de [documentatie van Microsoft](https://learn.microsoft.com/en-us/defender-office-365/email-authentication-dkim-configure) vind je ze in de Defender-portal onder **Email & collaboration > Policies & rules > Threat policies > Email authentication settings**, tabblad DKIM. Klik op je domein, zet de CNAME-records in je DNS en zet daarna de schakelaar op Enabled. Microsoft gebruikt er twee zodat de sleutel later kan wisselen. Draai je de sleutels om, dan duurt het vier dagen voordat de nieuwe sleutel tekent.

### Google Workspace

In de Google-beheerconsole ga je naar **Apps > Google Workspace > Gmail > E-mail verifiëren**. Daar [maak je een sleutel aan](https://support.google.com/a/answer/174124?hl=nl) met **Nieuwe record maken**. Kies 2048 bits, tenzij je DNS-provider dat niet aankan, en laat de standaardselector `google` staan. Je krijgt een TXT-record voor `google._domainkey`. Zet dat in je DNS en klik daarna in de beheerconsole op **Verificatie starten**. Google waarschuwt dat het tot 48 uur kan duren voordat DKIM werkt.

### Mail via je hosting (DirectAdmin of cPanel)

Draait je mail bij je hostingpartij, dan zet je DKIM daar aan. In DirectAdmin is dat **Email Accounts > Enable DKIM**, op servers waar de beheerder die functie heeft vrijgegeven. In cPanel heet het [Email Deliverability](https://docs.cpanel.net/cpanel/email/email-deliverability-in-cpanel/): daar zie je per domein of DKIM goed staat, met een knop Repair of Manage.

Let op als je DNS ergens anders zit dan je hosting, bijvoorbeeld bij je registrar of Cloudflare. Het paneel zet het record dan alleen in de lokale DNS, die niemand leest. Je moet het record zelf overnemen bij de partij waar je DNS echt draait. [DirectAdmin schrijft](https://docs.directadmin.com/other-hosting-services/exim/) dat mail anders wel getekend wordt maar de controle faalt, en noemt dat erger dan helemaal geen DKIM.

### Nieuwsbrief, webshop en andere diensten

Mailchimp, Klaviyo, Brevo en Shopify Email vragen je om je domein te verifiëren of te authenticeren. Je krijgt dan een paar CNAME- of TXT-records met hun eigen selector. Zonder die stap tekenen ze met hun eigen domein en sluit de mail niet aan op je DMARC. WordPress en WooCommerce mailen standaard via de webserver, vaak zonder DKIM. Een SMTP-plugin die via je mailbox of een maildienst verstuurt, lost dat op.

## Zo controleer je het: de DKIM check

**1. Doe een DKIM check op je domein.** De gratis [e-mail check](https://www.joepify.nl/email-check) probeert de selectors die Microsoft 365, Google Workspace en de meeste hostingpartijen gebruiken, en laat zien hoe sterk je sleutel is. Je ziet in één keer ook je SPF en DMARC. Het onderdeel e-mail van de [website check](https://www.joepify.nl/website-apk#apk-modules) doet hetzelfde als deel van een volledige keuring.

**2. Kijk in een echte mail.** Stuur een mail naar een Gmail-adres, open hem en kies **Meer > Origineel tonen** ([uitleg van Google](https://support.google.com/mail/answer/29436?hl=nl)). Bij DKIM moet PASS staan, met jouw domein erachter. In de volledige kopregels zie je iets als:

`dkim=pass header.d=jouwdomein.nl header.s=selector1`
Staat er een ander domein achter `header.d`, dan tekent de dienst nog met zijn eigen domein.

**3. Zoek het record zelf op.** Weet je de selector, dan zie je de sleutel met:

`nslookup -type=TXT google._domainkey.jouwdomein.nl`
Bij Microsoft 365 krijg je eerst de CNAME te zien.

Eén eerlijke kanttekening: geen enkele DKIM check kan een selector raden die een dienst zelf verzint. Meldt een check "niet gevonden" terwijl stap 2 PASS geeft, dan staat DKIM gewoon goed onder een andere naam.

## Veelgemaakte fouten

- **DKIM staat klaar maar is niet aangezet.** Bij Microsoft 365 en Google Workspace is het record alleen niet genoeg: je moet in het beheerpaneel ook op aanzetten of verificatie starten klikken.
- **Het record staat op de verkeerde plek.** Veel panelen plakken je domeinnaam er zelf achter. Typ je `google._domainkey.jouwdomein.nl`, dan staat het record daarna op die naam met je domein er nog een keer achter. Vul dan alleen `google._domainkey` in.
- **Een lange sleutel is afgekapt.** Een 2048-bits sleutel is langer dan 255 tekens. Sommige DNS-panelen knippen hem dan af of willen hem in stukken. Controleer na het opslaan of de hele sleutel er staat.
- **Testmodus blijft aan.** Staat er `t=y` in het record, dan behandelen ontvangers je mail volgens RFC 6376 alsof hij niet getekend is.
- **Een lege sleutel.** `p=` zonder waarde betekent dat de sleutel is ingetrokken. Dat zie je soms na een verhuizing naar een andere mailprovider.
- **Een te korte sleutel.** Volgens [RFC 8301](https://www.rfc-editor.org/rfc/rfc8301.html) moet een sleutel minstens 1024 bits zijn en hoort hij 2048 bits te zijn. Kun je kiezen, kies dan 2048.
- **DNS bij een andere partij** dan je hosting, waardoor het record nooit live komt. Zie het stuk over DirectAdmin en cPanel hierboven.

## Na DKIM: SPF en DMARC

DKIM werkt het best samen met de andere twee. Met een [SPF record](https://www.joepify.nl/kennisbank/spf-record-instellen) geef je aan welke servers namens je domein mogen mailen. Met [DMARC](https://www.joepify.nl/kennisbank/dmarc-instellen) vertel je ontvangers wat ze moeten doen met mail die niet klopt, en krijg je rapporten over wie er namens jou mailt. In die rapporten zie je ook snel welke dienst nog niet met DKIM tekent. Wil je alle drie in één keer laten nalopen, doe dan de [e-mail check](https://www.joepify.nl/email-check).

- Gratis tool[Doe een DKIM check met de gratis e-mail check](https://www.joepify.nl/email-check)
- Liever uitbesteden[Mailt je WordPress-site niet goed? Bekijk WordPress onderhoud](https://www.joepify.nl/wordpress-onderhoud)

---
Bron: [DKIM instellen en checken: zo werkt het](https://www.joepify.nl/kennisbank/dkim-instellen) · Licentie: CC BY 4.0, noem Joepify met een link naar de originele pagina.
