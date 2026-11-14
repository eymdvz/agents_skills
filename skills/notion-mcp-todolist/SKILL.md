---
name: notion-mcp-todolist
description: Repo TODO queue in Notion via MCP — sweep repo checkboxes, triage P0/P1/P2/Park, write Todos/Folders database rows, live % rollups. Load when gathering, reviewing, or wrapping up repo todos.
---

# Notion MCP todolist (generic)

One method per repo queue. Marketer is the worked instance; repeat per repo.

## Databases (per repo queue)

- `<Repo> Todos`: Name TITLE, Done CHECKBOX, Priority
  SELECT(P0/P1/P2/Park), Status SELECT(Todo/Doing/Blocked/Done),
  Seq NUMBER, Owner SELECT(owner/agent), Source RICH_TEXT,
  Folder RELATION→Folders DUAL.
- `<Repo> Todo Folders`: Name TITLE + rollups off the Todos
  relation: Done % percent_checked, Open unchecked, Total count.
  Done drives %; Status is working state.

## Sweep (read-only)

Count `- [ ]`/`- [x]` in active files only (`plan.md`,
`APP_CHECKLIST.md`, `discussion.md`, `SECURITY.md`).
Changelog/DEV_NOTES history excluded. Parked items (parked,
out-of-scope, blanks, conditional-only, pure notes) excluded from %.

## Triage

P0 today (verify-first, needs-approval) · P1 owner batch (one live
session, Seq 1..N, view SORT BY Seq ASC) · P2 engineering queue
(agent-workable) · Park appendix. Dedupe repeats (secrets, auth).
Every row: Priority + Owner + Source `file:L#` + Folder link
(unlinked rows miss %).

## Wrap-up hook

For each touched repo: add rows / tick Done / flip Status. Never
rewrite the page body; % recomputes itself. Verify with row counts
per Priority and per Folder (must match sweep).

## Views (per draft page)

Folder progress (live %) on top, then P0 / P1 (sorted by Seq) /
P2 / Park tables. Linked views only; databases live at workspace
level, draft page is the entry point.

## Mapping (canonical — this table is the truth)

| GitHub remote | Repo role | Parent Notion page | Draft page | Todos data source | Folders data source |
|---|---|---|---|---|---|
| github.com/ikrammdzmn/marketer | marketer repo | To do Work `3e433d51-8ddd-80b4-a48b-c12c2fd637ac` | todo draft `41833d51-8ddd-80cb-b9cc-ef7ddf842814` | `collection://41833d51-8ddd-81c4-aa16-000b3e08ed16` | `collection://41833d51-8ddd-815b-ac05-000bad01fd56` |
| github.com/MAMTJ6/dev | dev repo | TO DO MAMTJ6 `3e533d51-8ddd-80fc-8dcc-c625fa328c32` | — | — | — |
| github.com/unija-info/unija-info | other repo | Side Project / UNIJA `3e833d51-8ddd-806d-9af4-d63c6605b74c` | unija draft `41833d51-8ddd-8075-adb3-cdad06d409e6` (form db, views live on UNIJA page) | `collection://41833d51-8ddd-8184-b9f7-000b09f05ccf` | `collection://41833d51-8ddd-8174-984d-000b75197b65` |
| github.com/unija-info/unija-map | other repo | Side Project / UNIJA `3e833d51-8ddd-806d-9af4-d63c6605b74c` | unija draft (same form db, views on UNIJA page) | `collection://41833d51-8ddd-8184-b9f7-000b09f05ccf` | `collection://41833d51-8ddd-8174-984d-000b75197b65` |

New repo: verify `git remote -v` (remote URL is the key, not the
folder name), create the pair, seed rows, then append one row here.
Per-PC local paths live in
`~/.opencode/notion-mcp-todolist-this-pc.md` (one-way: this table →
local mirror).
