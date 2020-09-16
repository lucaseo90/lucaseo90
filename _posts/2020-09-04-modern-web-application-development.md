---
title: Modern Web Application Development
author_profile: true
read_time: true
comments: true
share: true
related: true
layout: single
tags: 
- jhipster
- study
---

### What is the full stack developer?
**Full stack developer** is the most popular developer title. The stack can be classified into two areas - **frontend** and **backend**.
* *frontend(client-side)* for the user interface.
* *backend(server-side)* for the business logic, database interactions, user authentication, server configuration, and so on.

A full stack Java web application developer is expected to work on both frontend and backend technologies. 

### How to make a web application?
1. Design the architecture and the domain model
2. Create server-side code and database queries for the domain model
3. Implement server-side code for business logic and API
4. Write integration tests for the API
5. Implement frontend code such as services and components 
6. Build the page and style 
7. Write automated end-to-end tests
8. Have tested whether everything works locally, and created pull requests or checked the code into the version control system used
9. Wait for the continuous integration process
10. Start the deployment to stage environment before the production environment when everything is ok
11. Repeat the step again and again for improving the software

#### Key technologies
* Client-side: HTML, JavaScript, build tools, transpilers, frameworks, and patterns
* Container technologies: Docker, container orchestration tools, and container management tools
* Cloud services: Their (maybe AWS, Asure, GCP) APIs and related orchestration tools
* (Javs) server-side technologies: JVM languages, such as Scala, Groovy, and Kotlin, and server-side frameworks

> **The most important thing of all is to make sure that all of these work well together when required.**

### Web architecture patterns
The **web application architecture patterns** can be classified into two patterns - **monolithic architecture** and **microservices architecture**

#### Monolitic web architecture
This architecture is the most widely used pattern for web applications
* Support different clients by exposing APIs like REST web services or message queues
* Handle HTTP requests, execute business logic, access database, and exchange data with other systems
* Run on web application containers, such as Tomcat and JBoss and by scaled vertically

#### Microservice architecture
This architecture is gaining popularity in large-scale web application development - modularity and scalability
* Support loosely coupled components and can be developed using the different technology - components can be lightweight and charge of specific functionality 
* Utilize advanced features such as service discovery, circuit breaking, and load balancing
* Have an extensive monitoring and troubleshooting setup

### Reference 
* Full stack development with JHipster, chapter 01. Introduction to Modern Web Application Development
