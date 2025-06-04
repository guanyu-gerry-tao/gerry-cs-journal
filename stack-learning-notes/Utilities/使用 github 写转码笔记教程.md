# 使用 github 写转码笔记教程

本教程教授如何使用 obsidian / git / github / markdown 这四个 软件/技术 来进行学习笔记的写作。本文由人工结合 ChatGPT 代写。

# ❓为什么要写笔记？

- 写笔记是**最有效的学习方式**：
    - [”学然后知不足，教然后知困“ - 礼记·学记](https://baike.baidu.com/item/%E5%AD%A6%E7%84%B6%E5%90%8E%E7%9F%A5%E4%B8%8D%E8%B6%B3%EF%BC%8C%E6%95%99%E7%84%B6%E5%90%8E%E7%9F%A5%E5%9B%B0/6687683)
    - [费曼学习法](https://sspai.com/post/73353)
- 程序员有记录、写文档的传统，**写清楚比写出来更重要**
- 开源精神鼓励**分享知识、组织内容、持续改进**
- 用 Markdown + GitHub 写笔记，是程序员常用的方法，利于展示和积累

# ❓Part 0：为什么需要 Git，Github，Obsidian 和 Markdown
这四者常常一起出现，是**现代开发者/写作者/学生/研究人员**的基本工具组合。

这是一个面向转码学习者的笔记系统方案，目标是：

- 高效记录与组织学习过程
- 支持本地编辑、版本控制与远程同步
- 可视化笔记结构，便于查阅与回顾
- 易于展示，适合作为公开项目与作品集

| **工具**       | **作用**                             |
| ------------ | ---------------------------------- |
| **Markdown** | 使用**简洁语法**来书写**排版漂亮**的笔记与文档（程序员风格） |
| **Obsidian** | 本地编辑 Markdown，结构清晰、支持插件（如 git）     |
| **Git**      | 跟踪文件变化，做版本控制                       |
| **GitHub**   | 远程备份与公开托管，云端保存笔记和共享                |

为什么不选以下工具？

|**工具**|**问题**|
|---|---|
|**Word / Apple Notes**|无法结构化管理、缺乏版本控制、不利于代码插入与同步|
|**Notion**|内容完全依赖云端，无法本地化；协作分享不灵活；不支持 Git 管理；不够程序员 (not geek enough)|
|**单纯本地 Markdown**|无备份、无版本、无分享能力；一旦丢失不可恢复|

接下来将对四个使用到的工具一一解释。

## 0.1 你将用 Git 做什么？

Git 是一个版本控制工具（Version Control System）

你可以把它想象成：
- 备份器：你写的每一份代码、每一个笔记，都可以保存一个“历史版本”
- 后悔药：不小心改坏了文件？你可以回退到任意一个历史时刻
- 协作器：多人写代码/写文档时，可以同时工作、合并成果

💡 **举例**：
> 你写了一份论文或程序，在第 5 天你删掉了一段关键内容；  
> 如果用 Git，你只需一句命令，就能恢复第 3 天的版本。

## 0.2 你将用 Github 做什么？

GitHub 是一个远程托管平台（Remote Repository Hosting）

你可以把它想象成：
- **云硬盘 + 社交网站**：专门存放和分享用 Git 管理的项目
- **项目展示平台**：你的代码可以对外公开，HR/面试官一眼就能看到你的作品
- **协作空间**：任何人都可以给你项目提交建议，进行开源协作

> [!NOTE]
> **Git 是本地的工具，GitHub 是联网的空间**。  
> 两者常常搭配使用  
> Git：在你电脑本地记录版本  
> GitHub：把这些版本上传、分享、协作

## 0.3 你将用 Obsidian 做什么？

Obsidian 是一款基于本地 Markdown 文件（马上会介绍）的知识管理工具，适合程序员、研究者和转码学习者做系统性笔记。它最大的特点是：

- 所有内容都是 .md 文件，存储在你自己的电脑上
- 通过插件支持 版本控制（Git）、任务管理、自定义界面，配合 git 和 Github 管理和分享笔记

## 0.4你将用 Markdown 做什么？

Markdown 是一种轻量级标记语言

你可以把它想象成：
- 写作神器：用最简单的语法，写出结构清晰的文本
- GitHub 的通用语言：项目说明（README）、笔记、博客、甚至简历都用 Markdown 写
- 适合程序员和工程师的文档格式：支持代码块、公式、表格、链接等
- 比 Word文档 或 Apple Notes 等更适合代码工作，效果极其简洁干练，排版操作快速。

> 💡 举例展示一个 markdown 文件快速编写一个项目介绍（无需鼠标选字体，粗体等）

`````markdown
# 项目标题
我是一个项目的介绍

## 功能介绍
- 登录/注册
- 数据可视化
- 导出 CSV

```python
def xfunc():
    print("hello world!")

xfunc() # hello world!
```
`````

---

# 🧰 Part 1：安装 Git（版本控制工具）

## 💻 1.1 Windows 系统安装 Git

### ✅ 1.1.1 步骤一 下载 Git 安装包
1. 打开浏览器，访问官网：[https://git-scm.com](https://git-scm.com)    
2. 页面会自动识别你的系统（Windows），点击 **“Download for Windows”** 按钮  
### ✅ 1.1.2 步骤二：运行安装程序
1. 双击下载好的 .exe 安装文件
2. 安装时一路点击 **“Next”**，建议保留默认设置
3. 遇到以下几个关键选项时，保持默认即可：

| **步骤**   | **选项**                                                     | **默认建议**      |
| -------- | ---------------------------------------------------------- | ------------- |
| 选择编辑器    | Use Vim                                                    | 保持默认即可（后续可以换） |
| PATH 设置  | Git from the command line and also from 3rd-party software | **保持默认**      |
| HTTPS 设置 | Use the OpenSSL library                                    | 默认            |
| 行结尾转换    | Checkout Windows-style, commit Unix-style                  | 默认            |
| 终端模拟器    | Use MinTTY                                                 | 默认            |

4. 最后点击 **“Install”** 安装，结束后点击 **“Finish”**

## 🍎 1.2 macOS 系统安装 Git

### ✅ 1.2.1 方法一：使用命令行工具（推荐）

[test][test]


1. 打开[“终端” (Terminal)](https://support.apple.com/zh-cn/guide/terminal/apd5265185d-f365-44cb-8b09-71a064a42125/mac)
2. 输入以下命令：    

```
git --version
```

3. 如果没有安装 Git，系统会弹出提示窗口，问你是否要安装 Xcode Command Line Tools
4. 点击“安装”按钮即可（自动下载安装 Git） 

### ✅ 1.2.2 方法二：使用 Homebrew（适合愿意接触一点终端的新手）

1. 确保你已经安装了 Homebrew（Mac 的包管理工具）。没装的话，在终端里执行：

```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

2. 安装 Git： 

```
brew install git
```

## 🔍 1.3 验证安装是否成功

无论你是 Windows 还是 macOS，安装完后：

1. 苹果电脑打开[“终端” (Terminal)](https://support.apple.com/zh-cn/guide/terminal/apd5265185d-f365-44cb-8b09-71a064a42125/mac) 
2. Windows电脑打开 [cmd](https://www.dell.com/support/kbdoc/zh-cn/000130703/windows-%E5%91%BD%E4%BB%A4%E6%8F%90%E7%A4%BA%E7%AC%A6%E4%BF%A1%E6%81%AF%E5%8F%8A%E5%85%B6%E4%BD%BF%E7%94%A8%E6%96%B9%E6%B3%95%E5%88%97%E8%A1%A8#:~:text=%E6%8C%89Windows%20%E9%94%AE%2B%20r%E3%80%82,%E7%84%B6%E5%90%8E%E5%8D%95%E5%87%BB%E2%80%9C%20%E7%A1%AE%E5%AE%9A%E2%80%9D%E3%80%82) 或 刚被安装的Git Bash
3. 输入：

```
git --version
```

3. 正常会输出类似：

```
git version 2.42.0.windows.1
```

说明安装成功！

## 1.4 Git 安装完之后我们要对 Git 做什么？

**暂时什么都不需要做。**

现在安装 Git 的唯一目的，是为了让你的系统支持：
- 使用命令行或图形工具（如 Obsidian 插件）进行版本控制
- 后续能把本地笔记连接到 GitHub 做同步与备份

换句话说：

Git 是底层工具（依赖项），现在不直接使用它也没关系，但你系统里必须要有它，其他软件（如 Obsidian）才能正常调用它。

---

# 📄 Part 2：配置 GitHub（网页版）

本节目标：**只使用浏览器完成 GitHub 的基本设置和操作**，不涉及命令行和本地同步。

## 2.1 步骤 1：注册 GitHub 账号

1. 打开浏览器，访问：[https://github.com](https://github.com)
2. 点击右上角 **Sign up**
3. 填写信息
4. 按页面提示完成验证和确认邮箱

> [!TIP]
> 建议使用长期可用的主力邮箱地址，未来简历/作品集中也会用到 GitHub 链接

## 2.2 步骤 2：创建一个新仓库（repository）

> 仓库（repository）相当于一个“文件夹”，可以放你的笔记、项目、练习内容  

1. 登录并进入 https://github.com 后，点击屏幕最右上角的头像
2. 选择 **Your repositories**
3. 点击右上方绿色的 **"New"** 进入创建仓库页面
4. 填写项目信息：
    - **Repository name**：使用英文输入一个仓库名字，例如 my-CS-notes
    - **Description**（可选）：填写简短说明
    - **Public / Private**：一般选择 Public（公开，便于展示）
    - 勾选：Add a README file（一定要勾选）
    - 其他可按默认
5. 点击 **Create repository**

接下来会自动进入项目页。由于教程目标是尽快部署笔记工作流，如果要探索 Github 请翻到本页最后，会对 Github 的功能进行进一步解释。

> [!TIP]
> 虽然不推荐这样用，  
> - 但是你可以直接在网页版项目页中，直接添加文件：在右上角绿色"Code"左边的"Add file"中选择上传或者新建文件。  
> - 你也可以直接下载项目文件：点击"Code"，并选择"Download ZIP"  
> 
> 这样的方式无法真正体验 GitHub 最核心的版本管理和协作能力。
---

# 📒 Part 3：Obsidian 入门

## 3.1 安装 Obsidian

1. 打开官网：[https://obsidian.md](https://obsidian.md)
2. 点击 “Download” → 选择你的系统（Windows / macOS）
3. 安装完成后启动 Obsidian

## 3.2 第一次打开 Obsidian 要做什么？

1. 创建一个 Vault（笔记库）：
    1. 选择 Create new vault
    2. Vault name 可设为 notes 或 转码笔记
    3. Folder 路径：
        - 对于🍎苹果电脑，建议在iCloud中建立，这样可以在苹果手机 Obsidian App中写作
            1. 首先进入电脑 iCloud Drive
                1. 如果找不到，可以先打开 Finder（苹果电脑的笑脸 app）
                2. 在顶部菜单点击：前往 → 前往文件夹…
                3. 输入 `~/Library/Mobile Documents/com~apple~CloudDocs` 并回车
            2. 新建一个文件夹，命名 "Obsidian"
            3. 然后回到 Obsidian，选择这个新建的 Obsidian 文件夹作为 Vault 文件夹的地址
        - 对于🪟Windows电脑
            - 如果需要与苹果手机的 Obsidian App 同步，建议使用付费的 [Obsidian sync](https://obsidian.md/sync) 同步。如果选择使用付费同步，Vault 可以在任意地址，除了 iCloud，onedrive 等云盘下（因为 sync 会和云盘冲突）
            - 如果没有在手机上使用的需求，可以把 Vault 建立在任何地方。  
2. 建立完成后你会进入编辑器界面
3. 为了使用 Github 备份笔记，必须首先创建一个文件夹，文件夹名建议和你的 Github 项目名一致：my-CS-notes
4. 除了创建一个文件夹之外，先不用写任何东西

## 3.3 插件准备：Git

1. 进入设置（在 Obsidian 中的时候，看屏幕最左上角🍎图标的右边，选择 Obsidian，选择 Setting）
2. 点击 Community Plugins
3. 关闭 Restricted Mode
4. 点击 Community Plugins 右边的 “Browse” 搜索插件：Git
5. 安装并启用

## 3.4 配置 Github Token 和 Obsidian Git

### 3.4.1 首先配置 Github token（先别管这是什么）
1. 回到 https://github.com/
2. 点击右上角你的头像
3. 点击 Setting
4. 左边选择栏里向下滑，找到 Developer settings
5. 左边点击 Personal access tokens
6. 点击 Tokens (classic)
7. 点击 Generate new token
8. 选择 Generate new token (classic)
9. 给你的 Token 起名，以方便自己识别。可以写：Obsidian Git
10. 设置 Expiration，选择 No expiration
11. 接下来点选 repo（系统自动选择repo下的全部选项），不勾选其他内容
12. 往下翻，点击 "Generate token"
13. ⚠️ 此时页面会显示你的 token，这是一串字符，显示在一个绿色的框内
14. ⚠️ 马上复制 token 然后保存在本地，一旦刷新或者关闭页面，这个 token 就不会再次显示。如果丢失 token，你可以重新生成一个 token，但是你要重新配置 Obsidian git。

### 3.4.2 配置 remote repo URL（也别管这是什么）
1. 首先复制粘贴以下内容（URL）到任意地方
`https://<PERSONAL_ACCESS_TOKEN>@github.com/<USERNAME>/<REPO>.git`
2. 将 `<PERSONAL_ACCESS_TOKEN>` 改为你刚才保存下来的token
3. 将 `<USERNAME>` 改为你的 github 用户名。通过在 github 右上角点击头像，弹出边框最上面的加粗字体就是 github 用户名
4. 将 `<REPO>` 改为你刚刚在 2.2 新建的仓库的名字：my-CS-notes
5. 保存下修改好的 URL ⛓

### 3.4.3 然后配置 Obsidian Git
1. 返回 Obsidian 
2. 键盘选择 cmd+P (苹果电脑)，或 ctrl+P (Windows电脑)
3. 输入 "clone"，选择 "Obsidian Git: Clone an existing remote repo"
4. 系统会询问 "Enter remote URL"，输入刚才在 3.4.2 修改好的 URL ⛓
5. 接下来系统询问 "Enter directory for clone. It needs to be empty or not existent"，输入刚才在 3.2 新建的 Obsidian 文件夹名：my-CS-notes（刚刚我们重名建立的文件）
6. 之后 Obsidian 界面右上角会提示 "Clone new repo" 和 "Please restart Obsidian"。遵照提示使用 cmd+Q （苹果）或者 Alt+F4 （Windows）关闭之后，重新打开 Obsidian。

### 3.5 验证

此时 Obsidian Git 应该已经配置好了。我们应该能看到 Obsidian 左侧文件夹下会出现一个 README，这是我们在 2.2 中创建仓库时勾选了 Add README 之后自动生成的 README 文件。

现在往 README 中随便写一些东西。

我们在 Obsidian 最左边的一列按钮中，找到 "Open Git source control"，大概这个样子：

![[Snipaste_2025-06-03_16-51-50.png]]

然后会在 Obsidian 右边弹出一个窗口。此时我们在弹出的窗口最上面点击这个按钮：

![[Snipaste_2025-06-03_16-53-04.png]]

这时候如果看到 "Pushed 1 file to remote"，就可以返回 Github，进入你的项目页，往下滚动，就能马上看到你写的东西了。

> [!NOTE]
> README 是 Github 用来在项目页展示信息的文件。它的全名是 `README.md`，本身是一个 Markdown 格式的文件。
>
> README 可以在每一个子文件夹中存在，并且跳转到子文件夹后，也会被展示在这个文件夹的首页。因此，我们可以用以下的格式写我们的笔记，优化笔记展示的体验：

```
Obsidian Vault/
└── my-CS-notes
    ├── README.md   <- 这里是项目的总体介绍、笔记文件夹的导航页
    ├── stacks
        ├── README.md  <- 这里是导航页，比如罗列笔记，或者介绍笔记
        ├── Python
            ├── python-note-1.md
            └── python-note-2.md
        └── Java
            ├── java-note-1.md
            └── java-note-2.md
    └── leetcode
        ├── README.md  <- 这里是导航页，比如罗列笔记，或者介绍笔记
        └── greedy-algorithm
            ├── problem-#1.md
            └── problem-#2.md
        ...
```

---

除此之外，可以参考这一套[教程](https://forum.obsidian.md/t/the-easiest-way-to-setup-obsidian-git-to-backup-notes/51429)进行配置

# Part 4：Markdown 基础语法

## 4.1 Markdown 教程
Markdown 是 Github 和 Obsidian 等使用的轻量化标记语言，用纯文本就能写出结构化的内容。这里是一个非常优秀的[教程](https://www.markdowntutorial.com/zh-cn/) 

## 4.2 补充内容

> [!IMPORTANT]
4.1 的教程缺失部分重要内容，例如”代码块“。代码块是 Markdown 用来展示代码的语法。如果你是写转码笔记，你不可能不用代码块。

### 4.2.1 代码块
代码块的 Markdown 语法如下：

````
```python
print("hello world!")  # hello world!
```
````

显示效果如下：

```python
print("hello world!")  # hello world!
```

#### 语法解读：
首先敲入两组 ` ``` ` ，你就可以在两组 ` ``` ` 中编写代码了。  
代码会被包裹起来，并且以`mono`字体显示（代码用字体）  

如果在第一组` ``` `后面写上代码的语言，例如` ```python`  
则会给例如`print()`等关键词配色方便阅读。


### 4.2.2 行内代码
观察下面两句话：

- 在 python 中使用 print("hello world") 可以打印出 "hello world"
- 在 python 中使用 `print("hello world")` 可以打印出 `"hello world"`

第二句话可以将 `print()` 在段落中突出并以代码字体展示，适合强调函数名，变量名，关键命令等内容。

#### 语法解读：
首先敲入两个 ``` `` ``` ，然后再在里面写入内容。

行内代码不支持上色标记

### 4.2.3 嵌套的代码

如果要编写教程，例如本教程，可以在代码块里嵌套代码块：

`````
````
```python
print("hello world!")
```
````
`````

只要外面一圈代码块比内一圈代码块的`` ` `` 多，就可以将内部的```` ``` ```` 以文字显示出来，而不是被当做 Markdown 语法处理。

---

为了直观显示，以下是本章 Markdown 的截图：
![[Snipaste_2025-06-03_17-36-43.png]]

---

### 4.2.4 分隔符
使用分隔符可以有效分割章节。以下是分隔符的语法：
```markdown
---
```

这是使用效果：

---

以上是使用效果。

### 4.2.5 图片
大部分情况下我们希望将图片截图然后显示在笔记中。

和 word，notion 等不同的是，Markdown 程序（包括 Obsidian 和 Github）需要把图片存储在某个位置，然后用 Relative Link 引入，例如：

`![](src/使用 github 写转码笔记教程/截图1.png)`

- 其中开头的 `!` 表示这是图片而不是文件链接  
- 其中随后的 `[]` 里面填入”替代文字“，不用填（是当图片不能正常显示时显示出来的文字）
- 其中括号 `()` 里就是图片的链接地址。

正如例子，这里建议图片存储在以下地址：

```
    my-notes
    ├── src  <- 这是你这里所有 my-note 下笔记的截图的文件夹
        ├── 截图1.png  <- 这是你的笔记用到的截图
        ├── 截图2.png  <- 其他截图
        ...
    ├── 使用 github 写转码笔记教程.md  <- 这是你的笔记
    ├── 其他笔记1.md                 <- 其他笔记
    ├── 其他笔记2.md
    ...
```

你可以在 Obsidian 设置，这样每次粘贴截图的时候，Obsidian 会自动把图片放在如上的位置：

- 打开 `Setting -> Files and links`
- 将 `Defualt location for new attachments` 改为 `In subfolder under current folder`
- 将 `Subfolder name` 改为 `src` （或者你自定义的名字）

> [!TIP]
> 当然你不这么做也可以，这样只是方便管理截图。

### 4.2.6 高亮的提醒，警告：
在上一章结尾我用了一个 `Tip` 的方块，展示了一些信息。
Obsidian 和 Github 中可以使用拓展的引用语法展示特别的信息：

```markdown
> [!NOTE]
> Useful information that users should know, even when skimming content.

> [!TIP]
> Helpful advice for doing things better or more easily.

> [!IMPORTANT]
> Key information users need to know to achieve their goal.

> [!WARNING]
> Urgent info that needs immediate user attention to avoid problems.

> [!CAUTION]
> Advises about risks or negative outcomes of certain actions.
```

![](src/Pasted%20image%2020250603180024.png)

## 4.3 Obsidian 的 Markdown
> [!WARNING]
> Obsidian 使用的 Markdown 在链接文件的时候，使用的是 Obsidian 自己的连接方式 Wikilink：`[[笔记名]]` ，这和 Github 使用的标准 Markdown 的 Relative Link `[笔记名](./笔记.md)`方式不同。
> 
> 这会导致 README 在 Obsidian 中可以链接到其他笔记，而 Github 中不能。

**解决方法是：**

可以在 `Setting -> Files and Link -> Use [[Wikilink]]` 中关掉这个选项。

也可以使用 Obsidian 插件 [Link Converter](obsidian://show-plugin?id=obsidian-link-converter) 来一键将全部笔记从 Obsidian 的默认方式改为 Relative Link。


---

终。

---

# 如果我遇到问题怎么办？如果我有其他提问怎么办？

你可以将本页复制给 ChatGPT，然后让 ChatGPT 回答。