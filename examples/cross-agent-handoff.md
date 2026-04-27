# Pressure Test: Cross-Agent Handoff

## Prompt

```text
Use shipping-engineering-work to hand this task from Codex to Claude Code:

Codex diagnosed a flaky integration test and made a small patch, but Claude Code will continue implementation tomorrow. Preserve enough context so the next agent does not restart from scratch.
```

## Expected Agent Behavior

The agent should produce a portable handoff, not a platform-specific transcript. It should include:

1. Current goal.
2. Repository and branch.
3. Files touched.
4. Evidence gathered.
5. Commands run and results.
6. Current hypothesis or confirmed root cause.
7. Open questions.
8. Next safe action.
9. Warnings about user changes or files not to overwrite.

## Failure Signs

- Dumping a long chat transcript instead of a concise handoff.
- Using only Codex-specific or Claude-specific tool names.
- Omitting commands and results.
- Omitting dirty worktree warnings.

## Good Handoff Shape

```text
Goal: stabilize integration test X without changing public API.
Repo/branch: acme/app, branch fix/flaky-x.
Touched: src/session.ts, test/session.test.ts.
Evidence: failure occurs when cleanup races with async reconnect.
Commands: npm test test/session.test.ts -- failed before patch, passed after patch.
Next: run full integration suite, then review diff for cleanup scope.
Warning: docs/TASK_HANDOFF.md has unrelated user edits; do not revert.
```
