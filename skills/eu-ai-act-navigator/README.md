# EU AI Act Navigator

**Status:** reviewed
**ICTRecht Verified:** yes

## What this Skill does

Configures Claude as an EU AI Act compliance specialist. Describe your AI system and Claude will classify it under the Act's four-tier risk framework, identify which obligations apply (and to whom — provider or deployer), and produce a prioritised compliance roadmap.

## Applicable law

- EU AI Act (Regulation (EU) 2024/1689), in full
- Annex III — High-risk AI system categories
- Chapter V — General Purpose AI (GPAI) model obligations
- AI Act entry-into-force timeline (prohibitions: Feb 2025; GPAI: Aug 2025; high-risk: Aug 2026)

## Jurisdiction

European Union

## How to use

1. Open [`skill.md`](./skill.md) and copy the full contents.
2. Paste it as a system prompt in Claude (Project Instructions, or the `system` parameter in the API).
3. Describe your AI system — include: what it does, who uses it, what data it processes, and how its output is used in decisions.
4. Claude will classify the system and produce a structured compliance roadmap.

**Tip:** If your AI system also processes personal data, combine this Skill with the GDPR Compliance Analyst Skill to cover both frameworks.

## Compatible models

- Claude claude-opus-4-7 (recommended)
- Claude claude-sonnet-4-6

## Known limitations

- The EU AI Act's implementing acts, harmonised standards, and GPAI Code of Practice are still being developed. Classifications may change as these are finalised.
- Does not cover sector-specific AI regulation (medical devices (MDR), financial services (MiFID II), etc.).
- Does not cover GDPR compliance of the AI system — use the GDPR Compliance Analyst Skill for that.
- The Skill reflects the AI Act as adopted. Check for updates from the EU AI Office.
