# Source: https://coursify.hasanraiyan.me/course/design-and-analysis-of-algorithms-daa/graph-traversals-bfs-dfs

# Graph Traversals: BFS & DFS

40 mins

Master the two fundamental algorithms for traversing graphs. Learn their data structure requirements, their step-by-step logic, and how to choose the right algorithm based on real-world engineering constraints.

### Learning Goals

- Compare and contrast Breadth-First Search (BFS) and Depth-First Search (DFS) in terms of traversal order and memory usage.
- Identify the appropriate data structures (Queue vs. Stack) required for each traversal technique.
- Trace the BFS algorithm step-by-step given an adjacency list representation of a graph.
- Calculate the time complexity of traversals based on the graph representation used.

---

### Compare and Contrast: BFS vs. DFS

_(Directly answers the 7-mark subjective questions from 2024 Q5a & 2023 Q7a)_

Both Breadth-First Search (BFS) and Depth-First Search (DFS) are used to visit every vertex and edge in a graph. However, their approaches are fundamentally opposite.

| Feature | Breadth-First Search (BFS) | Depth-First Search (DFS) |
| --- | --- | --- |
| **Traversal Order** | Explores the graph layer by layer (level order). It visits all immediate neighbors of the starting node before moving deeper. | Plunges as deep as possible down a single path until it hits a dead end, then backtracks. |
| **Data Structure** | Uses a **Queue** (First-In, First-Out) to track which nodes to visit next. | Uses a **Stack** (Last-In, First-Out) or system recursion to track the path and backtrack. |
| **Memory Usage** | High memory usage in wide graphs, as it must store an entire "level" of nodes in the queue at once. | Lower memory usage, as it only needs to store the nodes on the current path from the root to the leaf. |
| **Shortest Path?** | Automatically finds the shortest path (minimum number of edges) between two nodes in an unweighted graph. | Does **not** guarantee finding the shortest path; it just finds _a_ path. |
| **Optimal Applications** | GPS navigation (unweighted), Social Network friends mapping, Web Crawlers. | Solving mazes/puzzles, Topological Sorting, Cycle Detection, Bipartite graph checking. |

**Time Complexity for Both:**

- If using an Adjacency List: **O(V+E)O(V + E)O(V+E)** where VVV is vertices and EEE is edges.
- If using an Adjacency Matrix: **O(V2)O(V^2)O(V2)**.

### Trace: Breadth-First Search (BFS) Traversal

1. 1
 
 Step 1
 
 The Target Graph (From Adjacency List)
 
 The exam question provides an Adjacency List. Let's first visualize the directed graph it represents:
 
 _(Note: While the exam gave edge weights, pure BFS ignores weights!)_
 
2. 2
 
 Step 2
 
 Initialization
 
 We need three things:
 
 1. A **Queue** to track nodes to process.
 2. A **Visited Array** (or set) to ensure we don't process a node twice.
 3. The **Output List** to show the traversal order.
 
 Start by enqueuing the start node 'A' and marking it visited. `Queue: [A]`, `Visited: {A}`, `Output: []`
 
3. 3
 
 Step 3
 
 Process Node A
 
 Dequeue 'A'. Add to Output. Look at A's neighbors: B and C. Neither are visited. Mark them visited and enqueue them. `Queue: [B, C]`, `Visited: {A, B, C}`, `Output: [A]`
 
4. 4
 
 Step 4
 
 Process Node B
 
 Dequeue 'B'. Add to Output. Look at B's neighbors: C and D. C is already visited! Ignore it. D is not visited. Mark D visited and enqueue D. `Queue: [C, D]`, `Visited: {A, B, C, D}`, `Output: [A, B]`
 
5. 5
 
 Step 5
 
 Process Node C
 
 Dequeue 'C'. Add to Output. Look at C's neighbors: B, D, E. B and D are already visited! Ignore them. E is not visited. Mark E visited and enqueue E. `Queue: [D, E]`, `Visited: {A, B, C, D, E}`, `Output: [A, B, C]`
 
6. 6
 
 Step 6
 
 Process Nodes D and E
 
 Dequeue 'D'. Add to output. Neighbor E is already visited. `Queue: [E]`, `Output: [A, B, C, D]` Dequeue 'E'. Add to output. Neighbor D is already visited. `Queue: []`, `Output: [A, B, C, D, E]` The Queue is empty. The BFS traversal is complete!
 

### Trace: Depth-First Search (DFS) Traversal

1. 1
 
 Step 1
 
 The State-Space Logic
 
 Let's trace DFS on the exact same graph starting from Node A. Instead of a Queue, DFS uses a **Stack** (LIFO). We push A to the stack. We pop A, mark it visited, and push its unvisited neighbors to the stack.
 
2. 2
 
 Step 2
 
 Step 1: Start at A
 
 Push A. Pop A. Output it. Push neighbors C, then B (pushing B last means it pops first). `Stack: [C, B]`, `Visited: {A}`, `Output: [A]`
 
3. 3
 
 Step 3
 
 Step 2: Plunge deeper to B
 
 Pop B. Output it. Push B's unvisited neighbors: D, then C (but C is already in stack, wait, C is not visited yet). DFS pushes D. `Stack: [C, D]`, `Visited: {A, B}`, `Output: [A, B]`
 
4. 4
 
 Step 4
 
 Step 3: Plunge to D
 
 Pop D. Output it. Push D's unvisited neighbors: E. `Stack: [C, E]`, `Visited: {A, B, D}`, `Output: [A, B, D]`
 
5. 5
 
 Step 5
 
 Step 4: Plunge to E
 
 Pop E. Output it. Push E's unvisited neighbors: D (already visited). `Stack: [C]`, `Visited: {A, B, D, E}`, `Output: [A, B, D, E]`
 
6. 6
 
 Step 6
 
 Step 5: Backtrack to C
 
 We hit a dead end! We now pop the last remaining item on the stack: C. Output it. C's neighbors are B, D, E (all visited). `Stack: []`, `Visited: {A, B, C, D, E}`, `Output: [A, B, D, E, C]`
 
7. 7
 
 Step 7
 
 Compare the Outputs!
 
 Notice the difference in traversal paths for the exact same graph: **BFS Output:** `[A, B, C, D, E]` (Layer by layer) **DFS Output:** `[A, B, D, E, C]` (Deep plunge, then backtrack)
 

### Knowledge Check

Question 1 of 3

Q1Single choice

In DFS traversal of a graph, which data structure is used to keep track of visited nodes?

Queue

Stack

Priority Queue

Heap

BackNext

[BFS and DFS Visualizer\\ \\ web](https://visualgo.net/en/dfsbfs)

[Previous\\ \\ PYQ Analysis & Exam Preparation — Module 2](https://coursify.hasanraiyan.me/course/design-and-analysis-of-algorithms-daa/pyq-analysis-exam-preparation-module-2) [Next\\ \\ Shortest Path Algorithms & Transitive Closure](https://coursify.hasanraiyan.me/course/design-and-analysis-of-algorithms-daa/shortest-path-algorithms-transitive-closure)