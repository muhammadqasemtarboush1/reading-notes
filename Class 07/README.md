# Class 07:

## Python Scope & the LEGB Rule: Resolving Names in Your Code

### what is Scope rules
Name defines the area of a program in which you can unambiguously access that name, such as variables, functions, objects, and so on. A name will only be visible to and accessible by the code in its scope
### LEGB 
Local, Enclosing, Global, and Built-in scopes

there are two general scopes:
1. Global scope: The names that you define in this scope are available to all your code.

2. Local scope: The names that you define in this scope are only available or visible to the code within the scope.


* For example, 
  * if you assign a value to a name inside a function, then that name will have a local Python scope. In contrast, if you assign a value to a name outside of all functions—say, at the top level of a module—then that name will have a global Python scope.

### Python Scope vs Namespace
In Python, the concept of scope is closely related to the concept of the namespace. As you’ve learned so far, a Python scope determines where in your program a name is visible. Python scopes are implemented as dictionaries that map names to objects. These dictionaries are commonly called namespaces. These are the concrete mechanisms that Python uses to store names. They’re stored in a special attribute called .__dict__.

### Using the LEGB Rule for Python Scope
They are named after the Python scope for names. The letters in LEGB stand for Local, Enclosing, Global, and Built-in. Here’s a quick overview of what these terms mean:
* Local (or function) scope is the code block or body of any Python function or lambda 
expression. This Python scope contains the names that you define inside the function.
These names will only be visible from the code of the function. 

* Enclosing (or nonlocal) scope is a special scope that only exists for nested functions.
If the local scope is an inner or nested function, then the enclosing scope is the scope
of the outer or enclosing function. This scope contains the names that you define in the
enclosing function. The names in the enclosing scope are visible from the code of 
the inner and enclosing functions.

* Global (or module) scope is the top-most scope in a Python program, script, or module. 
This Python scope contains all of the names that you define at the top level of a program 
or a module. Names in this Python scope are visible from everywhere in your code.

* Built-in scope is a special Python scope that’s created or loaded whenever you run 
a script or open an interactive session. This scope contains names such as keywords,
functions, exceptions, and other attributes that are built into Python.

### dir()
To inspect the names within your main global scope, you can use dir(). If you call dir() without arguments, 
then you’ll get the list of names that live in your current global scope.

ex :
>>dir()
>  >
>> ['__annotations__', '__builtins__',..., '__package__', '__spec__']
> >
>> var = 100  # Assign var at the top level of __main__
> >
>> dir()
> >
>>['__annotations__', '__builtins__',..., '__package__', '__spec__', 'var']

_Good programming practice recommends using local names rather than global names. Here are some tips:_
* Write self-contained functions that rely on local names rather than global ones.
* Try to use unique objects names, no matter what scope you’re in.
* Avoid global name modifications throughout your programs.
* Avoid cross-module name modifications.
* Use global names as constants that don’t change during your program’s execution.

summary of the implications of Python scope are shown in the following table:

| Action                                                        | Global Code | Local Code	                                      | Nested Function Code                              |
|---------------------------------------------------------------|-------------|--------------------------------------------------|---------------------------------------------------|
| Access or reference names that live in the global scope	      | Yes         | Yes                                              | Yes                                               |
| Modify or update names that live in the global scope	         | Yes         | No (unless declared global)                      | No (unless declared global)                       |
| Access or reference names that live in a local scope	         | No          | Yes (its own local scope), No (other local scope | Yes (its own local scope), No (other local scope) |
| Override names in the built-in scope	                         | Yes         | Yes (during function execution)                  | Yes (during function execution)                   |
| Access or reference names that live in their enclosing scope	 | N/A         | N/A                                              | Yes                                               |
| Modify or update names that live in their enclosing scope	    | N/A         | N/A                                              | No (unless declared nonlocal)                     |

### The global Statement
With this statement, you can define a list of names that are going to be treated as global names.
All the names that you list in a global statement will be mapped to the global or module scope in which you define them.

### The nonlocal Statement
 With a nonlocal statement, you can define a list of names that are going to be treated as nonlocal.
can be accessed from inner functions, but not assigned or updated. If you want to modify them, then you need to use a nonlocal statement

* Unlike global, you can’t use nonlocal outside of a nested or enclosed function. To be more precise, you can’t use a nonlocal statement in either the global scope or in a local scope.

### Using Enclosing Scopes as Closures
Closures are a special use case of the enclosing Python scope. When you handle a nested function as data,
the statements that make up that function are packaged together with the environment in which they execute. 


## Notes:
* We’ll be using the term name to refer to the identifiers of variables, constants, functions, classes, or any other object that can be assigned a name.
* There’s an important difference between assignment operations and reference or
access operations. When you reference a name, you’re just retrieving its content 
or value. When you assign a name, you’re either creating that name or modifying it.
* If you call the same function multiple times, or recursively. Each call
will result in a new local scope being created.
* Python assumes that names assigned in the body of a function are local to that function.
* > The use of global is considered bad practice in general. If you find yourself using global to fix problems 
like the one above, then stop and think if there is a better way to write your code.
  > 
## [Source](https://realpython.com/python-scope-legb-rule/#conclusion)

