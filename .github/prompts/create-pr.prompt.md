---
name: create-pr
description: "Create a pull request following safety best practices, including branch safety, local validation, code quality checks, and clear PR metadata."
---

# Create Pull Request

Follow this prompt to create a high-quality, safe pull request that passes all safety gates and minimizes reviewer burden.

## MCP-first rule

For GitHub operations in this workflow, use GitHub MCP tools first and foremost.
Use terminal git commands only as a fallback when MCP cannot perform a required step.

## Prerequisites

Before starting, ensure:

- [ ] You are on a feature branch (not `main`, `develop`, `release/*`, or `staging`)
- [ ] Your branch name follows `task/<ticket>-<slug>` or `fix/<description>` pattern
- [ ] Your branch is up to date with the base branch (rebased or merged)

## 1. Run Local Validation

Confirm all local checks pass:

```bash
# Run tests
npm test  # or your test command

# Run linting and type checks
npm run lint && npm run type-check

# Check for secrets and large binaries
git diff --cached --name-only | grep -E '\.(env|local|secret|pem|key)$' && echo "⚠️  Secrets detected!" || echo "✓ No secrets"
```

If any check fails, fix it locally before proceeding.

## 2. Review Your Commit(s)

Ensure commits are clean and descriptive:

```bash
git log --oneline origin/main..HEAD
```

Each commit should:
- [ ] Have a clear, descriptive message (not "fix", "update", "changes")
- [ ] Follow Conventional Commits format: `type(scope): message` (e.g., `feat(auth): add MFA support`)
- [ ] Change only one logical concern (no mixing refactor + feature)

If commits are messy, squash or rebase them:

```bash
git rebase -i origin/main
```

## 3. Review File Changes

Ensure your change scope is focused:

```bash
git diff --stat origin/main..HEAD
```

Check:
- [ ] Only intended files changed
- [ ] No accidental changes to unrelated code
- [ ] Change size is reasonable (typically < 500 lines; if larger, justify it)

## 4. Craft Your PR Title and Description

Use this template for your PR title:

```
[TYPE] Short description of what this PR does

Types: feat, fix, docs, refactor, chore, security, perf, test
Examples:
  - feat: add support for user roles
  - fix: resolve race condition in cache invalidation
  - docs: update API documentation for v2
```

Draft your PR description following this template:

```markdown
## Description

Brief explanation of what this PR changes and why.

## Related Issue

Closes #123  (or see #123 for more context)

## Type of Change

- [ ] Bug fix (non-breaking change that fixes an issue)
- [ ] New feature (non-breaking change that adds functionality)
- [ ] Breaking change (fix or feature that would cause existing functionality to change)
- [ ] Documentation update

## Breaking Changes?

If yes, list them clearly and explain the migration path.

## Testing

Describe how you tested this change:
- Manual testing: ...
- Test coverage: ...
- Unit tests added: ...

## Checklist

- [ ] Code follows style guidelines
- [ ] Tests pass locally
- [ ] No new warnings generated
- [ ] Documentation updated if needed
- [ ] No hardcoded secrets or sensitive data
- [ ] Change scope is focused on a single concern
```

## 5. Verify Coverage and Quality

Before opening the PR:

```bash
# Check test coverage (if applicable)
npm run coverage

# Verify no secrets are committed
git log -p origin/main..HEAD | grep -E 'password|secret|api.?key|token' && echo "⚠️  Secrets in history!" || echo "✓ Clean"
```

Confirm:
- [ ] Test coverage does not decrease
- [ ] No secrets in commit history
- [ ] No deprecated API usage introduced

## 6. Create or Update the PR (MCP-first)

Preferred flow:

- Push your working branch.
- Create PR with `mcp_github_create_pull_request`.
- Update PR metadata with `mcp_github_update_pull_request`.
- Request Copilot review with `mcp_github_request_copilot_review`.

If MCP is unavailable, fallback to terminal/CLI flow for branch push and PR creation.

If branch history was rebased, use safe push behavior (`--force-with-lease`, never `--force`) and coordinate with reviewers.

## Final Checklist

Before requesting review:

- [ ] Branch is not `main` or a long-running shared branch
- [ ] Branch is up to date with base branch
- [ ] All local tests pass
- [ ] Linting and type checks pass
- [ ] Commit messages are descriptive and follow conventions
- [ ] PR title follows `[TYPE] description` format
- [ ] PR description is clear and includes linked issue(s)
- [ ] Change scope is focused and justified
- [ ] No secrets or sensitive data committed
- [ ] Test coverage did not decrease
- [ ] No deprecated APIs introduced
- [ ] CI pipeline is green (if available)
- [ ] Conversations and feedback are addressed

Once all items are checked, your PR is ready for review. Request reviewers and watch for feedback.
