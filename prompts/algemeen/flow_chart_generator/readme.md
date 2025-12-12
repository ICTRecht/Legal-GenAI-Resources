# Mermaid Flowchart Generator

Deze prompt helpt bij het omzetten van aangeleverde tekst en/of documenten naar een Mermaid flowchart (Markdown).  
De prompt is domein-agnostisch en geschikt voor het structureren en visualiseren van processen, beslisbomen, rollen/partijen en complexe relaties, zonder inhoudelijke aannames te doen over het onderwerp.

De output is direct bruikbaar in Markdown-omgevingen die Mermaid ondersteunen.

## Doel

Het doel van deze prompt is om:
- impliciete processen, flows en relaties uit tekst of documenten te extraheren;
- deze te vertalen naar een Mermaid code;
- deze code kun je copy/pasten naar een mermaid editor die de code vertaalt naar een visuele flowchart.

De prompt is met name geschikt om complexe processen of situaties overzichtelijk en visueel weer te geven voor effectieve commmunicatie.

## Wat deze prompt doet

De prompt instrueert het taalmodel om:
1. bouwstenen (stappen, beslissingen, rollen, inputs/outputs) uit de input te identificeren;
2. een consistente flow te construeren met start- en eindpunten;
3. optioneel swimlanes (subgraphs) te gebruiken per rol of partij;
4. een syntactisch correcte Mermaid flowchart te genereren;
5. onzekerheden expliciet te maken via vragen of aannames.

## Wat deze prompt níet doet

- Geen inhoudelijke of juridische interpretaties toevoegen.
- Geen domeinspecifieke modellen afdwingen.
- Geen visualisaties anders dan Mermaid flowcharts genereren.
- Geen toelichtende tekst buiten het Mermaid codeblock opnemen.

## Input

De gebruiker kan:
- vrije tekst invoeren;
- één of meerdere documenten uploaden (bijv. contracten, beleidsstukken, e-mails, memo’s).

Alle input wordt behandeld als bronmateriaal waaruit structuur, volgorde en relaties moeten worden afgeleid.

## Output

De output bestaat uit:
- exact één Markdown codeblock met ```mermaid``` als taalhint;
- een Mermaid `flowchart` met:
  - duidelijke stappen en beslispunten;
  - optionele swimlanes per rol/partij;
  - edge labels voor voorwaarden of uitkomsten;
  - optionele comments voor bronverwijzingen of aannames.

Er wordt geen extra uitleg of tekst buiten het codeblock gegeven.

## Omgaan met onzekerheid

Als essentiële informatie ontbreekt, hanteert de prompt één van twee strategieën:
- **Vragen stellen**: maximaal 4 korte, gerichte vragen; de output stopt dan vóór het genereren van een flowchart.
- **Aannames maken**: expliciet vermeld als Mermaid comments bovenaan de flowchart.

De gekozen strategie is instelbaar in de promptparameters.

## Geschikte toepassingen

Deze prompt is onder andere geschikt voor:
- het visualiseren van interne of externe processen;
- het structureren van complexe besluitvormingsflows;
- het in kaart brengen van verantwoordelijkheden en overdrachten;
- het voorbereiden van documentatie of analyse waarbij overzicht cruciaal is.

## Gebruik

Kopieer de prompt uit de promptbibliotheek, voeg je tekst en/of documenten toe, en laat het model de flowchart genereren.  
De resulterende Mermaid-code kan direct worden opgenomen in Markdown-documentatie of tooling die Mermaid ondersteunt.
