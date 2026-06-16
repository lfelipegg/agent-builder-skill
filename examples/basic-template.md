# AGENTS.md

Use this file as the quick-start guide for agents working in this repository.
Keep it short, current, and under 200 lines.

## Project Overview

- Purpose: confirm before use
- Target user: confirm before use
- Stack: inspect repository files first; confirm before use if unclear
- Package manager: inspect lockfiles and manifests first; confirm before use if unclear

## Source Of Truth

- Read `README.md` before making meaningful changes.
- Read package manifests, lockfiles, config files, and existing docs before
  choosing commands or conventions.
- Follow explicit user instructions over this file.

## Commands

Do not invent commands. Add commands here only after finding them in repo files
or receiving them from the user.

- Install: confirm before use
- Dev: confirm before use
- Build: confirm before use
- Test: confirm before use
- Lint: confirm before use

## Agent Workflow

- Inspect existing files before editing.
- Keep changes small and scoped to the request.
- Match existing naming, style, and structure.
- Ask before making risky assumptions.
- Report any command that cannot run and include the reason.

## Guardrails

- Do not install dependencies without permission.
- Do not delete, overwrite, push, deploy, force-push, or run destructive git
  commands without explicit approval.
- Do not print, request, or commit secrets.
- Do not weaken tests, checks, auth, authorization, or CI to make work pass.
- Do not change unrelated files or revert user changes.

## Testing And Verification

- Run the smallest relevant checks that exist in the repository.
- Add or update tests when behavior changes.
- If no test command is confirmed, explain what was inspected manually.

## Small Repo Policy

- Keep guidance in this single `AGENTS.md` unless it would exceed 200 lines.
- Do not add `docs/agents` or `/agents` unless the user asks or distinct
  workstreams make them clearly useful.

## Assumptions to confirm

- Project purpose and target user.
- Canonical install, dev, build, test, and lint commands.
- Whether dependency installs are allowed.
- Whether pushes, deploys, force-pushes, or destructive git commands are ever
  allowed.

## Final Response

Summarize changed files, verification performed, and any remaining risks or
assumptions.
