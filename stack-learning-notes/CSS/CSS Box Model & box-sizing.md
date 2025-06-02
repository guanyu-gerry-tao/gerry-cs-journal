# CSS Box Model & box-sizing

## **🔹 Box Model 构成**

每个 HTML 元素在页面上可以看成是一个矩形盒子，由以下部分组成：

- **content**：实际内容区域，如文字、图片等
- **padding**：内容与边框之间的内边距
- **border**：边框的粗细与样式
- **margin**：元素与其他元素之间的外边距

```
margin
  └── border
        └── padding
              └── content
```

---

## **🔹 box-sizing 属性**

用于定义如何计算元素的总宽高。

### **✅ content-box（默认值）**

- `width` 和 `height` 只包含 content
- `padding` 和 `border` 会另外加上 → 元素会“撑大”

```css
.card {
  width: 100px;
  padding: 10px;
  border: 5px solid black;
  box-sizing: content-box;
}
/* 实际宽度 = 100 + 20 + 10 = 130px 
注意padding和border都是翻倍因为左右各一个 */
```

---

### **✅ border-box（推荐使用）**

- `width` 和 `height` 包含 **content + padding + border**
- 元素总大小就是你设置的宽高

```css
.card {
  width: 100px;
  padding: 10px;
  border: 5px solid black;
  box-sizing: border-box;
}
/* 实际宽度 = 100px，总体不变 
但是内容会被压缩，意味着内容宽度 = 100px - 20px - 10px = 70px */
```

---

## **📌 示例推导**

### **情况：**

```css
.card {
  box-sizing: border-box;
  width: 1000px;
  padding: 100px;
  border: 10px solid black;
}
```

### **计算过程：**

- `padding`: 100px × 2 = 200px
- `border`: 10px × 2 = 20px
- **content 宽度 = 1000 - 200 - 20 = 780px**

---

## **✅ 建议设置**

统一设置全局 box model 更简洁可靠：

```css
* {
  box-sizing: border-box;
}
```

而不是 `box-sizing: content-box;`