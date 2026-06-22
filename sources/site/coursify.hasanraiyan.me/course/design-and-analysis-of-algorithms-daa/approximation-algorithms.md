# Source: https://coursify.hasanraiyan.me/course/design-and-analysis-of-algorithms-daa/approximation-algorithms

# Approximation Algorithms

30 mins

Understand how to solve intractable optimization problems by trading exact optimality for guaranteed speed using Approximation Algorithms, focusing on the Vertex Cover problem.

### Learning Goals

- Define Approximation Algorithms and the Approximation Ratio.
- Explain why Approximation Algorithms are critical for solving NP-Hard optimization problems.
- Trace the 2-Approximation Algorithm for the Vertex Cover problem.

---

### Why Approximation Algorithms?

In previous modules, we learned that **NP-Hard optimization problems** (like the Traveling Salesperson Problem, Bin Packing, or Vertex Cover) have no known polynomial-time algorithms. If we want the _exact optimal_ answer, we are forced to use algorithms like Backtracking or Branch & Bound, which take exponential time (O(2n)O(2^n)O(2n)) and crash on large datasets.

**Approximation Algorithms** are the engineering compromise. Instead of spending centuries looking for the perfect answer, they guarantee a "near-optimal" answer in fast, polynomial time.

### The Approximation Ratio (ρ\\rhoρ)

We measure how "near-optimal" the algorithm is using the Approximation Ratio (ρ\\rhoρ). For a minimization problem (like finding the smallest vertex cover), the ratio is: ρ\=Cost of Approximation AlgorithmCost of True Optimal Solution\\rho = \\frac{\\text{Cost of Approximation Algorithm}}{\\text{Cost of True Optimal Solution}}ρ\=Cost of True Optimal SolutionCost of Approximation Algorithm​

If an algorithm has a ratio of **2**, it is called a "2-Approximation Algorithm." This mathematically guarantees that the answer it gives will _never_ be more than twice the size of the true optimal answer, no matter the input.

### Trace: 2-Approximation Algorithm for Vertex Cover

1. 1
 
 Step 1
 
 The Objective (2024 Q9b iii)
 
 The Vertex Cover problem asks us to find the minimum number of vertices that touch every single edge in a graph. Finding the true minimum is NP-Hard. We will trace a greedy 2-Approximation algorithm that runs in O(V+E)O(V+E)O(V+E) time.
 
2. 2
 
 Step 2
 
 The Target Graph
 
 _Optimal Vertex Cover:_ Nodes {B, E} (Size = 2). They touch all 5 edges.
 
3. 3
 
 Step 3
 
 The Algorithm Logic
 
 1. Initialize an empty set CCC for the cover.
 2. While there are edges left in the graph:
 - Pick _any_ arbitrary edge (u,v)(u, v)(u,v).
 - Add BOTH endpoints uuu and vvv to the cover CCC.
 - Remove every edge from the graph that touches uuu or vvv.
 3. Return CCC.
 
4. 4
 
 Step 4
 
 Step 1: Pick an Edge
 
 Let's randomly pick edge **(C, E)**. We add both **C** and **E** to our cover: C\={C,E}C = \\{C, E\\}C\={C,E}. We now delete edge (C,E), and all other edges touching C or E. This deletes (B,C) and (B,D). Wait, D is connected to E! It deletes (C,E), (B,C), and (D,E).
 
5. 5
 
 Step 5
 
 Step 2: Pick Another Edge
 
 The only edge surviving in the graph is **(A, B)**. We pick edge (A, B). We add both **A** and **B** to our cover: C\={C,E,A,B}C = \\{C, E, A, B\\}C\={C,E,A,B}. We delete edge (A,B). The graph now has 0 edges left.
 
6. 6
 
 Step 6
 
 Evaluating the Approximation
 
 Our greedy algorithm returned a cover of size **4** (nodes C, E, A, B). The true optimal cover was size **2** (nodes B, E). Notice that our answer (444) is exactly 2×2 \\times2× the optimal (222). Because we add _both_ endpoints of an edge every time, the worst we can ever do is exactly double the optimal answer. This mathematically proves it is a **2-Approximation Algorithm**!
 

### Knowledge Check

Question 1 of 2

Q1Single choice

Why are Approximation Algorithms important in the context of NP-hard problems?

Because they find the exact optimal solution faster than Branch and Bound.

Because they guarantee a near-optimal solution in polynomial time when exact algorithms would take exponential time.

Because they convert NP-Hard problems into Class P problems.

Because they always find the optimal solution by making random choices.

BackNext

[Previous\\ \\ PYQ Analysis & Exam Preparation — Module 4](https://coursify.hasanraiyan.me/course/design-and-analysis-of-algorithms-daa/pyq-analysis-exam-preparation-module-4) [Next\\ \\ Randomized Algorithms](https://coursify.hasanraiyan.me/course/design-and-analysis-of-algorithms-daa/randomized-algorithms)