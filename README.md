# Flâneur — `.dev`

Dev workspace orchestrator for the [Flâneur](https://github.com/flaneur-app) organization:
a fast, open, multi-service video client. Your subscriptions and history, kept in sync.

## What's in here

| File / folder | Purpose |
| --- | --- |
| `.devcontainer/` | Devcontainer (`org-workspace` clones the org repos) |
| `.claude/commands/commit.md` | `/commit` slash command |
| `.vscode/settings.json` | Shared editor settings |
| `flaneur-app.code-workspace` | Multi-root VS Code workspace |
| `AGENTS.md` | Canonical AI / agent rules for all flaneur-app repos |

## Quick start — GitHub Codespaces (recommended)

Open a Codespace on `flaneur-app/.dev` directly from GitHub. The `org-workspace` feature clones the
org's repos (see `.devcontainer/devcontainer.json`) into `/workspaces/<repo>` automatically.

Secrets (`GH_TOKEN`, …) come from OpenBao — `kv/orgs/flaneur-app`, plus `kv/shared/*` — through the
[`openbao-env`](https://github.com/helpers4/devcontainer/tree/main/src/openbao-env) feature, into
every process of the container (VS Code included). On fajro, `lar up flaneur-app` hands the
container its credentials. In GitHub Codespaces, set the Codespaces secrets `BAO_ROLE_ID` and
`BAO_SECRET_ID` (AppRole `flaneur-app`) and give the codespace Tailscale access: OpenBao is only
reachable on the tailnet.

## Quick start — local (Docker Desktop / WSL2)

```bash
mkdir flaneur-app && cd flaneur-app
gh repo clone flaneur-app/.dev
code .dev/flaneur-app.code-workspace
```

Reopen `.dev` in the devcontainer — sibling repos are cloned automatically by
the `org-workspace` feature. The secrets come from OpenBao (see above).

## Verifying the environment

```bash
bash .devcontainer/test-container.sh
```

When a new repository is added to the organization, nothing needs to change here: the
`org-workspace` feature discovers the org's repos and updates `flaneur-app.code-workspace` for you.

## License

[AGPL-3.0-or-later](LICENSE).
