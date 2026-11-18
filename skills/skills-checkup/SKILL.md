---
name: skills-checkup
description: Re-sweep the global skill registry against mapped repos — report missing, stale, or orphaned skills and refresh SKILLS-MAP. Load when adding, moving, or retiring any skill, or on wrap-up drift checks.
---

# Skills checkup (global-only routine)

One copy, lives here. It operates *on* repos from outside — never
duplicate it per repo (that recreates the drift it exists to fix).
Each repo carries only the output: a pointer plus its last-sync note.

## Procedure

1. Read `SKILLS-MAP.md` (registry) + global `skills/*/SKILL.md`
   frontmatter (`name` + `description`).
2. Per mapped repo: list its `skills/` dirs, confirm each has
   `SKILL.md`, grep `AGENTS.md`/docs for skill-id references.
3. Report three lists, always: **missing** (global skill the repo
   should adopt) / **stale** (description or behavior drifted from
   the canonical copy) / **orphaned** (repo references a retired id,
   or a dir has no `SKILL.md` and no owner flag).
4. Refresh `SKILLS-MAP.md` rows + Freshness date in the same session.

## Boundaries

- Report first, edit on explicit go — never auto-move or auto-delete
  another repo's skills (deletion diffs first; divergent copies may
  carry owner history).
- Untracked mid-session work dirs (e.g. `temp-data/`, active
  `all-creative/` trees) are not drift — leave them alone.
- Applied here 2026-11-15: first pass caught marketer `tiktok-ads`
  present on disk but missing from the map row — added.
