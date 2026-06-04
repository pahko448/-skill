# Collaboration Checkpoints

Use this when work is complex, visual, import-sensitive, ambiguous, or has failed more than once.

## Before Starting

Restate four things before editing:

```text
目标：用户最终想得到什么
验收标准：用户会怎么看是否正确
本次范围：这次会改什么，不会改什么
验证方式：源码检查 / 本地页面 / 导入后页面 / 截图对照
```

If the user asked to hear the solution first, do not edit until the user confirms.

## Before High-Impact Changes

Ask for confirmation before changing:

- Layout and spacing rules.
- Page grouping or ordering.
- PRD format.
- Flowchart structure.
- Import strategy.
- Component structure for critical visual elements.
- Any change that affects many pages or shared styles.

## When Feedback Uses References

When the user says "like this", "same as this", "this one", or sends a screenshot:

1. Identify the exact reference area.
2. Describe what will be copied from it: spacing, layout, content structure, visual style, or interaction.
3. State what will not be copied.
4. Wait for confirmation if the interpretation is not obvious.

## Two-Failure Rule

If the same issue is not fixed after two attempts:

1. Stop patching the same approach.
2. State the observed failure plainly.
3. Separate possible causes:
   - misunderstanding of requirement
   - source data missing
   - local rendering issue
   - import/conversion issue
   - layout/style clipping
4. Propose a different implementation strategy.
5. Ask for confirmation before continuing.

## Validation Levels

Never treat one validation level as proof of another:

```text
源码存在：HTML/CSS/data contains the value.
本地可见：browser or screenshot shows the value locally.
导入可见：Modao/imported canvas shows the value.
```

For visual/import tasks, final confidence requires the highest available validation level.

## Progress Reporting

For repeated fixes, report using this format:

```text
问题1：已解决 / 未解决 / 需要确认
证据：本地截图 / 导入截图 / 文件检查 / 命令结果
风险：仍可能被导入工具裁切 / 需要用户在目标页面确认
```

## Tone And Recovery

- Do not argue from source code when the user's screenshot contradicts it.
- Acknowledge mismatch quickly.
- Prefer changing strategy over repeatedly tuning a fragile implementation.
- Keep the user's acceptance standard as the source of truth.
