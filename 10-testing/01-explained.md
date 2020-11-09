# TDD Explained

## What is TDD
[Test Driven Development](https://medium.com/javascript-scene/tdd-changed-my-life-5af0ce099f80) (TDD) is a development practice that requires tests to be written before code, 100% of the time.
- Write a failing test (red)
- Write the minimum amount of code to get the test to pass (green)
- Review the written code and test for efficiency (refactor)

## Why use TDD
- Saves Time
    - Tests not properly written or nonexistent make diagnosing and resolving bugs a potentially tedious task. At times the stacktrace and error message don't bring us to the exact location of the problem; requiring us to manually log inputs and output until we spot the issue.
- Save Money
    - As developers our ability to maximize our efficiency and quality is a major responsibility. If we are wasting time debugging untested code we are making the best use of our time.
- Save Energy
    - Debugging can be frustrating, especially when it isn't your code you are trying to fix and test. Ensuring we test appropriately helps everybody involved enjoy our code a little more.

## Where do tests go
- The goal of testing is to make sure the code behaves as expected. As such the tests themselves should be contained as closely to the source as possible. However, different circumstances require different strategies, so the true answer comes from a conversation with your team.

## How are tests written
- Like everything else in software: libraries, plug-ins, languages and strategies are plentiful with just as many opinions to go with them. A test plan could refer to naming convention, language or tech used for testing, coverage requirements, the list goes on. The important part is documentation, and an agreement between those involved in the development of the product.

## Whose responsibility is testing
- Especially when talking about TDD, the responsibility of implementing the test of the tests lies upon the developer who wrote the code. The catch is the team is responsible for reviewing your code (because Pull Requests are awesome) and making sure you test meet the guidelines agreed upon by the team.

## When to test
- Before implementation of code
- Before merging in code
- Before deploying new code
