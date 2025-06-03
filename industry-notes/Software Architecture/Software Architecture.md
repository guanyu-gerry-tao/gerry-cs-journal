# Software Architecture

## **1. What Is Software Architecture?**

- **Software architecture** is the **organization of the software system（软件系统的组织结构）**
- Serves as a **blueprint（蓝图）** for developing components
- Captures **fundamental structures and design principles（基本结构与设计原则）**
- Defines:
    - **Component interactions（组件交互）**
    - **Operating environment（运行环境）**
    - **Non-functional attributes（非功能性需求）**

---

## **2. Importance of Well-Designed Architecture**

- Supports **stakeholder communication**（支持利益相关者沟通）
- Represents **early design decisions**（代表早期设计决策）
    - Costly to change later（后期更改成本高）
- Enables **agility** when requirements change（需求变更时能够保持敏捷性）
- Extends **lifespan of software**（延长软件生命周期）
- Guides:
    - **Technology stack choices**（技术栈选择）
    - **Production deployment decisions**（生产部署决策）

---

## **3. Tech Stack Considerations**

- **Tech stack** = software + programming languages + libraries + frameworks（技术组合）
- Architecture helps match the stack to **non-functional requirements**:
    - **Performance（性能）**
    - **Scalability（可扩展性）**
    - **Maintainability（可维护性）**
    - **Interoperability（互操作性）**
    - **Security（安全性）**
    - **Manageability（可管理性）**

---

## **4. Architecture Design Artifacts（架构设计产物）**

- **Software Design Document (SDD)**:
    - Describes **functional behavior（功能描述）**
    - Includes:
        - Assumptions（假设）
        - Dependencies（依赖）
        - Constraints（约束）
        - Objectives（目标）
        - Methodologies（方法）

URS（先有用户需求）
↓
SRS（转化为软件要做的功能）
↓
SDD（设计这些功能如何做出来）

SysRS 是并行或后续对系统层级进行补充

- **Requirements Documentation**：总称，所有需求相关的文件集合。
- **URS**：用户想要什么、为什么要，业务视角。
- **SRS**：软件具体要做什么，开发可落地的功能描述。
- **SysRS**：系统整体如何运作，涵盖软硬件与合规要求。

- **SDD**：软件准备怎么做这件事，设计思路和结构细节。不是Requirements的内容

- **Architectural Diagram（架构图）**:
    - Shows **components**, **interactions**, **constraints**, and **patterns used**
- **UML Diagrams（统一建模语言图）**:
    - **Standardized diagrams** showing structure and behavior
    - **Language-agnostic（不依赖具体编程语言）**

---

## **5. Deployment and Production Environment**

- Architecture drives decisions about **production environments（生产环境）**
- Includes:
    - **Infrastructure（基础设施）**: servers, databases, load balancers
    - Ensures the system can be **deployed and delivered to users**

> **Load balancers（负载均衡器）**：如何把请求合理分配给多个服务或服务器，保证系统可用性和性能
> 

---

# Architectural Pattern

1. ***Peer-to-peer***
    1. Consist of a decentralized network of nodes that behave both as client and as server
    2. P2P
        1. BitTorrent
        2. Bitcoin
2. ***Microservices***
    1. Have applications composed of several loosely coupled services that communicate using APIs
    2. 将一个应用拆分为多个**独立可部署的小服务**
    3. 每个服务只负责一个功能，服务之间通过 API 通信
        1. 亚马逊、Netflix 的后台服务
3. ***Event-driven***
    1. Have consumers that send requests to producers
    2. 系统中的组件通过**事件进行通信**
    3. 组件对事件作出反应，而不是持续等待调用
    4. **解耦合**，扩展性好
    5. 适合需要异步处理的场景
    
    ![image.png](gerry-cs-journal/industry-notes/Software%20Architecture/src/Software%20Architecture/image.png)
    
4. ***Two-tier***
    1. Clients communicates with a server
    2. 简单开发快，不适合复杂系统
        1. Access+Excel
5. ***Three-tier***
    1. Presentation, application, data
    2. 传统Web构架基础