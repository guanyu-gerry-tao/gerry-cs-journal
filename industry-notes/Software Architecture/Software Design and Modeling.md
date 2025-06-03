# Software Design and Modeling

## **1. Overview**

- **Software Design** involves documenting the **structural components** and **behavioral attributes** of a system before development.
- One major activity is **modeling**, which uses diagrams to express:
    - The overall software system
    - Its sub-components
    - Interactions between components

---

## **2. Structured Design（结构化设计）**

- Breaks down a problem into smaller, organized **modules（模块）** and **sub-modules（子模块）**
- Focus: **Organization**, **Cohesion**, and **Coupling**

### **Key Principles:**

- **Cohesion（内聚性）**: Related functionality is grouped together within a module（将相关功能组织在同一模块中）
- **Coupling（耦合性）**: Degree of dependency between modules（模块之间的依赖程度）
    - **Loose coupling** is preferred: modules can change independently（松耦合更受欢迎：模块可以独立变化）
    - Common in **Service-Oriented Architecture** and **Microservices**（常见于面向服务架构和微服务中）

![image.png](gerry-cs-journal/industry-notes/Software%20Architecture/src/Software%20Design%20and%20Modeling/image.png)

### **Example:**

- A billing system:
    - Main module: Billing
    - Sub-modules: Insurance Verification, Submit Claim, Output Total
    - Arrows show **data flow（数据流）**

![image.png](gerry-cs-journal/industry-notes/Software%20Architecture/src/Software%20Design%20and%20Modeling/image%201.png)

---

## **3. Behavioral Models（行为模型）**

- Describe **what a system does**, **not how** it does it.
- Focus on **system behavior** in response to **events** or **interactions**

---

## **4. UML (Unified Modeling Language) 统一建模语言**

- A **standardized, language-agnostic** way to visualize system architecture and behavior
- Divided into two main types:
    - **Structural diagrams（结构图）**
    - **Behavioral diagrams（行为图）**

### **Benefits:**

- **Plan features** before coding → saves time and cost
- Help new team members **understand system structure quickly**
- **Bridge communication** between technical and non-technical stakeholders
- Serve as a **map for navigating source code**

---

## **5. State Transition Diagram（状态转换图）**

- A type of **behavioral UML diagram**
- Describes:
    - **States（状态）** of a system
    - **Events（事件）** that trigger transitions between states

### **Example:**

- A patient visiting a clinic:
    - States: Waiting, Testing, With the doctor
    - Arrows: labeled with **triggering events（触发事件）**

![image.png](gerry-cs-journal/industry-notes/Software%20Architecture/src/Software%20Design%20and%20Modeling/image%202.png)

---

## **6. Interaction Diagram（交互图）**

- Models the **dynamic behavior** of objects in the system
- 是Behavior Diagram的一种
- **Sequence diagrams（时序图）** show:
    - **Objects（对象）**
    - **Messages sent over time（消息随时间的传递）**

### **Example:**

- Patient making an appointment in an online portal

![image.png](gerry-cs-journal/industry-notes/Software%20Architecture/src/Software%20Design%20and%20Modeling/image%203.png)

| **元素** | **含义** |
| --- | --- |
| 左边的小人（actor） | 表示“**用户**”（病人） |
| 每个方框 | 表示一个“**对象/组件**”，比如 Appointment 模块、Server |
| 虚线（lifeline） | 表示对象在整个流程中的“存在时间” |
| 箭头 | 表示对象之间**发送的消息/调用的操作** |
| 从上到下 | 代表**时间顺序**（越往下时间越晚） |

| **类型** | **图示** | **名称** | **含义** |
| --- | --- | --- | --- |
| **实线箭头** | ➝ | **Synchronous Message（同步消息）** | 表示**调用一个操作或方法**，发送者会**等待**接收者处理完成 |
| **虚线箭头** | ╌╌╌➝ | **Return Message（返回消息）** | 表示**处理完后的返回值或结果**，返回给调用者 |

### **1️⃣病人 → Appointment**

### **：Select doctor**

- 用户在界面上选择医生
- 这个动作触发前端（Appointment 模块）开始工作

---

### **2️⃣Appointment → Patient（返回）**

### **：Offer times**

- Appointment 查询后端数据，查出可预约时间
- 然后把**候选时间**返回给用户（图中向左的箭头）

---

### **3️⃣病人 → Appointment**

### **：Submit appt（提交预约）**

- 用户选好了时间后点击“预约”
- 前端模块把预约信息发送出去

---

### **4️⃣Appointment → Server**

### **：Submit appt**

- Appointment 模块把预约信息传给 Server（服务器）

---

### **5️⃣Server → Appointment**

### **：Confirm appt**

- 服务器处理完后返回“预约成功”

---

### **6️⃣Appointment → 病人**

### **：Confirm appt**

- 最后前端告诉病人：“预约成功”

---

## **✅ 总结流程图（按步骤）**

1. 病人选择医生
2. Appointment 提供可预约时间
3. 病人提交预约请求
4. Appointment 把请求交给服务器
5. Server 返回确认信息
6. Appointment 显示确认结果给病人

![image.png](gerry-cs-journal/industry-notes/Software%20Architecture/src/Software%20Design%20and%20Modeling/image%204.png)