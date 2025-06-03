# JavaScript map() 笔记

### **✅ 基本作用：**

> `map()` 会对数组中
> **每个元素进行处理**
> **新的数组**

适合用来：

- **将原始数据转换成 JSX 元素**
- **渲染列表**

---

### **✅ 基本语法：**

```js
array.map((element, index, array) => {
  // return 新的值
})
```

| **参数** | **含义** | **是否必须** |
| --- | --- | --- |
| `element` | 当前元素 | ✅ 必需 |
| `index` | 当前元素索引 | ⬅️ 可选 |
| `array` | 整个原数组 | ⬅️ 很少用 |

---

### **✅ React 中常见用法：**

```js
const listItems = data.map(item =>
  <li key={item.id}>{item.title}</li>
);
```

> 💡 每个返回的元素都要加 key（通常用 id），以便 React 跟踪更新
> 

---

### **🆚 和 forEach 的区别：**

| **特性** | `map()` | `forEach()` |
| --- | --- | --- |
| 是否返回新数组 | ✅ 是 | ❌ 否 |
| 是否适合用于渲染 | ✅ 非常适合 | ❌ 不适合 |
| 推荐程度（在 React 中） | ✅✅✅ | ❌ |

---

### **✅ 带 index 的例子：**

```js
items.map((item, index) =>
  <li key={index}>
    {index + 1}. {item.name}
  </li>
)
```