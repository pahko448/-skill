# PRD Standard

Use PRD mode only after page flow, module structure, or backend fields are confirmed.

## Numbered Structure

```md
## Page Name

1、Page Goal
1-1：...
1-2：...

2、Entry And Permissions
2-1：...
2-2：...

3、Page Structure
3-1：...
3-2：...

4、Module Breakdown
4-1：...
4-2：...

Continue this numbered style for fields, states, interactions, validation, exceptions, fallback, data mapping, product-to-tech mapping, logs, and non-goals.
```

## Numbered Writing Rules

- Prefer numbered paragraphs over tables. Use `1、`, `1-1：`, `1-2：` style for PRD bodies so items can be reviewed, referenced, and changed precisely.
- Do not use tables as the default PRD structure.
- Use tables only when the user explicitly requests a table or when a compact comparison matrix is clearly better.
- Write backend behavior and end-user behavior as linked numbered items under the same function/module, not as separate scattered tables.

## Product-To-Tech Mapping

For implementation-oriented PRDs, include:

1、Route list
1-1：Page route.
1-2：Page owner.

2、Component tree
2-1：Page component.
2-2：Module component.
2-3：Shared component if any.

3、Data model
3-1：API field or mock key.
3-2：Enum or backend constant.
3-3：State or status value.

4、API/mock boundary
4-1：Backend source.
4-2：Mock/config source.
4-3：Files allowed to change.
4-4：Files not allowed to change.

## Exception And Fallback

All backend configuration PRDs must include backend and end-user handling:

```md
1、Exception Source
1-1：Impact scope.
1-2：Blocking strategy.
1-3：Backend presentation.
1-4：End-user presentation.
1-5：Fallback rule.
1-6：Logs/alerts.
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
