# Code Organization Methods

## **Why Code Organization Matters**

- Good organization improves **readability**, **maintainability**, and **reliability**.
- Visually planning code helps reduce **bugs** and **errors**.
- Structured code enhances **consistency** and reduces confusion across the team.

---

## **Two Main Code Organization Methods**

### **1. Flowcharts（流程图）**

- A **graphical representation** of an algorithm using shapes and arrows.
- Best for:
    - Simple problems and concepts
    - Early-stage planning
- **Common symbols**:
    - Start/End → capsule（椭圆形，开始/结束）
    - Process → rectangle（矩形，过程）
    - Decision → diamond（菱形，条件判断）
    - Data/Input/Output → parallelogram（平行四边形，输入/输出）
    - Connectors → arrows（箭头，用于连接步骤）

### **Example**

### **: Adding Two Numbers**

1. Start
2. Input n1, n2
3. Sum = n1 + n2
4. Print Sum
5. End

### **Flowchart Tools**

- Microsoft Visio
- Lucidchart
- Draw.io
- DrawAnywhere

---

### **2. Pseudocode（伪代码）**

- A **textual outline** of a program using plain English-like instructions.
- Focuses on **logic**, not **syntax**.
- **Language-independent**, easy to translate into any code.

### **Benefits of Pseudocode**

- Easy for **beginners**
- Allows programmers and non-programmers to collaborate
- Emphasizes **what each line should do**, not how
- Easier to review and modify than real code
- More concise than flowcharts; usually under one page

```
// Input a number
IF number MOD 2 == 0
    PRINT "Even"
ELSE
    PRINT "Odd"
```