# JavaScript 常见写法 / 语法结构总览

## **✅ 1. 普通函数定义**

```js
function sayHello(name) {
  console.log("Hello, " + name);
}
```

---

## **✅ 2. 函数表达式（匿名函数赋值给变量）**

```js
const sayHi = function(name) {
  console.log("Hi, " + name);
};
```

- 通常用于作为回调或参数传入
- 可以形成闭包

---

## **✅ 3. 箭头函数（简写，不绑定 this）**

```js
const greet = (name) => {
  console.log("Hello, " + name);
};
```

- 简洁
- 常用于回调
- 不建议在需要 this 的地方使用（如构造函数）

---

## **✅ 4. 立即执行函数表达式（IIFE）**

```js
(function(name) {
  console.log("Welcome, " + name);
})("Alice");
```

- 函数定义完立刻执行
- 用来创建临时作用域
- 常用于闭包隔离变量

---

## **✅ 5. forEach回调函数三参数**

```js
array.forEach((element, index, array) => {
  console.log(index, element);
});
```

- 第一个是当前元素
- 第二个是索引
- 第三个是原始数组本身

---

## **✅ 6. addEventListener 回调绑定（推荐方式）**

```js
button.addEventListener("click", () => {
  console.log("Clicked!");
});
```

- 比行内 onclick="..." 更专业
- 支持多个绑定、解绑、结构更清晰

---

## **✅ 7. setTimeout 结合闭包的错误用法（共享变量）**

```js
for (var i = 0; i < 3; i++) {
  setTimeout(() => {
    console.log(i); // ❌ 全部输出 3
  }, 1000);
}
```

---

## **✅ 8. 正确写法： let 或 IIFE**

```js
// 使用 let
for (let i = 0; i < 3; i++) {
  setTimeout(() => {
    console.log(i); // ✅ 输出 0, 1, 2
  }, 1000);
}

// 或使用 IIFE
for (var i = 0; i < 3; i++) {
  (function(j) {
    setTimeout(() => {
      console.log(j);
    }, 1000);
  })(i);
}
```

---

## **✅ 9. 匿名函数作为事件回调（函数表达式）**

```js
element.onfocus = function() {
  showHelp("Focused!");
};
```

---

## **✅ 10. 用 .classList 操作 class 的简洁写法**

```js
element.classList.add('active');
element.classList.remove('hidden');
element.classList.toggle('expanded');
```

- 更安全灵活，替代 element.className = ...

---

## **✅ 11. querySelector vs getElementById**

```js
document.querySelector("#id");         // 推荐：CSS 选择器通用写法
document.getElementById("id");         // 仅用于查找 ID
```

- querySelector 支持所有 CSS 选择器，如 `.class`, `[attr]`, `div` `span`

---

## **✅ 12. 设置元素内容**

```jsx
element.textContent = "Hello";  // 设置纯文本
element.innerHTML = "<b>Hello</b>";  // 设置 HTML 内容
```

---

## **✅ 13. 清空类名（不推荐的写法）**

```jsx
element.classList.value = "";  // ❌ 不规范
element.className = "";        // ✅ 正确
```

---

## **🧠 总结：掌握这些结构，就掌握了现代 JavaScript 的基础构建单元。**
