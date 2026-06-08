---
name: prototype-delivery-router
description: Use when starting prototype, PRD, flowchart, style replication, C-end/user-app interaction, backend/admin prototype, or Modao import work. This skill routes the task through a short question-driven intake, selects the right template/style/import mode, prevents premature full-batch generation, and coordinates with prototype PRD delivery standards before execution.
metadata:
  short-description: Route prototype, PRD, and Modao delivery work
---

# Prototype Delivery Router

Use this skill before doing prototype/PRD/Modao work. Its job is to choose the right delivery path before creating pages, writing PRDs, or importing anything.

## Hard Rule

Do not start full production immediately. First run the routing intake, state the selected templates and validation method, then wait for confirmation when the task is high-impact, visual, or involves Modao import.

## Trigger Examples

Use this skill when the user asks for:

- C-end/user-app prototype, H5 prototype, AI dialogue flow, inquiry flow, app screen states
- Style replication from a reference page
- PRD annotation for each screen or element-source mapping
- Flowchart or interaction transition map
- Backend/admin prototype or PRD
- Importing HTML/prototype/PRD boards into Modao
- Avoiding repeated style drift, missing interactions, text truncation, or import distortion

## Routing Intake

Ask these questions concisely before execution unless the answer is already obvious from the user request:

1. Delivery priority:
   - Visual fidelity first
   - Modao editability first
   - PRD review clarity first

2. Style source:
   - Use a provided reference page/image
   - Use an existing style pack
   - Create a new style pack from scratch

3. Delivery scope:
   - One-page sample first
   - One functional block first
   - Full batch after sample approval

4. Target output:
   - HTML/local preview only
   - Images + PRD board
   - Modao import
   - Flowchart + PRD

Then output:

```text
I will call:
1. Template: ...
2. Style method: ...
3. PRD format: ...
4. Import mode: ...
5. Validation: ...
```

## Template Selection

Use `references/template-selection.md` to choose templates for user-app, backend/admin, PRD, flowchart, and Modao tasks.

Default choices:

- C-end AI inquiry flow: `user-questioning-flow`
- C-end page annotation PRD: `c-end-prd-annotation`
- Style replication: `style-token-extractor`
- Modao delivery: `modao-import-validator`
- Backend/admin systems: `admin-system-page`

## C-End Prototype Rules

For user-facing app/H5 work, read `references/c-end-prototype-rules.md`.

Core rule: keep the reference style fixed. Only content and state may change between screens unless the user approves a style change.

## PRD Rules

For screen-by-screen PRD, read `references/prd-annotation-rules.md`.

Use numbered format, not tables:

```text
1. Module name
1-1: Element: ...
1-2: Source: ...
1-3: Rule: ...
```

Every meaningful visual or interactive element needs a source and behavior. Do not use generic headings like "operation button"; use the actual button name.

## Modao Routing

For Modao import or HTML-to-Modao work, read `references/modao-import-strategy.md`.

Default decision:

- If visual fidelity matters, use HTTPS image for phone screens and editable PRD/annotations beside it.
- If editability matters, use simple HTML layers and accept visual differences.
- Never treat browser preview as Modao acceptance.

## Stop Conditions

Stop and recalibrate instead of patching when:

- The same issue appears twice, such as missing percent, truncated text, or mismatched labels.
- Modao import differs from browser preview in a new way.
- The user says a flow, module, or button was added without permission.
- A label number does not match the PRD number.

When stopping, summarize:

```text
What failed:
Root cause:
Options:
Recommended next step:
```

## Execution Handoff

After routing, use `prototype-prd-delivery-standard` for the detailed delivery workflow when available.
