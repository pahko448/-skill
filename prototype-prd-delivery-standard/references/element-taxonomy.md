# Element Taxonomy

Use this taxonomy to identify elements consistently across user apps and backend systems.

## Element Types

1. Static display elements
   - Title, icon, copy, description, helper text, section header, placeholder.

2. Dynamic data elements
   - Status, progress, amount, count, time, user info, quota, membership rights, computed values.

3. User input elements
   - Text input, textarea, selector, date picker, upload, checkbox, radio, switch, slider, search field.

4. User action elements
   - Button, link, menu item, tab, segmented control, bulk action, row action, shortcut action.

5. System feedback elements
   - Loading, empty state, success state, error state, toast, modal, validation message, disabled state.

6. Flow control elements
   - Stepper, progress bar, navigation, return, exit, cancel, retry, skip, confirm, next/previous.

7. AI/generated elements
   - AI reply, suggested tags, recommendation, summary, generated report, model judgment, extracted entities.

8. Backend/admin elements
   - Table, filter, search, pagination, detail field, audit log, permission control, import preview, export button.

## Source Types

Use one or more source types per element:

- Frontend fixed configuration.
- Current page state.
- User input.
- Service API response.
- Backend/admin configuration.
- Permission system.
- AI/agent/model generation.
- Third-party API.
- Local cache.
- Operations/marketing configuration.
- System default value.
- Derived/computed value.

## Update Rules

For dynamic elements, always describe how values update:

- Page initialization load.
- User click/selection.
- User input submit.
- AI/model response.
- API polling or websocket push.
- Backend configuration change.
- Permission or role change.
- Local cache restore.
- Retry after failure.

## Required Description

Every meaningful element should answer:

```text
What is it?
Where does it come from?
When does it update?
What happens when the user interacts with it?
What happens when source data is missing or fails?
```
