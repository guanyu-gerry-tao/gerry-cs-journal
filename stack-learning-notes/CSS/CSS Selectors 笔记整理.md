# CSS Selectors 笔记整理

## **1. 基本选择器（Basic Selectors）**

| **类型** | **示例** | **说明** |
| --- | --- | --- |
| 元素选择器 | `div` `input` `p` | 选中所有该类型的 HTML 元素 |
| 类选择器 | `.box` | 选中所有 class 为 box 的元素 |
| ID 选择器 | `#main` | 选中 id 为 main 的唯一元素 |
| 通配选择器 | `*` | 选中所有元素 |

---

## **2. 属性选择器（Attribute Selectors）**

| **写法** | **匹配条件** | **示例** |
| --- | --- | --- |
| `[attr]` | 有这个属性即可 | `[disabled]` 选中所有被禁用的元素 |
| `[attr="val"]` | 属性值等于指定值 | `input[type="button"]` |
| `[attr~="val"]` | 属性值中包含某个 **单词**（空格分隔） | `[class~="active"]` |
| `[attr|="val"]` | 属性值以 val 或 val- 开头（常用于语言）匹配 “en”, “en-US”，不匹配”english” | `[lang|=”en”]` |
| `[attr^="val"]` | 属性值以 val 开头 | `a[href^="https"]` |
| `[attr$="val"]` | 属性值以 val 结尾 | `img[src$=".png"]` |
| `[attr*="val"]` | 属性值中包含 val（任意位置） | `a[href*="example"]` |

---

## **3. 伪类选择器（Pseudo-classes）**

| **名称** | **示例** | **说明** |
| --- | --- | --- |
| `:hover` | `button:hover` | 鼠标悬停时 |
| `:active` | `a:active` | 被点击时 |
| `:focus` | `input:focus` | 获得输入焦点时 |
| `:first-child` | `li:first-child` | 某元素是其父元素的第一个子元素 |
| `:last-child` | `li:last-child` | 某元素是其父元素的最后一个子元素 |
| `:nth-child(n)` | `li:nth-child(2)` | 第 n 个子元素（从 1 开始） |
| `:not(selector)` | `div:not(.disabled)` | 排除某类元素 |
| `:checked` | `input:checked` | 被选中状态（复选框等） |

---

## **4. 伪元素选择器（Pseudo-elements）**

| **名称** | **示例** | **说明** |
| --- | --- | --- |
| `::before` | `p::before` | 在元素内部最前面插入内容 |
| `::after` | `p::after` | 在元素内部最后插入内容 |
| `::first-letter` | `p::first-letter` | 段落首字母 |
| `::first-line` | `p::first-line` | 段落首行 |

伪元素通常需要配合 content 属性使用：

```css
a::after {
  content: " ↗";
}
```

---

## **5. 组合选择器（Combinators）**

| **写法** | **示例** | **含义** |
| --- | --- | --- |
| 后代选择器（空格） | `div p` | 所有 `div` 内的 `p` |
| 子代选择器 > | `ul > li` | 所有 `ul` 的**直接**子元素 `li` |
| 相邻兄弟 + | `h1 + p` | 所有紧跟在 `h1` 后面的 `p` |
| 任意兄弟 ~ | `h1 ~ p` | 所有出现在 `h1` 后的 `p`（不是必须紧挨） |

---

## **6. 分组选择器**

```css
h1, h2, .title {
  font-weight: bold;
}
```

多个选择器共用一组样式，用逗号 , 分隔。

---

## **✅ 推荐使用场景示例**

```css
/* 所有按钮手指光标 */
input[type="button"] {
  cursor: pointer;
}

/* 第一个 dot 特别样式 */
.progress .dot:first-child {
  background-color: red;
}

/* 所有没有 .first 的 .progress */
.progress:not(.first) {
  border-color: gray;
}
```

