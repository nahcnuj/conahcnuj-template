# conahcnuj-template

Template repository for **agentical issue-driven development** powered by
[conahcnuj](https://github.com/marketplace/actions/conahcnuj).

Use this template ("Use this template" on GitHub) to bootstrap a new repository
whose issues and pull requests are driven end-to-end by the conahcnuj agent:
feature branch -> PR -> review feedback -> ready-to-merge PR, with auto-merge
after owner approval.

## Setup

1. Create a repository from this template:
   - GitHub web: open this repository and click **Use this template** -> **Create a new repository**.
   - GitHub CLI: `gh repo create <new-repo> --template nahcnuj/conahcnuj-template --public`
     (use `--private` instead of `--public` as needed).
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

The driver also resumes on a failed required check through the `workflow_run`
trigger, which watches a workflow named `CI`. If your CI workflow uses a
different name, rename it to `CI` or update the `workflows: [CI]` entry in
`.github/workflows/issue-driver.yml`.

## Workflows

- `.github/workflows/issue-driver.yml` — drives issues/PRs via the reusable
  `nahcnuj/conahcnuj` workflow. It also supports `workflow_dispatch` with a
  `number` input to manually continue a specific issue or pull request.
- `.github/workflows/auto-merge.yml` — enables auto-merge on owner approval.
