# Development teamwork

# Front-end and Back-end work

Back‑end development powers the server‑side functionality that supports everything you do on a website or cloud app.

---

## **1. Front‑End vs. Back‑End Collaboration**

- **Front‑End** builds the user interface with HTML, CSS, JavaScript
- **Back‑End** creates and manages the server infrastructure
- Both teams must align on requirements and integration points
- Ongoing collaboration to add features and resolve issues

---

## **2. Core Responsibilities of Back‑End Developers**

- **Request Handling**
    - Process user inputs (search terms, form data, login)
    - Route requests via defined API endpoints
    - Return data or errors (e.g., 404 if no matching endpoint)
- **Data Management**
    - Query and update databases securely
    - Use SQL and/or ORM tools for data access
    - Design data schemas and optimize performance
- **Security & Authentication**
    - Implement user account management (login, permissions)
    - Securely handle sensitive data (addresses, credit cards)
    - Enforce encryption and safe storage practices

---

## **3. APIs, Routes & Endpoints**

API（抽象的接口定义）

└ 包含多个 Route（路径和请求方式的组合）

└ 每个 Route 对应一个 Endpoint（具体的请求入口）

### **API (Application Programming Interface)**

A set of rules and conventions that allow different software components to communicate.

前端与后端通信时，前端通过 API 发出请求，后端通过 API 返回数据。

- Defines rules for data exchange (often JSON/XML)
- Serves resources to web, mobile, and cloud clients

### **Routes**

指定“某个 URL + HTTP 方法（如 GET、POST）”被**映射到哪个后端逻辑**上处理。

A pattern that maps a client’s URL and HTTP method (GET, POST, etc.) to a specific back‑end function or controller.

- Map URL paths to back‑end services
- Pass request parameters to the correct handlers

### **Endpoints**

- 每个“URL + 方法”的组合就是一个 endpoint
- 是一个具体服务的入口

A specific URL (including its method) where an API service listens for requests. Every route defines one endpoint.

- Specific URI where an API service listens
- Return data or status messages in response
- If missing endpoint, 404 is returned

---

## **4. Common Back‑End Languages & Frameworks**

- **JavaScript (Node.js / Express)**
    - Leverages JavaScript on the server
    - Popular for full‑stack JS environments
- **Python (Django / Flask)**
    - Easy to learn, versatile for web, data, scripting
    - Django for “batteries‑included” features; Flask for minimalism
- **Other Technologies**
    - Java (Spring), Ruby (Rails), PHP (Laravel), etc.
    - Choice depends on project needs and team expertise

---

## **5. Working with Databases**

- **Relational Databases** (e.g., PostgreSQL, MySQL)
    - Use SQL for queries, joins, transactions
- **NoSQL Databases** (e.g., MongoDB)
    - Schema‑flexible, document‑oriented storage
    - example: JSON-like
- **ORM (Object‑Relational Mapping)**
    - Abstracts SQL into language‑native objects
    - Speeds development but understanding raw SQL remains valuable
    - ORM 不是替代数据库或 SQL/NoSQL 工具，而是建立在它们之上的一种抽象层。你可以这样理解：ORM 是“翻译官”，帮你把程序代码中的对象，**自动转换为数据库能理解的操作（SQL 或 NoSQL 调用）**。

```python
user = User(name="Alice")
print([user.name](http://user.name/))
```

# Teamwork and Squads

Collaboration plays a vital role in software engineering. Effective teamwork boosts creativity, code quality, and team morale.

---

## **1. What is Teamwork?**

- A **team** = a group working toward a shared goal
- Combines people with diverse skills and experience
- Enables individuals to:
    - Focus on their strengths
    - Learn new skills from teammates
- Encourages creativity through idea exchange and discussion
- Fosters accountability and better outcomes via shared ownership

---

## **2. Key Elements of Effective Teamwork**

- **Trust & Respect**
    - Built over time through equitable contributions
- **Defined Goals & Roles**
    - Prevents duplicated effort or overlooked tasks
- **Leveraging Strengths**
    - Maximizes each person’s impact
- **Celebrating Success & Analyzing Issues**
    - Reinforces good practices and continuous improvement
- **Effective Communication**
    - Shared tools and methods to ensure everyone stays aligned

---

## **3. Teamwork in Practice (Software Engineering)**

- **Kick-off Meetings**
    - Set project goals and assign roles
- **Ongoing Meetings**
    - Team/sub-team syncs to review progress
- **Code & Design Reviews**
    - Improve quality and encourage peer learning
- **Walkthroughs**
    - Presentations by team members to ensure visibility and alignment
    - Key members may walkthrough with stakeholders as well
- **Retrospectives (when project is complete)**
    - Review successes and challenges
- **Mentoring**
    - One-on-one or group learning to build skills and support growth
- **Internal Contributions**
    - Work on shared tools, coding standards, or infrastructure improvements

---

## **4. Benefits of Team Collaboration**

- Promotes **creativity** and **knowledge sharing**
- Encourages **clean, maintainable code** and **adherence to standards**
- Reduces stress—team members can rely on each other
- Improves problem-solving through discussion and multiple perspectives
- Helps developers see the **bigger picture** of the system

---

## **5. What are Squads?**

- Used in **Agile** organizations to describe a small (10 people), self-contained team
- **Typically includes:**
    - **Squad Leader**: Anchor developer and coach
    - **Product developers**: Build features and write tests
    - **UX Designers / developers**: Ensure usability and design
- Often practice **pair programming** (covered in another module)

# Peer Programming

Pair programming is a collaborative Agile practice where **two developers work together** on the same task, often at one workstation or via shared virtual setup.

---

## **1. What is Pair Programming?**

- Two developers share one task and one codebase
- Can be in-person (preferred) or remote (via screen sharing)
- Encourages constant discussion, joint planning, and iterative feedback
- Aims to improve code quality and developer learning

---

## **2. Styles of Pair Programming**

### **Driver/Navigator (most common)**

- **Driver** types the code
- **Navigator** gives direction, reviews code, and thinks about the overall design
- **Regular role-switching is essential to keep both engaged**

### **Ping-Pong**

- Based on **Test-Driven Development (TDD)**
- One developer writes a failing test
    
    > 第一个人写的不是功能代码，而是测试代码，这部分代码是为了验证功能是否存在、是否正确工作。
    > 
- The other writes code to pass the test
- Roles swap with each task
- Jointly refactor (重构) the solution after each round

**Example:**

步骤 1：A 写一个“失败的测试” （还没有功能代码）

```python
# test_calculator.py
from calculator import add

def test_add():
    assert add(1, 2) == 3
```

步骤 2：B 写“最小的代码”让测试通过。只写**刚好**能让测试通过的代码，不提前实现未来功能、不做过度设计。不要一次实现多个功能。

```python
# calculator.py
def add(a, b):
    return a + b
```

然后运行测试，✅通过。表示功能已实现，而且**只实现了需求里提到的那部分**。
****

**步骤 3：一起 Refactor（可选）**

### **Strong Style**

- Ideal for mentoring junior developers
- Rule: *“For an idea to go from your head to the computer, it must go through someone else’s hands”*
- Experienced dev is the **navigator**
- Junior dev is the **driver**
- Driver implements without challenging midway, learning through action

---

## **3. Benefits of Pair Programming**

- Enhances **technical skills** and **soft skills** (communication, collaboration)
- Speeds up onboarding of new team members
- Promotes **knowledge sharing**
- Reduces bugs and typos through real-time code review
- Improves solution quality by combining perspectives early
- May reduce time spent on post‑coding activities like testing and debugging

---

## **4. Challenges of Pair Programming**

- **Mentally exhausting** due to long sessions of focused collaboration
- **Schedule conflicts** can disrupt pairing continuity
- **Imbalance in contribution** may lead to one dominating (typist/programmer issue)
- **Personality mismatches** may affect productivity
- **Noise in shared spaces** when multiple pairs are discussing at once