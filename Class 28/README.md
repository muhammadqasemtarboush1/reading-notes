# Class 28

Live link: [Graphs](https://muhammadqasemtarboush1.github.io/reading-notes/Class%2028/)

## Graphs

- Graph:
  - is a non-linear data structure that can be looked at as a collection of vertices (or nodes) potentially connected by line segments named edges.
- Vertex - A vertex, also called a “node”, is a data object that can have zero or more adjacent vertices.
- Edge - An edge is a connection between two nodes.
- Neighbor - The neighbors of a node are its adjacent nodes, i.e., are connected via an edge.
- Degree - The degree of a vertex is the number of edges connected to that vertex.

### Directed vs Undirected

- Undirected Graph:
  - is a graph where each edge is undirected or bi-directional. This means that the undirected graph does not move in any direction.
- Directed Graphs (Digraph)
  - A Directed Graph also called a Digraph is a graph where every edge is directed.

### Complete vs Connected vs Disconnected

- Complete Graphs:
  - A complete graph is when all nodes are connected to all other nodes.
- Connected
  - A connected graph is graph that has all of vertices/nodes have at least one edge.
- Disconnected
  - A disconnected graph is a graph where some vertices may not have edges.

### Acyclic vs Cyclic

- Acyclic
  - An acyclic graph is a directed graph without cycles.
  - A cycle is when a node can be traversed through and potentially end up back at itself.
- Cyclic
  - A Cyclic graph is a graph that has cycles.
  - A cycle is defined as a path of a positive length that starts and ends at the same vertex.

### Graph Representation

1. Adjacency Matrix
   - An Adjacency matrix is represented through a 2-dimensional array. If there are n vertices, then we are looking at an n x n Boolean matrix Each Row and column represents each vertex of the data structure.
   - The elements of both the column and the row must add up to 1 if there is an edge that connects the two, or zero if there isn’t a connection.
2. Adjacency List
   - An adjacency list is the most common way to represent graphs.
   - An adjacency list is a collection of linked lists or array that lists all of the other vertices that are connected.
   - Adjacency lists make it easy to view if one vertices connects to another.

### Weighted Graphs

A weighted graph is a graph with numbers assigned to its edges.

### Traversals

You will be required to traverse through a graph. The traversals itself are like those of trees. Below is a breakdown of how you would traverse a graph.

- BreadthFirst():
  - In a breadth first traversal, you are starting at a specific vertex/node. This node must be specified when calling the BreadthFirst() method.
- DepthFirst():
  - or breadth first. While the breadth first traversal uses a Queue to visit all children at a given level, the depth first traversal uses a Stack to visit all children of a given subtree.

## Notes

Real World Uses of Graphs

- GPS and Mapping
- Driving Directions
- Social Networks
- Airline Traffic
- Netflix uses graphs for suggestions of products

---

## Resources

### [Graphs](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-35/resources/graphs.html)

---
