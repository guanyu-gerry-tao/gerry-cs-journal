# 📌 React 中的副作用（Side Effects）  

## 🧠 什么是副作用？  

> **副作用** 是指在函数执行过程中，访问或修改了函数作用域外的事物。

### ✅ 常见副作用包括：

- 操作 DOM
    例如：`ref.current.play()`、`document.title = "..."`
- 发起网络请求
    例如：`fetch('/api')`
- 设置定时器
    例如：`setTimeout`, `setInterval`
- 日志、全局变量修改
    例如：`console.log()`, `window.count++`

---

## 🎯 React 为什么限制副作用？

React 的组件函数应该是：
- **纯函数**（pure function）：不产生副作用
- 每次调用只负责“生成 JSX”，不能影响外部状态或环境  

这样可以保证：
- 渲染结果可预测
- 性能优化容易（如跳过渲染、并发渲染）

---

## ❌ 错误示例（在组件函数中直接操作 DOM）

```jsx
function VideoPlayer({ isPlaying }) {
  const ref = useRef();
  if (isPlaying) {
    ref.current.play(); // ❌ 副作用：不能在这里操作 DOM
  }
  return <video ref={ref} />;
}
```

---

## ✅ 正确做法：使用 `useEffect`

  

> useEffect 是 React 提供的用于执行副作用的 Hook。  
> 它在组件渲染完成、DOM 已挂载之后运行。

```jsx
function VideoPlayer({ isPlaying }) {
  const ref = useRef();

  useEffect(() => {
    if (isPlaying) {
      ref.current?.play();
    } else {
      ref.current?.pause();
    }
  }, [isPlaying]); // ✅ 依赖于 isPlaying

  return <video ref={ref} />;
}
```

---

> [!NOTE]
> - **副作用 = 改变外部世界的行为**
> - React 不允许在组件函数中执行副作用
> - 副作用必须放到 useEffect() 中处理