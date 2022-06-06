# Class 4

## Classes and Objects

Objects are an encapsulation of variables and functions into a single entity. Objects get their variables and functions from classes. Classes are essentially a template to create your objects.

> ex:

    class MyClass:

      variable = "blah"

      def function(self):
          print("This is a message inside the class.")
to assign the above class(template) to an object you would do the following:
> ex:

    class MyClass:
      variable = "blah"

      def function(self):
        print("This is a message inside the class.")

    myobjectx = MyClass()

### init()

> The __init__() function, is a special function that is called when the class is being initiated. It's used for asigning values in a class.

ex:

      class NumberHolder:
        def __init__(self, number):
           self.number = number

### [Source](https://www.learnpython.org/en/Classes_and_Objects)

## Pytest :Fixtures

> In testing, a fixture provides a defined, reliable and consistent context for the tests. This could include environment (for example a database configured with known parameters) or content (such as a dataset).

- They can used to define a test’s act phase; this is a powerful technique for designing more complex tests.

### Fixtures Errors

pytest does its best to put all the fixtures for a given test in a linear order so that it can see which fixture happens first, second, third, and so on. If an earlier fixture has a problem, though, and raises an exception, pytest will stop executing fixtures for that test and mark the test as having an error.

<br />
There is more examples and improvments on the source take a look at it

### [Source](https://docs.pytest.org/en/latest/explanation/fixtures.html)

## Coverage

> Used Case: when software gets larger and more complex, it's not going to be so easy to eyeball it. That where you want to have "code coverage", checking that your tests have run all of the code.

### [Source](https://www.linuxjournal.com/content/python-testing-pytest-fixtures-and-coverage)

## Things I want to know more about

- Learn how to create a completely app based on classes
- Learn how to create  act phase tests
- Sharing test data
- Coverage in action tests

## Things I like it in reading topics

- When a test is marked as having an error, it doesn’t mean the test failed, though. It just means the test couldn’t even be attempted because one of the things it depends on had a problem.
