# custom-pi-agent-config

A curated, optimized skill stack for the **pi coding agent** (`~/.pi/agent`).
It trims redundancy from the default superpowers / compound / gstack /
ponytail / design stack, adds session memory + anti-AI-slop rules, and pins a
set of plugins.

> This repo stores only the **config** (`skills/`, `gsd-core`, `gsd-hooks`,
> `scripts/`, `extensions/`, `settings.json`, `mcp.json`, bundled CLIs).
> Caches, model stores, sessions, and secrets (`auth.json`) are git-ignored.

---

## Install

Everything installs into `~/.pi/agent`. pi discovers plugins listed in
`settings.json` → `packages`. Install each plugin once (they only need to exist
on disk), then restart pi — the package auto-adds itself to `settings.json`.

### Step 1 — Install plugins

Run these once. Each prints how to register itself; follow the prompt (or add
the line to `packages` in `~/.pi/agent/settings.json`).

| Plugin | Install command |
|--------|-----------------|
| **gstack** (router + specialists: autoplan, review, cso, ios, benchmark…) | `git clone https://github.com/garrytan/gstack ~/.pi/agent/git/github.com/garrytan/gstack` |
| **gsd-core** (spec/planning/execute/verify workflows, prompt refs) | `npx @opengsd/gsd-core@latest --pi --global` |
| **compound-engineering** (ce-brainstorm, ce-plan, ce-work, ce-code-review…) | `pi install git:github.com/EveryInc/compound-engineering-plugin` |
| **ponytail** (lazy-dev review mode) | `pi install git:github.com/DietrichGebert/ponytail` |
| **pi-serena** (code navigation, symbol editing) | `pi install npm:@bacnh85/pi-serena` |
| **pi-serena-hooks** | `pi install npm:@lystran/pi-serena-hooks` |
| **pi-obsidian** (Obsidian vault CLI) | `pi install npm:@bacnh85/pi-obsidian` |
| **pi-frontend-design** (frontend UI skill) | `pi install npm:@sentiolabs/pi-frontend-design` |
| **pi-subagents** (delegate to child agents) | `pi install npm:pi-subagents` |
| **pi-ask-user** (interactive multiple-choice prompts) | `pi install npm:pi-ask-user` |
| **pi-mcp-adapter** (MCP gateway) | `pi install npm:pi-mcp-adapter` |
| **pi-llama-cpp** (local model backend) | `pi install npm:pi-llama-cpp` |

### Step 2 — Install bundled CLIs (optional)

`bin/` holds CLIs the stack relies on. If your system already provides them,
skip. The `go` / `gopls` entries are thin wrappers that resolve to your PATH.

```bash
# gh  — GitHub CLI  (gstack uses it for PRs)
# fd  — fast file finder (ripgrep-alt drop-in)
# Drop the .exe files somewhere on your PATH, e.g.:
cp bin/gh.exe bin/fd.exe /usr/local/bin/
```

### Step 3 — Register packages

If a plugin didn't auto-add itself, add it to `packages` in
`~/.pi/agent/settings.json`:

```jsonc
"packages": [
  "npm:pi-llama-cpp",
  "git:github.com/DietrichGebert/ponytail",
  "npm:@sentiolabs/pi-frontend-design",
  "npm:@bacnh85/pi-serena",
  "npm:pi-mcp-adapter",
  "npm:@lystran/pi-serena-hooks",
  "npm:@bacnh85/pi-obsidian",
  "git:github.com/EveryInc/compound-engineering-plugin",
  "npm:pi-subagents",
  "npm:pi-ask-user",
  "git:github.com/garrytan/gstack"
]
```

Then restart pi.

---

## What's in this repo

### `skills/` — the pi skill index

The heart of the stack. pi reads `skills/SKILLS.md` as the index; each entry
points at a `SKILL.md` that loads on demand.

- **Trimmed index** — the default stack had redundant entry points. This index
  collapses them:
  - `superpowers:brainstorming` is marked deprecated → `ce-brainstorm` is the
    sole primary brainstormer.
  - gstack `autoplan` / `review` / `cso` are **escalate-only** →
    `ce-code-review` handles normal changes.
  - Niche gstack rows (ios-fix/qa/design-review/clean/sync, codex, pair-agent,
    gbrain setup/sync) are folded into one "rarely used" row.
  - Design skills collapsed onto one engine: `impeccable` does design /
    redesign / audit / polish for any frontend UI, so 9 redundant design
    skills were removed from disk (`anthropic-frontend-design`,
    `redesign-existing-projects`, `design-taste-frontend`,
    `design-design-critique`, `vercel-web-design-guidelines`, `design-system`,
    `ux-copy`, `ux-flow-wireframer`, `accessibility-review`). The
    `design-skills` index now routes research (`user-research`,
    `research-synthesis`), Figma → code (`figma-to-code`), themes
    (`theme-factory`), canvases (`json-canvas`), and handoff
    (`design-handoff`) around it.
- **`project-memory/`** — session memory convention. Copies `.planning/`
  (`STATE.md`, `PROJECT.md`, `ROADMAP.md`, `REQUIREMENTS.md`) into a project,
  read-at-start / append-at-end, and feeds Serena / ce-compound / graphify.
  Templates live under `project-memory/templates/planning/`.
- **`anti-slop/`** — anti-AI-slop rules (27 code rules + UI taste + banned
  phrases + comms style). Modeled on `uncodixfy`; wired as a shared checklist,
  pointing back to `ponytail` (code) and the design skills (taste), not as a
  parallel authority.
- **`WORKFLOW.md`** — the full workflow diagram + cross-links + deprecations,
  moved out of the index to keep the index lean.
- Design skills: `impeccable` is the primary design engine; the rest
  (`user-research`, `research-synthesis`, `figma-to-code`, `theme-factory`,
  `json-canvas`, `design-handoff`) are routed through the `design-skills`
  index. Obsidian / ponytail / subagents skills are unchanged references from
  upstream. graphify is provided by `npm:graphify-pi`.

### `WORKFLOW.md`

Full diagram of how the stack's pieces connect (brainstorm → plan → spec →
code → review → verify → ship) and which skill owns each step.

### `gsd-core/`

The GSD Core plugin's shipped content: workflow prompts, gate/reference
markdown, and templates (AI-SPEC, state, roadmap, ADRs, verification reports…).
Installed via `npx @opengsd/gsd-core@latest --pi --global`.

### `gsd-hooks/`

Node/Shell hooks that wire gsd into your editor: pre/post tool guards, session
state, graphify updates, status line, update checks, write/commit guards.

### `scripts/`

Tooling: `changeset/` (versioning + release notes), capability-registry and
loop-contract generators, slash-command fixer.

### `extensions/`

pi extension manifests.

### `bin/`

Bundled CLIs: `gh.exe` (GitHub CLI), `fd.exe` (file finder), plus `go` /
`gopls` wrappers. Optional if your system already has these.

### Installed CLI: qmd

`@tobilu/qmd` is installed globally (via `npm install -g @tobilu/qmd`) and is
exposed as a pi skill (`qmd`) — a local markdown search/RAG CLI (BM25 + semantic
+ LLM reranking, all local via node-llama-cpp).

```bash
qmd collection add ~/notes --name notes   # index a folder of documents
qmd context add qmd://notes "Personal notes and ideas"
qmd search "how do I reset the plan"       # hybrid search
```

Upgrade with `npm install -g @tobilu/qmd@latest`. Lives in the global npm
prefix (resolved from PATH), so nothing to make portable here.

### `settings.json`

pi config: theme, thinking-budget tiers, and the `packages` list that pins the
installed plugins.

### `mcp.json`

MCP server registrations (graphify, serena).

### Root files

`AGENTS.md` (global instructions + lazy-skills guide), `package.json` /
`package-lock.json` (local npm deps), `gsd-file-manifest.json` (gsd file index).

---

## Updating

Updates depend on how each plugin was installed — npm packages vs git clones.

### npm packages (auto-update)

These are versioned npm packages. pi installs the pinned version once; to get
newer versions, update them and let pi re-register.

```bash
pi update npm:@bacnh85/pi-serena          # or: npm update -g <pkg>
```

Then restart pi — it re-reads the installed version and adds the line back to
`settings.json` `packages` if needed. To pin a specific version, edit the entry
to e.g. `npm:@bacnh85/pi-serena@0.4.0`.

> npm packages here: pi-llama-cpp, pi-frontend-design, pi-serena,
> pi-serena-hooks, pi-obsidian, pi-mcp-adapter, pi-subagents, pi-ask-user.

### git packages (track a branch)

These are cloned from GitHub and referenced by repo URL. They update when the
upstream branch moves. gstack and compound-engineering and ponytail live under
`~/.pi/agent/git/github.com/<owner>/<repo>/`.

```bash
cd ~/.pi/agent/git/github.com/garrytan/gstack
git pull            # fetch upstream changes into your local clone
# restart pi to pick up the new code
```

> git packages here: ponytail, compound-engineering-plugin, gstack.

### gsd-core (npm, npx-managed)

gsd-core was installed via `npx @opengsd/gsd-core@latest --pi --global`. It
ships as workflow/prompt markdown and hooks. To refresh:

```bash
npx @opengsd/gsd-core@latest --pi --global    # re-run to pull latest
```

### This repo's config (skills/, settings.json, mcp.json)

These lines are *yours*. When an upstream plugin updates, only its own code
changes — it does **not** touch `skills/SKILLS.md`, `settings.json`, or
`mcp.json`. So:

- Upstream plugin updates → **safe, won't break this config**. The index still
  points to the same skill names.
- This repo gets new/changed skills (e.g. a future SKILLS.md tweak) → pull and
  merge manually. Merge conflicts here mean two sides edited the same pointer;
  resolve by keeping the intended skill row.

## Updating the bundled CLIs

`gh.exe` and `fd.exe` in `bin/` are static binaries — no auto-update. To get
newer versions, re-download from their releases and replace the file. If your
system already has `gh`/`fd` on PATH, you can drop these entirely
(`git rm --cached bin/gh.exe bin/fd.exe`).

## Reverting / editing

The index in `SKILLS.md` is the source of truth. A skill can be removed from
disk (as with the 9 redundant design skills folded into `impeccable`) — restore
it by re-adding its files and its row in `SKILLS.md`. To deprioritize a skill
without deleting it, edit its row instead. The `.planning/` memory files in any
project are yours; `STATE.md` is append/update-only (never rewritten) to
preserve history.
