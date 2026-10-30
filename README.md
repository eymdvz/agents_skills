# agents_skills - Personal Skills Collection

Centralized skills for OpenCode (also compatible with `.claude/skills`, `.agents/skills`).

## Layout

```text
./skills/<skill-id>/SKILL.md
./skills/<skill-id>/references/
./skills/<skill-id>/scripts/
```

Or flat file: `./<skill-id>.md`

ID = path-derived, case-sensitive. Use `lowercase-kebab-case`.

## Use

Clone once per PC:

```powershell
git clone https://github.com/eymdvz/agents_skills.git ~/shared/agents_skills
```

Global `~/.config/opencode/opencode.jsonc` (`%USERPROFILE%\.config\opencode\opencode.jsonc` on Windows):

```jsonc
{
  "$schema": "https://opencode.ai/config.json",
  "skills": ["~/shared/agents_skills/skills"]
}
```

Point at the `skills/` subfolder, not the repo root.
On this PC: `"skills": ["D:/Document/GitHub/eymdvz/agents_skills/skills"]`

Then `/reload` in OpenCode. Update with `git pull`.
