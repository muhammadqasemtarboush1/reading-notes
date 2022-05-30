# Testing and Modules

## Test-Driven Development in Python

### What is TDD

 a process that has been documented considerably over recent years. A process of baking your tests right into your everyday coding, as opposed to a nagging afterthought, should be something that developers seek to make the norm, rather than some ideal fantasy.

*~ This approach allows you to escape the trap that many developers fall into. ~*

The process can be defined as such:

* Write a failing unit test
* Make the unit test pass
* Refactor
>
> ### Syntax for Unit Testing
>
> * assert: base assert allowing you to write your own assertions
> * assertEqual(a, b): check a and b are equal
> * assertNotEqual(a, b): check a and b are not equal
> * assertIn(a, b): check that a is in the item b
> * assertNotIn(a, b): check that a is not in the item b
> * assertFalse(a): check that the value of a is False
> * assertTrue(a): check the value of a is True
> * assertIsInstance(a, TYPE): check that a is of type "TYPE"
> * assertRaises(ERROR, a, args): check that when a is called with args that it raises ERROR

>
### Some Packages For Testing

* py.test
  * It's framework makes it easy to write small, readable tests, and can scale to support complex functional testing for applications and libraries.

> #### Why use PyTest?
>
> * Very easy to start with because of its simple and easy syntax.
>* Can run tests in parallel.
>* Can run a specific test or a subset of tests
>* Automatically detect tests
>* Skip tests
>* Open source

## Python Modules and Packages – An Introduction

There are actually three different ways to define a module in Python:

1. A module can be written in Python itself.

2. A module can be written in C and loaded dynamically at run-time, like the re (regular expression) module.

3. A built-in module is intrinsically contained in the interpreter, like the itertools module.

### List

List literals are written within square brackets [ ]. Lists work similarly to strings -- use the len() function and square brackets [ ] to access data, with the first element at index 0.

## Recursion

### What is Recursion

The process in which a function calls itself directly or indirectly is called recursion and the corresponding function is called a recursive function. Using a recursive algorithm, certain problems can be solved quite easily.

### Recursion VS Iteration

| Recursion  | Iteration |
| --- | ----------- |
| Terminates when the base case becomes true.  | Terminates when the condition becomes false.|
 | Used with functions.  |Used with loops. |
 | Every recursive call needs extra space in the stack memory.  |Every iteration does not require any extra space. |
|  Smaller code size.  |Larger code size. |

<br></br>

## Things I want to know more about

1. How to deal with pytest in real world projects
2. Know and get the best benefits from Recursion used case
