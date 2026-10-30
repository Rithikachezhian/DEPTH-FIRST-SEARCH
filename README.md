## BREADTH-FIRST-SEARCH
## ExpNo 3 : Implement Breadth First Search Traversal of a Graph</h1> 
## Name: RITHIKA N
## Register Number: 212223230172

## Aim:
To Implement Breadth First Search Traversal of a Graph using Python 3.

## Theory:
Breadth-First Traversal (or Search) for a graph is like the Breadth-First Traversal of a tree. The only catch here is that, unlike trees, graphs may contain cycles so that we may come to the same node again. To avoid processing a node more than once, we divide the vertices into two categories:

1. Visited
2. Not Visited
A Boolean visited array is used to mark the visited vertices. For simplicity, it is assumed that all vertices are reachable from the starting vertex. BFS uses a queue data structure for traversal.

How does BFS work?
Starting from the root, all the nodes at a particular level are visited first, and then the next level nodes are traversed until all the nodes are visited. To do this, a queue is used. All the adjacent unvisited nodes of the current level are pushed into the queue, and the current-level nodes are marked visited and popped from the queue. Illustration: Let us understand the working of the algorithm with the help of the following example.
* Step1: Initially queue and visited arrays are empty.
![image](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/8acdebf8-ecc2-4d10-a208-45cce441f059)
Queue and visited arrays are empty initially.

* Step2: Push node 0 into queue and mark it visited.
![image](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/0e9ce012-8e1f-43d7-b7b9-c0fb19fe0c3f)
Push node 0 into queue and mark it visited.

* Step 3: Remove node 0 from the front of queue and visit the unvisited neighbours and push them into queue.
![image](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/67d8fa3b-ce9e-46c2-9dd7-089e204e667a)

* Step 4: Remove node 1 from the front of queue and visit the unvisited neighbours and push them into queue.
![image](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/b0cf0fde-8a86-41cb-a054-36875ac24ab0)

* Step 5: Remove node 2 from the front of queue and visit the unvisited neighbours and push them into queue.
![image](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/8968a163-6b3a-4f7e-8ad4-bbf24f326b9b)

* Step 6: Remove node 3 from the front of queue and visit the unvisited neighbours and push them into queue. 
As we can see that every neighbours of node 3 is visited, so move to the next node that are in the front of the queue.
![image](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/7a1c1b16-ea69-497f-a099-8440200f6dc0)

* Steps 7: Remove node 4 from the front of queue and visit the unvisited neighbours and push them into queue. 
As we can see that every neighbours of node 4 are visited, so move to the next node that is in the front of the queue.
![image](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/8e16ffa3-c3d6-4774-822b-6eb84adedad9)

Remove node 4 from the front of queue and visit the unvisited neighbours and push them into queue.
Now, Queue becomes empty, So, terminate these process of iteration.


## Algorithm:
* Construct a Graph with Nodes and Edges
* Breadth First Uses Queue and iterates through the Queue for Traversal.
* Insert a Start Node into the Queue.
* Find its Successors Or neighbors and Check whether the node is visited or not.
* If Not Visited, add it to the Queue. Else Continue.
* Iterate steps 4 and 5 until all nodes get visited, and there are no more unvisited nodes.

## Program:
```
from collections import deque
from collections import defaultdict
def bfs(graph, start, visited, path):
    queue = deque()
    visited[start] = True
    queue.append(start)
    path.append(start)
    while queue:
        node = queue.popleft()
        for neighbour in graph[node]:
            if not visited[neighbour]:
                visited[neighbour] = True
                queue.append(neighbour)
                path.append(neighbour)

    return path


graph = defaultdict(list)

v, e = map(int, input("Enter the number of nodes and edges: ").split())
print("\nEnter the edges (Adjacent Nodes):")
for i in range(e):
    u, w = input(f"Edge {i+1} (u v): ").split()
    graph[u].append(w)
    graph[w].append(u)
print("\nAdjacency List:")
for node in graph:
    print(node, "->", graph[node])
start = input("\nEnter the start node for BFS: ")
if start not in graph:
    print("Invalid start node!")
else:
    visited = defaultdict(bool)
    path = []

 traversedpath = bfs(graph, start, visited, path)
 print("\nBFS Traversal:", " -> ".join(traversedpath))
 ```
## Sample Input:
7 9
A B
A C
A F
C E
C F
C D
D E
D G
G F
## Sample Output:
['A', 'B', 'C', 'F', 'E', 'D', 'G']

## Sample Input:
5 6
0 1
0 2
1 2
1 3
2 4
3 4

## Sample Output:
['0', '1', '2', '3', '4']

## Output:
<img width="500" height="450" alt="AI img3" src="https://github.com/user-attachments/assets/feffd33a-a986-4f4a-a3a6-3dc7ae18a469" />

## Result:
Thus,a Graph was constructed and implementation of Breadth First Search for the same graph was done successfully.







