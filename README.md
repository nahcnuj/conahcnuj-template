# conahcnuj-template

Template repository for **agentical issue-driven development** powered by
[conahcnuj](https://github.com/marketplace/actions/conahcnuj).

Use this template ("Use this template" on GitHub) to bootstrap a new repository
whose issues and pull requests are driven end-to-end by the conahcnuj agent:
feature branch -> PR -> review feedback -> ready-to-merge PR, with auto-merge
after owner approval.

## Getting Started

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
5. Remove entirely the contents of this file, and rewrite with yours.


