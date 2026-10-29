# conahcnuj-template

Template repository for **agentical issue-driven development** powered by
[conahcnuj](https://github.com/marketplace/actions/conahcnuj).

Use this template ("Use this template" on GitHub) to bootstrap a new repository
whose issues and pull requests are driven end-to-end by the conahcnuj agent:
feature branch -> PR -> review feedback -> ready-to-merge PR, with auto-merge
after owner approval.

## Setup

1. Create a repository from this template.
2. In the new repository, add the GitHub App secrets (Settings -> Secrets and variables -> Actions):
   - `APP_ID`
   - `INSTALLATION_ID`
   - `PRIVATE_KEY` (the App's private key PEM)
3. Create an environment named `conahcnuj` (Settings -> Environments) and put the
   above secrets there (or rely on repository secrets).
4. Enable **Allow auto-merge** (Settings -> General -> Pull Requests).

Once configured, opening an issue triggers `.github/workflows/issue-driver.yml`,
which calls the reusable conahcnuj driver. Owner approval triggers
`.github/workflows/auto-merge.yml`.

## Workflows

- `.github/workflows/issue-driver.yml` — drives issues/PRs via the reusable
  `nahcnuj/conahcnuj` workflow.
- `.github/workflows/auto-merge.yml` — enables auto-merge on owner approval.
