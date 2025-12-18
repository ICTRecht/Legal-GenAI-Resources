# ✏️ Promptverbeteraar: Track Changes met Inline Wijzigingen (Word)
## 🎯 Doel van deze promptverbeteraar
Deze promptverbeteraar maakt het mogelijk om **inhoudelijke wijzigingen in een aangeleverd Word-document (.docx) automatisch en fijnmazig vast te leggen als Track Changes**.

In tegenstelling tot eenvoudige revisies (waarbij hele alinea’s worden vervangen of gedupliceerd), zorgt deze aanvulling ervoor dat:
- wijzigingen **binnen bestaande alinea’s** worden aangebracht;
- **ongewijzigde woorden en zinsdelen intact blijven**;
- alleen daadwerkelijke verschillen zichtbaar worden als Track Changes.

Het resultaat benadert het revisiegedrag van een menselijke redacteur of jurist.


## 🧠 Wat deze promptverbeteraar doet
Wanneer deze promptverbeteraar wordt gebruikt in combinatie met een bestaande prompt en een Word-document:

- Het `.docx`-bestand wordt behandeld als een ZIP-archief met Office Open XML-structuur;
- De inhoud wordt aangepast op XML-niveau;
- Wijzigingen worden vastgelegd via:
  - `w:del` (verwijderingen);
  - `w:ins` (invoegingen);
- Wijzigingen worden **zo lokaal en minimaal mogelijk** toegepast (woord- of zinsdeel-niveau);
- De oorspronkelijke structuur, opmaak en leesbaarheid blijven behouden.


## 📝 Wanneer gebruik je deze promptverbeteraar?
Deze aanvulling is geschikt voor prompts die onder meer:

- teksten herschrijven of redigeren;
- juridische formuleringen aanscherpen;
- namen, definities of termen aanpassen;
- feedback verwerken in bestaande documenten;
- consistentie- of stijlcorrecties doorvoeren.

Met name in juridische, beleidsmatige en redactionele contexten waarin **transparantie en controle over wijzigingen** essentieel zijn.


## ⚙️ Instructies voor gebruik
1. Neem een bestaande prompt die wijzigingen aanbrengt in tekst.
2. Voeg deze promptverbeteraar **ongewijzigd** toe aan die prompt (bij voorkeur onderaan).
3. Upload samen met de prompt het Word-document (`.docx`).
4. Vraag expliciet om uitvoering van de prompt.

De output is een aangepast Word-document waarin alle wijzigingen zichtbaar zijn via *Wijzigingen bijhouden*.


## 📌 Belangrijke uitgangspunten
- Wijzigingen worden **niet stilzwijgend** doorgevoerd.
- Bestaande alinea’s worden aangepast, niet vervangen.
- Ongewijzigde tekst blijft onaangeroerd.
- Alleen gevraagde inhoudelijke wijzigingen worden verwerkt.
- Er worden geen opmerkingen of toelichtingen toegevoegd in het document, tenzij expliciet gevraagd.


## ⚠️ Beperkingen
- Deze promptverbeteraar is specifiek bedoeld voor Word-documenten (`.docx`).
- Andere formaten (zoals PDF of Google Docs) vallen buiten scope.
- Als Track Changes technisch niet correct kan worden toegepast, moet het model dit vooraf melden en geen wijzigingen doorvoeren.


## ✅ Resultaat
De gebruiker ontvangt een Word-document waarin:
- alle wijzigingen zichtbaar zijn als Track Changes;
- wijzigingen eenvoudig kunnen worden geaccepteerd of geweigerd;
- de auteur van de wijziging herkenbaar is;
- geen duplicatie van tekst of alinea’s optreedt.


