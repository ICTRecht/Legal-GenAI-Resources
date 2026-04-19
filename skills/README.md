# Skills

Claude Skills are reusable instruction sets that configure Claude as a legal specialist for an entire session. Unlike a one-shot prompt, a Skill persists — it determines how Claude reasons, what output format it uses, and what legal standards it applies throughout the conversation.

## How to use a Skill

1. Open the Skill folder and read the `README.md` for context, model compatibility, and limitations.
2. Copy the contents of `skill.md`.
3. Paste it as a system prompt in Claude (Project Instructions, or the system prompt field in the API).
4. Start your session — Claude now behaves as the configured specialist.

## Available Skills

| Skill | Description | Status |
|---|---|---|
| *Coming soon* | | |

## Skill format

Every Skill follows this structure:

```
skills/{skill-name}/
├── skill.md          # The system prompt / instruction set
├── README.md         # Purpose, legal context, compatible models, limitations
├── example_output.md # Real or illustrative output example
└── metadata.json     # Model version, validated by, date, regulation version, status
```

## Contributing a Skill

See [CONTRIBUTING.md](../CONTRIBUTING.md) for the full format requirements and submission process.
