---
name: design-skills
description: Curated index for the design skills. Use when the user wants to design, audit, wireframe, theme, hand off, or research UI/UX — pick the right one instead of guessing. Trigger with "design X", "how should this look", "audit this design", "hand off this design", "research our users".
---

# Design Skills Index

You have a design task. Read this, pick the one skill that matches, then follow it.
This is a navigation layer — it does not replace the skill it points to.

## The pipeline

Research → **Design** → Hand off

`impeccable` now covers the Design stage end to end (design, redesign, shape,
critique, audit, polish, theming, typography, layout, color, motion, UX copy,
design tokens, empty/error states). The old Plan / Standardize / Audit rows
folded into it, so the pipeline is short: gather research, shape the UI with
`impeccable`, hand it off. Use the side tools below for inputs/outputs `impeccable`
doesn't touch.

## Pick by what you're doing

| You want to… | Skill | Path |
|---|---|---|
| Design / redesign / audit / polish any frontend UI (web, dashboards, app shells, components, forms, settings, onboarding, empty states) | `impeccable` | `skills/impeccable/SKILL.md` |
| Understand our users (interviews, surveys, usability tests) | `user-research` | `skills/user-research/SKILL.md` |
| Distill research into themes + recommendations | `research-synthesis` | `skills/research-synthesis/SKILL.md` |
| Build code from a Figma link / frame / screenshot | `figma-to-code` | `skills/figma-to-code/SKILL.md` |
| Apply a consistent theme to decks / slides / docs / reports | `theme-factory` | `skills/theme-factory/SKILL.md` |
| Build a visual canvas (mind map, flowchart, diagram) | `json-canvas` | `skills/json-canvas/SKILL.md` |
| Turn a finished design into a dev spec sheet | `design-handoff` | `skills/design-handoff/SKILL.md` |

## Why so few now

`impeccable` absorbed the skills it fully covers, so they were removed:

- `anthropic-frontend-design`, `redesign-existing-projects` → `impeccable` craft/shape
- `design-taste-frontend` → `impeccable` craft-floor + 61-rule detector
- `design-design-critique`, `vercel-web-design-guidelines` → `impeccable` critique/audit
- `design-system`, `ux-copy`, `ux-flow-wireframer`, `accessibility-review` → `impeccable` covers these for light use

Those four (`design-system`, `ux-copy`, `ux-flow-wireframer`, `accessibility-review`)
each had deeper specialized form; they were removed in favor of `impeccable`. If you
need a full **WCAG 2.1 AA** audit or a durable **token + component-doc** system,
reinstall the skill or add it back — `impeccable`'s detector checks AI-design *tells*,
not a complete WCAG checklist.

## How to use

1. Match the current need to the table.
2. Read that skill's `SKILL.md` fully — it has the real workflow.
3. If the task spans stages (e.g. "research then design"), start at the earliest stage.
4. For a pre-launch gate, run `impeccable`'s `detect` pass, then `design-handoff`.
