# State And Permission Rules

Use for status machines, multi-role systems, backend admin workflows, AI generation states, and gated user flows.

## State Definition

For each state, define:

```text
State name
Entry condition
Visible fields
Available actions
Next states
Failure states
Can return or edit
Logs/audit requirements
```

## Common State Categories

- Not started.
- In progress.
- Waiting for user input.
- Waiting for system/AI/API.
- Completed.
- Failed.
- Draft.
- Submitted.
- Pending review.
- Approved.
- Rejected.
- Disabled.
- Expired.

## Permission Definition

For each role/action:

```text
Role
Visible fields
Editable fields
Available buttons
Data scope
Export/import permission
Audit requirement
No-permission presentation
```

## Backend Logs

For backend/admin systems, define audit records for:

- Create.
- Edit.
- Delete.
- Enable/disable.
- Approve/reject.
- Import/export.
- Permission changes.
- Configuration changes.
- Manual retry or rollback.

Each log should include operator, time, action, object ID, before/after value, result, and failure reason when relevant.
