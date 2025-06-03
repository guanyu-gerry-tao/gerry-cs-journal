# React useState 与 setState 函数详解笔记（含批处理陷阱）

## **🔰 1. `useState()` 是 React 的状态 Hook**

```jsx
const [state, setState] = useState(initialValue);
```

- `state` 是当前状态值
- `setState` 是用来更新该状态的函数（由 React 内部生成）
- `initialValue` 是初始值，只在首次渲染中使用

---

## **⚠️ 2. 你命名的 `setState`（如 `setScore`）不是 React 全局内置函数，而是你通过解构命名的**

```jsx
const [score, setScore] = useState(0);
```

- 你可以命名为任意变量名：

```jsx
const [banana, setBanana] = useState(0);
```

- React 内部始终会返回 [值, 更新函数]

---

## **⚙️ 3. setState() 的行为：异步 & 批处理**

- 它不会**立刻更新** `state`，而是**安排一次异步更新**
- 多次调用 `setState(value)`，React 可能**批处理合并为一次**
- 所以你不能期望在当前函数里立即看到新值！

---

## **🧪 4. 示例说明：为什么多次 `increment()` 没有用？**

### **错误代码：**

```jsx
function increment() {
  setScore(score + 1);
}

<button onClick={() => {
  increment();
  increment();
  increment();
}}>+3</button>
```

**你以为结果是 score + 3，但实际只加了 1！**

### **❓原因：**

- score + 1 是在**当前函数作用域中计算的值**
- 三次调用都使用了**相同的 score 值**（比如都是 0）
- 所以三次 `setScore(score + 1)` 都是 `setScore(1)`
- React 批处理后，只保留最后一次 → score = 1

---

## **✅ 正确写法：使用函数式更新**

```jsx
setScore(prev => prev + 1);
```

这样每次递增都以“最新的 state”为基础。

### **修复后的 +3 按钮：**

```jsx
<button onClick={() => {
  setScore(s => s + 1);
  setScore(s => s + 1);
  setScore(s => s + 1);
}}>+3</button>
```

- 每次都基于上一次的 score 值进行更新
- 所以最终结果是真正地 +3

---

## **✅ 总结对比**

| **写法** | **是否安全** | **说明** |
| --- | --- | --- |
| `setScore(score + 1)` | ❌ 不安全 | 多次更新时可能重复引用旧值 |
| `setScore(s => s + 1)` | ✅ 安全 | 每次以最新值为基础计算 |

---

## **🧠 一句话总结：**

> `setScore(score + 1)` 使用的是当前作用域的旧值，不适合连续调用；
> 

> 要想确保每次都基于“最新的状态值”，应使用 setScore(prev => prev + 1) —— 这就是函数式更新，它能避免状态闭包带来的 bug，是 React 推荐的写法。
>