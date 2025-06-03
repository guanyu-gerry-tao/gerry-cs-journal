# React 中的 Mutation, immer 与不可变更新（Immutable Update）笔记

## **1. 什么是 Mutation？**

> Mutation
> 

### **✅ 举例（数组与对象）**

```jsx
arr.push('new')            // ❌ 改变原数组
obj.key = 'value'          // ❌ 改变原对象
arr[0].field = 'changed'   // ❌ 改变对象的嵌套字段
```

---

## **2. 为什么 React 中禁止 Mutation？**

React 判断 `state` 是否变化的机制是：

```jsx
if (oldState !== newState) {
  // 说明 state 变了 → 触发重新渲染
}
```

因此，如果你直接修改原对象或数组的内容，**引用没变**，React 会**认为没有变化**，从而：

- 不触发 UI 更新
- 或出现状态污染（多个组件意外共享引用）

---

## **3. 如何安全地进行不可变更新？**

### **✅ 推荐方式（不修改原对象）：**

### **数组：**

```jsx
// 添加
setList([...list, newItem]);

// 删除
setList(list.filter(item => item.id !== targetId));

// 修改
setList(list.map(item =>
  item.id === targetId ? { ...item, seen: true } : item
));
```

### **对象嵌套更新（手动）：**

```
setState({
  ...state,
  user: {
    ...state.user,
    profile: {
      ...state.user.profile,
      name: 'New Name'
    }
  }
});
```

> 手动展开每一层，
> 
> 
> **控制清晰，但繁琐**
> 

---

## **4. Immer：让你“写 mutation、得 immutable”**

### **✅ 安装**

```bash
npm install immer
```

或使用封装更方便的版本：

```bash
npm install use-immer
```

---

### **✅ 使用方式：**

### **`useImmer`（封装版）**

```jsx
import { useImmer } from 'use-immer';

const [person, updatePerson] = useImmer({
  name: 'Tom',
  info: { city: 'Beijing' }
});

updatePerson(draft => {
  draft.info.city = 'Shanghai';  // ✅ 简洁、直接、安全
});
```

---

## **5. 浅复制 vs 深复制**

| **操作** | **是否安全** | **是否改变原始值** |
| --- | --- | --- |
| `const copy = [...arr]` | ✅ 仅复制数组结构 | ❌ 元素引用未变 |
| `arr[0].field = x` | ❌ 会 mutation | ✅ 改变原对象 |
| `map(item => ({...item}))` | ✅ 每个对象都新建 | ✅ 安全 |
| `produce(draft => { draft.x = y })` | ✅ 安全 | ❌ 不影响原对象 |

---

## **6. 推荐使用场景**

| **场景** | **推荐方式** |
| --- | --- |
| 简单数值布尔切换 | `useState` |
| 多字段对象、数组更新 | map / 展开操作 |
| 嵌套结构、表单、JSON 编辑 | **`Immer` / `useImmer`** 推荐 |

---