# Source: https://coursify.hasanraiyan.me/course/design-and-analysis-of-algorithms-daa/computability-complexity-classes-p-and-np

# Computability & Complexity Classes: P and NP

30 mins

Dive into computational complexity theory. Understand the difference between finding a solution (Class P) and verifying a solution (Class NP).

### Learning Goals

- Define Tractability and Intractability in algorithms.
- Understand Class P and identify problems that belong to it.
- Understand Class NP and the concept of Nondeterministic Polynomial time.
- Explain the relationship between P and NP.

---

### Tractable vs. Intractable Problems

Before we classify problems, we must understand how we measure them:

- **Tractable Problems:** Problems that can be solved in **Polynomial Time**. This means the algorithm's time complexity is bounded by O(nk)O(n^k)O(nk) for some constant kkk. Examples: O(n)O(n)O(n), O(nlog⁡n)O(n \\log n)O(nlogn), O(n2)O(n^2)O(n2). We consider these "efficiently solvable" by modern computers.
- **Intractable Problems:** Problems that CANNOT be solved in polynomial time. Their time complexity grows exponentially (O(2n)O(2^n)O(2n)) or factorially (O(n!)O(n!)O(n!)). For large inputs, these problems would take centuries to compute, even on supercomputers.

Pro-Tips & Pitfalls

Real-World ImpactExam Strategy

- **NP ≠ "Non-Polynomial":** This is the most frequent error. NP stands for **Nondeterministic Polynomial**. Many problems in NP (like those in P) _are_ solvable in polynomial time.
- **Verification vs. Solution:** Being in NP only means a solution is easy to **check**, not necessarily easy to **find**.
- **P vs. NP Status:** Remember that P\=NPP = NPP\=NP is currently **unproven**. While most researchers suspect PeqNPP eq NPPeqNP, we don't have a mathematical proof yet.

#### Undecidable Problems

There is a separate category called **Undecidable Problems**, like the Halting Problem, which cannot be solved by any algorithm at all, no matter how much time is given.

more...

### Class P (Polynomial Time)

**Class P** contains all decision problems that can be **solved** by a deterministic computer (like the one you are using) in polynomial time.

If a problem is in P, we have a fast, known algorithm to find the correct YES/NO answer.

- **Examples in P:**
 - Is array A sorted? (O(n)O(n)O(n))
 - Is there a path from node X to Y? (BFS: O(V+E)O(V+E)O(V+E))
 - What is the shortest path? (Dijkstra: O(Elog⁡V)O(E \\log V)O(ElogV))

### Class NP (Nondeterministic Polynomial Time)

**Class NP** contains all decision problems where, if you are given a "YES" answer along with a certificate (a proposed solution), you can **verify** if that solution is correct in polynomial time.

It does **NOT** mean "Not Polynomial". It stands for "Nondeterministic Polynomial". A nondeterministic computer (a theoretical machine that can guess perfectly or run infinite parallel branches) could solve it in polynomial time, but a normal computer might take exponential time to _find_ the solution.

- **Examples in NP:**
 - **Sudoku:** Solving an empty 9x9 grid might take a lot of brute-force guessing. But if I hand you a _completed_ grid (the certificate), you can quickly verify if it follows the rules of Sudoku in polynomial time. Therefore, Sudoku is in NP.
 - **Traveling Salesperson (Decision Version):** "Is there a tour with cost <k< k<k?" Hard to find, but if I hand you a specific tour, you just add up the edges to verify it is <k< k<k in O(n)O(n)O(n) time.

### Trace: Solving vs. Verifying (The Sudoku Example)

1. 1
 
 Step 1
 
 The Objective
 
 To truly understand why P eqNPP \\ eq NPP eqNP is the biggest question in computer science, let's trace the difference between _finding_ a solution and _verifying_ a solution using a 9x9 Sudoku puzzle.
 
2. 2
 
 Step 2
 
 Solving (Finding the Answer)
 
 Imagine an empty Sudoku grid. To solve it, an algorithm might have to try placing a number, realize it leads to a dead end 20 moves later, and **backtrack**. In the worst case, a generalized N×NN \\times NN×N Sudoku puzzle takes exponential time (O(2N)O(2^N)O(2N)) to solve. This means finding the solution is Intractable.
 
3. 3
 
 Step 3
 
 Verifying (Checking the Certificate)
 
 Now imagine your friend claims they solved the puzzle. They hand you the completed grid. This completed grid is called the **Certificate**. To verify it, you just scan the rows, columns, and 3x3 sub-grids to ensure no numbers repeat. This takes very little time—specifically, Polynomial Time O(N2)O(N^2)O(N2). Because you can _verify_ the certificate quickly, Sudoku belongs to the class **NP**.
 

### The Relationship: P⊆NPP \\subseteq NPP⊆NP

If a problem is in P, you can solve it from scratch in polynomial time. If you can solve it from scratch that fast, you can certainly _verify_ a given solution in polynomial time.

Therefore, every problem in P is also in NP. **P is a subset of NP (P⊆NPP \\subseteq NPP⊆NP).**

The greatest unsolved question in computer science is **P\=NP?P = NP?P\=NP?** Does being able to quickly _verify_ an answer mean there must exist a way to quickly _find_ that answer? Most scientists believe P≠NPP \\neq NPP\=NP, meaning some problems are inherently hard to solve but easy to check.

### Frequently Asked Questions

What happens to the world if someone proves P = NP?

Why is Sudoku NP if I can solve a puzzle in 5 minutes?

### Knowledge Check

Question 1 of 2

Q1Single choice

What is the relationship between NP and P complexity classes?

P is a subset of NP

NP is a subset of P

P and NP are equivalent

P and NP are disjoint sets

BackNext

[Previous\\ \\ PYQ Analysis & Exam Preparation — Module 3](https://coursify.hasanraiyan.me/course/design-and-analysis-of-algorithms-daa/pyq-analysis-exam-preparation-module-3) [Next\\ \\ NP-Complete and NP-Hard Problems](https://coursify.hasanraiyan.me/course/design-and-analysis-of-algorithms-daa/np-complete-and-np-hard-problems)