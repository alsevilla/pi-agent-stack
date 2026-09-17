---
name: design-skills
description: Curated index for the design skills. Use when the user wants to design, audit, wireframe, theme, hand off, or research UI/UX — pick the right one instead of guessing. Trigger with "design X", "how should this look", "audit this design", "hand off this design", "research our users".
---

# Design Skills Index

You have a design task. Read this, pick the one skill that matches, then follow it.
This is a navigation layer — it does not replace the skill it points to.

## The pipeline

Research → Plan → Design → Standardize → Audit → Hand off
Most tasks start partway through. Match the *current* need, not the whole journey.

## Pick by what you're doing

| You want to… | Skill | Path |
|---|---|---|
| Understand our users (interviews, surveys, usability tests) | `user-research` | `skills/user-research/SKILL.md` |
| Distill research into themes + recommendations | `research-synthesis` | `skills/research-synthesis/SKILL.md` |
| Sketch the flow / low-fi wireframes before designing | `ux-flow-wireframer` | `skills/ux-flow-wireframer/SKILL.md` |
| Write or review microcopy, CTAs, empty states, error messages | `ux-copy` | `skills/ux-copy/SKILL.md` |
| Design a distinctive, production-ready UI from a brief | `anthropic-frontend-design` | `skills/anthropic-frontend-design/SKILL.md` |
| Upgrade an existing app/site to premium (any CSS / vanilla) | `redesign-existing-projects` | `skills/redesign-existing-projects/SKILL.md` |
| Build code from a Figma link / frame / screenshot | `figma-to-code` | `skills/figma-to-code/SKILL.md` |
| Apply a consistent theme to decks / slides / docs / reports | `theme-factory` | `skills/theme-factory/SKILL.md` |
| Build a visual canvas (mind map, flowchart, diagram) | `json-canvas` | `skills/json-canvas/SKILL.md` |
| Define / extend a design system (tokens, component docs) | `design-system` | `skills/design-system/SKILL.md` |
| Get structured feedback on a design in progress | `design-design-critique` | `skills/design-design-critique/SKILL.md` |
| Audit WCAG 2.1 AA accessibility | `accessibility-review` | `skills/accessibility-review/SKILL.md` |
| Audit UX / layout / typography against web guidelines | `vercel-web-design-guidelines` | `skills/vercel-web-design-guidelines/SKILL.md` |
| Turn a finished design into a dev spec sheet | `design-handoff` | `skills/design-handoff/SKILL.md` |
| Anti-slop / taste check on a frontend (landing, portfolio) | `design-taste-frontend` | `skills/design-taste-frontend/SKILL.md` |

## The caveat that matters

`design-taste-frontend` is **not a design method** — it's an anti-slop / taste checklist.
It reads a brief, infers a direction, and ships interfaces that don't look templated, but it
explicitly does *not* cover dashboards, data tables, or multi-step product UI. Use it as a
final pass to kill generic AI looks, not as the thing that designs the thing.

For actual end-to-end design:
- **New UI from a brief** → `anthropic-frontend-design` (committed direction, hero/sections/components).
- **Upgrading something that already exists** → `redesign-existing-projects` (audit → remove AI patterns → apply standards without breaking functionality).

## How to use

1. Match the current need to the table.
2. Read that skill's `SKILL.md` fully — it has the real workflow.
3. If the task spans stages (e.g. "research then design"), start at the earliest stage and
   chain skills in pipeline order.
4. For a pre-launch gate, run `vercel-web-design-guidelines` + `accessibility-review` before `design-handoff`.
