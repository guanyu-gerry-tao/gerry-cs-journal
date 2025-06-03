# Object-Oriented Analysis and Design (OOAD)

## **1. What is OOAD?**

- OOAD stands for **Object-Oriented Analysis and Design（面向对象分析与设计）**
- It’s a methodology for analyzing and designing software systems using **object-oriented programming languages** (e.g., Java, C++, Python) OOP
- Focuses on **objects（对象）** that contain both **data（数据）** and **behavior（行为）**
- Objects interact to form a working system

---

## **2. Object vs. Class（对象 vs 类）**

### **Class（类）**

- A **blueprint/template（蓝图/模板）** for creating objects
- Defines:
    - **Attributes（属性/数据）**: e.g., LastName
    - **Methods（方法/行为）**: e.g., CancelAppointment()

### **Object（对象）**

- An **instance（实例）** of a class
- Created through a process called **instantiation（实例化）**
- Carries real values for the attributes
- Can execute its defined methods

### **Example:**

- Patient class → defines generic attributes and methods
- Naya Patel → an object (instance) of the Patient class
    - Has LastName = "Patel"
    - Can call CancelAppointment()

---

## **3. Purpose of OOAD**

- Breaks the system into **interacting objects**
- Enables **modular design**: multiple developers can work independently on different objects
- Promotes **reusability（可复用性）** and **maintainability（可维护性）**

---

## **4. UML Class Diagram（类图）**

- A **structural UML diagram（结构图）** that visualizes the classes in a system and their relationships
- Each box = a **class**
    - Top section: **class name**
    - Middle section: **attributes**
    - Bottom section: **methods**

### **● Class Relationships:**

- **Inheritance（继承）**: subclass inherits attributes/methods from a parent class
- Example:
    - MedicalPersonnel is the parent
        - Nurse, Doctor, Technician inherit from it
    - Specialist is a subclass of Doctor, so:
        - Specialist inherits from Doctor, and thus indirectly from MedicalPersonnel

![image.png](gerry-cs-journal/industry-notes/Software%20Architecture/src/Object-Oriented%20Analysis%20and%20Design%20(OOAD)/image.png)