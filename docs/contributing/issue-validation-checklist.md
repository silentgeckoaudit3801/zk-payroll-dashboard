# Issue validation checklist

Use this checklist before opening a pull request for dashboard, SDK, or contract-facing issues. The goal is to give reviewers enough evidence to confirm scope, reproduce the change, and trust that the PR is ready for CI.

## Before you start

- Confirm the issue is still open and not already assigned to another contributor.
- Search open pull requests for the same issue number or branch topic.
- Pull the latest `main` and confirm your branch has no merge conflicts before requesting review.
- Keep the change scoped to the repository and files named in the issue unless a maintainer asks for broader work.
- Note any command you cannot run locally and explain why in the PR description.

## Dashboard UI issues

Validate dashboard changes with evidence reviewers can inspect quickly:

- Identify the affected route, component, or user journey.
- Run the relevant unit, smoke, or visual regression test when local tooling is available.
- Include screenshots or short clips for visible UI changes, including mobile or narrow viewport states when layout changes.
- Check loading, empty, error, and permission-denied states for the changed flow.
- Confirm keyboard focus order, labels, contrast, and screen-reader text for new controls.
- Verify no secret, salary amount, proof input, or private wallet data appears in logs, screenshots, or test fixtures.

## SDK utility issues

Validate SDK-related changes before linking them from dashboard code:

- Confirm the public API name, type, and error shape match the SDK documentation or issue acceptance criteria.
- Add representative tests for success, invalid input, retryable failure, and terminal failure paths where applicable.
- Keep examples free of real keys, salaries, proof inputs, and production contract addresses.
- Document backwards-compatible aliases when a public name cannot be changed immediately.
- Note whether dashboard consumers need a follow-up dependency bump or only documentation changes.

## Contract test or docs issues

When a dashboard issue depends on contract behavior or contract documentation:

- Reference the exact contract module, event, error text, or typed error used by the dashboard.
- Distinguish authorization failures from state-transition failures and malformed input.
- Mark retryable and non-retryable failures so UI copy does not encourage unsafe repeated submissions.
- Avoid changing contract behavior from a dashboard PR unless the issue explicitly asks for cross-repo work.
- Link the relevant contract docs, SDK error docs, or compatibility notes in the PR description.

## PR readiness checklist

Before opening a PR, confirm:

- [ ] The branch is up to date with `main` and has no merge conflicts.
- [ ] CI-relevant commands are listed, including skipped commands and reasons.
- [ ] Screenshots or clips are attached for visible UI changes.
- [ ] Tests cover the acceptance criteria or the PR explains why static/docs validation is sufficient.
- [ ] The PR links the issue and summarizes what changed by file area.
- [ ] No secrets, salaries, proof inputs, private keys, or production credentials appear in code, fixtures, logs, or screenshots.

## Review notes template

Copy this into the PR description when useful:

```markdown
Validation:
- Scope checked against issue: <issue number/title>
- Commands run: <commands or "not run: reason">
- UI evidence: <screenshots/clips or "not applicable">
- Conflict check: branch is <ahead/behind status> against main
- Privacy check: no secrets, salary values, proof inputs, or private keys added
```