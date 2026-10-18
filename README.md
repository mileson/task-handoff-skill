# Task Handoff

[English](README.md) | [简体中文](README_CN.md)

> A Claude Code / Cursor skill that turns messy ongoing work into a clean, executable handoff package for another user, another agent, or your future self.

[Features](#readme-section-1) · [Best Use Cases](#readme-section-3) · [Quick Start](#readme-section-4) · [Output Structure](#readme-section-6) · [Why This Skill Exists](#readme-section-11) · [Project Structure](#readme-section-13) · [Security](#readme-section-14)

<a id="readme-section-1"></a>

## Features

- **Compresses noisy context** into a concise handoff summary
- **Generates a reusable handoff prompt** for another user or agent
- **Separates facts from uncertainty** with `confirmed / unverified / pending confirmation`
- **Preserves execution-critical context** like repo path, worktree, branch, logs, commands, IDs, and constraints
- **Optimizes for actionability** so the next executor knows what to read first and what to do next
- **Supports multiple task types** including bug triage, feature continuation, remote ops, and multi-worktree handoff

<a id="readme-section-2"></a>

## What It Does

- **Compresses noisy context** into a concise handoff summary
- **Generates a reusable handoff prompt** for another user or agent
- **Separates facts from uncertainty** with `confirmed / unverified / pending confirmation`
- **Preserves execution-critical context** like repo path, worktree, branch, logs, commands, IDs, and constraints
- **Optimizes for actionability** so the next executor knows what to read first and what to do next
- **Supports multiple task types** including bug triage, feature continuation, remote ops, and multi-worktree handoff

<a id="readme-section-3"></a>

## Best Use Cases

### 1. Bug / Incident Handoff
When you've debugged for a while and don't want the next person to re-read a huge conversation or raw logs.

### 2. Continue Development in a Fresh Session
When the current session is bloated or drifting, and you want to restart with only the essential context.

### 3. Multi-Agent Collaboration
When one agent has done investigation, another agent should implement, and you want only the distilled conclusions to carry forward.

### 4. Worktree / Environment Transfer
When the next step must continue in a different branch, worktree, machine, or remote host.

<a id="readme-section-4"></a>

## Quick Start

1. Copy the `task-handoff` folder into your local skills directory
2. Restart Claude Code / Cursor if needed
3. Ask the model to create a handoff prompt for the current task

<a id="readme-section-5"></a>

## Installation

Copy this folder into your local skills directory.

### Claude Code

```bash
cp -R task-handoff ~/.claude/skills/
```

### Cursor / Codex-style Skills Folder

```bash
cp -R task-handoff ~/.cursor/skills/
```

<a id="readme-section-6"></a>

## Output Structure

By default, the skill produces two blocks:

1. **Handoff Summary**
   - 5–10 lines for fast scanning
2. **Complete Handoff Prompt**
   - directly reusable as the next prompt

It can also include a very short acceptance checklist when needed.

<a id="readme-section-7"></a>

## Workflow

The skill follows this logic:

1. Identify the handoff type
2. Extract the minimum necessary context
3. Keep only materials that affect the next step
4. Mark the fact boundary clearly
5. Produce a clean summary + executable prompt

<a id="readme-section-8"></a>

## Usage

### Natural Language

```text
Please turn the current task into a handoff prompt for another agent.
```

```text
整理一下当前上下文，生成一个接手继续做的交接提示词。
```

### Skill Invocation

```text
/task-handoff
```

<a id="readme-section-9"></a>

## Example Prompts

- `Create a handoff package for this unfinished bug investigation.`
- `Summarize the current worktree status and produce a prompt for the next agent.`
- `不要从零分析，帮我把当前进度整理成可直接接手的 handoff prompt。`
- `Prepare a concise handoff for remote ops acceptance, including host, service, logs, and next verification step.`

<a id="readme-section-10"></a>

## Agent Prompt Pattern

You can use this skill when you want a model to stop continuing the current messy session and prepare a clean transfer package instead.

```text
Use the task-handoff skill.
Compress the current state into:
1. a short handoff summary
2. a complete handoff prompt
Clearly separate confirmed facts, unverified items, next steps, and things that must not be changed.
```

<a id="readme-section-11"></a>

## Why This Skill Exists

Long sessions are powerful, but they also decay.

When a task gets stuck, branches into multiple directions, or needs to be continued in another worktree or by another agent, the real bottleneck is often **not implementation** — it is **context transfer**.

`task-handoff` codifies a practical habit:

- stop appending more noisy turns,
- compress only the facts that still matter,
- separate confirmed findings from guesses,
- and hand over a prompt that lets the next executor work immediately.

In short: this skill helps you do the deliberate, high-quality handoff that a fresh session actually needs.

<a id="readme-section-12"></a>

## Design Principles

- **Actionability over completeness**
- **Fresh-session friendly**
- **Precise facts beat vague summaries**
- **Do not mix completed work with recommended next steps**
- **Keep context small, but keep the next move obvious**

<a id="readme-section-13"></a>

## Project Structure

```text
task-handoff/
├── SKILL.md        # Skill behavior and workflow rules
├── template.md     # Default handoff prompt template
├── README.md       # English overview
├── README_CN.md    # Chinese overview
├── CONTRIBUTING.md # Contribution guide
├── SECURITY.md     # Security disclosure policy
└── LICENSE         # MIT license
```

<a id="readme-section-14"></a>

## Security

See [SECURITY.md](SECURITY.md).

<a id="readme-section-15"></a>

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md).

<a id="readme-section-16"></a>

## License

[MIT](LICENSE) © 2026 Mileson

<a id="readme-section-17"></a>

## Author
- X: [Mileson07](https://x.com/Mileson07)
- Xiaohongshu: [超级峰](https://xhslink.com/m/4LnJ9aB1f97)
- Douyin: [超级峰](https://v.douyin.com/rH645q7trd8/)
