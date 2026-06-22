# Source: https://coursify.hasanraiyan.me/course/design-and-analysis-of-algorithms-daa/pyq-analysis-exam-preparation-module-1

# PYQ Analysis & Exam Preparation — Module 1

45 mins

A strategic analysis of 20 exam questions spanning 2022–2024. Module 1 heavily tests recurrences (Master's theorem & substitution method) and asymptotic notation theory. Know exactly what to practice.

### Learning Goals

- Identify the three guaranteed question types: Master's theorem applications, substitution method traces, and asymptotic notation explanations.
- Practice with actual MCQ questions from 2022–2024 papers.
- Understand the answer structure for the highest-mark theoretical questions: O/Ω/Θ definitions and best/worst/average case analysis.

---

### The Exam Blueprint: Module 1 PYQ Deep Analysis (2022–2024)

An analysis of **20 exam questions spanning 2022 to 2024** reveals that Module 1 is foundational and predictable. **Master's Theorem** and the **Substitution Method** are guaranteed to appear every single year for 5–7 marks each. The theoretical aspect strictly focuses on **Asymptotic Notations** and **Time/Space Complexity definitions**.

#### Complete PYQ Table (20 Questions)

| Year | Q# | Marks | Topic | Type |
| --- | --- | --- | --- | --- |
| 2023 | Q1a | **2** | Worst-case notation = Big-O | MCQ |
| 2024 | Q1a | **2** | Space complexity definition | MCQ |
| 2024 | Q1b | **2** | Asymptotic upper bound of 5n²+3n+7 | MCQ |
| 2022 | Q1b | **2** | max{f(n), g(n)} for two independent complexities | MCQ |
| 2024 | Q1c | **2** | T(n)=T(n/2)+1 → O(log n) | MCQ |
| 2023 | Q1d | **2** | Stable O(n²) sort = Insertion Sort | MCQ |
| 2023 | Q1e | **2** | T(n)=2T(n/4)+n²logn → Θ(n²logn) | MCQ |
| 2022 | Q1f | **2** | Asymptotically smallest function | MCQ |
| 2023 | Q1f | **2** | Space complexity = memory used | MCQ |
| 2022 | Q1h | **2** | Merge sort avg comparisons for 2-element lists = 8/3 | MCQ |
| 2023 | Q2a | **7** | Explain asymptotic notation (Big-O, Ω, Θ) | Theory |
| 2024 | Q2a | **7** | Best/worst/average case + linear search examples | Theory |
| 2022 | Q2a | **7** | Substitution method: f(n)=3f(n/2)+6, f(1)=1 | Numerical |
| 2023 | Q2b | **7** | Substitution method: T(n)=2T(n/2)+n | Numerical |
| 2024 | Q2b | **7** | Substitution method: T(n)=T(n-1)+n, T(1)=1 | Numerical |
| 2023 | Q3a | **5** | Master Theorem: T(n)=4T(n/2)+n³ and T(n)=T(n/2)+2ⁿ | Numerical |
| 2024 | Q3a | **7** | Master Theorem: 3 cases + apply to 3 recurrences | Numerical |
| 2023 | Q4a | **7** | Linear search trace + time/space complexity analysis | Theory+Num |
| 2022 | Q8b | **7** | Master Theorem + T(n)=2T(n^(1/2))+log n | Numerical |
| 2022 | Q9 | **14** | Short notes: Asymptotic Notations | Theory |

**Total marks tracked: 108 marks across 3 years.**

---

#### Topic Heat Map

| Topic | 2022 | 2023 | 2024 | Total Marks |
| --- | --- | --- | --- | --- |
| **Asymptotic Notation (O/Ω/Θ theory)** | 9M ✅ | 9M ✅ | 7M ✅ | **25M** |
| **Substitution Method** | 7M ✅ | 7M ✅ | 7M ✅ | **21M** |
| **Master's Theorem** | 7M ✅ | 5M ✅ | 7M ✅ | **19M** |
| **MCQ — Complexity Analysis** | 4M ✅ | 6M ✅ | 6M ✅ | **16M** |

---

#### The 3 Guaranteed Question Types

> **1\. 🔴 Substitution Method Recurrence (7M) — appeared in ALL 3 years** Always a different form. You must show the expansion steps clearly, generalize to the kkk\-th step, and substitute the base case. _Examples: 3f(n/2)+63f(n/2)+63f(n/2)+6, 2T(n/2)+n2T(n/2)+n2T(n/2)+n, T(n−1)+nT(n-1)+nT(n−1)+n._

> **2\. 🔴 Master's Theorem Application (5–7M) — appeared in ALL 3 years** You must state the values of aaa, bbb, and f(n)f(n)f(n), calculate nlog⁡ban^{\\log\_b a}nlogb​a, and explicitly state which Case applies. Watch out for equations where the theorem **fails** (like T(n)\=2T(n/2)+n/log⁡nT(n) = 2T(n/2) + n/\\log nT(n)\=2T(n/2)+n/logn).

> **3\. 🟠 Asymptotic Notation Theory (7M) — appeared in ALL 3 years** Either "explain O/Ω/Θ" or "differentiate best/worst/average cases." Always include graphs and a standard example (like Linear Search) in your answers.

### Solved Numericals: The Exam-Critical Calculations

---

#### Numerical 1: Substitution Method

> _"T(n) = T(n−1) + n, with T(1) = 1. Solve using substitution method."_

**Step 1: Expand the recurrence** T(n)\=T(n−1)+nT(n) = T(n-1) + nT(n)\=T(n−1)+n T(n−1)\=T(n−2)+(n−1)T(n-1) = T(n-2) + (n-1)T(n−1)\=T(n−2)+(n−1) T(n−2)\=T(n−3)+(n−2)T(n-2) = T(n-3) + (n-2)T(n−2)\=T(n−3)+(n−2)

**Step 2: Substitute back** T(n)\=\[T(n−2)+(n−1)\]+nT(n) = \[T(n-2) + (n-1)\] + nT(n)\=\[T(n−2)+(n−1)\]+n T(n)\=\[T(n−3)+(n−2)\]+(n−1)+nT(n) = \[T(n-3) + (n-2)\] + (n-1) + nT(n)\=\[T(n−3)+(n−2)\]+(n−1)+n

**Step 3: Generalize for k steps** T(n)\=T(n−k)+(n−(k−1))+⋯+(n−1)+nT(n) = T(n-k) + (n-(k-1)) + \\dots + (n-1) + nT(n)\=T(n−k)+(n−(k−1))+⋯+(n−1)+n

**Step 4: Reach the base case** We reach the base case when n−k\=1  ⟹  k\=n−1n-k = 1 \\implies k = n-1n−k\=1⟹k\=n−1. T(n)\=T(1)+2+3+⋯+(n−1)+nT(n) = T(1) + 2 + 3 + \\dots + (n-1) + nT(n)\=T(1)+2+3+⋯+(n−1)+n T(n)\=1+2+3+⋯+nT(n) = 1 + 2 + 3 + \\dots + nT(n)\=1+2+3+⋯+n

**Step 5: Solve** This is the sum of the first nnn natural numbers. T(n)\=n(n+1)2\=n22+n2T(n) = \\frac{n(n+1)}{2} = \\frac{n^2}{2} + \\frac{n}{2}T(n)\=2n(n+1)​\=2n2​+2n​ **Complexity: O(n2)O(n^2)O(n2)**

---

#### Numerical 2: Master's Theorem Cases

> _"Use Master's Theorem to solve: (i) T(n) = 2T(n/2) + n, (ii) T(n) = 3T(n/2) + n², (iii) T(n) = 2T(n/2) + n/log n. Explain which case applies."_

**(i) T(n)\=2T(n/2)+nT(n) = 2T(n/2) + nT(n)\=2T(n/2)+n**

- a\=2,b\=2,f(n)\=na=2, b=2, f(n)=na\=2,b\=2,f(n)\=n
- nlog⁡ba\=nlog⁡22\=n1\=nn^{\\log\_b a} = n^{\\log\_2 2} = n^1 = nnlogb​a\=nlog2​2\=n1\=n
- Since f(n)\=Θ(nlog⁡ba)f(n) = \\Theta(n^{\\log\_b a})f(n)\=Θ(nlogb​a), **Case 2** applies.
- Solution: T(n)\=Θ(nlog⁡n)T(n) = \\Theta(n \\log n)T(n)\=Θ(nlogn)

**(ii) T(n)\=3T(n/2)+n2T(n) = 3T(n/2) + n^2T(n)\=3T(n/2)+n2**

- a\=3,b\=2,f(n)\=n2a=3, b=2, f(n)=n^2a\=3,b\=2,f(n)\=n2
- nlog⁡ba\=nlog⁡23≈n1.58n^{\\log\_b a} = n^{\\log\_2 3} \\approx n^{1.58}nlogb​a\=nlog2​3≈n1.58
- Since f(n)\=Ω(nlog⁡ba+ϵ)f(n) = \\Omega(n^{\\log\_b a + \\epsilon})f(n)\=Ω(nlogb​a+ϵ) for ϵ≈0.4\\epsilon \\approx 0.4ϵ≈0.4, we check the regularity condition: 3(n/2)2≤cn2  ⟹  34n2≤cn23(n/2)^2 \\le c n^2 \\implies \\frac{3}{4} n^2 \\le c n^23(n/2)2≤cn2⟹43​n2≤cn2 (holds for c≥3/4c \\ge 3/4c≥3/4).
- **Case 3** applies.
- Solution: T(n)\=Θ(n2)T(n) = \\Theta(n^2)T(n)\=Θ(n2)

**(iii) T(n)\=2T(n/2)+n/log⁡nT(n) = 2T(n/2) + n/\\log nT(n)\=2T(n/2)+n/logn**

- a\=2,b\=2,f(n)\=n/log⁡na=2, b=2, f(n) = n/\\log na\=2,b\=2,f(n)\=n/logn
- nlog⁡ba\=nlog⁡22\=nn^{\\log\_b a} = n^{\\log\_2 2} = nnlogb​a\=nlog2​2\=n
- We compare f(n)\=n/log⁡nf(n) = n/\\log nf(n)\=n/logn with nnn. Here, f(n)f(n)f(n) is asymptotically smaller than nnn, but NOT polynomially smaller (the ratio is log⁡n\\log nlogn, not nϵn^\\epsilonnϵ).
- **Master's Theorem DOES NOT APPLY** (it falls into the gap between Case 1 and Case 2).

---

#### Numerical 3: The Variable Substitution Trap

> _"Find time complexity: T(n) = 2T(n^(1/2)) + log n"_

This cannot be solved directly by Master's Theorem. We must transform it. Let n\=2m  ⟹  m\=log⁡2nn = 2^m \\implies m = \\log\_2 nn\=2m⟹m\=log2​n. Substitute nnn: T(2m)\=2T(2m/2)+mT(2^m) = 2T(2^{m/2}) + mT(2m)\=2T(2m/2)+m

Now, rename the function to make it look standard: Let S(m)\=T(2m)S(m) = T(2^m)S(m)\=T(2m). S(m)\=2S(m/2)+mS(m) = 2S(m/2) + mS(m)\=2S(m/2)+m

Now apply Master's Theorem to S(m)S(m)S(m):

- a\=2,b\=2,f(m)\=ma=2, b=2, f(m)=ma\=2,b\=2,f(m)\=m
- mlog⁡22\=mm^{\\log\_2 2} = mmlog2​2\=m
- f(m)\=Θ(m)f(m) = \\Theta(m)f(m)\=Θ(m), so **Case 2** applies.
- Solution for S(m)S(m)S(m): S(m)\=Θ(mlog⁡m)S(m) = \\Theta(m \\log m)S(m)\=Θ(mlogm)

Substitute back m\=log⁡nm = \\log nm\=logn: T(n)\=Θ(log⁡n⋅log⁡(log⁡n))T(n) = \\Theta(\\log n \\cdot \\log(\\log n))T(n)\=Θ(logn⋅log(logn))

### Knowledge Check

Question 1 of 6

Q1Single choice

Which of the following notations is used to represent the worst-case time complexity of an algorithm?

O-notation

Ω-notation

Θ-notation

δ-notation

BackNext

### High-Yield Subjective Bank: Structure Your Answers

---

####Explain Asymptotic Notations (7 Marks)\*\*

**Answer structure:**

1. **Definition** (1M): Asymptotic notations are mathematical tools used to represent the time and space complexity of algorithms as input size n→∞n \\to \\inftyn→∞.
2. **Big-O (O) Notation - Upper Bound** (2M):
 - Represents the worst-case scenario.
 - f(n)\=O(g(n))f(n) = O(g(n))f(n)\=O(g(n)) if there exist constants c\>0c > 0c\>0 and n0≥0n\_0 \\ge 0n0​≥0 such that 0≤f(n)≤c⋅g(n)0 \\le f(n) \\le c \\cdot g(n)0≤f(n)≤c⋅g(n) for all n≥n0n \\ge n\_0n≥n0​.
 - _Draw a graph showing c⋅g(n)c \\cdot g(n)c⋅g(n) staying above f(n)f(n)f(n) after n0n\_0n0​._
3. **Big-Omega (Ω) Notation - Lower Bound** (2M):
 - Represents the best-case scenario.
 - f(n)\=Ω(g(n))f(n) = \\Omega(g(n))f(n)\=Ω(g(n)) if there exist constants c\>0c > 0c\>0 and n0≥0n\_0 \\ge 0n0​≥0 such that 0≤c⋅g(n)≤f(n)0 \\le c \\cdot g(n) \\le f(n)0≤c⋅g(n)≤f(n) for all n≥n0n \\ge n\_0n≥n0​.
 - _Draw a graph showing c⋅g(n)c \\cdot g(n)c⋅g(n) staying below f(n)f(n)f(n) after n0n\_0n0​._
4. **Big-Theta (Θ) Notation - Tight Bound** (2M):
 - Represents the exact bound (average case).
 - f(n)\=Θ(g(n))f(n) = \\Theta(g(n))f(n)\=Θ(g(n)) if there exist constants c1,c2\>0c\_1, c\_2 > 0c1​,c2​\>0 and n0≥0n\_0 \\ge 0n0​≥0 such that 0≤c1⋅g(n)≤f(n)≤c2⋅g(n)0 \\le c\_1 \\cdot g(n) \\le f(n) \\le c\_2 \\cdot g(n)0≤c1​⋅g(n)≤f(n)≤c2​⋅g(n) for all n≥n0n \\ge n\_0n≥n0​.
 - _Draw a graph showing f(n)f(n)f(n) sandwiched between c1g(n)c\_1g(n)c1​g(n) and c2g(n)c\_2g(n)c2​g(n)._

---

#### Differentiate Best, Worst, Average Case + Why Worst is Preferred (7 Marks)\*\*

**Answer structure:**

1. **Best Case** (1.5M): Minimum time required for program execution. For Linear Search on array AAA, the target is at A\[0\]A\[0\]A\[0\]. Complexity: Ω(1)\\Omega(1)Ω(1). Not very useful for practical guarantees.
2. **Worst Case** (1.5M): Maximum time required. Target is at the very end or not in the array at all. The algorithm must check all nnn elements. Complexity: O(n)O(n)O(n).
3. **Average Case** (1.5M): Expected time over all possible inputs. For Linear Search, target is somewhere in the middle (expected checks = n/2n/2n/2). Complexity: Θ(n)\\Theta(n)Θ(n).
4. **Why Worst-Case is Preferred** (2.5M):
 - It provides an absolute **guarantee** — the algorithm will _never_ take longer than this.
 - Crucial for real-time systems (e.g., medical devices, avionics) where missing a deadline causes failure.
 - Average-case is often mathematically difficult to compute and depends on assumptions about input probability distributions that might not hold true in reality.

[Master's Theorem - Visual Guide\\ \\ web](https://www.geeksforgeeks.org/advanced-master-theorem-for-divide-and-conquer-recurrences/)

[Previous\\ \\ Recurrence Relations and Recursive Algorithm Analysis](https://coursify.hasanraiyan.me/course/design-and-analysis-of-algorithms-daa/recurrence-relations-and-recursive-algorithm-analysis) [Next\\ \\ Brute-Force & Greedy Strategies](https://coursify.hasanraiyan.me/course/design-and-analysis-of-algorithms-daa/brute-force-greedy-strategies)