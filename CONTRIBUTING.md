# Contributing to Legal GenAI Resources

Thank you for contributing to the Legal GenAI Resources repository. This guide explains how to add prompts, Skills, templates, plugins, or resources.

---

## Before you start

- All content must relate to legal work under Dutch or European law.
- All contributions must be in **English** (the legal context may reference Dutch/EU law, but instructions should be in English).
- Every item must include a `README.md` with legal context, usage instructions, and known limitations.
- If you want to flag a missing use case without submitting content yourself, open an [issue](https://github.com/ICTRecht/Legal-GenAI-Resources/issues/new/choose).

---

## Content types

### 1. Prompts (`/prompts/`)

A prompt is a one-shot instruction for a specific legal task. The user copies it, pastes it into an LLM, and gets a result.

**Folder structure:**
```
prompts/{category}/{prompt-name}/
├── prompt.md        # or prompt.xml / prompt.json
└── README.md
```

**Branch naming:** `prompt/{descriptive-name}`

**README.md must contain:**
- Purpose and legal context
- Usage instructions (what to include, what to upload)
- Known limitations (what the prompt does NOT handle well)
- Example output (optional but strongly encouraged)

---

### 2. Skills (`/skills/`)

A Skill is a reusable system prompt that configures Claude to behave consistently as a legal specialist throughout a session.

**Folder structure:**
```
skills/{skill-name}/
├── skill.md          # The system prompt / instruction set
├── README.md         # Purpose, legal context, compatible models, limitations
├── example_output.md # Real or illustrative output
└── metadata.json     # Model version, validated by, date, regulation version, status
```

**Branch naming:** `skill/{descriptive-name}`

**metadata.json format:**
```json
{
  "model": "claude-opus-4-7",
  "validated_by": "ICTRecht",
  "validation_date": "YYYY-MM-DD",
  "regulation_version": "e.g. GDPR as of 2024",
  "status": "draft | reviewed | production"
}
```

---

### 3. Templates (`/templates/`)

A template is a GRC document (DPIA, checklist, risk register, processor agreement) that AI can help complete or review.

**Folder structure:**
```
templates/{regulation}/{template-name}/
├── template.md       # or template.docx / template.xlsx
└── README.md
```

**Branch naming:** `template/{descriptive-name}`

**Regulation subfolders:** `gdpr/`, `ai-act/`, `nis2/`, `general/`

---

### 4. Plugins (`/plugins/`)

A plugin is an integration that lets Claude reach an external system (rechtspraak.nl, EUR-Lex, etc.).

**Folder structure:**
```
plugins/{plugin-name}/
├── README.md         # What the plugin does, setup instructions
├── plugin.json       # Plugin manifest
└── ...               # Integration files
```

**Branch naming:** `plugin/{descriptive-name}`

Plugins require technical review before merging. Please open an issue first to discuss the integration approach.

---

### 5. Resources (`/resources/`)

A resource is a curated reference to an external source, dataset, API, or tooling relevant to Legal AI.

**File:** add an entry to the relevant `README.md` in `/resources/` or create a new `.md` file.

**Branch naming:** `resource/{descriptive-name}`

---

## Submission process

### 1. Fork & clone

```bash
git clone {url of your fork}
```

### 2. Create a branch

Use the naming convention for your content type:

```bash
git checkout -b prompt/nda-checker
# or: skill/contract-reviewer
# or: template/dpia-gdpr
```

### 3. Add your content

Follow the folder structure and README requirements above.

### 4. Open a Pull Request

Go to [GitHub](https://github.com/ICTRecht/Legal-GenAI-Resources) and open a PR from your branch to `main`. Use the appropriate issue template.

### 5. Review

The ICTRecht team will review for legal accuracy, format compliance, and quality. We may suggest changes before merging.

---

## Quality standards

| Requirement | Prompts | Skills | Templates | Plugins |
|---|---|---|---|---|
| English language | Required | Required | Required | Required |
| Legal context in README | Required | Required | Required | Required |
| Known limitations documented | Required | Required | Required | Required |
| Example output | Encouraged | Required | Encouraged | Required |
| metadata.json | No | Required | No | Required |
| ICTRecht review | Standard | Full review | Standard | Full review |

---

## ICTRecht Verified label

Content that has been validated in actual legal practice by ICTRecht lawyers receives the **ICTRecht Verified** label in its README. This is applied by the ICTRecht team, not by contributors.

---

Thank you for helping build the leading open-source Legal AI resource platform.
