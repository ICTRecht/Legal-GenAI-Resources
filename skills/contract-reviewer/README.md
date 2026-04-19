# Legal Contract Reviewer

**Status:** reviewed
**ICTRecht Verified:** yes

## What this Skill does

Configures Claude as a specialist contract reviewer operating under Dutch and EU law. Upload a contract and Claude will review it clause by clause, flag red flags, identify missing standard clauses, and produce a structured annotation — ready for lawyer review.

## Applicable law

- Dutch contract law (Burgerlijk Wetboek, Book 6)
- EU Unfair Contract Terms Directive (93/13/EEC) — for consumer contracts
- GDPR (Regulation (EU) 2016/679) — for data processing clauses
- General Dutch commercial contracting practice

## Jurisdiction

Netherlands / European Union

## How to use

1. Open [`skill.md`](./skill.md) and copy the full contents.
2. Paste it as a system prompt in Claude:
   - In Claude.ai: open or create a Project, paste in **Project Instructions**
   - Via API: use as the `system` parameter
3. Upload the contract you want reviewed (PDF, Word, or paste the text).
4. Ask Claude to review it — no further prompt needed. The Skill will structure the output automatically.

## Compatible models

- Claude claude-opus-4-7 (recommended)
- Claude claude-sonnet-4-6
- GPT-4o (may require minor prompt adjustments)

## Known limitations

- Does not replace a lawyer. Flags issues for human review — not a substitute for legal advice.
- Optimised for Dutch and EU law. Contracts governed by UK, US, or other non-EU law require jurisdiction-specific review.
- Complex multi-party agreements or consortium contracts may require iterative review (one contract section at a time).
- Does not generate redlines or tracked-changes output — use the structured annotation to guide a lawyer or drafting tool.
- AI models have a context window limit. Very long contracts (>100 pages) should be reviewed in sections.

## See also

- [`/prompts/juridisch/contracten/contract_review/`](../../prompts/juridisch/contracten/contract_review/) — one-shot prompts for specific contract types (NDA, DPA, copyright transfer)
- [`/templates/gdpr/`](../../templates/gdpr/) — GDPR-related contract templates
