## 🔧 Promptverbeteraar: Wijzigingen aanbrengen met Track Changes (Word)

### Doel
Deze aanvulling zorgt ervoor dat alle inhoudelijke wijzigingen die het taalmodel aanbrengt in een aangeleverd Word-document (.docx) **zichtbaar en fijnmazig worden vastgelegd als Track Changes**, zonder duplicatie van tekst of vervanging van volledige alinea’s.

### Toepassing
Gebruik deze promptverbeteraar naast of onderaan een bestaande prompt die het model vraagt om tekst te wijzigen, herschrijven, corrigeren of redigeren in een Word-document.

### Instructie aan het model
Wanneer de gebruiker een Word-document (.docx) uploadt en vraagt om wijzigingen:

1. **Behandel het .docx-bestand als een ZIP-archief**
   - Pak het document uit volgens de standaard Office Open XML-structuur.
   - Werk uitsluitend binnen de bestaande structuur (met name `word/document.xml`, en indien relevant headers/footers).

2. **Gebruik Track Changes op XML-niveau**
   - Overschrijf bestaande tekst nooit direct.
   - Leg elke wijziging vast via Track Changes door:
     - oorspronkelijke tekst te markeren als verwijdering (`w:del`);
     - nieuwe tekst toe te voegen als invoeging (`w:ins`).
   - Voorzie wijzigingen van een auteur en datum/tijd (ISO-formaat is voldoende).

3. **Werk binnen bestaande alinea’s**
   - Gebruik bestaande alinea’s (`w:p`) als uitgangspunt.
   - Vervang geen volledige alinea’s en voeg geen nieuwe alinea’s toe als vervanging, tenzij dit expliciet is gevraagd.

4. **Pas een inhoudelijke vergelijking toe (inline diff)**
   - Vergelijk de oorspronkelijke tekst met de beoogde nieuwe tekst.
   - Bepaal per woord of zinsdeel wat:
     - ongewijzigd blijft (laat deze tekst intact);
     - wordt verwijderd (markeer als `w:del`);
     - wordt toegevoegd (markeer als `w:ins`).

5. **Minimaliseer en lokaliseer wijzigingen**
   - Breng wijzigingen zo fijnmazig mogelijk aan (woord- of zinsdeel-niveau).
   - Voorkom het verwijderen en opnieuw invoegen van volledige zinnen of alinea’s als slechts een deel wijzigt.
   - Combineer meerdere woorden in één wijziging alleen als dit technisch noodzakelijk is.

6. **Behoud structuur en leesbaarheid**
   - Laat opmaak, stijlen, volgorde, interpunctie en witruimte intact waar mogelijk.
   - Wijzig geen metadata, stijlen of sectie-indelingen tenzij expliciet gevraagd.
   - De Track Changes-weergave moet logisch en goed leesbaar zijn voor een menselijke gebruiker.

7. **Pak het document opnieuw in**
   - Herpak de aangepaste XML-structuur tot een geldig `.docx`-bestand.
   - Lever het resultaat aan als downloadbaar Word-document.

### Resultaatvereisten
De gebruiker moet in Word:
- alle wijzigingen kunnen zien via *Wijzigingen bijhouden*;
- wijzigingen kunnen accepteren of weigeren;
- de auteur van de wijziging kunnen herkennen.

### Belangrijke beperkingen
- Geef geen tekstuele suggesties buiten Track Changes om.
- Voeg geen commentaar of toelichtingen toe in het document zelf, tenzij expliciet gevraagd.
- Als Track Changes technisch niet mogelijk zijn, meld dit vooraf en voer geen stilzwijgende wijzigingen door.

### Samenvattend
> *Voer de gevraagde inhoudelijke wijzigingen door binnen bestaande alinea’s, op basis van een minimale inhoudelijke diff, en materialiseer uitsluitend de daadwerkelijke verschillen als Track Changes op XML-niveau in het Word-document.*
