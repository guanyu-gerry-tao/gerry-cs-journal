# 全栈 React 项目结构说明 ✅ 从零搭建全栈项目的 6 个步骤

一个典型的「React 全栈项目」通常包括以下结构：

```
project-name/              ← 项目主文件夹
├── frontend/              ← 前端项目（React，Vite）
│   ├── src/               ← 前端源码
│   └── package.json       ← 前端依赖配置
├── backend/               ← 后端项目（Node.js + Express）
│   ├── index.js           ← 后端入口文件
│   └── package.json       ← 后端依赖配置
├── .gitignore             ← 忽略 Git 不需要追踪的文件
├── README.md              ← 项目说明文档
```

这个结构常见于练习项目、作品集项目、或入门全栈实践，**前后端分目录独立管理，但仍属于一个 Git 仓库（Monorepo 方式）**。

---

## **✳️ 步骤 1：初始化 Git 仓库**

**操作方式：**

- 打开 VS Code，新建主项目文件夹，例如 turbo-lobster
- 打开左侧 Source Control 面板，点击「Initialize Repository」

**作用解释：**

- 这一步等于运行了 git init，是告诉 Git：“我要用你来记录这个项目的变化历史”
- 你以后修改的每一行都可以追踪、提交、同步到 GitHub

---

## **✳️ 步骤 2：创建前后端两个子目录**

在VSCode里新建一个terminal，然后输入：

```bash
mkdir frontend backend
```

**解释：**

- 在mkdir 是创建文件夹命令
- 你现在把 React 和 Express 拆成两个项目，分别管理，逻辑清晰

---

## **✳️ 步骤 3：初始化前端项目（用 Vite + React）**

```bash
cd frontend
npm create vite@latest . -- --template react
npm install
cd ..
```

**每一步解释如下：**

| **命令** | **作用** |
| --- | --- |
| `cd frontend` | 进入 frontend 文件夹 |
| `npm create vite@latest . -- --template react` | 调用 Vite 的脚手架工具，在当前目录生成 React 项目结构 |
| `npm install` | 安装依赖包（如 React、Vite 等），生成 node_modules/ |
| `cd ..` | 回到项目根目录 |

**你当时的困惑：**

- 为什么 npm create 而不是 npm create react？
    
    👉 因为调用的是一个“脚手架工具”，叫 create-vite，不是 React 自带的。
    
- 为什么分两步？
    
    👉 因为脚手架只是“生成模板”，安装依赖要手动执行。（意味着create-vite只生成了众多文件，以及一个package.json。真正安装依赖的是`npm install`这个步骤）
    

---

## **✳️ 步骤 4：初始化后端项目（Express）**

```bash
cd backend
npm init -y
npm install express
touch index.js
```

**解释：**

- `npm init -y`：生成一个 package.json 文件（告诉 npm：这是一个 Node 项目）
- `npm install express`：安装 Express 框架（构建后端 API）
- `touch index.js`：创建后端入口文件（你也可以手动创建）

**后端代码示例（写在 index.js 里）：**

```jsx
const express = require('express');
const app = express();
const port = 3000;

app.get('/api/hello', (req, res) => {
  res.json({ message: 'Hello from backend!' });
});

app.listen(port, () => {
  console.log(`Server running at http://localhost:${port}`);
});
```

---

## **✳️ 步骤 5：创建 `.gitignore` 文件**

内容如下（避免上传不必要的大文件或隐私信息）：

```
# 前端忽略项
/frontend/node_modules
/frontend/dist

# 后端忽略项
/backend/node_modules

# 通用忽略项
.env
.DS_Store
```

**解释：**

- .gitignore 告诉 Git 哪些文件**不要追踪**
- 例如 node_modules 太大，不需要上传；.env 通常包含密码或秘钥

---

## **✳️ 步骤 6：连接 GitHub 仓库**

**操作方式（图形界面）：**

1. 打开 VS Code 的 Source Control 面板
2. 选择「Publish to GitHub」
3. 登录 GitHub，输入仓库名（比如 turbo-lobster）
4. 点击确认，VS Code 会自动：
    - 创建 GitHub 仓库
    - 推送本地代码
    - 建立远程连接

---

## **✅ 补充说明**

### **为什么不用 branch、pull request？**

- 因为你是自己开发，不需要代码审查或协作流程
- 你可以直接 commit + push 到 main 分支

### **create-vite 做了什么、没做什么？**

- 它只是生成模板结构
- 不会安装依赖、不会初始化 Git、不会连接远程仓库

### **npx 和 npm 的区别？**

- npx 是临时执行 CLI 工具
- npm 是安装依赖包用的
- 所以我们用 npx create-vite 是**临时调用项目生成器**

---

## **📘 小结一句话版**

> 在项目主文件夹里建 frontend 和 backend，分别用 Vite 和 Express 初始化，手动安装依赖，写好 .gitignore 后初始化 Git，再用 VS Code 一键发布到 GitHub。
> 

# Q&A

Q：为什么 `npm install express` 不需要先执行 `npm install`？

A：因为 `npm install express` 会自动读取当前目录的 package.json，然后安装 express 并把它写入 dependencies。只要你之前已经执行过 `npm init` 创建了 package.json，就不需要先执行 `npm install`。

---

Q：`npm install` 和 `npm install express` 有什么区别？

A：`npm install`（不加参数）是安装 package.json 中已经列出的所有依赖；`npm install express` 是新增并安装一个名为 express 的依赖，并写入 package.json 的 dependencies 中。

---

Q：`npm install` 安装的是本地的还是全局的？

A：默认是安装在当前项目的本地 node_modules 文件夹里，而不是全局。如果要全局安装需要加 -g 参数，例如：`npm install -g create-vite`。

---

Q：前端和后端项目都需要各自的 package.json 吗？

A：是的。每个独立的 Node 项目（不管是 React 还是 Express）都应该有自己的 package.json，它用来记录该项目的依赖、脚本命令等。你也需要在每个项目中分别执行一次 `npm install` 来安装各自的依赖。

---

Q：为什么 React 项目中要先执行 `npm create vite`，后面还要再执行 `npm install`？

A：npm create vite 只是帮你生成了一个项目结构和模板文件，它并不会自动安装依赖。npm install 是你手动去安装这些依赖，让项目能够正常运行。

---

Q：我看到别人直接用 npm create vite，这是什么操作？不是应该 npx 吗？

A：`npm create vite` 是 `npx create-vite` 的简写（语法糖），作用是调用一个叫做 create-vite 的 CLI 工具。它并不是 npm 的核心功能，而是 npm 7+ 之后添加的新用法，用来运行项目生成器。

---

Q：那为什么不是 `npm create react`？

A：因为 React 官方的脚手架工具叫 create-react-app，而不是 create-react。你要使用的是 `npx create-react-app`，或者更现代的是用 create-vite 来生成 React 项目结构。

---

Q：我不太喜欢语法糖，这样会不会影响我学习？

A：完全不会，反而是好事。语法糖虽然写法更短，但会掩盖背后的运行原理。你现在愿意用显式的命令、搞懂每一步怎么运行，是非常正确的方式。真正厉害的工程师都不会被语法糖迷惑，而是清楚地知道：它只是让某些事写得短一些而已。