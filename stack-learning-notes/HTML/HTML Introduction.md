# HTML Introduction

HTML example

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>Sample Page</title>
  </head>
  <body>
    <p>Example paragraph</p>
    <!-- this is a comment -->
  </body>
</html>
```

`<!DOCTYPE html>` Declaration tag represents document type, instruct browser about version, and should be the first line of HTML code

`<html>` is root of tree, contain all HTML element except document type `<!DOCTYPE html>`.

`<head>`elements contains:

- title`<title>`
- scripts`<script>`
- style`<style>`
- style sheet links`<link>`
- meta information`<meta>`
- browser support information, other initialization functions`<base>`

# DOM

DOM = Document Object Model

![image.png](%F0%9F%93%9D%20HTML%20Introduction%201f603e65cf698030bb80de85164a41bc/image.png)

**DOM（文档对象模型）** 是浏览器在加载网页时，**将 HTML 文档转化成的树状结构**，这个结构中的每个节点（Node）代表页面上的一个元素（Element）、属性（Attribute）或文本（Text）等。

- 它是 JavaScript 和网页之间沟通的桥梁。
- 页面一旦加载，JavaScript 就可以通过 DOM 来**读取、修改、添加或删除页面内容**。

# DOM Accessors

**DOM Accessors（DOM访问器）** 是**JavaScript 提供的接口函数或属性，用于访问和操作 DOM 元素**。

- 它们就是你访问 DOM 树的“钥匙”。
- 例如：document.getElementById("greeting") 就是一个访问器，用来访问 ID 为 greeting 的节点。
- 只在浏览器环境运行，使用JS语言。（Node.js因此无法运行DOM accessors）

# XML

example

```xml
<?xml version="1.0" encoding="UTF-8"?>
<html xmlns="https://www.w3.org/1999/xhtml">
  <head>
    <meta http-equiv="Content-Type" content="application/xhtml+xml; charset=ISO-8859-1" />
    <title>Example document</title>
  </head>
  <body>
    <p>Example paragraph</p>
  </body>
</html>
```

`<!xml version="1.0" encoding="UTF-8"?>` makes it XML rather than HTML

Besides,

`<meta http-equiv="Content-Type" content="application/xhtml+xml; charset=ISO-8859-1" />`
 is required 

# XML vs HTML

| XML = XHTML | HTML |
| --- | --- |
| Tags need to be lowercase | Doesn’t matter |
| Codes must be well-formed | Unmatched quotation marks OK 
引号不匹配OK
Non-terminated OK
标签没闭合OK
Uncontained element OK
不合理嵌套OK |
| XML parser stop processing when syntax wrong | Syntax is less rigorous |

## **Sandboxing (HTML5 Feature)**

- **Sandboxed browsing context**:
    - Applies extra restrictions to **untrusted content**
    - Used with embedded content (like `<iframe>`)

- Adding sandbox attribute:
	- Prevents third-party content from having same permissions as host page
	- Helps avoid **unintended ad scripts** or malicious behavior

## **Document Object Model (DOM)**

- Every HTML page becomes a **Document object**
- DOM provides **access to all HTML elements**

### **DOM Tree Accessors (常用 DOM 访问器)**

| **DOM API**      | **Description**                 |
| ---------------- | ------------------------------- |
| document.head    | Returns the `<head>` element    |
| document.images  | Returns all `<img>` elements      |
| document.scripts | Returns all `<script>` elements |

## Common DOM Methods

- document.getElementById(id)
    - Returns the element with a specific id
- document.getElementsByTagName(tag)
    - Returns **all elements** with the given tag (as a NodeList)

```html
<script type="text/javascript">
  function textChecker() {
    let input = document.getElementById('textField1').value;
    if (input) {
      alert("You typed: " + input);
    } else {
      alert("Please enter something!");
    }
  }
</script>
<body>
  <input type='text' id='textField1'>
  <input type='button' onClick='textChecker()' value='Submit'>
</body>
```

### **Explanation:**

- Gets input field content using getElementById
- Stores it in a variable
- Displays result in an **alert dialog**

# Check if Browser support one feature

```jsx
var input = document.createElement('input');
input.setAttribute('type', 'date');

if (input.type === 'date') {
  console.log('This browser supports input type="date"');
} else {
  console.log('input type="date" is not supported, using fallback.');
}
```

即使浏览器**不支持** type="date"，它仍然能创建一个 `<input>` 标签对象。

但它会**自动回退**成 type="text"。

所以你可以通过检查 .type 属性值是否真的为 'date' 来判断浏览器是否支持这个类型

# Web workers

在 HTML5 中，**Web Workers** 是一种在后台线程中运行 JavaScript 脚本的机制。它的最大特点就是：

> 可以在不阻塞主线程（UI线程）的情况下执行密集的计算任务。
> 

也就是说，Web Workers 允许你“在后台工作”，不会让页面卡顿或界面冻结。

# Structural elements

指语义标签，如 `<header>`、`<section>`，与性能无关

# Elements

元素是 HTML 的实际构建单位（包含标签+内容）

# Nodes

节点是 DOM 的术语，HTML 的“构建块”应该叫元素

# 语义，结构化

**结构化**指的是：用标签（tags）把网页内容划分为不同的区域或块（block），像在写文档或做演示时给内容分章节一样。

比如你写一个网页，有这些部分：

- 页眉（Header）
- 主体内容（Main content）
- 页脚（Footer）
- 侧边栏（Sidebar）
- 导航栏（Navigation）

这些内容是网页的“**结构**”，你需要告诉浏览器（也告诉人和搜索引擎）哪一块是干什么用的。

先结构化再语义化

语义（Semantic）指的是：**标签本身有含义**，能表达出它里面的内容是什么类型、起什么作用。

| **标签**      | **语义性强吗？** | **说明**               |
| ----------- | ---------- | -------------------- |
| `<div>`     | ❌ 没有语义     | 只是一个普通容器，没有告诉我们里面是什么 |
| `<header>`  | ✅ 有语义      | 明确告诉我们：这里是页面的头部内容    |
| `<nav>`     | ✅ 有语义      | 表示这是导航区域，里面是链接       |
| `<article>` | ✅ 有语义      | 表示是独立的一篇文章、帖子、新闻等    |

| **概念** | **含义** | **举例** |
| --- | --- | --- |
| 结构化 | 把页面分成不同区域 | 用 `<div>` 或 `<section>` 把内容分块 |
| 语义化 | 用有意义的标签表达内容的角色 | 用 `<header>`、`<nav>`、`<article>` 而不是 `<div>` |

先结构化再语义化的例子：

```html
<!-- 结构化但不语义化 -->
<div class="header">...</div>
<div class="nav">...</div>
<div class="content">...</div>
<div class="footer">...</div>
```

```html
<!-- 结构化 + 语义化 -->
<header>...</header>
<nav>...</nav>
<main>...</main>
<footer>...</footer>
```

# Tags

标签只是构建元素的“语法”部分，不是构建块本身

# Sandbox

是一个属性，给iframe使用的时候，会加上一组严格的安全限制，避免嵌入内容造成威胁

sandbox 是 HTML5 引入的，用于给 iframe 加沙盒（sandbox），让它**运行在一个受限的环境中**，从而防止：

- 跨站脚本攻击（XSS）
- 恶意代码访问主页面的数据
- 自动跳转
- 表单提交
- 弹窗骚扰

```jsx
<iframe src="https://example.com" sandbox></iframe>
```

sandbox 可以带一些关键词，允许部分功能：

```jsx
<iframe src="https://example.com" sandbox="allow-scripts allow-forms"></iframe>
```

| **属性值** | **作用说明** |
| --- | --- |
| allow-scripts | 允许运行 JavaScript 脚本 |
| allow-forms | 允许提交表单 |
| allow-same-origin | 允许被嵌页面视为“同源” |
| allow-popups | 允许打开新窗口（如通过 window.open） |
| allow-modals | 允许使用 alert()、prompt() 等弹窗函数 |