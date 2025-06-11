# React 自定义 Hook 总结

## 1. 什么是自定义 Hook？

自定义 Hook 是一个**专门用于封装和复用 React 状态逻辑的 JavaScript 函数**。它内部可以调用 `useState`、`useEffect` 等内置 Hook，将组件中重复的逻辑抽象出来。

**示例：`useOnlineStatus`**

```jsx
// useOnlineStatus.js
import { useState, useEffect } from 'react';

export function useOnlineStatus() {
  const [isOnline, setIsOnline] = useState(true); // 内部使用 useState
  useEffect(() => { // 内部使用 useEffect
    function handleOnline() { setIsOnline(true); }
    function handleOffline() { setIsOnline(false); }
    window.addEventListener('online', handleOnline);
    window.addEventListener('offline', handleOffline);
    return () => {
      window.removeEventListener('online', handleOnline);
      window.removeEventListener('offline', handleOffline);
    };
  }, []);
  return isOnline; // 返回状态值
}
```

## 2. 自定义 Hook 与普通函数的区别

|特征|自定义 Hook|普通函数|
|:--|:--|:--|
|**命名**|必须以 `use` 开头 (例如 `useMyHook`)|无特定限制|
|**内部调用**|**可以** 调用其他 React Hook|**不能** 直接调用 React Hook|
|**目的**|复用**带有状态逻辑**的组件行为|复用**不带状态逻辑**的纯计算或操作|
|**Hook 规则**|必须遵守 Hook 规则 (顶层调用)|不受 Hook 规则限制|

**示例：`getSorted` (普通函数 vs `useSorted` (非典型 Hook))**

```javascript
// ✅ 普通函数：不调用 Hook，只做纯计算
function getSorted(items) {
  return items.slice().sort();
}

// 🔴 避免：没有调用其他 Hook 的 Hook (通常不推荐)
// function useSorted(items) {
//   return items.slice().sort();
// }
```

## 3. 为什么要和什么时候使用自定义 Hook？

- **复用逻辑：** 当多个组件需要共享相同的状态逻辑（例如，监听网络状态、处理表单输入、获取数据）时，将其封装成自定义 Hook 可以避免代码重复。

```javascript
// 在不同组件中复用 useOnlineStatus
function StatusBar() {
  const isOnline = useOnlineStatus(); // 简洁地获取在线状态
  return <h1>{isOnline ? '✅ Online' : '❌ Disconnected'}</h1>;
}

function SaveButton() {
  const isOnline = useOnlineStatus(); // 同样简洁地获取在线状态
  function handleSaveClick() { console.log('✅ Progress saved'); }
  return (
    <button disabled={!isOnline} onClick={handleSaveClick}>
      {isOnline ? 'Save progress' : 'Reconnecting...'}
    </button>
  );
}
```

- **抽象复杂性：** 将与外部系统同步（如网络请求、浏览器 API 订阅）的复杂细节隐藏在 Hook 内部，使组件代码更具可读性和声明性。组件只关心“做什么”，不关心“怎么做”。  
    
- **优化和迁移：** 当 React 引入新的、更优化的 API 来处理特定场景时（如 `useSyncExternalStore`），你可以只修改自定义 Hook 的实现，而不需要修改所有使用该 Hook 的组件。

```javascript
// useOnlineStatus.js (旧实现)
// ... 基于 useState 和 useEffect

// useOnlineStatus.js (新实现，无需修改组件)
import { useSyncExternalStore } from 'react';
function subscribe(callback) { /* ... */ }
function getSnapshot() { return navigator.onLine; }
export function useOnlineStatus() {
  return useSyncExternalStore(subscribe, getSnapshot, () => true);
}
```


- **推荐时机：** 每当你写 Effect 时，考虑将其包裹在自定义 Hook 中，尤其是当 Effect 需要与外部系统同步、处理复杂的副作用或需要竞态条件处理时。

## 4. 自定义 Hook 的使用限制

- **Hook 规则：** 自定义 Hook 本身必须遵守 Hook 规则，即只能在 React 函数组件的顶层或其他自定义 Hook 的顶层调用。
- **名称必须以 `use` 开头。**
- **共享的是逻辑，不是状态本身：** 对同一个自定义 Hook 的每次调用都会拥有独立的 state。它们共享的是管理状态的逻辑，而不是同一个状态变量。