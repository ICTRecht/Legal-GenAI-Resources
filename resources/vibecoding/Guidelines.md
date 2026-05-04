# The Vibe Coding Handbook

> A practical playbook for building real software by describing what you want — not by writing every line yourself.

**What this is.** A working guide to the craft of *vibe coding*: directing AI coding agents to build small, focused tools that solve real problems. The principles are tool-agnostic. The examples cover the five tools most people are choosing from in 2026: **Claude Code, Cursor, Lovable, Google Antigravity, and OpenAI Codex**.

**Who it's for.** Anyone who can describe what they want clearly but doesn't want to (or can't) write every line of code themselves. Founders prototyping. Designers building real interactivity. Lawyers automating their own workflows. Researchers wrangling data. Engineers who want leverage. Curious people who got told "you'd need a developer for that" once too often.

**What it's not.** A tutorial on any specific framework or language. A list of prompts to copy-paste. A buy-it-now product comparison. The patterns here outlive specific tools — they'll still apply when whatever's hot in 2027 ships.

> **Brand new to all this?** If words like *terminal*, *CLI*, *IDE*, *repo* feel like noise, skim the [Glossary](#19-glossary-terms-and-acronyms) first or read sections 1–3 with it open in another tab. Section 2 in particular gives you the foundation everything else builds on.

---

## Table of contents

**Start here**

1. [What "vibe coding" actually means in 2026](#1-what-vibe-coding-actually-means-in-2026)
2. [How software is organised: folders, files, projects](#2-how-software-is-organised-folders-files-projects)
3. [The mental model: it's not a chatbot](#3-the-mental-model-its-not-a-chatbot)
4. [Picking your tool](#4-picking-your-tool)
5. [What you can actually build](#5-what-you-can-actually-build)
6. [Setup, by tool](#6-setup-by-tool)
7. [Your first 30 minutes: a Claude Code Desktop walkthrough](#7-your-first-30-minutes-a-claude-code-desktop-walkthrough)

**The fundamentals**

8. [Persistent instructions: the highest-leverage configuration](#8-persistent-instructions-the-highest-leverage-configuration)
9. [The core workflow: Explore → Plan → Build → Verify](#9-the-core-workflow-explore--plan--build--verify)
10. [Prompting patterns that work](#10-prompting-patterns-that-work)
11. [Context is the resource: managing it ruthlessly](#11-context-is-the-resource-managing-it-ruthlessly)

**Going deeper** *(safe to skip on first read)*

12. [Skills, agents, rules, commands: when to use which](#12-skills-agents-rules-commands-when-to-use-which)
13. [Ten patterns that recur in real projects](#13-ten-patterns-that-recur-in-real-projects)
14. [Verification: how to trust what you didn't write](#14-verification-how-to-trust-what-you-didnt-write)
15. [Failure modes, and recognising them early](#15-failure-modes-and-recognising-them-early)
16. [Going further: parallel sessions, automation, MCP](#16-going-further-parallel-sessions-automation-mcp)

**Reference**

17. [A reference project structure](#17-a-reference-project-structure)
18. [Resources](#18-resources)
19. [Glossary: terms and acronyms](#19-glossary-terms-and-acronyms)

---

## 1. What "vibe coding" actually means in 2026

The term "vibe coding" was coined in early 2025 to describe a shift in how software gets made. Instead of typing every line of code yourself, you describe the *intent* and *feel* of what you want, and an AI agent figures out the implementation. You stay in the driver's seat — directing, reviewing, redirecting — but the agent does most of the typing.

A year later, this stopped being a meme and became a real working methodology. Tens of thousands of small tools, internal apps, prototypes, and even production products are now being built this way every week. The tooling has matured into a recognisable category: AI coding agents that can read your project, edit multiple files, run commands, test their own work, and iterate.

What hasn't changed: **the people getting good results have specific habits**. The ones getting bad results — endless loops, broken builds, half-working prototypes that crash in production — are usually missing the same handful of fundamentals.

This guide is about those fundamentals. The rest is about which tool you point them at.

---

## 2. How software is organised: folders, files, projects

If you've never written software, this section gives you the model everything else in this guide assumes. Five minutes of reading; saves an hour of confusion later.

### A project is just a folder

Every piece of software you'll build with these tools lives in one folder on your computer (or, with Lovable, on a server somewhere). That folder is the project. Inside it: text files, sub-folders, configuration, sometimes data. That's the whole thing.

When this guide says "your project," "your repo," "your workspace," or "your codebase" — those are all words for *the folder*. Different traditions, same thing. (A *repo* is technically a folder under version control with `git`. In practice, treat the words as interchangeable until you have a reason not to.)

### Files have meaning by convention

A web project might have an `index.html` (the homepage), some `.css` files (styling), some `.js` files (interactivity), and a `package.json` (which lists the project's dependencies). The names matter — tools and frameworks expect specific filenames in specific places. You don't need to memorise these; the AI agent knows them. You just need to know that *the names aren't arbitrary*.

A few file extensions you'll see throughout this guide:

- `.md` — markdown. Plain text with light formatting. Used for documentation and instructions to the agent.
- `.json` / `.yaml` — structured data. Used for configuration.
- `.html` / `.css` / `.js` / `.ts` — the building blocks of web apps.
- `.py` — Python, popular for scripts and data work.

You don't need to know any of these languages to vibe code. The agent writes them; you read the output and judge whether it works.

### One folder per thing

The best mental model: **one folder for each separate tool, app, or project you're working on.** Don't pile everything into one giant folder. When you start a new project, you start a new folder.

Inside a typical folder you'll find a mix of:

- **Inputs** — the data you want to process, or the source material you're working with.
- **Reference material** — your style guide, your playbook, your standards. The "rules" the agent should follow.
- **Configuration** — instructions for the agent (a `CLAUDE.md` file or equivalent), plus settings.
- **The actual code or app** — what the agent generates and edits.
- **Outputs** — what gets produced when you run the thing.

This isn't a rigid structure — you can organise your folder however you like. But this rough split (inputs, reference, code, outputs) shows up in almost every project, and the rest of this guide assumes it.

### The folder is also the boundary

When the agent works inside your folder, it can read every file in there but nothing outside. This isn't just a convenience — it's a safety property. Your other documents, your downloads, your unrelated work — all invisible. The folder is your scope guardrail.

This also means: **if the agent needs to know about something, it has to be in the folder.** If you want the agent to follow your firm's writing style, the style guide goes in the folder. If you want it to summarise a contract, the contract goes in the folder. Things that aren't there don't exist, from the agent's perspective.

### Why this matters before we go further

Once you have this picture in your head, the rest of the guide makes sense. "Open a terminal in your project folder" means: navigate to that specific folder before running the command. "Persistent instructions" live in a specific file *in the folder*. "Context window" is about how much of the folder the agent is currently holding in its working memory.

If you're still hazy on any of this, that's fine — it'll click as you actually do it.

---

## 3. The mental model: it's not a chatbot

This is the single biggest shift to internalise before picking a tool. ChatGPT-style chat interfaces are *conversational*: you ask, you get an answer, you ask again. Each turn is largely independent. The interface *is* the experience.

AI coding agents are *agentic and folder-scoped*. The folder is the experience. The agent reads files, writes files, runs commands. You direct the work, but the agent does it — sometimes for minutes at a time, sometimes touching dozens of files. Your job is to set up the folder well, point the agent at the right task, and verify the result.

Three things follow:

**Context is finite and degrades.** Every file the agent reads, every command it runs, every piece of conversation, fills up its working memory (the "context window"). As that fills, performance drops — the agent starts forgetting earlier instructions and making more mistakes. Most of the best practices in this guide exist to manage this one constraint.

**Structure beats chat.** A two-line instruction in a project-level config file does more for output quality than a paragraph of context pasted into every prompt. Persistent context beats per-conversation context.

**You stay responsible.** The agent will produce confident-looking work that's wrong in subtle ways. For anything that matters — sent to a customer, deployed to production, used to make a decision — verification isn't optional. The habits in [section 14](#14-verification-how-to-trust-what-you-didnt-write) are not skippable.

The shift, in one sentence: *you're not asking questions, you're managing a workspace.*

---

## 4. Picking your tool

Five tools dominate the conversation in 2026. They're not interchangeable, but the differences matter less than people online suggest. Pick one based on your starting point and the kind of thing you want to build; switch later if needed.

### Quick guide

| If you… | Try |
| --- | --- |
| Have a Claude Pro/Max subscription and want the most-used vibe-coding tool | **Claude Code** *(desktop app — no terminal needed)* |
| Want to start in your browser with no install at all | **Lovable** |
| Want an editor that feels familiar and lets you stay close to the code | **Cursor** |
| Want to experiment with parallel agents on a generous free tier | **Antigravity** |
| Already pay for ChatGPT and want a cloud-based agent | **Codex** |

If in doubt, **start with Claude Code Desktop** if you have a Claude subscription, or **Lovable** if you don't. Both get you to a working tool in under an hour without writing code yourself.

### Lovable

**What it is.** A web-based app builder that turns plain-language descriptions into full-stack web applications. You describe the app in chat; Lovable builds the frontend, backend, and database. Visual editor for tweaking the result.

**Best for.** Non-technical builders who want a working web app — internal tools, landing pages, simple SaaS products, customer-facing dashboards. Especially strong for React + Supabase stacks. The most "no-code-feeling" of the five, by some distance.

**Notable.** Knowledge base tab where you persist project context (similar role to a `CLAUDE.md` file, different mechanism). One-click deployment. Strong on UI generation; weaker on complex backend logic. The fastest path from idea to running web app.

### Cursor

**What it is.** A fork of VS Code (the world's most popular code editor) with AI woven through every layer. Looks and feels like a normal IDE; the AI is the upgrade.

**Best for.** Anyone with even a little code-editor experience. The lowest-friction path from "I've used VS Code or similar before" to "I'm shipping AI-built code." Excellent for editing existing codebases, multi-file refactors, and staying close to the code while the AI helps.

**Notable.** Configuration in `.cursorrules` files. Tab-completion that actually feels intelligent. Multiple models selectable per task (Claude, GPT, Gemini). Background agents for longer autonomous work. Around a million daily users in 2026 — by far the largest IDE community.

### Claude Code (Anthropic)

**What it is.** Anthropic's AI coding agent, available in two equally first-class forms: a **desktop app** (Mac and Windows; redesigned April 2026 into a full IDE-like environment with parallel sessions, file editor, diff viewer, and live preview) and a **CLI** (terminal-native, scriptable, runs anywhere including Linux). Both share the same engine, the same `CLAUDE.md` configuration, the same skills and hooks. Use whichever fits the task.

**Best for.** The default choice if you have a Claude subscription. The desktop app is genuinely beginner-friendly — file tree on the left, diffs reviewed in-app, no terminal commands required. The CLI is what you reach for once you want scripting, automation, or remote/SSH workflows. Strong at long, multi-step tasks where the agent works for minutes at a time, and at running multiple parallel sessions across projects.

**Notable.** Configuration in `CLAUDE.md` files. Rich ecosystem of skills, sub-agents, slash commands, hooks, and MCP integrations. Permission-based safety model. Routines (scheduled or event-triggered automations) for hands-off recurring work. Sonnet 4.5 / Opus 4.7 under the hood. Requires a Pro, Max, Team, or Enterprise plan.

### Google Antigravity

**What it is.** A VS Code-derived AI editor built around Google's Gemini models, with multi-agent orchestration as a first-class feature. You can dispatch multiple agents (called "missions") to work in parallel.

**Best for.** Builders who want to experiment with parallel agents and don't mind a younger product. Generous free preview, very long context window (Gemini's strength), built-in browser for end-to-end testing.

**Notable.** Configuration via `AGENTS.md` files (an emerging cross-tool standard). Native browser controls for testing web apps. Mission Control for managing parallel work. No MCP support yet at the time of writing.

### OpenAI Codex

**What it is.** OpenAI's AI coding agent, available as a CLI, a cloud-based agent, a desktop app, and a VS Code extension. Bundled with ChatGPT Plus/Pro subscriptions.

**Best for.** People already paying for ChatGPT who want a terminal/cloud agent without another subscription. Strong at long-running cloud tasks — kick off a feature build, check back later. GPT-5 reasoning under the hood.

**Notable.** Cloud execution mode: tasks run on OpenAI's infrastructure, not your machine. Configuration also via `AGENTS.md`. Sandboxed by default. Tight GitHub integration with automatic pull-request creation.

### How to choose, in plain language

You can — and many people do — use more than one. Claude Code Desktop for daily building, Lovable for quick prototypes you want to share publicly, Cursor when you want to stay close to a specific codebase, Codex if it comes free with your existing ChatGPT plan. The principles in this guide apply to all of them, so the cost of switching later is low.

---

## 5. What you can actually build

Concrete examples that someone could realistically build in a weekend, none requiring you to ship production-grade software:

- **A personal dashboard** that pulls in data you care about — calendar, emails, tasks, the weather, whatever — and shows it the way *you* want to see it.
- **An internal tool for your team.** Intake form, reviewing process, output document. Replaces the messy spreadsheet everyone hates.
- **A document review pipeline.** Takes a PDF, runs it through a checklist, produces a structured summary. Works for contracts, research papers, expense reports, anything.
- **A scraper-and-organiser.** Reads a folder of files (or fetches from a website), sorts and tags them, produces a searchable index.
- **A landing page with real interactivity.** Not just a marketing site — embedded calculators, interactive demos, calendar bookings, lightweight forms-with-logic.
- **A custom CRM-lite.** Tracks the dozen people you care about for whatever you're working on, in the structure that fits *your* work, not the structure Salesforce wants.
- **A chatbot grounded in your own data.** Knowledge base + retrieval + conversation. The "ChatGPT for your company docs" pattern, scaled down to "ChatGPT for *my* docs."
- **A scheduled job that does one annoying thing.** Every Monday morning, do X. Every time a new file appears in this folder, do Y.
- **A custom report generator.** Structured input data + a template + a styled output (PDF, Word, slides). The thing your manager keeps asking for in a slightly different format every quarter.
- **A prototype of a real product** — enough to test the core idea with five people before you decide if it's worth investing in.

The common shape: a folder with inputs, a folder with reference material, a clear instruction file, and a structured output. Most useful tools fit this shape. Notice that none of these are "the next Facebook." The leverage is in *small, specific, yours*.

---

## 6. Setup, by tool

The 30-minute version for each. Skip to the one you're using.

### Before any local install: how to open a terminal

If you've never used a terminal, here's the thirty-second version:

- **Mac.** Press `Cmd+Space`, type "Terminal", press Enter. A black (or white) window opens with a blinking cursor. That's it.
- **Windows.** Press the Windows key, type "Terminal" or "PowerShell", press Enter. Same idea.
- **Inside VS Code or Cursor.** `View → Terminal` (or `Ctrl/Cmd+\``). This opens a terminal panel inside your editor — convenient because you see your folder and your terminal at the same time.

To navigate to a folder, type `cd` followed by the folder path, e.g. `cd Documents/my-project`. To see what's in the current folder, type `ls` (Mac/Linux) or `dir` (Windows). That's all the terminal vocabulary you need to start.

### Lovable (no install)

Go to [lovable.dev](https://lovable.dev), sign in, click "New project." Describe what you want in plain language. Lovable builds it in front of you. Use the Knowledge tab (in project settings) to add persistent project context. Connect a Supabase project for the backend; connect a GitHub repo if you want the code under version control. No local install required. No terminal required. This is the lowest-friction path of the five.

### Cursor

Download from [cursor.com](https://cursor.com), install, open. If you've used VS Code, it's the same — your extensions and themes import automatically. If you haven't: it's a window with a file tree on the left, an editor in the middle, and a chat panel you can open on the right. Sign in for the AI features. Create a `.cursorrules` file in your project root for project-specific instructions. Hit `Cmd/Ctrl+L` to open the chat panel; `Cmd/Ctrl+K` for inline edits.

### Claude Code

Two ways to install, depending on whether you want the desktop app or the CLI. Most people start with the desktop app.

**Desktop app (recommended for beginners; Mac and Windows).** Download from [claude.com/product/claude-code](https://claude.com/product/claude-code). Install, sign in with your Claude Pro or Max account, and click the **Code** tab. Point a session at any folder on your computer. On Windows you'll also need [Git for Windows](https://git-scm.com/download/win); Mac comes with git built in. No terminal commands required.

**CLI (Linux, scripting, or terminal preference).**

```bash
# macOS / Linux
curl -fsSL https://claude.ai/install.sh | bash

# Windows: install Node.js first, then
npm install -g @anthropic-ai/claude-code
```

Open a terminal in your project folder (see above) and run `claude`. Sign in. Run `/init` to generate a starter `CLAUDE.md`. Run `/permissions` to decide which actions Claude can take without asking. Done.

The two share configuration — `CLAUDE.md` files, skills, hooks, and MCP servers all work identically across both. You can use both on the same project; nothing to migrate.

### Google Antigravity

Download from the [Antigravity site](https://antigravity.google.com), install, open. VS Code-like UI; if you have VS Code you'll find your way around in a minute. Sign in with a Google account for the free preview. Create an `AGENTS.md` file in your project root for persistent instructions. Use Mission Control (the agent panel) to dispatch tasks.

### OpenAI Codex

If you have ChatGPT Plus or Pro, you have Codex. CLI install:

```bash
npm install -g @openai/codex
```

Run `codex` in your project folder. Sign in via your ChatGPT account. Create an `AGENTS.md` file for project context. For longer tasks, use cloud mode — the task runs on OpenAI's infrastructure and you can close your laptop.

### Universal recommendation

Whichever tool you pick (other than Lovable, which handles this for you), install [`git`](https://git-scm.com/) and use it from day one. Initialise every project with `git init`, commit before any big change. Git is your "undo for whole projects." When the AI breaks something in five files at once, you can revert the whole batch in one command.

For the IDE-style tools, also install the [GitHub CLI (`gh`)](https://cli.github.com/) — every agent listed above knows how to use it for committing, opening pull requests, and reading issues.

---

## 7. Your first 30 minutes: a Claude Code Desktop walkthrough

If you're brand new to all this, the fastest way to get the *feeling* of vibe coding is to actually do it. This walkthrough gets you a working tool in roughly half an hour, using the **Claude Code desktop app** — the most-used vibe-coding tool in 2026 and, since the April 2026 redesign, also one of the most beginner-friendly. No terminal commands required.

> **Don't have a Claude Pro or Max subscription?** Claude Code Desktop needs one. If you'd rather try something free first, jump to the [Lovable alternative](#alternative-lovable-no-install-needed) at the end of this section — same idea, different tool, no install required.

We'll build a tiny tool: **a personal reading tracker**. You log a book you're reading, mark progress, see your list. Trivial — but it touches frontend, backend, and a database, which is the same shape as much more useful internal tools.

### A quick orientation to the desktop app

Before the walkthrough, three things to know about Claude Code Desktop:

1. It's a **proper desktop application** for Mac or Windows (not Linux yet — Linux users can still use the CLI). Looks and feels like an IDE: file tree on the left, working area in the middle, a session sidebar.
2. It has **three tabs** at the top: *Chat* (regular Claude conversation, no file access), *Code* (the IDE-like environment we'll use), and *Cowork* (cloud-based autonomous agent). For this walkthrough, you live in the **Code** tab.
3. It uses the **same engine and configuration as the CLI** — the `CLAUDE.md` files, MCP servers, hooks, and skills you set up here all work identically if you ever switch to the terminal version. Nothing to relearn.

If you've never installed software like this, that's the whole new vocabulary. Just install and click "Code."

### The walkthrough

**Step 1: Install.** Go to [claude.com/product/claude-code](https://claude.com/product/claude-code) and download the desktop app for your platform. On Windows, you'll also need [Git for Windows](https://git-scm.com/download/win) installed — the desktop app uses git internally to keep parallel sessions isolated. Mac comes with git already.

Install, open, sign in with your Claude Pro or Max account. Click the **Code** tab.

**Step 2: Create a project folder.** On your computer, make a new empty folder somewhere you'll remember. For example: `Documents/reading-tracker`. The folder doesn't need anything in it yet — Claude will populate it.

In the desktop app, click "New session" (or whatever your version calls the equivalent — usually a `+` button in the sidebar). Point it at the folder you just made. The app now treats that folder as your project workspace.

**Step 3: Describe what you want.** In the chat panel, paste roughly this prompt:

> Build a personal reading tracker as a single-page web app. No login, no
> backend — just localStorage. I want to:
> - Add a book (title, author, total pages, current page)
> - See a list of all books with a progress bar
> - Update the current page on any book
> - Mark a book as finished
>
> Use plain HTML, CSS, and JavaScript — no frameworks. Use a clean, calm
> design with no bright colours. Don't add anything I haven't asked for.
>
> Show me a plan first before writing any files.

Hit send. Notice that the last line asks for a plan first. Claude will respond with a written plan — the files it intends to create, the structure, any decisions it's making. Read it. If something looks wrong, say so.

**Step 4: Approve and let it build.** When the plan looks good, just say *"Looks good, please build it."* You'll watch files appear in the file tree on the left. The app shows you a diff for each file before it commits the change — you can accept, reject, or edit anything inline.

**Step 5: Run it.** Once the files are written, the desktop app's preview pane can render an HTML file directly. Click the preview button (or open `index.html` in your browser if you prefer). Try adding a book, updating progress, marking one finished. Almost certainly something is slightly off — that's normal and expected.

**Step 6: Iterate.** Tell Claude what to change, conversationally:

> The progress bar is too thin. Make it twice as tall.
> Also, when I mark a book finished, can it move to a separate "Finished"
> section below the active list?

Watch the diff appear. Approve. Refresh the preview. The whole edit-review-test loop now takes seconds.

**Step 7: Set up persistent instructions.** Now the high-leverage move. Click into the file tree and create a new file called `CLAUDE.md` at the root of your project folder. Paste:

```markdown
# Reading tracker

## What this is
Personal reading tracker. Single-page web app, plain HTML/CSS/JS,
localStorage. No frameworks.

## Hard rules
- No new dependencies unless I explicitly ask.
- No frameworks (React, Vue, etc.) unless I explicitly ask.
- Keep the design minimal — no shadows, no gradients, no bright colours.
- When you change a file, briefly tell me what changed, then stop.

## Workflow
- Show me a plan before writing or editing files.
- One change at a time unless I ask for more.
```

Save the file. From now on, every prompt in this project respects these rules — Claude reads `CLAUDE.md` at the start of every session. Notice how the next thing you ask gets handled differently because of this.

**Step 8: Test the guardrails.** Try one prompt where you *expect* Claude to push back or clarify:

> Can you add a feature that automatically downloads every new book I add
> as a PDF from the internet?

Claude should refuse or ask clarifying questions — there's no clean way to do that, copyright is a mess, and the prompt is vague. Notice how it handles ambiguity. This is your chance to get a feel for the tool's failure modes early, in a low-stakes setting.

**Step 9: Commit your work.** Either ask Claude *"Please commit everything we've done so far with a sensible commit message,"* or use the desktop app's git panel. You now have a saved snapshot you can roll back to. From here you can keep iterating, knowing every change is undoable.

### What you just learned

In the space of about 30 minutes you've experienced most of what this guide is about:

- A real folder on your computer that *is* the project (section 2)
- A persistent instructions file (`CLAUDE.md` — see section 8)
- The Explore → Plan → Build → Verify loop, in miniature (section 9)
- Iterative prompting and self-correction (section 10)
- The agent doing things you didn't ask for (and you reining it in via rules)
- Diff-based review (section 13)
- Version control as your safety net

Everything else in this guide is variations on, deepening of, or escape valves from this same basic loop. Now that you've felt it, the rest will land.

### What to try next

Once the reading tracker works, the same shape lets you build many more useful things. Some good next steps from here:

- **Open multiple sessions** in the sidebar and run a different small project in each. This is what the redesigned desktop app is built for — parallel agentic work.
- **Add a `.claude/skills/` folder** with a skill for "house style" or "data formats I use" — the agent will load it automatically when relevant. (See section 12.)
- **Set up a Routine** (a scheduled or event-triggered automation) for something you do regularly — like drafting a weekly summary every Monday morning.

### Alternative: Lovable, no install needed

If installing software isn't an option for you, or if you don't have a Claude Pro/Max subscription, [Lovable](https://lovable.dev) gives you a similar first experience entirely in the browser:

1. Sign up at [lovable.dev](https://lovable.dev), click "New project."
2. Paste the same reading-tracker prompt (drop the "plain HTML, CSS, JavaScript — no frameworks" line; Lovable will use React + Supabase by default and that's fine for this).
3. Use the **Knowledge tab** in project settings instead of `CLAUDE.md` for persistent rules.
4. Iterate the same way — describe changes, watch them happen.
5. Click "Publish" when done — your app is on a real URL you can share.

The skills transfer directly between tools. If you start with Lovable, you can move to Claude Code Desktop later when you want more control or bigger projects.

---

## 8. Persistent instructions: the highest-leverage configuration

Every tool in this guide has some equivalent of "instructions that load every time." Different name, same purpose:

| Tool | File / location |
| --- | --- |
| Claude Code | `CLAUDE.md` at project root |
| Cursor | `.cursorrules` at project root |
| Lovable | Knowledge tab in project settings |
| Antigravity | `AGENTS.md` at project root |
| Codex | `AGENTS.md` at project root |

Configuring this well is the single highest-leverage thing you can do. A good persistent instruction file is *short* — well under a page — and covers:

- **What this project is.** One or two sentences.
- **Defaults.** Working language, style, framework, output format, jurisdiction or context.
- **Things to never do.** Specific traps you've hit. ("Never use a paid API. Never commit `.env` files. Never invent function names you haven't verified exist.")
- **Workflow conventions.** ("Run tests before suggesting a commit. Commit after each logical change.")
- **Pointers, not content.** Reference other files rather than copying their contents.

A working example for a typical project:

```markdown
# Project: client-feedback-tracker

## What this does
Internal tool for collecting and triaging customer feedback. Inputs are
emails forwarded to a designated mailbox; outputs are sorted entries in
a Notion database, with auto-generated tags.

## Defaults
- Stack: Next.js + Supabase. No new dependencies without asking.
- Working language: English.
- Style: minimal, follow shadcn/ui defaults. No custom CSS unless required.

## Hard rules
- Never log customer email addresses or message content.
- Never call OpenAI directly — go through our wrapper in lib/llm.ts.
- Never edit files in /vendored/ — those are pinned upstream copies.

## Workflow
- Plan first. Show me the plan before editing files.
- Test before commit. Run `npm test` after changes.
- Conventional commit messages.

## Reference
- Architecture notes: docs/architecture.md
- Component library: components/ui/ (shadcn/ui)
```

Things to **leave out**:

- Anything the agent can figure out by reading the code
- Generic best practices ("write clean code")
- Long tutorials or background reasoning
- Things that change frequently

The discipline: **for every line, ask "would removing this cause the agent to make a mistake?" If not, cut it.** A bloated instruction file causes the agent to ignore the rules that actually matter, because they get lost in the noise. If the agent keeps doing something despite a rule against it, the file is probably too long and the rule is getting buried.

In Lovable specifically, the equivalent lives in the Knowledge tab rather than a file in your repo — same idea, different mechanism. Add the same kind of content there: defaults, hard rules, workflow conventions, pointers to reference material. Lovable's chat will pick it up on every interaction.

---

## 9. The core workflow: Explore → Plan → Build → Verify

Letting the agent jump straight to building almost always produces something that's either over-engineered or solves a slightly wrong version of the problem. Separating phases fixes most of it.

**Step 1: Explore.** Get the agent oriented before letting it change anything. Most tools have a read-only mode for this:

- **Claude Code:** Plan Mode (`Shift+Tab`)
- **Cursor:** Ask mode (`Cmd/Ctrl+L`, set to "Ask" not "Agent")
- **Lovable:** start with questions in chat before clicking through to building
- **Antigravity:** Ask mode in the chat panel
- **Codex:** Use `--ask` mode or the equivalent

Have it read the relevant files and summarise what it sees. Push back on misunderstandings *before* code gets written.

**Step 2: Plan.** Still read-only. Ask for a written plan. *"What files need to change? What's the order? Any new dependencies? Edge cases I should think about?"* Read the plan. Edit it if needed. The plan is cheap to change at this stage; the code isn't.

In Cursor and Antigravity you can save the plan to a markdown file in the repo (`PLAN.md`) and reference it later. In Lovable it lives in the chat history. Either way: the plan is a separate artefact from the implementation.

**Step 3: Build.** Switch the agent to write mode. Tell it to follow the plan. *"After each step, briefly tell me what you did. If you hit something not covered by the plan, stop and ask."* Watch the file changes go by. Don't be afraid to interrupt — every tool here lets you stop the agent mid-task without losing context.

**Step 4: Verify.** Run it. Look at the output. Did it work? Did it do what you asked? Did it accidentally also do five things you didn't ask for? Verification is in [section 14](#14-verification-how-to-trust-what-you-didnt-write) in detail.

**When to skip the plan.** If you can describe the change in one sentence ("rename this variable", "add a log line", "fix this typo"), just ask. Plan Mode adds overhead and you don't need it for trivial changes. The rule of thumb: *if you could describe the diff in a single sentence, skip the plan.*

---

## 10. Prompting patterns that work

The agents are good. They get better when you talk to them well. Five patterns that pay back disproportionately.

### 10.1 Be specific about scope

| Vague | Specific |
| --- | --- |
| "Improve the dashboard" | "On the dashboard page, the chart in the top-right is too tall on mobile. Constrain it to 240px max-height below 768px viewport. Don't touch anything else." |
| "Fix the login bug" | "Users report login fails after their session times out. Check `src/auth/`, especially the token refresh logic. Write a failing test that reproduces it, then fix. Address the root cause, don't suppress the error." |

Vague prompts work fine when you're exploring and can afford to course-correct. A prompt like *"what would you change about this file?"* can surface things you wouldn't have asked. But for any prompt where you have a specific outcome in mind, name it.

### 10.2 Reference, don't paraphrase

Most tools support `@`-mentioning files. This loads the actual file content into the prompt:

```
Follow the patterns in @components/ui/Button.tsx when building the new
DropdownButton component.
```

This is more reliable than describing what's in the file. Pasting URLs to public docs also works in most tools — the agent will fetch them.

### 10.3 Show one good example

One concrete example beats five adjectives. If you want output in a specific format, show one example of that format. If you want code in a specific style, point to existing code in that style.

```
Here's how we structured the existing API endpoints — see @app/api/users/route.ts.
Build the new /api/feedback endpoint following the same conventions:
- Same error handling shape
- Same auth middleware
- Same response format

Don't introduce new patterns.
```

### 10.4 Tell the agent what *not* to do

Modern agents are trained to be helpful, which sometimes means doing things you didn't ask for: refactoring along the way, adding error handling for cases that can't happen, generating documentation, "improving" things. Be explicit when you don't want that.

```
Do NOT:
- Refactor unrelated code, even if you think it's worse than the new code
- Add try/catch around things that don't need them
- Write comments explaining what the code obviously does
- Add new dependencies — work with what's already in package.json
- Create new abstractions for one-time-use logic

Just make the change I asked for. If something else is genuinely broken
and blocking the change, tell me; don't fix it.
```

This single block, in your project's persistent instructions, will save you hours.

### 10.5 Build a self-check into the prompt

For prompts you'll re-use, append a verification block. The agent is surprisingly good at catching its own mistakes when explicitly told to:

```
Before declaring this done, verify:
- [ ] All existing tests still pass
- [ ] No new TypeScript errors
- [ ] No console.log left in code
- [ ] No hardcoded values that should be config
- [ ] The feature works for the example case I gave

Run through the checklist explicitly and report the result of each.
```

This pattern — *contract format up front, self-check at the end* — is the workhorse for any prompt you'll run more than once.

> **A note on "tests."** Several patterns here mention tests. A *test* is just a small piece of code that automatically checks whether your main code does what it should. The agent can write these for you (often in the same session as the feature itself); when you "run the tests," a script tries them all and tells you which pass and which fail. You don't need to know how to write tests yourself — just know that asking for them, and asking the agent to keep them passing, is one of the strongest ways to catch problems early.

---

## 11. Context is the resource: managing it ruthlessly

Context — the working memory the agent has during a session — is the single biggest determinant of output quality. Performance degrades smoothly as the window fills: instructions get forgotten, mistakes accumulate, focus drifts. Most "the agent got worse over the session" complaints are really "the context window filled up."

Five habits, in rough order of importance.

**Reset between unrelated tasks.** Finished one feature and now switching to a different one? Start fresh. In Claude Code: `/clear`. In Cursor: open a new chat. In Lovable: start a new conversation thread. Don't carry yesterday's context into today's job.

**Use sub-tasks or sub-agents for investigation.** When you ask the agent to "look around and figure out how X works", the reading itself fills your main context with files you don't actually need to keep. Better: dispatch a sub-task. Claude Code has explicit sub-agents; Antigravity has parallel missions; Cursor and Codex can run background agents. The sub-task reads in its own context and reports back a summary. Your main session stays clean.

**Prefer pointers to embeds.** `@playbook/standards.md` is a one-line reference; the file gets loaded once when needed. Pasting the contents of the playbook into the chat costs context every turn.

**Plan in a file, execute in a fresh session.** For larger features, ask the agent to write a `SPEC.md` after a planning conversation. Then start a new session: *"Implement `@SPEC.md`."* The new session has clean context entirely focused on building, and you have a written spec to reference and improve.

**Prune persistent instructions.** If the agent keeps doing something despite a rule against it, your instruction file is probably too long. Cut anything the agent already does correctly without instruction. Less is more.

For long-running tasks, most tools auto-compact the conversation when you approach the limit. You can also trigger this manually (`/compact` in Claude Code; in Cursor, summarise and start fresh). Use it before a long task is going to push you over.

---

## 12. Skills, agents, rules, commands: when to use which

> *Safe to skip on first read.* This section is the deep end of project configuration. You can build perfectly good tools using only a persistent instructions file (section 8). Come back here when your projects start having repeating patterns you want to formalise.

Different tools, similar concepts under different names. Pick by purpose, not by what the tool calls it.

### Persistent rules (the everywhere kind)

Loads on every interaction. Use for things that always apply: house style, hard prohibitions, default stack.

- Claude Code: `CLAUDE.md`
- Cursor: `.cursorrules`
- Antigravity / Codex: `AGENTS.md`
- Lovable: Knowledge tab

### Skills / on-demand context

Specialised knowledge or capability that loads *when relevant*, not every time. Use for things that bloat your main rules file: jurisdiction-specific formatting, a particular API's quirks, your firm's writing voice.

- Claude Code: `.claude/skills/<name>/SKILL.md`
- Cursor: scoped rules in `.cursor/rules/<name>.mdc` (the newer file format)
- Antigravity / Codex: scoped `AGENTS.md` files in subdirectories
- Lovable: separate Knowledge entries with clear titles

### Sub-agents / focused workers

A specialised assistant the main agent can delegate to. Runs in its own context window. Useful for tasks that read a lot of files or need a focused, narrower mandate.

- Claude Code: `.claude/agents/<name>.md`
- Antigravity: dispatched missions
- Cursor: background agents
- Codex: cloud tasks
- Lovable: limited support — closer to "open a new chat for that"

### Commands / reusable workflows

A multi-step procedure you trigger by a short alias. Use for things you do over and over.

- Claude Code: `.claude/commands/<name>.md`, triggered as `/name`
- Cursor: prompts library, available via `@`
- Antigravity / Codex: typically scripts you wire to your shell
- Lovable: less applicable — re-paste your standard prompt or save it as a snippet

### Hooks / guarantees

Automatic actions that run *every* time, with no exceptions. Use for things you can't afford to forget: linting, security checks, formatting.

- Claude Code: `.claude/settings.json` hooks
- Cursor: built-in lint/format integration
- Antigravity / Codex: pre/post-task hooks (varies by version)
- Lovable: limited; typically baked into deployment pipeline

### Picking between them

| If the thing is… | Use |
| --- | --- |
| Standing knowledge / style that should always apply | Persistent rules |
| Specific knowledge that should apply when relevant | Skills / scoped rules |
| A task that needs its own clean context to do well | Sub-agent |
| A multi-step workflow you'll trigger many times | Command / saved prompt |
| A guard that must run every time, no exceptions | Hook / pipeline check |

These compose: a saved command can invoke a sub-agent, which uses a skill. Most mature projects end up using all five categories.

---

## 13. Ten patterns that recur in real projects

Most projects are recombinations of a small number of patterns. Recognise them, and most builds become "pick patterns A, C, and F, then wire them together."

### 13.1 Reference-data-as-markdown

The "rules" of your project — playbook, standards, prompts, business logic — live as markdown files in the repo. The agent reads them as reference on every relevant task. Update the markdown, behaviour changes, no redeployment. Most powerful pattern in this list.

### 13.2 Template + structured input → polished output

A template file (Word, slide deck, HTML) with placeholders, plus a structured input file (markdown, YAML, JSON) describing the variables. The agent fills the template and produces the deliverable. Far more reliable than asking the agent to "write a document about X" from scratch.

### 13.3 Diff-based revision

For revisions, give the agent both the previous version and the new instructions. *"Revise `@drafts/v3.md` according to `@notes/feedback.md`. Show me a diff first; don't apply until I confirm."* Diffs are easier to review than full re-drafts.

### 13.4 Two-pass generation

First pass: structure and substance. Second pass (often via a sub-agent with a different prompt): tone, polish, consistency, citations. Trying to do both at once produces mediocre results in both.

### 13.5 Verified output via second-agent review

Any output that matters gets a second pass by a different agent (or the same agent in a fresh session) whose only job is to look for problems. The reviewer doesn't share context with the writer, so it catches things the writer was blind to.

### 13.6 Folder-scoped scope guardrail

One folder per project / matter / customer. The agent operates inside the folder; everything outside is invisible. This is your privilege boundary, your scope guardrail, and your audit trail.

### 13.7 Plain-language summary paired with technical output

Every technical output (memo, report, draft, code change) gets a 3-sentence plain-language summary at the top. For stakeholder communications, that summary is often the only part that gets read. Build it in by default.

### 13.8 Risk-graded output

Group findings by severity rather than by document order. Stakeholders want to see `HIGH` issues first. A consistent rubric (e.g. *blocking / negotiate / accept* or *critical / warning / nit*) means every output speaks the same language.

### 13.9 Human-in-the-loop checkpoints

Bake review steps into the workflow. A command that runs steps 1–4, then *stops* and asks you to confirm before steps 5–6. The agent does grunt work; you provide judgement at the right moments.

### 13.10 Iteratively narrow examples

When the agent's output keeps drifting from what you want, add more specific examples to the persistent instructions. One example beats five adjectives; three examples beat one. Build up your `examples/` folder organically — every time you get a good output, save it.

---

## 14. Verification: how to trust what you didn't write

Output that looks correct but contains a fabricated fact is worse than no output at all. Verification is not optional. The good news: agents are genuinely good at catching their own mistakes when verification is set up properly.

### Three layers

**Layer 1: Structural (automatic).** A script or hook checks structure: required sections present, no `[TODO]` markers left in a "final" output, expected output format, no obvious errors. The agent can write these checks for you.

**Layer 2: Content (semi-automatic).** A separate agent session, with no memory of how the output was produced, reviews the output against the source material. *"Here's the spec. Here's the implementation. Find anything in the implementation that doesn't match the spec, or any spec requirement that's missing."* Fresh context catches errors the writing session was blind to.

**Layer 3: Human (always).** You read the output. The first two layers exist to make this layer fast — by the time you're reading, structural problems are gone and obvious content problems have been spot-checked. You're focused on judgement, not proofreading.

### Concrete techniques

- **Run the code.** For software projects, the build either passes or it doesn't. The tests either pass or they don't. The page either loads or it doesn't. Use these binary signals as your first filter.
- **Tag uncertainty explicitly.** Tell the agent: *"If you're not sure about something, write `[UNCERTAIN: <reason>]` rather than guessing."* Then make `[UNCERTAIN]` part of your structural check.
- **Diff against a known-good example.** For repeated workflows, keep an `examples/` folder of past outputs you trust. New outputs should look structurally similar; large structural deviations are a signal something went wrong.
- **Test on a known case.** Before trusting a new tool on real work, run it on three cases where you already know what the right answer looks like. If it's right on those, you have a baseline.
- **Never deploy without a kill switch.** For any tool with side-effects (sending email, posting to a system, charging a card), the final step should be human approval, not autonomous execution.

The asymmetry to internalise: **the agent will produce confident-looking wrong answers.** This isn't a bug you can prompt away; it's a property of the model. Your job is to build verification that doesn't rely on you spotting confident-but-wrong by eye.

---

## 15. Failure modes, and recognising them early

Five patterns come up over and over. The first time costs you a day; recognising them later costs minutes.

**The kitchen-sink session.** You started with one task, drifted into another, doubled back. The agent is now confused about what you actually want. *Symptom:* answers feel less precise; the agent keeps re-explaining things. *Fix:* clear context, restart with a focused prompt.

**The over-corrected output.** You corrected the agent twice, the third draft is still off, you correct again. Context is now full of failed attempts and the agent is averaging across them. *Symptom:* each correction makes the output marginally worse, not better. *Fix:* reset, write a *better* prompt incorporating what you learned, start fresh. A good prompt almost always beats long correction chains.

**The bloated instruction file.** You kept adding rules every time something went wrong. Now the agent ignores half of them. *Symptom:* a rule clearly stated in your `CLAUDE.md` / `.cursorrules` / Knowledge tab is being violated. *Fix:* prune. Move details into skills or scoped rules. Keep only what's broadly applicable.

**Confident hallucination.** A function name, an API endpoint, a library that doesn't exist — fluent and plausible, also wrong. *Symptom:* something specific that you can verify turns out to be invented. *Fix:* the verification layers from section 14. Treat every unverified specific claim as suspect, especially names of things.

**Infinite exploration.** "Investigate the codebase" with no scope. The agent reads dozens of files trying to understand everything. *Symptom:* long minutes of file-reading, context window approaching full, no concrete output. *Fix:* scope tightly. *"Look only at the auth code. Just answer one question: where does the session token get refreshed?"* Use sub-agents to keep exploration out of your main context.

The general rule: **if the same correction has happened more than twice, the problem is the prompt or the context, not the agent's effort.** Stop trying harder; restart smarter.

---

## 16. Going further: parallel sessions, automation, MCP

Once you're comfortable with single-session work, three multipliers let you scale up.

### Parallel sessions

Run multiple agents in parallel — one drafting, one reviewing, one investigating. Each gets its own clean context. Common patterns:

- **Writer / Reviewer.** Session A writes, Session B (in a fresh window) reviews. The reviewer isn't biased toward what they just wrote, so it catches problems the writer missed.
- **Test / Implement.** Session A writes tests for what the tool should do. Session B implements until tests pass.
- **Multiple tasks in parallel.** One agent per feature. Truly isolated, no context bleed.

Antigravity is the most opinionated about this — multi-agent missions are a first-class feature. Cursor offers up to 8 parallel background agents. Claude Code has agent teams and git worktree isolation. Codex has parallel cloud tasks. Lovable is more single-threaded by design.

### Non-interactive mode for automation

Most of the agent CLIs support a non-interactive mode for scripting:

```bash
# Claude Code
claude -p "review the open PRs and post a summary to Slack"

# Codex
codex run "summarise this week's commits in CHANGELOG.md"
```

This is how a single project becomes a tool that runs on a schedule, reacts to events, or that a colleague can run from their laptop without ever opening the agent interactively.

### MCP servers: connecting external systems

[Model Context Protocol](https://modelcontextprotocol.io/) is the emerging open standard for connecting agents to external systems — your document management system, your database, your email, your calendar — without writing custom integration code. Many MCP servers already exist (Google Drive, Notion, Slack, GitHub) and the ecosystem is growing fast.

MCP support varies by tool: Claude Code has the most mature support, Cursor supports it natively, Codex has CLI support, Antigravity hadn't shipped MCP at the time of writing, and Lovable doesn't expose MCP directly (but supports its own integrations to common services).

The most useful MCP integrations for most builders: a file system (so the agent can read where your work actually lives), a calendar/email client (for summarisation and scheduling), and a knowledge base (Notion, Obsidian, or similar — so your collective knowledge becomes part of every relevant task). Connect what you actually use; ignore the rest.

---

## 17. A reference project structure

A starting structure that works for most projects. Adapt freely — this is a starting point, not a standard.

```
my-project/
├── README.md                   # what this does, how to run it
├── CLAUDE.md / AGENTS.md       # persistent agent instructions
│   .cursorrules                # (or whichever your tool uses)
├── .claude/                    # tool-specific config (varies)
│   ├── skills/
│   ├── agents/
│   ├── commands/
│   └── settings.json
├── docs/
│   ├── architecture.md
│   ├── decisions.md            # ADRs — why we did X not Y
│   └── house-style.md
├── reference/                  # the "rules" of your domain
│   ├── playbook.md
│   └── glossary.md
├── templates/                  # documents, prompts, code scaffolds
├── examples/                   # known-good outputs to diff against
├── inputs/                     # current work inputs (gitignored if sensitive)
├── outputs/                    # generated deliverables (gitignored)
└── src/                        # actual code (if applicable)
```

**The pattern:** stable folders (`reference/`, `templates/`, `examples/`, agent config) carry the intelligence; throwaway folders (`inputs/`, `outputs/`) carry the current work. New job, new contents in `inputs/`; everything else stays put.

Put it under git from day one. You get full history, the ability to roll back any change, and the option to share with collaborators by pushing to a (private) repository. For Lovable projects specifically, connect a GitHub repo from project settings — same benefit, no local install required.

---

## 18. Resources

### Official documentation

- **Claude Code:** [Best Practices](https://code.claude.com/docs/en/best-practices) · [Common workflows](https://code.claude.com/docs/en/common-workflows) · [Skills](https://code.claude.com/docs/en/skills) · [MCP](https://code.claude.com/docs/en/mcp)
- **Cursor:** [Cursor Docs](https://docs.cursor.com/) · [Rules for AI](https://docs.cursor.com/context/rules)
- **Lovable:** [Lovable Docs](https://docs.lovable.dev/)
- **Google Antigravity:** [Antigravity Docs](https://antigravity.google.com/docs)
- **OpenAI Codex:** [Codex Docs](https://platform.openai.com/docs/guides/codex)
- **Prompt engineering:** [Anthropic's prompting guide](https://docs.claude.com/en/docs/build-with-claude/prompt-engineering/claude-4-best-practices) — applies broadly, not just to Claude

### Community resources

- [awattar/claude-code-best-practices](https://github.com/awattar/claude-code-best-practices) — example commands, agents, patterns
- [shanraisshan/claude-code-best-practice](https://github.com/shanraisshan/claude-code-best-practice) — extensive curated patterns
- [Cursor Directory](https://cursor.directory/) — community-shared `.cursorrules` examples
- [Lovable Templates](https://lovable.dev/templates) — starter projects
- [Model Context Protocol](https://modelcontextprotocol.io/) — open standard for agent integrations

---

## 19. Glossary: terms and acronyms

A jargon-buster for the terms used in this guide. Click any section to expand it. If a term in the guide isn't here and should be, that's a bug — let us know.

> **Tip:** Browser search (Ctrl-F / Cmd-F) doesn't always find text inside collapsed blocks. To search the whole glossary, expand all sections first or view this page in raw view on GitHub.

<details>
<summary><strong>Vibe coding itself</strong></summary>

- **Vibe coding.** A way of building software where you describe the *intent* and *feel* of what you want, and an AI agent figures out the implementation. You stay in charge — directing, reviewing, redirecting — but the agent does most of the typing. Coined in early 2025; now a working methodology rather than a meme.
- **Agent.** An AI system that doesn't just answer questions but *takes actions* — reads files, runs commands, makes changes — usually iterating across multiple steps to accomplish a goal. The defining feature of all the tools in this guide. *Note:* "AI agent," "agent," and "agentic system" are roughly interchangeable; "the model" usually refers to the underlying LLM (e.g. Claude Sonnet 4.5) rather than the agent built around it.
- **Agentic.** Adjective form of *agent*. "An agentic workflow" = a workflow where an agent is autonomously taking action across multiple steps. Contrast with *conversational*, where each turn is independent.
- **Sub-agent** (also: subagent). A specialised, scoped agent that the main agent can delegate to. Runs in its own context so it doesn't clutter the main session. Good for *"go investigate X and report back."*
- **LLM** — *Large Language Model*. The underlying AI that powers all of these tools. Claude, GPT, Gemini are all LLMs. The model is the engine; the agent is the car built around it.

</details>

<details>
<summary><strong>The basics: where code lives and runs</strong></summary>

- **Terminal** (also: command line, shell). The window with text where you type commands instead of clicking buttons. On Mac it's called *Terminal*; on Windows it's *Command Prompt*, *PowerShell*, or *Windows Terminal*; on Linux it's just *the terminal*. Looks intimidating, isn't really. See section 6 for how to open one.
- **CLI** — *Command Line Interface*. A program you control by typing commands into the terminal, rather than clicking on a UI. `git`, `npm`, and `claude` are all CLIs.
- **IDE** — *Integrated Development Environment*. A program for writing code that bundles editor + file browser + debugging + terminal in one window. **VS Code** (Visual Studio Code) is the most popular IDE in the world. Cursor and Antigravity are forks of it (modified copies with extra features).
- **VS Code.** Microsoft's free IDE. Most of the AI coding tools either *are* VS Code with modifications (Cursor, Antigravity) or have plugins for it.
- **Linux / kernel-level.** Linux is a family of open-source operating systems used to run most of the internet's servers. The *kernel* is the deepest part of the operating system — the bit that talks directly to hardware. *Kernel-level sandboxing* means restrictions enforced by the OS itself, which is much harder to escape than restrictions enforced by an application.
- **Sandbox / sandboxing.** Running code inside a restricted environment so that if it misbehaves, it can't damage the rest of your system. Like a playpen for software.
- **Cloud.** Someone else's computer that you rent time on over the internet. *"Running in the cloud"* means the work happens on a remote server, not your laptop.

</details>

<details>
<summary><strong>Working with code: files, projects, version control</strong></summary>

- **Project.** Your work, all together — typically one folder with all the files for one tool, app, or piece of software. See section 2.
- **Repo / repository.** A folder containing a project, tracked by `git` so you have full history of every change. *"Repo"* is just shorthand for *"repository"*; same thing. Most often you'll see *"GitHub repo"*, meaning a repository hosted on GitHub.
- **Codebase.** Yet another word for the collection of code in a project. *"Our codebase"* = *"all the code we have."*
- **Workspace.** The folder the agent treats as its world. Anything inside is fair game; anything outside is invisible. The folder *is* the scope guardrail.
- **Git.** The world's most-used version control system. Tracks every change you make to files in a project; lets you undo, branch, merge, and collaborate. Once you start using it, you don't go back.
- **GitHub.** A website (owned by Microsoft) where people host git repositories. Most open-source code lives here. Not the same as git itself — git is the tool, GitHub is one place to put git repos.
- **Commit.** A saved snapshot of your project at a point in time. Each commit has a message describing what changed. Commits are how git keeps history.
- **Branch.** A parallel line of development. You make a branch when you want to try something without disturbing the main version. If it works, you merge it back; if not, you discard it.
- **Fork.** A copy of someone else's repo that you own. Cursor and Antigravity are *forks* of VS Code — copies that the new owners then modified.
- **Diff.** The list of differences between two versions of a file. *"Show me a diff first"* means *"show me what would change before you actually change it."*
- **PR — Pull Request.** A formal proposal to merge changes from one branch into another, with a place for review and discussion. Standard way teams ship code to a shared codebase.
- **`.gitignore`.** A file that tells git which files to ignore (not track in version control). Things like passwords, generated files, and local-only config go here.
- **Markdown (`.md`).** A simple plain-text format for writing documents with light formatting (headings, lists, links, bold). This guide is written in markdown. GitHub renders it as a styled webpage automatically.

</details>

<details>
<summary><strong>How software is built: stacks, frameworks, languages</strong></summary>

- **Stack.** The combination of technologies a project uses. *"Next.js + Supabase"* is a stack — meaning Next.js for the frontend and Supabase for the backend and database. *"MERN stack"* means MongoDB + Express + React + Node — a popular shorthand.
- **Frontend.** The part users see and interact with — the website, the app screens, the buttons. Built with HTML, CSS, JavaScript, and frameworks like React.
- **Backend.** The part users *don't* see — servers, databases, business logic. Often a different language and framework from the frontend.
- **Framework.** A pre-built foundation for a particular kind of project. **React** is a frontend framework for building interactive UIs; **Next.js** is built on top of React and adds more conventions; **Tailwind** is a styling framework.
- **Database.** The structured store where an app keeps its data. **SQL** databases (PostgreSQL, MySQL, SQLite) store data in tables; **Supabase** is a hosted Postgres database with extras built in.
- **API — Application Programming Interface.** The contract that lets one piece of software talk to another. When this guide talks about *"the Claude API"* it means the way external code can send requests to Claude and get responses back.
- **API endpoint.** A specific URL that an API exposes for a specific purpose. `/api/users` is an endpoint for user-related operations.
- **Deploy / deployment.** Putting code somewhere it actually runs and is accessible — typically on the cloud, often on a hosting service like Vercel or Netlify.
- **Environment variable / `.env`.** Configuration values (API keys, database passwords, settings) stored outside your code so they don't get committed to git. Usually in a file called `.env` that's gitignored.
- **Test.** A small piece of code that automatically checks whether your main code does what it should. *Running the tests* = a script tries them all and tells you which pass and which fail. The agent can write tests for you.

</details>

<details>
<summary><strong>Languages and notation</strong></summary>

- **HTML.** The markup language for web page structure — what's a heading, what's a paragraph, what's a link.
- **CSS.** The language for styling web pages — colours, fonts, spacing, layout.
- **JavaScript (JS) / TypeScript (TS).** The programming languages of the web. JavaScript runs in browsers and on servers. TypeScript is JavaScript with type-checking added — popular for larger projects.
- **JSON — JavaScript Object Notation.** A standard way to represent structured data as text, like `{"name": "Alice", "age": 30}`. Used everywhere on the web.
- **YAML.** Another structured data format, more human-readable than JSON, popular in configuration files.

</details>

<details>
<summary><strong>Development tools you'll see in setup instructions</strong></summary>

- **Node.js.** A way to run JavaScript outside a browser — on your laptop, on a server, in a CLI. Many of the AI coding tools are installed via Node.
- **npm — Node Package Manager.** A program that comes with Node.js for installing JavaScript libraries. `npm install -g <something>` installs a tool globally on your machine.
- **Python.** A programming language popular for data analysis, scripting, and automation. Comes pre-installed on Mac and Linux.
- **`gh` — GitHub CLI.** A command-line tool for interacting with GitHub: opening pull requests, creating issues, browsing repos.

</details>

<details>
<summary><strong>AI coding concepts</strong></summary>

- **Prompt.** The instruction you give the AI. *"Write me a function that does X"* is a prompt. Persistent project rules are *also* prompts — they just travel with the project rather than being typed each time.
- **Token.** The unit LLMs measure text in. Roughly: one token ≈ ¾ of a word in English. Pricing is usually per-token; context windows are measured in tokens.
- **Context window.** How much text (input + history) the model can hold in its working memory at once. Bigger is better, up to a point — model performance still degrades as the window fills, even before it's full. Managing it is a core skill.
- **RAG — Retrieval-Augmented Generation.** A technique where, before answering, the AI looks up relevant chunks of a knowledge base and includes them in its context. Most *"ChatGPT for your docs"* products use RAG under the hood.
- **MCP — Model Context Protocol.** An open standard, originated by Anthropic, for connecting AI agents to external tools and data sources (your Notion, your calendar, your database) without writing custom integrations for each. Increasingly supported across tools.
- **Plan Mode / Ask Mode.** Most of these tools have a read-only mode where the agent can look at files and answer questions but can't make changes. Different tools call it different things — Claude Code calls it *Plan Mode*, Cursor calls it *Ask*, Antigravity calls it *Ask mode*. All do the same thing: let you orient the agent before turning it loose to edit.
- **Cowork.** Anthropic's autonomous background agent that runs tasks in a cloud-based virtual machine, accessible through the Claude desktop app. Unlike the regular Code mode which works on your local files, Cowork operates remotely — useful for long-running tasks where you don't want your laptop tied up.
- **Routines.** Scheduled or event-triggered automations in Claude Code. You configure them once; they run on Anthropic's cloud infrastructure on a schedule, in response to a webhook (e.g. a new GitHub PR), or via an API call. Useful for nightly summaries, recurring triage tasks, or anything you'd otherwise have to remember to run yourself.

</details>

<details>
<summary><strong>Configuration concepts (the stuff in your project's <code>.claude/</code> or <code>.cursor/</code> folder)</strong></summary>

- **Skill.** A bundle of domain knowledge (a markdown file plus optional helpers) that the agent loads when relevant — not on every prompt. Use for specialised knowledge that would bloat your main rules file.
- **Command** (slash command). A reusable multi-step workflow you trigger with a short alias like `/triage-nda`. The body of the command tells the agent what to do step by step.
- **Hook.** A script that runs *automatically* at a specific point in the agent's workflow — for example, after every file edit. Use for guarantees you can't afford to forget (linting, formatting, security checks).
- **Rules file** (`CLAUDE.md`, `AGENTS.md`, `.cursorrules`). Persistent instructions loaded at the start of every session in this project. The single highest-leverage configuration in your project.
- **Workflow.** A repeatable sequence of steps to accomplish something. Some workflows are written down as commands; others live in your head. Either way, having explicit workflows beats improvising.

</details>

<details>
<summary><strong>Services and platforms mentioned in this guide</strong></summary>

- **Supabase.** A hosted backend-as-a-service: database (Postgres) + auth + file storage + APIs. Common pairing with Lovable.
- **Notion.** A document/database/wiki app, popular for team knowledge bases. Has an MCP integration so agents can read and write to it.
- **Slack.** Workplace chat. Has integrations for both reading messages and posting agent output.
- **Figma.** Design tool. Has MCP integrations so agents can read design specs and turn them into working components.
- **Obsidian.** A markdown-based personal knowledge base. Files-on-disk, so any agent that can read a folder can read your Obsidian vault.

</details>

---

## Closing note

The temptation when you start vibe coding is to build something elaborate — a polished tool, a feature-complete app, the next big thing. Resist it. The people getting the most value out of these tools are building small, ugly, specific things that solve one real problem on their desk this week. They iterate when something goes wrong. They throw out tools that don't earn their keep.

Start with one workflow you do every week. Build the smallest possible version. Run it on a real task. Notice what's wrong. Improve it. By the time you've done this three or four times, you'll have your own intuitions — better than any guide can give you.

The patterns here are starting points, not rules.
