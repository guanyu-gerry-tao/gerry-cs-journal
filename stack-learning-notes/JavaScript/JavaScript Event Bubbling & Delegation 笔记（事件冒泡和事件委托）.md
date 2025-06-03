# JavaScript Event Bubbling & Delegation 笔记（事件冒泡和事件委托）

# **🧩 1. Event Bubbling（事件冒泡）**

### **✅ 定义**

> 事件从目标元素触发后，会
> 
> 
> **沿着 DOM 树一路向上传播**
> 

### **✅ 过程示意：**

```html
<div id="grandparent">
  <div id="parent">
    <button id="child">Click me</button>
  </div>
</div>
```

点击 `#child` 时触发顺序：

```
#child → #parent → #grandparent → document
```

### **✅ 浏览器默认行为**

- `click`, `input`, `keydown`, `dragover` 等大部分事件都会冒泡
- 特例：`focus`, `blur` 不会冒泡

### **✅ 停止冒泡**

```jsx
e.stopPropagation();  // 阻止事件继续向上传播
```

---

## **🧠 2. Event Delegation（事件委托）**

### **✅ 定义**

> 将子元素的事件监听“委托”给某个祖先元素来统一处理。
> 

### **✅ 依赖机制：**

### **必须依赖事件冒泡**

因为事件最终会“经过”祖先元素，所以祖先可以统一监听。

---

### **✅ 示例：点击列表项**

```html
<ul id="menu">
  <li>Home</li>
  <li>About</li>
</ul>
```

```jsx
document.getElementById('menu').addEventListener('click', e => {
  if (e.target.tagName === 'LI') {
    console.log('Clicked:', e.target.textContent);
  }
});
```

- ✅ 监听器只绑定一次
- ✅ 动态创建的 li 也能监听
- ✅ 性能更优

---

## **🔁 冒泡 vs 委托 对比表**

| **对比点** | **Event Bubbling** | **Event Delegation** |
| --- | --- | --- |
| 是什么 | 浏览器事件传播机制 | 开发者事件处理技巧 |
| 谁触发 | 浏览器自动 | 开发者主动实现 |
| 是否依赖关系 | 本身是机制 | 必须依赖冒泡 |
| 是否自动发生 | ✅ 是 | ❌ 不是（需要代码） |
| 应用目的 | 控制传播、拦截事件 | 优化事件绑定、动态支持 |

---

## **✅ 委托的常见形式**

| **形式** | **说明** |
| --- | --- |
| click, input, submit | 都支持委托 |
| 处理多个子元素类型 | if (e.target.matches(...)) 判断 |
| 支持动态添加的元素 | 只要是祖先都能监听 |
| 封装函数统一管理 | 如 delegateEvent(parent, selector, eventType, handler) |

---

## **❌ 委托限制**

| **情况** | **原因** |
| --- | --- |
| 非祖先节点无法委托 | 不在冒泡路径上 |
| 不冒泡事件不能委托 | 如 focus, blur |
| 兄弟节点之间无法委托 | 无事件传播路径 |

---

## **✅ 判断是否可以委托的规则**

- 事件会不会冒泡？→ 查 MDN 文档
- 委托元素是不是触发元素的祖先？→ 是就可以
- 是否需要捕捉动态元素？→ 用委托更好
