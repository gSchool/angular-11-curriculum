# Red, Green, Refactor
It's important to remember that [Red, Green, Refactor](https://medium.com/@tunkhine126/red-green-refactor-42b5b643b506) is an iterative cycle. The goal is not to write all your tests at once, the same way the goal isn't to write all code at once. Rather, take turns between writing a "failing test" and writing the smallest amount of code possible to get that test to pass. 

### Red
Red is the stage where you write your `failing test`. A failing test will fail when first written because the code it's testing shouldn't exist.

### Green
Green is where you write your actual code to satisfy the conditions of the failing test. This code should not be verbose and should only implement behavior directly tied to the test written. At this point the goal is simply to get the test to pass, not make the code pretty.

### Refactor 
Refactor is the stage where you apply your experience and skill to optimize and refine the code you just implemented. At this point you might consider your formatting, naming conventions, scope, and potential to refactor previously written code and tests.
