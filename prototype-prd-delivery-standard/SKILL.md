---
name: prototype-prd-delivery-standard
description: Use for universal product prototype delivery work, including user-facing apps, backend/admin systems, page analysis, PRD writing, element-source mapping, flowcharts, state transitions, permissions, HTML/Modao import checks, and final acceptance validation. Trigger when the user asks to build, refine, document, annotate, import, connect, or review prototypes and PRDs across different page types.
---

# Prototype PRD Delivery Standard

Use this skill to produce reusable, implementation-facing product deliverables. It is not tied to one business domain. Apply it to user apps, AI flows, backend/admin systems, data dashboards, configuration pages, import/export tools, and multi-step workflows.

## Core Workflow

1. Identify the delivery target.
   - User-facing page, backend/admin page, AI-assisted page, mixed system, or import/export template.
   - Prototype only, PRD only, flowchart only, Modao/HTML import only, or full delivery.

2. Calibrate collaboration before high-impact or repeated work.
   - Read `references/collaboration-checkpoints.md` when the task affects layout, flow, PRD rules, import structure, or when the same issue has failed more than once.
   - Restate the goal, acceptance criteria, change scope, and validation method before editing.

3. Classify page types before writing.
   - Read `references/page-types.md` when the page type is unclear or mixed.

4. Extract elements using the shared taxonomy.
   - Read `references/element-taxonomy.md`.
   - Every visible or interactive item must have element, source, and behavior.

5. Select domain rules.
   - User-facing flows: read `references/user-app-rules.md`.
   - Backend/admin systems: read `references/admin-system-rules.md`.
   - State, permissions, roles, and logs: read `references/state-and-permission-rules.md`.

6. Write PRD in numbered format.
   - Read `references/prd-format.md`.
   - Do not use tables unless the user explicitly requests them.

7. Build or revise flowcharts.
   - Read `references/flowchart-rules.md`.
   - Include main flow, branch flow, exception flow, return/exit flow, and completion flow.

8. If generating HTML for Modao or another visual import target, apply import-safe rules.
   - Read `references/modao-html-import-rules.md`.
   - Local HTML correctness is not enough. Check actual visual readability after import when possible.

9. Finish with acceptance validation.
   - Read `references/validation-checklist.md`.
   - Report unresolved risks clearly.

## Non-Negotiable Rules

- Do not bind output to a previous project unless the user explicitly says to reuse that business content.
- Do not write generic button sections such as "operation button". Use the actual button name as the module title.
- Do not omit source mapping. Every meaningful element needs a source.
- Do not rely on tables for PRD body structure. Use consistent numbered sections.
- Do not claim visual correctness from source code alone. Verify rendered/imported output when the target is visual.
- Do not silently discard branch, failure, permission, or return/exit flows.
- If the same issue fails twice, stop patching and recalibrate before making another change.

## Default PRD Line Format

Use this format for every module:

```text
1、模块名称
1-1：元素：页面上看到的具体元素
1-2：来源：前端固定配置 / 用户输入 / 当前页面状态 / 服务端接口返回 / 后台配置项 / 权限系统 / AI生成 / 第三方接口 / 运营配置 / 系统默认值
1-3：说明：展示规则、点击规则、更新规则、异常规则
```

For buttons, use the real button name:

```text
4、提交审核
4-1：元素：提交审核
4-2：来源：前端页面状态配置 + 权限系统
4-3：说明：点击后校验必填字段；校验通过后提交服务端，状态进入「待审核」；失败时展示错误提示并保留用户输入。
```

## Output Expectations

- Keep deliverables complete enough for product, design, and development to align.
- Prefer short but precise rules over long prose.
- For ambiguous systems, state assumptions and separate confirmed rules from proposed rules.
- When importing to Modao or another tool, keep visual assets and text import-safe, then validate.
