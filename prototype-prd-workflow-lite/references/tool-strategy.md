# Tool Strategy

Use tools deliberately and only when they fit the current stage.

## UI/UX

Use `ui-ux-pro-max` when the task asks for:

- UI/UX quality.
- Page design.
- Backend/admin interaction design.
- Visual polish.
- Layout review.
- Component-level design judgment.

Use it after stage framing so UI detail does not override scope.

## Browser

Use Browser plugin/browser skill for:

- Opening local prototypes or in-app pages.
- Inspecting current UI.
- Clicking and verifying interactions.
- Taking screenshots.
- Checking visual layout after frontend changes.

## Pencil MCP

Use Pencil MCP tools for `.pen` files or design canvas work:

- `get_editor_state` for current file/selection.
- `batch_get` for components/nodes.
- `batch_design` for structured edits.
- `snapshot_layout` or `get_screenshot` for verification.

## Documents And Spreadsheets

- Use Documents plugin only for `.docx`, Word, or document artifacts.
- For Markdown PRDs, edit Markdown files directly.
- Use Spreadsheets plugin for `.xlsx`, `.xls`, `.csv`, spreadsheet analysis, or Excel import templates.

## Backend Truth Order

When backend truth matters, use:

1. Existing source map, local source, or frontend chunks.
2. Current backend page through Browser.
3. Database schema and sample data when credentials are provided.
4. Old prototype as reference only.
