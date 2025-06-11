# React 笔记：Effect 依赖项问题总结

本节重点讨论 `useEffect` 依赖项的正确使用，以及 React 如何通过检查工具强制执行规则。

## 1. Effect 如何知道需要重新同步？

- **你告诉 React：** 通过将响应式值包含在 Effect 的 **依赖列表** (`[]`) 中。
- **比较机制：** 每次组件重新渲染后，React 会比较当前依赖数组中的值与上次渲染时的值。如果任何值不同（使用 `Object.is` 比较），Effect 将重新同步。

```javascript
function ChatRoom({ roomId }) { // roomId 是 props，响应式的
  useEffect(() => {
    const connection = createConnection(serverUrl, roomId);
    connection.connect();
    return () => {
      connection.disconnect();
    };
  }, [roomId]); // ✅ roomId 放在依赖数组中，当它变化时 Effect 会重新同步
  // ...
}
```

## 2. Effect 会“响应”于响应式值

- **响应式值的定义：**
    
    - 组件内部声明的 `props`。
    - 组件内部声明的 `state`。
    - 从 `props` 或 `state` 计算出来的其他值（在组件函数体内）。
- **特性：** 这些值在渲染过程中计算，并参与 React 数据流，可能会随时间变化。
    
- **规则：** Effect 内部读取的 **所有响应式值都必须** 包含在依赖项中，以确保 Effect 在这些值变化时能够重新同步。

```javascript
function ChatRoom({ roomId }) { // roomId 是响应式的
  const [serverUrl, setServerUrl] = useState('https://localhost:1234'); // serverUrl 是响应式的
  // const calculatedValue = roomId + '_' + serverUrl; // calculatedValue 也是响应式的

  useEffect(() => {
    const connection = createConnection(serverUrl, roomId); // Effect 使用了 serverUrl 和 roomId
    connection.connect();
    return () => {
      connection.disconnect();
    };
  }, [roomId, serverUrl]); // ✅ 所有响应式依赖都已声明
  // ...
}
```

**非响应式值：**

- 组件外部的常量或全局变量（如果它们不随渲染变化）。
- `useState` 返回的 `set` 函数和 `useRef` 返回的 `ref` 对象本身（它们是稳定的，保证在重新渲染时不会改变）。这些可以省略。
- **可变值（陷阱）：** 像 `location.pathname` 或 `ref.current` 这样的值是可变的，但它们的改变不触发 React 渲染，因此不能作为 Effect 依赖。应使用 [`useSyncExternalStore`](https://www.google.com/search?q=%5Bhttps://zh-hans.react.dev/learn/you-might-not-need-an-effect%23subscribing-to-an-external-store%5D\(https://zh-hans.react.dev/learn/you-might-not-need-an-effect%23subscribing-to-an-external-%3C7%3E%3C4%3Estore\)) 处理外部可变值。

## 3. 没有依赖项的 Effect (`[]`) 的含义

- **含义：** Effect 代码不使用任何响应式值。
    
- **执行时机：** 仅在组件挂载时连接，在组件卸载时断开。在开发环境中，React 会额外执行一次来压力测试清理逻辑。

```javascript
const serverUrl = 'https://localhost:1234'; // 在组件外部，非响应式
const roomId = 'general'; // 在组件外部，非响应式

function ChatRoom() {
  useEffect(() => {
    const connection = createConnection(serverUrl, roomId);
    connection.connect();
    return () => {
      connection.disconnect();
    };
  }, []); // ✅ Effect 内部没有使用任何响应式值，所以依赖数组为空
  // ...
}
```

## 4. React 会验证依赖关系是否正确

- **检查工具 (Linter)：** 配置了 React 的检查工具（如 ESLint 配合 `eslint-plugin-react-hooks`）会检查 Effect 代码中使用的每个响应式值是否已声明为其依赖项。
    
- **发出错误：** 如果 Effect 使用了响应式值但未将其列为依赖项，检查工具会发出警告或错误（例如 `React Hook useEffect has missing dependencies`）。这表明代码存在潜在的 Bug。

```javascript
function ChatRoom({ roomId }) { // roomId 是响应式的
  const [serverUrl, setServerUrl] = useState('https://localhost:1234'); // serverUrl 是响应式的
  useEffect(() => {
    const connection = createConnection(serverUrl, roomId); // Effect 使用了 serverUrl 和 roomId
    connection.connect();
    return () => connection.disconnect();
  }, []); // 🔴 Lint 错误：缺少 roomId 和 serverUrl 依赖
  // ...
}
```