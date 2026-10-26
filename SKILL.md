---
name: doc-html5-visuals
description: >-
  Generate Feishu/lark-doc html5-block research visuals as single-file HTML
  (identity cards, card groups, layered panoramas, ECharts radar/scatter).
  Use when the user asks for 文档配图, 调研配图, 身份卡, html5-block, report
  charts, or visuals matching the AI research-report house style.
---

# 文档 html5-block 配图（House Style）

为调研报告 / 飞书文档生成**单文件 HTML 配图**，风格对齐 `examples/` 里的 AI 调研报告源文件。

输出是可嵌进飞书的 `html5-block`，**不是**位图、不是 React、不是多文件工程。

## 何时用

- 用户要「配图 / 可视化 / 身份卡 / 分层全景 / 雷达图 / 散点图」
- 内容要嵌进飞书文档（`lark-cli` + `html5-block`）
- 需要和现有调研报告视觉一致

## 工作流

1. **选类型**（见下表）→ 复制对应 `templates/*.html` 再填字段
2. 写出完整单文件 HTML（含 `<!doctype>`、meta、内联 CSS/JS）
3. 本地用浏览器打开自检；ECharts 图需能联网
4. 若要发飞书：同目录 XML + `html5-block`，再 `lark-cli docs +create/update`
5. 关键数字 / 结论用 `<b>`；争议或爆点字段加 `class="hot"`

### 类型选择

| 意图 | 模板 | 参考样例 |
|---|---|---|
| 单个产品/公司档案 | `templates/id-card.html` | `examples/visual_02.html`～`04`, `07`～`10` |
| 2～4 个对象并排对比 | `templates/card-group.html` | `examples/visual_06.html` |
| 分层全景 / 品类地图 | `templates/layered-panorama.html` | `examples/visual_01.html` |
| 多维定性对比 | `templates/radar.html` | `examples/visual_05.html` |
| 二维定位（X/Y/气泡/品类色） | `templates/scatter.html` | `examples/visual_11.html` |

自定义图：先对齐 [tokens.md](tokens.md)，再扩展；不要另起配色体系。

## House Style（必须遵守）

### 设计令牌

```css
:root {
  --brand: #2f6fed;
  --brand-2: #60a5fa;
  --amber: #f59e0b;
  --green: #10b981;
  --red: #ef4444;
  --hot: #b42318;
  --ink: #1f2d3d;
  --ink-2: #334155;
  --mute: #94a3b8;
  --line: #e8edf3;
  --hair: #f0f3f7;
}
```

- 背景：`#fff`；正文字体：`-apple-system, "PingFang SC", "Microsoft YaHei", sans-serif`
- Logo 方块：`linear-gradient(135deg, #2f6fed, #60a5fa)` + 白字缩写
- 强调：普通重点 `value b { color: var(--brand) }`；爆点/纠偏 `.hot .value` 用 `--hot`
- 卡片：白底、`1px solid #e8edf3`、圆角 14～16、轻阴影 `0 6px 24px rgba(31,45,61,.06)`
- ECharts 调色板顺序：`['#2f6fed','#f59e0b','#10b981','#ef4444','#64748b']`；`renderer:'svg'`

### 飞书 html5-block 头

每张图必须带：

```html
<meta name="use-iframe" content="true">
<meta name="html-box-height-mode" content="auto">
<meta name="description" content="一句话说明这张图在讲什么">
```

`lang="zh-CN"`；`title` / `description` 写清用途，方便检索。

### 文案规范

- 副标题格式：`品类/定位 · 身份卡 · YYYY-MM`（或等价信息密度）
- 字段：上灰标签（12px mute）+ 下正文（15px ink-2）；两列 grid，长字段 `wide` 跨列
- 标题要有**结论感**（散点/雷达的 `title.text` 写判断，不是复述坐标轴）
- `subtext` 解释轴含义、评分口径、数据时点
- 缺数据如实写「公开资料未检到」，不要编造

### 禁止

- 紫渐变、深色主题、玻璃拟态、大装饰插画、emoji 堆砌
- 外链 CSS/字体；除 ECharts 外不引第三方库
- 把多张不相关图塞进一个 HTML
- 位图导出当主交付（主交付永远是 `.html`）

## ECharts CDN

默认（字节内网，与样例一致）：

```html
<script src="https://unpkg.byted-static.com/echarts/5.5.1/dist/echarts.min.js"
  integrity="sha384-Mx5lkUEQPM1pOJCwFtUICyX45KNojXbkWdYhkKUKsbv391mavbfoAmONbzkgYPzR"
  crossorigin="anonymous"></script>
```

外网预览可改用：`https://cdn.jsdelivr.net/npm/echarts@5.5.1/dist/echarts.min.js`（可去掉 integrity）。

## 嵌进飞书

同目录放置 HTML 与 XML，例如：

```xml
<title>文档标题</title>
<p>下文为配图：</p>
<html5-block path="@visual_xx.html"></html5-block>
```

```bash
lark-cli docs +create --as user --content @doc.xml
```

细节见 [feishu-embed.md](feishu-embed.md)。飞书能力走 `lark-doc` / `lark-shared` skill。

## 交付清单

- [ ] 单文件 HTML，可双击打开
- [ ] 令牌与样例一致；强调色只用 brand / hot
- [ ] 飞书 meta 齐全；移动端有简单 `@media` 折列
- [ ] 文件名：`visual_NN.html` 或 `visual_<slug>.html`
- [ ] 用户若要入库：同时给可粘贴的 `html5-block` XML 片段

## 延伸阅读

- 令牌与层级色：[tokens.md](tokens.md)
- 飞书嵌入：[feishu-embed.md](feishu-embed.md)
- 完整样例：`examples/visual_01.html` … `visual_11.html`
