# ai-docs

Shared AI configuration docs and settings for multi-repo VS Code workspaces.

## Design goal

Drop-in behavior with no install step and no sync step.

If `ai-docs` is included as a folder in your workspace, the shared instructions, prompts, skills, and MCP config are available automatically.

## Minimum workspace

- current-project
- ai-docs

## Automatic behavior

- `.github/` content in `ai-docs` is discovered by Copilot Chat in the workspace.
- `.vscode/mcp.json` in `ai-docs` provides the GitHub MCP server configuration for that workspace.
- No user-level symlink, no install script, and no sync hook are required.

## Shared assets

### Prompts
- .github/prompts/create-pr.prompt.md

### Workspace Instructions
- .github/copilot-instructions.md

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

### Validation Workflow
- .github/workflows/validate-config.yml
