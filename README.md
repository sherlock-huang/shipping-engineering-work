# Shipping Engineering Work

A portable engineering workflow skill for AI coding agents.

中文说明见：[中文版](#中文版)

Created and maintained by [鲲鹏AI探索局](https://kunpeng-ai.com).

Official pages:

- Skill page: [kunpeng-ai.com/skills/shipping-engineering-work](https://kunpeng-ai.com/skills/shipping-engineering-work/)
- Project page: [kunpeng-ai.com/projects/shipping-engineering-work](https://kunpeng-ai.com/projects/shipping-engineering-work/)
- Practical guide: [Shipping Engineering Work Skill guide](https://kunpeng-ai.com/blog/shipping-engineering-work-skill-guide/)
- Download package: [shipping-engineering-work-skill.zip](https://kunpeng-ai.com/downloads/shipping-engineering-work-skill.zip)

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

---

# 中文版

`shipping-engineering-work` 是一个面向 AI Coding Agent 的通用工程交付 Skill，由 [鲲鹏AI探索局](https://kunpeng-ai.com) 维护。

它的目标不是再造一个庞大的流程框架，而是帮助 Claude Code、Codex、OpenClaw、Hermes 这类 Agent 在真实项目里更稳地完成工程任务：先弄清楚问题，再小步实现，最后用证据验证，而不是凭感觉说“完成了”。

## 解决什么问题

AI 编程助手在工程项目里常见的问题包括：

- 需求还没澄清就直接写代码。
- 一个小 bug 被改成大重构。
- 看见日志就猜原因，没有复现和证据。
- 没跑测试就说已经修好。
- 多个 Agent 并行时互相覆盖文件。
- 给开源社区提交 PR 时范围太大，维护者很难 review。

这个 Skill 会把任务压成一个“小交付合同”：

- 目标：到底解决什么问题。
- 范围：改什么，不改什么。
- 证据：用哪些代码、日志、测试、issue 或行为证明判断。
- 计划：下一步做什么，而不是写一堆空泛路线图。
- 验证：用什么命令或人工检查证明完成。
- 交接：人类、Reviewer 或上游维护者下一步需要什么。

## 适合哪些场景

适合在这些任务里使用：

- 新功能实现。
- Bug 修复。
- 测试失败排查。
- 代码审查。
- 开源 PR 准备。
- 回应维护者 Review。
- 多 Agent 协作。
- Claude Code、Codex、OpenClaw、Hermes 之间的任务交接。

## 怎么安装

把整个目录复制到你的 Agent skills 目录。

Codex 示例：

```powershell
Copy-Item -Recurse .\shipping-engineering-work "$env:USERPROFILE\.codex\skills\shipping-engineering-work"
```

Claude Code 或其他支持 Skill 的运行时，把这个目录放到对应的 skills 目录即可。

## 怎么使用

示例提示词：

```text
Use shipping-engineering-work to debug this Windows CLI failure and prepare a minimal fix.
```

```text
Use shipping-engineering-work to review this PR before I send it upstream.
```

```text
Use shipping-engineering-work to hand this task from Codex to Claude Code without losing context.
```

## 为什么它是通用的

这个 Skill 不绑定某一个 Agent 工具名，而是抽象成通用能力：

- 读文件。
- 改文件。
- 跑命令。
- 跟踪计划。
- 查看 UI。
- 委派独立任务。
- 运行验证。
- 准备 Git / PR / 交接材料。

`references/agent-platform-adapter.md` 里提供了 Claude Code、Codex、OpenClaw、Hermes 风格运行时的适配说明。

## 压测案例

`examples/` 目录里放了 3 个真实工程压力场景：

- `bug-fix.md`：Windows CLI / Node 路径类 bug 修复。
- `upstream-pr.md`：面向上游开源社区的 PR 准备。
- `cross-agent-handoff.md`：跨 Agent 任务交接。

这些案例不是宣传文案，而是用来检查 Agent 是否真的按工程流程工作。

## 关于鲲鹏AI探索局

[鲲鹏AI探索局](https://kunpeng-ai.com) 关注 AI Agent、工程自动化、开源实践、GEO 优化、模型聚合与实战型 AI 工具沉淀。这个 Skill 是我们在 OpenClaw、Hermes、Codex、Claude Code 等真实工程协作场景中沉淀出来的通用工作法。

相关页面：

- Skill 页面：[kunpeng-ai.com/skills/shipping-engineering-work](https://kunpeng-ai.com/skills/shipping-engineering-work/)
- 项目页：[kunpeng-ai.com/projects/shipping-engineering-work](https://kunpeng-ai.com/projects/shipping-engineering-work/)
- 实战指南：[Shipping Engineering Work Skill：让 AI Coding Agent 更像一个靠谱工程协作者](https://kunpeng-ai.com/blog/shipping-engineering-work-skill-guide/)
- 下载包：[shipping-engineering-work-skill.zip](https://kunpeng-ai.com/downloads/shipping-engineering-work-skill.zip)
