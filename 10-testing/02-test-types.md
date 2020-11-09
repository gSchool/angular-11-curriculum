# Test Types

### !callout-info
There are literally 10s to 100s of testing patterns, types, style and languages. If interested, take a look at [this article](https://www.softwaretestingmaterial.com/types-of-software-testing/) to get a better picture at how verbose testing can be. 
### !end-callout

The 2 most common types of test.

## Unit
Unit testing is the most common and possibly valuable form of testing. When we implement unit testing we are only concerned with the logic that is contained inside a single function.

### !callout-info
As example, say our requirements are for an endpoint that:
- retrieves a list of measurements from a database
- converts the values from metric to standard
- sorts the list from largest to smallest  
Taking the second requirement we would `FIRST` write a test to show what we will expect our function to do. Then we write the code to fulfill that test. However, we won't write test or code for the sort logic as it will have a separate test. 
### !end-callout

## Integration
Integration testing is a step above unit testing. Use integration testing to verify that a group of components, methods or classes produce the expected output given a specific input.

### !callout-info
As example, say our requirements are for an endpoint that:
1. retrieves a list of measurements from a database
2. converts the values from metric to standard
3. sorts the list from largest to smallest

Integration testing in not concerned with the inner workings of a single method. Instead, integration testing says, "If I query the endpoint for a list will it: retrieve, convert and sort as expected."
### !end-callout

## Other Types of Tests

Regression, Smoke, Alpha, Beta, System, Stress & Performance are all different types of testing used for specific use cases. Keep in mind that at times the different testing methodologies can be used, combined or altered depending on the task and requirements at that time.
