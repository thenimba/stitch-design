# stitch-design

> A Claude skill that generates `DESIGN.md` files in the official [Google Stitch](https://stitch.withgoogle.com) format from any project context — spec, brief, PRD, or brand guide.

![Claude Skill](https://img.shields.io/badge/Claude-Skill-orange?logo=anthropic)
![Format](https://img.shields.io/badge/Format-Google%20Stitch-blue)
![License](https://img.shields.io/badge/License-MIT-green)

---

## What is DESIGN.md?

`DESIGN.md` is a machine-readable design system file introduced by Google Stitch. It encodes your brand's visual rules — colors, typography, components, elevation — in plain Markdown that AI coding agents can read and apply consistently.

Think of it as a system prompt for your UI. Drop it into any project and agents like Stitch, Lovable, Cursor, Antigravity, or Claude Code will generate on-brand interfaces without you re-explaining your design on every prompt.

| File | Who reads it | What it defines |
|------|-------------|----------------|
| `AGENTS.md` | Coding agents | How to build the project |
| `DESIGN.md` | Design agents | How the project should look and feel |

---

## What This Skill Does

Give it any project context — a spec document, a PRD, a brand guide, or even a short description — and it generates a complete, production-ready `DESIGN.md` following the official Stitch format.

**Input:** Anything describing your product (text, document, URL, or freeform description)  
**Output:** A `DESIGN.md` with 6 structured sections ready to use across your AI toolchain

### The 6 Sections

| # | Section | What it captures |
|---|---------|-----------------|
| 1 | **Overview** | Mood, density, design philosophy |
| 2 | **Colors** | Semantic palette with hex values and usage roles |
| 3 | **Typography** | Font families and hierarchy rules |
| 4 | **Elevation** | Shadow system or flat depth strategy |
| 5 | **Components** | Buttons, inputs, cards, navigation, and more |
| 6 | **Do's and Don'ts** | Project-specific design guardrails |

---

## Installation

Download [`stitch-design.skill`](./stitch-design.skill) and install it in your Claude environment.

---

## Usage

Once installed, trigger it naturally:

```
צור design.md לפרויקט שלי
```
```
Create a DESIGN.md for my SaaS dashboard
```
```
Generate a design system file based on this spec document: [paste spec]
```
```
Make a DESIGN.md for a dark-themed fintech app, primary color #1a73e8
```

The skill will extract or ask for: project name, brand colors, light/dark mode, typography, mood, and key components — then output a complete `DESIGN.md` file.

---

## Example Output

See [`example/DESIGN.md`](./example/DESIGN.md) — a real `DESIGN.md` generated for **Nimy.AI**, a dark Hebrew-first AI consulting platform.

```markdown
# Design System: Nimy.AI

## Overview
A dark, authoritative interface for an AI consulting and training platform
targeting Israeli business professionals...

## Colors
- **Primary** (#64b3f4): CTAs, active states, links, key interactive elements
- **Background** (#0D1117): Page and app background — deep charcoal, not pure black
- **Surface** (#161b22): Cards, panels, modals — slightly elevated from background
...

## Do's and Don'ts
- Do use Primary (#64b3f4) only for the single most important interactive element per screen
- Don't add decorative drop shadows; depth comes from surface color only
...
```

---

## Supported Tools

Works with any AI agent that accepts file context:

- [Google Stitch](https://stitch.withgoogle.com)
- [Lovable](https://lovable.dev)
- [Cursor](https://cursor.sh)
- [Antigravity](https://antigravity.google)
- [Claude Code](https://claude.ai/code)
- Any LLM-backed coding agent

---

## Format Reference

This skill strictly follows the official Stitch DESIGN.md specification:

- [Overview](https://stitch.withgoogle.com/docs/design-md/overview/)
- [Format](https://stitch.withgoogle.com/docs/design-md/format/)
- [Usage](https://stitch.withgoogle.com/docs/design-md/usage/)

For community-contributed `DESIGN.md` examples, see [awesome-design-md](https://github.com/VoltAgent/awesome-design-md).

---

## License

MIT — free to use, modify, and share.

---

Built by [@nimrodbr](https://www.threads.net/@nimrodbr) · [Nimy.AI](https://nimy.ai)
