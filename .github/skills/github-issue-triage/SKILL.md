---
name: github-issue-triage
description: "Use when: triaging GitHub issues, labeling, assigning, or creating follow-up tasks with GitHub MCP tools"
---

# GitHub Issue Triage Skill

Use this skill to run a consistent issue triage workflow with GitHub MCP.

## Inputs to collect

- Repository owner
- Repository name
- Triage query or issue number
- Labels and assignees policy

## Workflow

1. Find target issues with `mcp_github_search_issues`.
2. Read details and current metadata before editing.
3. Apply labels, assignees, and status updates with `mcp_github_issue_write`.
4. If the issue needs implementation, delegate with `mcp_github_assign_copilot_to_issue`.
5. Post a clear issue comment summarizing triage actions with `mcp_github_issue_write`.

## Guardrails

- Do not close issues without explicit reason.
- Confirm labels exist before applying broad label changes.
- Keep triage comments short and action-oriented.
- Never commit or push directly to `main` while implementing issue follow-up work.
- Use short-lived branches and PRs for any code changes resulting from triage.

## Output format

- Issues reviewed
- Actions taken per issue
- Follow-up items delegated to Copilot
- Open questions or blockers
