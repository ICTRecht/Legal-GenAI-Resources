# 📚 Generative AI Prompts Repository

Welkom bij onze open-source repository voor prompts! Dit project is bedoeld als een gedeelde bron voor het verzamelen, organiseren en delen van prompts die werken met ChatGPT en andere Generative AI (GenAI) systemen en gericht zijn op juridische of ondersteunende taken.

---
## 🧠 Hoe de prompts te gebruiken

1. **Structuur**
   - GenAI gaat goed om met zeer gestructureerde instructies (bijvoorbeeld in de vorm van XML, JSON of MarkDown). 
   - De prompts binnen deze omgeving hebben allemaal een dergelijke structuur.

2. **Gebruik**
   - Je kunt de prompts kopieren en plakken in een willekeurige GenAI-toepassing om deze uit te voeren. Aan de prompt zelf hoef je niets meer te doen. Sommige prompts zijn ontwikkeld om een bestand te reviewen. In dat geval upload je het bestand samen met de prompt. Vaak is een druk op enter voldoende maar het kan zijn dat de AI vraagt of het de prompt moet uitvoeren. Een vriendelijke 'ja, graag' is dan voldoende.
   - Sommige prompts bevatten specifieke instructies of zijn geschikt voor specifieke modellen, lees in dat geval het Readme bestand voor aanvullende informatie.

3. **Aanpassen naar eigen wens**
   - Heb je een prompt gevonden die je graag wil aanpassen naar een specifieke situatie, zoals het invoegen van een bedrijfsspecifiek playbook? Kopieer de prompt dan samen met het playbook in een AI en vraag het om de prompt aan te passen naar de specifieke situatie. De gestructureerde prompt zal aangepast worden zonder de opzet aan te passen.
   - Vergeet de nieuwe prompt niet te delen!


## 🛠️ Hoe de repository te gebruiken

1. **Verkennen**
   - Blader door de mappen en bestanden om prompts te vinden die nuttig kunnen zijn voor jouw projecten.
   - Elke prompt bevat een beschrijving van het doel, voorbeelden en gebruiksinstructies.

2. **Bijdragen**
   - Heb je een interessante prompt ontwikkeld? Voeg deze toe aan de repository door een Pull Request te maken.
   - Zorg ervoor dat je prompt voldoet aan de richtlijnen voor indeling en beschrijving (zie hieronder).

3. **Aanpassen en experimenteren**
   - Pas prompts aan naar jouw behoeften en deel verbeteringen met de community.

---

## 🆕 Nieuwe prompts toevoegen?
   - De makkelijkste route is om bovenaan deze pagina een issue aan te maken en een prompt in te sturen. Dit mag een kant en klare prompt zijn, maar het idee voor een prompt is ook van harte welkom! Wij zorgen ervoor dat er een uitgebreide en gestrutureerde versie van komt. 
   - Wil je - als doorgewinterde GitHub-gebruiker 🤓 - zelf uploaden? Zie dan hieronder bij **Bijdragen**.

## 📂 Bestandsstructuur

We hebben een eenvoudige en duidelijke structuur om prompts te organiseren:

```
/
├── README.md            # Beschrijving van de repo
├── CONTRIBUTING.md      # Richtlijnen voor bijdragen
├── prompts/
│   ├── algemeen/        # Prompts die breed toepasbaar zijn
│   ├── juridisch/       # Prompts voor juridische toepassingen
│   │   ├── contract_review/ # Prompts voor contractanalyse
│   │   ├── rechtspraak/     # Samenvattingen van rechtspraak
│   │   ├── juridische_vragen/ # Antwoorden op juridische vragen
│   │   └── ...              # Andere juridische domeinen
│   ├── experimenten/    # Ongeteste of conceptuele prompts
│   └── sjablonen/       # Algemene formats of sjablonen voor prompts
└── voorbeelden/         # Voorbeeldinteracties met prompts
```

### Beschrijving van submappen

- **algemeen/**: Prompts die nuttig zijn voor algemene doeleinden (bijv. brainstormen, samenvatten, enz.).
- **juridisch/**: Prompts gericht op juridische domeinen, zoals contractreview, rechtspraak samenvatten en juridische vragen beantwoorden.
  - **contract_review/**: Analyseer en verbeter juridische contracten.
  - **rechtspraak/**: Maak samenvattingen van juridische uitspraken en vonnissen.
  - **juridische_vragen/**: Beantwoord veelvoorkomende of complexe juridische vragen.
- **experimenten/**: Prompts die nog verfijnd moeten worden; werk in uitvoering.
- **sjablonen/**: Basisstructuren om nieuwe prompts mee op te zetten.
- **voorbeelden/**: Bevat conversaties en resultaten die zijn gegenereerd met behulp van de prompts.

---

## 📜 Richtlijnen voor Prompts

### Bestandsnaam
Gebruik duidelijke en beschrijvende bestandsnamen, zoals `contract_review_voorbeeld.md` of `rechtspraak_samenvatting.md`.

### Bestandssjabloon
Elke prompt moet de volgende structuur volgen:

```markdown
# 🎯 Doel van de Prompt
Beschrijf het doel van de prompt en waarvoor deze bedoeld is.

---

## 📝 Prompt
```
[Hier plaats je de prompt die kan worden gekopieerd en geplakt.]
```

---

## 💡 Tips voor Gebruik
- Voeg hier tips toe voor het aanpassen of optimaliseren van de prompt.

---

## 📋 Voorbeeldoutput
Geef hier een voorbeeld van de gegenereerde output, zodat gebruikers weten wat ze kunnen verwachten.
```

---

## ✍️ Bijdragen
Wil je bijdragen aan dit project? Volg dan deze stappen om je wijzigingen correct in te dienen:

### 1. Fork & Clone
Fork deze repository en clone je fork naar je lokale omgeving.

```bash
git clone https://github.com/ICTRecht/prompts.git
cd prompts
```

### 2. Maak een feature branch
Werk nooit direct in `master` of `dev`. Maak een nieuwe branch gebaseerd op `dev`:

```bash
git checkout dev
git pull origin dev  # Zorg dat je up-to-date bent
git checkout -b prompt/{naam-van-je-prompt}
```

### 3. Werk aan je wijzigingen
Voeg je codewijzigingen toe, commit ze en push naar je fork:

```bash
git add .
git commit -m "Beschrijving van de wijziging"
git push origin prompt/{naam-van-je-prompt}
```

### 4. Maak een Pull Request aan
1. Ga naar de [GitHub repo](https://github.com/ICTRecht/prompts).
2. Open een **Pull Request** van jouw `prompt/{naam-van-je-prompt}` branch naar de `dev` branch.
3. Voeg een duidelijke beschrijving toe van je wijziging.

### 5. Review en Merge
- Het team zal je PR beoordelen en eventueel feedback geven.
- Zodra goedgekeurd, wordt de wijziging gemerged in `dev`.
- Het team kan nog mogelijk optimalisaties uitvoereen aan de prompts, waarna wijzigingen ook op de `master` branch zullen worden gepubliceerd.

### 6. Synchroniseer je lokale repo
Na het mergen, houd je lokale repository up-to-date:

```bash
git checkout dev
git pull origin dev
git branch -d prompt/{naam-van-je-prompt}  # Verwijder de feature branch lokaal
```

**Dank voor je bijdrage!**
---

## 📜 Licentie en community
```
De prompts zijn te gebruiken onder een CC BY licentie en mogen vrijelijk hergebruikt en aangepast worden.
---

## 🌐 Community en support

Heb je vragen of wil je feedback geven? Open een [issue](https://github.com/ICTRecht/prompts/issues).
