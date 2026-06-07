# Agent Builder Skill

`agent-builder` is a reusable agent skill for creating compact, durable
`AGENTS.md` guidance for a repository. It helps an agent interview before
drafting, keep the root `AGENTS.md` short, split deeper rules into
`docs/agents/*`, and recommend focused `/agents` subagents when the project
would benefit from them.

## What This Skill Does

Use this skill when you want to create, improve, review, or reorganize agent
instructions for a codebase. It is especially useful when a repository needs:

- a short root `AGENTS.md` that future agents will actually read
- durable project commands, guardrails, testing expectations, and response style
- supporting `docs/agents/*` files for stack, security, database, frontend, or
  deployment details
- `/agents` subagent plans for distinct workstreams such as frontend, backend,
  database, CI, docs, architecture, or security review

The root rule is simple: interview first, then write. The skill should not draft
final agent instructions until it has asked the minimum required questions or
has clearly marked assumptions that the user approved.

## When To Use It

Use `agent-builder` for prompts like:

```text
Create an AGENTS.md for this repository.
```

```text
Review our AGENTS.md and make it shorter.
```

```text
Move our long agent instructions into docs/agents and propose subagents.
```

```text
Plan /agents for this project so future coding agents can split work safely.
```

Do not use it as a general coding workflow skill. It is specifically for agent
instructions, repo guidance, and subagent planning.

## How The Workflow Works

1. Inspect the repository, examples, package files, docs, and existing agent
   instructions.
2. Ask the required interview questions about project identity, stack, commands,
   guardrails, dependencies, worktrees, documentation policy, subagents, and
   final response style.
3. Summarize answers and assumptions before drafting.
4. Create or update `AGENTS.md` with a hard 200-line maximum.
5. Split detailed guidance into `docs/agents/*` when the root file would become
   too long or too specialized.
6. Recommend `/agents/orchestrator.md` whenever recommending more than one
   subagent.
7. Verify line count, links, commands, placeholders, and subagent ownership.

## Expected Output Files

Depending on the repository and the user's choices, the skill may create or
recommend:

- `AGENTS.md`
- `docs/agents/*.md`
- `agents/orchestrator.md`
- `agents/{subagent}/subagent.md`
- `agents/{subagent}/info/*`
- `agents/{subagent}/scripts/*`

The skill keeps `AGENTS.md` as the quick-start operating guide. Deeper or
less-frequently-needed details belong in supporting files.

## Quality Gates

Before finishing, the agent should confirm:

- `AGENTS.md` is 200 lines or fewer
- every linked `docs/agents/*` or `/agents/*` path exists
- commands came from repository files or user answers
- placeholders are removed or clearly marked as assumptions requiring
  confirmation
- subagents have clear purpose, inputs, editable areas, forbidden areas,
  verification, and final output format
- the final response lists files created, verification performed, and open risks

## Where To Save It

Copy the whole `agent-builder` folder, including `SKILL.md` and `examples/`, into
the skill directory for the agent you want to use.

### Codex

Current Codex docs list these authored-skill discovery paths:

| Scope | Save as |
| --- | --- |
| Repository | `.agents/skills/agent-builder/SKILL.md` |
| Personal user | `$HOME/.agents/skills/agent-builder/SKILL.md` |

Codex can invoke the skill implicitly when a request matches its description, or
explicitly by selecting it from `/skills` or mentioning `$agent-builder`.

This copy currently lives at:

```text
~/.codex/skills/agent-builder
```

That may work in local or previously migrated setups, but for new authored
skills use `.agents/skills` or `$HOME/.agents/skills` unless your Codex setup is
intentionally loading another directory.

### Claude Code

Claude Code docs list these skill discovery paths:

| Scope | Save as |
| --- | --- |
| Project | `.claude/skills/agent-builder/SKILL.md` |
| Personal user | `~/.claude/skills/agent-builder/SKILL.md` |

Claude Code can invoke the skill implicitly when a request matches its
description, or explicitly with:

```text
/agent-builder
```

## Files In This Skill

- `SKILL.md` - the main skill instructions
- `examples/basic-template.md` - compact `AGENTS.md` starter shape
- `examples/agents-example.md` - alternate compact example
- `examples/Very-long-AGENTS.md` - fuller example that still demonstrates a
  bounded root guide

For current platform details, see the official
[Codex Agent Skills docs](https://developers.openai.com/codex/skills) and
[Claude Code skills docs](https://code.claude.com/docs/en/skills).
