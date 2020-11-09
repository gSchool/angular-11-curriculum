# Arrange Act Assert (AAA)
[AAA](https://medium.com/@pjbgf/title-testing-code-ocd-and-the-aaa-pattern-df453975ab80) is a testing pattern that helps make the tests easier to read. Having a natural order to how we write tests makes it easier to adjust and understand what is going on.

## Arrange
This is where we instantiate or declare all the pieces need to run our test. This can be arranged on the individual test level or on the class test level. (Will you need the variable multiple times? Better to make it usable across multiple tests.)
```
Hashmap<String, String> actualInputes = new HashMap<>();
Hashmap<String, String> expectedOutputs = new HashMap<>();
```

## Act
In Act, we can do a few things. We can set fields for out variables or call another function to perform an action. In general, our act stage is where state changes and data manipulations should happen.
```
actualInputs.put("name", "tmobile");
actualInputs.put("industry", "telecomunications");
actualInputs.put("fav_color", "magenta");

expectedOutputs.put("tmobile", "name");
expectedOutputs.put("telecomunications", "industry");
expectedOutputs.put("magenta", "fav_color");
```

## Assert
Assert is the place to declare your expectation of the test once all other phases have run.
```
assertEquals(expectedOutputs, MainClass.reverseTheHash(actualInputs));
```
