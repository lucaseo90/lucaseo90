---
title: Building Monolithic Web Applications with JHipster
---

# The environment 

# Application generation
## Preparing the workspace
Create a new folder for the workspace

```bash
$mkdir e-commerce-app
$cd e-commerce-app
```

Create a new folder for the application

```bash
$mkdir online-store
$cd online-store
```

## Generating code using JHipster
Initialize JHipster

```bash
$jhipster
```
### Server-side options
### Client-side options
### Modules
# Code walkthrough
## File structure
## Server-side source code
## Client-side source code
# Starting the application
Execute the Gradle command

```bash
$cd online-store
$./gradlew
```

or

```bash
./gradlew webpack bootRun -Pdev
```
# Running generated tests
## Server-side tests
In the **src/test/java** folder

```bash
$./gradlew test integrationTest
```
## Client-side tests
In the **src/test/javascript** folder

See all available Gradle tasks 

```bash
$./gradlew tasks
```

Run Jest unit tests

```bash
$npm test
```

Run Protractor end-to-end(e2e) tests (The server should be running)
* The test will open a new Chrome brower instance and execute tests there.  

```bash
$npm run e2e
```
