# CSS 伪元素笔记（Pseudo-elements）

> 官方文档参考 - MDN

---

## **✅ 什么是伪元素？**

> 伪元素是 CSS 提供的机制，允许你
> **选中 HTML 元素的一部分或“创造”虚拟内容节点**

---

## **✅ 基本语法**

```css
selector::pseudo-element {
  property: value;
}
```

- 使用两个冒号 ::
- 部分老式浏览器仍支持 :before、:after（一个冒号）

---

## **📌 常见伪元素一览**

| **伪元素** | **作用** |
| --- | --- |
| `::before` | 在元素开头插入内容 |
| `::after` | 在元素末尾插入内容 |
| `::first-letter` | 选中首字母 |
| `::first-line` | 选中第一行文字 |
| `::placeholder` | 针对 input 的 placeholder 文本样式 |
| `::selection` | 选中文本的高亮样式 |

---

## **🧪 示例笔记**

---

### **1. `::before` & `::after`**

用于在元素前后添加装饰性内容（**必须加 content**）。

```css
button::after {
  content: ' →';
  color: gray;
}
```

```css
<button>Next</button>
<!-- 实际显示：Next → -->
```

```css
a::before {
  content: '🔗';
  margin-right: 5px;
}
```

---

### **2. `::first-letter`**

选择段落的第一个字母，适合做装饰性首字设计。

```css
p::first-letter {
  font-size: 200%;
  color: red;
}
```

---

### **3. `::first-line`**

给段落的**第一行文字**加样式。

```css
p::first-line {
  font-weight: bold;
  color: blue;
}
```

---

### **4. `::placeholder`**

针对 `<input>` 或 `<textarea>` 的 placeholder 字体样式。

```css
input::placeholder {
  color: gray;
  font-style: italic;
}
```

---

### **5. `::selection`**

用户**选中文本时**的高亮颜色。

```css
::selection {
  background: yellow;
  color: black;
}
```

---

## **🎯 使用注意：**

- ::before 和 ::after 不会出现在 DOM 中，**JavaScript 无法直接选中**
- 只能用于块级或行内元素，不能用于 `<img>`、`<input type="text">` 等无内容元素
- content 是 ::before / ::after **必须**设置的属性，否则无效果

---

## **✅ 常见用途总结**

| **用法** | **伪元素** |
| --- | --- |
| 添加装饰箭头、符号 | ::before, ::after |
| 文章首字大写 | ::first-letter |
| 引导用户注意首行 | ::first-line |
| 自定义输入提示样式 | ::placeholder |
| 改变文字选中颜色 | ::selection |