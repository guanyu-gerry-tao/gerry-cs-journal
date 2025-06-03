# Programming Concepts

# **Introduction to Programming Concepts – Part 1**

## **1. Identifiers（标识符）**

- Used to **reference program components（引用程序组件）**, such as:
    - Variables（变量）
    - Constants（常量）
    - Methods（方法）
    - Classes（类）
- Give meaningful names to values or structures in code for readability and maintenance.

---

## **2. Constants（常量）**

- A **fixed value** that does not change during program execution.
- Examples:
    - Mathematical constant: pi = 3.14
    - Text constant: "PlayerName"
- Benefits:
    - **Improves readability（提高可读性）**
    - **Easier to update** (change value in one place instead of many)
- Also called **named constants（具名常量）**

---

## **3. Variables（变量）**

- A value that **can change during the program’s execution（程序运行过程中可改变）**
- Examples: user input, high score, username
- Types:
    - String（字符串）
    - Integer（整数）
    - Boolean（布尔值） etc.
- Benefits:
    - Avoids hardcoding
    - Can be assigned initially or later in the program

---

## **4. Containers（容器）**

- Special identifiers that **store multiple elements（存储多个元素）**
- Avoids creating many individual variables (e.g., 1,000 integers)

### **Array（数组）**

- **Fixed size container（固定大小容器）**
- Stores **elements of the same type（相同类型元素）** in **sequential memory（连续内存）**
- Indexing starts at **0**
- Syntax (C/C++-like):

```cpp
int numbers[10];
```

### **Vector（向量/动态数组）**

- **Dynamic size container（动态大小容器）**
- **Automatically resizes（自动扩容）** when adding/removing elements
- Uses more memory and is slightly slower than arrays (due to non-contiguous memory)
- Syntax (C++-like):

```cpp
vector<int> numbers;
```

Vector有点像Python的List

---

# **Introduction to Programming Concepts – Part Two**

## **1. Functions（函数）**

### **What is a Function?**

- A **structured, stand-alone, reusable block of code（结构化、独立、可重用的代码块）**
- Performs a **single, specific task（单一具体任务）**
- Core part of **modular programming（模块化编程）**

### **Why Use Functions?**

- Breaks a complex program into **manageable, logical parts**
- **Improves readability and reusability（提升可读性与可重用性）**

### **Types of Functions:**

- **Standard Library Functions（标准库函数）**
    
    e.g. print(), if, while (provided by the language)
    
- **User-defined Functions（用户自定义函数）**
    
    You write them once, and reuse them anywhere
    

### **Function Workflow:**

1. **Define** (create) the function
2. **Call** (invoke) the function when needed
3. (In C/C++): May also need to **declare** the function before defining it

### **Language-Specific Syntax:**

- Braces {} (C/C++)
- begin / end (Pascal)
- Indentation (Python)

---

## **2. Objects（对象）**

### **What is an Object?**

- Central concept in **Object-Oriented Programming (OOP，面向对象编程)**
- An object combines:
    - **Data** → called **properties** or **attributes（属性）**
    - **Behaviors** → called **methods（方法）**

### **OOP vs Procedural Programming:**

| **方法论** | **聚焦点** | **数据与逻辑的关系** |
| --- | --- | --- |
| **OOP** | Objects（对象） | 绑定在一起 |
| **Procedural** | Functions（过程） | 分离 |

### **Real-world Analogy:**

- Object = Thing in real world (e.g. car, washing machine)
- Ask:
    - What **states（状态）** can it be in?
    - What **behaviors（行为）** can it perform?

### **Software Objects Examples:**

- Windows service（系统服务）
- User account（用户账户）
- Database table（数据库表）
- System folder（系统文件夹）

### **Terminology Mapping:**

| **概念** | **通用术语** | **在某些语言中的别称** |
| --- | --- | --- |
| **Property** | Field（字段） | Variable（变量） |
| **Method** | Function（函数） | Procedure（过程） |

---