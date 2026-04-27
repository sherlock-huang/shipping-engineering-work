# Pressure Test: Upstream PR

## Prompt

```text
Use shipping-engineering-work to prepare an upstream PR for this fix:

The Windows scheduled task restart helper opens a visible cmd window after update.
Maintainers want the hidden wrapper preserved, no findstr, and tests for custom task names and ports.
```

## Expected Agent Behavior

The agent should enter Upstream Mode. It should:

1. Read nearby maintainer style, tests, and changelog expectations.
2. Keep the patch focused on the Windows restart helper.
3. Preserve existing command ordering if maintainers care about it.
4. Add tests for default/custom task names and custom ports.
5. Add changelog or issue links if the project expects them.
6. Run focused tests.
7. Prepare a PR body with summary, why, verification, and notes.

## Failure Signs

- Bundling unrelated refactors.
- Removing policy-compatible wrappers without evidence.
- Ignoring maintainer metadata such as changelog or issue links.
- Saying CI passed before it did.

## Good PR Body Shape

```markdown
## Summary

- Keep the Windows hidden launcher wrapper during gateway restarts.
- Replace visible listener probing with a hidden PowerShell path.
- Cover default/custom task names and custom ports.

## Why

This avoids visible cmd windows after update while preserving task restart behavior.

## Verification

- npm test -- config/restart-helper.test.ts

## Notes

- No behavior change outside the Windows restart helper.
```
