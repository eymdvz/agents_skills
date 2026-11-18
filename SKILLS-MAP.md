# SKILLS-MAP — all skills, global + per repo

Owner overview dashboard, not ground truth. Ground truth is each
`SKILL.md` + agent auto-discovery (descriptions). Keyed by GitHub
remote (universal); local paths differ per PC — resolve via the
`~/.opencode/*-this-pc.md` mirrors, never written here.

## Global (registered set — lives in this repo)

| Skill | Purpose | Home |
|---|---|---|
| `session-handoff` | End-of-session wrap-up ritual | `skills/session-handoff/` |
| `git-clone-setup` | Post-clone Git/GCM + repo-local identity (Windows) | `skills/git-clone-setup/` |
| `browser-access` | Real-Chrome driving via browse relay (per-profile pairing, per-PC mapping) | `skills/browser-access/` |
| `notion-mcp-todolist` | Repo TODO queues in Notion (sweep, triage, live % rollups) | `skills/notion-mcp-todolist/` |
| `skills-checkup` | Registry-vs-repo drift sweep (missing/stale/orphaned) + map refresh | `skills/skills-checkup/` |

## Per repo (repo-local skills only)

| Repo (remote) | Local skills | Notes |
|---|---|---|
| github.com/ikrammdzmn/marketer | `tiktok-api`, `tiktok-ads`, `tiktok-ads-mcp`, `tiktok-shop`, `vercel-deploy`, `neon-db`, `creative-analysis`, `telegram-rich`, `calendar-picker`, `ttam-metrics`, `tiktok-ads-analysis`, `ttam-bc-analysis`, `chart-legend-gating` | `0-tiktok-agentic-hub-library/` has no SKILL.md (invisible to discovery) |
| github.com/MAMTJ6/dev | — | no `skills/` dir (surveyed 2026-11-14) |
| github.com/unija-info/unija-info | — | no `skills/` dir (surveyed 2026-11-14) |
| github.com/unija-info/unija-map | — | `skills/` dir exists but empty (local copies removed 2026-11-14) |
| github.com/eymdvz/haji-awang-family | — | `skills/` dir exists but empty (local copy removed 2026-11-14) |

## Policy (decided 2026-11-14)

`session-handoff` and `browser-access` live here only — never
duplicated per repo (project config resolves them from the global
set). Past local copies were older/divergent rituals; the rule stops
them reappearing unnoticed. Repo-specific bits belong in that repo's
own `AGENTS.md`/docs, not in a shadow skill.

## Freshness

Last refresh: 2026-11-15 (added `skills-checkup`, caught marketer `tiktok-ads` gap).
Hand-maintained. When skills are added, removed, or re-homed, update
this file in the same session (wrap-up Step 5b covers it). If in
doubt, re-sweep: global `skills/` + each mapped repo's `skills/`.
