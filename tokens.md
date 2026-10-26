# 设计令牌与排版细则

与 `examples/` 源文件一致。改色只改 CSS 变量，不要在组件里硬编码第二套色。

## 色板

| Token | Hex | 用途 |
|---|---|---|
| `--brand` | `#2f6fed` | 主色、logo 渐变起点、`<b>` 强调 |
| `--brand-2` | `#60a5fa` | logo 渐变终点、次级层左边线 |
| `--amber` | `#f59e0b` | 品类/层强调、ECharts 第 2 色 |
| `--green` | `#10b981` | 正向层、ECharts 第 3 色 |
| `--red` | `#ef4444` | 警示层、ECharts 第 4 色 |
| `--hot` | `#b42318` | `.hot` 爆点/纠偏字段正文 |
| `--ink` | `#1f2d3d` | 主标题、图表标题 |
| `--ink-2` | `#334155` | 字段正文、轴名 |
| `--mute` | `#94a3b8` | 标签、副标题、subtext |
| `--line` | `#e8edf3` | 卡片边框、层边框 |
| `--hair` | `#f0f3f7` | 字段顶部分割线 |
| slate | `#64748b` | 中性品类（文本写作等）|

分层全景左边线建议：顶层 green → brand → brand-2 → amber → slate。

## 字号（身份卡）

| 元素 | 字号 | 字重 |
|---|---|---|
| 卡标题 `.title` | 22px | 700 |
| 副标题 `.subtitle` | 13px | 400，mute |
| 字段标签 `.label` | 12px | mute |
| 字段值 `.value` | 15px | ink-2，行高 1.45 |
| Logo 缩写 | 22px | 700，白字 |

卡片组缩一档：标题 17、logo 40×40、正文 12.5。

## 间距与圆角

- 身份卡 padding：`28px 32px`；头下边距 22；grid gap `14px 40px`
- 卡片圆角 16（单卡）/ 14（组内）；logo 圆角约 13
- body padding：`8px`（卡）或 `16px 12px`（全景）
- 阴影：`0 6px 24px rgba(31,45,61,.06)`（组内可略弱）

## 图表文案

- `title.text`：一句判断（结论优先）
- `subtext`：轴 / 评分 / 口径说明，11～12px mute
- legend 放底部；grid 为标题和 legend 留空
- scatter 标签 `fontWeight:600`、`fontSize:11`、颜色 ink
