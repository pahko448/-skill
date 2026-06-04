# User App Rules

Use for mobile apps, H5 pages, consumer web pages, AI chat flows, onboarding, payment/member pages, and result pages.

## Required Areas

- Entry source and user goal.
- Page title and navigation.
- Main content and explanation.
- User input or selection.
- Action buttons.
- Status/progress/stepper.
- Loading, success, error, empty, and retry states.
- Return, exit, cancel, and interruption behavior.
- Result page and follow-up actions.

## AI Interaction Pages

For AI-generated content, always define:

- AI content source.
- Whether frontend can rewrite content.
- Loading state while generating.
- Failure state and retry.
- User can edit, regenerate, or continue.
- Generated tags/recommendations and how they are selected.
- What user input is submitted back to AI.

## Flow Pages

For each step:

```text
Step name
Entry condition
Visible elements
User action
Data submitted
Next step
Back/exit behavior
Failure fallback
```

## User Input Rules

- Define placeholder text source.
- Define selected value display.
- Define send/submit action.
- Define whether input can be empty.
- Define whether user can revise previous input.
- Define what happens after submit.

## Visual Deliverable Rules

- Avoid small critical text in narrow capsules.
- Progress, status, price, quota, and button names must be fully readable.
- If using HTML import tools, prefer stable dimensions and avoid clipped overflow.
