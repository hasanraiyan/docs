# Source: https://coursify.hasanraiyan.me/course/design-and-analysis-of-algorithms-daa/cooks-theorem-reduction-techniques

# Cook's Theorem & Reduction Techniques

50 mins

Learn the foundational theorem of complexity theory. Understand how polynomial-time reductions are used to prove NP-completeness, complete with a step-by-step trace of reducing 3-SAT to Vertex Cover.

### Learning Goals

- State Cook's Theorem and explain its foundational importance.
- Identify the standard NP-Complete problems as defined by the syllabus.
- Understand the properties and purpose of Polynomial-Time Reductions.
- Trace the mathematical reduction from 3-SAT to Vertex Cover using Graph Gadgets.

---

### Cook's Theorem

_(Directly answers 2024 Q8a ii & iii)_

**Cook's Theorem (1971)** states that the Boolean Satisfiability Problem (SAT) is **NP-Complete**.

**Why is this a foundational result?** Before Stephen Cook (and Leonid Levin), the NP-Complete class was just a theory. No one knew if an NP-Complete problem actually existed. Cook proved that _any_ problem in the NP class (from factoring large numbers to finding graph paths) could be converted (reduced) into a boolean SAT formula in polynomial time.

By providing the very first mathematically proven NP-Complete problem, Cook gave computer scientists a "seed." From that day on, to prove a new problem was NP-Complete, you didn't have to reduce _every_ NP problem to it; you only had to reduce SAT to it!

### Standard NP-Complete Problems

Once Cook proved SAT was NP-Complete, Richard Karp published 21 other problems that could be reduced from SAT. According to the syllabus, you must be familiar with these "Standard" NP-Complete problems:

1. **Boolean Satisfiability (SAT / 3-SAT):** Can you assign TRUE/FALSE to boolean variables such that the entire formula evaluates to TRUE?
2. **Clique Problem:** Does a graph contain a complete subgraph (where every node connects to every other node) of size kkk?
3. **Vertex Cover:** Can you find a set of kkk vertices such that every single edge in the graph touches at least one of those vertices?
4. **Hamiltonian Cycle:** Is there a path in the graph that visits every vertex exactly once and returns to the start?
5. **Traveling Salesperson (Decision Version):** Is there a Hamiltonian cycle with a total weight ≤k\\le k≤k?
6. **0/1 Knapsack (Decision Version):** Can you pick items such that the total profit is ≥P\\ge P≥P while the total weight is ≤W\\le W≤W?

### Polynomial-Time Reduction (A≤pBA \\le\_p BA≤p​B)

_(Directly answers 2024 Q8b i & ii)_

A **Polynomial-Time Reduction** is an algorithm that transforms instances of Problem A into instances of Problem B in polynomial time, such that the answer to B is "YES" if and only if the answer to A is "YES".

We write this mathematically as **A≤pBA \\le\_p BA≤p​B** (A reduces to B).

**How it proves NP-Completeness:** If we already know that Problem A is NP-Complete (e.g., 3-SAT), and we successfully write a polynomial-time reduction from A to our new Problem B (e.g., Vertex Cover), it proves that Problem B is _at least as hard_ as A. If B is also verifiable in polynomial time (in NP), then B is officially proven to be **NP-Complete**.

**Key Properties of Reduction:** _(Answers 2022 Q1i)_

- If A≤pBA \\le\_p BA≤p​B and B∈PB \\in PB∈P, then A∈PA \\in PA∈P (If B is easy, A must be easy).
- If A≤pBA \\le\_p BA≤p​B and A∉PA \\notin PA∈/P, then B∉PB \\notin PB∈/P (If A is hard, B must be hard).
- **Transitivity:** If A≤pBA \\le\_p BA≤p​B and B≤pCB \\le\_p CB≤p​C, then A≤pCA \\le\_p CA≤p​C.

### Trace: Reducing 3-SAT to Vertex Cover

1. 1
 
 Step 1
 
 The Objective (2024 Q8b iii)
 
 We want to prove that the Vertex Cover problem is NP-Complete. To do this, we will reduce **3-SAT** (a known NP-Complete problem) to **Vertex Cover**. We must convert a boolean formula into an undirected graph.
 
2. 2
 
 Step 2
 
 The 3-SAT Formula
 
 Let's take a simple 3-SAT Boolean formula with n\=2n=2n\=2 variables and m\=1m=1m\=1 clauses. Formula: F\=(x1∨xˉ1∨x2)F = (x\_1 \\lor \\bar{x}\_1 \\lor x\_2)F\=(x1​∨xˉ1​∨x2​). Our goal is to construct a graph GGG that has a Vertex Cover of size kkk **if and only if** FFF is satisfiable.
 
3. 3
 
 Step 3
 
 Step 1: Construct Variable Gadgets
 
 For each variable xix\_ixi​, we create two vertices in our graph: one for xix\_ixi​ and one for xˉi\\bar{x}\_ixˉi​. We connect them with an edge. Because they are connected, any valid Vertex Cover MUST select at least one of them. Selecting xix\_ixi​ means we assign the variable TRUE; selecting xˉi\\bar{x}\_ixˉi​ means we assign it FALSE.
 
4. 4
 
 Step 4
 
 Step 2: Construct Clause Gadgets
 
 For each clause, we create a triangle of 3 vertices connected to each other. Because it's a triangle, any valid Vertex Cover MUST select at least 2 of the 3 vertices to cover the inner edges.
 
5. 5
 
 Step 5
 
 Step 3: Connect Gadgets to Clauses
 
 We draw edges connecting the literal nodes in the variable gadgets to their corresponding nodes in the clause triangles. To cover these connecting edges, if the Vertex Cover doesn't pick the clause vertex, it _must_ pick the variable vertex (making that literal TRUE, satisfying the clause!).
 
6. 6
 
 Step 6
 
 Step 4: The Target Size kkk
 
 We set our target Vertex Cover size to: **k\=n+2mk = n + 2mk\=n+2m**
 
 - nnn vertices come from selecting exactly one truth value for each of the nnn variables.
 - 2m2m2m vertices come from selecting exactly 2 vertices in each of the mmm clause triangles. If the graph has a vertex cover of exactly size kkk, it mathematically proves there is a valid truth assignment satisfying all clauses in FFF. The reduction is complete!
 

### Knowledge Check

Question 1 of 2

Q1Single choice

What is the primary technique used to prove that a problem is NP-complete?

Divide and conquer

Dynamic programming

Polynomial-time reduction from a known NP-complete problem

Space complexity calculation

BackNext

[Previous\\ \\ NP-Complete and NP-Hard Problems](https://coursify.hasanraiyan.me/course/design-and-analysis-of-algorithms-daa/np-complete-and-np-hard-problems) [Next\\ \\ PYQ Analysis & Exam Preparation — Module 4](https://coursify.hasanraiyan.me/course/design-and-analysis-of-algorithms-daa/pyq-analysis-exam-preparation-module-4)