# 📍 Position & DOM Coordinate System 笔记总结

## **✅ 一、CSS 中 position: absolute 的核心知识点**

### **1. absolute 定位参考谁？**

- 默认 `position: static` ，根据默认的html排布
- 绝对定位元素（position: absolute）相对于**最近一个有定位的祖先元素**（即设置了 position: relative / absolute / fixed / sticky 的元素）来定位。
- 这意味着如果需要让某个元素可以根据上级元素定位，上级元素必须要设置position，至少不可以是默认的static
- `position: relative` 可以让元素调整自身的位置。例如 `transform: translate (-50%, -50%)` 如果不设置relative则无法生效。此外设置relative可以帮助子元素依照本元素定位（因为至少不是static）。

### **2. 没有定位祖先？**

- 会相对于 `<html>` 元素（即整个页面）定位。

### **✅ 记忆口诀：**

> “absolute 要靠 relative 定位”
> 

---

## **✅ 二、JavaScript 获取坐标方式**

### **1. `e.pageX` / `e.pageY`**

- 鼠标点击点相对于 **整个页面左上角**（含滚动）的坐标。

### **2. `e.clientX` / `e.clientY`**

- 鼠标点击点相对于 **当前视口（viewport）左上角** 的坐标，**不包含滚动偏移。**

### **3. `offsetTop` / `offsetLeft`**

- 当前元素相对于**最近的 offsetParent（有定位属性的祖先元素）**左上角的位置。
- 是一个“**层级内的相对位置**”。

```jsx
const buttonTop = e.target.offsetTop;
const buttonLeft = e.target.offsetLeft;
```

---

### **4. getBoundingClientRect()**

```jsx
const rect = e.target.getBoundingClientRect();
console.log(rect.top, rect.left);
```

- 返回的是一个包含元素边界信息的对象。
- **相对于视口（浏览器可视区域）左上角**。**不包括滚动**
- 包含的属性有：
    - top / left：元素左上角相对视口的位置
    - width / height：元素当前可视宽高（包括缩放、滚动等）
    - bottom / right：元素右下角相对视口位置

---

## **🔍 `offsetTop` 对比 `getBoundingClientRect().top`**

| **属性** | **offsetTop** | **getBoundingClientRect().top** |
| --- | --- | --- |
| 参考点 | offsetParent | 视口（viewport） |
| 精度 | 只支持整型位置 | 返回浮点数（更精准） |
| 推荐用途 | 计算元素内部相对坐标（如放置子元素） | 计算元素是否出现在可视区域中等 |

---

### **✅ 示例：按钮点击效果中用哪个？**

你希望 ripple 动画出现在按钮点击的位置 ——

最推荐组合是：

```jsx
const { top, left } = e.target.getBoundingClientRect();
const xInside = e.clientX - left;
const yInside = e.clientY - top;
```

- clientX 是点击点相对视口位置
- getBoundingClientRect() 给出按钮左上角相对视口位置
- 相减即可得到点击点在按钮内部的精确坐标

---

## **✅ 三、推荐的事件坐标处理方法总结**

| **目标** | **推荐方式** |
| --- | --- |
| 获取点击点在整个页面的位置 | `e.pageX` / `e.pageY` |
| 获取点击点在视口中的位置 | `e.clientX` / `e.clientY` |
| 获取元素在视口中的位置 | `element.getBoundingClientRect()` |
| 获取元素在父级中的位置 | `element.offsetTop` / `offsetLeft` |
| 获取点击点相对元素内部位置 | `clientX - rect.left` / `clientY - rect.top` |
