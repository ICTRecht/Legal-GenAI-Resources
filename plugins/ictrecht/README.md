# ICTRecht Plugin

De ICTRecht Plugin is een interne AI-plugin voor Claude Cowork die juridische analyses uitvoert op basis van:

- ICTRecht playbooks  
- ICTRecht Risk Rubric  
- ICTRecht clausulebibliotheek  

De plugin ondersteunt gestructureerde contractbeoordeling en risicoclassificatie volgens de interne methodiek van ICTRecht.

> Deze plugin ondersteunt juridische analyse en vervangt geen professionele beoordeling.

---

# Installatie

De plugin kan op twee manieren worden toegevoegd in Claude Cowork.

---

## Optie 1 — Installatie via GitHub (aanbevolen)

Geschikt voor centrale distributie en automatische updates.

### Stap 1
Open Claude → **Plugins**

### Stap 2
Klik op **+** → kies **Add marketplace from GitHub**

### Stap 3
Voer de repository in:

ICTRecht/Legal-GenAI-Resources


Claude detecteert automatisch beschikbare plugins in de repository.

### Stap 4
Selecteer:

ictrecht


Klik op **Add** en activeer de plugin via de toggle.

### Voorwaarden

De repository moet:
- Publiek zijn  
  of  
- Toegankelijk zijn voor de GitHub-account waarmee Claude is verbonden  

De plugin moet zich bevinden in:

plugins/ictrecht/.claude-plugin/plugin.json


---

## Optie 2 — Installatie via Upload (lokale installatie)

Geschikt voor testen of wanneer GitHub-koppeling niet beschikbaar is.

### Stap 1
Open Claude → **Plugins**

### Stap 2
Klik op **+**

### Stap 3
Kies: **Upload plugin**

### Stap 4
Selecteer de volledige map:

plugins/ictrecht


Belangrijk: upload de volledige directory waarin zich bevindt:

.claude-plugin/plugin.json


Niet alleen het JSON-bestand.

### Stap 5
Activeer de plugin via de toggle.

---

# Structuur

```
/
plugins/ictrecht/
├── .claude-plugin/
│ └── plugin.json
├── .mcp.json
├── knowledge/
├── playbooks/
├── skills/
└── commands/

```

---

# Architectuur

- **Playbooks** → Inhoudelijke ICTRecht-standaarden  
- **Risk Rubric** → Gestandaardiseerde risicobeoordeling  
- **Clausulebibliotheek** → Preferred + fallback clausules  
- **Skills** → Workflowlogica  
- **Commands** → Interface binnen Claude  

---

Indien gewenst kan deze README later worden uitgebreid met workflows, voorbeelden en interne richtlijnen.
