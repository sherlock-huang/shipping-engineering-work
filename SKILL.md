---
name: shipping-engineering-work
description: Use when an AI coding agent is asked to plan, implement, debug, review, test, ship, or upstream engineering work in a real codebase, especially when requirements are ambiguous, changes are risky, verification matters, multiple agents may be involved, or work must be portable across Claude Code, Codex, OpenClaw, and Hermes.
---

# Shipping Engineering Work

## Overview

Ship small, useful, verified engineering changes. This skill combines product judgment, implementation discipline, evidence-based debugging, and contribution hygiene without depending on one agent platform's tool names.

## Core Contract

Before doing non-trivial work, make a small delivery contract:

- Goal: what user-visible or maintainer-visible problem is being solved.
- Scope: what will change and what will stay untouched.
- Evidence: what files, logs, docs, issues, tests, or behavior prove the diagnosis.
- Plan: the next few steps, not a fantasy roadmap.
- Verification: exact command or manual check needed before claiming success.
- Handoff: what the user, reviewer, or upstream maintainer needs next.

For tiny tasks, this can be one sentence. For risky work, write it as a short plan.

## Mode Selection

Choose the lightest mode that fits the risk:

| Mode | Trigger | Output |
| --- | --- | --- |
| Frame | Ambiguous request, broad idea, unclear success | problem, options, recommendation |
| Inspect | Existing codebase or unfamiliar behavior | evidence summary and next step |
| Design | New behavior or architecture choice | small spec or design sketch |
| Implement | Clear change with known tests | patch plus verification |
| Debug | Failure, test break, log error, regression | repro, cause, fix, regression check |
| Review | Asked for review or before upstream PR | findings, risks, tests, maintainer notes |
| Upstream | Open-source contribution or PR response | minimal patch, docs/changelog, PR body |

Read `references/workflow-modes.md` when mode choice is unclear or the task spans multiple modes.

## Delivery Loop

1. Frame the real problem. Ask "what would make this worth shipping?"
2. Inspect before editing. Read nearby code, tests, docs, issues, logs, and current git state.
3. Slice thinly. Prefer the smallest change that creates verifiable value.
4. Preserve local conventions. Use existing patterns, tooling, structure, and maintainer style.
5. Work with evidence. For bugs, reproduce or identify the concrete failure before fixing.
6. Add tests when behavior changes. If tests are unavailable, state the manual verification path.
7. Verify fresh. Run the relevant command and read the output before claiming success.
8. Package the result. Summarize changes, verification, risks, and next steps.

## Platform Neutrality

Do not write instructions that only work in one agent runtime when the idea is portable. Refer to capabilities, then map them to the current platform:

- read files
- edit files
- run shell commands
- browse or inspect UI
- track plan/todos
- delegate work
- run verification
- inspect git and create handoff/PR artifacts

Read `references/agent-platform-adapter.md` when writing docs, skills, or prompts intended for Claude Code, Codex, OpenClaw, and Hermes.

## Collaboration Rules

- Protect user changes. Never revert unrelated dirty work.
- Prefer concrete questions over long speculative lists.
- Use parallel work only when tasks are independent and file ownership is clear.
- Keep humans in the loop for destructive commands, production deploys, credentials, public posting, and upstream PR strategy.
- When interrupted, answer the latest request and continue from the real current state.

## Engineering Guardrails

- No implementation before understanding enough context.
- No broad refactor unless it is necessary for the requested change.
- No "done" claim without fresh verification evidence.
- No hidden assumptions in public or upstream-facing claims.
- No mock confidence: say what was verified, what was not, and why.

## Upstream Readiness

For open-source work, optimize for maintainers:

- Minimal patch.
- Clear issue link or user problem.
- Tests or explicit verification.
- Docs/changelog when behavior changes.
- Backward compatibility and platform compatibility.
- PR body that explains why this shape is low-risk.

Read `references/contribution-readiness.md` before preparing an upstream PR or responding to maintainer review.

## Common Failures

| Failure | Correction |
| --- | --- |
| Building before understanding | Inspect and state a small delivery contract |
| Treating a guess as root cause | Reproduce, find evidence, or label it as hypothesis |
| Overbuilding abstractions | Ship the narrow verified change first |
| Writing tests after the fact only | Prefer behavior-first tests and watch failures when feasible |
| Parallel agents collide | Assign disjoint ownership and integration points |
| Claiming success from vibes | Run verification and report exact result |
| PR is hard to merge | Shrink scope, match style, add maintainer metadata |

## Completion Standard

Final response should include:

- What changed.
- What was verified, with command or check.
- Any residual risk or unverified area.
- Practical next step only when useful.
