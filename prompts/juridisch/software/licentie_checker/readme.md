📌 Overzicht
Deze prompt voert een technische-juridische analyse uit van open-source-licenties in een codebasis, met als doel publieke verspreiding (bijv. GitHub, binaries, SaaS) veilig te laten verlopen.

🚀 Hoe gebruik je het?
1. Kies invoeroptie **A** (Git-repository) of **B** (losse bestanden / metadata).
2. Vul de gevraagde gegevens in (repository-URL + token/submodules of bestandslijst + licentie-/manifestinhoud).
3. Kopieer de XML-prompt naar een LLM naar keuze. Deze prompt is wel het **beste getest met het *o3*-model in ChatGPT**.

🛠 Aanpassingen
* Pas de inputvelden aan (bijvoorbeeld extra manifest- of asset-types) door in de prompt de `<inputChoices>` te wijzigen.
* Wijzig analyse- of labelstappen (stap 1–5) door teksten in `<analysisRequest>` aan te passen of extra sub-taken toe te voegen.
* Stem het uitvoerformaat af op je behoeften: wijzig `<outputFormat>` naar Markdown, JSON of ander gewenst format.
* Test na elke wijziging of de AI nog de juiste outputstructuur levert.

📖 Voorwaarden
* Deze prompt biedt een technische-juridische analyse, géén bindend juridisch advies.
* Controleer altijd de output nauwkeurig en schakel zo nodig een IT-jurist in.
* Houd rekening met specifieke bedrijfs- of projectvereisten voordat je definitief publiceert.
