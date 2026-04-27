# Shipping Engineering Work

A portable engineering workflow skill for AI coding agents.

It helps an agent turn a vague engineering request into a small, verified, reviewable delivery. The skill blends product judgment, evidence-based debugging, implementation discipline, and upstream contribution hygiene without depending on one agent runtime's tool names.

Designed for:

- Claude Code
- Codex
- OpenClaw-style agent runtimes
- Hermes-style agent runtimes
- Other CLI-first coding agents with file, shell, git, and verification capabilities

## What Problem It Solves

AI coding agents often fail in predictable ways:

- They start coding before understanding the real problem.
- They make broad refactors for narrow bugs.
- They guess root causes from logs without evidence.
- They say "done" without running the right checks.
- They collide when multiple agents work in parallel.
- They open upstream PRs that are too large or hard to review.

This skill gives the agent a compact workflow for shipping real engineering work safely:

1. Frame the real problem.
2. Inspect before editing.
3. Make a small delivery contract.
4. Work in thin slices.
5. Verify with fresh evidence.
6. Package the result for a human, reviewer, or maintainer.

## Repository Layout

```text
shipping-engineering-work/
  SKILL.md
  agents/
    openai.yaml
  references/
    agent-platform-adapter.md
    workflow-modes.md
    contribution-readiness.md
  examples/
    bug-fix.md
    upstream-pr.md
    cross-agent-handoff.md
```

## Install

Copy this directory into your agent skill directory.

For Codex:

```powershell
Copy-Item -Recurse .\shipping-engineering-work "$env:USERPROFILE\.codex\skills\shipping-engineering-work"
```

For Claude Code or other skill-compatible runtimes, place the folder in the runtime's configured skills directory.

## When To Use

Use this skill when an AI coding agent is asked to:

- implement a feature
- fix a bug
- debug failing tests
- review code
- prepare an upstream PR
- respond to maintainer review
- coordinate multiple agents
- hand off work across Claude Code, Codex, OpenClaw, Hermes, or similar runtimes

## Core Idea

Every non-trivial engineering task should have a small delivery contract:

- Goal
- Scope
- Evidence
- Plan
- Verification
- Handoff

For tiny tasks, this can be one sentence. For risky work, make it a short plan.

## Example Prompts

```text
Use shipping-engineering-work to debug this Windows CLI failure and prepare a minimal fix.
```

```text
Use shipping-engineering-work to review this PR before I send it upstream.
```

```text
Use shipping-engineering-work to hand this task from Codex to Claude Code without losing context.
```

## Why It Is Portable

The skill describes capabilities instead of hard-coding tool names:

- read files
- edit files
- run shell commands
- track a plan
- inspect UI
- delegate independent subtasks
- verify behavior
- prepare git/PR artifacts

`references/agent-platform-adapter.md` maps those capabilities to Claude Code, Codex, OpenClaw, and Hermes-style environments.

## Validation Cases

The `examples/` folder includes three pressure tests:

- bug fix
- upstream PR
- cross-agent handoff

They are written as realistic prompts plus expected behavior, so maintainers can test whether an agent actually follows the workflow instead of treating it as motivational text.

## License

MIT
