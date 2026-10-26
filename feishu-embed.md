# 飞书 html5-block 嵌入

## 最小 XML

```xml
<title>报告标题</title>
<p>导语段落。</p>
<html5-block path="@visual_01.html"></html5-block>
<p>图下解读。</p>
<html5-block path="@visual_02.html"></html5-block>
```

`path` 用 `@文件名`，且 HTML 与 XML **同目录**。

## 发布

需已配置 `lark-cli`（见 `lark-shared` / `lark-doc`）：

```bash
lark-cli docs +create --as user --content @report.xml
# 或更新已有文档（以当前 lark-doc skill 为准）
```

## HTML 侧约束

- 必须：`use-iframe=true`、`html-box-height-mode=auto`
- 高度靠内容撑开；ECharts 容器给明确 `height`（如 460～520px）并 `resize` 监听
- 避免 `position:fixed`、整页滚动劫持
- 图表 CDN：内网用 byted-static；外网预览可换 jsDelivr

## 与位图的关系

主交付是 HTML。若用户只要贴图：可浏览器截图，但不要替换 html5-block 作为默认路径。
