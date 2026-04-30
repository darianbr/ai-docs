---
name: pr-readiness-verification
description: "Use when: before requesting review or merging a PR, verify CI passes, PR scope is focused, description is complete, and no unresolved comments exist"
---

# PR Readiness Verification Skill

Use this skill to confirm a pull request is ready for review or merge, preventing common issues that waste reviewer time or introduce regressions.

## Safety policy

- CI/CD pipeline must pass before requesting review.
- PR description must clearly articulate the change, why, and any side effects.
- PR scope must be narrow and focused on a single concern; flag scope creep.
- All conversations and requested changes must be resolved.
- No WIP, draft, or "hold" markers in title; PR must be actively ready.

## Inputs to collect

- Repository owner and name
- Pull request number
- Review checklist or form

## Workflow

1. Check PR CI status via GitHub Actions/workflows; if failed, list failures.
2. Verify PR title and description are clear and include linked issue(s).
3. Count lines changed and files modified; flag if unusually large (e.g., > 500 lines, > 20 files).
4. List open conversations, pending comments, or requested changes.
5. Verify no WIP/draft/hold markers in title or labels.
6. Confirm author has not force-pushed without coordinating with reviewers.
7. Generate a pre-review summary and confirm readiness.

## Guardrails

- Block review request if CI is still running or has failed.
- Require linked issue or explicit scope statement in PR body.
- Warn if PR changes span multiple unrelated domains.
- Flag unresolved conversations or requested changes.
- Require confirmation that no force pushes occurred without notice.

## Output format

- CI status and any failure details
- PR scope and linked issues
- Conversation summary (resolved vs. unresolved)
- Readiness checklist results
- Recommendation: Ready for review / Needs revision
