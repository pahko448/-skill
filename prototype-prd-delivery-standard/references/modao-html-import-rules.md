# Modao And HTML Import Rules

Use when generating HTML for Modao or similar tools that convert HTML into editable design elements.

## Core Principle

Local HTML correctness is not enough. The imported result must be visually checked because import tools can change layout, text clipping, fonts, overflow, and element boundaries.

## Import-Safe Layout

- Use stable widths and heights for critical elements.
- Avoid relying on narrow capsules for critical text.
- Avoid complex nested spans for values that must remain visible.
- Avoid internal scroll clipping unless the imported tool supports it.
- Avoid `overflow:hidden` on containers holding important text.
- Keep text and icon hit areas large enough.
- Use explicit line-height and white-space rules for key labels.
- For critical badges, consider a dedicated element with inline width/height if import is fragile.

## Critical Text Checklist

Always verify these after import:

- Page title.
- Navigation and stage labels.
- Status text.
- Progress percent.
- Price/amount/count/quota.
- Button names.
- Error messages.
- Table headers.
- Form labels.
- AI-generated summaries or recommendations.

## Modao-Specific Lessons

- A text value can exist in source but still be visually clipped after import.
- Class-based CSS can be overridden or interpreted differently.
- A capsule that looks wide enough in code may still clip final characters.
- PRD text can show a value while prototype text clips the same value; verify both.
- Re-importing may create a new document; confirm the user is viewing the latest import.

## Validation Rule

When possible, inspect the imported canvas or a screenshot. If not possible, state that validation is limited to local HTML/source checks.
