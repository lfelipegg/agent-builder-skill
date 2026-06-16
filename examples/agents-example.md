# Compact AGENTS.md Plus One Subagent

This example shows a compact root guide plus the smallest useful `/agents`
plan: an orchestrator and one focused reviewer. Use this shape only when the
repo has a real recurring workstream that benefits from separate context.

## AGENTS.md

# AGENTS.md

Use this file as the quick-start guide for agents working in this repository.
Keep it short, current, and under 200 lines.

## Project Overview

- Purpose: maintain a small web application.
- Stack: inspect repository files before choosing tools or commands.
- Source of truth: current code, package manifests, lockfiles, `README.md`, and
  explicit user instructions.

## Commands

Do not invent commands. Use only commands found in repository files or confirmed
by the user.

- Install: confirm before use
- Dev: confirm before use
- Build: confirm before use
- Test: confirm before use
- Lint: confirm before use

## Agent Workflow

- Inspect existing files before editing.
- Keep changes small and scoped to the request.
- Match existing patterns.
- Ask before dependency installs, deploys, pushes, force-pushes, destructive git
  commands, schema changes, or paid-service changes.
- Run the smallest relevant existing checks after changes.

## Subagent Plan

Use `/agents` only when it keeps context smaller or separates ownership.

- `agents/orchestrator.md`: coordinate tasks that need a second focused pass.
- `agents/ui-reviewer/subagent.md`: review user-facing UI changes for
  accessibility, responsive behavior, and consistency with existing patterns.

If a task does not affect UI or does not need separate review, work inline.

## Assumptions to confirm

- Canonical commands.
- Dependency install policy.
- Push, deploy, force-push, and destructive git policy.

## Final Response

Summarize changed files, verification performed, and remaining risks.

## agents/orchestrator.md

# Orchestrator

Use this subagent only when a task benefits from a separate focused review.

## Duties

- Restate the task, constraints, and files likely to change.
- Decide whether the UI reviewer is useful.
- Keep editing ownership clear so workers do not overlap.
- Integrate findings into one final answer.
- Run or request final verification using commands from repo files or user
  answers.

## Do Not

- Dispatch subagents when one inline pass is enough.
- Ask workers to edit unrelated files.
- Invent commands or deployment steps.

## Final Output

Report changed files, checks run, review findings, and unresolved risks.

## agents/ui-reviewer/subagent.md

# UI Reviewer

Use this subagent for user-facing UI changes that need a focused accessibility
or responsive-behavior review.

## Inputs

- User request and constraints.
- Changed UI files or proposed patch.
- Relevant design or style docs if they exist.

## Editable Areas

- UI components, styles, tests, and docs directly related to the requested UI
  change.

## Forbidden Areas

- Backend logic, migrations, deployment config, secrets, and unrelated files.

## Verification

- Inspect responsive behavior, keyboard access, focus states, and visible text.
- Run existing UI, lint, or test commands only when sourced from repo files or
  user answers.

## Final Output

Summarize findings, fixes made, checks run, and any remaining UI risks.
