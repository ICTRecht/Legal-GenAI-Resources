<div align="center">

# 🧠 The Prompt Engineering Handbook

**A comprehensive guide to crafting effective AI prompts — from first principles to advanced techniques**

[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)
[![Made by ICTRecht](https://img.shields.io/badge/Made%20by-ICTRecht-blue)](https://www.ictrecht.nl)
[![Based on Google Research](https://img.shields.io/badge/Sources-Google%20AI%20Research-red)](https://cloud.google.com/vertex-ai)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](https://github.com/ICTRecht)

*Compiled and curated by [ICTRecht](https://www.ictrecht.nl) · Based on Google's Prompt Engineering Whitepaper (Lee Boonstra, 2024) and the Google Workspace Gemini Prompting Guide 101*

</div>

---

## 📖 Table of Contents

1. [What Is Prompt Engineering?](#-what-is-prompt-engineering)
2. [The Four Building Blocks](#-the-four-building-blocks-persona--task--context--format)
3. [LLM Output Configuration](#-llm-output-configuration)
4. [Prompting Techniques](#-prompting-techniques)
   - [Zero-Shot Prompting](#1-zero-shot-prompting)
   - [One-Shot & Few-Shot Prompting](#2-one-shot--few-shot-prompting)
   - [System, Role & Contextual Prompting](#3-system-role--contextual-prompting)
   - [Step-Back Prompting](#4-step-back-prompting)
   - [Chain of Thought (CoT)](#5-chain-of-thought-cot)
   - [Self-Consistency](#6-self-consistency)
   - [Tree of Thoughts (ToT)](#7-tree-of-thoughts-tot)
   - [ReAct (Reason + Act)](#8-react-reason--act)
   - [Automatic Prompt Engineering](#9-automatic-prompt-engineering)
   - [Code Prompting](#10-code-prompting)
5. [Ready-to-Use Prompt Templates](#️-ready-to-use-prompt-templates)
   - [Summarisation & Extraction](#-summarisation--extraction)
   - [Writing & Editing](#️-writing--editing)
   - [Research & Analysis](#-research--analysis)
   - [Iteration & Refinement Prompts](#-iteration--refinement-prompts)
6. [Best Practices](#-best-practices)
7. [Quick Reference Cheat Sheet](#-quick-reference-cheat-sheet)
8. [Sources](#-sources)

---

## 🔍 What Is Prompt Engineering?

> *"You don't need to be a data scientist or a machine learning engineer, everyone can write a prompt."*
> Google Prompt Engineering Whitepaper, 2024

A **prompt** is the input you provide to a large language model (LLM) to generate a response. An LLM works as a prediction engine: it takes sequential text and predicts what the next token should be, based on patterns learned during training.

**Prompt engineering** is the process of designing high-quality prompts that guide LLMs to produce accurate, relevant, and useful outputs. It is an **iterative process** — your first prompt is rarely your best one.

Key factors that affect prompt quality:
- The model you use
- The model's training data
- Model configuration (temperature, top-K, top-P)
- Word choice, style, and tone
- Structure and context of the prompt

> ⚠️ **Always review AI outputs** for clarity, relevance, and accuracy before acting on them. The output is your responsibility, not the model's.

---

## 🏗 The Four Building Blocks: Persona · Task · Context · Format

The foundation of any effective prompt rests on four components. You don't need all four every time, but combining them dramatically improves results.

| Component | What it does | Example |
|-----------|-------------|---------|
| 🎭 **Persona** | Tells the model *who it is* | `"You are a senior HR manager..."` |
| ✅ **Task** | Tells the model *what to do* | `"...draft a performance review email..."` |
| 📋 **Context** | Gives the model *relevant background* | `"...for an employee who exceeded targets in Q3..."` |
| 📐 **Format** | Specifies *how to structure the output* | `"...in bullet points, max 200 words."` |

### 💡 Example Prompt Using All Four

```
You are a program manager in the legal tech industry. [PERSONA]
Draft an executive summary email to the leadership team [TASK]
based on our Q3 product roadmap document. [CONTEXT]
Limit to bullet points, no more than 5 items. [FORMAT]
```

### ⚡ Six Quick-Start Tips

1. **Use natural language** — Write as if speaking to a colleague, in full sentences
2. **Be specific and iterate** — Tell the model exactly what to do; use follow-up prompts to refine
3. **Be concise, not vague** — Brief but specific beats long and meandering
4. **Make it a conversation** — Don't settle for the first result; push back and refine
5. **Provide your documents** — Reference your own files for personalized, grounded outputs
6. **Let the model suggest** — Many tools offer contextual next-step prompts you can build on

---

## ⚙️ LLM Output Configuration

Before diving into techniques, it helps to understand the knobs that control how an LLM generates text. These settings matter especially when using APIs or developer tools.

### 🌡️ Temperature

Temperature controls the **degree of randomness** in token selection.

| Temperature | Behavior | Best for |
|-------------|----------|----------|
| `0` | Deterministic — always picks most likely token | Factual Q&A, classification, math |
| `0.1–0.4` | Conservative, coherent, predictable | Summarization, data extraction |
| `0.5–0.8` | Balanced creativity and coherence | Business writing, emails |
| `0.9–1.0+` | Creative, diverse, unpredictable | Brainstorming, storytelling |

### 🎲 Top-K and Top-P (Nucleus Sampling)

These settings restrict *which* tokens the model can choose from:

- **Top-K** — Only sample from the top K most likely next tokens. Higher K = more creative; K=1 = greedy decoding (same as temp=0)
- **Top-P** — Sample from tokens whose cumulative probability doesn't exceed P. Values range from 0 (greedy) to 1 (all tokens)

<details>
<summary><strong>📊 Recommended Starting Configurations</strong></summary>

| Use Case | Temperature | Top-P | Top-K |
|----------|------------|-------|-------|
| Balanced / general use | 0.2 | 0.95 | 30 |
| Creative / brainstorming | 0.9 | 0.99 | 40 |
| Precise / factual | 0.1 | 0.90 | 20 |
| Single correct answer (math) | 0 | — | — |

> ⚠️ Setting temperature to 0 makes top-K and top-P irrelevant. Setting top-K to 1 has the same effect. More freedom (higher values) can reduce relevance.

</details>

### 📏 Output Length

Controlling the number of tokens in the response affects cost, speed, and quality. If you need a short output, **engineer your prompt to say so** — simply limiting tokens doesn't make the model more concise, it just cuts off the response.

---

## 🎯 Prompting Techniques

### 1. Zero-Shot Prompting

The simplest form of prompting: give the model a task description with no examples.

```
Classify movie reviews as POSITIVE, NEUTRAL or NEGATIVE.

Review: "Her is a disturbing study revealing the direction humanity is 
headed if AI is allowed to keep evolving, unchecked. I wish there were 
more movies like this masterpiece."

Sentiment:
```

**Output:** `POSITIVE`

> **When to use:** Simple, well-defined tasks where the model's training data is sufficient. Good starting point before escalating to few-shot.

---

### 2. One-Shot & Few-Shot Prompting

Provide one or more examples to show the model the desired output pattern. The model learns to imitate the pattern.

- **One-shot** — One example (single demonstration)
- **Few-shot** — Multiple examples (3–5 recommended; more for complex tasks)

```
Parse a customer's pizza order into valid JSON:

EXAMPLE:
I want a small pizza with cheese, tomato sauce, and pepperoni.
JSON Response:
{"size": "small", "type": "normal", "ingredients": ["cheese", "tomato sauce", "pepperoni"]}

Now parse: "Can I get a large pizza, with the first half cheese and 
mozzarella, and the other half tomato sauce, ham and pineapple."
JSON Response:
```

**Tips for good few-shot examples:**
- Use diverse, high-quality, well-written examples
- Include edge cases if your task requires robustness
- One bad example can mislead the entire output

---

### 3. System, Role & Contextual Prompting

Three related techniques for shaping the model's identity and approach:

<details>
<summary><strong>🖥️ System Prompting</strong> — Sets the overall rules and purpose</summary>

Defines the "big picture" — what the model should be doing overall. Great for enforcing output format, tone, and safety constraints.

```
Classify movie reviews as positive, neutral or negative. 
Only return the label in uppercase.

Review: "Her is a disturbing study..."
Sentiment:
```

You can also use system prompts to enforce structured output:

```
Classify movie reviews as positive, neutral or negative. Return valid JSON:

Schema:
MOVIE: { "sentiment": "POSITIVE" | "NEGATIVE" | "NEUTRAL", "name": String }

Review: [review text here]
JSON Response:
```

> 💡 Returning JSON forces structure and reduces hallucinations — ideal for applications that process the output programmatically.

</details>

<details>
<summary><strong>🎭 Role Prompting</strong> — Assigns a specific identity to the model</summary>

Assigning a role shapes the model's tone, vocabulary, and domain expertise. The role acts as a blueprint for style and knowledge.

```
I want you to act as a travel guide. I will write to you about my 
location and you will suggest 3 places to visit near me.

My suggestion: "I am in Amsterdam and I want to visit only museums."
Travel Suggestions:
```

**Effective role styles you can assign:**
`Confrontational` · `Descriptive` · `Direct` · `Formal` · `Humorous` · `Influential` · `Informal` · `Inspirational` · `Persuasive`

</details>

<details>
<summary><strong>📌 Contextual Prompting</strong> — Provides task-specific background</summary>

Gives the model immediate, dynamic context about the current task — making responses more accurate and relevant.

```
Context: You are writing for a blog about retro 80's arcade video games.

Suggest 3 topics to write an article about, with a few lines of 
description of what each article should contain.
```

> **Key difference:** Context prompts are *dynamic* and task-specific. System prompts set *static* overarching rules.

</details>

---

### 4. Step-Back Prompting

Ask the model to consider a **general principle first**, then apply that reasoning to the specific task. This activates broader background knowledge before tackling the problem.

**Two-step approach:**

```
Step 1 — General question:
"What are the general principles of contract law that govern 
force majeure clauses?"

Step 2 — Apply to specific task:
"Using those principles, analyze whether the COVID-19 pandemic 
qualifies as a force majeure event under [specific clause]."
```

**Benefits:**
- More accurate and insightful answers
- Reduces bias by focusing on principles rather than specific details
- Encourages critical thinking over pattern matching

---

### 5. Chain of Thought (CoT)

Prompt the model to **show its reasoning step by step** before giving the final answer. This dramatically improves performance on complex reasoning tasks.

```
Q: A store is selling apples for €1.50 each and oranges for €2.00 each. 
If I buy 3 apples and 2 oranges, how much do I spend in total?

Think step by step before giving the final answer.
```

**Expected output pattern:**
```
Step 1: Calculate the cost of apples: 3 × €1.50 = €4.50
Step 2: Calculate the cost of oranges: 2 × €2.00 = €4.00
Step 3: Add the totals: €4.50 + €4.00 = €8.50

Total: €8.50
```

> **CoT best practices:**
> - Add `"Think step by step"` or `"Let's reason through this"` to trigger reasoning
> - Works best with capable models (larger parameter counts)
> - Combine with few-shot examples showing the reasoning chain for complex tasks

---

### 6. Self-Consistency

Run the **same prompt multiple times** and aggregate the results. The most frequent answer is typically more reliable than any single output.

```
[Same prompt, run 3–5 times with temperature > 0]

Result 1: €8.50
Result 2: €8.50  
Result 3: €8.50  ← majority vote = final answer
```

> **When to use:** High-stakes tasks where accuracy is critical. Also useful to detect when a model is uncertain (high variance across runs).

---

### 7. Tree of Thoughts (ToT)

An extension of CoT where the model **explores multiple reasoning paths simultaneously**, evaluating and pruning branches like a decision tree. Best suited for complex problem-solving where multiple valid approaches exist.

```
Consider three different approaches to solve this problem.
For each approach:
1. Outline the reasoning path
2. Evaluate the strengths and weaknesses
3. Score it from 1–10 for viability

Problem: [complex task]

Then select the best approach and execute it fully.
```

---

### 8. ReAct (Reason + Act)

Combines **reasoning** with **action** — the model generates reasoning traces and decides when to call external tools (search, calculator, API, etc.) to gather information before producing the final answer.

```
You have access to the following tools:
- Search: look up current information on the web
- Calculator: perform arithmetic

Question: What is the current VAT rate in the Netherlands, and how much 
VAT would apply to a €450 purchase?

Thought: I need to find the current Dutch VAT rate.
Action: Search["Netherlands VAT rate 2024"]
Observation: [search result]
Thought: Now I can calculate.
Action: Calculator[450 × 0.21]
Final Answer: [result]
```

> ⚠️ **Important:** Set a reasonable output token limit for ReAct prompts — without it, the model may keep generating reasoning tokens after the answer is complete.

---

### 9. Automatic Prompt Engineering

Let the model **generate and evaluate its own prompts**. Useful when you're unsure how to phrase a task optimally.

```
Generate 5 different ways to prompt an AI to summarize a legal contract 
in plain language for a non-lawyer audience. 

For each prompt, rate its effectiveness from 1–10 and explain why.
Then output the best-performing prompt.
```

---

### 10. Code Prompting

LLMs are highly capable at code-related tasks. Use specific sub-techniques depending on your goal:

<details>
<summary><strong>✍️ Writing Code</strong></summary>

```
Write a Python function that takes a list of email addresses and returns 
only the valid ones using regex. Include docstrings and type hints.
```

</details>

<details>
<summary><strong>📖 Explaining Code</strong></summary>

```
Explain what the following Python code does, step by step, 
in plain English suitable for a non-programmer:

[paste code here]
```

</details>

<details>
<summary><strong>🔄 Translating Code</strong></summary>

```
Convert the following JavaScript function to Python, maintaining 
the same logic and adding appropriate Python conventions:

[paste code here]
```

</details>

<details>
<summary><strong>🐛 Debugging & Reviewing Code</strong></summary>

```
Review the following Python code for bugs, security vulnerabilities, 
and style issues. Suggest improvements and explain each one:

[paste code here]
```

</details>

---

## 🗂️ Ready-to-Use Prompt Templates

These templates are designed to be immediately useful across a wide range of professional tasks. Replace the `[bracketed placeholders]` with your own details. Each template applies the Persona → Task → Context → Format framework and can be iterated on with follow-up prompts.

---

### 📄 Summarisation & Extraction

<details>
<summary><strong>Summarise a document</strong></summary>

```
Summarise the following document in plain language.
Focus on: key arguments, main conclusions, and any action points.
Target audience: [non-specialist / senior management / legal professional].
Format: 3–5 bullet points followed by one concise paragraph.

[paste document text here]
```

</details>

<details>
<summary><strong>Extract key information from a text</strong></summary>

```
Read the following text and extract:
1. All dates and deadlines mentioned
2. Names of parties or organisations involved
3. Any obligations, rights, or conditions stated
4. Open questions or ambiguities

Present the results as a structured list.

[paste text here]
```

</details>

<details>
<summary><strong>Compare two documents</strong></summary>

```
Compare the following two texts [TEXT A] and [TEXT B].
Identify:
- Points where they agree
- Points where they differ
- Anything present in one but absent in the other

Present as a side-by-side comparison table, followed by a 
2–3 sentence overall assessment.
```

</details>

---

### ✍️ Writing & Editing

<details>
<summary><strong>Draft a professional email</strong></summary>

```
Draft a professional email to [recipient / role].
Purpose: [describe the goal of the email — inform, request, respond, etc.]
Key points to include: [list 2–4 points]
Tone: [formal / neutral / direct]
Length: concise — no more than 150 words.
End with a clear next step or call to action.
```

</details>

<details>
<summary><strong>Rewrite for clarity and plain language</strong></summary>

```
Rewrite the following text in plain, accessible language.
Target audience: [non-specialist / general public / management].
Keep the meaning intact. Avoid jargon.
Maximum length: [same as original / shorter by 30%].

[paste text here]
```

</details>

<details>
<summary><strong>Adapt tone for a different audience</strong></summary>

```
Rewrite the following text for three different audiences:
1. [Audience A — e.g. technical experts]
2. [Audience B — e.g. senior leadership]
3. [Audience C — e.g. the general public]

Original text:
[paste text here]
```

</details>

<details>
<summary><strong>Give feedback on a draft</strong></summary>

```
Review the following draft and give structured feedback.
Evaluate on:
- Clarity and readability
- Logical structure and flow
- Completeness (anything missing?)
- Tone (is it appropriate for the audience?)

For each point, suggest a concrete improvement.

[paste draft here]
```

</details>

---

### 🔍 Research & Analysis

<details>
<summary><strong>Explain a complex concept simply</strong></summary>

```
Explain [concept / term / regulation] in plain language.
Assume the reader has no background in [field].
Use a concrete real-world example to illustrate.
Keep it under 200 words.
```

</details>

<details>
<summary><strong>Map pros and cons of a decision</strong></summary>

```
We are considering [decision or option].
List the most important arguments for and against, structured as:

PRO:
- [argument 1]
- [argument 2]

CON:
- [argument 1]
- [argument 2]

Context: [relevant background information]
End with a balanced 2-sentence assessment.
```

</details>

<details>
<summary><strong>Scenario analysis</strong></summary>

```
Analyse [situation or decision] across three scenarios:
1. Best case — what if things go well?
2. Base case — what is the most likely outcome?
3. Worst case — what if things go wrong?

For each scenario: describe the situation, key assumptions, 
likely consequences, and recommended response.
Present as a comparison table.
```

</details>

<details>
<summary><strong>Generate structured questions for an interview or meeting</strong></summary>

```
I am preparing for a [meeting / interview / consultation] with [person / organisation].
Topic: [subject of the meeting]
My goal: [what I want to achieve or find out]

Generate 8–10 structured questions, ordered from broad to specific.
Flag any question that might be sensitive or require careful framing.
```

</details>

---

### 💬 Iteration & Refinement Prompts

Once you have a first output, use these follow-up prompts to push it further:

```
Make this more concise — cut it by 30% without losing the key points.
```

```
The tone is too [formal / informal / technical]. Rewrite it to be more [target tone].
```

```
This is a good start. Now add a section on [missing topic].
```

```
Summarise your response in one sentence.
```

```
What are the three most important things I should take away from your answer?
```

```
Play devil's advocate: what are the strongest counterarguments to your conclusion?
```

```
What assumptions are you making in this analysis? List them explicitly.
```

---

## ✅ Best Practices

### 🧱 Structural Best Practices

| Practice | Why it matters |
|----------|---------------|
| **Provide examples** | Few-shot examples dramatically improve output quality and consistency |
| **Design with simplicity** | A clear, concise prompt outperforms a complex, overwrought one |
| **Be specific about output** | Tell the model exactly what format, length, and structure you need |
| **Use instructions over constraints** | Say *what to do*, not just *what to avoid* — positive instructions work better |
| **Use variables** | Replace specific values with `[brackets]` to create reusable prompt templates |
| **Control token length** | Set explicit length limits in your prompt, not just in API settings |

### 🔁 Iteration & Testing

| Practice | Why it matters |
|----------|---------------|
| **Experiment with formats** | Try different writing styles and input structures; small changes can have big effects |
| **Mix up classes in few-shot** | For classification tasks, vary the order of examples to avoid pattern bias |
| **Document your prompts** | Track versions, results, and configurations — treat it like code |
| **Experiment together** | Share prompts with colleagues; what works for one task may inspire another |
| **Adapt to model updates** | Model behavior changes with updates; re-test prompts when models are upgraded |

### 🔒 Quality & Safety

- Always **review AI outputs** before using them — especially for legal, financial, or sensitive content
- Use system prompts to enforce **safety and tone** (e.g., `"You should be respectful and professional in all responses"`)
- Requesting **JSON output** forces structure and helps limit hallucinations in automated workflows
- Keep in mind: **the final output is always yours** — AI is a tool, not the author

---

## 📋 Quick Reference Cheat Sheet

```
╔══════════════════════════════════════════════════════════════════╗
║              PROMPT ENGINEERING — QUICK REFERENCE                ║
╠══════════════════════════════════════════════════════════════════╣
║                                                                  ║
║  FRAMEWORK          Persona · Task · Context · Format            ║
║                                                                  ║
║  TECHNIQUES                                                      ║
║  ├─ Zero-shot       Task only, no examples                       ║
║  ├─ Few-shot        Task + 3–5 examples                          ║
║  ├─ Role            "Act as a [role]..."                         ║
║  ├─ System          Set rules and output format upfront          ║
║  ├─ Contextual      "Context: You are writing for..."            ║
║  ├─ Step-back       General principle → specific task            ║
║  ├─ Chain of Thought "Think step by step..."                     ║
║  ├─ Self-consistency Run 3–5× and take the majority result       ║
║  ├─ Tree of Thoughts Explore multiple reasoning paths            ║
║  └─ ReAct           Reason → Action → Observe → Answer           ║
║                                                                  ║
║  TEMPERATURE GUIDE                                               ║
║  ├─ 0               Deterministic (math, facts)                  ║
║  ├─ 0.1–0.4         Conservative (summaries, extraction)         ║
║  ├─ 0.5–0.8         Balanced (emails, reports)                   ║
║  └─ 0.9–1.0         Creative (brainstorm, fiction)               ║
║                                                                  ║
║  GOLDEN RULES                                                    ║
║  ✓ Be specific     ✓ Iterate         ✓ Show examples             ║
║  ✓ Set format      ✓ Review output   ✓ Document prompts          ║
║                                                                  ║
╚══════════════════════════════════════════════════════════════════╝
```

### 🧰 Prompt Template Starter Kit

**General-purpose prompt:**
```
You are a [ROLE] at [ORGANIZATION/INDUSTRY].
[TASK]: [specific action verb + object]
Context: [relevant background information]
Format: [output structure, length, tone]
```

**Analysis prompt:**
```
Analyze [SUBJECT] and provide:
1. [First analysis dimension]
2. [Second analysis dimension]
3. [Recommendations/conclusions]
Context: [relevant background]
Audience: [who will read this]
```

**Comparison prompt:**
```
Compare [OPTION A] and [OPTION B] across the following dimensions:
- [Dimension 1]
- [Dimension 2]
- [Dimension 3]
Present as a structured table. End with a recommendation and rationale.
```

**Iterative refinement prompt:**
```
[Previous output has been generated]
This is a good start. Now:
- Make the tone more [formal/casual/concise]
- Expand the section on [topic]
- Remove [element]
- Add [missing element]
```

---

## 📚 Sources

This guide was compiled from the following primary sources:

- 📄 **Google Prompt Engineering Whitepaper** 
  Author: Lee Boonstra · Reviewers: Michael Sherman, Yuan Cao, Erick Armbrust, Anant Nawalgaria, Antonio Gulli, Simone Cammel

- 📄 **Google Workspace with Gemini — Prompting Guide 101**
  *A quick-start handbook for effective prompts* · Google Workspace team

Both documents are published by Google and used here for educational and knowledge-sharing purposes under a curated summary.

---

<div align="center">

---

*Have suggestions or improvements? Open a pull request or file an issue.*

</div>
