# Class-27
## Graphs 
- A graph is a non-linear data structure that can be looked at as a collection of `vertices` (or `nodes`) potentially connected by line segments named `edges`.
![](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSMHZtpw4yNs1CEihS2HvVpMXiQLoDphpPWnA&usqp=CAU)
- **Vertex** : A vertex, also called a “node”, is a data object that can have zero or more adjacent vertices.
- **Edge** : An edge is a connection between two nodes.
- **Neighbor** : The neighbors of a node are its adjacent nodes, i.e., are connected via an edge.
- **Degree**: The degree of a vertex is the number of edges connected to that vertex.
##### Directed vs Undirected
![](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSxgm-DoSOsTSWk8P14fFXrErG28XXLhSm54g&usqp=CAU)
- **Directed graph**: A graph where all the edges have a direction indicating what is the start vertex and what is the end vertex,also called a **Digraph**
- **Undirected graph**: A graph with edges that have no direction
#### Complete vs Connected vs Disconnected
![](https://adrianmejia.com/images/connected-vs-complete-graph.jpg)
- **Complete Graphs**: A complete graph is when all nodes are connected to all other nodes.
- **Connected**: A connected graph is graph that has all of `vertices`/`nodes` have at least one edge . **Tree** is a form of a connected graph.
- **Disconnected**: A disconnected graph is a graph where some vertices may not have edges.
#### Acyclic vs Cyclic
![](https://adrianmejia.com/images/cyclic-vs-acyclic-directed-graph.jpg)
- **Acyclic Graph**: An acyclic graph is a directed graph without cycles, when a node can be traversed through and potentially end up back at itself.
- **Cyclic Graphs**: A Cyclic graph is a graph that has cycles. it is defined as a path of a positive length that starts and ends at the same vertex.
#### Graph Representation
![](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSWZePGl-7sBuottwt0kNzKXbchowrZh3z5aA&usqp=CAU)
- **Adjacency Matrix**: An Adjacency matrix is represented through a 2-dimensional array. If there are n vertices, then we are looking at an n x n Boolean matrix.
- **Adjacency List**: An adjacency list is a collection of linked lists or array that lists all of the other vertices that are connected. it makes it easy to view if one vertices connects to another
#### Weighted Graphs 
![](https://www.softwaretestinghelp.com/wp-content/qa/uploads/2019/08/6.weighted-graph-and-its-adjacency-matrix.png)
- A weighted graph is a graph with numbers assigned to its edges. These numbers are called `weights`.


