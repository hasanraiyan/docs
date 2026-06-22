# Source: https://coursify.hasanraiyan.me/course/design-and-analysis-of-algorithms-daa/shortest-path-algorithms-transitive-closure

# Shortest Path Algorithms & Transitive Closure

50 mins

Navigate the core algorithms for finding shortest paths in a graph. Learn when to use Dijkstra's Algorithm vs Bellman-Ford based on edge weights, and how to compute All-Pairs Shortest Paths using Floyd-Warshall.

### Learning Goals

- Answer system design questions by choosing the correct shortest-path algorithm based on edge weight constraints.
- Perform a step-by-step trace of Dijkstra's algorithm using the edge relaxation method.
- Trace Bellman-Ford's algorithm and explain how it detects negative weight cycles.
- Understand the DP recurrence relation for the Floyd-Warshall algorithm.

---

### System Design: Shortest Paths on Google Maps

When designing a routing system like Google Maps, the choice of the shortest path algorithm depends entirely on the nature of the graph's edge weights (road lengths/traffic delays).

1. **All roads have equal length (Unweighted Graph):**
 
 - **Algorithm:** Breadth-First Search (BFS).
 - **Reasoning:** BFS explores layer-by-layer. The first time it reaches the destination, it guarantees the minimum number of edges. It is much faster (O(V+E)O(V+E)O(V+E)) than applying a weighted algorithm.
2. **Roads have varying lengths, but NO negative lengths:**
 
 - **Algorithm:** Dijkstra's Algorithm.
 - **Reasoning:** Dijkstra uses a priority queue (Min-Heap) to greedily lock in the shortest path to a node. Since there are no negative weights, once a node's distance is locked, it can never be improved. Time complexity is O(Elog⁡V)O(E \\log V)O(ElogV).
3. **Some roads have negative lengths (Negative weight cycles):**
 
 - **Algorithm:** Bellman-Ford Algorithm.
 - **Reasoning:** Dijkstra fails if negative weights exist because it might lock a node's distance prematurely. Bellman-Ford systematically relaxes all edges V−1V-1V−1 times, guaranteeing it finds the shortest path even with negative edges. It also runs a final VVV\-th pass to explicitly detect "negative weight cycles" (where looping infinitely reduces the cost). Time complexity is O(V×E)O(V \\times E)O(V×E).

### Dijkstra's Algorithm Pseudocode

_(Answers 2024 Q6b)_

`1Algorithm Dijkstra(G, source): 2   For each vertex v in G: 3      Dist[v] = INFINITY 4      Prev[v] = UNDEFINED 5   Dist[source] = 0 6    7   Let PQ be a Priority Queue (Min-Heap) 8   PQ.insert(source, 0) 9    10   While PQ is not empty: 11      u = PQ.extract_min() 12       13      For each neighbor v of u: 14         alt_dist = Dist[u] + weight(u, v) 15         If alt_dist < Dist[v]: 16            Dist[v] = alt_dist 17            Prev[v] = u 18            PQ.insert(v, alt_dist)`

### Trace: Dijkstra's Algorithm (Single Source Shortest Path)

1. 1
 
 Step 1
 
 The Target Graph
 
2. 2
 
 Step 2
 
 Initialization
 
 We want to find the shortest path from **Source A** to all other nodes.
 
 - Initialize distances: `Dist[A] = 0`, all others to ∞\\infty∞.
 - Priority Queue (Min-Heap): `[(0, A)]`
 - Visited Set: `{}`
 
3. 3
 
 Step 3
 
 Relaxation of A
 
 Extract A from PQ. Mark A as visited. Look at neighbors of A: B (weight 4) and C (weight 2).
 
 - `Dist[A] + 4 < Dist[B]`   ⟹  0+4<∞\\implies 0 + 4 < \\infty⟹0+4<∞. Update `Dist[B] = 4`.
 - `Dist[A] + 2 < Dist[C]`   ⟹  0+2<∞\\implies 0 + 2 < \\infty⟹0+2<∞. Update `Dist[C] = 2`. Push to PQ: `[(2, C), (4, B)]`
 
4. 4
 
 Step 4
 
 Relaxation of C
 
 Extract C (minimum distance = 2) from PQ. Mark C visited. Neighbors of C: B(1), D(8), E(10).
 
 - Path to B via C: `Dist[C] + 1 = 2 + 1 = 3`. Since 3<43 < 43<4, update `Dist[B] = 3`.
 - Path to D via C: `Dist[C] + 8 = 2 + 8 = 10`. Update `Dist[D] = 10`.
 - Path to E via C: `Dist[C] + 10 = 2 + 10 = 12`. Update `Dist[E] = 12`. Push updates to PQ. PQ extracts B next (distance = 3).
 
5. 5
 
 Step 5
 
 Relaxation of B
 
 Extract B (distance = 3) from PQ. Mark B visited. Neighbors of B: D(5).
 
 - Path to D via B: `Dist[B] + 5 = 3 + 5 = 8`. Since 8<108 < 108<10, update `Dist[D] = 8`. PQ extracts D next (distance = 8).
 
6. 6
 
 Step 6
 
 Final Relaxations
 
 Extract D (distance = 8). Neighbors: E(2).
 
 - Path to E via D: `Dist[D] + 2 = 8 + 2 = 10`. Since 10<1210 < 1210<12, update `Dist[E] = 10`. Extract E. No outgoing neighbors. **Final Distances from A:** B=3, C=2, D=8, E=10.
 

### Trace: Bellman-Ford on a Matrix

1. 1
 
 Step 1
 
 The Matrix (2023 Q6a Exam)
 
 Find shortest distance from **Source Node 3**.
 
 `1   1   2   3   4   5 21  0   1   8   1   4 32  1   0   12  4   9 43  8   12  0   7   3 54  1   4   7   0   2 65  4   9   3   2   0`
 
 Because the matrix is symmetric, it is an undirected graph. We extract all edges and their weights.
 
2. 2
 
 Step 2
 
 Initialization
 
 Set Dist\[3\] = 0. All other nodes to ∞\\infty∞. `Dist = [\infty, \infty, 0, \infty, \infty]` We have V\=5V=5V\=5, so we will run V−1\=4V-1 = 4V−1\=4 relaxation passes over all edges.
 
3. 3
 
 Step 3
 
 Pass 1
 
 We relax all edges. Edges leaving Node 3 will update first because `Dist[3]` is 0.
 
 - `Dist[3] + weight(3,1) < Dist[1]`   ⟹  0+8<∞\\implies 0 + 8 < \\infty⟹0+8<∞. Update `Dist[1] = 8`.
 - Update `Dist[2] = 12`.
 - Update `Dist[4] = 7`.
 - Update `Dist[5] = 3`. After Pass 1: `Dist = [8, 12, 0, 7, 3]`.
 
4. 4
 
 Step 4
 
 Pass 2
 
 Now we relax all edges again using the updated distances.
 
 - Edge (5,4) weight is 2. `Dist[5] + 2 < Dist[4]`   ⟹  3+2\=5<7\\implies 3 + 2 = 5 < 7⟹3+2\=5<7. Update `Dist[4] = 5`.
 - Edge (4,1) weight is 1. `Dist[4] + 1 < Dist[1]`   ⟹  5+1\=6<8\\implies 5 + 1 = 6 < 8⟹5+1\=6<8. Update `Dist[1] = 6`.
 - Edge (5,1) weight is 4. `Dist[5] + 4 < Dist[1]`   ⟹  3+4\=7\\implies 3 + 4 = 7⟹3+4\=7 (No update, 6 is smaller).
 - Edge (4,2) weight is 4. `Dist[4] + 4 < Dist[2]`   ⟹  5+4\=9<12\\implies 5 + 4 = 9 < 12⟹5+4\=9<12. Update `Dist[2] = 9`. After Pass 2: `Dist = [6, 9, 0, 5, 3]`.
 
5. 5
 
 Step 5
 
 Pass 3 and Pass 4
 
 We relax all edges again in Pass 3 and Pass 4. If we check (4,1), `5 + 1 = 6`, no change. If we check (4,2), `5 + 4 = 9`, no change. No distances are updated in Pass 3 or Pass 4. Since no updates occurred, the algorithm can terminate early! **Final Shortest Distances from Node 3:** Node 1: 6, Node 2: 9, Node 4: 5, Node 5: 3.
 

### All-Pairs Shortest Path: Floyd-Warshall Algorithm

What if we want the shortest path between _every_ possible pair of nodes, not just from a single source? We use the **Floyd-Warshall** algorithm. It is a Dynamic Programming algorithm that utilizes an Adjacency Matrix.

**The DP Logic:** For every pair of nodes `i` and `j`, we check if going through an intermediate node `k` is shorter than the direct path.

`1For k = 1 to V: 2   For i = 1 to V: 3      For j = 1 to V: 4         Dist[i][j] = MIN( Dist[i][j] , Dist[i][k] + Dist[k][j] )`

Because of the 3 nested loops, the time complexity is strictly **O(V3)O(V^3)O(V3)**.

### Transitive Closure (Warshall's Algorithm)

Transitive Closure asks a simpler question: Is there _any_ path (direct or indirect) from node `i` to node `j`? Instead of tracking weights, the matrix only stores 111 (Path Exists) or 000 (No Path). The logic is identical to Floyd-Warshall, but uses Boolean logic (AND / OR) instead of addition and MIN.

### Knowledge Check

Question 1 of 2

Q1Single choice

Which of the following algorithm solves the All Pair Shortest Path problem?

Dijkstra’s

Floyd-Warshall’s

Prim’s

Kruskal’s

BackNext

[Dijkstra's Algorithm Visualizer\\ \\ web](https://visualgo.net/en/sssp)

[Previous\\ \\ Graph Traversals: BFS & DFS](https://coursify.hasanraiyan.me/course/design-and-analysis-of-algorithms-daa/graph-traversals-bfs-dfs) [Next\\ \\ Minimum Spanning Tree Algorithms](https://coursify.hasanraiyan.me/course/design-and-analysis-of-algorithms-daa/minimum-spanning-tree-algorithms)