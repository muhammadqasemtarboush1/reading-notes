# Class 29

Live link: [React](https://muhammadqasemtarboush1.github.io/reading-notes/Class%2030/)

## ES6 Syntax and Feature Overview

ECMAScript 2015, also known as ES6, introduced many changes to JavaScript. Here is an overview of some of the most
common features and syntactical differences, with comparisons to ES5 where applicable.

> Legend

Here is a key of most identifier names used throughout this reference.

* Variable: x
* Object: obj
* Array: arr
* Function: func
* Parameter, method: a, b, c
* String: str

### Variables and constant feature comparison

* var:
  * Scope: Function scope
  * Hoisting: Yes
  * Can Be Reassigned: Yes
  * Can Be Redeclared: Yes
* let:
  * Scope: Block scope
  * Hoisting: No
  * Can Be Reassigned: Yes
  * Can Be Redeclared: No
* const:
  * Scope: Block scope
  * Hoisting: No
  * Can Be Reassigned: No
  * Can Be Redeclared: No

### Arrow functions

```javascript
func = (a) => {} // parentheses optional with one parameter
let func = (a, b, c) => {} // parentheses required with multiple parameters
```

### Template literals

#### Concatenation/string interpolation

```javascript
let str = `Release Date: ${date}`
```

#### Multi-line strings

```javascript
let str = `This text
            is on
            multiple lines`
```

#### Implicit returns

```javascript
let func = (a, b, c) => a + b + c // curly brackets must be omitted
```

#### Key/property shorthand

```javascript
let obj = {
  a,
  b,
}
```

#### Method definition shorthand

The function keyword can be omitted when assigning methods on an object.

```javascript
ES5
var obj = {
  a: function (c, d) {},
  b: function (e, f) {},
}

ES6
let obj = {
  a(c, d) {},
  b(e, f) {},
}

obj.a() // call method a

```

### Destructuring (object matching)

Use curly brackets to assign properties of an object to their own variable.

```javascript
ES5
var obj = {a: 1, b: 2, c: 3}
ES5
var a = obj.a
var b = obj.b
var c = obj.c


ES6
let {a, b, c} = obj

```

### Array iteration (looping)

```javascript
var arr = ['a', 'b', 'c']

ES5
for (var i = 0; i < arr.length; i++) {
  console.log(arr[i])
}

ES6
for (let i of arr) {
  console.log(i)
}
```

### Default parameters

```javascript
ES5
var func = function (a, b) {
  b = b === undefined ? 2 : b
  return a + b
}

ES6
let func = (a, b = 2) => {
  return a + b
}
func(10) // returns 12
func(10, 5) // returns 15
```

### Spread syntax

Spread syntax can be used to expand an array.

```javascript
ES6
let arr1 = [1, 2, 3]
let arr2 = ['a', 'b', 'c']
let arr3 = [...arr1, ...arr2]

console.log(arr3) // [1, 2, 3, "a", "b", "c"]

// Spread syntax can be used for function arguments.
let arr1 = [1, 2, 3]
let func = (a, b, c) => a + b + c

console.log(func(...arr1)) // 6
```

### Classes/constructor functions

ES6 introducess the class syntax on top of the prototype-based constructor function.

```javascript
ES5
function Func(a, b) {
  this.a = a
  this.b = b
}

Func.prototype.getSum = function () {
  return this.a + this.b
}

var x = new Func(3, 4)
ES6
class Func {
  constructor(a, b) {
    this.a = a
    this.b = b
  }

  getSum() {
    return this.a + this.b
  }
}

let x = new Func(3, 4)
x.getSum() // returns 7
```

### Inheritance

The extends keyword creates a subclass.

```JavaScript
ES5

function Inheritance(a, b, c) {
  Func.call(this, a, b)

  this.c = c
}

Inheritance.prototype = Object.create(Func.prototype)
Inheritance.prototype.getProduct = function () {
  return this.a * this.b * this.c
}

var y = new Inheritance(3, 4, 5)

ES6

class Inheritance extends Func {
  constructor(a, b, c) {
    super(a, b)

    this.c = c
  }

  getProduct() {
    return this.a * this.b * this.c
  }
}

let y = new Inheritance(3, 4, 5)
y.getProduct() // 60
```

### Modules - export/import

Modules can be created to export and import code between files.

```html
index.html
<script src="export.js"></script>
<script type="module" src="import.js"></script>
```

export.js

```JavaScript
let func = (a) => a + a
let obj = {}
let x = 0

export {func, obj, x}
```

import.js

```javascript
import {func, obj, x} from './export.js'

console.log(func(3), obj, x)
```

### Promises/Callbacks

Promises represent the completion of an asynchronous function. They can be used as an alternative to chaining functions.

```javascript
ES6 Promise

let doSecond = () => {
  console.log('Do second.')
}

let doFirst = new Promise((resolve, reject) => {
  setTimeout(() => {
    console.log('Do first.')

    resolve()
  }, 500)
})

doFirst.then(doSecond)
```

An example below using XMLHttpRequest, for demonstrative purposes only (Fetch API would be the proper modern API to use).

```javascript
ES6 Promise
function makeRequest(method, url) {
  return new Promise((resolve, reject) => {
    let request = new XMLHttpRequest()

    request.open(method, url)
    request.onload = resolve
    request.onerror = reject
    request.send()
  })
}

makeRequest('GET', 'https://url.json')
  .then((event) => {
    console.log(event.target.response)
  })
  .catch((err) => {
    throw new Error(err)
  })
```

## Note

* A commonly accepted practice is to use const except in cases of loops and reassignment. However, in this resource I'll
  be using let in place of var for all ES6 examples.
* **!Important note**:
  * *** The arrow function expression syntax is a shorter way of creating a function expression. Arrow functions do
      not have their own this, do not have prototypes, cannot be used for constructors, and should not be used as object
      methods.**
* The return keyword is implied and can be omitted if using arrow functions without a block body.

* Warning:

Since JSX is closer to JavaScript than to HTML, React DOM uses camelCase property naming convention instead of HTML attribute names.

For example, class becomes className in JSX, and tabindex becomes tabIndex.

* Recommend using the “Babel” language definition for your editor of choice so that both ES6 and JSX code is properly highlighted.

* Always start component names with a capital letter.
React treats components starting with lowercase letters as DOM tags. For example, <div /> represents an HTML div tag, but <Welcome /> represents a component and requires Welcome to be in scope.

*

## Resources

### [ES6 Syntax and Feature Overview](https://www.taniarascia.com/es6-syntax-and-feature-overview/)

### [Hello world](https://reactjs.org/docs/hello-world.html)

### [JSX](https://reactjs.org/docs/introducing-jsx.html)

### [Rendering-elements](https://reactjs.org/docs/rendering-elements.html)

### [Components and Props](https://reactjs.org/docs/components-and-props.html)

### [State and Lifecycle](https://reactjs.org/docs/state-and-lifecycle.html)

### [Handling Events](https://reactjs.org/docs/handling-events.html)

### [Utility-First Fundamentals](https://tailwindcss.com/docs/utility-first)

### [Create-nextjs-app](https://nextjs.org/learn/basics/create-nextjs-app)

---
