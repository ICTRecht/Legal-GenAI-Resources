# System-Behavior Optimizer Prompt
Dit document legt uit hoe je de **System-Behavior Optimizer prompt** gebruikt om hallucinaties te beperken, feitelijke nauwkeurigheid af te dwingen en de betrouwbaarheid van ChatGPT of vergelijkbare LLM’s te verbeteren.  
De optimizer zet een “RAW_PROMPT” om in een **strikte, minimale en duurzame instructie** die het model aanstuurt tot hoog-nauwkeurig gedrag.

## 🎯 Doel
Grote taalmodellen zijn krachtig maar gevoelig voor hallucinaties wanneer informatie ontbreekt, onduidelijk is of wordt aangenomen.  
Deze prompt creëert een **gedragscontract** dat het model verplicht om:
- Alleen verifieerbare feiten te geven  
- Onzekerheid te erkennen (“Ik weet het niet”)  
- Gerichte vervolgvragen te stellen bij onduidelijkheid  
- Niet te raden of te fabriceren  
- Antwoorden vooraf te controleren op fouten en aannames  

Het resultaat is aanzienlijk betrouwbaardere output, vooral in juridische, technische en compliance-contexten.

## 🧩 Hoe het werkt
De template fungeert als een *system-level instructie*.  
Wanneer je een RAW_PROMPT aanlevert, doet het model het volgende:

1. Leest de acceptatiecriteria  
2. Vat de gedragsregels samen tot een compacte instructie  
3. Produceert één sectie: **Final Instruction**  
4. Past alle beperkingen toe (≤80 woorden, eenvoudige taal, geen meta-opmerkingen)  
5. Levert een duurzame gedragsregel die als systeemprompt kan worden hergebruikt  

Deze regel fungeert als een herbruikbare veiligheidslaag rond elke instructieset die je wilt optimaliseren.

## 🚀 Gebruiksaanwijzing
### 1. Lever de prompt aan  
Plak de volledige structuur in het personaliseringveld onder de instellingen of het eerste bericht van een nieuw gesprek.

### 2. Voeg je RAW_PROMPT toe  
Vervang de placeholder door de instructies die je wilt opschonen, verscherpen of stabiliseren.

### 3. Ontvang de “Final Instruction”  
Het model genereert een korte, strikte gedragsregel (max. 80 woorden) die je kunt:
- Gebruik als zelfstandige systeemprompt  
- Inbouwen in API-aanroepen  
- Toepassen in agents en workflows  
- Opslaan als duurzame instructie voor herhaald gebruik  

### 4. Gebruik de Final Instruction in productie  
Deze beknopte regel vormt een **vaste systeemguardrail** voor situaties waarin nauwkeurigheid cruciaal is.

## 🧪 Tips voor optimaal gebruik
- Gebruik de verfijnde instructie bij voorkeur als **system-prompt**  
- Combineer met domeinspecifieke regels voor maximale betrouwbaarheid  
- Run de optimizer opnieuw wanneer interne richtlijnen wijzigen  
- Getest en bruikbaar met GPT, Claude, Gemini en andere moderne LLM’s  

## ⚠ Beperkingen
- Geen prompt kan hallucinaties volledig uitsluiten  
- Het model zal vaker “Ik weet het niet” antwoorden — dit is gewenst gedrag  
- Instructies langer dan 80 woorden worden ingekort of moeten worden herschreven  

## 🛡 Best practice
Combineer de verfijnde gedragsregel met domeinspecifieke instructies, zoals:

> “Bij juridische vragen: verwijs alleen naar gecodificeerde bronnen of benoem expliciet waar ambiguïteit bestaat.”

Dit vergroot de betrouwbaarheid sterk in professionele contexten.

## 📄 Voorbeeldworkflow
1. Schrijf een ruwe of rommelige initiële instructieset  
2. Voer deze door de System-Behavior Optimizer  
3. Ontvang de compacte Final Instruction  
4. Gebruik die als nieuwe system-prompt  
5. Stel vervolgens normale vragen — met minder hallucinaties en hogere nauwkeurigheid  

## 💬 Ondersteuning
Deze repository kan desgewenst worden uitgebreid met:
- Een striktere of mildere variant van de optimizer  
- Voorbeeld-RAW_PROMPT-templates  
- Een versie die aansluit op interne richtlijnen van jouw organisatie  
- Voorbeelden of logs van voorbeeldconversaties  

Open een issue of neem contact op voor uitbreidingen.
