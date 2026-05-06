# AI Agent Coordination

This repository is maintained with help from three AI agents:

- **Claude Code** (Anthropic) — scheduled weekly reviews, CI/CD, infra
- **Codex** (OpenAI) — interactive feature work invoked by the maintainer
- **Copilot** (GitHub) — interactive feature work invoked by the maintainer

## Branch Naming

| Agent | Prefix | Example |
|---|---|---|
| Claude | `claude/` | `claude/fix-send-mail` |
| Codex | `codex/` | `codex/add-html-support` |
| Copilot | `copilot/` | `copilot/add-html-support` |

All three prefixes auto-merge via the `auto-merge.yml` workflow once CI passes.

## Ownership Map

| Area | Primary owner | Notes |
|---|---|---|
| `.github/workflows/` | Claude | All workflow files |
| `AGENTS.md` | Claude | This file |
| `README.md` | Shared | Either may update |

## Conflict Protocol

Before opening a PR:

1. Run `gh pr list --repo API-Apoteket/routines-relay --state open` and check for open PRs touching the same files.
2. If another agent has an open PR on a file you need to modify, wait for it to merge and rebase.
3. Never force-push to a branch you did not create.
4. Never close or edit another agent's PR.

## Standards

- Shell: POSIX-compatible, `set -euo pipefail` in scripts
- All email addresses and secrets via env vars or msmtp config — never hardcoded
- Direct commits to `main` are not allowed — always use a branch + PR
