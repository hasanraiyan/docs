# Source: https://coursify.hasanraiyan.me/course/design-and-analysis-of-algorithms-daa/pyq-analysis-exam-preparation-module-3

# PYQ Analysis & Exam Preparation — Module 3

60 mins

A strategic analysis of 22 exam questions spanning 2022–2024. Module 3 focuses strictly on Graph and Tree Algorithms. Mastery of Dijkstra's, Bellman-Ford, Prim's, Kruskal's, and BFS/DFS will secure up to 30 marks on any paper.

### Learning Goals

- Identify the guaranteed question types: Shortest Path traces (Dijkstra/Bellman-Ford), MST traces, and BFS vs DFS theory.
- Practice with actual MCQ questions testing algorithm complexities and application domains.
- Understand the exact table structures required by examiners for tracing shortest path algorithms.

---

### The Exam Blueprint: Module 3 PYQ Deep Analysis (2022–2024)

An analysis of **22 exam questions spanning 2022 to 2024** reveals that Module 3 is highly standardized. The questions revolve around three core pillars: **Graph Traversals (BFS/DFS)**, **Shortest Paths**, and **Minimum Spanning Trees (MST)**. A new addition in 2024 is the **Ford-Fulkerson algorithm** for Network Flow.

#### Complete PYQ Table (22 Questions)

| Year | Q# | Marks | Topic | Type |
| --- | --- | --- | --- | --- |
| 2022 | Q1a | **2** | Adjacency matrix missing parallel edges | MCQ |
| 2022 | Q1c | **2** | Graph coloring for 2 edges | MCQ |
| 2022 | Q1d | **2** | BFS running time = O(V+E) | MCQ |
| 2022 | Q1g | **2** | All Pair Shortest Path = Floyd Warshall | MCQ |
| 2023 | Q1c | **2** | Algorithm for MST = Kruskal's | MCQ |
| 2023 | Q1i | **2** | Topological sort complexity = O(V+E) | MCQ |
| 2024 | Q1e | **2** | DFS traversal data structure = Stack | MCQ |
| 2024 | Q1f | **2** | MST algorithm = Prim's | MCQ |
| 2024 | Q1g | **2** | Topological sorting requires DAG | MCQ |
| 2024 | Q1h | **2** | Max flow algorithm = Ford-Fulkerson | MCQ |
| 2022 | Q3a | **7** | MST step-by-step trace | Numerical |
| 2022 | Q4a | **7** | Dijkstra's shortest path trace | Numerical |
| 2022 | Q7a | **7** | Bellman-Ford algorithm + Negative cycles | Theory |
| 2023 | Q6a | **7** | Bellman-Ford trace on matrix + Time complexity | Numerical |
| 2023 | Q6b | **7** | Explain MST + Prim's algorithm steps | Theory |
| 2023 | Q7a | **7** | Differentiate BFS vs DFS | Theory |
| 2024 | Q5a | **7** | Compare BFS vs DFS + Applications | Theory |
| 2024 | Q5b | **7** | System Design: Algorithm choice based on road lengths | Theory |
| 2024 | Q6a | **7** | Draw graph + BFS pseudo-code + BFS trace | Theory+Num |
| 2024 | Q6b | **7** | Dijkstra pseudo-code + trace | Theory+Num |
| 2024 | Q7a | **7** | Compare Prim's vs Kruskal's + Complexities | Theory |
| 2024 | Q7b | **7** | Ford-Fulkerson max flow trace | Numerical |

**Total marks tracked: 112 marks across 3 years.**

---

#### Topic Heat Map

| Topic | 2022 | 2023 | 2024 | Total Marks |
| --- | --- | --- | --- | --- |
| **Shortest Paths (Dijkstra, Bellman, Floyd)** | 16M ✅ | 7M ✅ | 14M ✅ | **37M** |
| **BFS & DFS Traversals** | 2M ✅ | 9M ✅ | 16M ✅ | **27M** |
| **Minimum Spanning Tree (Prim/Kruskal)** | 7M ✅ | 9M ✅ | 9M ✅ | **25M** |
| **Network Flow / Ford-Fulkerson** | — | — | 9M ✅ | **9M** |
| **Topological Sort** | — | 2M ✅ | 2M ✅ | **4M** |

---

#### The Guaranteed Question Types

> **1\. 🔴 Shortest Path Trace (7–14M)** Appeared in ALL 3 years. You must know both **Dijkstra’s** (for graphs with positive weights) and **Bellman-Ford** (for negative weights/cycles). Examiners expect to see a step-by-step distance table.

> **2\. 🔴 BFS vs DFS Comparison (7M)** Highly predictable theory question. You must compare them across 4 dimensions: data structures used, memory complexity, traversal order, and specific applications.

> **3\. 🟠 Prim's vs Kruskal's MST (7M)** Either tracing the MST on a graph (2022) or writing the differences/pseudo-code (2023, 2024).

> **4\. 🟡 Real-World Algorithm Selection (7M)** A new trend started in 2024 (e.g., Q5b) where you are given a scenario (like Google Maps) and must justify which graph algorithm to use based on edge weights.

### Solved Numericals: How to Structure Your Traces

---

#### Strategy 1: The Dijkstra Distance Table

When asked to trace Dijkstra's algorithm (e.g., 2022 Q4a, 2024 Q6b), do **not** just write the final shortest paths. Draw a table showing the relaxation of edges at each step.

**Standard Table Format:**

| Step | Visited Set (S) | Unvisited Queue (Q) | D(A)D(A)D(A) | D(B)D(B)D(B) | D(C)D(C)D(C) | D(D)D(D)D(D) |
| --- | --- | --- | --- | --- | --- | --- |
| 0 | `{}` | `{A, B, C, D}` | **0** | ∞\\infty∞ | ∞\\infty∞ | ∞\\infty∞ |
| 1 | `{A}` | `{B, C, D}` | 0 | 10 (A) | 3 (A) | ∞\\infty∞ |
| 2 | `{A, C}` | `{B, D}` | 0 | 7 (C) | 3 | 11 (C) |

_Key to scoring full marks: Always write the "parent node" in brackets next to the distance cost, e.g., `10 (A)`. This shows the exact path taken._

---

#### Strategy 2: Bellman-Ford Relaxation

Bellman-Ford requires relaxing ALL edges ∣V∣−1|V| - 1∣V∣−1 times. If the graph has 5 vertices, you must show **4 Passes**.

**Pseudo-code for the trace:**

`1For i = 1 to 4: 2    For every edge (u, v) with weight w: 3        If D[u] + w < D[v]: 4            D[v] = D[u] + w`

You must state: _"After Pass 4, we run one more pass to check for negative weight cycles. If any distance updates, a negative cycle exists."_

---

#### Numerical: Ford-Fulkerson Trace

> _"Find max flow from S to T. Capacities: S→A=10, S→C=10, A→B=4, A→C=2, C→D=9, B→T=10, D→B=6, D→T=10."_

**Step-by-step trace format required by examiners:**

**Path 1:** S → A → B → T

- Bottleneck (min capacity): min⁡(10,4,10)\=4\\min(10, 4, 10) = 4min(10,4,10)\=4
- Update residual graph: Decrease forward edges by 4, increase backward edges by 4.
- Flow so far = **4**

**Path 2:** S → C → D → T

- Bottleneck: min⁡(10,9,10)\=9\\min(10, 9, 10) = 9min(10,9,10)\=9
- Update residual graph.
- Flow so far = 4 + 9 = **13**

**Path 3:** S → A → C → D → B → T

- Bottleneck: min⁡(10−4\=6,2,9−9\=0 WAIT! C→D is full)\\min(10-4=6, 2, 9-9=0 \\text{ WAIT! C→D is full})min(10−4\=6,2,9−9\=0 WAIT! C→D is full).
- We must find a valid path in the residual graph. C→D is 0 capacity left.
- Valid residual path: S → A → C ... (cannot go to D).
- Can we go D → C (backward edge)? No path to T from C without D.
- Wait, B has remaining capacity to T (10 - 4 = 6). D has remaining to B (6). D has remaining to T (10 - 9 = 1).
- Let's trace S → C → D → B → T: Bottleneck min⁡(10−9\=1,9−9\=0)\\min(10-9=1, 9-9=0)min(10−9\=1,9−9\=0). S→C has 1 remaining. C→D has 0 remaining.
- Let's look at S → A → C ... C is blocked.

**Conclusion format:** _"No more augmenting paths exist from S to T in the residual graph. Max Flow = sum of flows = 13."_

_(Note: Always draw the residual graph after each path update to guarantee full marks)._

### Knowledge Check

Question 1 of 5

Q1Single choice

Which of the following algorithm solves the All Pair Shortest Path problem?

Dijkstra’s

Floyd-Warshall

Prim’s

Kruskal’s

BackNext

### High-Yield Subjective Bank: Structure Your Answers

---

####Compare and contrast BFS and DFS (7 Marks)\*\*

**Answer structure (Table Format):**

| Feature | BFS (Breadth-First Search) | DFS (Depth-First Search) |
| --- | --- | --- |
| **Data Structure** | Queue (FIFO). | Stack (LIFO / Recursion). |
| **Traversal Strategy** | Level by level (visits all neighbors first). | Goes deep down a branch until a dead end, then backtracks. |
| **Memory Usage** | High. Must store all nodes at the current level. O(V)O(V)O(V). | Low. Only stores nodes on the current path. O(h)O(h)O(h) where h is depth. |
| **Optimal for...** | Finding the shortest path in unweighted graphs. | Solving maze puzzles, topological sorting, cycle detection. |
| **Time Complexity** | O(V+E)O(V + E)O(V+E) using adjacency list. | O(V+E)O(V + E)O(V+E) using adjacency list. |

---

####Compare Prim’s and Kruskal’s algorithms (7 Marks)\*\*

**Answer structure:**

1. **Approach**:
 - **Prim's**: Vertex-based. Starts at a root node and greedily grows the tree by selecting the cheapest edge connected to the _current tree_.
 - **Kruskal's**: Edge-based. Sorts all edges globally by weight and adds them to the forest one by one, skipping edges that form a cycle.
2. **Data Structures**:
 - **Prim's**: Uses a Priority Queue (Min-Heap) to find the minimum connected edge.
 - **Kruskal's**: Uses the Disjoint-Set (Union-Find) data structure to detect cycles.
3. **Graph Suitability**:
 - **Prim's** performs better on **dense graphs** (lots of edges). Time complexity: O(Elog⁡V)O(E \\log V)O(ElogV).
 - **Kruskal's** performs better on **sparse graphs**. Time complexity: O(Elog⁡E)O(E \\log E)O(ElogE).

---

####System Design: Shortest Paths on Google Maps (7 Marks)\*\*

_Given a city graph mapping, which algorithm to use?_

1. **(i) All roads have equal length**:
 - **Algorithm**: BFS (Breadth-First Search).
 - **Reasoning**: When weights are equal (or 1), BFS inherently finds the shortest path without the overhead of maintaining a priority queue. It is the most efficient choice O(V+E)O(V+E)O(V+E).
2. **(ii) Roads have varying lengths, but no negative lengths**:
 - **Algorithm**: Dijkstra's Algorithm.
 - **Reasoning**: Dijkstra is the standard for non-negative weighted graphs. It uses a greedy approach (priority queue) to efficiently find the shortest path in O(Elog⁡V)O(E \\log V)O(ElogV) time.
3. **(iii) Some roads have negative lengths**:
 - **Algorithm**: Bellman-Ford Algorithm.
 - **Reasoning**: Dijkstra fails on negative weights because a previously finalized node's distance might decrease later. Bellman-Ford correctly handles negative weights by relaxing all edges V−1V-1V−1 times.

[Dijkstra's Algorithm - Visualized\\ \\ web](https://www.cs.usfca.edu/~galles/visualization/Dijkstra.html)

[Previous\\ \\ Topological Sorting & Network Flow](https://coursify.hasanraiyan.me/course/design-and-analysis-of-algorithms-daa/topological-sorting-network-flow) [Next\\ \\ Computability & Complexity Classes: P and NP](https://coursify.hasanraiyan.me/course/design-and-analysis-of-algorithms-daa/computability-complexity-classes-p-and-np)