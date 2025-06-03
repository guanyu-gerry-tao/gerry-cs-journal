# Interpreted and Compiled Programming Languages

This lesson introduces the difference between **interpreted** and **compiled** programming languages, their characteristics, use cases, and examples.

---

## **What Are Programming Languages?**

- Programming languages are **human-readable instructions** that tell computers what to do.
- Computers do not understand human language. They use **machine code（二进制机器语言）**, composed of 1s and 0s.
- Programming languages act as an intermediary between humans and machine code.

---

## **Two Major Categories of Programming Languages**

- **Interpreted Languages（解释型语言 / 脚本语言）**
- **Compiled Languages（编译型语言）**

---

## **Interpreted Programming Languages**

- Also known as **scripted languages（脚本语言）**
- Code is **executed line by line** using an **interpreter（解释器）**
- No need to compile before running the program
- Require the correct interpreter on the operating system or web browser

### **Characteristics:**

- More versatile, often easier to learn
- Portable across platforms (if interpreter is present)
- Often used in **web scripting** and **lightweight tasks**
- Interpreters may be built into browsers or installed separately

### **Examples:**

- **JavaScript**: Runs in web browsers（网页脚本语言）
- **Python**: Easy to learn and widely used（入门友好）
- **Lua**: Lightweight, used in games（轻量级游戏脚本）
- **HTML**: Used for web page structure（网页标记语言）

---

## **Compiled Programming Languages**

- Code is **converted into machine code** in advance by a **compiler（编译器）**
- Result is a **standalone executable file（可执行文件）**
- Runs faster and doesn’t require the source code at runtime
- Suitable for complex, large-scale applications and operating systems

### **Characteristics:**

- Higher performance and speed
- Can be executed repeatedly without recompilation
- Typically used in building applications like OS, desktop software, mobile apps

### **Examples:**

- **C, C++, C#**: Used in Windows, Linux, macOS（系统底层语言）
- **Java**: Compiled into bytecode, runs via JVM（Android 使用）

> Note:
> 
> 
> **Java ≠ JavaScript**
> 

---

## **Summary Comparison**

| **Feature** | **Interpreted Languages** | **Compiled Languages** |
| --- | --- | --- |
| Execution | Line-by-line via interpreter | Pre-compiled into one file |
| Speed | Slower | Faster |
| Portability | High (with interpreter) | Platform-dependent executable |
| Learning Curve | Easier | More complex |
| Typical Use | Web scripts, automation | OS, desktop, mobile software |
| Examples | JavaScript, Python, Lua, HTML | C, C++, C#, Java |