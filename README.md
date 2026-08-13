# Tuxery — `.github`

Shared GitHub defaults for the **Tuxery** organization.

This special repository centralizes the GitHub-facing bootstrap for the organization:

- the public organization profile in [`profile/README.md`](./profile/README.md)
- community health files inherited by future repositories
- issue and pull request templates
- reusable workflows and workflow templates as the organization grows

## What this repository is for

Use this repository for anything that should be shared across the organization on GitHub:

- contribution and support guidance
- security reporting policy
- issue / PR defaults
- reusable Actions workflows
- workflow templates surfaced in the GitHub UI

Do **not** use it for product implementation, runtime code, or repository-specific application logic.

## Layout

```text
.github/
├── .github/workflows/      # reusable workflows for product repos
├── ISSUE_TEMPLATE/         # org-wide issue templates
├── workflow-templates/     # starter workflow files shown by GitHub
├── profile/README.md       # GitHub organization profile
├── AGENTS.md               # repo-specific AI guidance
├── LICENSE                 # AGPL-3.0-or-later
├── CODE_OF_CONDUCT.md
├── CONTRIBUTING.md
├── PULL_REQUEST_TEMPLATE.md
├── SECURITY.md
└── SUPPORT.md
```

## Bootstrap status

The organization is intentionally starting with a small set of foundational repositories:

| Repository | Purpose |
| --- | --- |
| [`.github`](https://github.com/tuxery/.github) | Shared GitHub defaults and organization profile |
| [`.dev`](https://github.com/tuxery/.dev) | Shared workspace, devcontainer, and AI guidance |
| [`app`](https://github.com/tuxery/app) | The product monorepo (web UI, matching engine, source connectors) |

Future repositories (e.g. `site`, `spec`) will opt into the shared defaults from here as they
are created. Work that isn't done yet lives on the
[Tuxery GitHub Project](https://github.com/orgs/tuxery/projects/1), not in local TODO/ROADMAP
files.
