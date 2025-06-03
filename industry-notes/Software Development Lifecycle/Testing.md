# Testing

A part of SDLC 

To ensure:

1. function meet requirement
2. no error

# Test cases:

In order to test, team writes “test cases”

to verify the functionality and ensure requirement is satisfied

in various phases of SDLC

Content:

1. Steps
2. Data
3. Inputs
4. Expected Output

# 3 types of testing

## functional testing

Test: Usability and Accessibility

Usually use “black box” method, or System Under Test SUT

only concern input-output

may use manual or automatic tool

## non-functional testing

Test: Performance, Security, Scalability, Availability

Answer the question:

1. How does Apps work under stress
2. What if many users log in at same time
3. Are instruction consistent with behavior
4. Does App work same under different OSs
5. How does App handle disaster recovery
6. How secure is App

## regression testing

Confirms changes don’t break the application

make sure bug fix doesn’t hurt existing functionality

Need to be performed after **change in requirement** or **fixing bugs**

Test cases need to be selected

- Have frequent defects
- Frequent function
- recent features
- complex cases
- edge cases - 极端情况，极大值极小值，非法值等
- unstable features

# Testing Levels

1. Unit
2. Integration
3. System
4. Acceptance

## Unit

Testing of a module of code

by developer

Eliminate error before integration

## Integration

Identify errors after many units combine and interact

Type of Black-box

## System

System testing evaluate after integration testing

evaluate whole system’s compliance with requirement

Functional / Non-functional

Done in Staging environment - Similar to production environment

## Acceptance

Formal testing with user needs, requirement, business etc

Done by customer, stakeholders

at the end of SDLC