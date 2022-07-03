# Class 15

## Create a vocabulary/definition list

### Common Terminology

* Node - A Tree node is a component which may contain its own values, and references to other nodes
* Root - The root is the node at the beginning of the tree
* K - A number that specifies the maximum number of children any node may have in a k-ary tree. In a binary tree, k = 2.
* Left - A reference to one child node, in a binary tree
* Right - A reference to the other child node, in a binary tree
* Edge - The edge in a tree is the link between a parent and child node
* Leaf - A leaf is a node that does not have any children
* Height - The height of a tree is the number of edges from the root to the furthest leaf

### Traversals

* An important aspect of trees is how to traverse them. Traversing a tree allows us to search for a node,
print out the contents of a tree, and much more! There are two categories of traversals when it comes to trees:
* Depth First: Depth first traversal is where we prioritize going through the depth (height) of the tree first.
There are multiple ways to carry out depth first traversal, and each method changes the order in which we
search/print the root. Here are three methods for depth first traversal:
Pre-order: root >> left >> right
In-order: left >> root >> right
Post-order: left >> right >> root
* Pre-order: means that the root has to be looked at first. In our case, looking at the root just means that
we output its value. When we call preOrder for the first time

* Breadth First :
* Breadth first traversal iterates through the tree by going through each level of the tree node-by-node.

### Binary Tree Vs K-ary Trees

* Binary Trees restrict the number of children to two (hence our left and right children).

### K-ary Trees

* If Nodes are able have more than 2 child nodes, we call the tree that contains them a K-ary Tree.
In this type of tree we use K to refer to the maximum number of children that each Node is able to have.
* Big O:  time complexity for inserting a new node is O(n). Searching for a specific node will also be O(n).
Because of the lack of organizational structure in a Binary Tree, the worst case for most operations will involve
traversing the entire tree. If we assume that a tree has n nodes, then in the worst case we will have to look at n
items, hence the O(n) complexity.

### Binary Search Trees

* A Binary Search Tree (BST) is a type of tree that does have some structure attached to it. In a BST, nodes are
organized in a manner where all values that are smaller than the root are placed to the left, and all values that are
larger than the root are placed to the right.

## Notes

* The program will look for both a root.left and a root.right. Both will return null, so it will end the execution
of that method call  
* D will pop off of the call stack and the root will be reassigned back to B
This is the heart of recursion: when we complete a function call, we pop it off the stack and are able to continue
execution through the previous function call
* ![Img Resources](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-15/resources/images/DepthTraversal4.PNG)
* There is no specific sorting order for a binary tree. Nodes can be added into a binary tree wherever space allows

## [Source](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-15/resources/Trees.html)
