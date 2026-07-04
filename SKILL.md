---
name: agent-builder
description: Use when creating, updating, auditing, maintaining, or reorganizing AGENTS.md, nested AGENTS.md files, project agent instructions, docs/agents guidance, or /agents subagent plans for a repository
---

# Agent Builder

## Overview

Create, improve, audit, and maintain compact, durable agent instructions for a
repository. The main output is usually a short root `AGENTS.md` that future
agents will actually read. Supporting outputs may include nested `AGENTS.md`
files, `docs/agents/*` guidance, project documentation scaffolds, or focused
`/agents` subagent plans when they are justified.

The root `AGENTS.md` is the quick-start operating guide, not the encyclopedia
or project notebook. It should tell agents how to behave before editing files,
where source-of-truth documents live, which commands prove work is correct, and
which rules must never be ignored.

**Core rule:** Inspect first. For durable or high-stakes instructions, use the
full interview before finalizing. For a fast first draft, draft with a clearly
marked `Assumptions to confirm` section and mark risky unknowns as
`confirm before use`. Never invent commands, deployment details, policies,
skill availability, or project structure.

## When To Use

Use this skill when the user asks to:

- create, improve, review, audit, or rewrite `AGENTS.md`
- create an initial `AGENTS.md` for a new repository
- define durable coding-agent rules for a repository
- decide what belongs in `AGENTS.md` versus specs, plans, context, design docs,
  ADRs, handoffs, tasks, or issue trackers
- create nested `AGENTS.md` files for apps, packages, or subprojects
- organize detailed agent guidance under `docs/agents`
- migrate long or noisy agent instructions into a shorter root guide
- plan `/agents` subagents, orchestrators, reviewers, or task agents
- audit stale commands, wrong paths, vague rules, contradictions, or misplaced
  project knowledge in agent instructions

Do not use it as a general coding workflow skill. It is specifically for agent
instructions, repo guidance, documentation routing, and subagent planning.

## Non-Negotiables

- `AGENTS.md` must be at most 200 lines.
- Aim for 80-150 lines for small repos. Treat 200 lines as the hard stop unless
  the user explicitly chooses a different cap.
- `AGENTS.md` contains durable future-agent rules only.
- Do not put one-off task details, full product requirements, implementation
  plans, chat summaries, temporary TODOs, large glossaries, or design briefs in
  `AGENTS.md`.
- Route non-agent content to the correct document and leave only a short pointer
  in `AGENTS.md` when future agents need it.
- If detailed agent rules do not fit, split them into `docs/agents/*` and link
  from `AGENTS.md`; skip the split for small repos when one compact root file
  is enough.
- Ask only for facts that are not safely discoverable from repository files.
- Recommend `/agents/orchestrator.md` whenever recommending more than one
  subagent.
- Recommend focused subagents only when the project has distinct workstreams,
  ownership boundaries, or context-management needs.
- Use nested `AGENTS.md` files only when local repo areas have meaningful local
  rules. Nested files should not repeat the root unless repetition prevents a
  serious mistake.
- Do not copy full external skill instructions into `AGENTS.md`. Add only a
  compact skill usage map when the repo or user confirms those skills exist.
- Review changes to `AGENTS.md` like code: the new rule must be durable,
  specific, correctly placed, non-conflicting, and short.
- Preserve user preferences when they conflict with defaults.

## Quick Workflow

1. Inspect the repository, examples, package files, docs, existing agent
   instructions, and any nested instruction files.
2. Identify the request type: initial setup, standard creation/update, small
   repo draft, fast draft, maintenance audit, refactor, nested `AGENTS.md`, or
   `/agents` subagent planning.
3. Choose the smallest safe mode.
4. Ask only the essential questions for that mode. Ask one at a time for
   ambiguous or high-impact choices; group low-risk questions when the user
   asks for speed.
5. Summarize the answers, discovered facts, and assumptions before writing.
6. Draft or revise `AGENTS.md` with a 200-line budget.
7. Route misplaced content to the correct project document.
8. Split detailed agent guidance into `docs/agents/*` only when needed.
9. Create or recommend nested `AGENTS.md` files only for local rules.
10. Propose `/agents` subagents only when they are justified.
11. Verify line count, links, commands, placeholders, content routing, nested
    file scope, and subagent ownership.

## Modes

### Standard Mode

Use for durable instructions, high-stakes repos, shared teams, production
systems, or repositories with multiple stacks or workflows. Inspect the repo,
run the full interview for missing facts, summarize answers and assumptions,
then draft or revise.

Standard Mode should produce a compact root `AGENTS.md` and may recommend:

- `docs/agents/*` for detailed agent guidance
- nested `AGENTS.md` files for local app/package rules
- `/agents` subagents for distinct workstreams
- project documentation locations when missing or unclear

### Initial Setup Mode

Use when a repository is brand new or the user asks to set up agent guidance
before serious project setup.

Create the smallest useful first version. Prefer stubs and directories over
invented details. Define where future information should live instead of filling
`AGENTS.md` with unknowns.

Recommended initial outputs, when useful:

```text
AGENTS.md
CONTEXT.md              # optional stub for domain language
PRODUCT.md              # optional stub for product intent and audience
DESIGN.md               # optional stub when the project has UI
docs/specs/
docs/plans/
docs/decisions/
docs/handoffs/
docs/reviews/
```

The first `AGENTS.md` should usually define:

- workflow order
- required reading before coding
- source-of-truth document locations
- setup, dev, and quality command placeholders or confirmed commands
- implementation rules
- testing rules
- UI/design rules when applicable
- security and privacy rules
- review, acceptance, and merge rules
- optional skill usage map
- maintenance rules for `AGENTS.md` itself

Do not implement product features during Initial Setup Mode.

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
rules, git policies, documentation structures, skill availability, or review
rules. If a command, path, tool, skill, or policy is not in repo files or user
answers, either omit it or mark it as an assumption to confirm.

### Maintenance / Audit Mode

Use when the user asks to audit, clean up, improve, maintain, shorten, or
review an existing `AGENTS.md`.

Check for:

- stale or invented commands
- wrong paths or broken links
- vague rules that are not executable or checkable
- contradictions
- duplicated root and nested rules
- obsolete framework, package, or deployment guidance
- task-specific content that should move elsewhere
- specs, plans, product details, glossaries, design briefs, chat summaries, or
  TODOs stored in `AGENTS.md`
- missing durable rules from repeated review findings
- sections too long for future agents to follow

Default audit output:

```text
1. Keep as-is
2. Update
3. Move elsewhere
4. Delete
5. Proposed revised AGENTS.md
```

Do not rewrite unrelated project documents unless the user asks.

### Nested AGENTS.md Mode

Use when a monorepo, app, package, service, or subdirectory has local rules that
meaningfully differ from the root.

Root `AGENTS.md` should cover global behavior:

- global workflow
- source-of-truth documents
- shared quality commands
- branch, review, acceptance, and merge rules
- global security expectations
- global documentation rules

Nested `AGENTS.md` files should cover local differences only:

- local commands
- local architecture boundaries
- local testing rules
- local security constraints
- local design or package conventions
- local forbidden imports or editable areas

Keep nested files short. Do not repeat the root unless repetition prevents a
serious mistake.

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
4. **Source of truth:** Where do product requirements, implementation plans,
   domain context, design direction, ADRs, handoffs, reviews, and task records
   live?
5. **Guardrails:** What should agents never do automatically?
6. **Dependencies:** May agents install packages? Recommended default: no, ask
   first.
7. **Git and worktrees:** Should agents use git worktrees, and what path should
   they use? Recommended default: yes for non-trivial implementation, under
   `.worktrees/`.
8. **Documentation policy:** Should every task be documented, or only
   non-trivial tasks? Recommended default: non-trivial tasks. If enabled, use
   `docs/tasks/{ascending-number}-{iso-timestamp}-{task-title}/summary.md` and
   `docs/tasks/{ascending-number}-{iso-timestamp}-{task-title}/next-steps.md`.
9. **Review and acceptance:** What summary, verification, review, acceptance,
   merge, CI, rollout, and rollback expectations should future agents follow?
10. **Nested instructions:** Do any apps, packages, services, or directories
    need local `AGENTS.md` files?
11. **Skills:** Are project-specific or assistant-specific skills available?
    If yes, when should each be used? Do not invent installed skills.
12. **Subagents:** Should the project use `/agents`? Recommend based on the
    answers and explain which subagents are useful.
13. **Final response style:** How should agents summarize changes, tests, docs,
    risks, and follow-ups?

### Guardrail Examples

Offer examples and ask the user to choose or edit them:

- Do not install dependencies without permission.
- Do not delete, overwrite, push, deploy, force-push, or run destructive git
  commands without explicit approval.
- Do not print, request, or commit secrets.
- Do not weaken tests, type checks, auth, authorization, billing, migrations,
  accessibility, privacy, data safety, or CI to make work pass.
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
6. source-of-truth docs, if the repo already has them
```

If the user cannot answer, draft an `Assumptions to confirm` section and mark
every risky unknown as `confirm before use`.

## AGENTS.md Content Routing

Before adding anything to `AGENTS.md`, ask:

```text
Is this a durable rule every future agent should follow?
```

If yes, it may belong in `AGENTS.md`. If no, put it somewhere else.

### What Belongs In AGENTS.md

Good `AGENTS.md` content is durable, specific, and actionable:

- workflow rules future agents must follow
- required reading before coding
- source-of-truth document locations
- commands confirmed from repo files or user answers
- implementation constraints
- testing and verification expectations
- concrete security, privacy, accessibility, and data-safety rules
- review, acceptance, and merge gates
- short pointers to deeper docs
- maintenance rules for `AGENTS.md` itself

### What Does Not Belong In AGENTS.md

Do not add:

- one-off task notes
- current task progress
- full product requirements
- feature plans
- task backlogs
- full domain glossaries
- design briefs
- chat summaries
- temporary TODOs
- unresolved brainstorms
- long explanations of decisions
- full external skill instructions

### Right Document Routing

Use this routing table when refactoring or drafting:

| Content                                | Correct location                |
| -------------------------------------- | ------------------------------- |
| Durable future-agent rule              | `AGENTS.md`                     |
| Detailed agent guidance                | `docs/agents/*`                 |
| Product requirements or feature specs  | `docs/specs/*`                  |
| Implementation plans                   | `docs/plans/*`                  |
| Domain language and glossary           | `CONTEXT.md`                    |
| Product intent, audience, positioning  | `PRODUCT.md`                    |
| Visual direction and design principles | `DESIGN.md` or `PRODUCT.md`     |
| Architecture decisions and tradeoffs   | `docs/decisions/*`              |
| Handoff or continuation notes          | `docs/handoffs/*`               |
| Review records                         | `docs/reviews/*`                |
| Temporary tasks or backlog             | issue tracker or `docs/tasks/*` |

`AGENTS.md` may point to these locations. It should not duplicate their full
content.

## When To Update AGENTS.md

Update `AGENTS.md` only when a rule becomes reusable.

Good triggers:

- a review finds the same mistake more than once
- a required command changes
- the project adopts a new framework convention
- architecture boundaries become clear
- a design-system rule becomes mandatory
- security, privacy, accessibility, or data-safety rules become more specific
- CI, release, or verification expectations change
- the repo becomes a monorepo and needs nested instructions
- a tool or package introduces a local workflow rule

Bad triggers:

- one task needs special handling
- a single bug required a one-off fix
- a feature plan is still in progress
- an idea is being discussed but not decided
- a long chat summary needs to be saved
- the product spec changed
- the user wants to store temporary TODOs

Put bad-trigger content in the current task, plan, spec, handoff, ADR, or issue
tracker instead.

### Maintenance Loop

Use this loop whenever changing `AGENTS.md`:

1. Observe the issue or missing instruction.
2. Decide whether it will matter for future work.
3. Choose the right document.
4. Add the smallest useful rule.
5. Verify it does not conflict with existing rules.
6. Review the change like code.
7. Remove or revise stale rules later.

## AGENTS.md Shape

Use `examples/basic-template.md` for a small project shape and
`examples/agents-example.md` when a compact `/agents` plan is justified. Use
`examples/Very-long-AGENTS.md` as an example of a fuller but still compact
guide.

Treat examples as structure only. Do not copy template placeholders, unavailable
skills, unknown commands, or external links into a final `AGENTS.md`.

Recommended sections:

- Purpose or Project Overview
- Workflow
- Required Reading
- Source Of Truth
- Commands
- Agent Workflow or Implementation Rules
- Non-Negotiable Guardrails
- Worktrees And Git
- Documentation Policy
- Testing And Verification
- Security, Privacy, and Accessibility
- Review Rules
- Acceptance Rules
- Merge Rules
- AGENTS.md Maintenance Rules
- Nested AGENTS.md Rules, when applicable
- Skill Usage Map, when confirmed
- Subagent Plan, when justified
- Final Response

### Line Budget

Keep `AGENTS.md` readable:

| Section                                                  | Target   |
| -------------------------------------------------------- | -------- |
| Purpose, workflow, source of truth                       | 30 lines |
| Commands                                                 | 20 lines |
| Implementation workflow and guardrails                   | 45 lines |
| Stack, architecture, security, and UI conventions        | 45 lines |
| Testing, docs, review, accept, merge                     | 40 lines |
| Maintenance rules, nested instructions, subagent summary | 20 lines |

If the draft approaches 180 lines, stop adding detail and split files.

### Rule Quality

Rules should be specific, actionable, and checkable.

Avoid vague rules:

```text
Write good code.
Be secure.
Make the UI nice.
Document things when useful.
```

Prefer operational rules:

```text
Do not add dependencies without checking standard library, platform APIs,
existing project code, and already-installed dependencies first.
```

```text
Authorization must be enforced server-side. Client-side checks are UX only.
```

```text
Before UI work, read `PRODUCT.md` and `DESIGN.md`; use existing tokens and
components before creating new ones.
```

## Splitting Details

Move expanded agent guidance into `docs/agents/` when:

- `AGENTS.md` would exceed 200 lines
- a topic has many stack-specific rules
- guidance is useful but not needed on every task
- subagents need deeper background
- recurring review findings need detail beyond a short root rule

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
- `docs/agents/review.md`
- `docs/agents/subagents.md`

In `AGENTS.md`, link to the detailed file and keep only the rule that decides
when to read it.

Do not use `docs/agents/*` as a substitute for product specs, implementation
plans, ADRs, handoffs, reviews, or domain glossaries. Route those to the right
project documents.

## Source-Of-Truth Documents

When a project has or wants a broader documentation system, prefer these
locations:

```text
CONTEXT.md          domain language and glossary
PRODUCT.md          product intent, audience, positioning, product-wide rules
DESIGN.md           visual direction, design principles, UI constraints
docs/specs/         product requirements and feature specs
docs/plans/         implementation plans
docs/decisions/     architecture decision records and tradeoffs
docs/handoffs/      continuation notes
docs/reviews/       review records
docs/tasks/         task records, when the project uses repo task docs
docs/agents/        detailed agent operating guidance
```

Only create these files or folders when the user asks, the repo already follows
this structure, or Initial Setup Mode makes them useful. Otherwise, recommend
rather than force the scaffold.

## Review, Acceptance, And Merge Gates

When useful for the repository, include compact workflow gates in `AGENTS.md`.

### Review Rules

Before requesting review, agents should provide:

- summary of changes
- files changed
- tests or checks run
- known limitations
- deferred follow-up work

During review, check:

- spec, issue, or task alignment
- implementation simplicity
- tests and verification
- security and data safety
- accessibility
- UI/design quality, when applicable
- documentation updates

### Acceptance Rules

A task can be accepted only when:

- acceptance criteria are met
- relevant checks pass or failures are explained
- review findings are resolved or explicitly deferred
- documentation is updated when behavior, setup, commands, architecture, or
  product decisions changed
- no unrelated changes are included

### Merge Rules

Do not merge until:

- the task is accepted
- CI or local equivalent checks pass
- migrations, rollout risks, or data risks are documented
- rollback notes exist for risky changes
- `AGENTS.md` changes, if any, were reviewed as durable instructions

Keep these gates short. Put detailed review records in `docs/reviews/*` and
handoffs in `docs/handoffs/*`.

## Skill Usage Map

Add a skill usage map only when the repo or user confirms specific skills are
available. Do not invent installed skills and do not copy full skill manuals
into `AGENTS.md`.

A good skill map says when to use each skill:

```text
- Use requirements-grilling skills when requirements are unclear.
- Use PRD/spec skills to convert clarified requirements into specs.
- Use planning skills before non-trivial implementation.
- Use TDD/debugging skills for behavior changes and bug fixes.
- Use UI/design skills for user-facing work.
- Use review/audit skills before acceptance or merge.
```

If no skills are confirmed, omit the section or add:

```text
Project-specific skill usage: confirm before use.
```

## Root vs Nested AGENTS.md vs /agents Subagents

These are different tools.

```text
AGENTS.md                  root instructions for all agents
apps/web/AGENTS.md         local instructions for one app or package
packages/ui/AGENTS.md      local instructions for one package
agents/orchestrator.md     subagent coordination prompt
agents/ui-reviewer/...     focused subagent instructions and support files
```

Use root and nested `AGENTS.md` files for instruction discovery by location.
Use `/agents` subagents for context management, focused review, or separate
workstream ownership.

Do not create `/agents` just because a nested `AGENTS.md` exists. Do not create
nested `AGENTS.md` just because a subagent exists.

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

Do not add task content directly to `AGENTS.md`; add only the task-documentation
rule and location.

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

| Project signal                              | Suggested subagent          |
| ------------------------------------------- | --------------------------- |
| UI framework, design system, accessibility  | `frontend` or `ui-reviewer` |
| API, services, auth, queues                 | `backend`                   |
| Database, Prisma, Supabase, migrations, RLS | `database`                  |
| CI, deployment, build failures              | `ci`                        |
| Docs-heavy process or task logs             | `docs`                      |
| Security, billing, secrets, payments        | `security-reviewer`         |
| Large refactors or architecture decisions   | `architect`                 |

For each recommended subagent, define:

- purpose
- when to use
- inputs it needs
- files it may edit
- files it must not edit
- verification it should run
- final output format

## Output Package

When creating files, propose or create only what the repository needs.

Common outputs:

- `AGENTS.md`
- nested `{path}/AGENTS.md` files for local rules
- `docs/agents/*.md` for detailed agent guidance when needed
- `agents/orchestrator.md` when recommending more than one subagent or when the
  project needs coordination
- `agents/{subagent}/subagent.md` for each focused subagent
- `agents/{subagent}/info/*` for durable context
- `agents/{subagent}/scripts/*` only for reusable tooling

Optional Initial Setup Mode outputs:

- `CONTEXT.md`
- `PRODUCT.md`
- `DESIGN.md`
- `docs/specs/`
- `docs/plans/`
- `docs/decisions/`
- `docs/handoffs/`
- `docs/reviews/`

End with a short rationale explaining why each file exists and what was not
created because it was unnecessary.

## Quality Gates

Before finishing:

- Run `wc -l AGENTS.md` if the file exists.
- Confirm `AGENTS.md` is 200 lines or fewer.
- Search for leftover placeholders such as `[Name]`, `TODO`, and `TBD`.
- Check every linked `docs/agents/*`, nested `AGENTS.md`, or `agents/*` path
  exists if you created links.
- Confirm commands came from repo files or user answers.
- Confirm skill names came from repo files or user answers, or are marked
  `confirm before use`.
- Remove placeholders, or mark them as assumptions requiring confirmation.
- Confirm `AGENTS.md` contains durable rules only.
- Confirm specs, plans, product details, glossaries, design briefs, chat
  summaries, and task notes are routed elsewhere.
- Confirm nested `AGENTS.md` files contain local differences only.
- Confirm subagents have non-overlapping ownership where they may edit files.
- Confirm review, acceptance, merge, and maintenance rules are concise and
  checkable when included.
- Confirm the final response lists files created or changed, verification, and
  open risks.

Useful checks:

```bash
wc -l AGENTS.md
rg -n "\[[^]]+\]|TODO|TBD" AGENTS.md docs/agents agents
rg -n "docs/agents|agents/|AGENTS.md" AGENTS.md
```

For each command listed in `AGENTS.md`, confirm it appears in repo files or the
user's answers.

For audits, also check:

```bash
find . -name AGENTS.md -print
rg -n "spec|plan|TODO|handoff|glossary|brainstorm|chat summary" AGENTS.md
```

Use audit search results as signals, not automatic proof. Decide whether each
item is durable agent guidance or belongs elsewhere.

## Red Flags

Stop and correct course if you think:

- "The user asked for speed, so I can skip inspection."
- "The user asked for speed, so I can invent commands."
- "One long AGENTS.md is simpler."
- "Every repo should have subagents."
- "Every monorepo folder needs a nested AGENTS.md."
- "I can infer commands from the stack."
- "I should include every possible rule in the root file."
- "AGENTS.md is the right place for this feature plan."
- "The product spec changed, so AGENTS.md must change too."
- "A one-off bug fix should become a permanent agent rule."
- "Copying full skill instructions into AGENTS.md will help future agents."
- "Nested files should repeat the root file so they are self-contained."
- "The user can clean up the structure later."

## Rationalizations And Counters

| Rationalization                                          | Counter                                                                                        |
| -------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| "The user is in a hurry."                                | Inspect first, ask only risky unknowns, and mark assumptions clearly.                          |
| "A comprehensive file prevents questions."               | Overlong instructions are skipped. Keep root under 200 lines and split details.                |
| "This belongs in AGENTS.md because agents need context." | Agents need pointers to source-of-truth documents, not duplicated specs or notes.              |
| "Subagents sound fancy."                                 | They are a context-management tool. Recommend them only when workstreams are distinct.         |
| "The stack tells me the commands."                       | Commands belong to the repo and user, not the framework. Read or ask.                          |
| "Guardrails are obvious."                                | They differ by project. Ask about installs, deploys, pushes, secrets, and destructive actions. |
| "Nested AGENTS.md files should be complete."             | Root has global rules. Nested files should contain local differences only.                     |
| "A review finding means AGENTS.md needs an update."      | Update only when the finding reveals a durable recurring rule.                                 |

## Common Mistakes

- Drafting before inspecting or interviewing.
- Treating examples as universal instead of adapting them.
- Encoding volatile details in `AGENTS.md` instead of source-of-truth docs.
- Putting product requirements, plans, task notes, chat summaries, glossaries,
  or design briefs in `AGENTS.md`.
- Creating subagents without clear inputs, ownership, and verification.
- Creating nested `AGENTS.md` files that duplicate the root.
- Linking to supporting files but not creating them.
- Leaving unfinished placeholders in instructions future agents will treat as
  truth.
- Adding vague rules that cannot be executed or checked.
- Never removing stale commands or obsolete architecture rules.
- Updating `AGENTS.md` for one-off issues instead of recurring patterns.
