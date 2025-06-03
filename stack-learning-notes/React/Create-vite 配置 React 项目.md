# Create-vite 配置 React 项目

## **🛠️ 工具介绍**

- **Vite**：轻量级、快速的现代前端构建工具
- **React**：用于构建用户界面的 JavaScript 库
- 使用 Vite 替代 Create React App（CRA），配置更快、启动更迅速

---

## **1. 安装前准备**

确保你已经安装：

- [Node.js](https://nodejs.org/)（推荐 LTS 版本）
- npm 或 yarn

检查版本：

```bash
node -v
npm -v
```

---

## **2. 创建 React 项目（使用 Vite）**

### **使用 npm + create-vite：**

```bash
# 初始化项目（vite + react）
npm create vite@latest my-react-app -- --template react

# 进入目录
cd my-react-app

# 安装依赖
npm install

# 启动开发服务器
npm run dev
```

### **使用 yarn ：**

```bash
yarn create vite my-react-app --template react
cd my-react-app
yarn
yarn dev
```

---

## **3. 项目结构简解**

```
my-react-app/
├── public/           # 静态资源
├── src/
│   ├── App.jsx       # 主组件
│   ├── main.jsx      # 入口文件（绑定 DOM）
│   └── index.css     # 全局样式
├── index.html        # 模板文件
├── package.json      # 项目依赖
├── vite.config.js    # Vite 配置
```

---

## **4. 启动开发服务器**

```bash
npm run dev
```

输出形如：

```bash
Local: http://localhost:5173/
```

浏览器打开即可查看运行效果。

---

## **5. JSX 示例：基础组件**

**src/App.jsx**

```jsx
function App() {
  return (
    <div>
      <h1>Hello, React + Vite!</h1>
    </div>
  );
}

export default App;
```

---

## **6. 修改入口文件**

**src/main.jsx**

```jsx
import React from 'react'
import ReactDOM from 'react-dom/client'
import App from './App.jsx'
import './index.css'

ReactDOM.createRoot(document.getElementById('root')).render(
  <React.StrictMode>
    <App />
  </React.StrictMode>
)
```

---

## **7. 添加样式**

你可以在 src/index.css 或组件中加入 CSS：

```css
body {
  margin: 0;
  font-family: Arial, sans-serif;
}
```

---

## **8. 构建生产版本**

```bash
npm run build
```

构建完成后会生成 dist/ 文件夹，里面是可部署到服务器的静态资源。

---

## **9. 部署到 GitHub Pages（可选）**

安装插件：

```bash
npm install --save-dev vite-plugin-gh-pages
```

配置部署脚本等可另行整理。

---

## **✅ 总结流程**

1. 初始化项目：npm create vite@latest
2. 选择模板：--template react
3. 安装依赖：npm install
4. 启动开发：npm run dev
5. 编写组件，开发页面
6. 构建生产包：npm run build

---

是否需要我另外帮你整理一个可复用的 React 模板仓库结构，并包含完整的注释？