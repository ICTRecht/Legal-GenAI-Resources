# 📌 Overzicht

De **Legal Design DPA (Upload)-prompt** zet een **bestaande verwerkersovereenkomst** om in een **visueel, begrijpelijk en overzichtelijk Legal Design-document**. In plaats van vaste parameters analyseert deze prompt de **geüploade verwerkersovereenkomst** en haalt daar automatisch de relevante informatie uit, conform de AVG.

Het resultaat is een **samenvattende, visuele contractpagina** die de inhoud van de oorspronkelijke DPA toegankelijk maakt voor niet-juristen, zonder de juridische kern te verliezen.

Deze prompt is met name geschikt voor:

* Het visualiseren van bestaande (lange) verwerkersovereenkomsten
* Uitleg aan business, management of klanten
* Contractreviews en interne afstemming
* Sales- of onboardingdocumentatie
* Legal Design hergebruik van legacy contracten

---

# 🚀 Hoe gebruik je het?

## **Stap 1: Upload de verwerkersovereenkomst**

Upload eerst de bestaande verwerkersovereenkomst (bijvoorbeeld PDF of Word) in de AI-tool.
Zorg bij voorkeur voor:

* machine-leesbare tekst (geen scans)
* een volledige, definitieve versie van de overeenkomst

De prompt gebruikt deze overeenkomst als **primaire bron**.

---

## **Stap 2: Kopieer de XML-prompt**

Kopieer de volledige `<LegalDesignDPA>`-structuur in dezelfde chat of opdracht.

De prompt bestaat uit:

1. **Instructie** – analyse en herformulering van de geüploade DPA
2. **Output** – opmaak en inhoudelijke structuur van de visual
3. **Stijlregels** – visuele vormgeving
4. **FocusOnderwerpen** – welke AVG-thema’s expliciet worden uitgelicht

---

## **Stap 3: Kies het perspectief**

In de instructie wordt gewerkt vanuit één juridisch perspectief:

```xml
[Perspectief]
```

Dit kan zijn:

* **Verwerkingsverantwoordelijke**
* **Verwerker**

Het gekozen perspectief bepaalt:

* de toon van de samenvatting
* welke verplichtingen extra nadruk krijgen
* hoe verantwoordelijkheden visueel worden gepresenteerd

---

## **Stap 4: Focusonderwerpen bepalen**

De prompt haalt uitsluitend informatie uit de geüploade overeenkomst die relevant is voor de opgegeven focusonderwerpen, zoals:

```xml
<Onderwerp>Beveiliging van persoonsgegevens</Onderwerp>
<Onderwerp>Audits</Onderwerp>
<Onderwerp>Inschakeling subverwerkers</Onderwerp>
```

Je kunt onderwerpen:

* toevoegen (voor extra aandacht)
* verwijderen (voor een compactere visual)

Dit maakt de output modulair en doelgericht.

---

## **Stap 5: Stijl instellen (optioneel)**

Je kunt de visuele stijl volledig afstemmen op je huisstijl:

```xml
<StijlHoofdkleur>blauw</StijlHoofdkleur>
<StijlSteunkleur>turqoise</StijlSteunkleur>
<StijlTypografie>Raleway</StijlTypografie>
```

Optioneel kun je een logo uploaden.
Zonder logo gebruikt de prompt automatisch:

* de opgegeven hoofd- en steunkleuren
* een minimalistische, professionele layout
* duidelijke iconen en schema’s

---

## **Stap 6: Prompt indienen**

Stuur de XML-prompt samen met de geüploade verwerkersovereenkomst naar het AI-systeem, bijvoorbeeld met de instructie:

> “Genereer een Legal Design-versie van deze verwerkersovereenkomst volgens de prompt.”

De AI:

* leest en interpreteert de oorspronkelijke overeenkomst
* destilleert de kern per focusonderwerp
* herschrijft dit in eenvoudige taal
* visualiseert dit in één overzichtelijke contractpagina

---

# 📄 Output

De standaard output is:

```xml
<Paginaformaat>A4</Paginaformaat>
<Bestandsformaat>PNG</Bestandsformaat>
```

Maar ook geschikt voor:

* **PDF** (delen of printen)
* **HTML** (intranet, klantportaal, tooling)

De pagina bevat o.a.:

* titel en korte inleiding
* overzicht van partijen
* blokken/tabelstructuur met kernverplichtingen
* diagram (doel, flow of duur)
* visuele samenvatting per focusonderwerp
* ondertekeningsvelden en disclaimer

---

# 🧩 Wanneer gebruik je deze prompt?

Gebruik deze **upload-variant** vooral wanneer:

* er al een bestaande DPA ligt
* je geen handmatige parameterinvoer wilt
* de inhoud leidend moet zijn, niet het template
* je snel inzicht wilt geven in een complex contract

Voor nieuwe overeenkomsten of volledig configureerbare DPA’s is de **parameter-gedreven DPA-prompt** geschikter.

---

# 📖 Juridische aandachtspunten

* De output is een **visualisatie en samenvatting**, geen vervanging van het oorspronkelijke contract.
* Controleer altijd:

  * of alle essentiële verplichtingen correct zijn overgenomen
  * of nuances (bijv. uitzonderingen of voorwaarden) niet verloren zijn gegaan
  * of de focusonderwerpen passen bij het beoogde gebruik
