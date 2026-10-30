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

## Index

* `calendar-picker` — date-range picker pattern
* `creative-analysis` — creative-analysis tool + online creative module
* `neon-db` — Neon conventions (migrations, branches, patterns)
* `session-handoff` — end-of-session wrap-up ritual
* `telegram-rich` — Telegram delivery rules
* `tiktok-ads` — TikTok Ads measurement/creative/audience/bidding
* `tiktok-api` — verified TikTok API shapes
* `tiktok-shop` — verified TikTok Shop API shapes
* `ttam-metrics` — TTAM glossary + kill/scale/watch verdicts
* `vercel-deploy` — Vercel deploy ritual + Hobby caps
