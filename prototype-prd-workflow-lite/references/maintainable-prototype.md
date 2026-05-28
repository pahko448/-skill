# Maintainable Prototype Standard

Use this for medium/large prototypes, refactors, long-running sessions, or when file size/context bloat becomes a risk.

## Architecture Layers

Separate:

1. Route/page layer.
2. Module/component layer.
3. Data/config/mock layer.
4. State/interaction layer.
5. Visual/style layer.

Rules:

- Do not place page content, mock data, interaction logic, and styles in one large file.
- Each major page section should have a clear owner.
- Backend-like configuration, enums, option lists, report/recommendation content, scoring descriptions, and business data should live in config/mock files when they may change.
- Components should receive data through props or local data imports whenever feasible.
- Prefer local component-level changes over global changes.
- Do not rename paths, move files, or restructure folders during normal feature edits.
- Do not create a new parallel implementation when an existing module owns the behavior.

## Project Structure Lock

After Prototype, Review Fix, or Refactor begins, treat file structure as locked unless restructuring is requested.

- Do not rename routes, folders, components, config files, or mock files.
- Do not move files unless the task is explicitly Refactor.
- Do not modify global styles, shared layout, routing, or shared components unless confirmed.
- If shared files must change, explain why before editing.

## Module Ownership Map

Before editing mature prototypes, identify:

- Page owner.
- Module owner.
- Component owner.
- Data owner.
- Style owner.
- State owner.

If unclear, inspect current structure first. Do not duplicate modules or change multiple possible owners at once.

## Skeleton First

For new medium/large features:

1. Define routes/pages.
2. Define page/module list.
3. Define component tree.
4. Define data/config/mock files.
5. Define business and exception states.
6. Build skeleton with placeholders.
7. Implement one module at a time.
8. Wire interactions after layout is stable.
9. Polish visuals last.

## Data And UI Separation

- Do not hardcode changeable business lists, enums, report dimensions, scoring descriptions, or backend-controlled content inside large page components.
- Put mock data, options, report content, recommendation content, and backend-like configs into separate files.
- Keep display components as pure as feasible.
- Isolate interaction/state logic from static display content when feasible.

Suggested files:

- `mock/reportData.ts`
- `mock/userData.ts`
- `config/recommendConfig.ts`
- `config/assessmentOptions.ts`
- `constants/status.ts`
- `constants/enums.ts`

## Context Compression Protection

- Re-read relevant architecture notes and target files before editing.
- Prefer editing one page, module, or component per task.
- Maintain concise notes when useful:
  - `docs/PROJECT_ARCHITECTURE.md`
  - `docs/ROUTES.md`
  - `docs/MODULE_MAP.md`
  - `docs/DATA_MODEL.md`
  - `docs/CHANGELOG.md`
- If notes conflict with current files, trust current files.
- After significant structure changes, update relevant notes.

## Refactor Mode

Use only when asked to restructure, split files, reduce file size, reduce context bloat, extract components, or clean duplication.

- Preserve visual output, routes, interactions, and data behavior.
- Do not add features, redesign UI, or change copy unless requested.
- Split one page at a time.
- Extract one module at a time when risk is high.
- Move mock/config data out of large components when appropriate.
- Run syntax checks when feasible.

Refactor summary:

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
