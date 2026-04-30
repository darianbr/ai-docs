---
name: github-branch-safety
description: "Use when: creating branches, preparing commits, syncing with remote, and enforcing safe PR-first Git workflow with GitHub MCP"
---

# GitHub Branch Safety Skill

Use this skill to enforce safe branch and push practices before opening or updating pull requests.

## Safety policy

- Never commit directly to `main`.
- Never commit directly to long-running shared branches (for example `develop`, `release/*`, `staging`).
- Create a short-lived working branch per task.
- Keep your branch up to date with the base branch before pushing.
- Prefer small, focused commits and a PR-first workflow.

## Inputs to collect

- Repository owner
- Repository name
- Base branch name
- Proposed working branch name

## Workflow

1. Inspect remote branches and recent commits with branch and commit MCP tools.
2. Verify current branch is not `main` and not a protected long-running branch.
3. If currently on `main`, create and switch to a new working branch before making changes.
4. Check whether branch is behind base and sync by rebasing or merging base into working branch.
5. Verify only intended files changed and run local validation checks before push.
6. Push working branch and create or update a PR with `mcp_github_create_pull_request`.
7. Merge via PR only after checks and review; do not bypass directly to `main`.

## Guardrails

- Block direct push or commit plans targeting `main`.
- Block direct push or commit plans targeting long-running shared branches.
- If work starts on `main`, stop and branch before any commit.
- Require branch sync check before every push.
- Require a PR link for all non-trivial changes.
- Require explicit user approval before any direct-to-`main` exception.

## Output format

- Branch safety checks performed
- Sync status with base branch
- PR created or updated
- Any policy exceptions requested
