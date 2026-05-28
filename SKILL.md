---
name: prototype-prd-workflow
description: General workflow standard for product discovery, backend/admin page design, fast prototyping, interaction review, PRD documentation, import-template generation, UI quality checks, and tool selection. Use when the user asks to design or modify pages, build or optimize prototypes, define page architecture, write PRDs, generate import templates, improve output efficiency, or enforce a strict staged collaboration process.
---

# Prototype PRD Workflow

## Purpose

Use this skill to keep product work staged, fast, verifiable, and reusable. The standard is generic: do not bind it to one feature, project, or current request.

Separate discovery, page architecture, prototype edits, review fixes, PRD writing, and template generation. Do not mix stages unless the user explicitly asks.

## Stage Gate

At the start of each non-trivial task, identify the active stage:

- `Exploration`: read existing pages, source maps, screenshots, backend pages, database schemas, logs, or sample data. Do not generate final deliverables yet.
- `Design Frame`: define page type, role, core workflow, information architecture, reference priority, boundaries, and acceptance criteria. Do not edit files yet.
- `Prototype`: modify only the requested prototype surface. Do not write PRD unless asked.
- `Review Fix`: fix only screenshot-marked or explicitly listed issues.
- `PRD`: document only confirmed page structure, fields, interactions, exceptions, fallback rules, and data mapping.
- `Template`: generate import templates only after field structure and parsing rules are confirmed or read from source/backend/database.

If the user asks "explain your thinking first" or "restate before executing", respond with the stage, understanding, intended edits, and validation plan, then wait for confirmation.

## Universal Preflight

Before designing or changing any page, gather or infer:

1. Page type: admin config, list/detail, rule builder, content management, import tool, report page, C-side page, dashboard, or other.
2. User role: operator, admin, content editor, reviewer, end user, etc.
3. Product goal: what decision, workflow, or interaction must be validated.
4. Core workflow: the main user path from entry to completion.
5. Reference priority:
   - Real backend fields/enums/data.
   - User screenshots and annotations.
   - Current prototype style.
   - Old prototype or legacy page as secondary reference only.
6. Scope boundary:
   - Which files or surfaces to edit.
   - Whether to avoid old pages.
   - Whether to avoid real API saves.
   - Whether to produce prototype only, PRD only, or both.
7. Acceptance criteria:
   - Opens successfully.
   - Key interactions work.
   - No garbled text.
   - Syntax check passes when applicable.
   - No unrequested scope expansion.

## Universal Backend Page Design Standard

Apply this to admin, operations, configuration, content management, import, rule, report, permission, and status-management pages.

### Layout

- Use a workbench layout, not a landing-page layout.
- Prefer dense but readable structure: title, filters, action bar, table/list, add/edit modal or drawer, preview panel when needed.
- Keep page sections unframed unless they are repeated items, tools, or modals.
- Avoid decorative heroes, large marketing copy, oversized cards, gradient decoration, and unrelated visual flourishes.
- Use stable dimensions for tables, forms, buttons, tags, toolbars, counters, and fixed-format controls so dynamic content does not shift layout.

### Information Architecture

For most backend pages, use this order:

1. Page title and primary action.
2. Search/filter conditions.
3. Data table, configuration list, or rule list.
4. Row operations: view, edit, delete/disable, preview, copy, sort when relevant.
5. Add/edit modal or drawer.
6. Preview and validation feedback.
7. Empty, loading, disabled, and error states.

For complex configuration forms, split into modules:

- Basic information.
- Source/content selection.
- Rule or condition configuration.
- Display and preview.
- Status, release, or effective-time control.
- Validation result or import result.

### Controls

- Use selects for enums and preserve backend enum values.
- Use switches for enable/disable.
- Use checkboxes for multi-select conditions.
- Use segmented controls or tabs for mutually exclusive modes.
- Use numeric inputs for priority, score ranges, limits, weights, and sort.
- Use drag handles or up/down controls for ordering.
- Use preview buttons for any content that affects end-user display.
- Use icon buttons for common obvious actions; use text for risky or unclear actions.

### Interaction

- Add/edit flows:
  - Use modal for short forms.
  - Use drawer or full modal for multi-section configuration, rule builders, imports, or preview-heavy flows.
- Prototype mode does not require real persistence unless requested.
- Every table/list should support create, edit, delete/disable, preview when relevant.
- Every add/edit modal should define cancel, close, save draft when relevant, save/enable when relevant.
- Rule builders should separate selected conditions from editable condition controls.
- If one field selection determines downstream data, auto-fill derived fields and allow manual adjustment.
- Import tools should include upload, parse preview, module confirmation, validation result, completion, and failure-log access.

### Visual Style

- Use restrained color and clear status tags.
- Use primary color for primary actions and selected states.
- Use success color for enabled/success, warning color for manual confirmation, danger color for destructive/error.
- Keep card radius at 8px or less unless the existing system differs.
- Keep typography compact and readable; avoid hero-scale headings inside admin panels.
- Do not add visible tutorial copy for obvious UI behavior. Prefer labels, hints, and validation messages.

## Universal Exception And Fallback Standard

All backend configuration PRDs and prototypes must consider both backend behavior and end-user behavior. Do not stop at "show an error in admin".

For every exception, define:

1. Exception source.
2. Impact scope.
3. Blocking strategy.
4. Backend/admin presentation.
5. End-user presentation.
6. Fallback or degradation rule.
7. Logging, monitoring, or audit trail.

Use this generic table in PRDs:

```md
| Exception Source | Impact Scope | Blocking Strategy | Backend Presentation | End-User Presentation | Fallback Rule | Logs/Alerts |
| --- | --- | --- | --- | --- | --- | --- |
```

### Exception Sources

Cover these categories when relevant:

- Configuration disabled.
- Configuration expired or not yet effective.
- Referenced object deleted, disabled, archived, offline, or unavailable.
- Enum/source value removed.
- File/image/media unavailable.
- Link or route invalid.
- Rule has no match.
- Rule conflict or priority conflict.
- Required data missing.
- Dirty, duplicate, or inconsistent data.
- API timeout or backend error.
- Import partial success or parse failure.
- Permission or role mismatch.

### Blocking Strategy

Choose one:

- Block save.
- Allow draft but block enable/publish.
- Allow enable but degrade end-user display.
- Do not block; log and monitor.
- Require manual confirmation.

General principles:

- Errors that can be detected in admin should block enable/publish when they would break end-user flows.
- End users should not see backend configuration error details.
- Never let users click dead links, empty actions, or broken payment/submit/report-generation flows.
- Non-core modules such as recommendations, ads, decorative images, and helper copy should degrade or hide instead of blocking the main flow.
- Core actions such as payment, submission, report generation, identity verification, or data writing require stricter blocking or explicit user-facing retry/error states.
- Every degradation must be traceable.

### End-User Fallback Patterns

Use the least disruptive safe fallback:

- Hide the affected module.
- Hide or disable the affected button.
- Show default content.
- Show placeholder image.
- Skip the empty module while preserving page continuity.
- Use default rule/result.
- Ignore unavailable optional conditions.
- Show "try again later" only for core user-facing failures.
- Keep the main flow running when the failed item is optional.

## Tool And Skill Strategy

Use tools deliberately. State tool intent briefly when it affects workflow.

- Use `ui-ux-pro-max` when the task asks for UI/UX quality, page design, backend/admin interaction, visual polish, layout review, or component-level design judgment.
- Use the Browser plugin/browser skill when opening, inspecting, clicking, screenshotting, or verifying a local app/prototype/in-app page.
- Use Pencil MCP tools when the task involves `.pen` files or design canvas edits:
  - `get_editor_state` for file and selection context.
  - `batch_get` for reading components/nodes.
  - `batch_design` for structured design edits.
  - `snapshot_layout` or `get_screenshot` for verification.
- Use Documents plugin only for `.docx`, Word, or document artifacts. For Markdown PRDs, edit Markdown files directly.
- Use Spreadsheets plugin for `.xlsx`, `.xls`, `.csv`, Google-Sheets-style analysis, or Excel import templates.
- When backend truth matters, use this order:
  1. Existing source map, local source, or frontend chunks.
  2. Current backend page through Browser.
  3. Database schema and sample data when credentials are provided.
  4. Old prototype as reference only.

## Fast Prototype Rules

- Prefer the user's named prototype kit or current local prototype.
- Edit the smallest relevant surface.
- Preserve backend enums, fields, option labels, and business wording unless asked to change them.
- Do not invent fields, statuses, or option sets when source/backend/database evidence exists.
- Build the usable workflow first: list, filters, add/edit, preview, enable/disable, validation, and empty states.
- For screenshot feedback, change only the marked or stated issue unless the user authorizes broader cleanup.
- Run syntax checks after JS changes when feasible.

## PRD Mode

Use PRD mode only after the page flow, module structure, or backend fields are confirmed.

Use this structure:

```md
## Page Name

### 1. Page Goal
### 2. Entry And Permissions
### 3. Page Structure
### 4. Module Breakdown
### 5. Fields And Controls
### 6. Enums And States
### 7. Interaction Rules
### 8. Validation Rules
### 9. Exceptions And Backend Handling
### 10. End-User Fallback And Degradation
### 11. Data Mapping
### 12. Logs, Audit, And Monitoring
```

PRD rules:

- Follow confirmed prototype and real backend fields.
- Do not add modules not present in the confirmed scope unless clearly marked as proposed.
- Record every visible field, button, state, empty state, and error state.
- Include backend exceptions and end-user fallback rules.
- Include permissions, logs, audit, and monitoring when relevant.
- For import features, include parsing rules, validation rules, failure logs, retry paths, and partial-success behavior.

## Import Template Mode

Before generating an import template, read or confirm:

- Real backend behavior.
- Current import endpoints or frontend import logic if available.
- Database tables and sample records if credentials are provided.
- Existing import logs and failure reasons if available.
- Required file types and asset handling rules.

Generic import template order:

1. Basic information.
2. Core configuration modules.
3. Content/data rows.
4. Options/enums/scoring/rules when relevant.
5. Display/report/output modules when relevant.
6. Asset/file list when relevant.
7. Validation rules.
8. Failure and fallback rules.

For Markdown imports with images, prefer normal Markdown image paths:

```md
![image alt](./images/example.png)
```

Expected import behavior:

1. Resolve image path relative to the MD file or package root.
2. Upload image to backend/file service.
3. Replace Markdown image syntax with an uploaded URL for rich-text fields.
4. Attach images to the module where they appear.
5. If upload fails, keep text importable and mark the image as needing repair unless the image is required for the core flow.

## Efficiency Protocol

Use this rhythm for multi-step product work:

1. Explore source/backend/database/screenshots.
2. Frame target structure, boundaries, and acceptance criteria.
3. Prototype the smallest useful interaction.
4. Verify with browser and syntax checks when relevant.
5. Apply screenshot feedback narrowly.
6. Write PRD only after confirmation.
7. Generate templates only from confirmed fields.

When the user changes direction mid-task, acknowledge the newer request and reset the active stage.

## Failure Avoidance

- Do not generate PRD while page logic is still being discovered.
- Do not generate import templates before reading real structures when credentials or examples are provided.
- Do not treat old prototypes as truth when backend/database evidence contradicts them.
- Do not expand one module into unrelated pages.
- Do not silently replace user-provided workflow logic with a generic admin pattern.
- Do not apply a feature-specific rule as a universal rule unless abstracted into a generic standard.
