# PRD Format

Use numbered sections. Do not use tables unless the user explicitly asks for tables.

## Module Format

```text
1、模块名称
1-1：元素：具体元素名称或页面可见内容
1-2：来源：数据或配置来源
1-3：说明：展示、交互、更新、异常规则
```

## Button Format

Use the actual button name as the title. Do not write "操作按钮".

```text
4、保存草稿
4-1：元素：保存草稿
4-2：来源：前端固定入口 + 当前表单状态
4-3：说明：点击后校验可保存字段；保存成功后展示成功提示并停留当前页；失败时展示错误提示。
```

## Tag/Option Format

```text
3、候选标签区
3-1：元素：页面当前展示的候选标签
3-2：来源：后台配置 / 服务端接口 / AI生成 / 前端固定枚举
3-3：说明：点击后进入选中态；选中值回填到输入区或当前表单字段；提交后更新页面状态或进入下一流程。
```

## AI Content Format

```text
2、AI回复文案
2-1：元素：页面展示的AI回复内容
2-2：来源：AI/智能体生成
2-3：说明：前端原样展示，不改写；长文本按容器换行；生成失败时展示重试或兜底提示。
```

## Backend Field Format

```text
5、审核状态
5-1：元素：审核状态字段
5-2：来源：服务端接口返回 + 状态机
5-3：说明：状态包括「待审核」「已通过」「已驳回」；不同状态控制按钮可见性和可编辑范围。
```

## Avoid

- Do not use vague module names such as "页面内容", "功能按钮", "操作区域" when the actual function is known.
- Do not omit source just because the value looks static.
- Do not copy long visible text into PRD if it causes layout issues. Use short reference plus source rule.
- Do not mix multiple unrelated controls under one numbered item unless they share one behavior.
