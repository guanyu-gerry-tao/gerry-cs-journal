# Requirements

# Documents

Through out all phases

Documents are for technical and non-technical users

- System Documentation -> technical users / Design, Development, Testing
    - Readme
    - Inline Comments
    - Architecture and design documents
    - verification information
    - maintenance guides
- User Documentation -> non-technical users / Deployment, Maintainance
    - User guides
    - Instructional Videos
    - Manuals
    - Online or Inline help

# SRS

Gathering Requirements

1. Identify Stakeholders
2. Establishing goals and objectives
3. Eliciting requirements from stakeholders
4. Documenting the requirement
5. Analyzing and confirming the requirements
6. Prioritizing

## ID stakeholders

key personnel:

- Decision-makers
- End-users
- System Admins
- Engineering
- Marketing
- Sales
- Customer Support

Every group should have a representative

## Goal and Objectives

Goals:

- Customer outcomes
- Business Goal

Objectives: more specific

- actionable
- measurable - that actions can achieve goals

## Eliciting, Documenting, Confirming

- Eliciting
- Surveys
- Questionnaires
- Interviews

Document

- Align with goals and objectives
- Easy to understand

Confirming

- consistancy
- clarity
- completences

## Prioritizing

3 Levels
- Must have
- Highly Desired
- Nice to have

## Requirements Documentation

Requirements documentation != Documentations

Requirements documentation -> 内部文件 类比 任务书（建筑）

虽然不是合同，而是技术文件，但是合同常常refer要求

- 功能布局图（相当于 SRS）
- 设计任务书（相当于 URS）
- 系统图纸/水电图（相当于 SysRS）

Requirements documentation is internal management documentation,

- make sure everyone is doing what
- find and locate problems ahead
- set benchmark (what is right and what is not)
- Prevent Scope Creep
- legal record to talk with users

| 文档类型 | 谁撰写 (Author) | 谁确认 (Approver) | 谁使用/阅读 (Reader/User) |
| --- | --- | --- | --- |
| **URS**（User Requirements Specification） 用户需求说明 | - 用户代表（提供原始需求） - 业务分析师（BA）整理成文档 | - 用户（客户/委托方） - 产品经理（若有） | - 产品经理（定义功能） - 开发（理解背景） - 测试（UAT验收准备） |
| **SRS**（Software Requirements Specification） 软件需求说明 | - 业务分析师（BA） - 产品经理/开发负责人协助 | - 项目经理 - 技术负责人 - 客户（有时） | - 开发人员（实现功能） - 测试人员（编写测试用例） - 项目经理（进度跟踪） |
| **SysRS**（System Requirements Specification） 系统需求说明 | - 系统架构师 - 技术顾问 - 高级BA | - CTO / 技术总监 - 安全/运维负责人 | - DevOps（部署集成） - 架构师（系统规划） - 法规合规审核人（如有） |

### Software Requirements Specification - SRS

most common

- First Part
    - Capture functions that should perform
    - Establish benchmarks, service-levels for performance
    - Purpose and Scope
        - Purpose
            - Who has access to the SRS
            - How should it be used
        - Scope
            - Software benefits
            - Goals
            - Objectives
    - Constraints, assumptions and dependencies
    - Requirements
        - Functional: functions of the software
        - External interface: UI with hardware or software
        - System features: functions of the system
        - Non-functional: Performance, safety, security, quality
- Second Part
    - Constraints: how software must operate under what conditions
        - confirmation of standards
        - hardware limitation
    - Assumptions: Required OS or Hardware
    - Dependencies: on other software products?

### User Requirements Specification - URS

Describe the business need and the end-user expectation

- Who is user
- What is the function that needed
- Why does the user need it

Confirmed during UAT

often combined with the SRS

### System Requirements Specification - SysRS

Clearly outline the entire system

Broader than the SRS

contents:

- System capabilities
- Interfaces and user characteristics
- Policy requirements
- Regulation requirement
- Personnel requirement
- Performance requirement
- Security requirement
- System acceptance criteria
- Hardware expectation need