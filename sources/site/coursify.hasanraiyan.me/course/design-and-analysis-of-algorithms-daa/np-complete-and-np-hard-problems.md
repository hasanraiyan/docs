# Source: https://coursify.hasanraiyan.me/course/design-and-analysis-of-algorithms-daa/np-complete-and-np-hard-problems

# NP-Complete and NP-Hard Problems

35 mins

Learn the exact definitions of NP-Hard and NP-Complete classes. Understand how they relate to P and NP through Euler diagrams, answering the most frequently asked theoretical exam questions.

### Learning Goals

- Define the NP-Hard complexity class.
- Define the NP-Complete complexity class and its two strict requirements.
- Draw and explain the relationship between P, NP, NP-Complete, and NP-Hard.

---

### Defining NP-Hard and NP-Complete

_(Directly answers the 7-mark subjective questions from 2022 Q7b, 2023 Q7b, and 2024 Q8a)_

While **P** represents problems that are easy to solve, and **NP** represents problems that are easy to verify, we need a way to classify the absolute hardest problems in computer science.

#### Class NP-Hard (NPH)

A problem HHH is considered **NP-Hard** if _every_ problem in NP can be mathematically reduced to HHH in polynomial time. In simple terms: An NP-Hard problem is at least as hard as the hardest problems in NP. **Crucial Note:** An NP-Hard problem does **not** have to be in NP. It might not even be verifiable in polynomial time, and it might be entirely undecidable (like the Halting Problem).

#### Class NP-Complete (NPC)

A problem is **NP-Complete** if it satisfies two strict requirements:

1. It is in **NP** (Its solutions can be verified in polynomial time).
2. It is **NP-Hard** (Every problem in NP reduces to it).

You can think of NP-Complete problems as the "hardest possible problems within the NP boundary." If anyone ever finds a fast, polynomial-time algorithm to solve just _one_ NP-Complete problem, they will automatically have found a fast algorithm for every single problem in NP (proving P\=NPP = NPP\=NP). Examples include Boolean Satisfiability (SAT), Vertex Cover, and the Traveling Salesperson Problem.

### The Relationship Diagram (Assuming P≠NPP \\neq NPP\=NP)

To secure full marks on the exam, you must draw the Euler diagram that visually maps the relationship between these four classes.

**Breaking down the relationships:**

1. **P⊆NPP \\subseteq NPP⊆NP:** Everything inside P is also inside NP.
2. **NPC\=NP∩NPHNPC = NP \\cap NPHNPC\=NP∩NPH:** The NP-Complete boundary is the exact overlap where a problem is both inside NP and inside NP-Hard.
3. **NP-Hard extends beyond NP:** Some NP-Hard problems are so difficult that you can't even verify their solutions in polynomial time, placing them outside the NP bubble.

### Knowledge Check

Question 1 of 2

Q1Single choice

Which one is true of the following?

all NP hard problems are NP complete

all NP complete problems are NP hard

some NP complete problems are NP hard

None of these

BackNext

[Previous\\ \\ Computability & Complexity Classes: P and NP](https://coursify.hasanraiyan.me/course/design-and-analysis-of-algorithms-daa/computability-complexity-classes-p-and-np) [Next\\ \\ Cook's Theorem & Reduction Techniques](https://coursify.hasanraiyan.me/course/design-and-analysis-of-algorithms-daa/cooks-theorem-reduction-techniques)