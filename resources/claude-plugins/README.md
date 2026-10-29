# ICTRecht Plugin Suite voor Claude

Vier juridische Claude-plugins van ICTRecht, ingedeeld per rol: Privacy Officer, FG, Legal Counsel en Compliance Officer. Publiek beschikbaar op GitHub, gratis, onder CC BY-SA 4.0.

Repository: <https://github.com/ICTRecht/claude-plugin>

## Wat zit erin

| Plugin | Rol | Waarvoor |
|---|---|---|
| `ictrecht-privacy-officer` | Privacy Officer | DPIA, datalekbeoordeling, betrokkenenrechten, doorgifte, grondslag, verwerkersovereenkomsten, verwerkingsregister, data sharing, data governance, AI Act-classificatie |
| `ictrecht-fg` | Functionaris Gegevensbescherming | DPIA- en datalektoetsing, betrokkenencontact, doorgifte- en grondslagadvies, register- en VOK-toetsing, toezichtsplan, AP-contact, jaarverslag |
| `ictrecht-legal-counsel` | Legal Counsel | Contractreview, NDA, algemene voorwaarden, aansprakelijkheid, onderhandeling, SLA, juridische memo's, geschilvoorbereiding, IE (auteursrecht, merken, software-licenties, AI & IP) |
| `ictrecht-compliance-officer` | Compliance Officer | Verwerkingsregister, data sharing, data governance, Data Act, open data, dataverdragen, compliance-check, regelgeving-scan (AI Act, NIS2, DSA, DMA, Cyber Resilience Act) |

Een aantal skills zit bewust in meer dan één plugin, omdat ze voor meerdere rollen relevant zijn: `vok-review`, `risico-analyse`, `verwerkingsregister`, `data-sharing`, `data-governance` en `ai-act-classificatie`.

## Installeren in Claude Code

Marketplace eenmalig toevoegen:

```
/plugin marketplace add https://github.com/ICTRecht/claude-plugin
```

Daarna de plugin die bij je rol hoort:

```
/plugin install ictrecht-privacy-officer@ictrecht-plugins
```

Herstart Claude Code na de installatie.

## Inrichten op de eigen organisatie

Elke plugin heeft een `cold-start-interview` van ongeveer tien minuten dat een organisatieprofiel aanlegt:

```
/ictrecht-privacy-officer:cold-start-interview
```

Dat profiel wordt door alle ICTRecht-plugins herkend, dus het interview hoef je maar één keer te doen. Zonder profiel werken alle commando's ook — de analyses zijn dan generiek.

## Huisstijl

Elke plugin bevat een `SCHRIJFWIJZER.md` met de verplichte ICTRecht-conventies: toon, structuur, de driedeling kritiek punt / risico / aandachtspunt, en opmaak. Elke skill verwijst daar verplicht naar.

## Kennisbank-connector

De plugins werken op de ingebouwde juridische kennis van Claude. Wie analyses wil laten gronden in de actuele ICTRecht-kennisbanken kan de `ictrecht-knowledge-server`-connector toevoegen. Skills detecteren die connector automatisch en werken zonder net zo goed. De connector zit op dit moment in een closed beta; aanvragen via <support@ictrecht.nl>.

## Licentie

CC BY-SA 4.0 — <https://creativecommons.org/licenses/by-sa/4.0/>
