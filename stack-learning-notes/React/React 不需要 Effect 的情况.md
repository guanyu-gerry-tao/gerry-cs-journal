# React 不需要 Effect 的情况

这份笔记总结了 React 官方文档中关于何时避免使用 Effect 的建议，以及推荐的替代方案。

**核心思想：** Effect 是“脱围机制”，用于与**外部系统**同步。如果逻辑不涉及外部系统（例如，仅仅是根据 props 或 state 变化更新其他 state），则不应使用 Effect。

**常见情况和推荐做法：**

1. **转换渲染所需数据：**
    
    - **避免：** 在 Effect 中更新 state 来转换数据。
    - **推荐：** 在渲染期间（组件顶层）直接计算所需数据。
2. **缓存昂贵的计算：**
    
    - **避免：** 使用 Effect 来缓存计算结果。
    - **推荐：** 使用 [`useMemo`](https://www.google.com/search?q=%5Bhttps://zh-hans.react.dev/reference/react/useMemo%5D\(https://zh-hans.react.dev/reference/react/useMemo\)) Hook 来记忆昂贵的计算。
3. **当 Prop 变化时重置所有 state：**
    
    - **避免：** 在 Effect 中重置 state。
    - **推荐：** 为组件传入不同的 `key` 属性，使 React 重新挂载组件并重置其所有内部 state。
4. **当 Prop 变化时调整部分 state：**
    
    - **避免：** 在 Effect 中调整 state。
    - **推荐：** 在渲染期间直接调整 state（通过存储前序渲染信息），或更好地通过计算派生值而不是存储和调整 state。
5. **在事件处理函数中共享逻辑：**
    
    - **避免：** 在 Effect 中处理由特定用户事件引起的逻辑。
    - **推荐：** 将事件特定的逻辑放在相应的事件处理函数中，如果需要共享则提取成一个通用函数供多个事件处理函数调用。
6. **发送 POST 请求：**
    
    - **组件显示时需要发送的请求：** 放在 Effect 中（如分析请求）。
    - **由特定用户交互引起的请求：** 放在事件处理函数中（如表单提交）。
7. **链式计算 (Effect 之间相互触发)：**
    
    - **避免：** 多个 Effect 相互触发来调整 state。
    - **推荐：** 尽可能在渲染期间计算，并在事件处理函数中调整 state。
8. **初始化应用：**
    
    - **避免：** 将只需在应用加载一次的逻辑放在 Effect 中。
    - **推荐：** 通过顶层变量（如 `didInit` 标记）或在模块初始化和应用渲染之前执行。
9. **通知父组件有关 state 变化的信息：**
    
    - **避免：** 在 Effect 中通知父组件 state 变化。
    - **推荐：** 在事件处理函数中直接更新子组件和父组件的 state（批量处理），或者进行“状态提升”，让父组件完全控制子组件的 state。
10. **将数据传递给父组件：**
    
    - **避免：** 子组件在 Effect 中将数据传递给父组件。
    - **推荐：** 让父组件获取数据，并将其作为 `props` 向下传递给子组件。
11. **订阅外部 store：**
    
    - **避免：** 手动在 Effect 中订阅 React state 之外的数据。
    - **推荐：** 使用 [`useSyncExternalStore`](https://www.google.com/search?q=%5Bhttps://zh-hans.react.dev/reference/react/useSyncExternalStore%5D\(https://zh-hans.react.dev/reference/react/useSyncExternalStore\)) Hook 来订阅外部数据源。
12. **获取数据：**
    
    - **是 Effect 的合适用例**，因为需要与外部系统（网络）同步。
    - **重要提示：** 必须实现清理函数以避免“竞态条件”（旧请求结果覆盖新请求结果）。
    - **推荐：** 将获取逻辑封装到自定义 Hook 中，或使用现代框架内置的数据获取机制。