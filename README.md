# doc-html5-visuals

Cursor Agent Skill：为调研报告 / 飞书文档生成 **html5-block 单文件 HTML 配图**（身份卡、卡片组、分层全景、ECharts 雷达/散点），风格对齐 AI 调研报告 house style。

适用场景：

- 文档配图 / 调研配图 / 身份卡
- 飞书 `html5-block` 嵌入
- 需要与现有调研报告视觉一致的可视化

## 文件结构

```text
SKILL.md                 # Skill 主说明（选型、令牌、工作流）
tokens.md                # 设计令牌与排版细则
feishu-embed.md          # 飞书 html5-block 嵌入说明
templates/               # 5 类可填空 HTML 模板
examples/                # 风格样例（只读参考）
```

## 使用方式

1. 将本仓库内容放到 Cursor 个人 skills 目录，例如：
   `~/.cursor/skills/doc-html5-visuals/`
2. 在对话里说「用文档配图 skill 做一张身份卡 / 雷达图」等即可触发。

依赖（可选）：

- 飞书发布：已配置的 `lark-cli` + `lark-doc` / `lark-shared`
- ECharts 图：内网用 byted-static CDN；外网预览可用 jsDelivr

## License

MIT
