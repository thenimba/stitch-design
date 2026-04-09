# Design System: Nimy.AI

## Overview
A dark, authoritative interface for an AI consulting and training platform targeting Israeli business professionals. The design communicates technical depth and expertise without being intimidating — premium but approachable. High information density with generous use of negative space between sections. RTL-first (Hebrew), with full LTR support for English content.

## Colors
- **Primary** (#64b3f4): CTAs, active states, links, key interactive elements
- **Secondary** (#4a90d9): Supporting actions, hover states, secondary buttons
- **Background** (#0D1117): Page and app background — deep charcoal, not pure black
- **Surface** (#161b22): Cards, panels, modals — slightly elevated from background
- **Surface Raised** (#21262d): Dropdowns, tooltips, nested containers
- **On-surface** (#e6edf3): Primary text on dark backgrounds
- **On-surface Muted** (#8b949e): Captions, labels, placeholder text, secondary info
- **Accent** (#64b3f4): Highlights, badges, focus rings — same as primary
- **Border** (#30363d): Dividers, input borders, card outlines
- **Error** (#f85149): Validation errors, destructive actions
- **Success** (#3fb950): Confirmations, positive states, completed steps
- **Warning** (#d29922): Alerts, pending states, caution indicators

## Typography
- **Headline Font**: Assistant (Hebrew-first, excellent RTL support, modern humanist)
- **Body Font**: Assistant
- **Label Font**: Assistant
- **Monospace Font**: JetBrains Mono (for code snippets, technical content)

Headlines use bold weight (700) with tight letter-spacing. Body text uses regular weight (400) at 16px with 1.6 line-height for readability. Labels use medium weight (500) at 13px. All text defaults to RTL alignment; English inline content switches to LTR via `dir="ltr"`. Maximum line length is 70 characters for body text.

## Elevation
Depth is conveyed through surface color stepping, not drop shadows. Background (#0D1117) → Surface (#161b22) → Surface Raised (#21262d) creates a three-level hierarchy. A single subtle border (1px solid #30363d) outlines elevated surfaces. Modals use a stronger backdrop (rgba(0,0,0,0.7)) with the Surface Raised color. No decorative shadows anywhere in the UI.

## Components
- **Buttons**: Rounded (6px). Primary — solid Primary fill (#64b3f4) with dark text (#0D1117). Secondary — transparent with 1px Primary border and Primary text. Destructive — solid Error fill (#f85149). Disabled — muted opacity (40%), non-interactive. Height: 40px standard, 32px compact, 48px large.
- **Inputs**: 1px Border (#30363d) outline, Surface (#161b22) background, 12px horizontal padding. Focus state transitions border to Primary (#64b3f4). Error state uses Error (#f85149) border with inline message below the field. Placeholder text in On-surface Muted (#8b949e).
- **Cards**: Surface (#161b22) background, 1px Border (#30363d) outline, 8px corner radius. No shadows. Hover state brightens border to (#484f58). Padding 20px internal.
- **Navigation**: Top bar on desktop, fixed position. Surface (#161b22) background with bottom border. Active nav item uses Primary (#64b3f4) underline indicator. Collapses to hamburger drawer on mobile.
- **Badges**: Pill-shaped (full radius), small (12px font, 4px 10px padding). Color-coded by semantic role — use Success/Warning/Error/Primary fills at 15% opacity with matching text color.

## Do's and Don'ts
- Do use Primary (#64b3f4) only for the single most important interactive element per screen
- Do maintain a minimum 4.5:1 contrast ratio — on-surface text (#e6edf3) on background (#0D1117) is non-negotiable
- Do use the three-surface color steps (Background → Surface → Surface Raised) to establish hierarchy instead of shadows
- Do apply RTL layout by default; flip flex direction, text-align, and icon positions for Hebrew content
- Don't use pure black (#000000) or pure white (#ffffff) anywhere in the UI
- Don't mix rounded and sharp corners — 6px radius is the system standard for all components
- Don't add decorative drop shadows; depth comes from surface color only
- Don't place Primary colored text on Surface backgrounds without verifying contrast
