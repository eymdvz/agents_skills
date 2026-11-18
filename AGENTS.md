# AGENTS.md — agents_skills conventions

Central skill collection. Terse, verified-only, deltas only.

## Layout

* `skills/<skill-id>/SKILL.md` (+ optional `references/`, `scripts/`)
* ID = folder name, `lowercase-kebab-case`, case-sensitive
* Every `SKILL.md` needs frontmatter `name` + `description`
  (no `description` = no auto-discovery)

## Rules

* Update a skill in place; one delta per skill, same terse style as the file
* Verified-only: green probes/deploys in, guesses out
* `DEV_NOTES.md`: update if it exists; if missing, ask permission before creating
* Never stage, commit, or push unless explicitly asked

## Index (global-safe only)

* `session-handoff` — end-of-session wrap-up ritual
* `git-clone-setup` — post-clone Git/GCM + repo-local identity setup (Windows)
* `browser-access` — real-Chrome driving via browse relay (per-profile pairing, per-PC mapping)
* `notion-mcp-todolist` — repo TODO queues in Notion (sweep, triage, live % rollups)
* `skills-checkup` — registry-vs-repo drift sweep + map refresh

Per-repo `skills/` dirs hold repo-local skills only; `session-handoff`
and `browser-access` live here (global registered set) and must not be
duplicated per repo.

Repo-local skills (marketer, haji-awang-family, etc.) live in each
repo's own `skills/` + per-project `skills` entry, not here.
