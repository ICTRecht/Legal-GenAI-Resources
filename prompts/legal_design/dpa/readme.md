# 📌 Overzicht

De **Legal Design DPA-prompt** genereert een **visueel overzichtelijke, begrijpelijke en AVG-conforme verwerkersovereenkomst**. De prompt is bedoeld voor gebruik in AI-tools zoals ChatGPT of Claude en zet alle door jou ingevulde parameters automatisch om in:

* **Pagina 1:** de juridische kern van de verwerkersovereenkomst
* **Pagina 2:** een helder overzicht van verwerkingen én subverwerkers in tabelvorm

Het resultaat is een **professioneel vormgegeven contract**, afgestemd op niet-juristen, met iconen, schema’s en een minimalistische layout.

Deze prompt is ideaal voor:

* IT-leveranciers, SaaS-aanbieders en consultants
* Privacy- en securityteams die DPA’s toegankelijk willen presenteren
* Verwerkingsovereenkomsten binnen tenders of commerciële trajecten
* Interne documentatie en onboarding van medewerkers

---

# 🚀 Hoe gebruik je het?

## **Stap 1: Kopieer de volledige XML-prompt**

Kopieer de volledige `<LegalDesignDPA>`-structuur naar je AI-omgeving.
De prompt bestaat uit verschillende blokken:

1. **Instructies** – hoe het contract visueel moet worden opgebouwd
2. **Outputinstellingen** – bestandsformaat, pagina-indeling
3. **Parameters** – alle juridische en feitelijke input (partijen, grondslagen, meldtermijnen, enz.)
4. **Stijlregels** – kleuren, typografie en eventueel een logo
5. **Focusonderwerpen** – inhoudelijke thema’s die duidelijk visueel benadrukt worden
6. **Verwerkingen & Subverwerkers** – tabellen voor pagina 2

---

## **Stap 2: Vul de parameters aan**

Je kunt alle placeholders aanpassen aan de concrete situatie. Bijvoorbeeld:

```xml
<Perspectief>Verwerker</Perspectief>
<DoelVanVerwerking>Hosting van klantdata</DoelVanVerwerking>
<Meldtermijn>zonder onredelijke vertraging</Meldtermijn>
<DoorgiftePersoonsgegevens>Buiten EER met passend beschermingsniveau</DoorgiftePersoonsgegevens>
```

Of gegevens van partijen:

```xml
<PartijA>
  <Naam>Innovate Cloud BV</Naam>
  <Adres>Stationsweg 12, Utrecht</Adres>
  <KamerVanKoophandel>77889911</KamerVanKoophandel>
  <Rol>Verwerkingsverantwoordelijke</Rol>
</PartijA>
```

De prompt gebruikt standaard de termen **Verwerkingsverantwoordelijke** en **Verwerker**, zodat het document AVG-conform en begrijpelijk blijft.

---

## **Stap 3: Pas de stijl aan (optioneel)**

Je kunt een logo toevoegen of de layout baseren op eigen huisstijlkleuren:

```xml
<Logo>https://domein.nl/logo.png</Logo>
<StijlHoofdkleur>#003366</StijlHoofdkleur>
<StijlSteunkleur>#00AACC</StijlSteunkleur>
<StijlTypografie>Raleway</StijlTypografie>
```

Bij geen logo:

* wordt automatisch gewerkt met jouw gekozen hoofd- en steunkleur
* blijft de stijl minimalistisch, professioneel én illustratief

---

## **Stap 4: Verwerkingen en subverwerkers toevoegen**

Pagina 2 wordt automatisch opgemaakt in twee tabelvormen:

* **Verwerkingsoverzicht**
* **Subverwerkersoverzicht**

Voorbeeld uitbreidingen:

```xml
<Verwerking>
  <NaamVerwerking>Klantbeheer</NaamVerwerking>
  <Betrokkenen>Klanten</Betrokkenen>
  <SoortPersoonsgegevens>NAW, contactgegevens, bestelgeschiedenis</SoortPersoonsgegevens>
  <Grondslag>Gerechtvaardigd belang</Grondslag>
  <Doorgifte>Nee</Doorgifte>
</Verwerking>
```

```xml
<Subverwerker>
  <NaamSubverwerker>Analytics GmbH</NaamSubverwerker>
  <Activiteiten>Analysetools voor applicatiegebruik</Activiteiten>
  <Doorgifte>Ja</Doorgifte>
  <Verwerkersovereenkomst>Ja</Verwerkersovereenkomst>
</Subverwerker>
```

---

## **Stap 5: Verstuur de prompt**

Stuur de volledige XML-prompt (inclusief parameters, verwerkingen en subverwerkers) naar het AI-systeem. Voeg eventueel toe:

> “Genereer de verwerkersovereenkomst volgens deze prompt.”

Het systeem maakt vervolgens:

* **Eerste pagina:** kernovereenkomst, schema’s en iconen
* **Tweede pagina:** tabellen met alle verwerkingen en subverwerkers

Uitvoerformaat standaard: **PNG**, maar aanpasbaar naar **PDF** of **HTML**.

---

# 🧩 Aanpassingen & uitbreidingen

## **Juridische inhoud aanpassen**

Je kunt snel variëren door:

* strengere meldplichten te kiezen
* andere grondslagen of doeleinden te specificeren
* een auditregime aan te passen
* doorgifte buiten de EER strenger of soepeler te maken

Ook kun je nieuwe onderwerpen toevoegen aan `<FocusOnderwerpen>` als je extra visuele aandacht wilt:

```xml
<Onderwerp>Gegevensminimalisatie</Onderwerp>
<Onderwerp>Beveiligingscertificeringen</Onderwerp>
```

---

## **Visuele layout veranderen**

Alles wat visueel is, staat centraal configureerbaar in `<Stijlregels>`.
Voorbeelden:

* strakke of speelse iconen
* diagrammen met flows, tijdlijnen of datastromen
* grotere of kleinere signatuurblokken

---

# 📄 Outputmogelijkheden

De prompt ondersteunt:

```xml
<Bestandsformaat>PNG</Bestandsformaat>
<Bestandsformaat>PDF</Bestandsformaat>
<Bestandsformaat>HTML</Bestandsformaat>
```

Hiermee kun je de DPA opnemen in:

* contractbundels
* offertes
* interne wiki’s
* presentaties
* legal handbooks

---

# 📖 Voorwaarden & aandachtspunten

* De gegenereerde DPA is een **conceptweergave**; altijd juridisch laten toetsen.
* Controleer vooral:

  * De juistheid van alle verwerkingen en subverwerkers
  * De meldtermijnen (incidenten & verzoeken betrokkenen)
  * De grondslagen volgens de AVG
  * De rolverdeling (Verwerker / Verwerkingsverantwoordelijke)
* Voeg geen persoonsgegevens toe die niet noodzakelijk zijn.
