# SDLC Software Development Life Cycle

- Systematic process to develop high-quality software 系统开发流程
- To make software meeting requirements 满足需求
- Defined phases with processes and deliverables 明确阶段
- Cycle of **Planning, Design, Development** 开发周期
- Minimize risks, costs 降低风险

Conceived 1960s

Advantages:

- more efficiency 提高效率
- less risks 降低风险
- Members know what and when should they do 明确任务
- Facilities communication with stakeholders 促进沟通
- Members know they have complete the tasks, and move to next phase 明确进度
- Can response to changes 应对变化
- Problem solving is early in process 及早解决
- Reduce overlapping responsibility 减少重叠

## Phases

1. Planning
2. Designing
3. Developing
4. Testing
5. Deployment
6. Maintenance

each phase is discrete -> phase do not overlap with earlier one

### Planning Phase

Know

- Purpose
- Input / Output requirements
- User identification
- Compliance requirements
- Risk identification
- Quality assurance needs
- Resource allocation
- Project scheduling

Labor, time, money cost, member

**Prototype**

Prototyping is needed to tease out the requirements

to test design idea

prototype is needed in various stages

**Software Requirements Specification documents (SRS Documents)**

Need to be clearly understand

approved by stakeholder

Stakeholders need to involve

### Design Phase

requirements -> gather into software architecture

Team member gather to design architecture

architecture reviewed by stakeholders and team

Prototype is designed at this phase

**Design document**

created in design phase

used by developers during the development phase

### Development

Building phase or implementation phase

will start once the design document is finished

Produce planners use design documents to assign coding tasks

**Code Quality**

Such as

- Maintainability
- Readability
- Testability
- Security

Also

- Clean and consistent
- Easy to read and maintain
- Well documented
- Efficient

**Coding for quality**

is a set of practice:

- Following coding standards
- using linters to detect errors
- commenting to make it easy to understand and modify

### Testing Phase

Once development is completed, testing is started
Some big firms have testing team dedicated

ensure:

- stable
- security
- meet requirement of SRS

Bug is reported -> tracked -> fixed -> retested

**Testing level**

Unit testing

Down by developers, test small parts of the code

Isolated from system

integrating testing

See if tested code fit the larger code

system testing

When larger product is finished, system testing take place

acceptance testing

UAT -> by users

UAT (User Acceptance Testing) environment 用户验收测试（内测）

Release to inner user to test

Users UAT on platforms

### Deployment Phase

release to production environment and make available to users

Once users accept, will release to public (product environment)

Apply to website, mobile app store etc, software distribution server on corp etc

**Releases**

- Alpha - Testing
    - selected stakeholders
    - may have errors
    - preview of functioning version
    - Design may change
- Beta - Testing and Deployment
    - All stakeholders
    - User testing
    - have all functions
- GA - General Availability - Deployment
    - Stable version
    - All users

### Maintenance Phase

After deployment, maintenance helps identify bugs, UI issues, and additional requirements.

Code enhancements occur during this phase.

High-priority issues must be fixed immediately, while other changes are documented in the SRS for future development.