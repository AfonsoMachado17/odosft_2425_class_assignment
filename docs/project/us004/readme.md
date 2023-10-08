# US 004 - Build Automation using Node.js scripts

This file documents the differences between unit tests and API tests, and the patterns used thoughout the testing process within this project.

This project uses "jest", a Javascript / Typescript testing framework that provides many usefull features, such as code coverage and mocking. Moreover, for the API tests, "axios" is the tool used as the Rest client, in other words, the tool used to create the HTTP requests.

## Unit Tests

Unit tests focus on a single segment (unit) of the code, and test if it was implemented correctly. They help detecting bugs and edge case results.

### Patterns

 * Unit test suites test their counterpart file, identified by the name of the test file by removing ".spec" from their name (ex. Guard.ts is tested in file Guard.spec.ts). 1 to 1 relation.

 * Unit tests are part of the project, and are located in the same layer as their functional counterpart file.

 * Unit tests don't require the application to be running. Their execution will start the app and run only the test cases.

 * Unit tests are abstract to their dependencies, if they have any (tests at the domain layer have no dependencies). This can be achieved by using mocks, doubles, fakes, ...

 * Due to the nature of unit testing, each test case tests a very specific scenario.



## API Tests

API tests focus on the functionalities exposed by an API. Requests are made to the endpoints of an API and the response is evaluated.

### Patterns

 * These tests are not part of the project, and are implemented outsite of the code base (at ~/src/api_tests).

 * To correctly mimic a working environment, the application and all its dependencies needs to be running, as requests are performed against a fully working backend API.

 * To ensure the same environment in each test execution, stateful components (such as the database) need to be reset / restarted at each execution.

 * Each test case tests a variation of how a request could be made to an endpoint.

 * These tests are a subgroup of Functional Acceptance Tests, therefore, their goal is to test the business functionality aspect of a service.



## Running the Tests

There are 3 npm scripts to run the tests.

**npm run test** - Invokes "jest". All test suites are called. An HTML test-report will be generated. To ignore the api tests add "-- --testPathIgnorePatterns=api"

**npm run test:dev** - Invokes "jest" in "watch mode". This mode allows the tester to specify a set of tests to run instead of the complete test suite.

**npm run test:api** - Deletes and recreates the database, to ensure a clear environment at each execution. Afterwards, runs "jest" with code coverage analysis only for the API tests.
