# React Context 简明笔记

## **📌 React Context 机制简要流程**

- 你通过 `createContext(defaultValue)` 创建了一个 context 容器
- 上层组件（如 Section）使用 `<LevelContext value={...}>` 包住子组件
    - ⚠️ 这其实是语法糖，React 内部自动等效为 `LevelContext.Provider`
- 下层组件（如 Heading）使用 `useContext(LevelContext)` 获取当前值
- 获取的值就是最近一层 `<LevelContext value={...}>` 向下传的 value
- 因此：**只要你用了 `<LevelContext value={...}>`，并且下层用了 `useContext(...)`，就能实现自动数据读取**

```jsx
----- App.js

import Heading from './Heading.js';
import Section from './Section.js';

export default function Page() {
  return (
    <Section>
      <Heading>主标题</Heading>
      <Section>
        <Heading>副标题</Heading>
        <Heading>副标题</Heading>
        <Heading>副标题</Heading>
        <Section>
          <Heading>子标题</Heading>
          <Heading>子标题</Heading>
          <Heading>子标题</Heading>
          <Section>
            <Heading>子子标题</Heading>
            <Heading>子子标题</Heading>
            <Heading>子子标题</Heading>
          </Section>
        </Section>
      </Section>
    </Section>
  );
} // 这里Section组件没有输入level参数，因为在LevelContext.js中level参数默认为1，且在Section.js中设置每传递一次会自动+1

----- Section.js

import { LevelContext } from './LevelContext.js';

export default function Section({ level, children }) { // 注意这里需要传入一个level
  return (
    <section className="section">
      <LevelContext value={level + 1}>  
      // 注意这里使用了一个LevelContext
      // 如果使用 level + 1，则意味着每向下传递一次，+1
        {children}
      </LevelContext>
    </section>
  );
}

// LevelContext 是一个 LevelContext.js 里 createContext(1) 返回出来的组件。这里的(1)指默认是1

----- Heading.js

import { useContext } from 'react';
import { LevelContext } from './LevelContext.js'; 

export default function Heading({ children }) {
  const level = useContext(LevelContext); // 这里必须使用useContext
  // 并且传入 LevelContext
  // 如果不假如上面一行，则1.下面level没有办法使用；2.Heading组件不能读取context
  // 可以理解为，level是useContext通过解析LevelContext得出的值，告诉了本组件应该用什么level
  switch (level) {
    case 1:
      return <h1>{children}</h1>;
    case 2:
      return <h2>{children}</h2>;
    case 3:
      return <h3>{children}</h3>;
    case 4:
      return <h4>{children}</h4>;
    case 5:
      return <h5>{children}</h5>;
    case 6:
      return <h6>{children}</h6>;
    default:
      throw Error('未知的 level：' + level);
  }
}

----- LevelContext.js

import { createContext } from 'react';

export const LevelContext = createContext(1); // 这里LevelContext就是返回来的组件

```

---

## **🔁 数据传递示意（自上而下）**

```
Section（传值） --> Heading（用 useContext 取值）
```

---

## **🧱 代码结构解释**

### **LevelContext.js**

```jsx
import { createContext } from 'react';
export const LevelContext = createContext(1);
```

- 创建 `context`，默认值是 1（比如 `<h1>`）

---

### **Section.js**

```jsx
import { LevelContext } from './LevelContext';

export default function Section({ level, children }) {
  return (
    <LevelContext value={level}>
      {children}
    </LevelContext>
  );
}
```

- 将 level 包装为 context，向子组件传递

---

### **Heading.js**

```jsx
import { useContext } from 'react';
import { LevelContext } from './LevelContext';

export default function Heading({ children }) {
  const level = useContext(LevelContext); // 读取当前层级
  const Tag = `h${level}`;
  return <Tag>{children}</Tag>;
}
```

- 根据当前 context 中的 level 决定要渲染 `<h1>`、`<h2>` 等

---

## **✅ 快速记忆关键词**

- `createContext()`：创建容器
- `<Context value={...}>`：广播值
- `useContext(...)`：接收值
- `context` 默认只能传一个值；多个值请用对象或多个 `context`