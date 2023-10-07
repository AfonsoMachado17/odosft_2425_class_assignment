# US 001 - Create Build Automation using Gradle + Node.js plugin 

## 1. Requirements Engineering


### 1.1. User Story Description

As a software developer, I want to create and use npm scripts and Gradle tasks, in order to automate my builds.


### 1.2. Customer Specifications and Clarifications 

No customer specifications, as this is an increment for the development team's processes


### 1.3. Acceptance Criteria


* **AC1:** "npm run build" should compile the system and create the build artifacts
* **AC2:** "gradle npm_run_build" should call the npm script using the Nodejs plugin for gradle
* **AC3:** "gradle build" should be a new Gradle task that works similarly to the others


### 1.4. Found out Dependencies


* There is a dependency to Node.js plugin for Gradle (https://github.com/node-gradle/gradle-node-plugin/tree/master)


### 1.5 Input and Output Data


**Input Data:**

* CLI command (no args)


**Output Data:**

* Build artifacts in "dist" folder
* CLI logs

### 1.6. System Sequence Diagram (SSD)

Not applicable

### 1.7 Other Relevant Remarks

No relevant remarks

## 2. OO Analysis

### 2.1. Relevant Domain Model Excerpt

Not applicable

### 2.2. Other Remarks

No remarks

## 3. Design - User Story Realization 

### 3.1. Rationale

**The rationale grounds on the SSD interactions and the identified input/output data.**

Not applicable


### Systematization ##

Not applicable

## 3.2. Sequence Diagram (SD)

Not applicable

## 3.3. Class Diagram (CD)

Not applicable

# 4. Tests

Only exploratory testing was made

**Test 1:** Run "npm run build"

**Test 2:** Run "gradle npm_run_build"

**Test 3:** Run "gradle build"

# 5. Construction (Implementation)

The "npm run build" script was already built in the "package.json" file.

The "gradle npm_run_build" task needed the Node.js for gradle plugin installation. The plugin allows for npm scripts to be run through Gradle.

The "gradle build" was created in build.gradle. It also depends on Node.js plugin for Gradle. Besides logging and cleaning the dist folder, it is an "NpxTask" to allow calling "npx tsc". The "tsc" dependency is the typescript compiler , used for building the application using the tsconfig.json file.

# 6. Integration and Demo 

Not applicable

# 7. Observations

Not applicable
