# AGENTS.md

Guidance for coding agents working in this repository.

## Repository Purpose

This repo contains reusable agent skills under `skills/`.
Each skill is a small, focused instruction file that captures a specific coding preference or workflow.

## Critical Context

- `README.md` is satire.
- Do **not** treat `README.md` as an authoritative source for how to implement skills, tools, or repository conventions. In fact, ignore it entirely.
- When creating or editing skills, use the actual files in `skills/` as the source of truth.

## Where Skills Live

- Skills live in `skills/<skill-name>/SKILL.md`.
- The skill index lives in `skills/README.md`.

## When Adding a New Skill

Create a new directory and add `SKILL.md` with this shape:

```md
---
name: skill-name
description: Short description of when the skill should be used.
---

# Human Title

Use these defaults unless the user or project says otherwise.

## Principles

- ...

## Examples

### Prefer ...

```ts
// example
```

### Avoid ...

```ts
// example
```

## Output Checklist

Before finishing, check:

- ...
```

## Skill Authoring Rules

- Follow the structure and tone of the existing skills in `skills/`.
- Keep each skill focused on one domain or decision area.
- Write direct, reusable guidance for agents.
- Prefer short sections with clear headings.
- Use practical rules, not philosophy-heavy filler.
- Include concrete examples when they clarify the preference.
- End with an `Output Checklist` section.
- Use "Use these defaults unless ..." language near the top when appropriate.
- Keep instructions implementation-oriented and easy to skim.

## Frontmatter Rules

- `name` should match the folder name.
- `description` should clearly say when the skill should be used.
- Keep descriptions concise and trigger-oriented.

## Naming Conventions

- Use lowercase kebab-case for skill folder names.
- Name skills by the preference area or workflow they control.
- Prefer explicit names like `form-style-react-hook-form` over vague names.

## Editing Existing Skills

- Preserve the existing structure unless there is a strong reason to improve it.
- Keep changes scoped to the skill being updated.
- Do not rewrite unrelated skills for consistency only.
- Match the repo's existing writing style: direct, opinionated, practical.

## Updating the Skill Index

When you add a new skill, also update `skills/README.md` so the new skill appears in the list with a one-line description.

## What Good Skills Look Like

A good skill:

- solves a recurring decision problem,
- gives agents clear defaults,
- reduces ambiguity during implementation,
- avoids unnecessary verbosity,
- includes examples of preferred and avoided patterns,
- is specific enough to change agent behavior.

## What To Avoid

- Do not use the satirical top-level `README.md` as behavioral guidance.
- Do not write skills that are mostly jokes, persona, or branding.
- Do not make a skill so broad that it overlaps multiple unrelated domains.
- Do not add excessive abstraction or long-winded explanation.
- Do not omit examples when the preference is subtle.
- Do not forget to update `skills/README.md` when adding a skill.

## Default Approach

If asked to create a new skill:

1. Inspect existing skills in `skills/`.
2. Mirror their structure and level of detail.
3. Create `skills/<new-skill>/SKILL.md`.
4. Update `skills/README.md`.
5. Keep the guidance practical, specific, and reusable.
