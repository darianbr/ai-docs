---
name: code-quality-and-security-gates
description: "Use when: scanning code for security risks, dependency vulnerabilities, test coverage drops, and quality regressions before merge"
---

# Code Quality and Security Gates Skill

Use this skill to enforce quality and security standards on code changes, preventing low-confidence or risky code from reaching production.

## Safety policy

- No code with known security vulnerabilities or secrets should merge.
- Test coverage must not decrease; prefer coverage stability or growth.
- No critical or high-severity code scanning violations should merge without explicit exception.
- Dependency updates must not introduce new vulnerabilities (check Dependabot, supply chain).
- Breaking changes must be clearly documented and approved.

## Inputs to collect

- Repository owner and name
- Pull request number or branch name
- Acceptance criteria for coverage, security, and quality

## Workflow

1. Check for secrets and sensitive credentials via GitHub secret scanning.
2. Review Dependabot alerts and security scanning results from PR checks.
3. Compare test coverage before/after; warn if coverage drops below threshold.
4. Identify breaking changes in public APIs or config schemas.
5. Flag any deprecated dependency usage or unmaintained packages.
6. Summarize security and quality findings with severity levels.
7. Require explicit approval for any override of quality/security gates.

## Guardrails

- Block merge if secrets are detected.
- Block merge if critical/high security vulnerabilities are found.
- Block merge if test coverage drops below configured threshold (e.g., 80%).
- Require manual approval for breaking changes.
- Warn if PR introduces new deprecated APIs or unmaintained dependencies.
- Document all exceptions and their justification.

## Output format

- Security scanning results and any vulnerabilities
- Test coverage delta (before/after)
- Dependency changes and supply chain risks
- Breaking changes summary
- Quality gates: Pass / Conditional / Fail
- Exception log with justification
