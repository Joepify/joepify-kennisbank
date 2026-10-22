---
title: "DMARC instellen in 3 stappen (Microsoft 365, Google)"
canonical: https://www.joepify.nl/kennisbank/dmarc-instellen
updated: 2026-10-22
author: Ayoub Assaidi (Joepify)
license: CC BY 4.0
---

# DMARC instellen in 3 stappen (Microsoft 365, Google)

> Origineel en altijd actueel: https://www.joepify.nl/kennisbank/dmarc-instellen  
> Bijgewerkt: 2026-10-22 · Auteur: Ayoub Assaidi, [Joepify](https://www.joepify.nl) (Rotterdam)

**Kort antwoord:** DMARC stel je in met één TXT-record in de DNS van je domein, op de naam `_dmarc`. Begin met `v=DMARC1; p=none; rua=mailto:jouw-adres`, zodat je eerst alleen meekijkt. Zorg dat SPF en [DKIM](https://www.joepify.nl/kennisbank/dkim-instellen) kloppen voor alles wat namens jou mailt (je mailbox, je webshop, je nieuwsbrief). Werkt dat een paar weken goed, zet het beleid dan op `quarantine` en later op `reject`. DMARC is vastgelegd in RFC 9989 uit 2026, de opvolger van RFC 7489, en volgens het NCSC hoort DMARC op elk domein.

## Waarom DMARC?

DMARC is de instelling die voorkomt dat iedereen mail kan sturen die van jouw adres lijkt te komen. Zonder DMARC gebruiken oplichters je domein makkelijk voor valse facturen en phishing. Tegelijk zijn Gmail, Yahoo en Microsoft strenger geworden: Google eist sinds 2024 [SPF of DKIM voor alle verzenders en DMARC voor grote verzenders](https://support.google.com/a/answer/81126?hl=nl), en Outlook.com weigert sinds 5 mei 2025 mail van [grote verzenders die niet voldoen](https://techcommunity.microsoft.com/blog/microsoftdefenderforoffice365blog/strengthening-email-ecosystem-outlook%E2%80%99s-new-requirements-for-high%E2%80%90volume-senders/4399730). Stuur je als kleine ondernemer geen 5.000 mails per dag, dan raakt die harde grens je niet direct. Maar een goed ingesteld domein komt wel vaker in de inbox. Het [NCSC adviseert](https://www.ncsc.nl/phishing/bescherm-domeinnamen-tegen-phishing) SPF, DKIM en DMARC voor elk domein.

## Hoe hangen SPF, DKIM en DMARC samen?

SPF, DKIM en DMARC zijn drie DNS-records die samen bepalen of een ontvanger jouw mail vertrouwt:

- **SPF** is een lijst van servers die namens jouw domein mogen mailen.
- **DKIM** is een digitale handtekening op elke mail, die de ontvanger met een sleutel in jouw DNS controleert.
- **DMARC** vertelt ontvangers wat ze moeten doen als een mail niet door SPF of DKIM komt (of als het domein niet overeenkomt), en stuurt jou rapporten.

DMARC werkt dus alleen goed als SPF en DKIM eerst kloppen. Daarom begin je daar. De standaard voor DMARC stond sinds 2015 in [RFC 7489](https://www.rfc-editor.org/rfc/rfc7489.html). In 2026 verscheen [RFC 9989](https://www.rfc-editor.org/info/rfc9989), die RFC 7489 vervangt. Waar RFC 7489 een informatief document was, staat RFC 9989 op het standaardspoor van de IETF. Voor jou verandert er weinig: een DMARC-record begint nog steeds met `v=DMARC1`, en de beleidsopties none, quarantine en reject blijven bestaan.

## Stap 1: maak een lijst van alles wat namens jou mailt

De eerste stap bij DMARC instellen is een lijst van elke dienst die mail verstuurt met jouw domein als afzender. De meeste mailproblemen ontstaan omdat iemand vergeten is dat er nog iets anders mailt. Denk aan:

- je mailbox (Microsoft 365, Google Workspace, of de mail van je hosting);
- je website of webshop (orderbevestigingen, contactformulier);
- je nieuwsbrief (Mailchimp, Klaviyo, Brevo, Shopify Email);
- je boekhoudpakket of facturatiesoftware;
- een boekingssysteem of CRM.

Vraag ook collega's welke tools ze gebruiken, bijvoorbeeld voor offertes of afspraakherinneringen. Een dienst die niet op de lijst staat, krijg je later terug als mislukte mail in de DMARC-rapporten.

## Stap 2: SPF en DKIM goed zetten

SPF en DKIM zijn de twee controles waar DMARC op leunt, dus zet je die eerst goed.

**SPF.** Een domein mag volgens de [SPF-standaard](https://www.rfc-editor.org/rfc/rfc7208.html) maar **één** SPF-record hebben. Twee records die beide met `v=spf1` beginnen, maken SPF ongeldig. Voeg alle diensten samen in één record, bijvoorbeeld:

`v=spf1 include:spf.protection.outlook.com include:servers.mcsv.net -all`
Let op de grens van 10 DNS-opzoekingen. Elke `include` telt mee, en sommige includes bevatten er zelf weer meer. Ga je erover, dan faalt SPF. Meer daarover lees je in [SPF record instellen](https://www.joepify.nl/kennisbank/spf-record-instellen).

**DKIM.** DKIM zet je per dienst aan. Bij [Microsoft 365](https://learn.microsoft.com/nl-nl/defender-office-365/email-authentication-dmarc-configure) zijn dat twee CNAME-records (selector1 en selector2) en daarna een schakelaar in de Defender-portal. Bij [Google Workspace](https://support.google.com/a/answer/174124?hl=nl) maak je de sleutel aan in de beheerconsole en zet je een TXT-record op `google._domainkey`. Nieuwsbriefdiensten geven je hun eigen records onder "domein verifiëren" of "domain authentication".

## Stap 3: DMARC toevoegen, in drie fases

Een DMARC-record is een TXT-record dat je toevoegt in het DNS-beheer van je domein. Dat beheer zit bij je registrar of hostingpartij, zoals TransIP, Mijndomein, Strato, Vimexx of in DirectAdmin of Plesk. Weet je niet waar je DNS zit, dan laat de [website check](https://www.joepify.nl/website-apk#apk-modules) het je zien in het onderdeel domein.

Maak een TXT-record aan met als naam `_dmarc` (sommige panelen willen `_dmarc.jouwdomein.nl`). Daarna doorloop je drie fases: eerst meekijken, dan quarantine, tot slot reject.

### Fase 1: meekijken

`v=DMARC1; p=none; rua=mailto:dmarc@jouwdomein.nl`
Fase 1 is een meekijkfase: met `p=none` verandert er nog niets aan je mail. Je krijgt wel dagelijks rapporten (XML-bestanden) van grote mailproviders, bijvoorbeeld van Google en Microsoft. Daarin zie je welke servers namens jou mailen en of ze slagen. De bestanden zijn lastig leesbaar, dus gebruik een gratis of betaalde DMARC-rapportagedienst, of laat iemand meekijken. Reken op twee tot vier weken voor deze fase.

### Fase 2: quarantine

Fase 2 is de stap naar quarantine, zodra al je eigen diensten twee tot vier weken lang slagen. Zet het beleid dan op:

`v=DMARC1; p=quarantine; rua=mailto:dmarc@jouwdomein.nl`
Mail die niet voldoet, gaat nu naar de spammap van de ontvanger. Volgens RFC 9989 betekent quarantine dat jij als domeineigenaar mislukte mail verdacht vindt. De nieuwe standaard kent de tag `pct` niet meer, dus reken niet op een geleidelijke uitrol met bijvoorbeeld `pct=25`.

### Fase 3: reject

`v=DMARC1; p=reject; rua=mailto:dmarc@jouwdomein.nl`
Fase 3 is het eindpunt: met `p=reject` wordt valse mail namens jouw domein geweigerd. Volgens RFC 9989 mag een ontvanger zo'n mail ook in quarantaine plaatsen in plaats van weigeren, maar in beide gevallen komt de valse mail niet in de inbox. Blijf de rapporten na de overstap lezen, want een nieuwe dienst zonder SPF of DKIM valt nu meteen weg.

## Hoe werkt DMARC met je webshop of nieuwsbrief?

DMARC is voor je webshop of nieuwsbrief alleen veilig als elke dienst je eigen domein verifieert. De meeste DMARC-problemen zitten namelijk in automatisch verstuurde mail, niet in je gewone mailbox.

- **Shopify** verstuurt orderbevestigingen namens je eigen adres als je in de instellingen je domein hebt geverifieerd met de DNS-records van Shopify. Zonder verificatie gaat de mail via een Shopify-adres en sluit hij niet aan op je DMARC.
- **WooCommerce en WordPress** mailen standaard via de webserver. De webserver staat meestal niet in je SPF en tekent niet met DKIM. Gebruik een SMTP-plugin met je mailbox of een maildienst.
- **Nieuwsbriefdiensten** zoals Mailchimp, Klaviyo en Brevo willen dat je je domein verifieert. Zonder verificatie gaan je campagnes via hun domein, en in de DMARC-rapporten zie je dan "niet aligned".
- **Boekhoud- en boekingssoftware** mailt soms namens je adres zonder dat je het weet. In fase 1 zie je zulke mail vanzelf in de rapporten.

Daarom duurt fase 1 bij de meeste bedrijven twee tot vier weken: lang genoeg om elke maandelijkse factuurrun en nieuwsbrief een keer langs te zien komen. Verstuur je de nieuwsbrief liever niet zelf? Lees dan hoe [mailing uitbesteden](https://www.joepify.nl/blog/email-marketing-uitbesteden) werkt.

## Hoe bescherm je domeinen die niet mailen?

De beste bescherming voor een domein zonder mail is een strikt SPF-record plus een DMARC-record op reject. Denk aan een oude bedrijfsnaam, een tikfout-domein of een extra domein voor een doorverwijzing. Zo staat het ook in het advies van het [NCSC](https://www.ncsc.nl/phishing/bescherm-domeinnamen-tegen-phishing):

```
SPF:   v=spf1 -all
DMARC: v=DMARC1; p=reject
```
Met deze twee records meld je aan Gmail van Google, Outlook van Microsoft en andere ontvangers dat er van het domein nooit echte mail komt. Mail met zo'n afzender wordt dan geweigerd. Een rua-adres is hier niet verplicht, maar wel handig: in de rapporten zie je of iemand je domein probeert te misbruiken.

## Wat zijn veelgemaakte fouten bij DMARC?

De meest gemaakte fout bij DMARC is te snel naar reject gaan, maar er zijn er vijf die vaak terugkomen:

- **Twee SPF-records** na een overstap naar een nieuwe mailprovider.
- **Meteen op reject** zonder rapporten te bekijken. Dan verdwijnen je orderbevestigingen of facturen zonder dat je het merkt.
- **Webshopmail via de webserver** zonder DKIM. Laat WordPress liever via een SMTP-dienst of je mailbox versturen.
- **DMARC-record op de verkeerde plek**, zoals op `_dmarc.jouwdomein.nl.jouwdomein.nl`, omdat het paneel de domeinnaam al toevoegt.
- **Blijven hangen op p=none.** Dan heb je wel rapporten, maar nog geen bescherming.

In de praktijk zie ik daarnaast de tweede en de laatste fout het vaakst: de ene ondernemer zet in één keer alles op slot, de andere blijft jaren op meekijken staan.

## Hoe controleer je of DMARC werkt?

De controle of DMARC werkt, is een combinatie van een DNS-test en een testmail. DNS-wijzigingen zijn meestal binnen een uur zichtbaar, soms duurt het langer. Test daarna je domein met de [e-mail check](https://www.joepify.nl/email-check) of met [internet.nl](https://internet.nl/), de testsite van het Platform Internetstandaarden. Stuur daarnaast een mail naar een Gmail-adres en kijk via "Origineel weergeven" of SPF, DKIM en DMARC op PASS staan. Herhaal de testmail vanuit je webshop en je nieuwsbriefdienst, want daar gaat het vaker mis dan in je gewone mailbox.

## Wat de website APK hierbij checkt

De website APK is een gratis scan van Joepify die in het onderdeel e-mail je MX-, SPF- en DMARC-records leest. Je start de scan via de [website check](https://www.joepify.nl/website-apk#apk-modules). De APK telt dubbele SPF-records en kijkt welk [DMARC-beleid](https://www.joepify.nl/onderzoek-webshops-2026) je hebt. Voor DKIM probeert de scan de bekende selectors van Microsoft 365 en Google. Gebruik je een andere dienst, dan kan DKIM als onbekend verschijnen terwijl het wel goed staat.

- Gratis tool[Test je SPF, DKIM en DMARC met de gratis e-mail check](https://www.joepify.nl/email-check)
- Liever uitbesteden[Mailt je WordPress-site niet goed? Bekijk WordPress onderhoud](https://www.joepify.nl/wordpress-onderhoud)

---
Bron: [DMARC instellen in 3 stappen (Microsoft 365, Google)](https://www.joepify.nl/kennisbank/dmarc-instellen) · Licentie: CC BY 4.0, noem Joepify met een link naar de originele pagina.
