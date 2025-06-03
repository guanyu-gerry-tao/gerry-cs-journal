# Query and Assembly Programming Languages

1. 语言分高级和低级语言
2. 解释型语言和编译型语言都是高级语言
3. 低级语言包括机器码和汇编语言
4. 低级语言例如x86，是以字符表示机器码的底层语音，直接控制机器
5. SQL是解释型语言
6. “高级/低级语言” 和 “编译型/解释型语言” 是两种完全不同的分类维度，它们不能混为一谈，但可以交叉组合使用。

| **组合** | **举例** |
| --- | --- |
| 高级语言 + 编译型 | C, C++, Swift |
| 高级语言 + 解释型 | Python, JavaScript, SQL |
| 低级语言 + 编译型 | Assembly（汇编语言，用 assembler 翻译） |
| 低级语言 + 解释型 | ❌ 几乎不存在（机器太近，不能实时解释） |

## **1. Programming Language Levels**

### **High-Level Programming Languages（高级语言）**

- Use English-like syntax to improve readability and debugging.
- Abstract away hardware details.
- Faster for development.
- Examples:
    - **Query Languages（查询语言）**: SQL
    - **Structured Programming Languages（结构化编程语言）**: Pascal
    - **Object-Oriented Programming Languages（面向对象编程语言）**: Python

### **Low-Level Programming Languages（低级语言）**

- Use symbolic representations of machine code（用字母表示二进制机器码）.
- Offer precise control over hardware.
- Require more effort to learn and write.
- Examples:
    - **Assembly Languages（汇编语言）**: ARM, MIPS, x86

---

## **2. Query Languages（查询语言）**

### **Definition**

- Used to retrieve or manipulate data in a **database（数据库）**.
- Allow communication between user applications and databases.

### **Common Language:**

### **SQL (Structured Query Language 结构化查询语言)**

- Used for **CRUD operations（增删改查）**:
    - **Create（创建）**
    - **Read（读取）**
    - **Update（更新）**
    - **Delete（删除）**

### **Types of SQL Statements（SQL 语句类型）:**

- **SELECT**: query and retrieve data
- **INSERT / UPDATE / DELETE / CREATE**: manipulate data
- **Administrative**: manage users and permissions

### **Other Query Languages:**

- **AQL**, **CQL**, **Datalog**, **DMX**

### **SQL vs NoSQL (Not Only SQL):**

- **SQL databases（关系型数据库）**: structured schema（结构化模式）, predefined tables
- **NoSQL databases（非关系型数据库）**: dynamic schemas（动态结构）, handle unstructured data

---

## **3. Assembly Languages（汇编语言）**

### **Definition**

- Symbolic language that directly represents machine code.
- One-to-one mapping between instructions and machine operations.
    - 比如你在 C 语言写：’total = (a + b) * 2’, 实际上会有
        - 从内存取出 a
        - 从内存取出 b
        - 把它们相加
        - 把结果乘以 2
        - 把结果放回变量 total 的位置
- Each CPU architecture（处理器架构）has its own assembly syntax.

### **Translation:**

- Translated using an **assembler（汇编器）**, not a compiler（编译器）or interpreter（解释器）.

```nasm
[label:]  MNEMONIC  OPERANDS  ; comment
```

- **Mnemonic（助记符）**: symbolic name of the instruction (e.g., LDA, STA, ADD)
- **Operand（操作数）**: the data or location being referenced
- **Opcode（操作码）**: actual machine-level instruction

Example:

```nasm
mov TOTAL, 212   ; Transfer the value 212 into the memory variable TOTAL
```

### **Characteristics:**

- Very close to hardware, very fast
- Harder to learn and write than high-level languages
- Used in embedded systems（嵌入式系统）, drivers（驱动程序）, and performance-critical code