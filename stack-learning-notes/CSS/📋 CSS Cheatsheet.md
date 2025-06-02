# 📋 CSS Cheatsheet

```css
selector {
  property: value;
}
```

## **🎨 颜色与文本**

### **颜色**

```css
color: red; /* 文本颜色 */
background-color: #f0f0f0; /* 背景颜色 */
opacity: 0.5; /* 透明度 */
```

### **字体与排版**

```css
font-family: 'Arial', sans-serif;
font-size: 16px;
font-weight: bold; /* normal, bold, 100–900 */
line-height: 1.5;
text-align: center; /* left, right, center, justify */
text-decoration: underline; /* none, underline, line-through */
text-transform: uppercase; /* capitalize, lowercase */
letter-spacing: 1px;
word-spacing: 2px;
```

---

## **📐 盒模型（Box Model）**

### **尺寸**

```css
width: 100px;
height: 200px;
max-width: 100%;
```

### **边距与内边距**

```css
margin: 10px; /* 外边距 */
padding: 20px; /* 内边距 */
```

### **边框**

```css
border: 1px solid black;
border-radius: 10px; /* 圆角 */
```

---

## **📦 布局**

### **Display（显示类型）**

```css
display: block; /* 默认块级元素 */
display: inline;
display: inline-block;
display: flex;
display: grid;
display: none;
```

### **Flexbox**

display: flex; 是一种一维布局方式，让元素在**横轴或纵轴上**灵活排列。

```css
display: flex;
flex-direction: row;        /* 横向（默认） */
justify-content: center;    /* 主轴对齐：左中右/间距 */
align-items: center;        /* 交叉轴对齐：上中下 */
gap: 10px;                  /* 子元素间距 */
```

```css
flex: 1;                    /* 占满剩余空间 */
align-self: flex-start;     /* 单独控制对齐方式 */
```

示例：

```css
.container {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
```

实例：导航栏，卡片排布，响应式布局

### **Grid**

```css
display: grid;
grid-template-columns: repeat(3, 1fr);
grid-gap: 10px;
```

---

## **📍 定位**

```css
position: static; /* 默认 */
position: relative;
position: absolute;
position: fixed;
position: sticky;

top: 10px;
left: 20px;
z-index: 100;
```

---

## **🌀 其他常用属性**

### **背景**

```css
background-image: url('img.jpg');
background-size: cover;
background-position: center;
background-repeat: no-repeat;
```

### **阴影**

```css
box-shadow: 2px 2px 5px rgba(0,0,0,0.3);
text-shadow: 1px 1px 3px gray;
```

### **溢出与滚动**

当元素内容超出容器尺寸时，CSS 提供 overflow 属性控制是**截断、滚动、还是显示出来**。

```css
white-space: nowrap; /* 不换行 */

overflow: visible;   /* 默认，超出内容会显示 */
overflow: hidden;    /* 超出内容被裁剪，不显示 */
overflow: scroll;    /* 总是显示滚动条 */
overflow: auto;      /* 内容超出时才显示滚动条（最常用） */
```

### **过渡与动画**

```css
transition: all 0.3s ease-in-out;

@keyframes fadeIn {
  from { opacity: 0; }
  to { opacity: 1; }
}

animation: fadeIn 1s ease-in;
```

---

## **✏️ 媒体查询（响应式设计）**

```css
@media (max-width: 768px) {
  body {
    font-size: 14px;
  }
}
```

---

## **📚 选择器总结**

```css
/* ID 和类选择器 */
#idName { }
.className { }

/* 子元素与后代 */
.parent > .child { }
.parent .descendant { }

/* 属性选择器 */
input[type="text"] { }

/* 伪类和伪元素 */
a:hover { }        /* 鼠标悬停 */
input:focus { }    /* 聚焦 */
li:first-child { }
p::before { content: "→ "; }
```

