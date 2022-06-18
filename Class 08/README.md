# Class 08

## List Comprehensions in Python

### What is it?

List comprehension is a powerful and concise method for creating lists in Python that becomes essential the more you work with lists, and lists of lists.

### Syntax

my_new_list = [ expression for item in list ]

#### Create a List with range()

```

# construct a basic list using range() and list comprehensions
# syntax
# [ expression for item in list ]
digits = [x for x in range(10)]

print(digits)
```

Output:

```
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```

#### Create a List Using Loops and List Comprehension in Python

```python
# create a list using a for loop
squares = []

for x in range(10):
    # raise x to the power of 2
    squares.append(x**2)

print(squares)
```

output:

```python
[0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
```

The same thing can be done using a list comprehension, but with a fraction of the code. Let’s take a look at how to create a list of squares using the list comprehension method.

```python
# create a list using list comprehension
squares = [x**2 for x in range(10)]

print(squares)
```

Also, some examples of list comprehension:

* Multiplication

```python
multiples_of_three = [ x*3 for x in range(10) ]
```

* Even Numbers:

```python
 even_numbers = [ x for x in range(1,20) if x % 2 == 0] 
```

* With Strings

```
letters = [ name[0] for name in authors ]
```

* Separating the characters in a string

```python
letters = [ letter for letter in "20,000 Leagues Under The Sea"]
```

* Changing a letter’s case

```python
lower_case = [ letter.lower() for letter in ['A','B','C'] ]
upper_case = [ letter.upper() for letter in ['a','b','c'] ]
```

* Example 7: Identify numbers in a string using the isdigit() method

```python
user_data = "Elvis Presley 987-654-3210"
phone_number = [ x for x in user_data if x.isdigit()]
```

* Reading a poem with list comprehensions

```python
file = open("dreams.txt", 'r')
poem = [ line for line in file ]
```

* Adding arguments to list comprehension

```python
def double(x):
    return x*2
nums = [double(x) for x in range(1,10)]
```

## Notes

* List comprehension methods are an elegant way to create and manage lists.
* In Python, list comprehensions are a more compact way of creating lists.
* More flexible than for loops, list comprehension is usually faster than other methods.

### [Source](https://www.pythonforbeginners.com/basics/list-comprehensions-in-python)

## PySnooper

### What is PySnooper

 is a poor man's debugger. If you've used Bash, it's like set -x for Python, except it's fancier.

### Installation with

* pip:
  * $ pip install pysnooper
* Conda:
  * $ conda install -c conda-forge pysnooper
* Arch Linux:
  * $ yay -S python-pysnooper
* Fedora Linux:
  * $ dnf install python3-pysnooper

### Why do you need it?

 You can use it in your shitty, sprawling enterprise codebase without having to do any setup.
 Just slap the decorator on, as shown below, and redirect the output to a dedicated log file
 by specifying its path as the first argument.

### Example

```python
@pysnooper.snoop()
def number_to_bits(number):
    if number:
        bits = []
        while number:
            number, remainder = divmod(number, 2)
            bits.insert(0, remainder)
        return bits
    else:
        return [0]

number_to_bits(6)
```

### Features

* If stderr is not easily accessible for you, you can redirect the output to a file:
  * @pysnooper.snoop('/my/log/file.log')
  * You can also pass a stream or a callable instead, and they'll be used.
* See values of some expressions that aren't local variables:
  * @pysnooper.snoop(watch=('foo.bar', 'self.x["whatever"]'))
* Show snoop lines for functions that your function calls:
  * @pysnooper.snoop(depth=2)

and much more to Read them or to git more about this topic you can visit the Source

### [Source](https://pypi.org/project/PySnooper/)

## Primer on Python Decorators

### Short Summary

Decorators we can write them like so:
*They can be reused.

* They can decorate functions with arguments and return values.
* They can use @functools.wraps to look more like the decorated function.

## Things I want to know more about

I would like if there will be practical  using  for the Decorators through this advance course.
