# Implementation Specification Document 

## Introduction 

This document provides a detailed plan for implementing the process of creating a new vacancy through the selection of a template. Its purpose is to provide clear guidelines for the engineering department and project team members responsible for implementing the proposed solution. 

## Implementation Scope 

The implementation will involve adding a template system to the  vacancy creation process. This involves creating a new screen and modifying the vacancy creation screen to pre-load data from the selected template, allowing users to choose between creating a new vacancy from scratch or using one of the eleven most recently created vacancies as a template; including the creation of a API to obtain the latest vacancies. 

## Implementation Plan 

The following steps will be taken to implement the proposed solution: 

1.  Development of the api-hirers-caja-templates 

2.  Integrate the API into the application. 

3.  Incorporate the template system logic into the vacancy creation screen. 

4.  Implement tracking for Google Tag Manager. 

5.  Document the project. 

6.  Perform end-to-end testing using Cypress, including test design, development, execution, and release. 

7.  Test the new system in a development environment. 

8.  Implement OpenTelemetry for monitoring and visualization on both the front-end and back-end sides in Grafana. 

9.  Release the system during off-peak hours and conduct testing of changes in the production environment. 

## Technical Specifications 

The following are the software and hardware requirements for the implementation: 

* Node v14.18.0 

* Visual Studio Code 

* Postman or Insomnia 

* Access to Cisco VPN in development 

* PC or Laptop with a minimum of 8GB of RAM 

* Backend-login project to be running for login 

* OpenTelemetry 

* Grafana 

* Cypress 

* Drone 

* Go 

* ORM 

* Atomic 

* Gorm 

## Testing and Validation 

The following testing and validation plan will be implemented to ensure the successful implementation of the new vacancy template system: 

* Continuous automated testing to monitor the process of creating new vacancies, both from scratch and through the use of  templates . 

* Regression testing to identify any problems in the vacancy administrator caused by the implementation of the template system. 

* Functional and acceptance testing to verify that new vacancies are created based on a selected template. 

##Training and Support Plan 

The training and support plan aims to equip the product team with the necessary knowledge and tools to support the development team in conducting tests. The plan includes: 

* Thorough review of the template system documentation, including its features and functionalities. 

* Identification and analysis of the use cases of the template system and its integration with the vacancy creation process. 

* Deployment of the system in the production environment during off-peak hours. 

* Practical exercises to create test cases and perform tests using previously published vacancies. 

* Trace monitoring for service requests 

* Evaluation and feedback on the tests conducted by the development and product teams.(1,2) 

## Rollout Plan 

The rollout plan will include:   

* Deploying the new system to the production environment during off-peak hours.  

* Testing and verification of the system will be conducted to ensure a smooth transition.   

* A window will be provided  on AWS to revert to the  previous commit in case of any unexpected issues.   

* If there are no issues, the new system will be left in production and monitored with Cypress.   

* In case of any reports of issues or failures, a rollout to the previous version of recruiters-job-ads will be implemented. 

## Resources Required 

* Thorough documentation of the template system. 

* Access to previously published vacancies. 

* Tools for creating and managing test cases. 

* Test accounts. 

## Conclusion 

The implementation specification document outlines the implementation plan, technical specifications, testing and validation plan, training and support plan, and rollout plan for adding a template system to the vacancy creation process. 

## Appendix  

1.  Test Plan:  <https://github.com/occmundial/recruiters-job-ads/blob/master/docs/TestPlan.md> 

2.  Results Document: <https://github.com/occmundial/recruiters-job-ads/blob/master/docs/Results.md>
