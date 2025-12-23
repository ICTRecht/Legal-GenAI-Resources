# 📄 Visual Coverpage – Legal Design Prompt

## Overzicht

De **Visual Coverpage-prompt** is ontworpen om op basis van een bestaande overeenkomst een **visueel samenvattende coverpage** te genereren in Legal Design-stijl. Het doel is om in één oogopslag duidelijk te maken:

* waar de overeenkomst over gaat;
* wie de betrokken partijen zijn;
* wat de belangrijkste contractuele kernpunten zijn;
* hoe gunstig of ongunstig deze punten zijn vanuit een gekozen perspectief.

De output is nadrukkelijk **geen vervanging van de overeenkomst**, maar een visueel hulpmiddel voor uitleg, besluitvorming en communicatie met niet-juristen (zoals management, business, inkoop of klanten).

---

## Doel en toepassingsgebied

Deze prompt is geschikt voor onder meer:

* contract reviews en samenvattingen;
* interne besluitvorming (go/no-go);
* managementrapportages;
* onboarding van contracten;
* Legal Design-toepassingen richting cliënten.

De prompt is met name bedoeld voor gebruik in combinatie met AI-systemen die visuele output kunnen genereren (PNG, PDF, HTML).

---

## Hoe werkt de prompt?

De prompt bestaat uit vier hoofdonderdelen:

1. **Instructie**
   Beschrijft *wat* er moet worden gemaakt en *hoe*:

   * visuele samenvatting;
   * minimalistische, professionele layout;
   * eenvoudige taal;
   * gebruik van iconen;
   * focus op vooraf bepaalde onderwerpen.

2. **Output**
   Bepaalt het formaat en de inhoudelijke structuur van de coverpage:

   * A4-pagina;
   * vast stramien met titel, samenvatting, secties en footer;
   * vaste volgorde van informatie.

3. **Parameters**
   Bepaalt het **perspectief** van waaruit de overeenkomst wordt beoordeeld (bijvoorbeeld opdrachtgever of opdrachtnemer).
   Dit perspectief is relevant voor:

   * de duiding van risico’s;
   * het stoplichtmodel per onderwerp.

4. **Stijlregels & Focusonderwerpen**
   Bepaalt de visuele en inhoudelijke kaders:

   * kleuren, typografie en stijl;
   * welke contractonderwerpen expliciet worden uitgelicht.

---

## Stap-voor-stap gebruik

### Stap 1 – Voeg de overeenkomst toe

Upload of plak de volledige overeenkomst waarop de coverpage moet worden gebaseerd.

### Stap 2 – Controleer en pas parameters aan

Met name relevant:

```xml
<Perspectief>Opdrachtgever</Perspectief>
```

Pas dit aan indien de analyse vanuit een ander belang moet plaatsvinden.

### Stap 3 – Controleer stijlinstellingen

Je kunt de visual eenvoudig laten aansluiten bij huisstijl of doelgroep:

```xml
<StijlHoofdkleur>blauw</StijlHoofdkleur>
<StijlSteunkleur>turqoise</StijlSteunkleur>
<StijlTypografie>Raleway</StijlTypografie>
```

Indien gewenst kan een logo worden toegevoegd.

### Stap 4 – Genereer de visual

Gebruik de volledige prompt in één keer. De AI genereert een **visuele coverpage** volgens de vastgelegde structuur.

---

## Inhoudelijke opbouw van de coverpage

De gegenereerde coverpage bevat standaard:

1. **Titel en korte samenvatting**

   * Titel van de overeenkomst
   * Samenvatting in 4–6 regels, zonder juridisch jargon

2. **Partijenoverzicht**

   * Schematische weergave van de contractspartijen

3. **Looptijd en beëindiging**

   * Visueel diagram met:

     * startdatum
     * duur
     * einddatum
     * opzegtermijn

4. **Kernonderwerpen (FocusOnderwerpen)**

   * Tabelachtige structuur per onderwerp
   * Korte toelichting
   * Verwijzing naar het relevante artikel
   * Stoplichtmodel (groen/oranje/rood) vanuit het gekozen perspectief

5. **Footer**

   * Kleine iconen
   * Korte disclaimer (bijv. geen juridisch advies)

---

## Focusonderwerpen aanpassen

De onderwerpen die worden uitgelicht zijn flexibel aanpasbaar in:

```xml
<FocusOnderwerpen>
  <Onderwerp>Aansprakelijkheid</Onderwerp>
  <Onderwerp>Geheimhouding</Onderwerp>
  <Onderwerp>Verwerking van persoonsgegevens</Onderwerp>
</FocusOnderwerpen>
```

Je kunt:

* onderwerpen toevoegen of verwijderen;
* de prompt afstemmen op specifieke contracttypes (IT, SaaS, inkoop, samenwerking).

---

## Outputformaten

Standaard wordt een **PNG** gegenereerd, maar dit kan eenvoudig worden aangepast naar:

```xml
<Bestandsformaat>PDF</Bestandsformaat>
<Bestandsformaat>HTML</Bestandsformaat>
```

---

## Aandachtspunten en disclaimer

* De coverpage is een **visualisatie en samenvatting**, geen juridisch bindend document.
* Controleer altijd:

  * of alle relevante onderwerpen correct zijn geïnterpreteerd;
  * of artikelverwijzingen kloppen;
  * of de stoplichtbeoordeling past bij de context.
* Gebruik de visual bij voorkeur **naast** de volledige overeenkomst.
