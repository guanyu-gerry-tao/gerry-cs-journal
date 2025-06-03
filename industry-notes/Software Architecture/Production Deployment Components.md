# Production Deployment Components

## **1. Overview of a Typical n-Tier Deployment（n层架构部署概览）**

A standard **n-tier architecture** in production often includes the following layers (from top to bottom):

1. **Presentation Tier（表示层）**
    - Front-end clients (e.g., browser or mobile app)
    - Outside the firewall
2. **Web Tier（网页层）**
    - **Web Load Balancer（网页负载均衡器）** distributes requests to multiple **Web Servers（网页服务器）**
3. **Application Tier（应用层）**
    - **App Load Balancer / Proxy Server（应用负载均衡器 / 代理服务器）** routes to **App Servers（应用服务器）**
4. **Data Tier（数据层）**
    - **Database Server（数据库服务器）**
    - May include **High-Availability Replica（高可用副本）** for reliability

---

## **2. Key Components Explained**

### **Firewall（防火墙）**

- **Purpose**: Security device that monitors and filters traffic between networks
- **Function**:
    - Blocks unauthorized access (e.g., hackers, malware)
    - Allows or denies traffic based on defined rules
    - Sits at the **network boundary**

---

### **Load Balancer（负载均衡器）**

- **Purpose**: Distribute incoming requests evenly across servers
- **Function**:
    - Prevents overload on any single server
    - Maximizes **availability（可用性）** and **responsiveness（响应速度）**
    - Handles **concurrent client requests（并发请求）**
    - Two types in architecture:
        - **Web Load Balancer**: for distributing web traffic
        - **App Load Balancer**: for routing to application servers

---

### **Web Server（网页服务器）**

- **Delivers static content**: HTML, CSS, JavaScript, images, videos
- **Responds to HTTP requests** from clients (usually browsers)

---

### **Application Server（应用服务器）**

- Runs **server-side business logic（业务逻辑）**
- Provides application functionality to clients
- Interfaces with the **database** for reading/writing data
- Offloads logic from client devices

---

### **Proxy Server（代理服务器）**

- Acts as an **intermediary** between tiers
- Multiple purposes:
    - **Load balancing**, **caching**, **encryption**
    - Acts as firewall, hides request source (anonymity)
    - Enhances **efficiency**, **privacy**, **security**

---

### **Database Server（数据库服务器）**

- Stores and manages structured data
- Controlled by a **DBMS (Database Management System，数据库管理系统)**
- Connects to application via DBMS to allow:
    - **Data storage**
    - **Data retrieval**
    - **Data manipulation**

---

## **Summary Table**

| **Component** | **Role** |
| --- | --- |
| **Firewall** | Filters and protects traffic between networks |
| **Load Balancer** | Distributes requests across multiple servers |
| **Web Server** | Delivers static content (HTML, images, etc.) |
| **App Server** | Executes application logic and interacts with database |
| **Proxy Server** | Intermediary with caching, security, and optimization features |
| **Database Server** | Stores and manages application data |