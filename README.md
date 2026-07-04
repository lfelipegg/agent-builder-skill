# Agent Builder Skill

`agent-builder` is a reusable agent skill for creating, updating, auditing, and
maintaining compact, durable `AGENTS.md` guidance for a repository. It helps an
agent inspect before drafting, ask only for risky unknowns, keep the root
`AGENTS.md` short, route project knowledge to the right source-of-truth
location, create nested `AGENTS.md` files only when local rules justify them,
and recommend focused `/agents` subagents only when the project would benefit
from separate ownership or context management.

The root rule is simple: inspect first, then choose the smallest safe path.

## What This Skill Does

Use this skill when a repository needs:

- a short root `AGENTS.md` that future agents will actually read
- an initial `AGENTS.md` and documentation scaffold for a new project
- durable project commands, guardrails, testing expectations, and response style
- a decision about what belongs in `AGENTS.md` versus specs, plans, context,
  design docs, ADRs, handoffs, task notes, or issue trackers
- a maintenance audit of stale, vague, contradictory, or misplaced agent rules
- nested `AGENTS.md` files for apps, packages, services, or subprojects with
  meaningful local rules
- supporting `docs/agents/*` files for stack, security, database, frontend,
  deployment, testing, review, or documentation details when the root guide
  would become too long
- `/agents` subagent plans for distinct workstreams such as frontend, backend,
  database, CI, docs, architecture, or security review when separate ownership
  or context management is useful

`AGENTS.md` is the quick-start operating guide, not a project notebook. It
should contain durable future-agent rules only.

## Key Principles

- Inspect repository files before drafting or revising instructions.
- Keep the root `AGENTS.md` under 200 lines.
- Do not invent commands, deployment details, git policies, skill availability,
  project structure, or review rules.
- Add commands only when they come from repository files or explicit user
  answers.
- Put product requirements, implementation plans, domain glossaries, design
  briefs, architecture decisions, handoffs, reviews, and task notes in their
  proper source-of-truth locations.
- Add only short pointers in `AGENTS.md` when future agents need to know where
  those documents live.
- Use nested `AGENTS.md` files for local differences only.
- Use `/agents` subagents for context management and ownership boundaries, not
  decoration.
- Add a skill usage map only when the repository or user confirms those skills
  exist.

## Modes

- **Standard Mode:** interview-first for durable instructions, shared teams,
  production systems, high-stakes repos, or projects with multiple workflows.
- **Initial Setup Mode:** create the first compact `AGENTS.md` for a new
  project and optionally recommend or create `CONTEXT.md`, `PRODUCT.md`,
  `DESIGN.md`, and docs folders for specs, plans, decisions, handoffs, and
  reviews.
- **Small Repo Mode:** one compact `AGENTS.md` for tiny repos, solo projects,
  static sites, prototypes, early-stage repos, and small libraries. No
  `docs/agents` split, nested `AGENTS.md`, or `/agents` plan unless needed.
- **Fast Draft With Assumptions:** inspect repo files first, then draft with an
  `Assumptions to confirm` section and risky unknowns marked
  `confirm before use`.
- **Maintenance / Audit Mode:** review an existing `AGENTS.md` for stale
  commands, wrong paths, vague rules, contradictions, misplaced content,
  obsolete guidance, and missing recurring review findings.
- **Nested `AGENTS.md` Mode:** create local instruction files for monorepos or
  subprojects when local commands, boundaries, security rules, testing rules, or
  design constraints differ from the root.

## Content Routing

Before adding anything to `AGENTS.md`, ask whether the instruction is a durable
rule every future agent should follow. If not, route it elsewhere.

| Content | Correct location |
| --- | --- |
| Durable future-agent rule | `AGENTS.md` |
| Detailed agent guidance | `docs/agents/*` |
| Product requirements or feature specs | `docs/specs/*` |
| Implementation plans | `docs/plans/*` |
| Domain language and glossary | `CONTEXT.md` |
| Product intent, audience, positioning | `PRODUCT.md` |
| Visual direction and design principles | `DESIGN.md` or `PRODUCT.md` |
| Architecture decisions and tradeoffs | `docs/decisions/*` |
| Handoff or continuation notes | `docs/handoffs/*` |
| Review records | `docs/reviews/*` |
| Temporary tasks or backlog | issue tracker or `docs/tasks/*` |

## When To Use It

Use `agent-builder` for prompts like:

```text
Create an initial AGENTS.md for this repository.
```

```text
Review our AGENTS.md and make it shorter.
```

```text
Audit AGENTS.md and tell me what should stay, move, update, or be deleted.
```

```text
Move our long agent instructions into docs/agents and propose subagents.
```

```text
Create nested AGENTS.md files for the apps and packages that need local rules.
```

```text
Plan /agents for this project so future coding agents can split work safely.
```

Do not use it as a general coding workflow skill. It is specifically for agent
instructions, repo guidance, documentation routing, and subagent planning.

## How The Workflow Works

1. Inspect the repository, examples, package files, docs, existing agent
   instructions, and any nested instruction files.
2. Identify the request type: initial setup, standard creation/update, small
   repo draft, fast draft, maintenance audit, refactor, nested `AGENTS.md`, or
   `/agents` subagent planning.
3. Choose the smallest safe mode.
4. Ask only for missing facts that are not safely discoverable from repo files.
5. Summarize answers, discovered facts, and assumptions before drafting.
6. Create or update `AGENTS.md` with a hard 200-line maximum.
7. Route misplaced content to the right source-of-truth document.
8. Split detailed guidance into `docs/agents/*` only when the root file would
   become too long or too specialized.
9. Create or recommend nested `AGENTS.md` files only when local rules differ
   meaningfully from the root.
10. Recommend `/agents/orchestrator.md` whenever recommending more than one
    subagent, unless the user declines.
11. Verify line count, links, commands, placeholders, content routing, nested
    file scope, and subagent ownership.

## Expected Output Files

Depending on the repository and the user's choices, the skill may create or
recommend:

- `AGENTS.md`
- nested `{path}/AGENTS.md` files for local rules
- `docs/agents/*.md`
- `agents/orchestrator.md`
- `agents/{subagent}/subagent.md`
- `agents/{subagent}/info/*`
- `agents/{subagent}/scripts/*`

Initial Setup Mode may also recommend or create:

- `CONTEXT.md`
- `PRODUCT.md`
- `DESIGN.md`
- `docs/specs/`
- `docs/plans/`
- `docs/decisions/`
- `docs/handoffs/`
- `docs/reviews/`

Small Repo Mode may produce only `AGENTS.md`.

## Maintenance And Audit Output

For maintenance requests, the skill should classify findings as:

```text
1. Keep as-is
2. Update
3. Move elsewhere
4. Delete
5. Proposed revised AGENTS.md
```

This keeps audits practical and prevents full rewrites when a smaller cleanup is
enough.

## Quality Gates

Before finishing, the agent should confirm:

- `AGENTS.md` is 200 lines or fewer
- linked `docs/agents/*`, nested `AGENTS.md`, and `agents/*` paths exist when
  created or referenced
- commands came from repository files or user answers
- skill names came from repository files or user answers, or are marked
  `confirm before use`
- placeholders are removed or clearly marked as assumptions requiring
  confirmation
- `AGENTS.md` contains durable rules only
- specs, plans, product details, glossaries, design briefs, chat summaries, and
  task notes are routed elsewhere
- nested `AGENTS.md` files contain local differences only
- subagents have clear purpose, inputs, editable areas, forbidden areas,
  verification, and final output format
- the final response lists files created or changed, verification performed, and
  open risks

## Where To Save It

Copy the whole `agent-builder` folder, including `SKILL.md` and `examples/`,
into the skill directory for the agent you want to use.

### Codex

Codex skills are directories containing `SKILL.md` plus optional scripts and
resources. Codex can invoke a skill explicitly from `/skills` or by mentioning
it with `$`, and it can invoke a skill implicitly when the request matches the
skill description.

Recommended local authoring locations:

| Scope | Save as |
| --- | --- |
| Repository root | `$REPO_ROOT/.agents/skills/agent-builder/SKILL.md` |
| Repository local folder | `$CWD/.agents/skills/agent-builder/SKILL.md` |
| Personal user | `$HOME/.agents/skills/agent-builder/SKILL.md` |
| Admin/system | `/etc/codex/skills/agent-builder/SKILL.md` |

Codex also scans `.agents/skills` in parent folders from the current working
directory up to the repository root. For broad distribution beyond one repo or
one user, package skills as a Codex plugin.

### Claude Code

Claude Code skills are directories containing `SKILL.md` plus optional
supporting files. Claude Code can invoke a skill automatically when relevant, or
you can invoke it directly by command name:

```text
/agent-builder
```

Recommended local authoring locations:

| Scope | Save as |
| --- | --- |
| Project | `.claude/skills/agent-builder/SKILL.md` |
| Personal user | `~/.claude/skills/agent-builder/SKILL.md` |
| Nested project area | `<subdir>/.claude/skills/agent-builder/SKILL.md` |
| Plugin | `<plugin>/skills/agent-builder/SKILL.md` |

Claude Code also supports nested `.claude/skills/` directories for monorepos
and lets skills replace same-name custom commands.

## Files In This Skill

- `SKILL.md` - the main skill instructions
- `examples/basic-template.md` - minimal single-file `AGENTS.md` for Small Repo
  Mode, now including content routing and maintenance rules
- `examples/agents-example.md` - compact `AGENTS.md` plus an orchestrator and
  one focused subagent, with clear root/nested/subagent boundaries
- `examples/Very-long-AGENTS.md` - fuller example that still demonstrates a
  bounded root guide under the 200-line cap

For current platform details, see the official docs:

- OpenAI Codex Agent Skills: https://developers.openai.com/codex/skills
- Claude Code skills: https://code.claude.com/docs/en/skills