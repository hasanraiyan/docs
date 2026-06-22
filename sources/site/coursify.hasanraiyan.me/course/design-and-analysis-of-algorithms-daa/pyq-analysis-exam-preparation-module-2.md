# Source: https://coursify.hasanraiyan.me/course/design-and-analysis-of-algorithms-daa/pyq-analysis-exam-preparation-module-2

# PYQ Analysis & Exam Preparation — Module 2

60 mins

A strategic analysis of 21 exam questions spanning 2022–2024. Module 2 covers the core algorithmic paradigms: Greedy, Dynamic Programming, Backtracking, and Branch-and-Bound. It is heavily numerical, featuring matrix chain multiplication, knapsack, and sorting traces.

### Learning Goals

- Identify the guaranteed numerical question types: Matrix Chain Multiplication (DP), Fractional Knapsack (Greedy), and Backtracking traces (Hamiltonian/N-Queens).
- Practice with actual MCQ questions from 2022–2024 papers.
- Understand the theoretical differences between Greedy, DP, Backtracking, and Branch-and-Bound.

---

### The Exam Blueprint: Module 2 PYQ Deep Analysis (2022–2024)

An analysis of **21 exam questions spanning 2022 to 2024** reveals that Module 2 is the core application module of the course. It heavily emphasizes **Dynamic Programming (MCM)**, **Greedy Algorithms (Knapsack/Huffman)**, and **Backtracking/Branch-and-Bound** traces. You must be prepared to trace large matrices and state-space trees.

#### Complete PYQ Table (21 Questions)

| Year | Q# | Marks | Topic | Type |
| --- | --- | --- | --- | --- |
| 2023 | Q1b | **2** | Best average case sorting (Quick sort) | MCQ |
| 2024 | Q1d | **2** | DP solves by combining subproblems | MCQ |
| 2023 | Q1g | **2** | DP advantage over brute force (avoids redundancy) | MCQ |
| 2023 | Q1h | **2** | Dividing into smaller subproblems (DP/D&C) | MCQ |
| 2022 | Q1j | **2** | Kruskal algorithm is Greedy | MCQ |
| 2022 | Q2b | **7** | KMP algorithm and trace | Theory+Num |
| 2023 | Q3b | **9** | Quick Sort trace + comparisons | Theory+Num |
| 2022 | Q3b | **7** | Quick Sort algorithm + Best/Worst/Avg cases | Theory |
| 2024 | Q3b | **7** | Compare DP and Greedy (Overlapping/Substructure) | Theory |
| 2024 | Q4a | **7** | 0/1 Knapsack using Brute-force, Greedy, DP, B&B | Theory |
| 2022 | Q4b | **7** | Graph 3-colouring using Backtracking | Numerical |
| 2023 | Q4b | **7** | Fractional Knapsack using Greedy | Numerical |
| 2024 | Q4b | **7** | TSP using Branch-and-Bound | Numerical |
| 2022 | Q5a | **7** | Differentiate Divide & Conquer, Greedy, DP | Theory |
| 2023 | Q5a | **10** | Hamiltonian cycle using Backtracking (Matrix) | Numerical |
| 2022 | Q5b | **7** | Matrix Chain Multiplication (DP) trace | Numerical |
| 2023 | Q5b | **4** | Differentiate Backtracking and Branch & Bound | Theory |
| 2022 | Q6a | **7** | N-Queens solution pseudocode (Backtracking) | Theory |
| 2022 | Q6b | **7** | Huffman codes generation | Numerical |
| 2023 | Q8 | **14** | Matrix Chain Multiplication (DP) trace | Numerical |
| 2022 | Q8a | **7** | Fractional Knapsack optimal solution | Numerical |

**Total marks tracked: 129 marks across 3 years.**

---

#### Topic Heat Map

| Topic | 2022 | 2023 | 2024 | Total Marks |
| --- | --- | --- | --- | --- |
| **Dynamic Programming (MCM & Theory)** | 7M ✅ | 18M ✅ | 16M ✅ | **41M** |
| **Greedy Algorithms (Knapsack, Huffman)** | 16M ✅ | 7M ✅ | — | **23M** |
| **Backtracking (N-Queens, Hamiltonian, Coloring)** | 14M ✅ | 10M ✅ | — | **24M** |
| **Branch and Bound (TSP)** | — | 4M ✅ | 7M ✅ | **11M** |
| **Quick Sort & KMP** | 14M ✅ | 9M ✅ | — | **23M** |
| **MCQs** | 2M ✅ | 6M ✅ | 2M ✅ | **10M** |

---

#### The Guaranteed Question Types

> **1\. 🔴 Dynamic Programming: Matrix Chain Multiplication (7–14M)** Appeared in 2022 and 2023. You must construct the mmm (cost) and sss (split) tables. The 2023 paper asked a massive 14-mark version with 5 matrices.

> **2\. 🔴 Greedy Algorithms: Fractional Knapsack or Huffman (7M)** Highly predictable. Sort items by profit/weight ratio for Knapsack, or build the min-heap tree for Huffman coding.

> **3\. 🟠 Backtracking / Branch-and-Bound Traces (7–10M)** Drawing the state-space tree is mandatory. Problems rotate between Graph Coloring, Hamiltonian Cycle, N-Queens, and TSP.

> **4\. 🟡 Quick Sort (7–9M)** Frequently asked to trace the partition steps and explicitly define the best/worst/average case time complexities.

### Solved Numericals: The Exam-Critical Calculations

---

#### Numerical 1: Matrix Chain Multiplication (DP)

> _"Find minimum operations for matrix chain: A(10×20), B(20×50), C(50×1), D(1×100)."_

**Dimension array PPP:** P\=\[10,20,50,1,100\]P = \[10, 20, 50, 1, 100\]P\=\[10,20,50,1,100\] (Number of matrices n\=4n=4n\=4)

**Formula:** m\[i,j\]\=min⁡i≤k<j{m\[i,k\]+m\[k+1,j\]+Pi−1PkPj}m\[i, j\] = \\min\_{i \\le k < j} \\{ m\[i, k\] + m\[k+1, j\] + P\_{i-1} P\_k P\_j \\}m\[i,j\]\=mini≤k<j​{m\[i,k\]+m\[k+1,j\]+Pi−1​Pk​Pj​}

**Step 1: Chain length = 1** m\[1,1\]\=m\[2,2\]\=m\[3,3\]\=m\[4,4\]\=0m\[1,1\] = m\[2,2\] = m\[3,3\] = m\[4,4\] = 0m\[1,1\]\=m\[2,2\]\=m\[3,3\]\=m\[4,4\]\=0

**Step 2: Chain length = 2** m\[1,2\]\=m\[1,1\]+m\[2,2\]+10×20×50\=10,000m\[1,2\] = m\[1,1\] + m\[2,2\] + 10 \\times 20 \\times 50 = 10,000m\[1,2\]\=m\[1,1\]+m\[2,2\]+10×20×50\=10,000 (Split k\=1k=1k\=1) m\[2,3\]\=m\[2,2\]+m\[3,3\]+20×50×1\=1,000m\[2,3\] = m\[2,2\] + m\[3,3\] + 20 \\times 50 \\times 1 = 1,000m\[2,3\]\=m\[2,2\]+m\[3,3\]+20×50×1\=1,000 (Split k\=2k=2k\=2) m\[3,4\]\=m\[3,3\]+m\[4,4\]+50×1×100\=5,000m\[3,4\] = m\[3,3\] + m\[4,4\] + 50 \\times 1 \\times 100 = 5,000m\[3,4\]\=m\[3,3\]+m\[4,4\]+50×1×100\=5,000 (Split k\=3k=3k\=3)

**Step 3: Chain length = 3** m\[1,3\]\=min⁡{k\=1:m\[1,1\]+m\[2,3\]+10×20×1\=0+1000+200\=1,200k\=2:m\[1,2\]+m\[3,3\]+10×50×1\=10000+0+500\=10,500m\[1,3\] = \\min \\begin{cases} k=1: m\[1,1\] + m\[2,3\] + 10 \\times 20 \\times 1 = 0 + 1000 + 200 = \\mathbf{1,200} \\\\ k=2: m\[1,2\] + m\[3,3\] + 10 \\times 50 \\times 1 = 10000 + 0 + 500 = 10,500 \\end{cases}m\[1,3\]\=min{k\=1:m\[1,1\]+m\[2,3\]+10×20×1\=0+1000+200\=1,200k\=2:m\[1,2\]+m\[3,3\]+10×50×1\=10000+0+500\=10,500​ Optimal split for m\[1,3\]m\[1,3\]m\[1,3\] is k\=1k=1k\=1.

m\[2,4\]\=min⁡{k\=2:m\[2,2\]+m\[3,4\]+20×50×100\=0+5000+100,000\=105,000k\=3:m\[2,3\]+m\[4,4\]+20×1×100\=1000+0+2000\=3,000m\[2,4\] = \\min \\begin{cases} k=2: m\[2,2\] + m\[3,4\] + 20 \\times 50 \\times 100 = 0 + 5000 + 100,000 = 105,000 \\\\ k=3: m\[2,3\] + m\[4,4\] + 20 \\times 1 \\times 100 = 1000 + 0 + 2000 = \\mathbf{3,000} \\end{cases}m\[2,4\]\=min{k\=2:m\[2,2\]+m\[3,4\]+20×50×100\=0+5000+100,000\=105,000k\=3:m\[2,3\]+m\[4,4\]+20×1×100\=1000+0+2000\=3,000​ Optimal split for m\[2,4\]m\[2,4\]m\[2,4\] is k\=3k=3k\=3.

**Step 4: Chain length = 4** m\[1,4\]\=min⁡{k\=1:m\[1,1\]+m\[2,4\]+10×20×100\=0+3000+20000\=23,000k\=2:m\[1,2\]+m\[3,4\]+10×50×100\=10000+5000+50000\=65,000k\=3:m\[1,3\]+m\[4,4\]+10×1×100\=1200+0+1000\=2,200m\[1,4\] = \\min \\begin{cases} k=1: m\[1,1\] + m\[2,4\] + 10 \\times 20 \\times 100 = 0 + 3000 + 20000 = 23,000 \\\\ k=2: m\[1,2\] + m\[3,4\] + 10 \\times 50 \\times 100 = 10000 + 5000 + 50000 = 65,000 \\\\ k=3: m\[1,3\] + m\[4,4\] + 10 \\times 1 \\times 100 = 1200 + 0 + 1000 = \\mathbf{2,200} \\end{cases}m\[1,4\]\=min⎩⎨⎧​k\=1:m\[1,1\]+m\[2,4\]+10×20×100\=0+3000+20000\=23,000k\=2:m\[1,2\]+m\[3,4\]+10×50×100\=10000+5000+50000\=65,000k\=3:m\[1,3\]+m\[4,4\]+10×1×100\=1200+0+1000\=2,200​

**Result:** The minimum number of multiplications is **2,200**. **Optimal Parenthesization:** Using the kkk values, the split for 1..4 is at 3, so `(A..C)(D)`. For 1..3 the split is at 1, so `(A)(BC)`. Final result: **( A ( B C ) ) D**. **Complexity:** O(n3)O(n^3)O(n3) time and O(n2)O(n^2)O(n2) space.

---

#### Numerical 2: Fractional Knapsack (Greedy)

> _"Capacity W=15. Objects (Profit, Weight): (5,1), (10,3), (15,5), (7,4), (8,1), (9,3), (4,2). Find max profit."_

**Step 1: Calculate Profit/Weight ratios (P/WP/WP/W) and Sort descending**

| Item | Profit | Weight | Ratio (P/WP/WP/W) | Rank |
| --- | --- | --- | --- | --- |
| 1 | 5 | 1 | 5.0 | 2 |
| 2 | 10 | 3 | 3.33 | 3 |
| 3 | 15 | 5 | 3.0 | 4 (tie) |
| 4 | 7 | 4 | 1.75 | 7 |
| 5 | 8 | 1 | 8.0 | 1 |
| 6 | 9 | 3 | 3.0 | 5 (tie) |
| 7 | 4 | 2 | 2.0 | 6 |

**Step 2: Add to knapsack (Capacity = 15)**

1. Take Item 5 (Wt 1). Remaining = 14. Profit = 8.
2. Take Item 1 (Wt 1). Remaining = 13. Profit = 8 + 5 = 13.
3. Take Item 2 (Wt 3). Remaining = 10. Profit = 13 + 10 = 23.
4. Take Item 3 (Wt 5). Remaining = 5. Profit = 23 + 15 = 38.
5. Take Item 6 (Wt 3). Remaining = 2. Profit = 38 + 9 = 47.
6. Take Item 7 (Wt 2). Remaining = 0. Profit = 47 + 4 = 51.

**Result:** The knapsack is exactly full (15 units) without needing a fraction of any item. Total max profit is **51**. Item 4 is left behind.

### Knowledge Check

Question 1 of 4

Q1Single choice

Which of the following sorting algorithms has the best time complexity in the average case?

Bubble sort

Insertion sort

Quick sort

Selection sort

BackNext

### High-Yield Subjective Bank: Structure Your Answers

---

####Differentiate Divide & Conquer, Greedy, and Dynamic Programming (7 Marks)\*\*

**Answer structure (Table Format):**

| Feature | Divide & Conquer | Dynamic Programming | Greedy Method |
| --- | --- | --- | --- |
| **Approach** | Top-down. | Bottom-up (Tabulation) or Top-down (Memoization). | Top-down decision making. |
| **Subproblems** | Independent subproblems. | Overlapping subproblems. | No overlapping subproblems; relies on greedy choice. |
| **Optimization** | Not strictly for optimization. | Always used for optimization problems. | Used for optimization problems. |
| **Decision Making** | Combines solutions of subproblems blindly. | Explores all possible choices before picking the optimal one. | Makes the locally optimal choice immediately, never looks back. |
| **Global Optimum** | N/A | Guaranteed to find global optimum. | Not always guaranteed to find global optimum. |
| **Example** | Merge Sort, Quick Sort. | Matrix Chain Multiplication, 0/1 Knapsack. | Kruskal's, Fractional Knapsack. |

---

####Differentiate Backtracking and Branch & Bound (4 Marks)\*\*

**Answer structure:**

1. **Goal**:
 - _Backtracking_ is used to find **all** possible solutions (e.g., all arrangements of N-Queens) or any satisfying solution.
 - _Branch & Bound_ is used strictly to find the **optimal** (minimum or maximum) solution (e.g., shortest TSP route).
2. **Traversal Method**:
 - _Backtracking_ uses **Depth-First Search (DFS)**.
 - _Branch & Bound_ typically uses **Breadth-First Search (BFS)** or **Best-First Search** (using a priority queue).
3. **Pruning Mechanism**:
 - _Backtracking_ prunes the tree when the current state violates constraints (bounding function).
 - _Branch & Bound_ calculates a bound (e.g., lower bound cost) at each node. If a node's bound is worse than the best solution found so far, the entire branch is pruned.
4. **Applicability**:
 - Backtracking: Graph coloring, N-Queens, Sudoku.
 - Branch & Bound: TSP, 0/1 Knapsack optimization.

---

####Why Greedy Fails for 0/1 Knapsack (Part of 7 Marks)\*\*

**Answer structure:**

1. **The Greedy Property**: A greedy algorithm assumes that taking the item with the highest Profit/Weight ratio will lead to the global maximum.
2. **The 0/1 Constraint**: Unlike Fractional Knapsack, you cannot take a fraction of an item. You either take the whole item (1) or leave it (0).
3. **The Failure Case**:
 - Capacity W\=50W = 50W\=50.
 - Item 1: Profit = 60, Weight = 10 (P/W\=6P/W = 6P/W\=6).
 - Item 2: Profit = 100, Weight = 20 (P/W\=5P/W = 5P/W\=5).
 - Item 3: Profit = 120, Weight = 30 (P/W\=4P/W = 4P/W\=4).
 - **Greedy approach**: Picks Item 1 first (best ratio). Remaining weight = 40. Then picks Item 2. Remaining weight = 20. Cannot fit Item 3. Total Profit = **160**.
 - **Optimal (DP) approach**: Pick Item 2 and Item 3. Total weight = 50 (fits perfectly). Total Profit = **220**.
4. **Conclusion**: Because taking a high-ratio item might leave empty, unusable space in the knapsack, the greedy choice does not guarantee optimal substructure for the 0/1 variant. Dynamic Programming must be used to evaluate all combinations.

[Matrix Chain Multiplication - Visualized\\ \\ web](https://www.geeksforgeeks.org/matrix-chain-multiplication-dp-8/)

[Previous\\ \\ Problem Applications: Bin Packing, Knapsack & TSP](https://coursify.hasanraiyan.me/course/design-and-analysis-of-algorithms-daa/problem-applications-bin-packing-knapsack-tsp) [Next\\ \\ Graph Traversals: BFS & DFS](https://coursify.hasanraiyan.me/course/design-and-analysis-of-algorithms-daa/graph-traversals-bfs-dfs)