# Source: https://coursify.hasanraiyan.me/course/design-and-analysis-of-algorithms-daa/backtracking-branch-and-bound

# Backtracking & Branch and Bound

45 mins

Master the algorithmic strategies used to solve complex combinatorial problems. Learn how to traverse state-space trees using DFS for Backtracking (N-Queens, Graph Coloring) and BFS for Branch & Bound (TSP).

### Learning Goals

- Differentiate between Backtracking and Branch & Bound in terms of traversal strategy and use-case.
- Trace the state-space tree for the N-Queens problem and explain the backtracking conditions.
- Apply the backtracking technique to solve the m-Coloring problem on a graph.
- Understand how bounding functions prune the search tree in the Traveling Salesperson Problem (TSP).

---

### Backtracking vs. Branch & Bound

Both Backtracking and Branch & Bound are algorithmic paradigms used to solve combinatorial problems by generating a **State-Space Tree**. However, they have three critical differences that examiners test heavily:

| Feature | Backtracking | Branch & Bound |
| --- | --- | --- |
| **Traversal Strategy** | Uses **Depth-First Search (DFS)**. It goes as deep as possible into one branch. | Uses **Breadth-First Search (BFS)** or **Priority-Queue (Best-First Search)**. |
| **Problem Type** | Used for **Decision** or **Enumeration** problems (e.g., "Find _all_ solutions to N-Queens"). | Used strictly for **Optimization** problems (e.g., "Find the _shortest_ path in TSP"). |
| **Pruning Mechanism** | Prunes a branch the moment the current state violates the problem constraints (a "dead end"). | Prunes a branch if its calculated "lower bound" is already worse than the best optimal solution found so far. |

### Trace: The N-Queens Problem (Backtracking)

1. 1
 
 Step 1
 
 The Objective & Constraints
 
 The goal is to place NNN queens on an N×NN \\times NN×N chessboard such that no two queens attack each other. **Constraints:** No two queens can share the same row, same column, or same diagonal.
 
2. 2
 
 Step 2
 
 The State-Space Tree Logic
 
 We place queens column by column (or row by row). We place Queen 1 in Row 1, Col 1. Then we move to Row 2 and try to place Queen 2. If a placement is attacked, we prune that branch and **backtrack** to try the next column.
 
3. 3
 
 Step 3
 
 Mermaid Visualization of the Pruning
 
4. 4
 
 Step 4
 
 The Pseudocode Solution
 
 `1Algorithm NQueens(k, n): 2// k is current queen, n is total queens 3   For i = 1 to n do: 4      If Place(k, i) is True: 5         x[k] = i // Place queen k at column i 6         If k == n: 7            Print Solution(x) 8         Else: 9            NQueens(k+1, n) // Recurse for next queen`
 

### Trace: Graph Coloring (Backtracking)

1. 1
 
 Step 1
 
 The Objective
 
 Given a graph G\=(V,E)G = (V, E)G\=(V,E) and mmm colors, assign a color to every vertex such that no two adjacent vertices (connected by an edge) share the same color. If no such coloring exists, return false.
 
2. 2
 
 Step 2
 
 The State-Space Tree Logic
 
 We assign colors to vertices one by one (e.g., Vertex A, then B, then C). For each vertex, we try Color 1. If it doesn't conflict with its neighbors, we move to the next vertex. If we run out of valid colors for a vertex, we **backtrack** to the previous vertex and change its color.
 
3. 3
 
 Step 3
 
 Mermaid Visualization of Graph Coloring
 
4. 4
 
 Step 4
 
 Complexity
 
 Because we have mmm choices of colors for nnn vertices, the state space tree has mnm^nmn leaves. The worst-case time complexity is **O(mn)O(m^n)O(mn)**.
 

### Trace: Hamiltonian Cycle (Backtracking)

1. 1
 
 Step 1
 
 The Objective
 
 A Hamiltonian Cycle is a closed loop in a graph that visits every single vertex exactly once and returns to the starting vertex. Given an adjacency matrix, we must find this cycle using backtracking.
 
2. 2
 
 Step 2
 
 The State-Space Tree Logic
 
 Starting from an arbitrary node (e.g., Vertex A), we explore adjacent vertices. If we pick Vertex B, we add it to our path array. From B, we pick an unvisited neighbor. If we hit a dead end (a vertex with no unvisited neighbors) before visiting all vertices, we **backtrack** and try a different neighbor.
 
3. 3
 
 Step 3
 
 Trace the Matrix Constraints
 
 Let's say the current path is A →\\to→ B →\\to→ C. To check if D is a valid next step, we must verify two conditions:
 
 1. `Matrix[C][D] == 1` (An edge exists between the current vertex and D).
 2. D is not already in the path array.
 
4. 4
 
 Step 4
 
 Checking the Cycle Condition
 
 When the path array contains all VVV vertices, we do one final check: `Matrix[Last_Vertex][Start_Vertex] == 1`. If an edge connects the last visited node back to the start, a Hamiltonian Cycle is found! If not, we backtrack.
 
5. 5
 
 Step 5
 
 Complexity
 
 The backtracking approach explores a massive permutation tree. The worst-case time complexity is **O(V!)O(V!)O(V!)** where VVV is the number of vertices, though pruning impossible edges makes it practically faster than brute force.
 

### Trace: TSP using Branch & Bound

1. 1
 
 Step 1
 
 The Objective
 
 The Traveling Salesperson Problem requires a salesperson to visit every city exactly once and return to the starting city, minimizing the total distance. Since we want the absolute minimum distance, we use Branch & Bound.
 
2. 2
 
 Step 2
 
 Calculating the Root Lower Bound
 
 To prune branches, we must calculate a 'Lower Bound' for the starting node. We do this by reducing the distance matrix:
 
 1. **Row Reduction:** Find the minimum value in each row and subtract it from all elements in that row. Add these minimums to the bound.
 2. **Column Reduction:** Find the minimum value in each column of the _new_ matrix and subtract it. Add these to the bound. The sum of all subtracted values is the initial Lower Bound cost.
 
3. 3
 
 Step 3
 
 Branching to the next city
 
 From City A, we can travel to B, C, or D. For each path (e.g., A →\\to→ B), we calculate a new cost: `Cost(Node) = Parent_Cost + Matrix[A][B] + Reduction_Cost_of_New_Matrix`. To create the new matrix for path A →\\to→ B, we set row A to ∞\\infty∞, column B to ∞\\infty∞, and `Matrix[B][A]` to ∞\\infty∞ (preventing immediate return). Then we reduce the matrix again.
 
4. 4
 
 Step 4
 
 Pruning the Search Tree
 
 We maintain an 'Upper Bound' (the best complete tour found so far). If we calculate a partial path's lower bound (e.g., Path A →\\to→ C →\\to→ D) and its cost is _higher_ than our Upper Bound, we **prune** it. We mathematically guarantee that this path can never yield a better solution, saving massive amounts of computation time.
 

### Knowledge Check

Question 1 of 3

Q1Single choice

Which data structure is fundamentally used by the Backtracking algorithm to explore the state-space tree?

Queue

Priority Queue

Stack

Hash Table

BackNext

[N-Queens Visualizer\\ \\ web](https://www.cs.usfca.edu/~galles/visualization/RecQueens.html)

[Previous\\ \\ Dynamic Programming](https://coursify.hasanraiyan.me/course/design-and-analysis-of-algorithms-daa/dynamic-programming) [Next\\ \\ Problem Applications: Bin Packing, Knapsack & TSP](https://coursify.hasanraiyan.me/course/design-and-analysis-of-algorithms-daa/problem-applications-bin-packing-knapsack-tsp)