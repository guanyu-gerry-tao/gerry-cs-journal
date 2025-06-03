# React 列表渲染笔记：使用 map() 和合理设置 key

## **🔁 使用 map() 渲染列表**

- 在 React 中，通常使用 JavaScript 的 `map()` 方法，将一个数组**转换成 JSX 元素数组**。
- 基本写法如下：

```jsx
const items = ['a', 'b', 'c'];
const list = items.map(item => <li>{item}</li>);
```

- 可以直接在 JSX 中使用：

```jsx
<ul>
  {items.map(item => <li>{item}</li>)}
</ul>
```

---

## **🧷 为什么要使用 key？**

- React 渲染列表时，**必须为每个元素指定唯一的 `key` 属性**。
- `key` 是 React 识别每个元素的“身份”，帮助它判断哪些元素被新增、删除或重排。
- 没有 `key` 或 `key` 不唯一时，会影响 React 的 diff 算法，导致性能下降或出现渲染异常。

---

### **✅ 正确使用 key 的示例：**

```jsx
const people = [
  { id: 1, name: '爱达·洛芙莱斯' },
  { id: 2, name: '霍普' }
];

function PeopleList() {
  return (
    <ul>
      {people.map(person =>
        <li key={person.id}>
          {person.name}
        </li>
      )}
    </ul>
  );
}
```

> 注意：这里使用的是 `person.id`，因为它是唯一且稳定的标识符。
> 

---

## **🚫 常见错误：使用数组索引作为 key**

```jsx
items.map((item, index) => <li key={index}>{item}</li>);
```

- 虽然这样不会报错，但不推荐使用，**特别是在列表会动态变化的情况下**。
- 使用索引作为 `key` 可能导致：
    - 动画或焦点错乱
    - 不必要的组件重渲染
    - 数据状态“串位”等 UI 错误

---

## **📝 总结**

- 使用 `map()` 将数组渲染成 JSX 列表。
- 列表中的每个元素必须设置唯一的 `key`。
- 推荐使用稳定的 ID（如数据库中的 id）作为 `key`。
- **除非列表内容和顺序完全固定，避免使用索引作为 `key`**。