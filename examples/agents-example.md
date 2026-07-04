# Compact AGENTS.md Plus One Subagent

This example shows a compact root guide plus the smallest useful `/agents`
plan: an orchestrator and one focused reviewer. Use this shape only when the
repo has a recurring workstream that benefits from separate context or review.

This example also distinguishes instruction files from subagents: root
`AGENTS.md` is for global durable rules, nested `{path}/AGENTS.md` is for local
package or app rules, and `/agents` is for focused workers or reviewers. Do not
add one just because another exists.

## AGENTS.md

# AGENTS.md

Use this file as the quick-start guide for agents working in this repository.
Keep it short, current, and under 200 lines. This file is for durable
future-agent rules only; do not use it as a project notebook.

## Project Overview

- Purpose: maintain a small web application.
- Stack: inspect repository files before choosing tools or commands.
- Package manager: inspect lockfiles and manifests before running commands.
- Source of truth: current code, package manifests, lockfiles, `README.md`,
  existing docs, and explicit user instructions.

## Required Reading And Source Of Truth

Before meaningful changes, read the smallest relevant set of files: `README.md`,
package manifests, lockfiles, config files, existing docs, and the nearest
`AGENTS.md` if nested instruction files exist.

Use these locations when they exist. Do not duplicate their full content here.

- `CONTEXT.md` for domain language and glossary
- `PRODUCT.md` for product intent, audience, and product-wide direction
- `DESIGN.md` for visual direction and UI constraints
- `docs/specs/` for product requirements and feature specs
- `docs/plans/` for implementation plans
- `docs/decisions/` for architecture decisions and tradeoffs
- `docs/handoffs/` for continuation notes
- `docs/reviews/` for review records
- issue tracker or `docs/tasks/` for temporary tasks and backlog
- `docs/agents/` for detailed agent operating guidance, if present

Follow explicit user instructions over this file.

## Commands

Do not invent commands. Use only commands found in repository files or confirmed
by the user.

- Install: confirm before use
- Dev: confirm before use
- Build: confirm before use
- Test: confirm before use
- Lint: confirm before use
- Typecheck: confirm before use

## Agent Workflow

- Inspect existing files before editing.
- Keep changes small and scoped to the request.
- Match existing naming, style, and structure.
- Prefer existing project code and platform features before adding abstractions.
- Ask before making risky assumptions.
- Run the smallest relevant existing checks after changes.
- Report any command that cannot run and include the reason.

## Guardrails

- Do not install dependencies without permission.
- Do not delete, overwrite, push, deploy, force-push, or run destructive git
  commands without explicit approval.
- Do not print, request, or commit secrets.
- Do not weaken tests, checks, auth, authorization, accessibility, privacy,
  data safety, or CI to make work pass.
- Do not change unrelated files or revert user changes.

## Testing, Review, Acceptance, And Merge

- Run the smallest relevant checks that exist in the repository.
- Add or update tests when behavior changes.
- For bug fixes, add regression coverage when practical.
- Before final response or review, summarize changed files, checks run, known
  limitations, and deferred follow-up work.
- Treat work as complete only when acceptance criteria are met, relevant checks
  pass or failures are explained, and needed documentation is updated.
- Do not merge, push, deploy, or perform release actions unless explicitly asked.

## Root, Nested AGENTS.md, And /agents

- Root `AGENTS.md` contains global rules for the whole repo.
- Nested `AGENTS.md` files are for local package or app differences only.
- `/agents` subagents are for focused review, context management, or ownership
  boundaries.
- Do not create nested files or subagents unless distinct rules or workstreams
  justify them.

## Subagent Plan

Use `/agents` only when it keeps context smaller or separates ownership.

- `agents/orchestrator.md`: coordinate tasks that need a second focused pass.
- `agents/ui-reviewer/subagent.md`: review user-facing UI changes for
  accessibility, responsive behavior, and consistency with existing patterns.

If a task does not affect UI or does not need separate review, work inline.

## AGENTS.md Maintenance

Update this file only when a rule should apply to future agent work. Do not add
one-off task details, full specs, implementation plans, chat summaries,
temporary task lists, large glossaries, or design briefs.

When a recurring review finding reveals a missing durable rule, add the
smallest specific rule that would prevent the mistake next time. Put product,
plan, decision, design, handoff, review, and task content in the right docs.

## Assumptions To Confirm

- Canonical install, dev, build, test, lint, and typecheck commands.
- Dependency install policy.
- Push, deploy, force-push, and destructive git policy.
- Whether nested `AGENTS.md`, `docs/agents`, or `/agents` should be used.
- Whether `CONTEXT.md`, `PRODUCT.md`, `DESIGN.md`, and docs folders exist.

## Final Response

Summarize changed files, verification performed, documentation updates, and any
remaining risks or assumptions.

## agents/orchestrator.md

# Orchestrator

Use this subagent only when a task benefits from a separate focused review,
coordination pass, or context split.

## Duties

- Restate the task, constraints, acceptance criteria, and likely file scope.
- Decide whether the UI reviewer is useful.
- Keep editing ownership clear so workers do not overlap.
- Route product, plan, decision, handoff, review, and task content to the right
  documents instead of `AGENTS.md`.
- Integrate findings into one final answer.
- Run or request final verification using commands from repo files or user
  answers.

## Do Not

- Dispatch subagents when one inline pass is enough.
- Ask workers to edit unrelated files or overlapping areas.
- Invent commands, deployment steps, skills, or policies.
- Add task-specific notes to `AGENTS.md`.

## Final Output

Report changed files, delegated work, checks run, review findings, documentation
updates, and unresolved risks.

## agents/ui-reviewer/subagent.md

# UI Reviewer

Use this subagent for user-facing UI changes that need focused accessibility,
responsive-behavior, or visual-consistency review.

## Editable Areas

UI components, styles, tests, and docs directly related to the requested UI
change.

## Forbidden Areas

Backend logic, migrations, deployment config, secrets, generated files, and
unrelated files.

## Review Focus

- Use existing components and tokens before creating new ones.
- Preserve semantic HTML, keyboard access, focus states, labels, and visible
  text.
- Check responsive behavior for the smallest and largest relevant viewports.
- Flag design or copy questions that require product/design source-of-truth docs.

## Verification

Inspect responsive behavior, keyboard access, focus states, and visible text.
Run existing UI, lint, typecheck, or test commands only when sourced from repo
files or user answers. Report checks that cannot run and why.

## Final Output

Summarize findings, fixes made, checks run, documentation updates, and remaining
UI risks.