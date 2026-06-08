# C-End Prototype Rules

Use these rules for user-facing H5/app prototypes.

## Style Consistency

First create or select a style pack. Do not batch-generate many pages from free-form prompts.

Lock:
- phone canvas size
- background color
- header, status bar, stage navigation, bottom input structure
- font sizes and weights
- card, bubble, tag, button, and progress styles
- spacing, radius, shadow, and color tokens

Allowed between states:
- text content
- selected/current stage
- progress value
- AI/user bubbles
- whether helper tags, confirmation buttons, or result modules appear

Forbidden unless approved:
- new visual style
- changed header/nav/input layout
- changed button/tag/card style
- new flow stage
- unapproved module or button

## Interaction Completeness

Every screen is a state node, not just a static picture.

For every state define:
- entry condition
- AI prompt or system message
- user action options
- success path
- incomplete/failure path
- return/exit behavior
- next state

For AI inquiry flows, default logic:
1. User inputs first.
2. AI/Coze judges completeness or stage result.
3. Complete: ask user to confirm, then enter next stage.
4. Incomplete: show helper tags or ask for supplementary input.
5. Tags only assist input; they do not replace user confirmation.
6. Direct conclusion is a weak secondary entry, not the main flow.

## Batch Generation

Generate in this order:
1. one style reference screen
2. one approved sample state
3. one functional block
4. full batch only after approval

After each batch, check style drift and missing interactions before continuing.
