# Prensa FIFA Agent Guide

Use this file as the quick-start operating guide for agents working in this
repository. Keep it short, current, and authoritative. Put expanded conventions
in `docs/AGENT_GUIDE.md`, product requirements in `docs/PRD.md`, and product
design rules in `docs/DESIGN.md`.

## Project Purpose

Prensa FIFA is a Spanish-first SvelteKit website for press and media outlets to
learn about FIFA Fan Fest Monterrey artist press conferences and request
accreditation for one or more conference days.

The public experience has two core surfaces:

- Event intro page: event information, artist schedule, FAQ, and registration
  calls to action.
- Registration form: media outlet details, responsible contact, selected
  conference days, per-day accreditation rosters, and supporting evidence links.

Spanish is the default locale. English routes may live under `/en/` only when
the project keeps English content current.

## Required Stack

Use the existing project stack and the approved product stack:

- SvelteKit
- Svelte 5 Runes Mode
- TypeScript
- Vite
- TailwindCSS
- Paraglide
- GSAP when motion clearly improves hierarchy or transitions
- Supabase with Postgres for registration data
- Vercel as the deployment target

Do not add dependencies without explicit user approval.

## Source Of Truth

Read these before making meaningful changes:

- `docs/PRD.md` for product scope, registration rules, data model direction,
  and acceptance criteria.
- `docs/AGENT_GUIDE.md` for detailed coding, routing, i18n, testing, safety,
  documentation, and git conventions.
- `docs/DESIGN.md` before meaningful UI, styling, motion, or visual changes.
- `docs/CHANGELOG.md` for user-visible and important technical history.
- `package.json` for available scripts. Do not invent scripts.
- `messages/` and `project.inlang/` for localization configuration.

If guidance conflicts, follow this priority:

1. Explicit user request.
2. Current repository behavior and code.
3. `docs/PRD.md`.
4. `AGENTS.md`.
5. Detailed docs under `docs/`.
6. General framework habits.

## Agent Workflow

For non-trivial work:

1. Inspect existing files before deciding what to change.
2. Create or use a dedicated git worktree under `.worktrees/` for the task
   before mutating repo-tracked files.
3. Keep scope tight and avoid unrelated rewrites.
4. Create or update a task plan document under `docs/YYYY-MM-DD-001-task-name/`
   before implementation when the change affects multiple files, UI, routes,
   data structures, docs policy, i18n, or architecture.
5. Implement the smallest coherent change.
6. Add or update focused tests when behavior changes.
7. Run the relevant existing checks from `package.json`.
8. Update task documentation and `docs/CHANGELOG.md`.
9. Summarize changed files, verification, docs, and follow-ups.

## Planning Interrogation

Use `.codex/skills/grill-me` for major plans, architecture choices,
substantial UI or design changes, and explicit user requests to "grill me" or
stress-test a plan or design.

When using it, explore repo-discoverable facts instead of asking the user, ask
one question at a time, include the recommended answer with each question, and
resolve decision dependencies before implementation.

## Non-Negotiable Guardrails

- Use Svelte 5 Runes Mode for Svelte components.
- Use Tailwind utilities and the project theme. Do not create custom CSS
  classes or global styles unless explicitly approved.
- Keep reusable components in `src/lib/components`.
- Keep reusable data, labels, metadata, route labels, event schedules, form
  options, and localized content in `src/lib/data`.
- Keep reusable logic in `src/lib/utils`.
- Keep server-only Supabase writes, validation, and secrets in server routes or
  server-only modules. Never expose service-role keys to client code.
- Add both `es` and `en` values for new localized content when English is
  maintained for the affected route.
- Use Spanish slugs for Spanish routes.
- Work from a dedicated git worktree under `.worktrees/` for implementation
  tasks, including docs, UI, code, tests, data structures, and architecture
  changes.
- Do not change unrelated files.
- Do not delete, overwrite, push, deploy, force-push, or install dependencies
  without permission.
- Do not print or request secrets.

## Verification

Use the scripts that exist in `package.json`:

- `npm run check`
- `npm run lint`
- `npm run test`
- `npm run build`

Choose checks based on the change. If a check cannot run or fails because of
pre-existing unrelated work or environment setup, report that clearly with the
relevant output.

## Final Response

After coding, respond in this shape:

```txt
Done.

Changed:
- ...

Tested:
- ...

Docs:
- ...

Notes:
- ...
```
