---
name: github-release-readiness
description: "Use when: preparing a release by checking tags, release notes, open blockers, and release PR status through GitHub MCP"
---

# GitHub Release Readiness Skill

Use this skill to create a release readiness snapshot before cutting a release.

## Inputs to collect

- Repository owner
- Repository name
- Target version or tag
- Release branch (if applicable)

## Workflow

1. Check existing releases and tags via GitHub release and tag tools.
2. Search for open blocker issues using `mcp_github_search_issues`.
3. Search release-related PRs with `mcp_github_search_pull_requests`.
4. Verify changelog or release note updates in changed files.
5. If release does not exist yet, draft one with `mcp_github_issue_write` or PR automation flow.

## Guardrails

- Do not merge release PRs without explicit instruction.
- Flag missing migration notes and breaking-change notes.
- Include links to blocker issues in final report.
- Ensure release work is done on a dedicated branch, not directly on `main`.
- Ensure the release branch is synced with base before any release push or merge action.

## Output format

- Release status: ready or not ready
- Blocking issues and PRs
- Missing artifacts (notes, tags, approvals)
- Recommended next actions
