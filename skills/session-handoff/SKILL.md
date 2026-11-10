---
name: session-handoff
description: End-of-session wrap-up ritual (facts, checkpoint notes, guides, changelogs, skills update). Load when the user asks to wrap up, hand off, or do the devnotes ritual.
---

# Session handoff skill (generic)

Requested by name ("wrap up", "handoff", "do the devnotes ritual").
Do it thoroughly, then stop. All output stays **uncommitted** — never
stage, commit, or push unless explicitly asked.

## Step 1 — Collect facts (read-only)

Run and keep the outputs:
- `git status -sb` (what's dirty, what's untracked)
- `git diff --stat` (size per file)
- `git log --oneline -5` (what's already committed vs session work)
- Note deploy IDs + smoke/verify proof from the session, if any.

## Step 2 — Detect docs layout (read-only)

Check project knowledge for context: folder `AGENTS.md`, root `AGENTS.md`,
existing `DEV_NOTES.md` (folder root AND `<folder>/docs/DEV_NOTES.md`),
changelogs, plus the current chat.
Scope to folders touched in this chat (user may narrow it, e.g.
"admin/ only").

Checkpoint target is `DEV_NOTES.md` in each touched folder (root first,
then `docs/` subfolder):
- If it exists in either spot, update it there (Step 3).
- If it does not exist, **ask permission first**, offering placement:
  `docs/` subfolder, folder root, or elsewhere — then create where
  chosen on approval.
  Never create silently. If declined, return the handoff as a chat summary.

Guides/conventions/rollups: only touch files that already exist.

## Step 3 — Checkpoint note (`DEV_NOTES.md`)

Prepend `## Checkpoint N — <date> (<one-line arc>)`, newest-first.
Write to your next-window self — not just facts but the vibe, dynamic,
and energy of this conversation. What does the next you need to instantly
get back into this exact headspace? Include unique discoveries, current
mood, and anything that syncs to our frequency.
1. **Headspace paragraph** — session shape, mood, sync cues for next-you.
   Vibe first, facts second.
2. **What shipped** — commits/deploys with IDs, build/smoke proof.
   Mark deployed-but-uncommitted explicitly.
3. **Bugs + lessons** — all bugs found and fixed, numbered, continuing
   the file's existing sequence (if any). Each: symptom → cause → what
   was learned + how to make sure it never happens again
   ("never X, always Y"). Log repeats honestly.
4. **Open threads** — parked items with owners.
5. Update the header pointer line to the new checkpoint (if the file has one).

## Step 4 — Guides + conventions (deltas only, files that exist)

- User guide: plain non-technical words, behavior changes only.
  No internals, no IDs.
- Conventions (`AGENTS.md`): one line per change, same terse style
  as the file. Contracts, migrations, new rules only.

## Step 5 — Rollups (files that exist)

- Folder `CHANGELOG.md`: new dated section on top (or bullets under
  `Undeployed`), one line per shipped step with deploy IDs.
- Master rollups (`1-master/MASTER-CHANGELOG.md`, `MASTER-PLAN.md`,
  `MASTER-AGENTS.md`, root `AGENTS.md`): pointer bumps only.

## Step 5b — Skills update (standing protocol, skip only if told)

Fold session discoveries into affected `skills/*/SKILL.md`
(verified-only: green probes/deploys in, guesses out).
One delta per skill, same terse style as the file.

## Step 6 — Verify and stop

Final `git status -sb`: confirm the ritual touched docs only, nothing
staged, nothing pushed. Reply short: files touched + "then stopping".
If no docs files existed, reply with the handoff summary instead.
