# Source: https://coursify.hasanraiyan.me/course/design-and-analysis-of-algorithms-daa/complexity-classes-beyond-np-pspace

# Complexity Classes Beyond NP: PSPACE

20 mins

Explore the theoretical bounds of computer science by looking past polynomial time and into the realms of polynomial space (PSPACE) and exponential time (EXPTIME).

### Learning Goals

- Define the PSPACE complexity class.
- Understand the relationship between P, NP, PSPACE, and EXPTIME.
- Identify what makes a problem PSPACE-Complete.

---

### Moving Beyond Time: Space Complexity

Until now, we have classified problems based on how much **Time** they take to compute (P = Polynomial Time, NP = Nondeterministic Polynomial Time). But what if we classify problems by how much **Memory (Space)** they consume?

#### Class PSPACE

**PSPACE** is the set of all decision problems that can be solved by a deterministic computer using a polynomial amount of memory/space O(nk)O(n^k)O(nk), regardless of how much time it takes.

Because an algorithm can reuse the exact same memory blocks over and over for billions of years, space is vastly more powerful than time.

#### The Complexity Hierarchy

If you have polynomial time (P or NP), you can only possibly use polynomial space (you don't have enough time to write to more memory than that!). Therefore, everything in P and NP fits inside PSPACE.

Furthermore, if you have Exponential Time (**EXPTIME**), you have enough time to explore every single configuration of polynomial space.

This gives us the grand hierarchy of computational complexity:

_(Mathematical notation: P⊆NP⊆PSPACE⊆EXPTIMEP \\subseteq NP \\subseteq PSPACE \\subseteq EXPTIMEP⊆NP⊆PSPACE⊆EXPTIME)_

### PSPACE-Complete

Just like NP has NP-Complete (the hardest problems in NP), PSPACE has **PSPACE-Complete** (the absolute hardest problems that can be solved using polynomial memory).

To be PSPACE-Complete:

1. The problem must be in PSPACE.
2. Every other problem in PSPACE must be reducible to it in polynomial time.

**Classic Example:**

- **QBF (Quantified Boolean Formulas):** This is just like the SAT problem, but instead of just asking "Is there a truth assignment?", it allows "For All" (∀\\forall∀) and "There Exists" (∃\\exists∃) quantifiers.
- Example: ∀x∃y(x∨y)∧(xˉ∨yˉ)\\forall x \\exists y (x \\lor y) \\land (\\bar{x} \\lor \\bar{y})∀x∃y(x∨y)∧(xˉ∨yˉ​).
- Solving this requires tracking a massive, deep decision tree, which takes exponential time, but because we evaluate it depth-first, we only need to store the current path in memory, requiring only polynomial space!

Many two-player perfect-information board games (like generalized Chess, Checkers, and Go on an N×NN \\times NN×N board) are PSPACE-Hard or EXPTIME-Complete because calculating the perfect winning strategy requires evaluating deep, branching trees of possible future moves.

### Knowledge Check

Question 1 of 2

Q1Single choice

What does the complexity class PSPACE represent?

Problems solvable using a polynomial amount of time.

Problems solvable using a polynomial amount of memory (space), regardless of time.

Problems that require exponential space.

Problems that cannot be solved by a deterministic computer.

BackNext

[Previous\\ \\ Randomized Algorithms](https://coursify.hasanraiyan.me/course/design-and-analysis-of-algorithms-daa/randomized-algorithms) [Next\\ \\ PYQ Analysis & Exam Preparation — Module 5](https://coursify.hasanraiyan.me/course/design-and-analysis-of-algorithms-daa/pyq-analysis-exam-preparation-module-5)