# React 状态（state）是否保留的判断规则

### **🔹 核心原则：**

### **相同类型的组件渲染在相同位置，state 会保留**

---

### **✅ 会保留 state 的情况：**

- 组件类型不变（例如 `<Counter />` 仍是 `Counter`）
- 渲染位置不变（在 JSX 树中的相对位置）
- `key` 没有变化
- 父级标签的属性（如 `className`、`id`）发生变化，但不更换标签类型

```js
{isFancy ? <Counter /> : <Counter />} // ✅ 保留 state（位置相同，类型相同）
```

---

### **❌ 不会保留 state 的情况：**

- 更换组件类型（如从 `<Counter />` 变成 `<FancyCounter />`）
- 更换组件位置（如数组渲染中前后调换顺序）
- 添加了新的 `key` 或更改 `key`
- 父标签类型变了（如从 `<div>` 变成 `<section>`）
- 组件被 unmount（如条件渲染中先消失后又出现）

```js
{isFancy ? <Counter /> : <AnotherCounter />} // ❌ 类型不同，state 重置
{show ? <Counter /> : null} // ❌ 被卸载后再挂载，state 重置
```

---

### **🧠 额外说明：**

- React 判断组件是否是“同一个”的依据是：
    - JSX 中的类型
    - 渲染树中的位置
    - （可选）`key` 值
- 所以，只要位置、类型一致，React 会**复用组件实例**，保留 `useState` 的值。

---

### **🔗 官方文档出处：**

[React 官方：State 的保留与重置](https://zh-hans.react.dev/learn/preserving-and-resetting-state#same-component-at-the-same-position-preserves-state)