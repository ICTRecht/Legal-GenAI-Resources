## ✍️ Bijdragen
Wil je bijdragen aan dit project? Volg dan deze stappen om je wijzigingen correct in te dienen:

### 1. Fork & Clone
Fork deze repository en clone je fork naar je lokale omgeving.

```bash
git clone {url van je fork}
cd prompts
```

### 2. Maak een feature branch
Werk nooit direct in `main`. Maak een nieuwe branch gebaseerd op `main`:

```bash
git checkout main
git pull origin main  # Zorg dat je up-to-date bent
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
2. Open een **Pull Request** van jouw `prompt/{naam-van-je-prompt}` branch naar de `main` branch.
3. Voeg een duidelijke beschrijving toe van je wijziging.

### 5. Review en Merge
- Het team zal je PR beoordelen en eventueel feedback geven.
- Zodra goedgekeurd, wordt de wijziging gemerged in `main`.
- Het team kan nog mogelijk optimalisaties uitvoereen aan de prompts, waarna wijzigingen ook op de `main` branch zullen worden gepubliceerd.

### 6. Synchroniseer je lokale repo
Na het mergen, houd je lokale repository up-to-date:

```bash
git checkout main
git pull origin main
git branch -d prompt/{naam-van-je-prompt}  # Verwijder de feature branch lokaal
```

**Dank voor je bijdrage!**
