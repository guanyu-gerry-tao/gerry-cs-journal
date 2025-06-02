# 🔍 `<meta>` 常见内容 Cheatsheet

`<meta>` 标签用于提供**关于网页的元信息（metadata）**，主要放在 `<head>` 区块中，不直接展示在页面上。以下是常见的 `<meta>` 内容类型及其作用：

---

### **✅ 常见的`<meta>`标签类型**

| **类型** | **示例** | **作用** |
| --- | --- | --- |
| **字符集声明** | `<meta charset="UTF-8">` | 声明网页编码，推荐统一用 UTF-8 |
| **关键词** | `<meta name="keywords" content="HTML, CSS, JavaScript">` | （过时）用于SEO关键词提示，现已基本被忽略 |
| **描述** | `<meta name="description" content="A guide to web development basics.">` | 页面摘要，搜索引擎结果页中显示的内容 |
| **作者** | `<meta name="author" content="John Doe">` | 标注网页作者 |
| **视口设置** | `<meta name="viewport" content="width=device-width, initial-scale=1.0">` | 响应式设计必备，适配移动设备 |
| **刷新重定向** | `<meta http-equiv="refresh" content="5;url=https://example.com">` | 页面在5秒后自动跳转到指定URL |
| **浏览器兼容性** | `<meta http-equiv="X-UA-Compatible" content="IE=edge">` | 指定 IE 使用最新引擎渲染 |
| **社会媒体共享优化（Open Graph）** | `<meta property="og:title" content="Page Title">` 等 | 提高社交平台分享时的显示效果（如 Facebook、Twitter） |
| **版权信息** | `<meta name="copyright" content="© 2025 My Company">` | 提供版权声明 |

### **📌 小贴士：**

- `<meta charset="UTF-8">` 应该**始终放在 `<head>` 最前面**，避免乱码。
- 对于移动端网页，`<meta name="viewport">` 是**必须的**。
- 虽然 keywords 早期用于 SEO，但现在更多依赖**内容质量与语义结构**。