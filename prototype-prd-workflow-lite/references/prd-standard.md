# PRD Standard

Use PRD mode only after page flow, module structure, or backend fields are confirmed.

## Structure

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

## Product-To-Tech Mapping

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

For implementation-oriented PRDs, include:

- Route list.
- Component tree.
- Data model.
- State list.
- Config list.
- API/mock boundary.
- Files allowed to change.
- Files not allowed to change.

## Exception And Fallback Table

All backend configuration PRDs must include backend and end-user handling:

```md
| Exception Source | Impact Scope | Blocking Strategy | Backend Presentation | End-User Presentation | Fallback Rule | Logs/Alerts |
| --- | --- | --- | --- | --- | --- | --- |
```

Cover configuration disabled/expired, referenced object unavailable, enum removed, media unavailable, invalid link, rule no-match/conflict, required data missing, API error, import partial success, and permission mismatch when relevant.

End-user fallback patterns:

- Hide affected module.
- Hide or disable affected button.
- Show default content.
- Show placeholder image.
- Skip empty module while preserving continuity.
- Use default rule/result.
- Ignore unavailable optional conditions.
- Show retry only for core user-facing failures.

## Rules

- Follow confirmed prototype and real backend fields.
- Do not add modules outside confirmed scope unless marked as proposed.
- Record visible fields, buttons, states, empty states, and error states.
- Include permissions, logs, audit, and monitoring when relevant.
- For import features, include parsing, validation, failure logs, retry paths, and partial-success behavior.
