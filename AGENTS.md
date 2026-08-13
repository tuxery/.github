# AGENTS.md — Tuxery `.github`

This repository contains **organization-level GitHub configuration** only.

## Language

**All content must be in English** — templates, documentation, workflow names,
comments, issue titles. No exceptions.

## Scope

- community health files (`CODE_OF_CONDUCT.md`, `CONTRIBUTING.md`, `SECURITY.md`, `SUPPORT.md`)
- issue and pull request templates (`ISSUE_TEMPLATE/`, `PULL_REQUEST_TEMPLATE.md`)
- reusable workflows (`.github/workflows/`) — called by product repos
- workflow templates (`workflow-templates/`)
- GitHub organization profile (`profile/README.md`)

## Reusable workflows

| Workflow | Triggered by | Purpose |
| --- | --- | --- |
| `ci-web.yml` | `workflow_call` | typecheck, lint (oxlint), unit tests (vitest), build |
| `security-audit-web.yml` | `workflow_call` | `pnpm audit` |
| `sbom.yml` | `workflow_call` | generate a CycloneDX SBOM for a Node/pnpm project |
| `conventional-commits.yml` | `workflow_call` | validate commit messages via `helpers4/action/conventional-commits` |

Product repos call these with a thin caller workflow in their own `.github/workflows/`.

## Rules

- Prefer generic, reusable GitHub conventions over product-specific content.
- Do not implement Tuxery application features in this repository.
- Put org profile content in `profile/README.md`.
- Put reusable workflows in `.github/workflows/`.
- Keep issue templates actionable and short.

## Commit conventions

All repositories in this organization follow **Conventional Commits** with **gitmoji**.

### Format

```text
type(scope): <emoji> short description

[optional body]

[optional footer: Co-Authored-By, Fixes #...]
```

**Example:**

```text
feat(matcher): ✨ add Levenshtein-based name scoring

Implements the first pass of the dedup/matching engine described in init.md.

Co-Authored-By: Claude Sonnet 5 <noreply@anthropic.com>
```

### Types and their emoji

| Type | Emoji | When to use |
| --- | --- | --- |
| `feat` | ✨ | New feature or capability |
| `fix` | 🐛 | Bug fix |
| `docs` | 📝 | Documentation only |
| `chore` | 🔧 | Maintenance, config, tooling |
| `test` | ✅ | Adding or fixing tests |
| `refactor` | ♻️ | Code restructuring, no behaviour change |
| `perf` | ⚡️ | Performance improvement |
| `style` | 🎨 | Formatting, whitespace (no logic change) |
| `ci` | 👷 | CI/CD workflows |
| `security` | 🔒 | Security fix or hardening |
| `build` | 📦 | Build system, dependencies |
| `revert` | ⏪ | Reverts a previous commit |
| `wip` | 🚧 | Work in progress (never merge to main) |

### Scopes

Scopes are **per-repository** and defined in each repo's own `scopes.json` (read automatically
by the `conventional-commits` reusable workflow) and mirrored in `.vscode/settings.json`.

**Agents must use only the scopes listed in the calling repo's `scopes.json`.**
Do not invent a new scope unless a new module or top-level concern is introduced —
in that case, update `scopes.json` and `.vscode/settings.json` first.

| Repository | Allowed scopes |
| --- | --- |
| `.github` | `governance` `community` `templates` `workflows` `conventional-commits` `security` `support` |
| `.dev` | `workspace` `devcontainer` `ai` `docs` `ci` |
| `app` | `web` `matcher` `sources` `ui` `ci` `deps` |

### PR check

Every PR title/commits are automatically validated by the reusable workflow
`.github/workflows/conventional-commits.yml` (called from each product repo).
PRs with a non-compliant title are blocked from merging.

### VSCode extension

Install `vivaxy.vscode-conventional-commits`. Each repo ships a `.vscode/settings.json`
with `"conventionalCommits.gitmoji": true` and the repo's scope list — the extension
will prompt for type, scope, and emoji automatically.

## Related repositories

- `.dev` — central development workspace for the organization
- `app` — the Tuxery product (Qwik web app, matching engine, source connectors)

## License

All Tuxery repositories are licensed **AGPL-3.0-or-later** unless stated otherwise.
