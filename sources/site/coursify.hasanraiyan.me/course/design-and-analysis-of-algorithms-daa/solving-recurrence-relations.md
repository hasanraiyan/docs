# Source: https://coursify.hasanraiyan.me/course/design-and-analysis-of-algorithms-daa/solving-recurrence-relations

# Solving Recurrence Relations

40 mins

Master the mathematical techniques to calculate the time complexity of recursive algorithms. This section covers the Substitution Method, Recursion Tree Method, and the highly-tested Master's Theorem.

### Learning Goals

- Understand what a recurrence relation is and why it's necessary for recursive algorithms.
- Memorize the three cases of the Master's Theorem and identify when it fails.
- Trace mathematical solutions using the Substitution Method for linear recurrences.
- Visualize how recursive function calls split work using the Recursion Tree Method.

---

### The Basics of Recurrence

While calculating the time complexity of a standard `for` loop is straightforward, analyzing a **recursive** algorithm (an algorithm that calls itself, like Merge Sort or Binary Search) is mathematically complex. We cannot simply count loops. Instead, we must define the running time as a mathematical equation called a **Recurrence Relation**.

A recurrence relation defines a sequence based on its previous terms. For example, the time T(n)T(n)T(n) to sort an array of size nnn might be defined as the time to sort two halves T(n/2)T(n/2)T(n/2) plus the time to merge them O(n)O(n)O(n). T(n)\=2T(n/2)+O(n)T(n) = 2T(n/2) + O(n)T(n)\=2T(n/2)+O(n)

There are three primary methods to solve these recurrences and find the asymptotic bound:

1. **The Substitution Method:** Expanding the equation mathematically to guess and prove the bound.
2. **The Recursion Tree Method:** Visualizing the recursive calls as a tree and summing the work done at each level.
3. **The Master's Theorem:** A direct, formulaic shortcut for solving divide-and-conquer recurrences.

---

### The Master's Theorem (The Shortcut)

The Master's Theorem provides a "cookbook" method for solving recurrences of the specific form: **T(n)\=aT(n/b)+f(n)T(n) = aT(n/b) + f(n)T(n)\=aT(n/b)+f(n)**

Where:

- a≥1a \\ge 1a≥1: The number of recursive subproblems.
- b\>1b > 1b\>1: The factor by which the input size is divided.
- f(n)f(n)f(n): The cost of the work done outside the recursive calls (like merging or partitioning).

To solve, you always calculate the **critical exponent**: nlog⁡ban^{\\log\_b a}nlogb​a, and compare it to f(n)f(n)f(n).

**The 3 Cases:**

1. **Case 1 (Heavy Leaves):** If f(n)\=O(nlog⁡ba−ϵ)f(n) = O(n^{\\log\_b a - \\epsilon})f(n)\=O(nlogb​a−ϵ) for some constant ϵ\>0\\epsilon > 0ϵ\>0. Meaning: The work at the leaves dominates. **Solution:** T(n)\=Θ(nlog⁡ba)T(n) = \\Theta(n^{\\log\_b a})T(n)\=Θ(nlogb​a)
2. **Case 2 (Balanced Work):** If f(n)\=Θ(nlog⁡ba)f(n) = \\Theta(n^{\\log\_b a})f(n)\=Θ(nlogb​a). Meaning: The work is evenly distributed across the tree levels. **Solution:** T(n)\=Θ(nlog⁡balog⁡n)T(n) = \\Theta(n^{\\log\_b a} \\log n)T(n)\=Θ(nlogb​alogn)
3. **Case 3 (Heavy Root):** If f(n)\=Ω(nlog⁡ba+ϵ)f(n) = \\Omega(n^{\\log\_b a + \\epsilon})f(n)\=Ω(nlogb​a+ϵ) for some constant ϵ\>0\\epsilon > 0ϵ\>0. Meaning: The work at the root (the f(n)f(n)f(n) term) completely dominates. _Regularity Condition:_ You must also prove af(n/b)≤cf(n)a f(n/b) \\le c f(n)af(n/b)≤cf(n) for c<1c < 1c<1. **Solution:** T(n)\=Θ(f(n))T(n) = \\Theta(f(n))T(n)\=Θ(f(n))

### Trace: Master's Theorem Application

1. 1
 
 Step 1
 
 Identify the variables
 
 Given the recurrence T(n)\=3T(n/2)+n2T(n) = 3T(n/2) + n^2T(n)\=3T(n/2)+n2. We identify the constants: a\=3a = 3a\=3, b\=2b = 2b\=2, and the function f(n)\=n2f(n) = n^2f(n)\=n2.
 
2. 2
 
 Step 2
 
 Calculate the Critical Exponent
 
 We calculate nlog⁡ban^{\\log\_b a}nlogb​a, which is nlog⁡23n^{\\log\_2 3}nlog2​3. Since log⁡23≈1.58\\log\_2 3 \\approx 1.58log2​3≈1.58, our critical exponent is n1.58n^{1.58}n1.58.
 
3. 3
 
 Step 3
 
 Compare and Determine the Case
 
 We compare f(n)\=n2f(n) = n^2f(n)\=n2 with our critical exponent n1.58n^{1.58}n1.58. Since n2n^2n2 grows polynomially faster than n1.58n^{1.58}n1.58 (specifically, n2\=Ω(n1.58+0.4)n^2 = \\Omega(n^{1.58 + 0.4})n2\=Ω(n1.58+0.4)), **Case 3** applies. The work at the root dominates.
 
4. 4
 
 Step 4
 
 Check the Regularity Condition
 
 For Case 3, we MUST check if af(n/b)≤cf(n)a f(n/b) \\le c f(n)af(n/b)≤cf(n). Substituting our values: 3(n/2)2≤cn2  ⟹  34n2≤cn23(n/2)^2 \\le c n^2 \\implies \\frac{3}{4}n^2 \\le c n^23(n/2)2≤cn2⟹43​n2≤cn2. This holds true for any constant c≥3/4c \\ge 3/4c≥3/4. The condition is satisfied.
 
5. 5
 
 Step 5
 
 State the Final Complexity
 
 By Master's Theorem Case 3, the time complexity is strictly determined by f(n)f(n)f(n). Therefore, **T(n)\=Θ(n2)T(n) = \\Theta(n^2)T(n)\=Θ(n2)**.
 

### Trace: The Substitution Method

1. 1
 
 Step 1
 
 Expand the Recurrence
 
 Given T(n)\=T(n−1)+nT(n) = T(n-1) + nT(n)\=T(n−1)+n with a base case of T(1)\=1T(1) = 1T(1)\=1. Let's expand T(n−1)T(n-1)T(n−1) to see the pattern: T(n−1)\=T(n−2)+(n−1)T(n-1) = T(n-2) + (n-1)T(n−1)\=T(n−2)+(n−1).
 
2. 2
 
 Step 2
 
 Substitute Backwards
 
 Substitute the expansion back into the original equation: T(n)\=\[T(n−2)+(n−1)\]+nT(n) = \[T(n-2) + (n-1)\] + nT(n)\=\[T(n−2)+(n−1)\]+n. Let's expand one more time for clarity: T(n−2)\=T(n−3)+(n−2)T(n-2) = T(n-3) + (n-2)T(n−2)\=T(n−3)+(n−2). So, T(n)\=T(n−3)+(n−2)+(n−1)+nT(n) = T(n-3) + (n-2) + (n-1) + nT(n)\=T(n−3)+(n−2)+(n−1)+n.
 
3. 3
 
 Step 3
 
 Generalize to the k-th step
 
 We can clearly see a pattern emerging. After kkk expansions, the equation looks like this: T(n)\=T(n−k)+(n−(k−1))+⋯+(n−1)+nT(n) = T(n-k) + (n-(k-1)) + \\dots + (n-1) + nT(n)\=T(n−k)+(n−(k−1))+⋯+(n−1)+n.
 
4. 4
 
 Step 4
 
 Reach the Base Case
 
 The recursion stops when we hit the base case T(1)T(1)T(1). This happens when n−k\=1n - k = 1n−k\=1, which means k\=n−1k = n - 1k\=n−1. Substitute k\=n−1k = n - 1k\=n−1 into our generalized equation: T(n)\=T(1)+2+3+⋯+(n−1)+nT(n) = T(1) + 2 + 3 + \\dots + (n-1) + nT(n)\=T(1)+2+3+⋯+(n−1)+n.
 
5. 5
 
 Step 5
 
 Solve the Series
 
 Since T(1)\=1T(1) = 1T(1)\=1, the equation becomes the sum of the first nnn natural numbers: 1+2+3+⋯+n1 + 2 + 3 + \\dots + n1+2+3+⋯+n. The mathematical formula for this arithmetic progression is n(n+1)2\\frac{n(n+1)}{2}2n(n+1)​. Expanding this gives n22+n2\\frac{n^2}{2} + \\frac{n}{2}2n2​+2n​. Dropping constants yields **O(n2)O(n^2)O(n2)**.
 

### The Recursion Tree Method

While the Substitution Method relies heavily on algebra, the **Recursion Tree Method** relies on visualization. It converts the recurrence into a tree where:

- Each node represents the cost of a single subproblem.
- The tree branches represent the recursive calls.

To find the total complexity, you sum the costs across all nodes at each depth to get a set of per-level costs, and then sum those per-level costs across the entire depth of the tree.

**Example Visualization for T(n)\=2T(n/2)+nT(n) = 2T(n/2) + nT(n)\=2T(n/2)+n (Merge Sort):**

- **Level 0 Cost:** 1 node × n\\times \\ n× n = **nnn**
- **Level 1 Cost:** 2 nodes × n/2\\times \\ n/2× n/2 = **nnn**
- **Level 2 Cost:** 4 nodes × n/4\\times \\ n/4× n/4 = **nnn**

At every single level, the total work done is nnn. How deep does the tree go before hitting size 1? The depth of a tree that halves at each step is log⁡2n\\log\_2 nlog2​n. Therefore, Total Cost = (Cost per level) ×\\times× (Number of levels) = **n×log⁡2n  ⟹  O(nlog⁡n)n \\times \\log\_2 n \\implies O(n \\log n)n×log2​n⟹O(nlogn)**.

### Knowledge Check

Question 1 of 3

Q1Single choice

The recurrence T(n) = T(n/2) + 1 has a time complexity of:

O(n)

O(log n)

O(n log n)

O(n²)

BackNext

[Master's Theorem - Visual Guide\\ \\ web](https://www.geeksforgeeks.org/advanced-master-theorem-for-divide-and-conquer-recurrences/)

[Previous\\ \\ Complexity Analysis and Time-Space Trade-offs](https://coursify.hasanraiyan.me/course/design-and-analysis-of-algorithms-daa/complexity-analysis-and-time-space-trade-offs) [Next\\ \\ Recurrence Relations and Recursive Algorithm Analysis](https://coursify.hasanraiyan.me/course/design-and-analysis-of-algorithms-daa/recurrence-relations-and-recursive-algorithm-analysis)