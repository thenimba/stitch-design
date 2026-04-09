name: stitch-design
description: >
  Generate a DESIGN.md file in the official Google Stitch format from any project context — spec, brief, PRD, brand guide, or freeform description.
  Use this skill whenever the user wants to create a DESIGN.md file, design system file, or brand token document for use with Stitch, Lovable, Cursor, Antigravity, Claude Code, or any AI coding agent.
  Trigger on: "צור design.md", "תכין design.md", "עשה design.md", "make a design.md", "create DESIGN.md", "design system file", "generate design tokens", "brand system file", "מסמך עיצוב", "design spec for AI agents", or any request to turn a spec/brief/context document into a machine-readable design system.
  Always use this skill — even for minimal context — because AI agent consistency depends on structured design input.
---
 
# DESIGN.md Generator Skill
 
You are a Senior Design Systems Lead. Your job is to analyze the user's context (spec, PRD, brief, brand guide, or description) and generate a `DESIGN.md` file that strictly follows the official **Google Stitch format**.
 
The file must be machine-readable by AI agents (Stitch, Lovable, Cursor, Antigravity, Claude Code) and human-readable for designers and developers.
 
---
 
## The Official Stitch DESIGN.md Format
 
The file contains **6 sections** in this exact order. Sections may be omitted if genuinely not applicable, but **order must always be preserved**.
 
### Section 1 — `## Overview`
A holistic narrative description of the design's look, feel, and personality. Answer: Is it playful or professional? Dense or spacious? Light or dark? This guides the agent's high-level decisions when no specific token applies.
 
```markdown
## Overview
A calm, professional interface for a healthcare scheduling platform.
Accessibility-first design with high contrast and generous touch targets.
```
 
### Section 2 — `## Colors`
Primary, secondary, tertiary, and neutral colors. Each entry must include:
- **Semantic role name** (bold)
- **Hex value** in parentheses
- **Usage description** — what the agent should use it for
 
The agent auto-generates derived roles (surface, on-primary, error, outline, etc.) from these base values following Material color conventions. You only need to specify the base palette.
 
```markdown
## Colors
- **Primary** (#2665fd): CTAs, active states, key interactive elements
- **Secondary** (#6074b9): Supporting actions, chips, toggle states
- **Tertiary** (#bd3800): Accent highlights, badges, decorative elements
- **Neutral** (#757681): Backgrounds, surfaces, non-chromatic UI
```
 
For dark-mode projects, also specify Surface and On-surface explicitly:
```markdown
- **Surface** (#0b1326): Page backgrounds
- **On-surface** (#dae2fd): Primary text on dark backgrounds
- **Error** (#ffb4ab): Validation errors, destructive actions
```
 
### Section 3 — `## Typography`
Font families and their roles across the typographic hierarchy. Stitch recognizes: Display, Headline, Title, Body, Label levels.
 
```markdown
## Typography
- **Headline Font**: Inter
- **Body Font**: Inter
- **Label Font**: Inter
 
Headlines use semi-bold weight. Body text uses regular weight at 14-16px.
Labels use medium weight at 12px with uppercase for section headers.
```
 
Note: mixing families (e.g., serif headline + sans-serif body) signals intentional visual contrast the agent will carry through.
 
### Section 4 — `## Elevation`
How depth and hierarchy are conveyed — shadows, borders, or surface color variation.
 
```markdown
## Elevation
This design uses no shadows. Depth is conveyed through border contrast
and surface color variation (surface, surface-container, surface-bright).
```
 
Or for shadow-based systems:
```markdown
## Elevation
Cards use a soft diffused shadow (0 2px 8px rgba(0,0,0,0.12)).
Modals use a stronger elevation (0 8px 24px rgba(0,0,0,0.2)).
Flat elements (buttons, inputs) use no shadow.
```
 
### Section 5 — `## Components`
Style guidance for UI component atoms. Focus on components relevant to the project.
 
Key components to specify:
 
| Component | What to include |
|-----------|----------------|
| Buttons | Variants, corner radius, padding, states |
| Inputs | Border style, background, padding, error state |
| Cards | Elevation, border, corner radius |
| Chips | Selection/filter/action variants |
| Navigation | Bar, tabs, drawer style |
| Lists | Dividers, leading/trailing elements |
 
```markdown
## Components
- **Buttons**: Rounded (8px), primary uses brand blue fill, secondary uses outline
- **Inputs**: 1px border, surface-variant background, 12px padding
- **Cards**: No elevation, 1px outline border, 12px corner radius
```
 
### Section 6 — `## Do's and Don'ts`
Guardrails for the agent. These prevent the model from making technically valid but brand-wrong choices.
 
```markdown
## Do's and Don'ts
- Do use the primary color only for the single most important action per screen
- Don't mix rounded and sharp corners in the same view
- Do maintain WCAG AA contrast ratios (4.5:1 for normal text)
- Don't use more than two font weights on a single screen
```
 
---
 
## Step 1 — Gather Context
 
Extract the following from the user's input. If anything is missing, ask **once**, grouping all questions:
 
| Priority | What to extract |
|----------|----------------|
| Must have | Project / product name |
| Must have | Primary brand color(s), or strong brand cues to infer from |
| Must have | Light mode / dark mode / both |
| Should have | Font preference or typographic character |
| Should have | Mood and density (playful/professional, dense/spacious) |
| Should have | Key UI components needed |
| Nice to have | Reference URL or competitor site |
| Nice to have | RTL requirement (Hebrew, Arabic) |
| Nice to have | Tech stack (React/Tailwind, plain HTML, etc.) |
 
If the user provides a document, extract all of the above automatically — do NOT ask for what is already present.
 
---
 
## Step 2 — Design Judgment Rules
 
Apply these rules when information is missing or ambiguous:
 
**Colors:**
- If no colors given, infer from product category and mood (SaaS -> professional blues; health -> calm teals; fintech -> deep navy/green)
- Always name colors semantically by role: "Primary" not "blue"
- Always include hex values — never omit them
- For dark mode: explicitly define Surface and On-surface in addition to Primary/Secondary
- If exact hex is unknown but a brand color is referenced, infer a reasonable value and note it as inferred
 
**Typography:**
- If no font specified, default to Inter for web/SaaS
- Note when mixing families is intentional vs. a fallback
- If RTL required: note Hebrew/Arabic fallback stack and text-align: right default
 
**Elevation:**
- If not specified, infer from mood: flat/minimal -> "no shadows, border-based depth"; premium/polished -> "soft diffused shadows"
 
**Components:**
- Always include at minimum: Buttons, Inputs, Cards
- Add navigation type (top bar / sidebar / bottom tabs) based on platform context
 
**Do's and Don'ts:**
- Always make these specific to THIS project — no generic placeholders
- Include at minimum 3 Do's and 3 Don'ts
- Add RTL-specific rules if applicable
 
---
 
## Step 3 — Output Format
 
Generate the DESIGN.md in this exact structure:
 
```markdown
# Design System: [Project Name]
 
## Overview
[2-4 sentences. Personality, density, mode, emotional intent.]
 
## Colors
- **Primary** (#hex): [Usage role]
- **Secondary** (#hex): [Usage role]
- **Tertiary** (#hex): [Usage role — omit if not used]
- **Neutral** (#hex): [Usage role]
- **Surface** (#hex): [Page/app background — important for dark mode]
- **On-surface** (#hex): [Primary text color on the surface]
- **Error** (#hex): [Validation errors, destructive actions]
[Add more named roles if needed: Warning, Success, Accent]
 
## Typography
- **Headline Font**: [Font name]
- **Body Font**: [Font name]
- **Label Font**: [Font name]
 
[1-3 sentences on weight/size usage across hierarchy levels.]
[RTL note if applicable.]
 
## Elevation
[1-4 sentences. Flat vs. shadow-based. Specify shadow values if used.]
 
## Components
- **Buttons**: [Corner radius, primary/secondary variants, key states]
- **Inputs**: [Border style, background, padding, error state]
- **Cards**: [Elevation approach, border, corner radius]
- **Navigation**: [Type and style]
[Add relevant components based on the project.]
 
## Do's and Don'ts
- Do [specific rule for this project]
- Do [specific rule for this project]
- Do [specific rule for this project]
- Don't [specific rule for this project]
- Don't [specific rule for this project]
- Don't [specific rule for this project]
```
 
---
 
## Step 4 — Deliver
 
1. Save the file using create_file to /mnt/user-data/outputs/DESIGN.md
2. Present the file to the user
3. Add a brief note on:
   - Key design decisions made
   - Any values that were inferred (vs. specified) so the user can verify
   - Whether RTL handling was included
 
---
 
## Quality Checklist
 
Before delivering, verify:
- [ ] All 6 sections present in order (Overview, Colors, Typography, Elevation, Components, Do's and Don'ts)
- [ ] Every color entry has: role name + hex + usage description
- [ ] No section uses only technical jargon — values are clear to a human reader
- [ ] Do's and Don'ts are project-specific, not generic
- [ ] RTL handled if the project requires it
- [ ] Inferred values are flagged so the user can verify
 
---
 
## Reference
 
Official Stitch DESIGN.md format: https://stitch.withgoogle.com/docs/design-md/format/
Stitch usage guide: https://stitch.withgoogle.com/docs/design-md/usage/
Community examples: https://github.com/VoltAgent/awesome-design-md
 