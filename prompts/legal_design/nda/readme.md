Hieronder een voorstel voor een volledige **README** voor jouw nieuwe *Legal Design NDA-prompt*. Ik sluit qua indeling en stijl aan op de structuur van de reeds bijgevoegde readme, maar afgestemd op het doel van deze prompt: het genereren van visueel ontworpen, juridisch vereenvoudigde NDA’s.


# 📌 Overzicht

De **Legal Design NDA-prompt** is ontwikkeld om snel en consistent een **visueel overzichtelijke, juridisch begrijpelijke geheimhoudingsovereenkomst (NDA)** te genereren. De prompt zet jouw parameters automatisch om in een **professioneel vormgegeven contractpagina** in PNG-, PDF- of HTML-formaat.

Deze prompt is geschikt voor het gebruik in Nano Banana Pro. Alhoewel de prompt ook al werken in andere AI-systemen, zal de kwaliteit mogelijk minder zijn.

# 🚀 Hoe gebruik je het?

## **Stap 1: Kopieer de XML-prompt**

Kopieer de volledige `<LegalDesignNDA>`-structuur in je AI-tool.
De prompt bestaat uit drie hoofdonderdelen:

1. **Instructies & Output** – hoe de visual moet worden gebouwd
2. **Parameters** – alle inhoudelijke keuzes voor de NDA
3. **Stijlregels & Focusonderwerpen** – visuele stijl en juridische elementen


## **Stap 2: Vul de parameters in**

De prompt werkt het best wanneer alle placeholders worden ingevuld. Voorbeelden:

```xml
<PartijA>
  <Naam>Innovate BV</Naam>
  <Adres>Stationsweg 10, Utrecht</Adres>
  <KamerVanKoophandel>12345678</KamerVanKoophandel>
  <Rol>Informatieontvanger</Rol>
</PartijA>
```

Of inhoudelijke keuzes zoals:

```xml
<Reciprociteit>Wederkerig</Reciprociteit>
<Vertrouwelijkheid>Gebalanceerd</Vertrouwelijkheid>
<Boete>Ja</Boete>
<HoogteBoete>EUR 500 per overtreding</HoogteBoete>
```

Je kunt alle velden aanpassen aan de specifieke deal, interne template of huisstijl.


## **Stap 3: Optioneel – upload een logo**

Als je een logo toevoegt in `<Logo>`, gebruikt de AI automatisch:

* de kleuren uit het logo
* logische plaatsing bovenaan de pagina
* visuele accenten die passen bij de huisstijl

Zonder logo houdt de prompt zich aan jouw voorkeurskleuren:

```xml
<StijlHoofdkleur>blauw</StijlHoofdkleur>
<StijlSteunkleur>turqoise</StijlSteunkleur>
```


## **Stap 4: Verstuur de prompt**

Stuur de volledige XML-prompt in een bericht naar je AI-tool.
Voeg eventueel toe: **“Gebruik deze XML volledig”** of **“Genereer de NDA-visual volgens de prompt.”**

De AI genereert vervolgens een **volledig opgemaakte NDA-pagina**, inclusief:

* titelblok
* inleiding
* partijenschema
* diagram (flow/doel/duur)
* tabelstructuur met voorwaarden
* ondertekeningsblokken
* visuele iconen en minimalistische layout


# 🧩 Aanpassingen

## **Juridische inhoud aanpassen**

Je kunt eenvoudig variëren door:

* nieuwe onderwerpen in `<FocusOnderwerpen>` te plaatsen
* elementen weg te laten
* strengere of mildere definities te kiezen
* een ander doel van de NDA op te nemen

Voorbeeld uitbreiding:

```xml
<Onderwerp>Beveiligingsmaatregelen</Onderwerp>
<Onderwerp>Terugleverplicht van documenten</Onderwerp>
```

## **Visuele stijl wijzigen**

Alle visuele regels zijn centraal instelbaar:

* Minimalistisch, strak of illustratief
* Andere typografie (Google Fonts)
* Achtergrondkleur of -vlakken
* Gebruik van iconen

Je kunt de prompt zo inzetten voor marketing, legal of productteams.

# 📄 Outputmogelijkheden

De standaardinstelling is **PNG**, maar je kunt ook kiezen voor:

```xml
<Bestandsformaat>PDF</Bestandsformaat>
<Bestandsformaat>HTML</Bestandsformaat>
```

# 📖 Voorwaarden & aandachtspunten
* De gegenereerde NDA is een **conceptvoorstel** en vervangt geen juridisch advies.
* Controleer altijd:

  * correcte partijgegevens
  * de gekozen duur en reikwijdte van geheimhouding
  * het boetebeding
  * toepasselijk recht
* Houd rekening met vertrouwelijke gegevens bij het uploaden van logo’s of bedrijfsdetails.
