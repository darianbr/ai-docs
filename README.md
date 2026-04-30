# ai-docs

Shared AI configuration docs and settings that can be versioned and synced through GitHub.

This repository is intended to be used in a multi-repo VS Code workspace.

Minimum workspace folders:

- current-project
- ai-docs

## VS Code global config source

This repo stores the source of truth for VS Code user-level AI configuration.

- Source file: `global/vscode-user/mcp.json`
- Linked target: `~/.config/Code/User/mcp.json`

## Apply local link

Run:

```bash
ln -sfn "$HOME/projects/github.com/darianbr/ai-docs/global/vscode-user/mcp.json" "$HOME/.config/Code/User/mcp.json"
```

After updating files in this repo, commit and push to sync across machines.

## Shared skills

This repo includes reusable Copilot skills for GitHub workflows and safety practices.

### Prompts
- .github/prompts/create-pr.prompt.md — Create a PR following all safety and quality best practices

### GitHub Workflow Skills (MCP-enabled)
- .github/skills/github-issue-triage/SKILL.md
- .github/skills/github-pr-review-ops/SKILL.md
- .github/skills/github-release-readiness/SKILL.md

### Safety & Quality Skills
- .github/skills/github-branch-safety/SKILL.md
- .github/skills/local-pre-push-validation/SKILL.md
- .github/skills/pr-readiness-verification/SKILL.md
- .github/skills/code-quality-and-security-gates/SKILL.md
- .github/skills/merge-conflict-and-rebase-safety/SKILL.md

Use these as shared workflow docs in your multi-repo workspace setup.

#### Safety coverage

- **Branch safety**: No commits to `main` or long-running branches; PR-first workflow; branch sync enforcement.
- **Pre-push validation**: Local tests, linting, type checks; commit message quality; secret detection.
- **PR readiness**: CI passing; focused scope; clear description; resolved conversations.
- **Code quality & security**: Secret scanning; vulnerability checks; test coverage; breaking changes.
- **Merge safety**: Conflict resolution; safe rebase; force-push coordination; clean history.
- **Release readiness**: Tag checks; blocker inventory; changelog updates.
- **Issue triage**: Consistent labeling, assignment, delegation; safe code changes from tasks.
