# Architectural Patterns in Software

## **Definition**

- An **architectural pattern** is a **repeatable solution（可复用的解决方案）** to a common software architecture problem.
- Patterns define internal structures and relationships between software components.
- Not covered pattern:
    - **Model-View-Controller (MVC)**: Separates application into model (data), view (UI), and controller (logic) for better modularity（将数据、界面、控制逻辑分离，提高模块化）
    - **Message-Broker**: Uses an intermediary to route messages between decoupled services（通过中介传递消息，使服务解耦）
    - **Blackboard**: Components share a common data space and work collaboratively to solve complex problems（通过共享数据黑板，不同组件协作解决问题）
    - **Pipe-and-Filter**: Processes data through a sequence of independent steps (filters) connected by pipes（数据依次通过独立步骤处理，适合流式处理）
    - **Controller-Responder**: Separates request handling from response generation in web systems（将请求处理与响应生成分离，常用于 Web 架构）

---

## **1. Two-Tier Architecture（二层架构）**

- Also known as **client-server architecture（客户端-服务器架构）**
- Structure:
    - **Client** (UI or interface) sends requests
    - **Server** provides services or data in response

### **Use Cases:**

- Text messaging apps
- Database client/server applications

---

## **2. Three-Tier Architecture（三层架构）**

- Most common pattern, also called **n-tier architecture**
- Organized into horizontal layers:
    - **Presentation Tier（表现层）**: UI (user interface)
    - **Application Tier（应用层）**: Business logic
    - **Data Tier（数据层）**: Database management

### **Key Properties:**

- Tiers only communicate with adjacent tiers
- Loose coupling between layers
- Easy to maintain and scale

### **Use Cases:**

- Web applications with:
    - Web server (presentation)
    - Application server (logic)
    - Database server (data)

---

## **3. Peer-to-Peer (P2P，对等网络架构)**

- **Decentralized** network model
- Each **node（节点）** acts as both **client and server**
- Peers share resources like storage, bandwidth, or computation

### **Use Cases:**

- Cryptocurrency (e.g., Bitcoin, Ethereum)
- File sharing, messaging, collaborative platforms

---

## **4. Event-Driven Architecture（事件驱动架构）**

- Components are triggered by **events（事件）**
- Two roles:
    - **Producer（事件生产者）**: Emits event messages
    - **Consumer（事件消费者）**: Listens and reacts to events
- An **event router（事件路由器）** can determine which consumer receives which event

### **Use Cases:**

- Ride-sharing apps (e.g., Uber, Lyft)
- Systems requiring real-time updates or reactions

---

## **5. Microservices Architecture（微服务架构）**

- Application is split into **independent services（独立服务）**
- Each service performs a specific business task
- Communication is handled via:
    - **API Gateway（API网关）**
    - **Orchestration（服务编排）**

### **Key Features:**

- Services are **loosely coupled**
- Can be deployed, scaled, and maintained independently
- Each service can have its own tech stack

### **Use Cases:**

- Social media platforms (e.g., Facebook)
    - Services for account, news feed, ads, messaging, etc.

---

## **6. Combining Patterns（组合架构模式）**

- **Architectural patterns are not mutually exclusive**
- Possible combinations:
    - Three-tier + Microservices
    - Peer-to-peer + Event-driven

### **Limitation:**

- Some cannot be combined:
    - P2P ≠ Two-tier (P2P nodes are both client and server; two-tier separates them)

---

## ✅ **Summary**

| Pattern | Key Concept | Example |
| --- | --- | --- |
| **Two-tier** | Client-server model | Messaging app, database app |
| **Three-tier** | UI + Logic + Data | Typical web apps |
| **Peer-to-peer** | Decentralized, resource sharing | Cryptocurrency |
| **Event-driven** | Trigger-response mechanism | Uber/Lyft |
| **Microservices** | Independent, modular services | Social media apps |