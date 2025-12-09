# RogueCloud Organization Configurations

This repository contains shared configurations for the RogueCloud organization.

## Approval Policies

Centralized approval configurations for [Enterprise Approval Engine](https://github.com/RogueCloud/issueops-approvals).

### Files

| File | Description |
|------|-------------|
| `approvals.yml` | Default approval config for all repos |
| `{repo-name}_approvals.yml` | Repo-specific config (takes precedence) |

### How It Works

When a repo uses the Enterprise Approval Engine with `config_repo: RogueCloud/.github`:

1. First looks for `{repo-name}_approvals.yml` (e.g., `myapp_approvals.yml`)
2. Falls back to `approvals.yml` (organization default)
3. Falls back to local `.github/approvals.yml` in the repo

### Usage

In your workflow:

```yaml
- uses: RogueCloud/issueops-approvals@v1
  with:
    action: request
    workflow: production-deploy
    token: ${{ secrets.GITHUB_TOKEN }}
    config_repo: RogueCloud/.github
```

### Current Configs

- **approvals.yml** - Default for all RogueCloud repos
- **issueops-approvals_approvals.yml** - Specific config for the issueops-approvals repo
