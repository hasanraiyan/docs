# Source: https://coursify.hasanraiyan.me/course/design-and-analysis-of-algorithms-daa/the-complete-daa-exam-preparation-kit

# The Complete DAA Exam Preparation Kit

30 mins

A data-driven, all-module survival guide built from analyzing 75+ questions across 2022–2024 exam papers. Contains the guaranteed questions, the exact mark distribution, the 72-hour study plan, and the critical mistakes that fail students in Algorithms.

### Learning Goals

- Understand the exact module-wise mark distribution and identify the highest-ROI modules.
- Know the 8 guaranteed question types that appear every single year.
- Follow the 72-hour, 7-day, and 14-day study plans matched to your available preparation time.
- Avoid the 10 most common exam mistakes in complexity analysis and algorithm tracing.

---

### The Exam Architecture: Understanding the Paper

Before studying a single topic, understand how the exam is built. Based on 2022–2024 paper analysis:

**Paper Structure:**

- **Total Marks:** 70 marks (external exam)
- **Duration:** 3 hours
- **Section A:** 10 MCQs × 2 marks = **20 marks** (compulsory)
- **Section B:** 5 long-answer questions × 10 marks OR internal choices yielding **50 marks** total. Often split into 7-mark sub-questions.

**The Critical Implication:** Section A (MCQs) is worth 20 marks — nearly **30% of the paper** — and takes only 15–20 minutes. Getting MCQs wrong is the single biggest reason students fail who otherwise "knew the algorithms."

---

### The Module Power Ranking: Where Your Marks Actually Come From

Based on **75+ questions across 2022–2024**, here is the data-driven importance ranking:

| Rank | Module | Total PYQ Marks | Guaranteed Q? | Priority |
| --- | --- | --- | --- | --- |
| **#1** | **Module 2: Fundamental Strategies** | 129M | ✅ MCM, Knapsack, Backtracking | 🔴 CRITICAL |
| **#2** | **Module 3: Graph & Tree Algorithms** | 112M | ✅ Dijkstra, BFS/DFS, MST | 🔴 CRITICAL |
| **#3** | **Module 1: Introduction** | 108M | ✅ Master's Theorem, Substitution | 🔴 CRITICAL |
| **#4** | **Module 4: Tractable/Intractable** | 38M | ✅ P/NP Definitions, Cook's Theorem | 🟠 HIGH (Easiest marks) |
| **#5** | **Module 5: Advanced Topics** | 30M | ✅ Randomized Quick Sort | 🟡 MEDIUM |

**The ROI calculation:** If you only study **Modules 1, 2, and 3** perfectly, you can answer questions worth the vast majority of the paper. However, **Module 4** is the "hack" — it contains only 38 tracked marks, but they are the _exact same theory questions every year_. Do not skip Module 4.

### The 8 Guaranteed Question Types (Appear EVERY Year)

These are questions that have appeared in almost every exam from 2022 to 2024. If you master these 8, you can comfortably pass the paper.

---

#### 🔴 GUARANTEED #1: Matrix Chain Multiplication DP Trace (7–14 Marks)

**Module 2 | Priority: Absolute Maximum**

> Given matrix dimensions, find the minimum operations and optimal parenthesization.

- **What to practice:** Drawing the mmm (cost) and sss (split) tables.
- **Watch out for:** Miscalculating Pi−1×Pk×PjP\_{i-1} \\times P\_k \\times P\_jPi−1​×Pk​×Pj​.

#### 🔴 GUARANTEED #2: Shortest Path Trace (7 Marks)

**Module 3 | Priority: Absolute Maximum**

> Trace Dijkstra's or Bellman-Ford algorithm on a graph.

- **What to practice:** The tabular relaxation format for Dijkstra. For Bellman-Ford, explicitly showing ∣V∣−1|V|-1∣V∣−1 passes.

#### 🔴 GUARANTEED #3: Substitution Method Recurrence (7 Marks)

**Module 1 | Priority: Absolute Maximum**

> Solve a recurrence like T(n)\=3T(n/2)+nT(n) = 3T(n/2) + nT(n)\=3T(n/2)+n using substitution.

- **What to practice:** Expanding to the kkk\-th step, finding the pattern, and summing the series correctly to the base case.

#### 🔴 GUARANTEED #4: Master's Theorem Application (5–7 Marks)

**Module 1 | Priority: Absolute Maximum**

> Solve 2-3 recurrences using Master's Theorem.

- **What to practice:** Memorizing all 3 cases, especially checking the _regularity condition_ for Case 3 (af(n/b)≤cf(n)a f(n/b) \\le c f(n)af(n/b)≤cf(n)).

#### 🟠 GUARANTEED #5: P / NP / NP-Complete Definitions (7 Marks)

**Module 4 | Priority: High**

> Define P, NP, NP-Complete, and NP-Hard, and draw their relationship.

- **What to practice:** The exact wording (e.g., "verifiable in polynomial time" for NP), and the Euler diagram assuming P≠NPP \\neq NPP\=NP.

#### 🟠 GUARANTEED #6: Fractional Knapsack or Huffman Trace (7 Marks)

**Module 2 | Priority: High**

> Solve fractional knapsack or generate Huffman codes.

- **What to practice:** Always sorting by Profit/WeightProfit / WeightProfit/Weight ratio first for Knapsack.

#### 🟠 GUARANTEED #7: BFS vs DFS Comparison (7 Marks)

**Module 3 | Priority: High**

> Compare BFS and DFS in terms of data structures, complexity, and applications.

- **What to practice:** Memorizing the table: Queue vs Stack, Shortest Path vs Topological Sort.

#### 🟡 GUARANTEED #8: Cook's Theorem & Reductions (7 Marks)

**Module 4 | Priority: Medium**

> Explain Cook's Theorem and how to prove NP-Completeness via reduction.

- **What to practice:** The 3-SAT to Vertex Cover reduction trace.

### The 10 Most Common Exam Mistakes

These mistakes cost students **2–7 marks each** and are entirely avoidable:

| # | Mistake | Where | Marks Lost | Fix |
| --- | --- | --- | --- | --- |
| **1** | Applying Master's Theorem when it fails | Module 1 | 2-3M | Watch out for T(n)\=2T(n/2)+n/log⁡nT(n) = 2T(n/2) + n/\\log nT(n)\=2T(n/2)+n/logn. Master's Theorem DOES NOT apply here. |
| **2** | Skipping the regularity check in Case 3 | Module 1 | 2M | If Case 3 of Master's applies, you MUST explicitly write af(n/b)≤cf(n)a f(n/b) \\le c f(n)af(n/b)≤cf(n). |
| **3** | Using Greedy for 0/1 Knapsack | Module 2 | 7M | Greedy only works for _Fractional_ Knapsack. 0/1 Knapsack requires DP. |
| **4** | Forgetting parent nodes in Dijkstra | Module 3 | 3M | Don't just write distances. Write `10 (A)` to show _how_ you got there. |
| **5** | Bellman-Ford pass count error | Module 3 | 4M | You must show exactly $ |
| **6** | Misparenthesizing MCM result | Module 2 | 2M | Tracing the table perfectly but writing (A(BC)D)(A(BC)D)(A(BC)D) instead of (A(BC))(D)(A(BC))(D)(A(BC))(D). |
| **7** | Confusing NP-Hard and NP-Complete | Module 4 | 2M | NP-Complete must be IN NP. NP-Hard does not have to be in NP. |
| **8** | Confusing Backtracking and Branch & Bound | Module 2 | 3M | Backtracking finds _all_ solutions (DFS). B&B finds the _optimal_ solution (BFS/Priority Queue). |
| **9** | Not drawing the state-space tree | Module 2 | 4M | For N-Queens or Graph Coloring, the tree diagram IS the answer. |
| **10** | Confusing Las Vegas and Monte Carlo | Module 5 | 2M | Las Vegas = time varies, answer correct. Monte Carlo = time fixed, answer might be wrong. |

### The Study Plans: 72 Hours, 7 Days, and 14 Days

---

#### 🔴 THE 72-HOUR EMERGENCY PLAN (3 Days Before Exam)

**Goal:** Pass (35/70 marks). Focus ONLY on guaranteed numericals and easy theory.

| Day | Hours | What to Study |
| --- | --- | --- |
| **Day 1** (8hr) | 4hr | Module 1: Master's Theorem (all 3 cases) + Substitution Method traces. |
| | 4hr | Module 4: Memorize P/NP/NPC definitions, diagram, and Cook's Theorem. |
| **Day 2** (8hr) | 4hr | Module 3: Trace Dijkstra's and Bellman-Ford 3 times each on paper. |
| | 4hr | Module 3: Memorize BFS vs DFS, Prim's vs Kruskal's theory tables. |
| **Day 3** (4hr) | 2hr | Module 2: Practice Fractional Knapsack and Huffman Coding. |
| | 2hr | Revise all PYQ MCQs. Do NOT attempt Matrix Chain Multiplication (too risky to learn in 1 hour). |

**Expected score:** 40–55 marks. **You will pass.**

---

#### 🟡 THE 7-DAY PLAN (One Week Before Exam)

**Goal:** Score well (50–60/70 marks).

| Day | Focus Module | Topics |
| --- | --- | --- |
| **Day 1** | Module 1 | Asymptotic notations, Substitution method, Master's Theorem. |
| **Day 2** | Module 2 | Fractional Knapsack, Huffman, Compare DP/Greedy/D&C. |
| **Day 3** | Module 2 | **Matrix Chain Multiplication DP** (spend the whole day tracing this). |
| **Day 4** | Module 3 | Dijkstra, Bellman-Ford, Floyd-Warshall. |
| **Day 5** | Module 3 | BFS, DFS, Prim's, Kruskal's, Topological Sort. |
| **Day 6** | Mod 4 & 5 | P/NP definitions, reductions, Randomized Quick Sort. |
| **Day 7** | **Revision** | Redo all 2022–2024 MCQs. Practice 1 MCM and 1 Dijkstra trace. |

---

#### 🟢 THE 14-DAY MASTERY PLAN (Two Weeks Before Exam)

**Goal:** Score 65+ marks. Follow the 7-day plan, but allocate 2 full days to Module 2 (adding N-Queens, Graph Coloring, TSP), 2 full days to Module 3 (adding Ford-Fulkerson Max Flow), and take 2 full 3-hour mock exams using the 2023 and 2024 papers.

### Quick-Reference: The 15 Definitions You MUST Memorize

| # | Term | One-Line Definition |
| --- | --- | --- |
| 1 | **Big-O (O)** | Asymptotic upper bound (worst-case scenario). |
| 2 | **Big-Omega (Ω)** | Asymptotic lower bound (best-case scenario). |
| 3 | **Big-Theta (Θ)** | Asymptotic tight bound (average/exact case). |
| 4 | **Dynamic Programming** | Solves optimization problems by breaking them into overlapping subproblems and storing results (memoization/tabulation). |
| 5 | **Greedy Method** | Makes the locally optimal choice at each step with the hope of finding the global optimum. |
| 6 | **Backtracking** | Explores all possible solutions via DFS, abandoning a path (pruning) as soon as it violates constraints. |
| 7 | **Branch and Bound** | Explores solutions to find the _optimal_ one, pruning branches whose lower bound is worse than the best known solution. |
| 8 | **Minimum Spanning Tree** | A subset of edges in a weighted undirected graph that connects all vertices without cycles, with minimum total edge weight. |
| 9 | **Topological Sort** | A linear ordering of vertices in a DAG such that for every directed edge U→V, vertex U comes before V. |
| 10 | **P Class** | Decision problems solvable in polynomial time by a deterministic Turing machine. |
| 11 | **NP Class** | Decision problems whose solutions can be _verified_ in polynomial time. |
| 12 | **NP-Hard** | Problems to which _every_ problem in NP can be reduced in polynomial time. |
| 13 | **NP-Complete** | Problems that are BOTH in NP and are NP-Hard. |
| 14 | **Cook's Theorem** | States that the Boolean Satisfiability Problem (SAT) is NP-Complete. |
| 15 | **Las Vegas Algorithm** | A randomized algorithm that always gives the correct answer, but its runtime varies. |

### Formula Sheet: The Survival Equations

**Master's Theorem:** T(n)\=aT(n/b)+f(n)T(n) = aT(n/b) + f(n)T(n)\=aT(n/b)+f(n)

1. If f(n)\=O(nlog⁡ba−ϵ)f(n) = O(n^{\\log\_b a - \\epsilon})f(n)\=O(nlogb​a−ϵ), then T(n)\=Θ(nlog⁡ba)T(n) = \\Theta(n^{\\log\_b a})T(n)\=Θ(nlogb​a)
2. If f(n)\=Θ(nlog⁡ba)f(n) = \\Theta(n^{\\log\_b a})f(n)\=Θ(nlogb​a), then T(n)\=Θ(nlog⁡balog⁡n)T(n) = \\Theta(n^{\\log\_b a} \\log n)T(n)\=Θ(nlogb​alogn)
3. If f(n)\=Ω(nlog⁡ba+ϵ)f(n) = \\Omega(n^{\\log\_b a + \\epsilon})f(n)\=Ω(nlogb​a+ϵ) AND af(n/b)≤cf(n)af(n/b) \\le cf(n)af(n/b)≤cf(n), then T(n)\=Θ(f(n))T(n) = \\Theta(f(n))T(n)\=Θ(f(n))

**Matrix Chain Multiplication:** m\[i,j\]\=min⁡i≤k<j{m\[i,k\]+m\[k+1,j\]+Pi−1PkPj}m\[i, j\] = \\min\_{i \\le k < j} \\{ m\[i, k\] + m\[k+1, j\] + P\_{i-1} P\_k P\_j \\}m\[i,j\]\=mini≤k<j​{m\[i,k\]+m\[k+1,j\]+Pi−1​Pk​Pj​}

**Algorithm Time Complexities:**

- **Binary Search**: O(log⁡n)O(\\log n)O(logn)
- **Merge Sort / Quick Sort (Avg)**: O(nlog⁡n)O(n \\log n)O(nlogn)
- **BFS / DFS**: O(V+E)O(V + E)O(V+E)
- **Dijkstra's**: O(Elog⁡V)O(E \\log V)O(ElogV) (with Min-Heap)
- **Bellman-Ford**: O(V×E)O(V \\times E)O(V×E)
- **Floyd-Warshall**: O(V3)O(V^3)O(V3)
- **Prim's / Kruskal's**: O(Elog⁡V)O(E \\log V)O(ElogV)

### Knowledge Check

Question 1 of 2

Q1Single choice

You have exactly 3 hours before the DAA exam. Which numerical traces MUST you practice on paper to guarantee passing?

N-Queens and TSP Branch & Bound

Substitution Method, Dijkstra's Algorithm, and Master's Theorem

Ford-Fulkerson and KMP String Matching

Randomized Quick Sort and Vertex Cover Approximation

BackNext

[PYQDeck — Practice All DAA PYQs\\ \\ web](https://pyqdeck.in/it/it_sem5/it_sem5_106502/practice/)

[Previous\\ \\ PYQ Analysis & Exam Preparation — Module 5](https://coursify.hasanraiyan.me/course/design-and-analysis-of-algorithms-daa/pyq-analysis-exam-preparation-module-5)