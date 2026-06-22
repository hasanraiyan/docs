# Source: https://coursify.hasanraiyan.me/course/compiler-design-cd/finite-automata-nfa-and-dfa

# Finite Automata — NFA and DFA

45 mins

The mathematical engine behind every lexer. Learn to construct NFAs directly from regular expressions, then apply the subset construction algorithm to convert them to efficient, deterministic DFAs ready for implementation.

### Learning Goals

- Formally define a Non-Deterministic Finite Automaton (NFA) and a Deterministic Finite Automaton (DFA).
- Construct an NFA directly from a regular expression using Thompson's construction rules.
- Apply the Subset Construction algorithm to convert an NFA to an equivalent DFA.
- Minimize a DFA by identifying and merging indistinguishable states using the table-filling algorithm.
- Trace a DFA on a given input string to determine if it is accepted or rejected.

---

### Finite Automata — The Engine of Every Lexer

A regular expression _describes_ a token pattern. A **Finite Automaton** _implements_ it — it is the actual machine that reads a character stream and decides whether the input belongs to that pattern.

There are two kinds:

| Feature | NFA (Non-Deterministic) | DFA (Deterministic) |
| --- | --- | --- |
| **Transitions** | A symbol can lead to **multiple states** | A symbol leads to **exactly one state** |
| **ε-transitions** | ✅ Allowed (move without consuming input) | ❌ Not allowed |
| **State count** | Fewer states, compact | Can be up to 2n2^n2n states (from an nnn\-state NFA) |
| **Ease of construction** | Easy — built mechanically from regex | Hard to build directly |
| **Simulation speed** | Slower — must track a _set_ of states | Fast — O(n)O(n)O(n), one state at a time |
| **Use in compilers** | Intermediate step only | The actual running lexer |

Both are formally defined as a **5-tuple**: M\=(Q,Σ,δ,q0,F)M = (Q, \\Sigma, \\delta, q\_0, F)M\=(Q,Σ,δ,q0​,F)

- QQQ — finite set of states
- Σ\\SigmaΣ — input alphabet (the set of valid characters)
- δ\\deltaδ — transition function (Q×Σ→QQ \\times \\Sigma \\to QQ×Σ→Q for DFA; Q×(Σ∪{ε})→2QQ \\times (\\Sigma \\cup \\{\\varepsilon\\}) \\to 2^QQ×(Σ∪{ε})→2Q for NFA)
- q0∈Qq\_0 \\in Qq0​∈Q — start state
- F⊆QF \\subseteq QF⊆Q — set of accepting (final) states

**The compilation pipeline for a lexer:** Regex→Thompson’sNFA→Subset ConstructionDFA→MinimizationMinimal DFA\\text{Regex} \\xrightarrow{\\text{Thompson's}} \\text{NFA} \\xrightarrow{\\text{Subset Construction}} \\text{DFA} \\xrightarrow{\\text{Minimization}} \\text{Minimal DFA}RegexThompson’s​NFASubset Construction​DFAMinimization​Minimal DFA

### Thompson's Construction — The 4 Rules

Thompson's Construction is a mechanical algorithm that converts any regular expression into an NFA by recursively applying four rules. Each rule produces a small NFA fragment with exactly **one start state** and **one accepting state**.

**Rule 1 — Single Character `a`:**

**Rule 2 — Union `r|s`** (given NFAs for `r` and `s`):

**Rule 3 — Kleene Star `r*`** (given NFA for `r`):

**Rule 4 — Concatenation `rs`** (given NFAs for `r` and `s`): The accepting state of `r`'s NFA is merged with the start state of `s`'s NFA via an ε-transition.

Applying all four rules to `(a|b)*abb` produces the NFA below (Dragon Book states 0–10):

### Exam Problem: Design a DFA from Scratch

1. 1
 
 Step 1
 
 The Problem
 
 **\[PYQ 2024\] Design a finite automaton that accepts all binary strings that do not contain the substring '101'.**
 
 When asked to design a DFA that _does not_ contain a substring, it's often easier to first design the DFA that _does_ contain it, and then invert the accepting states.
 
2. 2
 
 Step 2
 
 Step 1: Design DFA for 'contains 101'
 
 Let's build a DFA that accepts strings containing '101'. We need 4 states to track our progress:
 
 - **A (start):** seen nothing
 - **B:** seen '1'
 - **C:** seen '10'
 - **D (accept):** seen '101'
 
 Notice that state D is a trap state — once you see '101', you stay in D forever and accept.
 
3. 3
 
 Step 3
 
 Step 2: Invert the Accepting States
 
 To accept strings that _do not_ contain '101', we take the exact same DFA and flip the accepting status of every state.
 
 - Non-accepting states (A, B, C) become accepting.
 - Accepting state (D) becomes non-accepting (a dead state).
 
 This is our final answer. The machine stays in the green states as long as it hasn't seen '101'. If it ever sees '101', it falls into the dead state D and rejects.
 

### Trace: Subset Construction (NFA → DFA) for (a|b)\*abb

1. 1
 
 Step 1
 
 Define ε-closure and move
 
 Before we start, two key operations:
 
 **ε-closure(T):** The set of all NFA states reachable from any state in set T using **only ε-transitions** (including the states in T themselves).
 
 **move(T, a):** The set of all NFA states reachable from any state in set T on **input symbol `a`** (no ε-transitions).
 
 The algorithm maintains a worklist of **unmarked DFA states**. Each DFA state is a _set_ of NFA states. We start with ε-closure of the NFA's start state.
 
2. 2
 
 Step 2
 
 DFA Start State A = ε-closure({0})
 
 From state 0, we can reach via ε: 0 → 1 → 2 and 1 → 4 and 0 → 7.
 
 **ε-closure({0}) = {0, 1, 2, 4, 7} = State A** (start state)
 
 State A is unmarked. We now compute its transitions on each input symbol (a, b).
 
3. 3
 
 Step 3
 
 Transitions from A
 
 **move(A, a):** Which NFA states are reached from {0,1,2,4,7} on 'a'?
 
 - State 2 -a→ 3 ✓
 - State 7 -a→ 8 ✓ So move(A, a) = {3, 8}.
 
 **ε-closure({3,8}):** From 3: 3→6→1→2, 6→7, 1→4. From 8: nothing. Result = {1, 2, 3, 4, 6, 7, 8} = **State B**
 
 **move(A, b):** From {0,1,2,4,7} on 'b':
 
 - State 4 -b→ 5 ✓ move(A, b) = {5}.
 
 **ε-closure({5}):** 5→6→1→2, 6→7, 1→4. Result = {1, 2, 4, 5, 6, 7} = **State C**
 
 Mark A. Add B and C to worklist.
 
4. 4
 
 Step 4
 
 Transitions from B and C
 
 **From State B = {1,2,3,4,6,7,8}:**
 
 move(B, a) = {3, 8} → ε-closure = {1,2,3,4,6,7,8} = **B** (loops to itself!) move(B, b) = {5, 9} → ε-closure({5,9}) = {1,2,4,5,6,7,9} = **State D** (new)
 
 Mark B.
 
 **From State C = {1,2,4,5,6,7}:**
 
 move(C, a) = {3, 8} → ε-closure = {1,2,3,4,6,7,8} = **B** (already exists) move(C, b) = {5} → ε-closure = {1,2,4,5,6,7} = **C** (loops to itself!)
 
 Mark C. Add D to worklist.
 
5. 5
 
 Step 5
 
 Transitions from D — Final State Discovered
 
 **From State D = {1,2,4,5,6,7,9}:**
 
 move(D, a) = {3, 8} → ε-closure = {1,2,3,4,6,7,8} = **B** move(D, b) = {5, 10} → ε-closure({5,10}) = {1,2,4,5,6,7,10} = **State E** (new)
 
 State 10 is the NFA's accepting state, so **any DFA state containing state 10 is an accepting state**. Therefore, **State E is the DFA's accepting state**.
 
 From E = {1,2,4,5,6,7,10}: move(E, a) = {3,8} → **B** move(E, b) = {5} → **C**
 
 Mark D and E. Worklist is now empty — construction complete!
 
6. 6
 
 Step 6
 
 The Complete DFA Transition Table & Diagram
 
 All 5 DFA states with their transitions:
 
 | DFA State | NFA States | on 'a' | on 'b' | Accepting? |
 | --- | --- | --- | --- | --- |
 | **A** (start) | {0,1,2,4,7} | B | C | No |
 | **B** | {1,2,3,4,6,7,8} | B | D | No |
 | **C** | {1,2,4,5,6,7} | B | C | No |
 | **D** | {1,2,4,5,6,7,9} | B | E | No |
 | **E**\* | {1,2,4,5,6,7,10} | B | C | **Yes** |
 
 This DFA recognizes all strings over {a,b} that **end in `abb`**.
 

### Trace: DFA Minimization (Table-Filling Algorithm)

1. 1
 
 Step 1
 
 Initial Partition
 
 The table-filling algorithm starts by partitioning states into two groups:
 
 - **Accepting states:** {E}
 - **Non-accepting states:** {A, B, C, D}
 
 We draw a triangular table for all pairs of distinct states. We will mark a pair **(p, q) as distinguishable** if there exists any input string that causes one to accept and the other to reject.
 
 **Initial marking:** Mark ALL pairs where one state is accepting and the other is not.
 
 Marked pairs (✗ = distinguishable): **(A,E), (B,E), (C,E), (D,E)**
 
 Unmarked pairs (? = unknown): (A,B), (A,C), (A,D), (B,C), (B,D), (C,D)
 
2. 2
 
 Step 2
 
 Iteration — Propagate Distinguishability
 
 For each unmarked pair (p,q), check: for any input symbol `x`, if the pair (δ(p,x), δ(q,x)) is already marked, then mark (p,q) too.
 
 **Check (C,D):**
 
 - On 'a': C→B, D→B → same state, skip.
 - On 'b': C→C, D→E → pair **(C,E) is marked!** → **Mark (C,D) ✗**
 
 **Check (A,D):**
 
 - On 'b': A→C, D→E → pair **(C,E) is marked!** → **Mark (A,D) ✗**
 
 **Check (B,D):**
 
 - On 'b': B→D, D→E → pair **(D,E) is marked!** → **Mark (B,D) ✗**
 
 **Check (B,C):**
 
 - On 'b': B→D, C→C → pair **(C,D) is now marked!** → **Mark (B,C) ✗**
 
 **Check (A,B):**
 
 - On 'b': A→C, B→D → pair **(C,D) is now marked!** → **Mark (A,B) ✗**
 
3. 3
 
 Step 3
 
 Check (A,C) — The Indistinguishable Pair
 
 **Check (A,C):**
 
 - On 'a': A→B, C→B → _same state_. ✓
 - On 'b': A→C, C→C → _same state_. ✓
 
 No further iteration can mark (A,C). Therefore, **states A and C are indistinguishable** — no input string can tell them apart!
 
 **Result:** States A and C can be **merged** into a single state \[AC\].
 
4. 4
 
 Step 4
 
 The Minimized DFA
 
 Merging A and C into state \[AC\] gives us a **4-state minimized DFA:**
 
 | State | on 'a' | on 'b' | Role |
 | --- | --- | --- | --- |
 | **\[AC\]** | B | \[AC\] | Start state |
 | **B** | B | D | — |
 | **D** | B | E | — |
 | **E**\* | B | \[AC\] | Accepting |
 
 The minimized DFA has **4 states** — one fewer than the original 5-state DFA — and is provably the smallest possible DFA for the language `(a|b)*abb`.
 

NFA (11 states)

DFA (5 states)Minimized DFA (4 states)

**From Thompson's Construction on `(a|b)*abb`**

- **States:** 0–10 (11 states)
- **ε-transitions:** 8 ε-transitions
- **Start:** State 0
- **Accepting:** State 10

**Advantages:** Compact, mechanical to construct from regex. **Disadvantages:** Cannot be directly simulated in O(n) — requires tracking a set of active states.

This form is never used directly in a compiled lexer. It is always converted to a DFA first.

#### Always: ε-closure AFTER move, Never Before

The single most common mistake in subset construction exams is applying ε-closure in the wrong order.

**Correct procedure:** `ε-closure( move(T, a) )`

1. First compute **move(T, a)** — find all states reachable on symbol 'a' (no ε-transitions)
2. Then compute **ε-closure(...)** — expand with all ε-reachable states from the result

**Also remember:** ε-closure always includes the state itself. So ε-closure({q}) always contains q.

more...

#### Dead States — Always Complete Your DFA

If a DFA state has no defined transition on some input symbol, a correct implementation requires a **dead state** (also called a _trap state_ or _error state_): a non-accepting state that transitions to itself on all inputs.

For example, if the DFA for `ab` is in state after seeing 'a', and it receives 'a' again — there is no valid transition. Instead of crashing, the lexer goes to the dead state and stays there, correctly rejecting the input.

**In exam questions:** If your transition table has blank cells, fill them with a dead state. Graders will deduct marks for an incomplete transition function since a DFA is formally required to have a total transition function.

more...

### Common Questions

Why not build the DFA directly from the regex, skipping the NFA?

Can every NFA be converted to an equivalent DFA?

Can the subset construction produce 2n2^n2n states?

### Knowledge Check

Question 1 of 6

Q1Single choice

How many transitions can an NFA have from a single state on a single input symbol?

Exactly one

At most one

Zero, one, or more

Always more than one

BackNext

[Compilers: Principles, Techniques & Tools (Dragon Book) — Chapter 3.6–3.9\\ \\ web](https://www.pearson.com/en-us/subject-catalog/p/compilers-principles-techniques-and-tools/P200000003268)

[Previous\\ \\ Lexical Analysis and Regular Languages](https://coursify.hasanraiyan.me/course/compiler-design-cd/lexical-analysis-and-regular-languages) [Next\\ \\ Scanner Generators — Lex and Flex](https://coursify.hasanraiyan.me/course/compiler-design-cd/scanner-generators-lex-and-flex)