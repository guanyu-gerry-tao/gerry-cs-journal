# Approaches to Application Architecture

# **1. Components（组件）**

- A **component** is a unit of encapsulated functionality（封装的功能单元） that contributes to an application when combined with other components.

### **Six Key Characteristics of Components**

- **Reusable**（可复用）: Can be used in multiple systems.
- **Replaceable**（可替换）: Can be swapped with another component without impacting the system.
- **Independent**（独立）: Has minimal dependencies on other components.
- **Extensible**（可扩展）: New behavior can be added without changing other components.
- **Encapsulated**（封装）: Internal state and logic are hidden; only interfaces are exposed.
- **Non-context-specific**（非上下文相关）: Can function in different environments; context passed externally.

### **Examples of Components**

- **API**: Reusable interfaces like database connectors.
- **DAO (Data Access Object)**: Abstracts database logic, allowing for easy switching.
- **Controller**: Determines and manages which components are called in response to events.

---

## **2. Component-Based Architecture**

- Focuses on decomposing a system into **loosely coupled（低耦合）**, **independent components（独立组件）**.
- Provides a higher level of abstraction than object-oriented design.
- Encourages **modular composition（模块化组合）**.

---

## **3. Services vs. Components**

| **Feature** | **Component（组件）** | **Service（服务）** |
| --- | --- | --- |
| Scope | Internal logic | Business functionality |
| Deployment | Within app | **Independently deployable（可独立部署）** |
| Reuse | App-level | System-level |
| Instance | Multiple | **Single instance with many clients（单例，多客户端）** |
- A **service** is a type of component.
- A **service** consists of one or more components and is accessed remotely via a communication protocol.

---

## **4. Service-Oriented Architecture (SOA，面向服务架构)**

- An architecture style where services:
    - Are **loosely coupled**（低耦合）
    - Communicate over a network using protocols (e.g., HTTP)
- Services solve **business-level problems（业务问题）** and can be reused across systems.

---

## **5. Distributed Systems（分布式系统）**

- A system where **multiple services run on different machines** but appear as a single coherent system to the user.

### **Key Characteristics:**

- **Resource Sharing**（资源共享）: Hardware, software, data
- **Fault-Tolerant**（容错）: System continues running despite node failures
- **Concurrent Execution**（并发执行）: Improves speed and throughput
- **Scalability**（可扩展性）: Can grow with user demand
- **Heterogeneous**（异构）: Supports different hardware, OS, languages

### **Node（节点）**

- Any device on a network that can send, receive, or process data

---

## **6. Architecture Styles Used in Distributed Systems**

- **Client-server（客户端-服务器）**
- **Three-tier（三层架构）**
- **Peer-to-peer（对等网络）**
- **Microservices（微服务）**