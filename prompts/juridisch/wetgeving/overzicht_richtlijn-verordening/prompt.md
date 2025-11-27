# 🎯 Doel van de Prompt
Het doel van deze prompt is om een overzicht van een Europese richtlijn of verordening te krijgen, die helpt om er snel inhoudelijk doorheen te navigeren. Doordat je per artikel het onderwerp en relevante overwegingen ziet, kun je makkelijk context geven bij het onderzoeken van de bepalingen. 
---

> **Let op:** Wees voorzichtig met het verwerken van persoonsgegevens, maar ook bedrijfsgegevens. Gebruik het liefste een Local LLM.

## 📝 Prompt
```
Bijgaand vind je de tekst van de AVG. Ik wil een overzicht van alle bepalingen hieruit. Maak daarvoor en tabel met de volgende kolommen:
- artikelnummer
- onderwerp van de bepalingen
- relevante overwegingen    
```

---

## 💡 Tips voor Gebruik

Deze prompt verwacht dat je de tekst van de richtlijn of verordening bijvoegt. Download hiervoor bijvoorbeeld de PDF van EUR-Lex.

Het wil nog wel eens voorkomen bij grotere richtlijnen of verordeningen dat artikelen worden overgeslagen in het overzicht. Met vervolgprompts kan dan worden geprobeerd het overzicht wel volledig te krijgen. Denk bijvoorbeeld aan prompts als 
```
Niet alle bepalingen komen terug in het overzicht. Er zijn een aantal overgeslagen. Kun je zorgen dat echt alle bepalingen zijn opgenomen?
```
---

## 📋 Voorbeeldoutput
Dit is een voorbeeld van zo'n overzicht gebaseerd op de AVG:

| Artikelnummer | Onderwerp | Relevante overwegingen |
|--------------|----------|------------------------|
| 1  | Onderwerp en doelstellingen | 1, 2, 3 |
| 2  | Materieel toepassingsgebied | 14, 15, 16 |
| 3  | Territoriaal toepassingsgebied | 22, 23, 24 |
| 4  | Definities | 26, 27, 28 |
| 5  | Beginselen inzake verwerking van persoonsgegevens | 39, 40, 41 |
| 6  | Rechtmatigheid van verwerking | 42, 43, 44 |
| 7  | Voorwaarden voor toestemming | 32, 33 |
| 8  | Toestemming van kinderen voor diensten van de informatiemaatschappij | 38 |
| 9  | Verwerking van bijzondere categorieën van persoonsgegevens | 51, 52 |
| 10 | Verwerking van persoonsgegevens betreffende strafrechtelijke veroordelingen en strafbare feiten | 50 |
| 11 | Verwerking waarvoor identificatie niet is vereist | 57, 58 |
| 12 | Transparante informatie en communicatie | 58, 59 |
| 13 | Informatie die moet worden verstrekt wanneer persoonsgegevens bij de betrokkene worden verzameld | 60, 61 |
| 14 | Informatie die moet worden verstrekt wanneer persoonsgegevens niet bij de betrokkene zijn verkregen | 62, 63 |
| 15 | Recht van inzage van de betrokkene | 63, 64 |
| 16 | Recht op rectificatie | 65 |
| 17 | Recht op wissing (‘recht op vergetelheid’) | 65, 66 |
| 18 | Recht op beperking van de verwerking | 67 |
| 19 | Kennisgevingsplicht inzake rectificatie of wissing van persoonsgegevens | 66, 67 |
| 20 | Recht op overdraagbaarheid van gegevens | 68 |
| 21 | Recht van bezwaar | 69, 70 |
| 22 | Geautomatiseerde individuele besluitvorming, met inbegrip van profilering | 71 |
| 23 | Beperkingen | 73 |
| 24 | Verantwoordelijkheid van de verwerkingsverantwoordelijke | 74, 75 |
| 25 | Gegevensbescherming door ontwerp en door standaardinstellingen | 78 |
| 26 | Gezamenlijke verwerkingsverantwoordelijken | 79 |
| 27 | Vertegenwoordigers van verwerkingsverantwoordelijken of verwerkers die niet in de Unie zijn gevestigd | 80 |
| 28 | Verwerkers | 81 |
| 29 | Verwerking onder gezag van de verwerkingsverantwoordelijke of de verwerker | 82 |
| 30 | Register van de verwerkingsactiviteiten | 82, 83 |
| 31 | Samenwerking met de toezichthoudende autoriteit | 82 |
| 32 | Beveiliging van de verwerking | 83 |
| 33 | Melding van een inbreuk in verband met persoonsgegevens aan de toezichthoudende autoriteit | 85 |
| 34 | Mededeling van een inbreuk in verband met persoonsgegevens aan de betrokkene | 86 |
| 35 | Gegevensbeschermingseffectbeoordeling | 90 |
| 36 | Voorafgaande raadpleging | 94 |
| 37 | Aanwijzing van de functionaris voor gegevensbescherming | 97 |
| 38 | Positie van de functionaris voor gegevensbescherming | 98 |
| 39 | Taken van de functionaris voor gegevensbescherming | 99 |
| 40 | Gedragscodes | 98 |
| 41 | Toezicht op goedgekeurde gedragscodes | 98 |
| 42 | Certificering | 100 |
| 43 | Certificeringsorganen | 101 |
| 44 | Algemene beginselen voor doorgiften | 102 |
| 45 | Doorgiften op basis van adequaatheidsbesluiten | 103 |
| 46 | Doorgiften op basis van passende waarborgen | 108 |
| 47 | Bindende bedrijfsvoorschriften | 110 |
| 48 | Doorgifte of bekendmaking niet toegestaan bij een rechterlijk vonnis of een besluit van een administratieve autoriteit van een derde land | 111 |
| 49 | Uitzonderingen voor specifieke situaties | 112 |
| 50 | Internationale samenwerking voor de bescherming van persoonsgegevens | 115 |
| 51 | Toezichthoudende autoriteit | 117 |
| 52 | Onafhankelijkheid | 118 |
| 53 | Algemene voorwaarden voor leden van de toezichthoudende autoriteit | 119 |
| 54 | Regels inzake de oprichting van de toezichthoudende autoriteit | 120 |
| 55 | Bevoegdheid | 121 |
| 56 | Bevoegdheid van de leidende toezichthoudende autoriteit | 122 |
| 57 | Taken | 123 |
| 58 | Bevoegdheden | 129 |
| 59 | Activiteitenverslagen | 125 |
| 60 | Samenwerking tussen de leidende toezichthoudende autoriteit en de andere betrokken toezichthoudende autoriteiten | 126 |
| 61 | Wederzijdse bijstand tussen toezichthoudende autoriteiten | 132 |
| 62 | Advies van het Comité | 128 |
| 63 | Coherentiemechanisme | 129 |
| 64 | Advies van het Comité in bepaalde gevallen | 130 |
| 65 | Geschillenbeslechting door het Comité | 131 |
| 66 | Spoedprocedure | 132 |
| 67 | Uitvoeringshandelingen | 133 |
| 68 | Algemene voorwaarden | 134 |
| 69 | Taken van het Comité | 135 |
| 70 | Verslag over de werkzaamheden van het Comité | 136 |
| 71 | Beroepsprocedures | 137 |
| 72 | Sancties | 138 |
| 73 | Specifieke verwerkingsomstandigheden | 139 |
| 74 | Verwerking van persoonsgegevens en vrijheid van meningsuiting | 140 |
| 75 | Verwerking en persoonsgegevensbeveiliging | 141 |
| 76 | Gegevensbeschermingsfunctionaris | 142 |
| 77 | Recht om klacht in te dienen bij een toezichthoudende autoriteit | 143 |
| 78 | Recht op een doeltreffende voorziening in rechte | 144 |
| 79 | Recht op een doeltreffende voorziening in rechte | 141 |
| 80 | Vertegenwoordiging van betrokkenen | 142 |
| 81 | Schorsing van de procedure | 144 |
| 82 | Recht op schadevergoeding en aansprakelijkheid | 146 |
| 83 | Algemene voorwaarden voor het opleggen van administratieve geldboeten | 148 |
| 84 | Sancties | 150 |
| 85 | Verwerking en vrijheid van meningsuiting en informatie | 153 |
| 86 | Verwerking en archivering in het algemeen belang | 152 |
| 87 | Verwerking en nationale identificatienummers | 153 |
| 88 | Verwerking in de context van werkgelegenheid | 154 |
| 89 | Garantievoorwaarden bij verwerking voor archivering in het algemeen belang, wetenschappelijk of historisch onderzoek of statistische doeleinden | 156 |
