# Using fullsend with this repository

This repository uses [fullsend](https://github.com/fullsend-ai/fullsend)
for AI-assisted development. Fullsend runs as a set of agent roles that
respond to GitHub events (issues, pull requests, comments) via the
`.github/workflows/fullsend.yaml` workflow.

## Configured roles

The `.fullsend/config.yaml` file enables six roles:

| Role | Trigger | What it does |
|------|---------|--------------|
| **triage** | Issue opened or labeled | Analyzes the issue, identifies root cause, and proposes a plan |
| **coder** | `/fs-code` comment on a triaged issue | Implements the fix or feature and opens a pull request |
| **review** | Pull request opened or updated | Reviews the PR for correctness, style, and completeness |
| **fix** | Review requests changes | Automatically addresses review feedback on agent PRs |
| **retro** | Pull request merged | Runs a retrospective to capture lessons learned |
| **prioritize** | On demand | Assesses and prioritizes open issues |

## How to interact

1. **Open an issue** describing a bug or feature request. The
   **triage** agent analyzes it and adds a `ready-to-code` label when
   the issue is actionable.
2. **Trigger the coder** by commenting `/fs-code` on a triaged issue.
   The **coder** agent creates a branch, implements the change, and
   opens a PR.
3. **Review happens automatically.** The **review** agent examines the
   PR and posts findings. If changes are requested, the **fix** agent
   attempts to resolve them.
4. **Merge the PR** once it passes review. The **retro** agent runs a
   retrospective after merge.

## Stopping the fix agent

If you want to prevent the fix agent from acting on a PR, comment
`/fs-fix-stop`. This adds the `fullsend-no-fix` label and disables
automatic fixes for that PR. Remove the label or comment `/fs-fix`
to re-engage.

## Configuration

The fullsend configuration lives in `.fullsend/config.yaml`. See the
[fullsend documentation](https://github.com/fullsend-ai/fullsend) for
available options.
