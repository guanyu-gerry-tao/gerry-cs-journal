# Tools

Developing a cloud application involves multiple stages from ideation to deployment. Throughout this process, several essential tools support the developer’s workflow. These tools include **version control**, **code libraries**, and **frameworks**.

---

## **Version Control（版本控制）**

- Tracks **who** made **what** changes and **when**
- Resolves conflicts in collaborative environments
- Useful even in solo development:
    - Allows reverting to previous versions
    - Helps understand project evolution over time
- Typically tied to a **code repository（代码仓库）**
- Recommended for all levels of developers

### **Common Tools**

- **Git**: A distributed version control system that tracks code changes and supports branching and merging
- **GitHub**: A cloud platform for hosting Git repositories and collaborating on projects

---

## **Code Libraries（代码库）**

- Pre-written sets of functions, programs, and subroutines reusable in your application
- Speeds up development by avoiding the need to write common features from scratch
- You call the library methods when needed; control returns to your program afterward
- Libraries are typically used to solve specific problems or add particular functionalities

### **Examples**

- **jQuery**: A JavaScript library for simplifying DOM manipulation（DOM 操作）
- **email-validator**: A small utility to validate email address formats
- **Apache Commons Proper**: A collection of reusable components for Java

---

## **Frameworks（开发框架）**

- Provide a **structured way** to build and deploy applications
- Act as a **skeleton** where you plug in your custom code
- Must be selected at the **beginning** of development
    - Not designed to be introduced mid-project

### **Characteristics**

- Define **architecture（架构）** and control **program flow（程序流程）**
- Enforce specific **project structure and conventions**
- Feature **Inversion of Control（控制反转）**:
    - The framework calls your code instead of you calling the framework
    - **使用框架的方式（控制反转）**：
        - 程序的整体流程由**框架决定**，你只是在指定位置写代码。
        - 框架在**它控制的流程中调用你写的函数或方法**。
        - 换句话说，**你写的代码被“注册”进框架，等框架需要的时候再去调用它**。
    - **而普通程序/使用库的方式**：
        - 你写的主程序掌控流程，你“主动”去调用库中的函数或方法。
        - 举例：你在代码里调用 validateEmail() 函数，这说明你控制了程序的流程。
- Offer less flexibility than libraries but greater standardization and reduced configuration work
- Often include built-in libraries for common tasks
- Some are **opinionated frameworks（强约束框架）**, which impose rules on:
    - File names
    - Directory structures
    - Coding patterns

### **Examples**

- **AngularJS**: JavaScript framework for building dynamic web applications
- **Vue.js**: Lightweight JavaScript framework focused on the UI（用户界面）
- **Django**: Python-based framework for scalable web development

---

## **Summary**

- **Version control（版本控制）** helps manage and track changes in your codebase.
- **Libraries（代码库）** provide modular solutions for specific tasks that you control.
- **Frameworks（开发框架）** define the overall structure and flow of your application with built-in control mechanisms.

These tools are foundational in modern software development, especially in cloud-based environments.

# **More Application Development Tools**

This lesson introduces additional tools that support the full lifecycle of app development and deployment, including **CI/CD**, **Build Tools**, **Packages**, and **Package Managers**.

---

## **CI/CD（持续集成/持续交付或部署）**

CI/CD is a best practice for devops teams enabling developers to deliver frequent changes reliably.

- **CI**: Continuous Integration（持续集成）
    - Developers frequently integrate code into a shared repository.
    - Ensures all components work together through **automated builds and tests**.
    - Performed using a **build-automation server（构建自动化服务器）**.
    - Encouraged to integrate **at least daily**, often **hourly** in fast-paced projects.
- **CD**: Continuous Delivery / Continuous Deployment（持续交付 / 持续部署）
    - Starts after CI completes.
    - Automatically delivers tested builds to **testing or staging environments（测试或预发布环境）**.
    - Allows fast, safe deployment of production-ready code.

---

## **Build Tools（构建工具）**

- Convert **source code（源代码）** into **binaries（可执行文件）**.
- Manage:
    - Source code organization
    - Compiler flags
    - Dependency tracking（依赖管理）
- Critical in multi-developer, multi-module environments.
- **Build Automation** is important because Building is complicated steps, easy to forget.
- The Building Automation tasks include:
    - Downloading dependencies
    - Compiling code
    - Packaging
    - Running tests
    - Deploying to production
- Build Tools → IDE or Command Line

### **Categories**

- **Build-automation utilities（构建自动化工具）**: e.g. compilers and bundlers
- **Build-automation servers（构建服务器）**: run utilities based on schedule or triggers

### **Examples**

- **Webpack**: Module bundler for JavaScript（JavaScript 模块打包工具）
- **Babel**: JavaScript compiler（JavaScript 编译器）
- **WebAssembly**: Binary instruction format that runs in browsers（浏览器可运行的二进制格式）

---

## **Packages（软件包）**

- Archive files containing:
    - App files
    - Installation instructions
    - Metadata (description, version, dependencies)
- Help make app installation **simple and user-friendly**.

---

## **Package Managers（软件包管理器）**

- Automate the process of:
    - Finding
    - Installing
    - Updating
    - Uninstalling software packages
- Tasks include:
    - Extracting archives
    - Verifying checksums and certificates
    - Managing dependencies
    - Interacting with software repositories

### **Examples by Platform**

- **Linux**: DPKG (Debian), RPM (Red Hat)
- **Windows**: Chocolatey
- **Android**: Package Manager
- **macOS**: Homebrew, MacPorts

**App Store / Microsoft Store / Google Play**：是**应用商店（Application Distribution Platforms），不算真正意义上的软件包管理器**

### **Examples by Programming Language**

- **Node.js / JavaScript**: npm
- **Java**: Gradle, Maven
- **Ruby**: RubyGems
- **Python**: pip, conda