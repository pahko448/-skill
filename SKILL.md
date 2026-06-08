---
name: prototype-prd-workflow
description: General workflow standard for product discovery, backend/admin page design, fast prototyping, interaction review, PRD documentation, import-template generation, UI quality checks, and tool selection. Use when the user asks to design or modify pages, build or optimize prototypes, define page architecture, write PRDs, generate import templates, improve output efficiency, or enforce a strict staged collaboration process.
---

# Prototype PRD Workflow

## Purpose

Use this skill to keep product work staged, fast, verifiable, and reusable. The standard is generic: do not bind it to one feature, project, or current request.

Separate discovery, page architecture, prototype edits, review fixes, PRD writing, and template generation. Do not mix stages unless the user explicitly asks.

## Intake Routing

Before prototype, PRD, flowchart, style replication, C-end/user-app, backend/admin, Modao, or template work, run Intake Routing before creating artifacts.

Intake Routing decides three things:

1. Task scale: `Lite`, `Standard`, or `Full`.
2. Delivery route: priority, style source, scope, output, and validation.
3. Reference loading: which skill or reference is needed.

### Task Scale Check

Use the lightest safe mode:

1. `Lite`
   - Use for copy, one button/field/tag, screenshot review fixes, one confirmed field, or local style tweaks.
   - Must not change business flow, backend-user linkage, external systems, imports, sync, links, QR codes, permissions, or state transitions.
   - Keep the check internal unless the user asks for confirmation.
2. `Standard`
   - Use for one backend module, one page, one modal/drawer/flow, existing workflow adjustment, backend config affecting user display, states, permissions, exceptions, fallback, or imports without complex multi-system linkage.
   - Briefly state goal, core object, source of truth, interaction model, scope, and validation when risk is meaningful.
3. `Full`
   - Use for long-running projects, multi-page flows, backend + user-side chains, external systems, live codes, links, QR codes, sync, import, permissions, state transitions, prototype + PRD + Modao handoff, or architecture-risky user proposals.
   - Must perform solution architecture, challenge-risk check, ownership/source-of-truth check, failure-first design, interaction model selection, and PRD system mapping as needed.

### Delivery Route

Use this routing only as much as needed:

1. Delivery priority:
   - Visual fidelity first.
   - Modao editability first.
   - PRD review clarity first.
   - Fast interaction validation first.
2. Style source:
   - Provided reference page/image.
   - Existing style pack or current prototype.
   - Historical project style.
   - New style direction.
3. Delivery scope:
   - One-page sample first.
   - One functional block first.
   - One core flow first.
   - Full batch after sample approval.
4. Target output:
   - HTML/local preview only.
   - Images + PRD board.
   - Modao import.
   - Flowchart + PRD.
   - Pure PRD.
   - Import template.
   - Maintainable prototype code.

For low-risk local edits, keep routing internal and proceed. For Standard/Full, high-impact, visual, full-batch, or Modao tasks, state the selected route and wait for confirmation when the user asked to confirm first.

Use this concise output when routing is needed:

```md
Intake Routing:
1、Task Scale:
1-1：...
2、Delivery Route:
2-1：...
3、Reference Loading:
3-1：...
```

Default delivery templates:

- C-end AI inquiry flow: `user-questioning-flow`.
- C-end page annotation PRD: `c-end-prd-annotation`.
- Style replication: `style-token-extractor`.
- Modao delivery: `modao-import-validator`.
- Backend/admin systems: `admin-system-page`.
- Flowchart: `interaction-flow-map`.

Modao rule: browser preview is not Modao acceptance. Before full Modao import, import or validate one page first, then check image visibility, critical text, annotation numbers, layout alignment, and PRD readability.

### Reference Loading

- Delivery routing or Modao import: use `prototype-delivery-router` first when available or explicitly named.
- Screen-level PRD, element-source mapping, flowcharts, state transitions, or import validation: use `prototype-prd-delivery-standard` after routing when available.
- Backend config affecting user-side behavior: load PRD/system mapping and failure-first rules when available.
- External systems, links, QR codes, live codes, sync, or third-party resources: load challenge, ownership/source-of-truth, and failure-first rules when available.
- Import templates: load import-template rules only after fields and parsing behavior are confirmed.

## Stage Gate

At the start of each non-trivial task, identify the active stage:

- `Intake Routing`: choose task scale, delivery route, and reference loading before artifact creation when the task involves prototype/PRD/flowchart/style replication/C-end/backend/admin/Modao/template delivery.
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

1. Intake: choose task scale, delivery route, reference loading, and validation when needed.
2. Explore: understand source material, existing files, backend/database/screenshots, and current constraints.
3. Frame: define target product structure, user roles, page goals, and business boundaries.
4. Architecture: define routes, modules, components, data/config files, states, and ownership.
5. Skeleton: build or adjust the page skeleton with placeholders before visual polish.
6. Prototype: implement the smallest useful interaction or page section.
7. Verify: run syntax checks, browser checks, or visual checks when possible.
8. Review Fix: fix only explicit review feedback or screenshot-marked issues.
9. Refactor: improve maintainability without changing visible output.
10. PRD: document confirmed product logic and implementation-facing requirements.
11. Handoff: freeze scope before Modao or external design handoff.
12. Template: generate import/export templates only after fields are confirmed.

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

Use numbered structure in PRDs:

```md
1、Exception Source
1-1：Impact scope.
1-2：Blocking strategy.
1-3：Backend/admin presentation.
1-4：End-user presentation.
1-5：Fallback or degradation rule.
1-6：Logs, monitoring, or audit trail.
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

- Use delivery routing before choosing tools when the task may produce prototype, PRD board, flowchart, C-end screens, backend/admin pages, style replication, or Modao output.
- If `prototype-delivery-router` is available and explicitly named, use it first for routing, then continue with this workflow for detailed product architecture, prototype, PRD, or template execution.
- If `prototype-prd-delivery-standard` is available and the task needs element-source mapping, screen-level PRD, state transitions, flowcharts, or Modao/import validation, use it after routing.
- Delivery routing does not override product architecture. For backend/admin systems, source of truth, core object ownership, exceptions, and user-side fallback still come from this workflow.
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

Use this numbered structure:

```md
## Page Name

1、Page Goal
1-1：...
1-2：...

2、Entry And Permissions
2-1：...
2-2：...

3、Page Structure
3-1：...
3-2：...

4、Module Breakdown
4-1：...
4-2：...

Continue this numbered style for fields, states, interactions, validation, exceptions, fallback, data mapping, product-to-tech mapping, logs, and non-goals.
```

PRD rules:

- Prefer numbered paragraphs over tables. Use `1、`, `1-1：`, `1-2：` style for PRD bodies so items can be reviewed, referenced, and changed precisely.
- Do not use tables as the default PRD structure. Use tables only when the user explicitly requests a table or when a compact comparison matrix is clearly better.
- Write backend behavior and end-user behavior as linked numbered items under the same function/module, not as separate scattered tables.
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

1. Run Intake Routing for task scale, delivery route, reference loading, and validation when the work is medium/high-impact or delivery-oriented.
2. Explore source/backend/database/screenshots.
3. Frame target product structure, roles, goals, and boundaries.
4. Define architecture: routes, modules, components, data/config files, states, and ownership.
5. Build or adjust the skeleton with placeholders.
6. Prototype the smallest useful interaction or page section.
7. Verify with browser and syntax checks when relevant.
8. Apply screenshot feedback narrowly.
9. Refactor only when requested or clearly staged.
10. Write PRD only after confirmation.
11. Freeze scope before Modao or external design handoff.
12. Generate templates only from confirmed fields.

When the user changes direction mid-task, acknowledge the newer request and reset the active stage.

## Modao Timing Rule

Modao is a presentation and review artifact, not the default source of product truth.

- Use one-page Modao pre-validation after prototype when the user only needs to test import behavior, editability, image visibility, text completeness, or annotation readability.
- Use formal `Handoff Freeze` and `Modao Handoff` only after the prototype flow or PRD/core product logic is confirmed.
- Browser preview success is not Modao acceptance.
- Product logic changed in Modao must be back-ported to PRD or prototype notes.
- If Modao conflicts with confirmed PRD, treat PRD as source of truth unless the user confirms the Modao change as a new requirement.

## Stop Conditions

Stop and recalibrate instead of continuing to patch when:

1. The same issue is pointed out twice.
2. The user says "not this", "not what I meant", or asks to confirm first after direct execution.
3. Output style clearly drifts from the reference or confirmed style.
4. Changes exceed the requested scope or affect unrelated modules.
5. Review Fix turns into redesign or refactor.
6. Refactor changes visible behavior.
7. Modao/import output differs materially from browser preview.
8. PRD, prototype, and Modao conflict on product logic.
9. Context compression or uncertainty makes the current owner or source structure unclear.
10. A confirmed "do not change" area was changed.

When stopping, output:

```md
Need recalibration:
1、Current deviation:
1-1：...
2、Original request:
2-1：...
3、Must preserve:
3-1：...
4、Smallest next scope:
4-1：...
```

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
