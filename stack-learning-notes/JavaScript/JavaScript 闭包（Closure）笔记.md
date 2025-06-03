# JavaScript 闭包（Closure）笔记

[👉 MDN 官方文档（中文）](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Guide/Closures)

---

## **✅ 闭包到底是什么？**

> 闭包是
> **函数 + 它定义时的变量环境**

> 意思是：
> **函数记住了它当时可以访问的外部变量**
> 
---

## **✅ 最简单例子**

```js
function outer() {
  let message = "hello";
  return function inner() {
    console.log(message);
  };
}

const fn = outer(); // outer 执行完了，message 理论上应该没了
fn(); // 但还能打印 "hello"！说明 message 被“闭”住了
```

---

## **✅ 闭包的典型用途：记住状态**

```js
function createCounter() {
  let count = 0;
  return function () {
    count++;
    console.log(count);
  };
}

const counter = createCounter();
counter(); // 1
counter(); // 2
counter(); // 3
```

这个 count 外面访问不到，但 counter 内部的闭包函数可以一直访问！

---

## **❗ 经典闭包“陷阱”问题**

```js
for (var i = 0; i < 3; i++) {
  setTimeout(() => {
    console.log(i);
  }, 1000);
}
```

你以为输出是：

```js
0
1
2
```

但实际输出是：

```js
3
3
3
```

---

## **🔍 为什么？因为**

## **var**

## **是函数作用域，而且有声明提升**

### **这段代码等价于这样：**

```js
var i;
for (i = 0; i < 3; i++) {
  setTimeout(() => {
    console.log(i);
  }, 1000);
}
```

- 所有 `setTimeout` 闭包都引用了**同一个变量 i**
- 当 1 秒后函数运行时，循环已经结束，`i === 3`

---

## **✅ 正确写法一：用**

## **let（每次循环都是新的变量）**

```js
for (let i = 0; i < 3; i++) {
  setTimeout(() => {
    console.log(i); // 输出 0, 1, 2
  }, 1000);
}
```

- `let` 是**块级作用域**
- 每次循环都生成一个新的 i，闭包各自记住自己的那个版本

---

## **✅ 正确写法二（IIFE）：**

```js
for (var i = 0; i < 3; i++) {
  (function(j) {
    setTimeout(() => {
      console.log(j);
    }, 1000);
  })(i);
}
```

---

## **✅ 总结口诀**

| **点** | **记住这句话** |
| --- | --- |
| 闭包是什么 | 函数记住了定义时的作用域变量 |
| var 的作用域 | 整个函数通用，循环里也是一个变量 |
| 常见错误 | 多个闭包共享同一个 var，就会一起输出同一个值 |
| 正确做法 | 用 let、或 IIFE 创建独立作用域 |