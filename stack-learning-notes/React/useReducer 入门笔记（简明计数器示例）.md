# useReducer 入门笔记（简明计数器示例）

### **背景**

`useReducer(reducer, initialState)` 是 React 提供的用于管理复杂组件状态的 Hook。相比 `useState`，它更适用于多种操作都需要更新同一状态的情况。

---

### **✅ 完整代码**

```jsx
import { useReducer } from 'react';

function reducer(state, action) { // 这里必须要两个参数，第一个传入当前状态，第二个传入一个叫action的参数，里面存储了动作类型。
  switch (action.type) { //action.type表明用户做了什么
    case 'increment':
      return { count: state.count + 1 };
    case 'decrement':
      return { count: state.count - 1 };
    default:
      throw new Error('Unknown action: ' + action.type);
  }
}

export default function CounterApp() {
  const [state, dispatch] = useReducer(reducer, { count: 0 });
// 上一行里，解构出了state, dispatch
// state是当下snapshot的状态，也就是“被更新”的状态
// dispatch是一个方法，用这个方法传入对象，包含type和其他需要的参数（在这里没传入其它参数）
// dispatch传入的参数会被送到action中，其中dispatch里传入的对象里的type会变成action.type

  return (
	  <>
	    <h1>Count: {state.count}</h1>
	    <button onClick={() => dispatch({ type: 'increment' })}>
	      +1  
	    </button>
	    <button onClick={() => dispatch({ type: 'decrement' })}>
	      -1
	    </button>
	  </>
  );
}
```

---

### **🧩 核心组成**

### **1. `useReducer(reducer, initialState)`**

- `reducer`：一个纯函数，接收 `(state, action)` 并返回新的 state
- `initialState`：初始状态对象（例子中为 `{ count: 0 }`）
- 返回值是一个数组 `[state, dispatch]`

### **2. `state`**

- 当前的状态值（对象）
- 在 CounterApp 中 `state.count` 是我们需要显示的数字

### **3. `dispatch(action)`**

- 用于触发 `reducer` 中的相应逻辑
- `action` 必须是一个对象，通常带有 `type` 字段（可以有其他字段）

### **4. `reducer(state, action)`**

- 根据 `action.type` 决定如何更新状态
- 每个分支返回一个新的状态对象（不能修改原状态）

---

### **🧭 使用场景建议**

- 状态逻辑复杂（多分支判断）
- 同一个状态受多个事件影响
- 多个子组件共享更新逻辑

---

### **📌 总结**

| **`useState`** | **`useReducer`** |
| --- | --- |
| 适用于简单状态 | 适用于复杂或可组合的状态 |
| 设置函数直接更新 | `dispatch` 事件让 `reducer` 处理 |
| 无需定义 `reducer` | 需定义 `reducer` 函数 |

---

📖 官方教程：[React 中文文档 - useReducer](https://zh-hans.react.dev/learn/extracting-state-logic-into-a-reducer)