# Page Type Classification

Identify page type before writing PRD or flowchart. A page can match multiple types.

## User-Facing Pages

- Flow page: guides users step by step.
- Form page: collects structured input.
- AI interaction page: includes AI replies, generated tags, recommendations, or summaries.
- Result page: shows generated or computed results.
- Detail page: shows one object, record, task, order, or content item.
- Payment/member page: includes pricing, rights, quotas, balances, renewal, or consumption.
- Content page: articles, lessons, recommendations, media, or community content.

## Backend/Admin Pages

- List page: table, search, filters, sorting, pagination, bulk actions.
- Detail page: record details, timeline, related data, audit info.
- Edit page: create/edit forms, validation, save/publish workflow.
- Review page: approval, rejection, comments, status transition.
- Configuration page: rules, switches, thresholds, templates, feature flags.
- Data dashboard: metrics, charts, date ranges, drill-down, export.
- Permission page: roles, resources, actions, visibility, authorization.
- Import/export page: upload, parse, validate, preview, confirm, result report.
- Log/audit page: action history, operator, before/after values, trace ID.

## Mixed Pages

When a page mixes user-facing and backend rules, split the PRD by role:

1. End-user experience.
2. Operator/admin experience.
3. Shared data model and state transitions.
4. Permission and audit requirements.

## Classification Output

Before writing detailed PRD, state:

```text
页面类型：后台列表页 + 审核页
使用规则：后台系统规则、状态流转规则、权限日志规则
主要风险：状态流转和权限边界需要后端确认
```
