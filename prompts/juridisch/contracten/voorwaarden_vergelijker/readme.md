## 📌 Overzicht
De Voorwaardenvergelijker is een geavanceerde prompt die je kunt gebruiken met AI-systemen zoals Claude of ChatGPT om juridische documenten systematisch te vergelijken. Deze tool is specifiek ontworpen om inkoopvoorwaarden en algemene voorwaarden naast elkaar te analyseren en biedt een gestructureerd rapport waarin overeenkomsten, conflicten en complementaire bepalingen duidelijk worden weergegeven.

## 🚀 Hoe gebruik je het?
### Stap 1: Voorbereiding
Zorg dat je beide documenten die je wilt vergelijken in een doorzoekbaar formaat hebt:
- PDF met machine-leesbare tekst (geen scans)
- Word-documenten (.docx)
- Tekstbestanden (.txt)

### Stap 2: XML-prompt aanpassen
1. Kopieer de volledige XML-prompt uit het bestand "prompt.xml"
2. Pas de parameters aan naar behoefte, bijvoorbeeld:
   ```xml
   <TaalVoorkeur>Nederlands</TaalVoorkeur> <!-- Of: Engels, Duits, etc. -->
   <DetailNiveau>Gedetailleerd</DetailNiveau> <!-- Keuze uit: Beknopt/Gedetailleerd/Uitgebreid -->
   ```
3. Pas de focusgebieden aan die voor jouw situatie relevant zijn:
   ```xml
   <FocusGebieden>
     <Gebied>Aansprakelijkheid</Gebied>
     <Gebied>Betalingstermijnen</Gebied>
     <!-- Voeg toe of verwijder naar behoefte -->
   </FocusGebieden>
   ```

### Stap 3: Documenten uploaden
1. Open ChatGPT, Claude of andere vergelijkbare tool die bijlagen ondersteunt in je browser
2. Upload beide documenten naar de chatinterface:

### Stap 4: Prompt indienen
1. Voeg de prompt.xml ook als bijlage toe.
2. Voeg een korte instructie toe, bijvoorbeeld: "Volg de prompt uit de XML."
3. Verzend je bericht

### Stap 5: Resultaten gebruiken
1. Je ontvangt een volledig gestructureerd rapport

## 🛠 Aanpassingen
### Wijzig detailniveau
Pas het detailniveau aan op basis van je behoeften:
- **Beknopt**: Korte samenvatting en alleen de belangrijkste punten
- **Gedetailleerd**: Standaard niveau met substantiële analyse
- **Uitgebreid**: Diepgaande analyse met uitgebreide vergelijkingen en meer context

### Aanvullende focusgebieden
Voeg extra focusgebieden toe die meegenomen moeten worden in de analyse, zoals:
- Overmacht
- Toepasselijk recht
- Geschillenbeslechting
- Certificeringseisen
- Verzekeringsvereisten

### Rapportage-opties
In de prompt kun je de rapportage-opties aanpassen:
- Pas de tabellen aan door kolommen toe te voegen/verwijderen
- Wijzig de prioriteitsschalen (bijv. van Hoog/Midden/Laag naar numerieke scores)
- Voeg extra secties toe aan het rapport

## 📖 Voorwaarden
- De prompt is bedoeld als ondersteunend hulpmiddel en vervangt geen juridisch advies.
- Controleer altijd de output voordat je deze gebruikt in juridische documenten.
- Wees voorzichtig met het verwerken van persoonsgegevens én bedrijfsgegevens. Vermijd het uploaden van gevoelige informatie naar online AI-diensten. Gebruik bij voorkeur een Local LLM voor maximale privacy.