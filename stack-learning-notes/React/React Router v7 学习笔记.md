# React Router v7 学习笔记

## 1. 核心概念

- **前端路由**：在单页应用 (SPA) 中，通过 JavaScript 模拟页面跳转，实现 URL 变化但无需刷新整个页面的效果。
- **React Router**：一个流行的 React 库，用于管理应用程序的路由。

## 2. 基础路由配置 (Declarative Mode)

- **安装**：`npm install react-router`
    
- **核心组件**：
    
    - `<BrowserRouter>` 或 `<HashRouter>`：选择路由模式。
        - `BrowserRouter` (推荐)：使用 HTML5 History API，URL 更美观。
        - `HashRouter`：使用 URL 哈希片段 (`#`)。
    - `<Routes>`：包裹所有的 `<Route>` 组件，用于路由匹配。
    - `<Route>`：定义单个路由规则。
        - `path`：匹配的 URL 路径 (例如 `/`, `/list`, `/about`)。
        - `element`：路径匹配时渲染的 React 组件。
        - `index`：作为父路由的默认子路由，当父路径被访问时渲染。

```javascript
// main.jsx
import { BrowserRouter, Routes, Route } from 'react-router';
import App from './App.jsx';
import Home from './pages/home.jsx';
import List from './pages/list.jsx';
import About from './pages/about.jsx';
import NotFound from './pages/404.jsx';

// ...
<BrowserRouter>
  <Routes>
    <Route path="/" element={<App />}>
      <Route index element={<Home />} />
      <Route path="list" element={<List />} />
      <Route path="about" element={<About />} />
    </Route>
    <Route path="*" element={<NotFound />} /> {/* 404 页面 */}
  </Routes>
</BrowserRouter>
```

### 代码解读：
`import { BrowserRouter, Routes, Route } from 'react-router';`  
这里将主要的几个部件从 `react-router` 中引入

---

```javascript
import Home from './pages/home.jsx';
import List from './pages/list.jsx';
import About from './pages/about.jsx';
import NotFound from './pages/404.jsx';
```
这里将主要的几个自定义的部件（页面）引入

---

这里是主要的路由部分。首先用 `BrowserRouter` 包裹一个 `Routes`

```javascript
<BrowserRouter>
  <Routes>  {/* 这里必须有一个路由 */}
    <Route path="/" element={<App />}>  {/* 这里是第一层 Route */}
      <Route index element={<Home />} />  {/* 这里是第二层 Route */}
      <Route path="list" element={<List />} />
      <Route path="about" element={<About />} />
    </Route>
    <Route path="*" element={<NotFound />} />  {/* 404 页面 */}
  </Routes>
</BrowserRouter>
```

这里有两层嵌套（两层`<Route>`，主要的目的是让第一层的内容可以被下面几个分享：
> 例如，当第一层嵌套里是一个页面顶部+页面底部的横幅，那么接下来的list, about, 以及 index(home) 都可以展示这个横幅。

其实没有两层嵌套的话，也是可以运行的，例如下图

```javascript
<BrowserRouter>
    <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/list" element={<List />} />
        <Route path="/about" element={<About />} />
        <Route path="*" element={<NotFound />} /> {/* 404 页面 */}
    </Routes>
</BrowserRouter>
```

---

`*` 是一个通配符，表示所有前面没有匹配到的路径。
因此方便适合用来匹配404页

## 3. 路由跳转与嵌套

- **`<Link>` 组件**：用于创建声明式导航链接。
    - `to` 属性：指定目标 URL 路径 (例如 `to="/list"`)。
    - 动态路径：``to={`/list/${item.id}`}``
- **`<Outlet>` 组件**：在父路由组件中作为占位符，用于渲染匹配到的子路由组件。

```javascript
// App.jsx 或 List.jsx
import { Link, Outlet } from 'react-router';

function App() {
  return (
    <div>
      <nav>
        <Link to="/">首页</Link>
        <Link to="/list">列表</Link>
        <Link to="/about">关于</Link>
      </nav>
      <Outlet /> {/* 子路由内容在此渲染 */}
    </div>
  );
}
```


## 4. 获取路由参数

- **`params` (路由参数)**：URL 路径中的动态部分，用于标识资源。
    
    - 定义：在 `Route` 的 `path` 中使用冒号 `:` (例如 `path=":id"`)。
    - 获取：在组件中使用 `useParams()` Hook。
    - 示例：`/list/123` 中 `id` 为 `123`。

```javascript
// ListDetail.jsx  即子页面
import { useParams } from 'react-router';
// ...
const params = useParams(); // { id: '123' }
console.log(params.id);
```

**`query` (查询参数)**：URL 中问号 `?` 后面的键值对，用于过滤、排序或传递额外信息。

- 定义：直接在 `Link` 的 `to` 属性中添加 (例如 `to="/list/3?type=a"`)。
- 获取：在组件中使用 `useSearchParams()` Hook。它返回一个 `URLSearchParams` 对象，可以使用其 `get()` 等方法。

```javascript
// ListDetail.jsx
import { useSearchParams } from 'react-router';
// ...
let [searchParams] = useSearchParams(); // 获取 URLSearchParams 对象
console.log(searchParams.get('type')); // 获取 'type' 参数的值
```

> [!NOTE]
> 在某些情况下，`params` 和 `query` 确实看起来可以互换。但实际上，它们各自有明确的语义和适用场景，所以即使 `query` 看起来能解决 `params` 的问题，它们仍然需要并存。
> - 语义上，`params` 指向唯一资源
> - 语义上，`query` 对于众多资源进行过滤操作，以及方便对SQL进行操作
> - 符合 RESTful API 的行业惯例
> - 符合 SEO 和浏览器习惯
> 尽管 `query` 参数在技术上很灵活，可以传递各种数据，但为了**语义清晰、URL 可读性、路由匹配的确定性以及遵循 Web 开发惯例**，`params` 和 `query` 各司其职，在不同场景下发挥着不可替代的作用。它们共同构成了强大而灵活的 URL 数据传递机制。

**`useLocation`**：获取更多路由信息，如当前路径名 (`pathname`)、查询字符串 (`search`)、哈希值 (`hash`) 等。

```javascript
// 任何组件
import { useLocation } from 'react-router';
// ...
let location = useLocation();
console.log(location.pathname);
```

## 5. 编程式导航

- 通过 JavaScript 代码主动触发页面跳转。（而非由用户点击）
    
- **`useNavigate()` Hook**：返回一个 `Maps` 函数。
    
    - `Maps('/some-path')`：跳转到指定路径。
    - `Maps(-1)`：后退一步。
    - `Maps('/login', { replace: true })`：替换当前历史记录（类似重定向）。

```javascript
// 任何组件
import { useNavigate } from 'react-router';
// ...
const navigate = useNavigate();
const backToHome = () => {
  navigate('/');
};
```

## 6. 自定义导航守卫 (路由守卫)

- 在路由跳转过程中介入，根据条件决定是否允许导航或执行额外操作。
- **两种实现方式**：
    1. **声明式守卫 (组件方式)**：
        
        - 创建一个 `RequireAuth` 组件，内部包含逻辑判断。
        - 使用 `<Navigate>` 组件进行重定向。
        - 在路由中使用此组件包裹需要守护的 `<Link>` 或 `<Route>`。

```javascript
// RequireAuth.jsx
import { useLocation, Navigate } from 'react-router';
// ...
export default function RequireAuth({ children }) {
  const whiteList = ["/", "/about"];
  const { pathname } = useLocation();
  const notRequiredAuth = whiteList.includes(pathname);
  // 假设 hasToken 是判断用户是否登录的标志
  return (hasToken || notRequiredAuth ? children : <Navigate to="/login" replace state={pathname} />);
}
```

### 代码解读

`const whiteList`   
- 这一行是在创建一个白名单的页面，也就是说，他们不需要任何认证（不需要守卫）

`const { pathname } = useLocation();`   
- 这里是通过解构直接取了 `useLocation()` 的 `pathname` 的属性，这个属性是**当前用户正要前往**的 url。
- 例如，如果当前的浏览器指向了 `www.example.com/index`，则返回 `/index`

`const notRequiredAuth = whiteList.includes(pathname);`  
- 这里是判断当前的 `pathname` 是否在白名单，用于下面一行

`return (hasToken || notRequiredAuth ? children : <Navigate to="/login" replace state={pathname} />);`  
- 首先 `hasToken` 是案例里跳过的部分，假设用户有账号密码，那么 `hasToken === true`。
- `hasToken || notRequiredAuth` 这里说，如果 1. 用户有 token，或者2. 在白名单不需要守卫，则都为true
- 接下来，如果是true，则return一个children，否则返回一个`<Navigate>`，这个`<Navigate>`可以让现在的浏览器导向一个 `login` page，并且替换掉当前的
- 其中有两个属性 `replace` 和 `state={pathname}`
    - 其中 `replace` 表示，**替换**浏览器历史记录堆栈中的当前条目，而不是加入一个新的条目。那么这样
        - 当用户点击浏览器“后退”按钮时，他们不会回到包含 `<Navigate>` 组件的那个页面，而是会跳过它，回到更早的历史记录页面。
        - 这对于重定向场景非常有用。例如，用户访问了 `/dashboard`，但没有登录，你将他们重定向到 `/login`。如果使用了 `replace`，用户登录后点击后退，不会再回到 `/dashboard`（因为他们本来就没权限），而是直接跳到登录前的页面。这提供了更流畅和安全的体验。
    - 其中 `state={pathname}` 是将用户想要去的url存储了下来，那么登录页面可以利用这个 `state`，在用户成功登录后，将用户重定向回他们最初想访问的页面。

> [!NOTE]
> 这里的 `state` 属性是一个**路由级别的、与 History API 关联的数据传递机制**，而 `useState` 是一个**组件级别的、用于管理组件内部状态的 Hook**。它们是完全不同的概念。

**编程式守卫 (Data Mode 中的 `loader`)**：

- 在路由配置的 `loader` 函数中定义守卫逻辑。
- 如果条件不满足，使用 `throw redirect('/login')` 进行重定向。
- 在组件渲染前执行，更适合权限校验。

```javascript
// authLoader.js
import { redirect } from 'react-router';
export function authLoader() {
  const token = localStorage.getItem('token');
  if (!token) {
    throw redirect('/login');
  }
  return null; // 允许继续
}

// main.jsx 路由配置
// ...
{
  element: <ProtectedLayout />,
  loader: authLoader, // 在此应用守卫
  children: [
    { path: 'dashboard', element: <DashboardPage /> },
    // ...
  ],
}
```


## 7. Data Mode (数据模式)

- React Router v7 的新特性，强调在**组件渲染前**完成数据加载和处理。
- 通过 `createBrowserRouter` 配置路由，并定义 `loader` 和 `action` 函数。
- **`loader` 函数**：在路由对应的组件渲染前执行，用于预加载数据或进行路由守卫。
    - 返回的数据可在组件中使用 `useLoaderData()` 获取。
- **`action` 函数**：用于处理表单提交或其他数据变更引起的写入/更新操作。
    - 通常与 React Router 的 `<Form>` 组件配合使用。
    - 可返回数据或通过 `redirect()` 进行重定向。
    - 在组件中可通过 `useActionData()` 获取 `action` 返回的数据。
- **`redirect()` 函数**：在 `loader` 或 `action` 中使用，通过 `throw redirect('/target')` 来触发重定向，阻止当前组件渲染。