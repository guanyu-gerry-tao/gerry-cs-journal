# Application Deployment Environments

- Application Environment
    - Pre-production Environment
        - Dev
        - QA
        - Staging
    - Production Environment

## **1. What Is an Application Environment?**

An **application environment** includes all hardware and software resources required to run an application, such as:

- Application code and binary files
- Required software stack（软件栈）
- Third-party libraries and middleware（中间件）
- Operating system（操作系统）
- Networking infrastructure（网络基础设施）
- Physical or virtual hardware: CPU, memory, storage

---

## **2. Pre-Production Environments（预生产环境）**

Used during development and testing stages before production.

### **Development Environment（开发环境）**

- Where the application is actively coded
- Often just the developer’s local machine

### **QA or Testing Environment（质量保证/测试环境）**

- Used by QA teams to test functionality, performance, bugs

### **Staging Environment（预发布环境）**

- Mimics the production environment as closely as possible
- Not available to end users; used for final validation

---

## **3. Production Environment（生产环境）**

- The **live system** accessed by actual users
- Must support **heavy load（负载）**, **security（安全）**, **reliability（可靠性）**, and **scalability（可扩展性）**
- Most complex and robust of all environments

---

# **Deployment Options（部署方式）**

### **On-Premises（本地部署）**

- All infrastructure is physically housed and managed in the organization
- Provides **maximum control and security**
- **More expensive** and requires internal maintenance
- Protected by firewalls（防火墙）

### **Public Cloud（公共云）**

- Hosted by cloud providers (e.g., AWS, Azure, Google Cloud)
- Shared infrastructure over the internet
- **Scalable and cost-effective**
- Most commonly used

### **Private Cloud（私有云）**

- Dedicated cloud infrastructure for a single organization
- May be on-premises or hosted by a provider (e.g., AWS Private Cloud)
- Offers **better security and customization**

### **Hybrid Cloud（混合云）**

- Combines public and private cloud infrastructures
- Aims to **optimize cost, security, and flexibility**

---

## **Summary**

| **Environment Type** | **Purpose** |
| --- | --- |
| **Development** | Active coding and early testing |
| **QA / Testing** | Formal testing by QA team |
| **Staging** | Final validation before release |
| **Production** | Live deployment for end users |

| **Deployment Model** | **Key Traits** |
| --- | --- |
| **On-Premises** | Full control, high cost |
| **Public Cloud** | Scalable, low cost, shared |
| **Private Cloud** | Secure, customizable |
| **Hybrid Cloud** | Flexible, balanced model |