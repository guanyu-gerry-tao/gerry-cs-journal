# React Refs 学习笔记  

## 📌 什么是 Ref？

- Ref（Reference）是 React 提供的一种机制，用来**访问 DOM 元素或组件实例**。
- 用于存储不随渲染周期变化的**可变值**。

---

## 🧱 创建 Ref

```jsx
import { useRef } from 'react';

const myRef = useRef(null);
```

- initialValue 通常是 null（DOM）。
- 返回值是一个 **ref 对象**：`{ current: value }`

---

## 📍 使用场景一：访问 DOM 元素

```jsx
import { useRef } from 'react';

export default function MyComponent() {
  const inputRef = useRef(null); // 这里定义inputRef

  function handleClick() {
    // 当点击按钮时，让 input 聚焦
    inputRef.current.focus();
  }

  return (
    <>
      <input ref={inputRef} /> // 这里将ref指向inputRef，在前面我们定义了它
      <button onClick={handleClick}>点击聚焦输入框</button>
    </>
  );
}
```

- ref.current 会指向 `<input>` 元素。
- 可用来控制焦点、滚动、测量尺寸等。
- 这里 `ref={}` 中，`ref` 是 React 引入的特殊的参数。
    - `{}` 这里是因为在 React 组件的 return 中，需要用 `{}` 来表示这是一个对象：`inputRef`
    - `inputRef` 是一个对象，他有一个这里提到的 `current` 属性，对应的指是使用 `ref={}` 的DOM，也就是这里的 `<input>`

---

## 📍 使用场景二：保存可变值（但不引发重渲染）

```jsx
const countRef = useRef(0);

function handleClick() {
  countRef.current++;
  console.log(countRef.current); // 不会引起 UI 更新
}
```

与 `useState` 不同，`useRef` 的变更不会触发组件重新渲染。

### 有什么用？

- 避免频繁更新数据，`useState` 疯狂重渲染影响性能：例如计时器
- 存储副作用，因为 `useState` 会在重渲染后将数据清空
- 纯逻辑用途，去除 `useState` 的重渲染的步骤

---

## 📍 使用场景三：保持上一次的值

```jsx
const prevCount = useRef(count);
useEffect(() => {
  prevCount.current = count;
}, [count]);
```

- `prevCount.current` 总是保存上一个渲染周期的 count 值。

---

## 🔧 操作 DOM 的方式（举例）

### 1. 设置焦点

```jsx
inputRef.current.focus();
```

### 2. 滚动到某个元素

```jsx
elementRef.current.scrollIntoView({ behavior: 'smooth' });
```

### 3. 测量尺寸

```jsx
const height = elementRef.current.getBoundingClientRect().height;
```

---

## ❗使用注意

- 不要滥用 ref 修改 DOM 状态，**优先使用 state 进行数据驱动渲染**。
- ref 适用于：
    - 管理焦点
    - 动画控制
    - 与第三方 DOM 库交互
- 不建议用于**读取或写入组件内部状态**