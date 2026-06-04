# Validation Checklist

Run this before final delivery.

## Completeness

- Page count matches source/prototype.
- PRD card count matches page count when page-level PRD is requested.
- Flowchart nodes cover all pages/states.
- Main flow has start and end.
- Branch flows reconnect or end clearly.
- Exception flows are not missing.

## PRD Quality

- Every module uses numbered format.
- Every module includes element, source, and explanation.
- Button titles use real button names.
- Tags/options describe selected state and submit behavior.
- AI-generated content has source and fallback.
- Backend fields include permissions and logs when relevant.
- Dynamic fields include update rules.

## Visual Quality

- No garbled text.
- No clipped key text.
- No button text overflow.
- No mismatched annotation numbers.
- No overlapping modules.
- No unnecessary empty boxes.
- Progress, status, price, quota, and button names are fully visible.

## Backend/Admin Quality

- List filters and columns are defined.
- Create/edit validation is defined.
- Status transitions are defined.
- Permission visibility is defined.
- Audit logs are defined.
- Import/export success, failure, and partial success are defined.

## User App Quality

- Return/exit behavior is defined.
- Loading/success/error states are defined.
- Input submit and selected value behavior are defined.
- Result and follow-up actions are defined.
- AI generation and retry behavior are defined when applicable.

## Import Quality

- Local HTML opens correctly.
- Imported result is checked when tool access is available.
- Critical text remains visible after import.
- If import validation cannot be performed, say so explicitly.
