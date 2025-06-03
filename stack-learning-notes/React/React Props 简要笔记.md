# React Props 简要笔记

## **✅ 什么是 Props？**

- Props（全称：**properties**）是 React 组件的**输入参数**
- 用于**父组件向子组件传递数据**
- 是**只读的对象**（组件不能修改收到的 props）

---

## **🧩 如何使用 Props？**

### **父组件传值：**

```jsx
<Card name="hello" />
```

### **子组件接收并使用：**

```jsx
function Card(props) {
  return <p>{props.name}</p>;
}
```

或使用解构写法更简洁：

```jsx
function Card({ name }) {
  return <p>{name}</p>;
}
```

---

## **🎯 特点总结**

- props 是单向数据流（从父 → 子）
- 可以传递任意类型的数据（字符串、数值、函数、JSX 等）
- 子组件只能读取，**不能修改 props 本身**

---

## **✅ 示例输出**

```jsx
<Card name="React" />
```

```jsx
<p>React</p>
```

---

需要我扩展一个含样式与多个 props 的实战版 Card 组件吗？

## **✅ 核心思路**

- 子组件**不能直接修改**父组件的数据
- 但父组件可以把一个函数通过 **props** 传给子组件
- 子组件调用这个函数，**父组件就会响应**

---

## **📌 父组件传递一个函数**

```jsx
function App() {
  const handleMessage = (msg) => {
    console.log("子组件说：", msg)
  }

  return <Card onSend={handleMessage} />
}
```

- handleMessage 是父组件定义的函数
- 通过 prop onSend 传给子组件

---

## **📌 子组件调用这个函数**

```jsx
function Card({ onSend }) {
  return (
    <button onClick={() => onSend("hello from Card")}>
      Click to Send
    </button>
  )
}
```

- 点击按钮时调用 `onSend("...")`
- 实际上执行的是父组件的 `handleMessage()` 函数