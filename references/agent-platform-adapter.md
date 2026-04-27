# Agent Platform Adapter

Use capability names in portable guidance. Map them to the current agent runtime during execution.

## Capability Map

| Capability | Claude Code | Codex | OpenClaw / Hermes style |
| --- | --- | --- | --- |
| Read files | Read, Glob, Grep | shell, rg, open files, MCP resources | shell/file tools exposed by runtime |
| Edit files | Edit, MultiEdit, Write | apply_patch preferred for manual edits | runtime edit tool or patch file |
| Run shell | Bash | shell_command | command execution tool |
| Track plan | TodoWrite | update_plan | task/memory/tool-specific todo |
| Browse UI | browser/MCP/browser tools | Browser Use / Chrome DevTools | browser automation if configured |
| Delegate | Task/subagents | spawn_agent only when requested | workflow/subagent/agent handoff if available |
| Verify | shell/tests/build/manual checks | shell/tests/build/manual checks | command/test tool plus logs |
| Git/PR | shell/gh/GitHub tools | shell/gh/GitHub tools | shell/gh or platform integration |

## Portable Language

Prefer:

- "read the relevant files"
- "run the focused test command"
- "apply a small patch"
- "update the task plan"
- "delegate an independent subtask if the platform supports it"

Avoid:

- "use Bash" when shell capability is enough
- "use TodoWrite" in general-purpose docs
- "use the Task tool" when a runtime may not have subagents
- "use MultiEdit" when patch/edit capability is the real requirement

## Platform-Specific Notes

Claude Code:

- Strong for file edits, task delegation, and long-running repo work.
- Skills often mention Claude-specific tools; translate to capabilities when writing open docs.

Codex:

- Prefer `rg` for search and `apply_patch` for manual edits.
- Use `update_plan` for visible progress on multi-step work.
- Subagents should be used only when explicitly authorized by the user.

OpenClaw / Hermes:

- Treat them as agent runtimes or workflows where tool availability may vary.
- Rely on shell, logs, project files, and explicit handoff artifacts.
- Keep instructions compatible with Windows, Node, PowerShell, and CLI-heavy environments when relevant.

## Handoff Shape

Portable handoff should contain:

- Current goal.
- Repo and branch.
- Files touched.
- Commands run and results.
- Open questions.
- Next safe action.
