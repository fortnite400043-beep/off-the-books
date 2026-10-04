---
inclusion: always
---

# Session Workflow

This project spans many separate conversations, in both **Kiro Web** (browser) and the **Kiro desktop app**. No session remembers previous ones. The repo is the only memory, so keep it current.

## At the start of every session

1. Work out which environment you're in (see the table below).
2. Read the **latest entry** in `docs/SESSION_LOG.md`, then `docs/DECISIONS.md` and `docs/OPEN_QUESTIONS.md`.
3. Read only the docs and system specs relevant to the task. Don't load everything.
4. Briefly tell the user where things stand and what you plan to do. Then work.

## Environments

| | Kiro Web (browser) | Kiro desktop app |
|---|---|---|
| OS | Linux sandbox | User's Windows PC |
| Repo location | `/projects/sandbox/off-the-books` (clone over HTTPS if missing) | User's local clone |
| Roblox Studio | **Not available.** You can't playtest or see the game. | Available, but run by the user |
| What you can run | git, Lune tests, StyLua, Selene, Blender (if installed), scripts | The same, plus anything on the user's machine |
| User visibility | User can't see the filesystem. Push branches or open PRs, and paste key output into chat. | User can open files directly |
| GitHub | Use `git push`. Open PRs with `gh api repos/{owner}/{repo}/pulls` (not `gh pr create`). | Normal git and gh |

- **Never run long-running processes** such as `rojo serve` or watchers. Ask the user to run them.
- Use PowerShell-compatible commands on Windows.
- When you need visual feedback (Studio playtests, Blender renders, UI layouts), ask the user for screenshots. In Web, you can render Blender previews headlessly if Blender is available.

## Git

- Never commit directly to `main`. Use feature branches and open PRs into `main`.
- Branch names: `docs/<topic>`, `feat/<system>`, `fix/<issue>`, `chore/<task>`, `assets/<asset>`.
- Commit messages use the Conventional Commits format, for example `feat(raids): add planning phase state machine` or `docs(gdd): spec employee traits`.
- Always give the user the PR or branch link at the end of a session.

## Rules for asking and deciding

- **Make no broad assumptions.** The user wants to be asked. If a spec has a gap, stop and ask before writing or coding around it.
- Batch your questions. Number them, and give each one a recommended default so the user can reply "default."
- Never contradict `docs/DECISIONS.md` silently. If the user changes a decision, update the entry, mark the old version as superseded, and add the date.
- Record new decisions in `DECISIONS.md` and unresolved items in `OPEN_QUESTIONS.md` as they happen, not just at the end.
- Push back honestly when a request conflicts with the design guardrails, Roblox policy, or technical reality. Explain the problem and propose an alternative.

## At the end of every session

Before you finish, append an entry to `docs/SESSION_LOG.md` in this format:

```
## YYYY-MM-DD: <short title>
- **Environment:** Web | Desktop
- **Done:** ...
- **Decisions added or changed:** ... (also update DECISIONS.md)
- **New open questions:** ... (also update OPEN_QUESTIONS.md)
- **Next steps:** ...
- **Branch/PR:** ...
```

Then commit and push.
