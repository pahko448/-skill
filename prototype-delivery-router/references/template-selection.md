# Template Selection

Use this file to select the right delivery template before creating artifacts.

## User-App / C-End

`user-questioning-flow`
- Use for H5/app flows with AI prompts, user input, stage navigation, status, progress, labels, and result pages.
- Required outputs: state list, transition rules, one screen per state, PRD per screen.

`c-end-prd-annotation`
- Use for a phone screen plus PRD explanation board.
- Required outputs: annotation numbers on the prototype, matching numbered PRD modules, source and behavior for each module.

`style-token-extractor`
- Use when the user gives a reference page/image and wants future screens to match it.
- Required outputs: style tokens, reusable component list, allowed state changes, forbidden style changes.

## Backend / Admin

`admin-system-page`
- Use for backend configuration, list, detail, audit, permissions, logs, or data dashboard pages.
- Required outputs: role/permission rules, field source, action states, empty/error/loading states.

## Flowchart

`interaction-flow-map`
- Use when user asks how each click/input flows.
- Required outputs: main flow, branch flow, failure flow, return flow, completion flow.

## Modao

`modao-import-validator`
- Use whenever output must be imported into Modao.
- Required outputs: import mode decision, one-page import sample, post-import checklist.

## Default Combinations

C-end AI inquiry + PRD + Modao:
- `user-questioning-flow`
- `style-token-extractor`
- `c-end-prd-annotation`
- `modao-import-validator`

Backend admin PRD:
- `admin-system-page`
- `interaction-flow-map`

Simple PRD only:
- `c-end-prd-annotation` for user pages
- `admin-system-page` for backend pages
