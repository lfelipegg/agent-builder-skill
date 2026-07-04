# AGENTS.md

Use this file as the quick-start guide for agents working in this repository.
Keep it short, current, and under 200 lines. This file is for durable future-agent
rules only; do not use it as a project notebook.

## Project Overview

- Purpose: confirm before use
- Target user: confirm before use
- Stack: inspect repository files first; confirm before use if unclear
- Package manager: inspect lockfiles and manifests first; confirm before use if unclear

## Required Reading

Before meaningful changes, read the smallest relevant set of files:

- `README.md` for project setup and human-facing context, if it exists.
- Package manifests, lockfiles, and config files before choosing commands.
- Existing docs before changing behavior, architecture, setup, UI, or tests.
- The nearest `AGENTS.md` if nested instruction files exist.

Follow explicit user instructions over this file.

## Source Of Truth

Use current repository files and explicit user instructions as source of truth.
When these documents exist, use them instead of duplicating their content here:

- `CONTEXT.md` for domain language and glossary
- `PRODUCT.md` for product intent, audience, and product-wide direction
- `DESIGN.md` for visual direction and UI constraints
- `docs/specs/` for product requirements and feature specs
- `docs/plans/` for implementation plans
- `docs/decisions/` for architecture decisions and tradeoffs
- `docs/handoffs/` for continuation notes
- `docs/reviews/` for review records
- issue tracker or `docs/tasks/` for temporary tasks and backlog

## Commands

Do not invent commands. Add commands here only after finding them in repo files
or receiving them from the user.

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
- Prefer existing project code and platform features before adding new abstractions.
- Ask before making risky assumptions.
- Report any command that cannot run and include the reason.

## Guardrails

- Do not install dependencies without permission.
- Do not delete, overwrite, push, deploy, force-push, or run destructive git
  commands without explicit approval.
- Do not print, request, or commit secrets.
- Do not weaken tests, checks, auth, authorization, accessibility, privacy,
  data safety, or CI to make work pass.
- Do not change unrelated files or revert user changes.

## Testing And Verification

- Run the smallest relevant checks that exist in the repository.
- Add or update tests when behavior changes.
- For bug fixes, add regression coverage when practical.
- If no test command is confirmed, explain what was inspected manually.
- If checks fail for unrelated or environmental reasons, report the failure and
  relevant output.

## Review, Acceptance, And Merge

Before final response or review, summarize:

- changed files
- checks run
- known limitations
- deferred follow-up work

Treat work as complete only when acceptance criteria are met, relevant checks
pass or failures are explained, and documentation is updated when behavior,
setup, commands, architecture, or product decisions changed.

Do not merge, push, deploy, or perform release actions unless explicitly asked.

## Small Repo Policy

- Keep guidance in this single `AGENTS.md` unless it would exceed 200 lines.
- Do not add `docs/agents`, nested `AGENTS.md`, or `/agents` unless the user asks
  or distinct workstreams make them clearly useful.
- If this file grows too long, move detailed guidance to the correct document and
  leave a short pointer here.

## AGENTS.md Maintenance

Update this file only when a rule should apply to future agent work.

Do not add:

- one-off task details
- full specs or product requirements
- implementation plans
- chat summaries
- temporary task lists
- large glossaries
- design briefs

When a recurring review finding reveals a missing durable rule, add the smallest
specific rule that would prevent the mistake next time.

## Assumptions To Confirm

- Project purpose and target user.
- Canonical install, dev, build, test, lint, and typecheck commands.
- Whether dependency installs are allowed.
- Whether pushes, deploys, force-pushes, or destructive git commands are ever
  allowed.
- Whether source-of-truth docs, task docs, nested `AGENTS.md`, or `/agents`
  should be used in this repository.

## Final Response

Summarize changed files, verification performed, documentation updates, and any
remaining risks or assumptions.