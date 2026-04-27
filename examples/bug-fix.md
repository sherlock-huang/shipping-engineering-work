# Pressure Test: Bug Fix

## Prompt

```text
Use shipping-engineering-work to fix this bug:

On Windows, after upgrading a CLI tool, the gateway starts but the messaging channel exits with:

"Only URLs with a scheme in: file, data, and node are supported by the default ESM loader. On Windows, absolute paths must be valid file:// URLs. Received protocol 'c:'"

Please patch the issue quickly.
```

## Expected Agent Behavior

The agent should not jump straight to a patch. It should:

1. Capture the exact symptom and platform.
2. Inspect the code path that loads the channel/plugin.
3. Identify whether Windows absolute paths are passed to ESM import without conversion to `file://`.
4. Create or identify a focused test or manual repro.
5. Patch the smallest loader boundary.
6. Verify on Windows or state the exact manual verification if Windows is unavailable.
7. Summarize root cause, files changed, verification, and residual risk.

## Failure Signs

- Suggesting "downgrade Node" as the only fix without inspecting code.
- Rewriting the whole plugin loader.
- Claiming success without a test or command.
- Ignoring Windows path behavior.

## Good Final Shape

```text
Root cause: Windows absolute paths were passed directly to dynamic import.
Change: convert filesystem paths to file URLs at the plugin/channel import boundary.
Verification: focused loader test passes; manual Windows command provided.
Risk: only affects local file path imports; remote/data/node specifiers unchanged.
```
