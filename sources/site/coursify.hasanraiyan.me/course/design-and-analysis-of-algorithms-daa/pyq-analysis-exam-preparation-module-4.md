# Source: https://coursify.hasanraiyan.me/course/design-and-analysis-of-algorithms-daa/pyq-analysis-exam-preparation-module-4

# PYQ Analysis & Exam Preparation — Module 4

30 mins

A strategic analysis of 8 exam questions spanning 2022–2024. Module 4 is the most theoretical module, focusing entirely on computational complexity classes and polynomial-time reductions.

### Learning Goals

- Identify the guaranteed theory question: Defining P, NP, NP-Complete, and NP-Hard with their relationship diagram.
- Understand Cook's Theorem and its foundational importance in complexity theory.
- Master the logic of polynomial-time reductions and practice the 3-SAT to Vertex Cover reduction.

---

### The Exam Blueprint: Module 4 PYQ Deep Analysis (2022–2024)

An analysis of **8 exam questions spanning 2022 to 2024** reveals that Module 4 is short but incredibly predictable. It has the tightest scope of any module. The question asking to **define P, NP, NP-Complete, and NP-Hard** has appeared in every single paper.

#### Complete PYQ Table (8 Questions)

| Year | Q# | Marks | Topic | Type |
| --- | --- | --- | --- | --- |
| 2022 | Q1e | **2** | All NP-complete problems are NP-hard | MCQ |
| 2022 | Q1i | **2** | Polynomial-time reduction properties | MCQ |
| 2023 | Q1j | **2** | P is a subset of NP | MCQ |
| 2024 | Q1i | **2** | Primary technique to prove NP-complete | MCQ |
| 2022 | Q7b | **7** | Define P, NP, NP-complete, NP-hard + Relation | Theory |
| 2023 | Q7b | **7** | Define P, NP, NP-complete, NP-hard + Relation | Theory |
| 2024 | Q8a | **7** | Complexity classes + Cook's Theorem | Theory |
| 2024 | Q8b | **7** | Polynomial-time reduction + 3-SAT to Vertex Cover | Theory |

**Total marks tracked: 38 marks across 3 years.**

---

#### Topic Heat Map

| Topic | 2022 | 2023 | 2024 | Total Marks |
| --- | --- | --- | --- | --- |
| **Complexity Classes Definitions & Relations** | 7M ✅ | 7M ✅ | 7M ✅ | **21M** |
| **Cook's Theorem & Reductions** | 2M ✅ | — | 14M ✅ | **16M** |
| **MCQs** | 4M ✅ | 2M ✅ | 2M ✅ | **8M** |

_(Note: Some topics overlap with MCQs)._

---

#### The 2 Guaranteed Question Types

> **1\. 🔴 The "Big Four" Complexity Classes (7M)** Appeared in ALL 3 years. You must formally define P, NP, NP-Complete, and NP-Hard, and draw the standard Euler diagram showing their assumed relationship (assuming P≠NPP \\neq NPP\=NP).

> **2\. 🟠 Reductions and Cook's Theorem (7M)** Started appearing heavily in 2024. You must be able to state Cook's Theorem ("SAT is NP-Complete") and explain the mechanism of polynomial-time reductions.

### The Critical Proofs & Reductions

---

#### Concept 1: Cook's Theorem

**Statement**: _The Boolean Satisfiability Problem (SAT) is NP-Complete._

**Why is it foundational?** Before Cook's Theorem (proven by Stephen Cook in 1971), to prove a problem was NP-Complete, one would theoretically have to prove that _every single problem_ in NP could be reduced to it. Cook proved that any non-deterministic Turing machine computation can be encoded as a Boolean formula. By proving that SAT is NP-Complete, Cook provided the **first** NP-Complete problem. From then on, to prove a new problem XXX is NP-Complete, we only need to reduce SAT (or another known NP-Complete problem) to XXX. It kickstarted the entire field of computational complexity.

---

#### Concept 2: The Logic of Polynomial-Time Reductions

**What is it?** A polynomial-time reduction from Problem A to Problem B (written as A≤pBA \\le\_p BA≤p​B) is an algorithm that transforms any instance of A into an instance of B in polynomial time, such that the answer to A is "YES" if and only if the answer to B is "YES".

**How is it used to prove NP-Completeness?** To prove that a new problem YYY is NP-Complete:

1. Prove that Y∈NPY \\in NPY∈NP (a given solution can be verified in polynomial time).
2. Choose a known NP-Complete problem XXX.
3. Prove that X≤pYX \\le\_p YX≤p​Y (reduce XXX to YYY in polynomial time). Because XXX is NP-Complete, all problems in NP reduce to XXX. If XXX reduces to YYY, by transitivity, all problems in NP reduce to YYY, making YYY NP-Hard. Since Y∈NPY \\in NPY∈NP and YYY is NP-Hard, YYY is NP-Complete.

---

#### Trace: Reducing 3-SAT to Vertex Cover

To reduce a 3-SAT formula ϕ\\phiϕ to a Vertex Cover graph GGG:

1. **Variables**: For each variable xix\_ixi​, create two connected vertices: xix\_ixi​ and ¬xi\\neg x\_i¬xi​. (This forces the vertex cover to pick exactly one truth value).
2. **Clauses**: For each clause (e.g., x1∨¬x2∨x3x\_1 \\lor \\neg x\_2 \\lor x\_3x1​∨¬x2​∨x3​), create a triangle of 3 connected vertices. (This forces the vertex cover to pick at least two of these vertices).
3. **Connections**: Connect the vertices in the clause triangles to their corresponding variable vertices in the variable gadgets.
4. **Conclusion**: ϕ\\phiϕ is satisfiable if and only if GGG has a vertex cover of size V+2CV + 2CV+2C (where VVV is the number of variables and CCC is the number of clauses). Since building this graph takes polynomial time, 3-SAT ≤p\\le\_p≤p​ Vertex Cover.

### Knowledge Check

Question 1 of 4

Q1Single choice

Which one is true of the following?

All NP hard problems are NP complete

All NP complete problems are NP hard

Some NP complete problems are NP hard

None of these

BackNext

### High-Yield Subjective Bank: Structure Your Answers

---

####Define P, NP, NP-Complete, and NP-Hard. What is the relation between them? (7 Marks)\*\*

**Answer structure:**

1. **P Class (Polynomial Time)** (1.5M):
 
 - The set of decision problems that can be **solved** by a deterministic Turing machine in polynomial time O(nk)O(n^k)O(nk).
 - These are considered "tractable" or easy problems.
 - _Examples: Sorting, Shortest Path, MST._
2. **NP Class (Non-deterministic Polynomial Time)** (1.5M):
 
 - The set of decision problems whose proposed solutions can be **verified** by a deterministic Turing machine in polynomial time.
 - Alternatively, problems that can be solved by a non-deterministic Turing machine in polynomial time.
 - _Note: P is a subset of NP._
3. **NP-Hard Class** (1.5M):
 
 - A problem XXX is NP-Hard if **every** problem Y∈NPY \\in NPY∈NP can be reduced to XXX in polynomial time (Y≤pXY \\le\_p XY≤p​X).
 - These are at least as hard as the hardest problems in NP. They do not have to be in NP themselves (e.g., they might not be decision problems).
 - _Example: Halting Problem, TSP Optimization._
4. **NP-Complete Class (NPC)** (1.5M):
 
 - A problem is NP-Complete if it satisfies two conditions:
 1. It is in NP.
 2. It is NP-Hard.
 - These are the hardest problems inside NP. If any NP-Complete problem is solved in polynomial time, then P\=NPP = NPP\=NP.
 - _Examples: 3-SAT, Vertex Cover, Graph Coloring._
5. **Relationship (Euler Diagram)** (1M):
 
 - _Draw the standard diagram showing the relationship assuming P≠NPP \\neq NPP\=NP:_
 - A large circle for NP.
 - Inside NP, a smaller circle for P at the bottom.
 - Another circle for NP-Complete at the top of NP, intersecting the boundary.
 - A region outside NP extending upwards representing NP-Hard, where the intersection of NP and NP-Hard forms the NP-Complete region.

[P vs NP and the Computational Complexity Zoo\\ \\ web](https://www.youtube.com/watch?v=YX40hbAHx3s)

[Previous\\ \\ Cook's Theorem & Reduction Techniques](https://coursify.hasanraiyan.me/course/design-and-analysis-of-algorithms-daa/cooks-theorem-reduction-techniques) [Next\\ \\ Approximation Algorithms](https://coursify.hasanraiyan.me/course/design-and-analysis-of-algorithms-daa/approximation-algorithms)