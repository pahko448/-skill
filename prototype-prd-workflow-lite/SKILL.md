---
name: prototype-prd-workflow-lite
description: Lightweight staged workflow for product discovery, backend/admin page design, maintainable prototypes, PRD documentation, import-template generation, and review fixes. Use when the user wants a faster, lower-context version of the prototype PRD workflow that loads detailed rules only when needed.
---

# Prototype PRD Workflow Lite

## Purpose

Use this skill as the lightweight version of `prototype-prd-workflow`. Keep the main workflow short, then load detailed references only when the task needs them.

The full version is stricter and self-contained. This lite version is faster for ordinary work and better for small edits.

## Stage Gate

Identify the active stage before acting:

- `Explore`: read source material, screenshots, backend/database, or current files. Do not generate final output yet.
- `Frame`: define page type, role, product goal, workflow, scope, and acceptance criteria. Do not edit yet.
- `Architecture`: define routes, page/module/component ownership, data/config files, states, and boundaries. Do not polish UI yet.
- `Skeleton`: create or adjust page/component skeleton with placeholders only.
- `Prototype`: implement the smallest useful page section or interaction.
- `Verify`: run syntax, browser, or visual checks when feasible.
- `Review Fix`: fix only explicit feedback or screenshot-marked issues.
- `Refactor`: improve maintainability without changing visible behavior.
- `PRD`: document confirmed product logic, fields, interactions, exceptions, fallback, and implementation mapping.
- `Template`: generate import/export templates only after fields are confirmed.

If the user asks to hear the plan first, output the stage, understanding, change boundary, and validation plan, then wait.

## Quick Decision Rules

- For small direct edits: keep the checklist internal and change the smallest owner file.
- For medium/high-risk edits: state what will change, what will not change, risk, and validation before editing.
- For new medium/large pages: use Architecture -> Skeleton -> Prototype. Do not jump directly to a polished page.
- For screenshot feedback: use Review Fix and edit only the marked issue.
- For file splitting, context bloat, or maintainability work: use Refactor, preserve visible behavior.
- For PRD: write only after page logic or structure is confirmed.
- For import templates: first read or confirm backend fields, import logic, sample data, or database structure.

## Reference Loading

Load only the references needed for the current task:

- Backend/admin page UI or interaction: read `references/backend-page-standard.md`.
- Medium/large prototype, file structure, refactor, context compression, ownership, data/UI separation: read `references/maintainable-prototype.md`.
- PRD writing or implementation-facing requirements: read `references/prd-standard.md`.
- Import/export template or MD/image import rules: read `references/import-template-standard.md`.
- Tool/plugin/MCP selection: read `references/tool-strategy.md`.

Do not load every reference by default.

## Default Workflow

Use this flow for medium or large work:

1. Explore.
2. Frame.
3. Architecture.
4. Skeleton.
5. Prototype.
6. Verify.
7. Review Fix.
8. Refactor only when requested or clearly staged.
9. PRD.
10. Template.

## Change Boundary

Before editing mature prototypes, identify:

- Target page.
- Target module.
- Target component/file.
- Data/config affected.
- State affected.
- Files allowed to change.
- Files not allowed to change.
- Shared components/global styles/routes affected or not affected.
- Validation method.

If ownership is unclear, inspect current structure first. Do not create a parallel implementation or modify multiple possible owners at once.

## Failure Avoidance

- Do not rename paths, move files, or change global structure during ordinary feature edits.
- Do not modify shared components or global styles for a local issue unless scope is confirmed.
- Do not combine feature edits and refactors unless explicitly asked.
- Do not rely on compressed conversation context when files or architecture notes can be re-read.
- Do not generate PRDs or templates before structure and fields are confirmed.
- Do not treat old prototypes as truth when backend/database/current files contradict them.
