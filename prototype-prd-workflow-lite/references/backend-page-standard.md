# Backend Page Standard

Use this for admin, operations, configuration, content management, import, rule, report, permission, and status-management pages.

## Layout

- Use a workbench layout, not a landing page.
- Prefer dense but readable structure: title, filters, action bar, table/list, add/edit modal or drawer, preview panel when needed.
- Avoid decorative heroes, oversized cards, marketing copy, gradient decoration, and unrelated visual flourishes.
- Use stable dimensions for tables, forms, buttons, tags, toolbars, and fixed-format controls.

## Information Architecture

Default order:

1. Page title and primary action.
2. Search/filter conditions.
3. Data table, configuration list, or rule list.
4. Row operations: view, edit, delete/disable, preview, copy, sort when relevant.
5. Add/edit modal or drawer.
6. Preview and validation feedback.
7. Empty, loading, disabled, and error states.

Complex configuration forms should split into:

- Basic information.
- Source/content selection.
- Rule or condition configuration.
- Display and preview.
- Status, release, or effective-time control.
- Validation result or import result.

## Controls

- Selects for enums; preserve backend enum values.
- Switches for enable/disable.
- Checkboxes for multi-select conditions.
- Tabs or segmented controls for mutually exclusive modes.
- Numeric inputs for priority, score ranges, limits, weights, and sort.
- Drag handles or up/down controls for ordering.
- Preview buttons for content that affects end-user display.

## Interaction

- Use modal for short forms.
- Use drawer/full modal for multi-section configuration, rule builders, imports, or preview-heavy flows.
- Prototype mode does not require real persistence unless requested.
- Every table/list should support create, edit, delete/disable, preview when relevant.
- Rule builders should separate selected conditions from editable controls.
- If one field selection determines downstream data, auto-fill derived fields and allow manual adjustment.
- Import tools should include upload, parse preview, module confirmation, validation result, completion, and failure-log access.

## Visual Style

- Use restrained color and clear status tags.
- Success for enabled/success, warning for manual confirmation, danger for destructive/error.
- Keep radius at 8px or less unless existing system differs.
- Keep typography compact and readable.
- Prefer labels, hints, and validation messages over visible tutorial copy.
