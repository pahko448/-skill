# PRD Annotation Rules

Use for C-end PRD boards and screen-by-screen documentation.

## Numbering

Each screen has its own PRD. Annotation numbers on the prototype must match PRD module numbers exactly.

Do not summarize several screens into one PRD unless the user asks.

## Required Format

Use numbered text, not tables:

```text
1. Module name
1-1: Element: exact visible text or component name
1-2: Source: front-end fixed config / user input / Coze generated / Coze variable / service API / backend config / permission system
1-3: Rule: display, click, update, validation, exception, or next-state rule
```

## Source Mapping

Common sources:
- Front-end fixed config: static labels, layout, fixed navigation
- User input: typed text, selected tag, voice input
- Coze generated: AI reply, dynamic suggestions, helper labels
- Coze variable: progress percent, current stage, completeness result
- Service API: membership time, account benefits, history records
- Backend config: feature switches, category lists, copy rules
- Permission system: visible actions, admin-only actions

## Interaction Flow Section

Every screen PRD needs a short interaction flow:

```text
Interaction flow
1. Click/Input A: go to ...
2. Click/Input B: stay on ... and show ...
3. AI complete: go to ...
4. AI incomplete: go to ...
5. Return/Exit: ...
```

## Avoid

- Generic headings such as "operation button"
- Repeating global header rules on every page; write global structure once, then focus later pages on changed elements
- Missing backend/Coze/source ownership
- PRD numbers that do not match prototype labels
