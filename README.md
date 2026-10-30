# agents_skills - Personal Skills Collection

Centralized skills for OpenCode (also compatible with `.claude/skills`, `.agents/skills`).

## Layout

```text
./skills/<skill-id>/SKILL.md
./skills/<skill-id>/references/
./skills/<skill-id>/scripts/
```

Prefer subfolders (supporting files, private base dir).
Flat `./skills/<skill-id>.md` only for trivial single-file skills.

ID = folder name (or flat file name), case-sensitive. Use `lowercase-kebab-case`.
Frontmatter `name` is display-only. `description` is required for auto-discovery.

## Use from another repo

Clone once per PC:

```powershell
git clone https://github.com/eymdvz/agents_skills.git ~/shared/agents_skills
```

**Option A — global (all projects, recommended):**
`~/.config/opencode/opencode.jsonc`
(`%USERPROFILE%\.config\opencode\opencode.jsonc` on Windows):

```jsonc
{
  "$schema": "https://opencode.ai/config.json",
  "skills": ["~/shared/agents_skills/skills"]
}
```

On this PC: `"skills": ["D:/Document/GitHub/eymdvz/agents_skills/skills"]`.
Point at the `skills/` subfolder, not the repo root.

**Option B — per-project (one repo only):**
`<project>/opencode.jsonc` or `<project>/.opencode/opencode.jsonc`:

```jsonc
{
  "$schema": "https://opencode.ai/config.json",
  "skills": ["D:/Document/GitHub/eymdvz/agents_skills/skills"]
}
```

Project entries stack on top of global. Same ID in
`<project>/.opencode/skills/` wins over central (use this for per-repo overrides).

Then in OpenCode:

1. `/reload` once
2. Agent auto-discovers by `description`, or force with `@<skill-id>` (e.g. `@session-handoff`)
3. Agent loads the full `SKILL.md` on demand via the `skill` tool

Update everywhere with `git pull` in the `agents_skills` clone.

## Do you need to point JSON at AGENTS.md?

No. `skills` takes only skill source dirs (folders with `SKILL.md` /
`*.md`) or HTTP catalog URLs. Pointing it at `AGENTS.md` does nothing.

`AGENTS.md` (this repo root) is AI-facing conventions, loaded when the
agent works inside this repo. To also load it in every other project,
add it separately as an instruction/reference in global `opencode.jsonc`:

```jsonc
{
  "instructions": ["D:/Document/GitHub/eymdvz/agents_skills/AGENTS.md"]
}
```

## Troubleshooting

* Skill missing: wrong path level (must be `skills/`), missing `description`,
  duplicate ID shadowed by a later source, forgot `/reload`.
* Wrong content loaded: check path-derived ID vs frontmatter `name`,
  plus `opencode/autoinvoke` and agent `skill` permissions.
