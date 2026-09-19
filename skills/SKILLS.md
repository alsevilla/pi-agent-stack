# Skills Index — Lazy Load

Skill `SKILL.md` files load **only when a task matches** — picked from this index and pointed at its real path (outside `skills/` for git-hosted ones).

---

## The skills

> **Layout:** This section is a compact pointer list. The **G-Stack section** below holds the full tables (superpowers, ponytail, gsd, compound, gstack) with every skill's exact path. Discovery still works — pi globs the real `SKILL.md` regardless of how much text is in this index.

### superpowers (method — full table in G-Stack section below)
- test-driven-development, systematic-debugging, verification-before-completion, writing-plans, executing-plans, subagent-driven-development, dispatching-parallel-agents, requesting/receiving-code-review, finishing-a-development-branch, using-git-worktrees, writing-skills

> **`superpowers:brainstorming` is deprecated** — `ce-brainstorm` is the sole primary brainstormer (intent-first). Kept on disk as fallback only; do not route to it. Superpowers still runs the TDD + executing-plans loop.

### anti-slop (consolidated taste rule — in `skills/`, auto-discovered)
- **anti-slop** — One checklist for anti-AI-slop across code + UI + writing: 27 code rules (ponytail's domain), UI taste (design-taste's domain), banned phrases, communication style. Not a new skill — the shared reference that **ponytail** + **ponytail-review** + the **design-* ** skills already enforce. Read it when reviewing code, shaping UI, or checking your own writing. | `skills/anti-slop/SKILL.md`

### project-memory (session memory — in `skills/`, auto-discovered)
- **project-memory** — Explicit cross-session project memory: `.planning/` (STATE.md live state, PROJECT.md, ROADMAP.md, REQUIREMENTS.md) + `docs/`. Use on greenfield bootstrap or when opening an existing project mid-work. Feed: Serena (how-to), ce-compound (solutions/), graphify (index the memory). | `skills/project-memory/SKILL.md`

### qmd (local markdown search — in `skills/`, auto-discovered)
- **qmd** — Query local markdown knowledge bases, notes, docs, wikis with QMD (BM25 + semantic + local LLM rerank, all local via node-llama-cpp). Use before web search when the answer may already be in indexed local files; also set up QMD access for a project. Prereq: `npm install -g @tobilu/qmd` (installed globally). Always: search → `qmd get`/`qmd multi-get` full source → answer citing paths/docids. MCP mode also available (`qmd mcp`). Prefer over the Obsidian CLI for search (instant, ranked). | `skills/qmd/SKILL.md`

### betterwright (persistent policy-guarded browser — in `skills/`, auto-discovered)
- **betterwright** — Drive a persistent, policy-guarded real web browser for live-web tasks (logging in, filling forms, booking, buying, reading a page an API won't give you). Native `browser`/`browser_download` tools are always loaded via `npm:betterwright`; this skill teaches the CLI + operate/safety rules. Use for anything needing the live web. | `skills/betterwright/SKILL.md`

### graphify (codebase knowledge graph — via `npm:graphify-pi`)
- **graphify** — Turn any folder of code/docs/papers/images/video into a persistent navigable knowledge graph (interactive HTML + GraphRAG JSON + plain-language GRAPH_REPORT.md), with query/path/explain. Use to index a codebase, answer architecture questions, or navigate relationships; semi-always-on via the graphify-pi extension (consult `graphify-out/wiki/index.md` → `GRAPH_REPORT.md` → `graph.json` before broad search; run `graphify update .` when code changed). Command: `/graphify <path>` / `--update` / `query` / `path` / `explain`. | `npm:graphify-pi`

### obsidian-cli (vault ops — in `skills/`, auto-discovered)
- **obsidian-cli** — Read/create/edit notes, tags, backlinks, tasks, plugin & theme dev in a running Obsidian vault. Use for vault *operations* (not search — that's `qmd`'s job). Requires Obsidian open. | `skills/obsidian-cli/SKILL.md`

### design-skills (curated index — in `skills/`, auto-discovered)
- **design-skills** — Pick the right design skill for a task instead of guessing. `impeccable` is the primary design engine (design / redesign / audit / polish any frontend UI); this index routes the rest — research (`user-research` / `research-synthesis`), Figma → code (`figma-to-code`), themes for decks/docs (`theme-factory`), visual canvases (`json-canvas`), dev handoff (`design-handoff`). Read it first when a task is "design X" / "audit this design" / "hand off this design". | `skills/design-skills/SKILL.md`

### impeccable (frontend design language — installs an engine binary on first run)
- **impeccable** — Design guidance for AI coding agents: 24 commands (craft/shape/critique/audit/polish/bolder/quieter/distill/animate/colorize/layout/typeset/delight/harden/onboard), 61 deterministic AI-design "tells," a craft floor (contrast/depth/spacing/type/motion/states/browser-surfaces bans), and Operate/Read/Persuade/Experience mode depth. Use to design, redesign, audit, or polish any frontend surface (dashboards, landing pages, app shells, forms, empty states). The launcher downloads a verified engine binary (sha256-checked) on first run; on Windows call `scripts/impeccable.cmd`. | `skills/impeccable/SKILL.md`

design (in `skills/`, auto-discovered — detailed rows in G-Stack section below)
- impeccable, frontend-design, figma-to-code, design-handoff, theme-factory, user-research, research-synthesis

### ponytail (mode — persistent guardrail — detailed rows in G-Stack section below)
- **ponytail**, ponytail-review, ponytail-audit, ponytail-debt, ponytail-gain, ponytail-help

### G-Stack: GSD Core + Compound Engineering + gstack (the full workflow stack)
These three are the same engineering discipline at different layers. Load order is the workflow:

**gsd-core** — the *orchestration layer*. Native `/gsd` command + `gsd_invoke` tool (a **programmatic command/tool**, NOT discoverable markdown skills — it drives the loop rather than being a row in the tables below). Spec-driven + context-engineering: drives *plan → execute → verify → release*. Installs via `npx @opengsd/gsd-core@latest --pi --global` → native extension at `~/.pi/agent/extensions/gsd.js`. Do **not** clone it manually or `pi install` it (its `prepare` = `tsc build` fails on npm `--omit=dev`). Companion hooks: `gsd-hooks` under `~/.pi/agent/gsd-hooks/`.

| Command | When to use | How it's reached |
|---|---|---|
| **`/gsd`** + `gsd_invoke` | Run any GSD command/tool — the meta-workflow hub | native command + tool (gsd-core) |
| `gsd-new-project` | Greenfield project bootstrap | native command |
| `gsd-onboard` | Onboard an existing codebase | native command |
| `gsd-spec` | Write a spec (the GSD spec-driven loop) | `gsd_invoke` family |
| `gsd-planning` | Plan the implementation | `gsd_invoke` family |
| `gsd-context-monitor` | Track/refresh context during work | `gsd_invoke` family |
| `gsd-review` | Structured review pass | `gsd_invoke` family |
| `gsd-release` | Orchestrate release | `gsd_invoke` family |

**superpowers** — the *engine that runs the loop* (method skills, discovered markdown). Loads when a task matches; mapped here as the execution backbone of the G-Stack. Installs via `pi install git:github.com/obra/superpowers`.

| Skill | When to use | Real location |
|---|---|---|
| writing-plans | After a design is approved — turns it into an implementation plan | `...\superpowers\skills\writing-plans\SKILL.md` |
| **test-driven-development** | Writing any feature/bugfix — tests before code (runs under `ce-work`) | `...\superpowers\skills\test-driven-development\SKILL.md` |
| executing-plans | Running a written plan in a separate session with review checkpoints | `...\superpowers\skills\executing-plans\SKILL.md` |
| **systematic-debugging** | Any bug/test failure — root-cause loop, not guess-and-patch | `...\superpowers\skills\systematic-debugging\SKILL.md` |
| subagent-driven-development | Executing a plan with independent parallel tasks | `...\superpowers\skills\subagent-driven-development\SKILL.md` |
| dispatching-parallel-agents | 2+ independent tasks sharing no state | `...\superpowers\skills\dispatching-parallel-agents\SKILL.md` |
| **verification-before-completion** | About to claim done/fixed/passed — run checks before asserting | `...\superpowers\skills\verification-before-completion\SKILL.md` |
| requesting-code-review | Done with work, want a review before merging | `...\superpowers\skills\requesting-code-review\SKILL.md` |
| receiving-code-review | Getting feedback, before applying suggestions | `...\superpowers\skills\receiving-code-review\SKILL.md` |
| finishing-a-development-branch | Work done, all tests pass — decide how to integrate | `...\superpowers\skills\finishing-a-development-branch\SKILL.md` |
| using-git-worktrees | Feature work needing isolation from the workspace | `...\superpowers\skills\using-git-worktrees\SKILL.md` |
| writing-skills | Creating/editing/verifying a skill | `...\superpowers\skills\writing-skills\SKILL.md` |

**ponytail** — the *persistent code-style guardrail* under the whole stack (active on every response). Installs via `pi install git:github.com/DietrichGebert/ponytail`.

| Skill | When to use | Real location |
|---|---|---|
| **ponytail** | Active on every response. Laziest working solution: stdlib/native first, delete over add, shortest diff. Off with `stop ponytail` / `normal mode`. | `C:\Users\MSI\.pi\agent\git\github.com\DietrichGebert\ponytail\skills\ponytail\SKILL.md` |
| ponytail-review | "review for over-engineering" — finds code to delete (reinvented stdlib, dead flexibility) | `...\ponytail\skills\ponytail-review\SKILL.md` |
| ponytail-audit | "audit this codebase" — full-repo over-engineering scan | `...\ponytail\skills\ponytail-audit\SKILL.md` |
| ponytail-debt | "ponytail debt" — collects deferred shortcuts into a ledger | `...\ponytail\skills\ponytail-debt\SKILL.md` |
| ponytail-gain | "ponytail gain" — the impact scoreboard | `...\ponytail\skills\ponytail-gain\SKILL.md` |
| ponytail-help | quick-reference card for all modes/commands | `...\ponytail\skills\ponytail-help\SKILL.md` |

**compound-engineering** — the *thinking-before-coding* method: intent-first planning, bounded phases, compound review, focus/work mode. Native pi extension (markdown skills). Installs via `pi install git:github.com/EveryInc/compound-engineering-plugin`.

| Skill | When to use | Real location |
|---|---|---|
| **ce-brainstorm** | Ambiguous/broad ask — intent-first kickoff, clarifies before planning | `.../EveryInc/compound-engineering-plugin/skills/ce-brainstorm/SKILL.md` |
| **ce-plan** | Approved intent — intent-first plan (context, scope, approach, WBS, checkpoints) | `.../EveryInc/compound-engineering-plugin/skills/ce-plan/SKILL.md` |
| **ce-work** | Executing a ce-plan (or any feature/bugfix) — phases 2/3/4, single-focus mode | `.../EveryInc/compound-engineering-plugin/skills/ce-work/SKILL.md` |
| **ce-code-review** | Done with code — intent-aligned review, not generic | `.../EveryInc/compound-engineering-plugin/skills/ce-code-review/SKILL.md` |
| **ce-compound** | Periodic multi-surface compound review across all open PRs | `.../EveryInc/compound-engineering-plugin/skills/ce-compound/SKILL.md` |
| **ce-ideate** | Divergent creative work, exploring many angles first | `.../EveryInc/compound-engineering-plugin/skills/ce-ideate/SKILL.md` |
| **ce-optimize** / **ce-simplify-code** / **ce-debug** | Tighten perf/memory, simplify, or debug | `.../EveryInc/compound-engineering-plugin/skills/ce-optimize/SKILL.md` etc. |
| **ce-prototype** | Prototype/scaffold before committing | `.../EveryInc/compound-engineering-plugin/skills/ce-prototype/SKILL.md` |
| **ce-riffrec-feedback-analysis** | Synthesize review feedback into a prioritized plan | `.../EveryInc/compound-engineering-plugin/skills/ce-riffrec-feedback-analysis/SKILL.md` |
| **ce-test-browser** | Browser E2E verification (`ce-work` phase-4 gate) | `.../EveryInc/compound-engineering-plugin/skills/ce-test-browser/SKILL.md` |
| **ce-commit** / **ce-commit-push-pr** / **ce-resolve-pr-feedback** / **ce-babysit-pr** / **ce-worktree** | Commit, PR, handle review feedback, long-lived PR | `.../EveryInc/compound-engineering-plugin/skills/ce-commit/SKILL.md` etc. |
| **ce-doc-review** / **ce-explain** / **ce-pov** / **ce-proof** / **ce-strategy** / **ce-handoff** / **ce-dogfood** / **ce-compound-refresh** | Docs, explain, POV, proof-of-work, strategy, handoff, dogfood, compound-refresh | `.../EveryInc/compound-engineering-plugin/skills/ce-doc-review/SKILL.md` etc. |
| **lfg** | Long-term focus guardrail (block context-switching) | `.../EveryInc/compound-engineering-plugin/skills/lfg/SKILL.md` |
| **council-mode**, **pi-subagents** (npm) | Parallel subagents for independent tasks | `npm:pi-subagents` |
| **ask-user** (npm) | Richer blocking multi-question flows | `npm:pi-ask-user` |

> Companion notes: `pi-subagents` (Task/TaskOutput) and `pi-ask-user` are optional — pi already ships `AskUserQuestion` natively, so `ce-brainstorm`/`ce-code-review` work without `pi-ask-user`. `pi-subagents` is the recommended companion for CE's subagent dispatch.

**gstack** (garrytan) — the *virtual engineering team*: CEO/designer/engineering-manager/reviewer/QA/security/release specialists, plus headless browser (`browse`), PDF (`make-pdf`), and diagrams. Native pi extension (symlinked skill dirs). Installs via `pi install git:github.com/garrytan/gstack` then `node_modules` removed (skills are pure markdown). See the router skill for full routing.

| Skill | When to use | Real location |
|---|---|---|
| **gstack** | Router — pick the right gstack skill | `.../garrytan/gstack/SKILL.md` |
| **autoplan** | Auto-review pipeline (CEO+design+eng+DX). **Escalate only** — PR is high-stakes/large/security-sensitive. Ordinary changes: `ce-code-review` alone. | `.../garrytan/gstack/skills/autoplan/SKILL.md` |
| **cso** | Security audit — OWASP + STRIDE. **Escalate only** when the change touches auth/secret/injection surfaces. | `.../garrytan/gstack/skills/cso/SKILL.md` |
| **review** | Engineering review (depth, risk, clarity). **Escalate only** — `ce-code-review` is primary for normal changes. | `.../garrytan/gstack/skills/review/SKILL.md` |
| **ship** | Ship the PR (title/body/labels/CI) | `.../garrytan/gstack/skills/ship/SKILL.md` |
| **land-and-deploy** | Deploy + verification + rollback | `.../garrytan/gstack/skills/land-and-deploy/SKILL.md` |
| **design-review** / **design-shotgun** / **design-html** / **design-consultation** | Design critique, adversarial design QA, ship design, consult | `.../garrytan/gstack/skills/design-*/SKILL.md` |
| **plan-eng-review** / **plan-ceo-review** / **plan-devex-review** / **plan-design-review** | Role-specific pre-shipping reviews | `.../garrytan/gstack/skills/plan-*/SKILL.md` |
| **plan-tune** | Tune the agent model/behaviors | `.../garrytan/gstack/skills/plan-tune/SKILL.md` |
| **qa** / **qa-only** | Full QA lead (open browser) / QA-only | `.../garrytan/gstack/skills/qa/SKILL.md` |
| **investigate** | Root-cause diagnosis (spec → PRD → design → plan) | `.../garrytan/gstack/skills/investigate/SKILL.md` |
| **guard** / **careful** / **freeze** / **unfreeze** | Review-guard, safe-mode edits, freeze context, unfreeze | `.../garrytan/gstack/skills/guard/SKILL.md` etc. |
| **office-hours** | CEO strategy + prioritization | `.../garrytan/gstack/skills/office-hours/SKILL.md` |
| **benchmark** / **benchmark-models** | Model benchmarking | `.../garrytan/gstack/skills/benchmark/SKILL.md` |
| **devex-review** / **diagram** | DX review, diagrams | `.../garrytan/gstack/skills/devex-review/SKILL.md` etc.
| **browse** / **open-gstack-browser** / **setup-browser-cookies** | Headless browser (needs logged-in browser) | `.../garrytan/gstack/skills/browse/SKILL.md` |
| **learn** / **retro** / **landing-report** / **spec** / **skillify** | Learn, retro, landing report, spec, skillify | `.../garrytan/gstack/skills/learn/SKILL.md` etc. |
| **rarely used (skip unless asked):** `ios-fix`/`ios-design-review`/`ios-clean`/`ios-qa`/`ios-sync` (iOS only), `codex` (OpenAI Codex CLI wrapper), `pair-agent` (remote pair-programming), `setup-gbrain`/`sync-gbrain` (codebase re-indexer — use **Serena** instead). | `.../garrytan/gstack/skills/...` |

## Workflow (one line each — full diagram + cross-links in `WORKFLOW.md`)
```
gsd:/gsd (hub) → ce-brainstorm (scope) → ce-plan → autoplan | gstack-router
Explore/index → **graphify** (persistent codebase knowledge graph) → **qmd** search (fallback **obsidian-cli** for unindexed vault bits)
ce-work (focus mode, tdd) → superpowers:systematic-debugging (clear failures)
ce-code-review (intent) → gstack autoplan (depth, only if PR needs it) → gstack ship + land-and-deploy
superpowers:verification-before-completion gates every done; gstack retro + benchmark closes it
```

### npm extensions (tools/hooks, not skills)
These provide persistent tools and lifecycle hooks, not loadable `SKILL.md` docs.
They're registered in `settings.json` `packages` but don't appear as skills here.
| Skill | When to use | Location |
|---|---|---|
| `npm:@bacnh85/pi-serena` | Semantic code tools (understand/refactor a codebase) via a persistent worker. Use for codebase architecture questions, refactors, or large multi-file changes. Binary: `serena` (also `serena-agent` on PATH). | `~/.pi/agent/npm/node_modules/@bacnh85/pi-serena/` |
| `npm:betterwright` | Persistent, policy-guarded web browser (network controls, trusted credential fill, proof screenshots, captcha). Native `browser`/`browser_download` tools always loaded; operator guidance lives in the lazy `skills/betterwright/SKILL.md`. Use for live-web tasks an API won't give you. | `~/.pi/agent/npm/node_modules/betterwright/` |

---

## Quick picks

- Fix a bug → **systematic-debugging** (not "guess and patch")
- Build anything → **ce-brainstorm** (superpowers:brainstorming is deprecated — see index), then **tdd** / **writing-plans**
- Over-engineered code → **ponytail-review**
- Index/understand a codebase → **graphify** (persistent knowledge graph, semi-always-on via graphify-pi)
- Search local markdown → **qmd** (instant, ranked); fallback **obsidian-cli** for vault bits the index lacks
- Boring/generic-looking UI → **impeccable** (design, redesign, polish, or run its 61-rule detector)
- Everything → **ponytail** is on by default; the ladder (skip → reuse → stdlib → native → dep → one line → minimum)
