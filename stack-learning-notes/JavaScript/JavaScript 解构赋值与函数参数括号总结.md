# JavaScript 解构赋值与函数参数括号总结

## **📌 一、解构赋值（Destructuring Assignment）**

### **🔹 1. 对象解构（使用 `{}`）**

```js
const { top, left } = element.getBoundingClientRect();
```

- 从对象中提取指定属性，按**属性名**赋值
- 等价于：

```js
const rect = element.getBoundingClientRect();
const top = rect.top;
const left = rect.left;
```


👉🏻**用途：简化代码、快速访问对象属性**

---

### **🔹 2. 数组解构（使用 []）**

```jsx
const [x, y] = [10, 20];
```

- 按照**顺序**取值，`x = 10, y = 20`

---

## **📌 二、函数参数使用()括号**

### **🔹 1. 普通参数**

```jsx
array.forEach((item, index) => {
  ...
});
```

- 所有函数参数都放在圆括号 `()` 里，和函数定义语法一致

---

### **🔹 2. 在函数参数中使用解构**

```jsx
array.forEach(({ id, name }) => {
  console.log(id, name);
});

// 等价于：
array.forEach(item => {
	let id = item.id;
	let name = item.name;
	console.log(id, name);
});
```

- 括号中使用解构从参数对象中提取字段
- 注意：**函数参数中用解构时必须加 `()` 包裹起来，即 `({ id, name})`，如果写 `{id, name}` 会报错**

---

## **📌 三、总结对比表**

| **场景** | **写法示例** | **括号类型** | **作用说明** |
| --- | --- | --- | --- |
| 从对象提取属性 | `const { a, b } = obj` | `{}` | 对象解构赋值 |
| 从数组提取值 | `const [x, y] = arr` | `[]` | 数组解构赋值 |
| 函数参数列表 | `(param1, param2) => {}` | `()` | 函数参数语法 |
| 函数参数中使用对象解构 | `({ top, left }) => {}` | `() + {}` | 参数解构 + 函数参数结构 |

---

## **✅ 实用建议记忆：**

> “{} 是解构，() 是函数，解构放函数中就要用两层。”
> 

---

如果你之后看到更复杂的结构（比如嵌套对象、默认值等），欢迎随时继续让我补充进来。要不要我也出两道题帮你练习一下？