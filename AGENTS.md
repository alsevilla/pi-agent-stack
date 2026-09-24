# Global Instructions

## Lazy skills — read this first

Most skills are **not** loaded at session start. `~/.pi/agent/skills/SKILLS.md`
is the index. **Read it** before picking up any method/over-engineering skill:
it names the right skill and points to its real `SKILL.md`.

### Why
Pi loads every package's skills at startup. To keep a plain session light, the
`obra/superpowers` package was removed from the always-on `packages` list, so
its skills load **0** at startup. When a task needs them, read `SKILLS.md`,
then the one `SKILL.md` it points to. The same rule applies to the G-Stack
skills (GSD Core, compound-engineering, gstack) — they're lazy too.

### What stays loaded
- `ponytail` (persistent mode, already in the system prompt) — on by default.
- Built-in skills in `~/.pi/agent/skills/` (obsidian-*, json-canvas, defuddle,
  design-*, ui-ux-pro-max, frontend-design, full-stack-e2e-review)
  — auto-discovered.
- Extensions loaded at startup (always-on tools/lifecycle, not lazy skills —
  keep in `packages`; do not remove to slim down): graphify-pi, pi-serena,
  gsd-core (`/gsd`), compound (`ce-*`), gstack (router + specialists),
  pi-subagents, pi-ask-user, betterwright (the `browser`/`browser_download`
  tools — operator guidance is the lazy `skills/betterwright/SKILL.md`).

> **Browser verification → betterwright, never the native `browser` tool.**
> For any "does this render / does the UI work" check in this repo, drive the
> browser with `betterwright run -c "..."` (see `skills/betterwright/SKILL.md`),
> not the built-in `browser` tool. The native tool has been unreliable here
> (empty calls, token-limit truncation). `betterwright run -c` runs snippets in
> a restricted sandbox: use `page.evaluate(() => ...)` to read/write the page,
> and avoid inline `$$eval`/`$eval` callbacks (the runner mangles them).

### What is lazy (read `SKILLS.md`, then load the one you need)
- **superpowers** system (brainstorming, writing-plans, TDD, systematic-debugging,
  verification, code-review…) — on demand via `SKILLS.md`.
- **GSD Core** commands (`/gsd-new-project`, `/gsd-onboard`, `gsd-spec`…) — on
  demand; `/gsd` is the hub for the rest.
- **compound-engineering** (`ce-brainstorm`, `ce-plan`, `ce-work`, `ce-code-review`,…)
  — on demand via `SKILLS.md`.
- **gstack** (`gstack` router + autoplan/cso/review/ship/qa/…) — on demand.
- Ponytail sub-skills (ponytail-review, -audit, -debt, -gain, -help) — loaded
  on demand via `SKILLS.md`.

### Workflow
A task needs a method → read `SKILLS.md` → read the matching `SKILL.md` →
proceed. The index lists skill, when-to-use, and path for every system.

## PR workflow
`~/.pi/agent` is a git clone of the main repo. **Never push straight to
`master`** — every change ships as a PR against `master`.

1. `git checkout -b <short-slug>` (new branch off `master`)
2. make changes, `git add -A`
3. `git commit -m "type(scope): imperative, value-first subject"`
4. `git push -u origin <branch>`
5. `gh pr create --base master --title "<subject>" --body "<what + why>"`

### Config (for reference)
- Always-on packages: `~/.pi/agent/settings.json` → `packages`.
- Remove a package from that list to make it fully lazy.
- **Do not remove `npm:graphify-pi` or `npm:@bacnh85/pi-serena`** — they are
  always-on extensions (tools + lifecycle), not lazy markdown skills. Slimming
  the list only targets lazy skill packages (e.g. superpowers, G-Stack).
