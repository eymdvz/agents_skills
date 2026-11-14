---
name: browser-access
description: Drive the user's real Chrome via the browse extension/relay on any PC — install, pair profiles, per-PC mapping, sessions. Load before any browser-driving task or when browser setup comes up.
---

# Browser access (browse relay)

The agent drives the user's real Chrome-family browser through the `browse`
extension: logins, extensions and open tabs are already there, the user can
watch or take over. Each Chrome **profile** pairs separately; each pairing
gets a stable browser id (`chrome-<machine>[-2]`, machine name slugged).

## Install (per PC, per profile)

1. In the target Chrome profile, open the browse connect page.
2. Agent runs: `irm https://opencode.ai/browse/install.ps1 | iex`
   (Windows; use the platform's documented equivalent elsewhere).
3. If the page says the browser isn't paired, agent runs
   `<bindir>\browse.exe pair` → prints one-time `XXXX-XXXX` code
   (valid 10 min) → user enters it on the page → Pair.
4. Agent verifies: `status` lists the new browser id.

## Mapping (canonical — this table is the truth)

| PC | Chrome profile | Gmail | Browse id |
|---|---|---|---|
| Pc_Ikram | 0.0 Eymdvz | darkvadez00@gmail.com | chrome-pc-ikram-2 |
| Pc_Ikram | 0.1 Marketer | ads.himproduct01@gmail.com | chrome-pc-ikram |
| Pc_Ikram | 0.2 Ikram | ikram.mdzmn00@gmail.com | chrome-pc-ikram-3 |

New PC/profile: install + pair, then append one row here.

## Machine-local note

Each PC keeps `~/.opencode/browse-this-pc.md`: this PC's rows only,
plus `sync:` (date copied from this table) and a pointer back here.
Direction is one-way: repo table → local mirror (manual copy).

## Driving rules

- Sessions are per-browser: `session_new` with the browser id; a session
  stays in its browser. Name sessions/profiles by the Chrome profile
  name (`0.0 Eymdvz`), never by bare browser id, in user-facing text.
- To see a user tab: user attaches via the extension toolbar, agent
  `session_adopt` (with `targetUrl` if several are attached).
- Settings (`window`, `grouping`) are user-owned: read to explain where
  tabs land, never change unasked.
- `status` before assuming which browsers exist; ids differ per machine.
