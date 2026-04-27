# Workflow Modes

## Frame Mode

Use for ambiguous or broad requests.

Steps:

1. Restate the problem in concrete terms.
2. Identify user, success, constraints, and non-goals.
3. Offer 2-3 approaches if the path is not obvious.
4. Recommend the narrowest useful wedge.
5. Ask for approval if implementation would be risky or large.

Output:

- Problem statement
- Options and tradeoffs
- Recommended next slice

## Inspect Mode

Use before editing unfamiliar code.

Steps:

1. Check git status.
2. Search for relevant files and tests.
3. Read nearest implementation and tests.
4. Identify existing patterns.
5. State likely change surface.

Output:

- Evidence summary
- Files likely to change
- Verification candidate

## Design Mode

Use for new behavior, architecture, UI, or workflow changes.

Steps:

1. Define behavior and acceptance criteria.
2. Split into components with clear ownership.
3. Define data flow and failure handling.
4. Define verification.
5. Keep scope small enough to implement and review.

Output:

- Small spec or design note
- Risks and non-goals

## Implement Mode

Use when scope and verification are clear.

Steps:

1. Create or identify a focused test when feasible.
2. Make the smallest patch.
3. Run formatting or focused checks.
4. Review diff.
5. Run final verification.

Output:

- Patch
- Verification evidence

## Debug Mode

Use for failing tests, errors, logs, flaky behavior, regressions, or broken workflows.

Steps:

1. Capture exact symptom.
2. Reproduce or inspect evidence.
3. Form a hypothesis.
4. Test the hypothesis with the smallest probe.
5. Fix root cause.
6. Add regression coverage when feasible.
7. Verify the original symptom is gone.

Output:

- Root cause
- Fix
- Regression check

## Review Mode

Use for code review or pre-PR review.

Steps:

1. Read diff and surrounding code.
2. Prioritize correctness, regression risk, security, data loss, and tests.
3. Report findings first with file/line references when possible.
4. Keep summaries secondary.

Output:

- Ordered findings
- Test gaps
- Open questions

## Upstream Mode

Use when contributing to another project.

Steps:

1. Read maintainer docs and recent local style.
2. Keep the patch minimal and issue-linked.
3. Add tests/docs/changelog if expected.
4. Run project checks.
5. Write a PR body that makes review easy.
6. Respond to review with evidence, not defensiveness.

Output:

- Maintainer-friendly patch
- PR body or review response
