# CSS Introduction

## **CSS 与 HTML 的关系**

- **HTML** 提供结构与数据，**CSS** 提供网页的样式与设计。
- 这种**结构与设计的分离**使得：
    - 页面可以更好地被搜索引擎索引。
    - 视觉障碍用户可以通过语音技术无障碍访问。
    - 不依赖于插件（如 Flash）。

---

## **CSS（Cascading Style Sheet）是啥？**

- 是用来描述 HTML 元素显示方式的样式语言。
- “Cascading（层叠）”的含义：
    - 子元素可以继承父元素的样式。
    - 样式之间有优先级覆盖机制。

---

## **CSS 的三种写法（按优先级排序）**

| **写法** | **说明** | **优点** | **缺点** |
| --- | --- | --- | --- |
| Inline CSS | 在 HTML 标签中使用 style | 优先级最高 | 不易维护，页面混乱 |
| Internal CSS | 在 `<style>` 中写在 `<head>` 内 | 适合单页设计 | 无法复用，影响加载速度 |
| External CSS | 使用 `<link>` 引入外部 CSS 文件 | 可重用、结构清晰 | 优先级最低 |

```html
<!-- inline CSS -->
<p style="color:red;">A red paragraph.</p>
```

```html
<!-- Internal CSS -->
<style>
	body {background-color: yellow;}
</style>
```

```html
<!-- External CSS -->
<head>
	<link rel="stylesheet" type="text/css" href="style.css">
</head>
```

---

## **常见可控制的元素**

- 字体（Fonts）
- 文本（Text）
- 背景（Backgrounds）
- 边框（Borders）
- 尺寸（Sizes）
- 间距（Spacing）
- 位置（Positioning）
- 视觉效果（Visual Effects）
- 表格与列表（Tables and Lists）

---

## **CSS 选择器格式**

```css
html-tag-name {
  property: value;
}
```

- html-tag-name 可为标签（如 div）、ID（如 #id）、类名（如 .class）

| **Tags** | 指任何 HTML 标签本身。比如：`<a>`、`<div>`、`<li>`、`<label>` 等。 在 CSS 中直接使用标签名可以选中所有这种类型的元素。 **例子**：div { color: red; } 表示把所有 `<div>` 标签的字体变成红色。 |
| --- | --- |
| **ID reference** | 指 HTML 元素的 id 属性，在 CSS 中用 # 开头来引用。 一个页面中每个 id 只能唯一存在一次。 **例子**：#main-title { font-size: 24px; } 表示给 id="main-title" 的元素设置字体大小。 |
| **Class reference** | 指 HTML 元素的 class 属性，在 CSS 中用 .（点）开头来引用。 同一个页面中多个元素可以有同一个 class，用于批量设定样式。 **例子**：.highlight { background: yellow; } 表示给所有 class="highlight" 的元素设置背景色。 |

### Tag selector

```css
h1 { 
    /* Styles for h1 elements */ 
    color: #3366cc; 
    font-size: 24px; 
}
```

### ID selector

```css
#header {
    /* Styles for the element with id="header" */ 
    background-color: #f0f0f0; 
    padding: 10px; 
}
```

### class selector

```css
.highlight { 
    /* Styles for elements with class="highlight" */
    background-color: #ffd700; 
    color: #333; 
}
```

---

## **基础样式建议**

- background-color: 背景色（建议用 RGB 十六进制）
- font-size: 字号，单位可为 px, em, %
- font-family: 字体，常见有 serif, sans-serif, monospace
- text-align: 文本对齐（left, center, right）
- float: 浮动方向（left, right）
- vertical-align: 上中下（top, middle, bottom）

---

## **布局方式选择**

| **类型** | **描述** | **使用场景** |
| --- | --- | --- |
| Fluid | 使用 % 或 em，页面随窗口变化而适应 | 响应式设计，移动端友好 |
| Fixed | 使用 px，尺寸固定不随窗口变化 | 控制精确，适合内容稳定的页面 |

## **什么是em？**

- em 是一个 **相对单位**，它的值取决于**当前元素或其继承链中的字体大小（font-size）**。
- 1em 的值 = **父元素的 font-size**。
- 它不仅能用于字体大小，也常用于 margin、padding、width 等属性。

```css
body {
  font-size: 16px;
}

p {
  font-size: 1.5em;  /* 实际效果是 16px × 1.5 = 24px */
}
```

```css
p {
  font-size: 20px;
  padding: 1em;   /* padding = 20px */
}
```

| **单位** | **相对对象** | **是否受嵌套影响** | **易控性** |
| --- | --- | --- | --- |
| em | 当前或父元素 | ✅ 会 | ❌ 易出错 |
| rem | 根元素（html） | ❌ 不会 | ✅ 更可控 |

所以现代项目中常用 rem 来做基础字号设置，用 em 做**组件内部布局的尺寸单位**。

---

## **学习重点回顾**

- **CSS 提供页面视觉风格，和 HTML 内容分离**
- **优先使用 External CSS**，减少冗余、提升维护效率
- **选择 Fluid 还是 Fixed Layout** 取决于用户设备与内容特性
- **三种 CSS 使用方式有不同优先级**，会“层叠”应用到元素上