# Class 5

## Create a vocabulary/definition list

### Big O: Analysis of Algorithm Efficiency

* Big O(oh): otation is used to describe the efficiency of an algorithm or function.
* Running Time: The amount of time a function needs to complete.
* Memory Space: The amount of memory resources a function uses to store data and instructions.

#### Overview

* Input Size: Refers to the size of the parameter values that are read by the algorithm.
* n: Refer to the Input Size value.
* Units of Measurement: factors to measure Time and Space complexity.
* Basic Operation: Refers to the operation that is contributing the most to the total running time.
* Working Space:  can be thought of as the creation of variables and reference points as our function performs calculations.

#### Orders of Growth

* Order of Growth: Represents the increase in Running Time or Memory Space.

* Constant Complexity(1):  means that no matter what inputs are thrown at our algorithm, it always uses the same amount of time or space.

* 1 : is used to represent a constant value

* Logarithmic Complexity(lgn): represents a function that sees a decrease in the rate of complexity growth, the greater our value of n. This can be seen when we are performing calculations on sorted data.
* Linear Complexity(n): The size of our inputs ‘n’ will directly determine the amount of Memory Space used and Running Time length.
Linearithmic Complexity(n* lgn) : This represents complexity that grows with n, but also by lgn. Linearithmic functions grow faster than input size n, but not by much.

* Quadratic Complexity (n^2): describes an algorithm with complexity growing at a rate of input size n multiplied by n.

* Cubic Complexity (n^3): Is typically just a higher degree of what makes the quadratic complexity grow at such a high rate.

* Exponential Complexity(2^n):Represents very rapidly growing complexity.

* Factorial Complexity (n!): Means that the our space and time requirements grow extremely fast, relative to our input size.

#### Worst Case, Best Case, Average Case

* Worst Case: The efficiency for the worst possible input of size n.
* Best Case: The efficiency for the best possible input of size n.
* Average Case: The efficiency for a “typical” or “random” input of size n.

##### Asymptotic Notations

* Asymptotic Notations : Other ways we can analyze algorithmic efficiencies.

* Big O(oh): This notation describes the Worst Case for an algorithm.
* Big Omega: This notation describes the Best Case for a given algorithm.
* Big Theta: This notation describes the Average Case.

### Short Summary

![Summary](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-05/resources/images/EfficiencyNotations.png)

### [Source](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-05/resources/big_oh.html)

<br />

## Linked Lists

### Terminology

* Linked Lists:A data structure that contains nodes that links/points to the next node in the list
* Singly: Refers to the number of references the node has. A Singly linked list means that there is only one reference, and the reference points to the Next node in a linked list.

* Doubly : Refers to there being two (double) references within the node. A Doubly linked list means that there is a reference to both the Next and Previous node.

* Nodes: Are the individual items/links that live in a linked list. Each node contains the data for each link.

* Next:Each node contains a property called Next. This property contains the reference to the next node.
* Head: Is a reference of type Node to the first node in a linked list.
* Current is a reference of type Node to the node that is currently being looked at.

### What does it look like

* Add(): Method will define what the value of the Node will be.
* AddBefore:  method that we will demonstrate will insert node before node.

* Addafter:  method that we will demonstrate will insert node after node.
* Includes():  method that We want to check whether or not our LinkedList Includes a specific value.

*
