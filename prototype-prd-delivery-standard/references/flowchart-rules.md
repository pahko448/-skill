# Flowchart Rules

Use flowcharts to connect pages, states, actions, branches, exceptions, and final outcomes.

## Required Flow Types

1. Main flow.
2. Branch flow.
3. Exception flow.
4. Return/exit flow.
5. Completion flow.

## Node Definition

Each node should include:

```text
Node ID
Page/state name
Entry condition
User/system trigger
Submitted data
Next node
Failure fallback
```

## Edge Definition

Each connection should define:

```text
From node
Trigger
Condition
To node
State update
```

## Output Pattern

Use compact node cards plus explicit line rules:

```text
01 页面A → 02 页面B → 03 页面C
03 点击「提交」且校验通过 → 04 成功页
03 点击「提交」且校验失败 → 03 当前页展示错误
03 点击「退出」且已有输入 → 退出确认弹窗
```

## Common Flow Risks

- Branch has no return or completion.
- Button has no target state.
- Error path is missing.
- Back/exit behavior is undefined.
- Generated content has no loading/failure state.
- Backend status transition is not aligned with UI state.
