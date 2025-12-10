## 📌 Overzicht
De Contract- en Normenvergelijker is een gestructureerde prompt die je kunt gebruiken in AI-systemen zoals ChatGPT of Claude om twee juridische documenten met elkaar te vergelijken. De prompt analyseert verschillen tussen contracten, beleidsstukken of normen en levert een duidelijk rapport met afwijkingen, juridische duiding, mogelijke strijdigheid met EU-verplichtingen en suggesties voor verbeterde clausules.

## 🚀 Hoe gebruik je het?

### Stap 1: Voorbereiding

Zorg dat beide documenten die vergeleken moeten worden beschikbaar zijn in een machine-leesbaar formaat:

* PDF met tekstlaag (geen scans)
* Word-documenten (.docx)
* Tekstbestanden (.txt)

### Stap 2: XML-prompt aanpassen

1. Kopieer de volledige XML-prompt uit het bestand `prompt.xml`.

2. Pas indien gewenst de parameters aan, zoals:

   ```xml
   <TaalVoorkeur>Nederlands</TaalVoorkeur>
   <DetailNiveau>Gedetailleerd</DetailNiveau>
   ```

3. Voeg of wijzig eventuele focusgebieden die belangrijk zijn voor de analyse:

   ```xml
   <FocusGebieden>
     <Gebied>Aansprakelijkheid</Gebied>
     <Gebied>EU-conformiteit</Gebied>
     <Gebied>Beveiliging en privacy</Gebied>
   </FocusGebieden>
   ```

### Stap 3: Documenten uploaden

1. Open ChatGPT, Claude of een vergelijkbare tool met bestandsupload.
2. Upload beide te vergelijken documenten in dezelfde chat.

### Stap 4: Prompt indienen

1. Voeg het bestand `prompt.xml` toe als bijlage.
2. Verstuur een korte instructie, zoals: *"Voer deze prompt uit op de bijgevoegde documenten."*

### Stap 5: Resultaten gebruiken

De AI levert een volledig rapport met:

* verschillen en afwijkingen tussen beide documenten,
* juridische consequenties en interpretatie,
* eventuele strijdigheid met EU-verplichtingen,
* en voorstellen voor versterkte of duidelijkere bepalingen.

## 🛠 Aanpassingen

### Detailniveau

Kies zelf hoe uitgebreid de analyse moet zijn:

* **Beknopt**: alleen kernverschillen
* **Gedetailleerd**: uitgebreide inhoudelijke analyse (standaard)
* **Uitgebreid**: diepgaande juridische en contextuele duiding

### Focus uitbreiden

Je kunt extra thema’s opnemen, zoals:

* Overmacht
* Risicotoedeling
* Geschillenbeslechting
* Technische of sectorale normen

### Rapportage-opties

* Tabellen uitbreiden of kolommen aanpassen
* Risicoscores wijzigen
* Aanbevelingen meer of minder uitgebreid maken

## 📖 Voorwaarden

* De prompt is een hulpmiddel en vervangt geen juridisch advies.
* Controleer altijd de gegenereerde analyse voordat je deze zakelijk of juridisch toepast.
* Vermijd het uploaden van vertrouwelijke informatie tenzij dit volgens interne richtlijnen is toegestaan.
