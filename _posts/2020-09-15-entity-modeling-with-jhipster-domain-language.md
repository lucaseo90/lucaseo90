---
title: Entity Modeling with JHipster Domain Language
tags: 
- jhipster
- study
toc: true
toc_sticky: true
---

# What is the JDL
## DSL grammer 
## Entity modeling
## Relationship management
## DTO, service, and pagination options
## JDL-Studio
## Use case 
# Entity generation with JHipster
Execute the `import-jdl` command

```bash
$cd online-store
$jhipster import-jdl online-store.jdl
```

## Generated code walkthrough
## Server-side 
## Client-side
## Generated pages
Execute the Gradle command

```bash
$./gradlew
```

If the server is already running, you just need to compile the source. Spring DevTools will hot reload the application.

```bash
$./gradlew compileJava
```

## Running the generated tests
Execute these commands

```bash
$./gradlew test integrationTest && npm test && npm run e2e
```
