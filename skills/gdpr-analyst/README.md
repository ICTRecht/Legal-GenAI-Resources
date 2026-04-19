# GDPR Compliance Analyst

**Status:** reviewed
**ICTRecht Verified:** yes

## What this Skill does

Configures Claude as a GDPR compliance analyst. Provide a document, system description, privacy notice, or processing activity description — Claude will systematically review it against the GDPR and the Dutch UAVG, identify compliance gaps, and produce a prioritised gap analysis.

## Applicable law

- GDPR (Regulation (EU) 2016/679), all chapters
- Dutch UAVG (Uitvoeringswet AVG)
- EDPB Opinion 28/2024 on AI models (for AI-related processing)
- AP (Dutch DPA) positions on generative AI

## Jurisdiction

Netherlands / European Union

## How to use

1. Open [`skill.md`](./skill.md) and copy the full contents.
2. Paste it as a system prompt in Claude (Project Instructions, or the `system` parameter in the API).
3. Provide the document or processing description you want reviewed.
4. Claude will produce a structured gap analysis referencing specific GDPR articles.

**Tip:** For DPIA assistance, combine this Skill with the DPIA Assistant prompt in [`/prompts/juridisch/privacy/dpia_assistant/`](../../prompts/juridisch/privacy/dpia_assistant/).

## Compatible models

- Claude claude-opus-4-7 (recommended for comprehensive analysis)
- Claude claude-sonnet-4-6 (suitable for shorter documents)

## Known limitations

- Does not replace a qualified DPO or privacy lawyer.
- ePrivacy / cookie compliance is out of scope — use a dedicated cookie consent tool.
- NIS2 cybersecurity requirements are out of scope.
- Non-EU privacy laws (CCPA, UK GDPR post-Brexit) require jurisdiction-specific review.
- Very complex processing activities (e.g. large-scale profiling systems) may require iterative review by processing purpose.
