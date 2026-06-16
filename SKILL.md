---
name: agent-builder
description: Use when creating or updating AGENTS.md, project agent instructions, docs/agents guidance, or /agents subagent plans for a repository
---

# Agent Builder

## Overview

Create a short, useful `AGENTS.md` by inspecting the repository, asking only
for risky unknowns, and splitting durable details into supporting files when
needed. The root `AGENTS.md` is the quick-start operating guide, not the
encyclopedia.

**Core rule:** Inspect first. For durable or high-stakes instructions, use the
full interview before finalizing. For a fast first draft, draft with a clearly
marked `Assumptions to confirm` section and mark risky unknowns as
`confirm before use`. Never invent commands, deployment details, or policies.

## When To Use

Use this skill when the user asks to:

- create, improve, review, or rewrite `AGENTS.md`
- define coding-agent rules for a repository
- plan `/agents` subagents, orchestrators, reviewers, or task agents
- organize agent docs under `docs/agents`
- migrate long agent instructions into a shorter root guide

## Non-Negotiables

- `AGENTS.md` must be at most 200 lines.
- If details do not fit, split them into `docs/agents/*` and link from
  `AGENTS.md`; skip the split for small repos when one compact root file is
  enough.
- Ask only for facts that are not safely discoverable from repository files.
- Recommend `/agents/orchestrator.md` whenever recommending more than one
  subagent.
- Recommend focused subagents only when the project has distinct workstreams,
  ownership boundaries, or context-management needs.
- Preserve user preferences when they conflict with defaults.

## Quick Workflow

1. Inspect the repository, examples, package files, docs, and existing agent
   instructions.
2. Choose Standard Mode, Small Repo Mode, or Fast Draft With Assumptions.
3. Ask only the essential questions for that mode. Ask one at a time for
   ambiguous or high-impact choices; group low-risk questions when the user
   asks for speed.
4. Summarize the answers and assumptions before writing.
5. Draft `AGENTS.md` with a 200-line budget.
6. Split detailed guidance into `docs/agents/*` when needed.
7. Propose `/agents` subagents only when they are justified.
8. Verify line count, links, commands, and unresolved placeholders.

## Modes

### Standard Mode

Use for durable instructions, high-stakes repos, shared teams, production
systems, or repositories with multiple stacks or workflows. Inspect the repo,
run the full interview for missing facts, summarize answers and assumptions,
then draft.

### Small Repo Mode

Use for tiny repos, solo projects, static sites, throwaway prototypes,
early-stage repos, and simple single-purpose libraries. Prefer one compact
`AGENTS.md` only. Do not create a `docs/agents` split unless the root file
would exceed 200 lines or the user asks for it. Do not recommend `/agents`
unless explicitly requested or clearly justified by distinct workstreams.

Keep the interview short and focused on risky unknowns. The 200-line
`AGENTS.md` cap still applies.

### Fast Draft With Assumptions

Use when the user asks for speed, a quick version, or a first draft. Inspect
repo files first, then draft useful guidance with an `Assumptions to confirm`
section. Mark risky unknowns as `confirm before use`.

Do not invent commands, deployment details, dependency policies, task-doc
rules, or git policies. If a command or policy is not in repo files or user
answers, either omit it or mark it as an assumption to confirm.

## Interview

Start with repository-discoverable facts. Ask only for what cannot be known
safely from files.

### Full Interview

Use this as the comprehensive path. Ask only for answers that are not safely
discoverable from files:

1. **Project identity:** What is the project name, purpose, target user, and
   owner skill level?
2. **Tech stack:** Which frameworks, languages, runtimes, package managers,
   databases, deployment targets, and test tools are canonical?
3. **Commands:** What are the install, dev, build, lint, test, typecheck,
   migration, and deploy commands? Should agents only use scripts from checked
   in package files?
4. **Guardrails:** What should agents never do automatically?
5. **Dependencies:** May agents install packages? Recommended default: no, ask
   first.
6. **Git and worktrees:** Should agents use git worktrees, and what path should
   they use? Recommended default: yes for non-trivial implementation, under
   `.worktrees/`.
7. **Documentation policy:** Should every task be documented, or only
   non-trivial tasks? Recommended default: non-trivial tasks. If enabled, use
   `docs/tasks/{ascending-number}-{iso-timestamp}-{task-title}/summary.md` and
   `docs/tasks/{ascending-number}-{iso-timestamp}-{task-title}/next-steps.md`.
8. **Subagents:** Should the project use `/agents`? Recommend based on the
   answers and explain which subagents are useful.
9. **Final response style:** How should agents summarize changes, tests, docs,
   risks, and follow-ups?

### Guardrail Examples

Offer examples and ask the user to choose or edit them:

- Do not install dependencies without permission.
- Do not delete, overwrite, push, deploy, force-push, or run destructive git
  commands without explicit approval.
- Do not print, request, or commit secrets.
- Do not weaken tests, type checks, auth, authorization, billing, migrations,
  or CI to make work pass.
- Do not change unrelated files or revert user changes.
- Do not invent commands. Read package files and docs first.
- Ask before schema changes, production data changes, paid services, deploy
  topology changes, and breaking public APIs.

### Quick Draft Interview

For Small Repo Mode or Fast Draft With Assumptions, ask only for missing facts
that would be risky to guess:

```text
Before I draft it, I need the few choices that would be risky to guess:
1. stack and package manager, if not discoverable
2. canonical install/dev/build/test/lint commands, if not discoverable
3. forbidden actions
4. dependency install policy
5. deploy, push, force-push, and destructive git policy
```

If the user cannot answer, draft an `Assumptions to confirm` section and mark
every risky unknown as `confirm before use`.

## AGENTS.md Shape

Use `examples/basic-template.md` for a small project shape and
`examples/agents-example.md` when a compact `/agents` plan is justified. Use
`examples/Very-long-AGENTS.md` as an example of a fuller but still compact
guide.

Treat examples as structure only. Do not copy template placeholders or external
links into a final `AGENTS.md`.

Recommended sections:

- Project Overview
- Source Of Truth
- Commands
- Agent Workflow
- Non-Negotiable Guardrails
- Worktrees And Git
- Documentation Policy
- Testing And Verification
- Subagent Plan
- Final Response

### Line Budget

Keep `AGENTS.md` readable:

| Section | Target |
| --- | --- |
| Overview and source of truth | 20 lines |
| Commands | 20 lines |
| Workflow and guardrails | 55 lines |
| Stack conventions | 40 lines |
| Testing, docs, git, final response | 45 lines |
| Subagent summary and links | 20 lines |

If the draft approaches 180 lines, stop adding detail and split files.

## Splitting Details

Move expanded guidance into `docs/agents/` when:

- `AGENTS.md` would exceed 200 lines
- a topic has many stack-specific rules
- guidance is useful but not needed on every task
- subagents need deeper background

In Small Repo Mode, skip `docs/agents/` unless a split is needed to stay under
the 200-line root cap or the user asks for separate docs.

Common files:

- `docs/agents/stack.md`
- `docs/agents/testing.md`
- `docs/agents/security.md`
- `docs/agents/database.md`
- `docs/agents/frontend.md`
- `docs/agents/deployment.md`
- `docs/agents/documentation.md`
- `docs/agents/subagents.md`

In `AGENTS.md`, link to the detailed file and keep only the rule that decides
when to read it.

## Task Documentation Policy

If the user wants task documentation, add this convention:

```text
For each non-trivial task, create:
docs/tasks/{ascending-number}-{iso-timestamp}-{task-title}/summary.md
docs/tasks/{ascending-number}-{iso-timestamp}-{task-title}/next-steps.md
```

Use an ascending number such as `001`, `002`, `003`. Use an ISO timestamp such
as `2026-05-10T15-30-00Z` or the repository's preferred timezone format.
Projects may override this if they already have an established task-doc format.

`summary.md` should include:

- request
- decisions
- files changed
- verification
- unresolved risks

`next-steps.md` should include:

- recommended follow-ups
- deferred work
- cleanup opportunities
- owners or prerequisites when known

## Subagent Planning

Whenever recommending more than one subagent, include `agents/orchestrator.md`
by default unless the user explicitly declines it. Also recommend an
orchestrator for projects with multiple workstreams, high-risk domains, or
recurring review needs.

Subagents are for context management and ownership boundaries, not decoration.
Recommend them when separate workers can safely own different domains,
background, or verification.

### When Not To Use Subagents

Do not recommend subagents by default for:

- small static sites
- single-purpose libraries
- small solo repos
- prototypes
- one-file or low-risk changes
- repos without distinct workstreams

In these cases, prefer a compact `AGENTS.md` and optional notes in
`Assumptions to confirm`.

### Recommended Structure

```text
agents/
  orchestrator.md
  frontend/
    subagent.md
    info/
  backend/
    subagent.md
    info/
  database/
    subagent.md
    info/
  ci/
    subagent.md
    scripts/
    info/
  docs/
    subagent.md
    info/
```

Use folders when a subagent needs support files. Use a single
`agents/{name}.md` only for tiny prompts with no scripts or reference material.

### Orchestrator Duties

`agents/orchestrator.md` should say how to:

- understand the task and constraints
- decide whether subagents are useful
- split independent work without overlapping write scopes
- keep the root context small
- integrate findings and patches
- run final verification
- report changed files, checks, docs, and residual risk

### Choosing Subagents

Recommend subagents from the interview:

| Project signal | Suggested subagent |
| --- | --- |
| UI framework, design system, accessibility | `frontend` or `ui-reviewer` |
| API, services, auth, queues | `backend` |
| Database, Prisma, Supabase, migrations, RLS | `database` |
| CI, deployment, build failures | `ci` |
| Docs-heavy process or task logs | `docs` |
| Security, billing, secrets, payments | `security-reviewer` |
| Large refactors or architecture decisions | `architect` |

For each recommended subagent, define:

- purpose
- when to use
- inputs it needs
- files it may edit
- files it must not edit
- verification it should run
- final output format

## Output Package

When creating files, propose or create this package:

- `AGENTS.md`
- `docs/agents/*.md` for detailed guidance when needed
- `agents/orchestrator.md` when recommending more than one subagent or when the
  project needs coordination
- `agents/{subagent}/subagent.md` for each focused subagent
- `agents/{subagent}/info/*` for durable context
- `agents/{subagent}/scripts/*` only for reusable tooling

End with a short rationale explaining why each file exists.

## Quality Gates

Before finishing:

- Run `wc -l AGENTS.md` if the file exists.
- Confirm `AGENTS.md` is 200 lines or fewer.
- Search for leftover placeholders such as `[Name]`, `TODO`, and `TBD`.
- Check every linked `docs/agents/*` or `agents/*` path exists if you created
  links.
- Confirm commands came from repo files or user answers.
- Remove placeholders, or mark them as assumptions requiring confirmation.
- Confirm subagents have non-overlapping ownership where they may edit files.
- Confirm the final response lists files created, verification, and open risks.

Useful checks:

```bash
wc -l AGENTS.md
rg -n "\[[^]]+\]|TODO|TBD" AGENTS.md docs/agents agents
rg -n "docs/agents|agents/" AGENTS.md
```

For each command listed in `AGENTS.md`, confirm it appears in repo files or the
user's answers.

## Red Flags

Stop and correct course if you think:

- "The user asked for speed, so I can skip questions."
- "The user asked for speed, so I can invent commands."
- "One long AGENTS.md is simpler."
- "Every repo should have subagents."
- "I can infer commands from the stack."
- "I should include every possible rule in the root file."
- "The user can clean up the structure later."

## Rationalizations And Counters

| Rationalization | Counter |
| --- | --- |
| "The user is in a hurry." | Inspect first, ask only risky unknowns, and mark assumptions clearly. |
| "A comprehensive file prevents questions." | Overlong instructions are skipped. Keep root under 200 lines and split details. |
| "Subagents sound fancy." | They are a context-management tool. Recommend them only when workstreams are distinct. |
| "The stack tells me the commands." | Commands belong to the repo and user, not the framework. Read or ask. |
| "Guardrails are obvious." | They differ by project. Ask about installs, deploys, pushes, secrets, and destructive actions. |

## Common Mistakes

- Drafting before interviewing.
- Treating examples as universal instead of adapting them.
- Encoding volatile details in `AGENTS.md` instead of docs.
- Creating subagents without clear inputs, ownership, and verification.
- Linking to supporting files but not creating them.
- Leaving unfinished placeholders in instructions future agents will treat as
  truth.
