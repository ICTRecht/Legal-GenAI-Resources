# Legal GenAI Resources

**The open-source Legal AI resource platform by [ICTRecht](https://ictrecht.nl)**

> Curated prompts, Claude Skills, GRC templates, and legal data integrations — built by lawyers, validated in practice, free to use.

[![ICTRecht Verified](https://img.shields.io/badge/ICTRecht-Verified-blue)](https://ictrecht.nl)
[![License](https://img.shields.io/github/license/ICTRecht/Legal-GenAI-Resources)](LICENSE.md)
[![Contributions Welcome](https://img.shields.io/badge/contributions-welcome-brightgreen)](CONTRIBUTING.md)

---

## What is this?

This repository is a growing platform of Legal AI resources for lawyers, compliance professionals, and legal tech practitioners. Every resource is grounded in Dutch and European law and validated by ICTRecht's legal team.

We cover five layers:

| Layer | What it is | Folder |
|---|---|---|
| **Prompts** | One-shot instructions for a specific legal task. Copy, paste, use. | [`/prompts/`](./prompts/) |
| **Skills** | Reusable instruction sets that give Claude persistent, structured behaviour — system prompts, personas, workflows. | [`/skills/`](./skills/) |
| **Templates** | GRC documents for AI-assisted completion or review: DPIAs, AI Act checklists, processor agreements, risk registers. | [`/templates/`](./templates/) |
| **Plugins** | Integrations that let Claude reach external systems: rechtspraak.nl, EUR-Lex, knowledge bases, document management. | [`/plugins/`](./plugins/) |
| **Resources** | References to external sources, datasets, research, and tooling. | [`/resources/`](./resources/) |

---

## Why ICTRecht?

ICTRecht is a Dutch law firm specialising in IT law, privacy, and digital regulations since 2004. Our team of lawyers uses these resources daily. The **ICTRecht Verified** label marks content that has been reviewed and tested in actual legal practice — something no other Legal AI GitHub repository offers.

---

## Quick start

### Using a prompt

1. Navigate to [`/prompts/`](./prompts/) and find a prompt for your task.
2. Open the `README.md` in the prompt folder to understand the context and limitations.
3. Copy the prompt content and paste it into Claude, ChatGPT, or your preferred LLM.

### Using a Skill

1. Navigate to [`/skills/`](./skills/) and choose a Skill.
2. Read the `README.md` to understand the Skill's purpose, compatible models, and known limitations.
3. Use `skill.md` as a system prompt to configure Claude for the session.

### Using a template

1. Navigate to [`/templates/`](./templates/) and select the relevant regulation folder.
2. Follow the instructions in the template's `README.md`.

---

## Repository structure

```
Legal-GenAI-Resources/
├── prompts/          # One-shot prompts per legal task
│   ├── contracts/
│   ├── privacy/
│   ├── litigation/
│   └── general/
├── skills/           # Reusable Claude instruction sets and personas
│   ├── contract-reviewer/
│   ├── gdpr-analyst/
│   └── ...
├── templates/        # GRC documents and compliance templates
│   ├── gdpr/
│   ├── ai-act/
│   └── nis2/
├── plugins/          # Integrations with external legal data sources
│   └── ictrecht/
├── resources/        # External sources, research, tooling references
└── CONTRIBUTING.md
```

---

## Highlighted resources

### Prompts
- **NDA Checker** — Reviews an NDA against standard Dutch clauses and flags deviations
- **DPA Checker** — Checks a Data Processing Agreement for GDPR compliance
- **DPIA Assistant** — Guides you through a Data Protection Impact Assessment
- **Contract Risk Manager** — Identifies risk clauses in commercial contracts
- **Judgment Summariser** — Summarises Dutch court rulings (rechtspraak.nl)

### Skills *(coming soon)*
- Legal Contract Reviewer
- GDPR Compliance Analyst
- EU AI Act Navigator
- NIS2 Checklist Assistant

### Templates *(coming soon)*
- DPIA template (GDPR)
- AI system classification checklist (EU AI Act)
- Processor agreement template
- Risk register

---

## Contributing

We welcome contributions from the legal and legal tech community. Please read [CONTRIBUTING.md](./CONTRIBUTING.md) before submitting.

Every contribution must include:
- A clear description of the legal context (applicable regulation, jurisdiction)
- An example output showing what the resource produces
- Explicit limitations (what it does *not* handle well)

---

## For Dutch users

*Voor Nederlandstalige gebruikers:* De juridische context van alle resources is gericht op het Nederlandse en Europese recht. De instructies zijn in het Engels geschreven omdat dit de kwaliteit en consistentie van AI-output verbetert en de vindbaarheid voor de internationale community vergroot. Je kunt Engelstalige prompts en Skills zonder moeite gebruiken in een Nederlandstalige workflow.

---

## ICTRecht publications on Legal AI

- [Factsheet: 'De kunst van het prompten'](https://www.ictrecht.nl/hubfs/AI-onderzoek%202025/Factsheet%20prompttrucs%20voor%20juristen.pdf)
- [Research: 'Kun je AI vertrouwen voor juridisch werk?'](https://www.ictrecht.nl/hubfs/AI-onderzoek%202025/AI-onderzoek%202025.pdf)
- [Research: 'AI tooling voor de juridische professional'](https://www.ictrecht.nl/hubfs/Kennisdocumenten/Onderzoek/AI-tooling%20voor%20de%20legal%20professionals/Onderzoek%20AI-tooling%20voor%20de%20legal%20professionals.pdf)
- [Factsheet: 'Richtlijnen gebruik LLMs'](https://www.ictrecht.nl/hubfs/Kennisdocumenten/Richtlijnen/ICTRECHT%20ChatGPT%20Richtlijnen.pdf)

---

## License

[MIT License](LICENSE.md) — free to use, adapt, and redistribute with attribution.

---

## About ICTRecht

[ICTRecht](https://ictrecht.nl) is a leading Dutch law firm in IT law, privacy, and digital compliance. We advise organisations on GDPR, the EU AI Act, NIS2, software contracts, and more. This repository is our contribution to the Legal AI community.

- Website: [ictrecht.nl](https://ictrecht.nl)
- LinkedIn: [ICTRecht](https://www.linkedin.com/company/ictrecht/)
