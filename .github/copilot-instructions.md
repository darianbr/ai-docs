---
name: AI Docs Workspace Setup
description: "Guidance for using shared AI configuration in multi-repo workspaces"
applyTo: "**"
---

# AI Docs Workspace Instructions

This workspace uses shared Copilot configuration from the **ai-docs** repository, including MCP servers, skills, prompts, and safety practices.

## Branch Protection Policy

These rules are required for all code changes:

1. Never commit directly to `main`.
2. Never push directly to `main`.
3. Always create a short-lived branch for changes, then open a PR into `main`.
4. Before push, ensure the branch is up to date with `main`.
5. Treat direct-to-`main` only as an explicit user-approved exception.

## GitHub MCP First Policy

1. Use GitHub MCP tools first for GitHub operations.
2. Prefer MCP for issues, pull requests, reviews, releases, and merge actions.
3. Use terminal git commands only when MCP does not support the required operation.

## At Session Start

When you open a new session or switch workspaces:

1. Confirm `ai-docs` is included as a workspace folder.

2. **Verify MCP is loaded** by running `MCP: List Servers` in the Command Palette (Ctrl+Shift+P)

3. **Test GitHub MCP** by opening Chat and requesting GitHub help (e.g., "List my recent issues")

## Available Skills

Type `/` in Chat to see all available skills:

- `/github-issue-triage` — Triage issues consistently
- `/github-pr-review-ops` — Review pull requests safely
- `/github-release-readiness` — Check release blockers
- `/github-branch-safety` — Enforce branch protection
- `/local-pre-push-validation` — Validate before push
- `/pr-readiness-verification` — Verify PR is ready for review
- `/code-quality-and-security-gates` — Check for security/quality issues
- `/merge-conflict-and-rebase-safety` — Safely resolve conflicts
- `/create-pr` — Create a new pull request following best practices

## If Skills Don't Appear

1. Confirm `.github/` folder is in the workspace
2. Run `MCP: List Servers` to verify GitHub MCP is enabled
3. Reload VS Code (Ctrl+Shift+P → "Developer: Reload Window")
4. Check [README.md](README.md) in ai-docs for troubleshooting

## Customizing for Your Project

When you clone this workspace setup for a new project:

1. Add your current-project as a second folder in the workspace
2. Add ai-docs as another folder in the same workspace
3. All skills and prompts will be available across both folders
4. Create project-specific skills under `current-project/.github/skills/` as needed
