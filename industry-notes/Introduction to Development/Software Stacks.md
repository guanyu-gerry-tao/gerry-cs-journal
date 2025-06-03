# Software Stacks

This lesson explains the concept of **software stacks**, introduces common stack configurations, and compares the advantages and challenges of different stack choices.

---

## **What is a Software Stack?**

- A **software stack** is a **combination of software technologies** used to develop and run applications.
- It includes:
    - **Front-end technologies**: UI frameworks, JavaScript libraries, design tools
    - **Back-end technologies**: servers, databases, operating systems, programming languages
- Technologies are **stacked hierarchically**:
    - Higher layers serve the user
    - Lower layers interact with the hardware
- Also known as a **technology stack（技术栈）**, especially when it includes infrastructure components (e.g., virtual machines, load balancers)
- Technology stack is broader term.

---

## **Stack Structure**

- A basic software stack includes:
    - **Presentation Layer**: UI/UX layer
    - **Business Logic Layer**: Application rules and logic
    - **Data Layer**: Data storage and management
- More complex stacks may include:
    - **Virtualization**（虚拟化）, **orchestration**（编排）, **runtime environments**（运行环境）, **security layers**（安全层）, etc.

### **Stack Composition**

- Components may come from:
    - Internal teams
    - Third-party vendors
    - Cloud providers
- No fixed structure: any combination that supports application development, functionality, or deployment is valid
- Not all layers are required—only those relevant to your project

---

## **Examples of Software Stacks**

### **Python-Django Stack**

- **Python**: General-purpose programming language（编程语言）
- **Django**: Web development framework（Web 开发框架）
- Used for large, fast-evolving applications
- Fully open-source

### **Ruby on Rails Stack**

- **Ruby**: Programming language
- **Rails**: Server-side web application framework
- Good for data exchange (JSON/XML) and front-end with HTML/CSS/JavaScript

### **ASP.NET Stack**

- Microsoft technologies:
    - **ASP.NET MVC**
    - **IIS Web Server**
    - **SQL Server**
    - **Azure Cloud Platform**

---

## **LAMP Stack（Linux, Apache, MySQL, PHP）**

- **Linux**: Operating system（操作系统）
- **Apache**: Web server
- **MySQL**: Relational database（关系型数据库）
- **PHP**: Server-side scripting language
- Open-source and modular (can swap components, e.g., PostgreSQL → LAPP, Python → LAMP with Python)
- Well-supported, mature stack
- Disadvantages:
    - Linux dependency limits flexibility (not platform-agnostic)平台相关
    - PHP on the backend + JavaScript on the frontend makes context-switching harder for developers

---

## **MEAN Stack（MongoDB, Express.js, Angular.js, Node.js）**

- **MongoDB**: NoSQL database（非关系型数据库）
- **Express.js**: Back-end web framework
- **Angular.js**: Front-end JavaScript framework
- **Node.js**: Server-side JavaScript runtime
- Fully JavaScript-based
- Benefits:
    - Unified language (JavaScript) throughout the stack
    - Free and open-source
    - Large ecosystem and reusable modules
- Challenges:
    - Not ideal for large-scale systems
    - MongoDB lacks relational features
    - Business logic in Express.js can limit service reuse

---

## **MEVN Stack（MongoDB, Express.js, Vue.js, Node.js）**

- Same as MEAN but uses **Vue.js** (lightweight front-end framework)
- Similar benefits to MEAN
- Vue.js has better performance than Angular.js but fewer reusable libraries

---

## **MERN Stack（MongoDB, Express.js, React, Node.js）**

- Same as MEAN but uses **React** (front-end library by Facebook)
- Flexible, high-performance front-end
- Very popular for modern single-page applications