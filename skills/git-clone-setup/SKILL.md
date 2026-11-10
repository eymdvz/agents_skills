---
name: git-clone-setup
description: Setup after git clone on Windows fresh or existing PC. Check Git/GCM install, GitHub login, auto-fix repo-local user.name/email. Use when user says just cloned, fresh pc, setup git, register repo.
---

# Git clone setup (Windows)

Auto-fix missing identity, ask before overwriting existing. Docs only + `git config --local` — never stage, commit, push, or change global `user.*`.

## 1 — Fresh-PC check (read-only)

Run: `git --version`, `git-credential-manager --version`.
If missing: install per `references/github-login.md`, then once per device:
`git-credential-manager configure` + `git config --global credential.helper manager`.
PowerShell note: GCM lives in `C:\Program Files\Git\mingw64\bin` — use full path, Git Bash, or `$env:Path += ";C:\Program Files\Git\mingw64\bin"`.

## 2 — Login

`git-credential-manager github login --browser` → approve in the browser profile for the wanted account → `git-credential-manager github list` to verify.
Picker = push/pull identity only, not commit author.

## 3 — Repo-local auto-fix

Run: `git rev-parse --show-toplevel`, `git config --local user.name`, `git config --local user.email`, `git remote -v`.
If missing: set `git config --local user.name "Name"` / `git config --local user.email "mail"`.
If exists but mismatched: ask before overwrite. Affects future commits only.

## 4 — Verify and stop

`git status -sb`. No push. On stale-cred push failure: `github logout <account>` + push retries login. Full doc: read `references/github-login.md`.
