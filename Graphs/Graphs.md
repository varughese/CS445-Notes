# Graphs

Graphs often have rules

## Trees:
Nodes: 0 - 2 children
"Value" important
no cycles / No weights

## Heap
Nodes: 0 - 2 children
"Value" important in a different way
No weights

## Linked List
Start
0 - 1 children
no cycles
no weights

# Graphs
- Rules
- Edge
- Vertex
- Weight
	- Cost of traveling a path (it depends what it should be)
- Direction
- Sparse
	- has one or two edges per vertex
- Dense
	- has relatively many edges


Matrix is one way to store a graph.

| 0 | 1 | 2 | 3 | 4 | 5 | 6 |
|---|---|---|---|---|---|---|
| F | F | F | T | F | F | F |
| F | F | T | T | F | F | F |
| F | F | F | F | F | F | F |
|   |   |   |   |   |   |   |
|   |   |   |   |   |   |   |
|   |   |   |   |   |   |   |
|   |   |   |   |   |   |   |

N^2 memory and n = # of vertices
Not a good way to store sparse graphs

Maybe a int[32] for an unweighted graph

Object solution:

Vertex object and has children

Or a memory efficient solution could be

[A] -> [C]
[B] -> [C]
[C] -> [A]
[D] -> [B] -> [C]


----

If we use a Map to store it:

[A] --> [could be a linked list / set / array list]
[B] --> []

A set would be fast but take a lot of memory.
If you use a HashMap that contains HashSet in memory it kind of looks like an array