# Contribution Readiness

Use this before opening an upstream PR or replying to maintainer feedback.

## Maintainer Checklist

- The patch solves a clear problem or linked issue.
- Scope is narrow and avoids unrelated refactors.
- Behavior change is covered by tests or documented verification.
- Docs, examples, changelog, or migration notes are included when expected.
- Existing style, naming, formatting, and architecture are preserved.
- Platform-specific behavior is guarded and tested where possible.
- Backward compatibility is considered.
- Failure modes are described if relevant.

## PR Body Template

```markdown
## Summary

- ...
- ...

## Why

This addresses ...

## Verification

- ...

## Notes

- ...
```

## Review Response Pattern

1. Acknowledge the concrete point.
2. Verify the claim against code, tests, or docs.
3. Implement the requested change when correct.
4. Explain respectfully when proposing an alternative.
5. Push a focused follow-up commit.
6. Comment with what changed and what was verified.

## Common Maintainer Hygiene

- Add one-line changelog attribution if the project asks for it.
- Link covered issues in the PR body.
- Avoid force-push surprises unless the project expects rebases.
- Keep generated files out unless required.
- Do not claim CI passed until it did.
- If local checks differ from CI, name the difference.

## Risk Language

Good:

- "Verified on Windows PowerShell and existing tests."
- "This preserves the existing command order and only changes the hidden launcher path."
- "I did not change behavior outside the Windows restart helper."

Bad:

- "Should be fixed."
- "Probably works."
- "Refactored the module while I was here."
- "CI was flaky so I ignored it."
