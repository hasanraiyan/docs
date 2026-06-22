# Source: https://coursify.hasanraiyan.me/course/design-and-analysis-of-algorithms-daa/minimum-spanning-tree-algorithms

# Minimum Spanning Tree Algorithms

40 mins

Understand how to find the Minimum Spanning Tree of a graph using Greedy strategies. Compare Prim's vertex-based growth approach with Kruskal's edge-based sorting approach.

### Learning Goals

- Define the properties of a Minimum Spanning Tree (MST).
- Compare Prim's and Kruskal's algorithms in terms of logic and data structures.
- Trace Prim's algorithm using a Priority Queue.
- Trace Kruskal's algorithm using edge sorting and Disjoint Sets (Union-Find) to detect cycles.

---

### Minimum Spanning Trees (MST): Prim vs. Kruskal

_(Directly answers the theoretical comparisons from the 2024 Q7a exam)_

A **Spanning Tree** is a subgraph that includes _all_ vertices of the original graph but has exactly V−1V-1V−1 edges and no cycles. A **Minimum Spanning Tree (MST)** is the spanning tree where the total sum of edge weights is minimized.

Both Prim's and Kruskal's algorithms use the **Greedy Method** to find the MST, but they build it in entirely different ways:

| Feature | Prim's Algorithm | Kruskal's Algorithm |
| --- | --- | --- |
| **Growth Strategy** | Vertex-based. Starts from a single arbitrary vertex and grows a single continuous tree outward. | Edge-based. Sorts all edges globally and picks the smallest ones, often creating disconnected "forests" that eventually merge. |
| **Data Structures** | Uses a **Priority Queue (Min-Heap)** to find the smallest edge connected to the growing tree. | Uses **Sorting** for edges and a **Disjoint Set (Union-Find)** to detect if adding an edge creates a cycle. |
| **Best Used For** | **Dense graphs** (where the number of edges EEE is close to V2V^2V2). | **Sparse graphs** (where the number of edges EEE is close to VVV). |
| **Time Complexity** | O(Elog⁡V)O(E \\log V)O(ElogV) using a binary heap. | O(Elog⁡E)O(E \\log E)O(ElogE) due to the initial edge sorting. |

### Trace: Prim's Algorithm

1. 1
 
 Step 1
 
 The Target Graph
 
 Consider this undirected, weighted graph:
 
2. 2
 
 Step 2
 
 Initialization
 
 Select an arbitrary starting node. Let's pick **A**.
 
 - MST Vertices: `{A}`
 - Edges in PQ (connected to A): `(A-B: 1), (A-C: 4)`
 - Total Cost: 0
 
3. 3
 
 Step 3
 
 Step 1: Grow to B
 
 Extract the minimum edge from the PQ. That is `A-B: 1`. Since B is not in the MST, we add it.
 
 - MST Vertices: `{A, B}`
 - We add B's outward edges to the PQ: `(A-C: 4), (B-C: 2), (B-D: 5)`
 - Total Cost: 1
 
4. 4
 
 Step 4
 
 Step 2: Grow to C
 
 Extract the minimum edge from the PQ. That is `B-C: 2`. Since C is not in the MST, we add it.
 
 - MST Vertices: `{A, B, C}`
 - We add C's outward edges to the PQ: `(A-C: 4), (B-D: 5), (C-D: 3)`
 - Total Cost: 1 + 2 = 3
 
5. 5
 
 Step 5
 
 Step 3: Grow to D
 
 Extract the minimum edge. That is `C-D: 3`. Since D is not in the MST, we add it.
 
 - MST Vertices: `{A, B, C, D}`. All vertices are now included!
 - Total Cost: 3 + 3 = **6**. _(Note: If we had extracted `A-C: 4` later, we would reject it because both A and C are already in the MST, meaning it would form a cycle)._ **Final MST Edges:** `A-B`, `B-C`, `C-D`.
 

### Trace: Kruskal's Algorithm

1. 1
 
 Step 1
 
 Initialization (Sort Edges)
 
 Using the exact same graph, Kruskal's begins by completely ignoring the vertices and sorting every single edge in ascending order of weight:
 
 1. `A-B (1)`
 2. `B-C (2)`
 3. `C-D (3)`
 4. `A-C (4)`
 5. `B-D (5)`
 
2. 2
 
 Step 2
 
 Step 1 & 2: Safe Edges
 
 We iterate through the sorted list and use a **Union-Find** data structure to check for cycles.
 
 - Pick `A-B (1)`. A and B are in different sets. Safe! Add to MST. (Cost: 1)
 - Pick `B-C (2)`. C is in a different set. Safe! Add to MST. (Cost: 1 + 2 = 3).
 
3. 3
 
 Step 3
 
 Step 3: Cycle Detection
 
 - Pick `C-D (3)`. D is in a different set. Safe! Add to MST. (Cost: 3 + 3 = 6).
 - Pick `A-C (4)`. **Wait!** Our Union-Find structure knows that A and C are already in the exact same connected component (via A-B-C). Adding this edge would create a cycle (A-B-C-A). **Reject it.**
 
4. 4
 
 Step 4
 
 Step 4: Completion
 
 - Pick `B-D (5)`. B and D are already in the same component. **Reject it.** We have exactly V−1\=3V-1 = 3V−1\=3 edges in our MST. **Final Cost:** **6**. Both algorithms successfully built the exact same Minimum Spanning Tree!
 

### Knowledge Check

Question 1 of 2

Q1Single choice

Which algorithm is used to find a Minimum Spanning Tree?

Dijkstra’s algorithm

Prim’s algorithm

Bellman-Ford algorithm

Floyd-Warshall algorithm

BackNext

[Previous\\ \\ Shortest Path Algorithms & Transitive Closure](https://coursify.hasanraiyan.me/course/design-and-analysis-of-algorithms-daa/shortest-path-algorithms-transitive-closure) [Next\\ \\ Topological Sorting & Network Flow](https://coursify.hasanraiyan.me/course/design-and-analysis-of-algorithms-daa/topological-sorting-network-flow)