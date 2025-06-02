# 📚 Flex 对齐属性全梳理笔记

## **✅ Flex 是前提条件**

所有的 `justify-*` 和 `align-*` 对齐属性，在 CSS 中**都必须与弹性盒子（flex）或网格布局（grid）配合使用**才能生效。

例如：

```css
.container {
  display: flex; /* 或 grid */
}
```

否则设置 `justify-content`, `align-items` 是**不会有任何效果的**。

---

## **🧭 主轴与交叉轴**

在 Flex 布局中，两个核心方向：

| **概念** | **默认方向** | **控制的对齐维度** | **控制谁** | **意味着** |
| --- | --- | --- | --- | --- |
| 主轴（main axis） | 水平（row） | justify-* 控制主轴 | 控制所有子项 | 控制物体左右排布 |
| 交叉轴（cross axis） | 垂直 | align-* 控制交叉轴 | 控制所有子项或单项 | 控制物体上下对齐 |

👉 `flex-direction: column` 时，主轴会变成垂直，交叉轴变成水平。

---

## **🧩 各类对齐属性汇总表**

| **属性名** | **控制方向** | **控制对象** | **使用条件** | **常见值** | **说明** |
| --- | --- | --- | --- | --- | --- |
| `justify-content` | 主轴 | 子项整体对齐 | flex/grid 容器 | center, space-between | 主轴方向整体布局 |
| `align-items` | 交叉轴 | 所有子项 | flex/grid 容器 | center, flex-start | 所有子项统一对齐 |
| `align-self` | 交叉轴 | **单个子项** | flex/grid 容器 | center, flex-end | 单个子项例外对齐 |
| `align-content` | 交叉轴 | 多行子项整体 | flex-wrap: wrap 时 | center, stretch | 多行内容整体排布 |
| `justify-items` | 主轴 | 所有子项 | 仅 grid | center, start | 控制每个 grid 子项在主轴方向对齐方式 |
| `justify-self` | 主轴 | **单个 grid 子项** | 仅 grid | center, end | 控制某个子项在主轴的对齐 |
| `text-align` | 水平（主轴） | 文本内容 | 任意 block 元素 | left, center, right | 控制文字内容对齐 |
| `vertical-align` | 行内交叉轴 | 行内或表格内容 | 行内元素 | middle, top, bottom | 控制行内元素竖直对齐 |

---

## **✅ 用法小总结**

- 想控制整个子项的**整体位置** ➤ 用 justify-content / align-content
- 想控制所有子项的**对齐方式** ➤ 用 align-items / justify-items
- 想让单个子项行为不同 ➤ 用 align-self / justify-self
- 不是盒子，而是**纯文字**对齐 ➤ 用 text-align（水平）或 vertical-align（垂直）

---

是否需要我将这份笔记转为 Markdown 或直接复制到你 Notion 文档中使用？也可以加上你提供的那张图替换成表格样式展示。

# 举例（全部以`flex-direction: row`为例）：

**justify-content: center**

![image.png](%F0%9F%93%9A%20Flex%20%E5%AF%B9%E9%BD%90%E5%B1%9E%E6%80%A7%E5%85%A8%E6%A2%B3%E7%90%86%E7%AC%94%E8%AE%B0%201ff03e65cf6980abafa7f22556d16ec3/image.png)

**justify-content: space-between**

![image.png](%F0%9F%93%9A%20Flex%20%E5%AF%B9%E9%BD%90%E5%B1%9E%E6%80%A7%E5%85%A8%E6%A2%B3%E7%90%86%E7%AC%94%E8%AE%B0%201ff03e65cf6980abafa7f22556d16ec3/image%201.png)

**justify-content: space-around**

![image.png](%F0%9F%93%9A%20Flex%20%E5%AF%B9%E9%BD%90%E5%B1%9E%E6%80%A7%E5%85%A8%E6%A2%B3%E7%90%86%E7%AC%94%E8%AE%B0%201ff03e65cf6980abafa7f22556d16ec3/image%202.png)

**justify-content: space-evenly**

![image.png](%F0%9F%93%9A%20Flex%20%E5%AF%B9%E9%BD%90%E5%B1%9E%E6%80%A7%E5%85%A8%E6%A2%B3%E7%90%86%E7%AC%94%E8%AE%B0%201ff03e65cf6980abafa7f22556d16ec3/image%203.png)

**align-items: center**

![image.png](%F0%9F%93%9A%20Flex%20%E5%AF%B9%E9%BD%90%E5%B1%9E%E6%80%A7%E5%85%A8%E6%A2%B3%E7%90%86%E7%AC%94%E8%AE%B0%201ff03e65cf6980abafa7f22556d16ec3/image%204.png)

**align-self: flex-start / flex-end**

![image.png](%F0%9F%93%9A%20Flex%20%E5%AF%B9%E9%BD%90%E5%B1%9E%E6%80%A7%E5%85%A8%E6%A2%B3%E7%90%86%E7%AC%94%E8%AE%B0%201ff03e65cf6980abafa7f22556d16ec3/image%205.png)

**align-content: space-around (wrap 多行)**

![image.png](%F0%9F%93%9A%20Flex%20%E5%AF%B9%E9%BD%90%E5%B1%9E%E6%80%A7%E5%85%A8%E6%A2%B3%E7%90%86%E7%AC%94%E8%AE%B0%201ff03e65cf6980abafa7f22556d16ec3/image%206.png)

**justify-items: center (grid)**

![image.png](%F0%9F%93%9A%20Flex%20%E5%AF%B9%E9%BD%90%E5%B1%9E%E6%80%A7%E5%85%A8%E6%A2%B3%E7%90%86%E7%AC%94%E8%AE%B0%201ff03e65cf6980abafa7f22556d16ec3/image%207.png)

**justify-items: start/end (grid)**

![image.png](%F0%9F%93%9A%20Flex%20%E5%AF%B9%E9%BD%90%E5%B1%9E%E6%80%A7%E5%85%A8%E6%A2%B3%E7%90%86%E7%AC%94%E8%AE%B0%201ff03e65cf6980abafa7f22556d16ec3/image%208.png)

**text-align: center**

![image.png](%F0%9F%93%9A%20Flex%20%E5%AF%B9%E9%BD%90%E5%B1%9E%E6%80%A7%E5%85%A8%E6%A2%B3%E7%90%86%E7%AC%94%E8%AE%B0%201ff03e65cf6980abafa7f22556d16ec3/image%209.png)

**text-align: left**

![image.png](%F0%9F%93%9A%20Flex%20%E5%AF%B9%E9%BD%90%E5%B1%9E%E6%80%A7%E5%85%A8%E6%A2%B3%E7%90%86%E7%AC%94%E8%AE%B0%201ff03e65cf6980abafa7f22556d16ec3/image%2010.png)

**text-align: justify**

![image.png](%F0%9F%93%9A%20Flex%20%E5%AF%B9%E9%BD%90%E5%B1%9E%E6%80%A7%E5%85%A8%E6%A2%B3%E7%90%86%E7%AC%94%E8%AE%B0%201ff03e65cf6980abafa7f22556d16ec3/image%2011.png)

控制text上下对齐，父级使用align-content

**vertical-align: top/middle/bottom**

![image.png](%F0%9F%93%9A%20Flex%20%E5%AF%B9%E9%BD%90%E5%B1%9E%E6%80%A7%E5%85%A8%E6%A2%B3%E7%90%86%E7%AC%94%E8%AE%B0%201ff03e65cf6980abafa7f22556d16ec3/image%2012.png)

![image.png](%F0%9F%93%9A%20Flex%20%E5%AF%B9%E9%BD%90%E5%B1%9E%E6%80%A7%E5%85%A8%E6%A2%B3%E7%90%86%E7%AC%94%E8%AE%B0%201ff03e65cf6980abafa7f22556d16ec3/image%2013.png)