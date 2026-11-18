# DEV_NOTES.md — agents_skills

## Checkpoint 3 — 2026-11-15 (relay check + skills-checkup)

Owner-driven follow-ups from a marketer session, all uncommitted. `browser-access` gains a Relay section (`pair --list` as first move: auto-starts stopped relay + shows pairing/`last seen`; stale `last seen` = extension not phoning home; `serve`/autostart opt-in with pros/cons). New global `skills-checkup` routine (operate-on-repos, never per-repo copies) + registered in SKILLS-MAP; first pass: marketer `tiktok-ads` on disk but missing from map row — added. `claude system/` bundle left untouched (other session active).

## Checkpoint 2 — 2026-11-14 (global-only skills consolidation)

Follow-up to Cp1, same session. Owner ordered per-repo `session-handoff` / `browser-access` copies removed, global registered set only. Sparring mode was on for the mapping design (challenged reader/scope/freshness assumptions); landed: root `SKILLS-MAP.md`, remote-URL keyed, no local paths, no Notion wiring.

### What shipped (all uncommitted, nothing pushed)

- Deleted 5 dirs: marketer `skills/session-handoff` + `skills/browser-access`, unija-map both, haji `skills/session-handoff`. Verified via `git status` in all 4 repos (marketer shows D x2 among its big pre-existing dirty tree; unija-map/haji trees otherwise clean).
- Salvage before delete: local copies were divergent rituals (End-of-day, B69+, smoke codes) vs generic global. Method-agnostic safety rules folded into global `browser-access` driving rules (agreed tabs, close after, never kill Chrome, never sign in, describe-then-act). Marketer `AGENTS.md:24` repointed to the global skill. Repo-specific numbers already live in those repos' own DEV_NOTES.
- New `SKILLS-MAP.md`: global 4 + per-repo table (marketer 12 + 1 skill-less folder flagged; dev/unija-info no dir; unija-map+haji dirs now empty) + global-only policy + freshness rule. `session-handoff` Step 5b hooks the refresh.
- Not checked: unija-map DEV_NOTES history still references local skills (left as history); haji `opencode.json` still wires now-empty `./skills` (harmless, global resolves; removal is owner call); marketer grew new untracked `all-creative/` dirs mid-session (not mine — owner or another agent active in parallel).
- Step 5c Notion: skipped with reason — touched mapped repo (marketer) got config/deletion edits only, no queue-worthy shipped work or new threads.

### Bugs + lessons

7. Sparring-mode finding that held up: a static map rots unless something owns refresh — hence the Step 5b hook, not just the file. A map without a refresh rule is a liability, not an asset.
8. Deletion diffs first, always: the "identical" local skills turned out to be divergent rituals with owner history (`don't touch` notes in unija-map DEV_NOTES). User overrode explicitly; without that, deleting would have been wrong.
9. `git status` per repo before wrap-up caught parallel activity (marketer `all-creative/` appeared mid-session). Never assume a dirty tree is all yours.

### Open threads

- Owner: commit/push rounds for agents_skills (Cp1+Cp2 batch), marketer, unija-map, haji — 4 separate decisions, nothing staged anywhere.
- haji `opencode.json` `./skills` wiring vs empty dir — tidy-up is owner call.
- `0-tiktok-agentic-hub-library/` still has no SKILL.md (flagged in map, owner call whether to write or drop it).

## Checkpoint 1 — 2026-11-14 (browser + Notion todo system build-out)

Big build session, all output uncommitted per standing rule. Arc: paired a 3rd Chrome profile → proved Notion MCP → mapped repos to Notion todo pages → swept 90 marketer todos → triaged with live % → converted to Notion databases → new `notion-mcp-todolist` skill → built the unija queue → closed the SALASILAH cron question from history. Mood: fast, user driving scope ("go"), me executing; two Plan-mode interludes, both exited cleanly.

### What shipped (all uncommitted, nothing pushed)

- Browse: paired `chrome-pc-ikram-3` (`0.2 Ikram`, ikram.mdzmn00@gmail.com, Profile 2). Mapping appended in `skills/browser-access/SKILL.md` + `~/.opencode/browse-this-pc.md` (session `quiet-comet-713`).
- Notion marketer queue: `Marketer Todos` (52 rows: P0 3 / P1 12 / P2 29 / Park 8) + `Marketer Todo Folders` (5 rows, Done %/Open/Total rollups), 5 views on `todo draft` (progress on top). P1 Seq 1–12 sorted; Status select added.
- Notion unija queue: `Unija Todos` (10 rows: P1 4 / P2 3 / Park 3) + `Unija Todo Folders` (2 rows), 4 views on UNIJA page (the `to-do-unija-draft` link is a form database and cannot host linked views — views live one level up).
- Skills: new `skills/notion-mcp-todolist/` (generic method + canonical mapping); `session-handoff` Step 5c repointed to row ops, mapping moved out; local mirror moved to `~/.opencode/notion-mcp-todolist-this-pc.md` (old session-handoff mirror deleted).
- Closed from history: SALASILAH `check cron job github` — answered from `haji-awang-family` DEV_NOTES Cp1 (external cron primary, GitHub backup). Left for owner: tick the box, keep-alive.yml cleanup.

### Bugs + lessons

1. Plan-mode file locks are real (edit/write blocked outside plan dir) — respect them, never shell around; report + hand exact diffs to a build agent.
2. Check Notion entity type before placing views: form/survey databases reject linked views. Fallback is the nearest regular parent page.
3. `notion-update-page` `replace_content` needs `new_str`, not `content`; `update_content` with exact old_str moves blocks (used for view reorder).
4. Notion build order: Folders db → folder rows → Todos db with DUAL relation → rollups (`percent_checked`/`unchecked`/`count` all valid) → rows → views (progress first, appends go last).
5. Folder name lies: `marketer/` is `ikrammdzmn/marketer`, `agents_skills/` is `eymdvz/agents_skills` — `git remote -v` is the recognition key, always.
6. QA checklists are not todos: unija-map's 100 `- [ ]` are manual test scripts — import the 3 DEV_NOTES items, reference the files, don't flood rows.
7. Sweep scope honesty: count active planning files only for %, exclude changelog history + parked, or the number flatters (2-gmvmax read 88% on history).

### Open threads

- Owner: tick SALASILAH box; keep-alive.yml delete-or-daily-ify; marketer P0 secrets-verify + dirty-tree commit approval (33 modified + ~18 untracked, last commit bb98404).
- Pending builds: dev repo (`MAMTJ6/dev`) Todos pair; marketer draft header % is a snapshot (refresh on wrap-ups); `to-do-unija-draft` form-db restructure (user decision).
- Skill debt: none known; Step 5c + mapping verified in place.
