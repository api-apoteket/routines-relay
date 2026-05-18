![Downloads](https://img.shields.io/github/downloads/blixten85/routines-relay/total)

# routines-relay

A GitHub Actions-based mail relay. Sends emails via `msmtp` on a self-hosted runner — no application server required.

## How it works

The relay is a single `workflow_dispatch` GitHub Action. Other workflows (or scripts) trigger it via the GitHub API with a subject and body, and the action sends the email through `msmtp` on the self-hosted runner.

## Usage

### Via GitHub CLI

```bash
gh workflow run send-mail.yml \
  --repo blixten85/routines-relay \
  --field subject="Daily check OK" \
  --field body="All systems nominal."
```

### Via GitHub API

```bash
curl -X POST \
  -H "Authorization: Bearer $GITHUB_TOKEN" \
  -H "Accept: application/vnd.github+json" \
  https://api.github.com/repos/blixten85/routines-relay/actions/workflows/send-mail.yml/dispatches \
  -d '{"ref":"main","inputs":{"subject":"Daily check OK","body":"All systems nominal."}}'
```

## Requirements

- A self-hosted GitHub Actions runner on the target host
- `msmtp` installed and configured on that host
- A GitHub token with `actions: write` scope

## License

MIT
