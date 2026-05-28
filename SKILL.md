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
- `Architecture`: define routes, page ownership, module ownership, component tree, data/config files, states, and implementation boundaries. Do not edit visual UI yet.
- `Skeleton`: create or adjust only the page/component skeleton with placeholder modules. Do not polish visual details yet.
- `Prototype`: modify only the requested prototype surface. Do not write PRD unless asked.
- `Review Fix`: fix only screenshot-marked or explicitly listed issues.
- `Refactor`: improve maintainability without changing visible behavior. Split large files, extract components, move mock data to config, remove duplication, and preserve existing routes, UI, and interactions.
- `PRD`: document only confirmed page structure, fields, interactions, exceptions, fallback rules, and data mapping.
- `Template`: generate import templates only after field structure and parsing rules are confirmed or read from source/backend/database.

If the user asks "explain your thinking first" or "restate before executing", respond with the stage, understanding, intended edits, and validation plan, then wait for confirmation.

Use this full staged flow for medium or large work:

1. Explore: understand source material, existing files, backend/database/screenshots, and current constraints.
2. Frame: define target product structure, user roles, page goals, and business boundaries.
3. Architecture: define routes, modules, components, data/config files, states, and ownership.
4. Skeleton: build or adjust the page skeleton with placeholders before visual polish.
5. Prototype: implement the smallest useful interaction or page section.
6. Verify: run syntax checks, browser checks, or visual checks when possible.
7. Review Fix: fix only explicit review feedback or screenshot-marked issues.
8. Refactor: improve maintainability without changing visible output.
9. PRD: document confirmed product logic and implementation-facing requirements.
10. Template: generate import/export templates only after fields are confirmed.

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

## Maintainable Prototype Architecture

For medium or large prototypes, separate these layers:

1. Route/page layer.
2. Module/component layer.
3. Data/config/mock layer.
4. State/interaction layer.
5. Visual/style layer.

Rules:

- Do not place all page content, mock data, interaction logic, and styles in one large file.
- Each major page section should have a clear module/component owner.
- Business data, recommendation content, report dimensions, enums, option lists, scoring descriptions, and backend-like configuration should live in config/mock files when they may change.
- Components should receive data through props or local data imports whenever feasible.
- Shared components should not be modified for a local page need unless explicitly confirmed.
- Prefer local component-level changes over global changes.
- Do not rename paths, move files, or restructure folders during normal feature edits.
- For mature prototypes, identify the exact target page, module, component, and data/config owner before editing.
- Do not create a new parallel implementation when an existing module already owns the behavior.

## Project Structure Lock

After the project enters `Prototype`, `Review Fix`, or `Refactor` stage, treat the existing file structure as locked unless the user explicitly requests restructuring.

Rules:

- Do not rename existing routes, folders, components, config files, or mock files.
- Do not move files unless the task is explicitly a `Refactor` task.
- Do not modify global styles, shared layout, routing, or shared components unless they are part of the confirmed scope.
- If a change requires touching shared files, explain why before editing.
- Prefer local component-level changes over global changes.
- For review fixes, edit only the component or file that owns the visible issue.
- Do not use a local request as a reason to redesign the whole page, restructure the whole project, or rewrite unrelated modules.

## Module Ownership Map

Before editing a mature prototype, identify the owner of the requested change:

- Page owner: which page or route owns this feature.
- Module owner: which page section owns this UI or behavior.
- Component owner: which component file should be changed.
- Data owner: which mock/config/API mapping file provides the content.
- Style owner: whether styles are local, module-level, shared, or global.
- State owner: whether state belongs to the page, module, store, mock data, or backend response.

If ownership is unclear:

- Inspect the existing structure first.
- Do not create a new parallel implementation.
- Do not duplicate an existing module.
- Do not modify multiple possible owners at once.
- Ask for confirmation only when multiple owners are equally likely and the risk is high.

## Skeleton First Rule

For new medium or large features, do not build the full visual page in one pass.

Use this sequence:

1. Define routes/pages.
2. Define the page/module list.
3. Define the component tree.
4. Define data/config/mock files.
5. Define business states and exception states.
6. Build the page skeleton with placeholder modules.
7. Implement one module at a time.
8. Wire interactions after the layout is stable.
9. Polish visual details last.

Do not mix layout architecture, business logic, mock data, and visual polish in the same edit unless the feature is very small.

When the user asks for a new complex page:

- First provide the proposed page/module/component structure.
- Then implement the skeleton.
- Then implement modules one by one.

## Data And UI Separation

For reusable prototypes:

- Do not hardcode business lists, recommendation items, report dimensions, enum labels, scoring descriptions, option lists, or backend-controlled content directly inside large page components.
- Put mock data, option lists, report content, recommendation content, and backend-like configs into separate files.
- If the content is expected to come from backend configuration, model it as config data even in prototype mode.
- Keep display components as pure as feasible.
- Components should focus on presentation.
- Data files should focus on mock values, field names, option labels, and backend-like configuration.
- Interaction/state logic should be isolated from static display content when feasible.

Suggested file examples:

- `mock/reportData.ts`
- `mock/userData.ts`
- `config/recommendConfig.ts`
- `config/assessmentOptions.ts`
- `constants/status.ts`
- `constants/enums.ts`

## Product-To-Tech Mapping

When product architecture is confirmed, generate or maintain a mapping table between product design and technical implementation.

Use this mapping logic:

| Product Layer | Technical Mapping |
| --- | --- |
| Page | Route / Page file |
| Module | Component |
| Field | API field / mock data key |
| Enum | Constant / backend enum |
| State | UI state / business status |
| Action | Event handler / API operation |
| Config item | Admin config / mock config |
| Exception | Error state / fallback rule |
| Permission | Role guard / visibility rule |

For implementation-oriented tasks, include:

- Route list.
- Component tree.
- Data model.
- State list.
- Config list.
- API/mock boundary.
- Files allowed to change.
- Files not allowed to change.

The goal is to make product architecture reusable for later engineering implementation.

## Change Impact Check

Before editing an existing feature, identify:

1. Target change.
2. Target page.
3. Target module.
4. Target component/file.
5. Data/config affected.
6. Files likely to change.
7. Files that must not change.
8. Shared components affected or not affected.
9. Global styles affected or not affected.
10. Routes affected or not affected.
11. Visual regression risk.
12. Interaction regression risk.
13. Validation method.

For mature prototypes, output or internally confirm:

```md
Will change:
- ...

Will not change:
- ...

Risk:
- ...

Validation:
- ...
```

If the task is a `Review Fix`, only change the marked or explicitly stated issue.

If the task requires touching shared files, explain why before editing.

## Change Boundary Checklist

Before editing an existing prototype, output or internally confirm:

- Target page:
- Target module:
- Target component/file:
- Data/config affected:
- State affected:
- Files allowed to change:
- Files not allowed to change:
- Shared components affected:
- Global styles affected:
- Routes affected:
- Validation method:

Rules:

- If the task is small and low risk, this checklist can be internal.
- If the task is medium or high risk, output the checklist before editing.
- If the user explicitly asks to confirm before execution, output the checklist and wait for confirmation.
- If the user asks for direct execution, keep the checklist internal and proceed with the smallest safe change.

## Context Compression Protection

For large projects or long-running Codex sessions:

- Do not rely on memory of previous code.
- Re-read the relevant architecture notes and target files before editing.
- Prefer editing one page, one module, or one component per task.
- Maintain concise architecture notes when possible:
  - `docs/PROJECT_ARCHITECTURE.md`
  - `docs/ROUTES.md`
  - `docs/MODULE_MAP.md`
  - `docs/DATA_MODEL.md`
  - `docs/CHANGELOG.md`
- Before making changes, compare the current request against the architecture notes.
- If architecture notes conflict with current files, trust the current files and update notes only after confirmation or after the refactor is completed.
- After significant structure changes, update the relevant architecture note.
- Do not load or rewrite unrelated files just to complete a local change.
- If context is compressed or uncertain, inspect current files again instead of guessing.

## Architecture Notes

For projects that may continue across many Codex sessions, create or maintain lightweight architecture notes.

Recommended files:

```text
docs/PROJECT_ARCHITECTURE.md
docs/ROUTES.md
docs/MODULE_MAP.md
docs/DATA_MODEL.md
docs/CHANGELOG.md
```

Suggested purpose:

- `PROJECT_ARCHITECTURE.md`: project goal, product scope, main user roles, high-level modules.
- `ROUTES.md`: page list, route paths, page ownership.
- `MODULE_MAP.md`: page-to-module-to-component mapping.
- `DATA_MODEL.md`: mock data, API-like fields, enums, status values, config items.
- `CHANGELOG.md`: important structural changes and decisions.

Rules:

- Keep these files concise.
- Do not turn them into long PRDs.
- Update them after major architecture, skeleton, or refactor changes.
- Use them as the first context entry when continuing work later.

## PM-Friendly Prototype Workflow

When the user is a product manager using Codex to build prototypes, guide the work in this order:

1. Product goal: clarify what problem the feature solves.
2. User role: clarify who uses it.
3. Entry and exit: clarify where users enter and where they go next.
4. Page structure: define all related pages.
5. Module structure: define sections inside each page.
6. State structure: define normal, empty, loading, error, disabled, permission, and completed states.
7. Data structure: define what fields each module needs and where the data comes from.
8. Config structure: define which content should be backend-configurable.
9. Component structure: map modules to components.
10. Skeleton: build only the page shell first.
11. Module implementation: implement one module at a time.
12. Review fix: fix only explicit feedback.
13. Refactor: split and clean structure without changing visible behavior.
14. PRD: document confirmed product and implementation details.

Do not jump directly from a vague product idea to a full polished page when the feature is medium or large.

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

## Feature Edit vs Refactor

Feature Edit:

- Use when the user asks to add or adjust product behavior, UI content, or interaction.
- Touch the smallest possible owner module.
- Do not restructure the project.

Refactor:

- Use when the user asks to improve maintainability, split large files, reduce context bloat, or clean code structure.
- Do not change visible behavior.
- Do not add features.

Never combine `Feature Edit` and `Refactor` in the same step unless the user explicitly asks for both.

## Fast Prototype Rules

- Prefer the user's named prototype kit or current local prototype.
- Edit the smallest relevant surface.
- Preserve backend enums, fields, option labels, and business wording unless asked to change them.
- Do not invent fields, statuses, or option sets when source/backend/database evidence exists.
- Build the usable workflow first: list, filters, add/edit, preview, enable/disable, validation, and empty states.
- For screenshot feedback, change only the marked or stated issue unless the user authorizes broader cleanup.
- Run syntax checks after JS changes when feasible.

## Review Fix Rules

When the user provides screenshot feedback, marked areas, or explicit review comments:

- Fix only the marked or explicitly described issue.
- Do not redesign surrounding modules.
- Do not change page structure unless the feedback requires it.
- Do not modify unrelated copy, spacing, colors, states, or components.
- If the issue belongs to one component, edit only that component.
- If the issue seems caused by shared styles, explain the risk before changing shared styles.
- Preserve the original visual style unless the feedback asks for a style change.
- After fixing, summarize exactly what changed and what was intentionally left unchanged.

## Refactor Mode

Use `Refactor Mode` only when the user asks to restructure, split files, reduce file size, improve maintainability, reduce context bloat, extract components, or clean up duplicated code.

Rules:

- Preserve current visual output.
- Preserve existing routes.
- Preserve existing interactions.
- Preserve existing data behavior.
- Do not add new features.
- Do not redesign the UI.
- Do not change copywriting unless explicitly requested.
- Split one page at a time.
- Extract one module at a time when risk is high.
- Move mock/config data out of large components when appropriate.
- Keep the refactor behavior-equivalent.
- After refactor, summarize before/after file structure.
- Run syntax checks when feasible.

Refactor output should include:

```md
Before:
- ...

After:
- ...

Changed files:
- ...

Unchanged behavior:
- ...

Validation:
- ...
```

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
### 12. Product-To-Tech Mapping
### 13. Logs, Audit, And Monitoring
### 14. Change Boundary And Non-Goals
```

PRD rules:

- Follow confirmed prototype and real backend fields.
- Do not add modules not present in the confirmed scope unless clearly marked as proposed.
- Record every visible field, button, state, empty state, and error state.
- Include backend exceptions and end-user fallback rules.
- Include permissions, logs, audit, and monitoring when relevant.
- Include route/page, module/component, field/API, enum/constant, state/status, and action/API mapping when the PRD may feed engineering implementation.
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
2. Frame target product structure, roles, goals, and boundaries.
3. Define architecture: routes, modules, components, data/config files, states, and ownership.
4. Build or adjust the skeleton with placeholders.
5. Prototype the smallest useful interaction or page section.
6. Verify with browser and syntax checks when relevant.
7. Apply screenshot feedback narrowly.
8. Refactor only when requested or clearly staged.
9. Write PRD only after confirmation.
10. Generate templates only from confirmed fields.

When the user changes direction mid-task, acknowledge the newer request and reset the active stage.

## Failure Avoidance

- Do not generate PRD while page logic is still being discovered.
- Do not generate import templates before reading real structures when credentials or examples are provided.
- Do not treat old prototypes as truth when backend/database evidence contradicts them.
- Do not expand one module into unrelated pages.
- Do not silently replace user-provided workflow logic with a generic admin pattern.
- Do not apply a feature-specific rule as a universal rule unless abstracted into a generic standard.
- Do not rename paths, move files, or rewrite global structure during ordinary feature edits.
- Do not create parallel implementations when an existing owner module already exists.
- Do not solve a local review fix by changing shared components or global styles unless the risk is explained and the scope is confirmed.
- Do not rely on compressed conversation context when target files or architecture notes can be re-read.
