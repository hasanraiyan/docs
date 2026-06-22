# Source: https://coursify.hasanraiyan.me/course/design-and-analysis-of-algorithms-daa/recurrence-relations-and-recursive-algorithm-analysis

# Recurrence Relations and Recursive Algorithm Analysis

15 mins

### Learning Goals

- Goal 1

---

### From Code to Recurrence: The Derivation Process

To analyze a recursive algorithm, you must first convert the code into a mathematical **Recurrence Relation**. This represents the total time T(n)T(n)T(n) as a sum of the work done at the current level plus the time taken by recursive calls.

#### 1\. Linear Recursion (e.g., Factorial)

`1int factorial(int n) { 2    if (n == 0) return 1;           // Base Case: Constant time c1 3    return n * factorial(n - 1);    // Recursive step: T(n-1) + c2 (multiplication) 4}`

**Recurrence:** T(n)\=T(n−1)+1T(n) = T(n-1) + 1T(n)\=T(n−1)+1 (where 1 is constant time for comparison/multiplication).

#### 2\. Divide and Conquer (e.g., Binary Search)

`1int binarySearch(int A[], int low, int high, int x) { 2    int mid = (low + high) / 2;             // Constant work: c 3    if (x == A[mid]) return mid; 4    if (x < A[mid])  5        return binarySearch(A, low, mid-1, x); // T(n/2) 6    else  7        return binarySearch(A, mid+1, high, x); // T(n/2) 8}`

**Recurrence:** T(n)\=T(n/2)+1T(n) = T(n/2) + 1T(n)\=T(n/2)+1. (Note: We only make ONE recursive call, not two).

#### 3\. Multiple Subproblems (e.g., Merge Sort)

Merge sort divides the array into two halves, calls itself twice, and then merges them. **Recurrence:** T(n)\=2T(n/2)+nT(n) = 2T(n/2) + nT(n)\=2T(n/2)+n. (The nnn comes from the linear-time Merge process).

### Formal Analysis: The Substitution Method (Induction)

In university exams, you are often asked to "Prove by induction" that a recurrence has a specific bound. This is the formal side of the Substitution Method.

**Problem:** Prove that T(n)\=T(n−1)+nT(n) = T(n-1) + nT(n)\=T(n−1)+n is O(n2)O(n^2)O(n2).

**Step 1: The Guess** We guess that T(n)≤c⋅n2T(n) \\le c \\cdot n^2T(n)≤c⋅n2 for some constant ccc.

**Step 2: Mathematical Induction (The Hypothesis)** Assume the guess holds for all values up to n−1n-1n−1. Therefore: T(n−1)≤c(n−1)2T(n-1) \\le c(n-1)^2T(n−1)≤c(n−1)2

**Step 3: Substitution** Substitute the hypothesis into the original recurrence: T(n)\=T(n−1)+nT(n) = T(n-1) + nT(n)\=T(n−1)+n T(n)≤c(n−1)2+nT(n) \\le c(n-1)^2 + nT(n)≤c(n−1)2+n T(n)≤c(n2−2n+1)+nT(n) \\le c(n^2 - 2n + 1) + nT(n)≤c(n2−2n+1)+n T(n)≤cn2−2cn+c+nT(n) \\le cn^2 - 2cn + c + nT(n)≤cn2−2cn+c+n

**Step 4: Prove the Bound** We need to show that cn2−2cn+c+n≤cn2cn^2 - 2cn + c + n \\le cn^2cn2−2cn+c+n≤cn2. This is true if −2cn+c+n≤0\-2cn + c + n \\le 0−2cn+c+n≤0. n(1−2c)+c≤0n(1 - 2c) + c \\le 0n(1−2c)+c≤0. This holds for c≥1c \\ge 1c≥1 and sufficiently large nnn. **Conclusion:** T(n)\=O(n2)T(n) = O(n^2)T(n)\=O(n2).

### Space Complexity: Tracing the Recursion Stack

1. 1
 
 Step 1
 
 Understand the Stack Frame
 
 Every time a recursive function is called, the system allocates a 'Stack Frame' containing local variables, parameters, and the return address. This consumes physical memory.
 
2. 2
 
 Step 2
 
 Calculate Stack Depth (Factorial)
 
 For `factorial(n)`, the calls go: n→n−1→⋯→0n \\to n-1 \\to \\dots \\to 0n→n−1→⋯→0. There are n+1n+1n+1 active frames on the stack at the deepest point. **Space Complexity:** O(n)O(n)O(n).
 
3. 3
 
 Step 3
 
 Calculate Stack Depth (Binary Search)
 
 For Binary Search, the problem size halves at each step: n→n/2→n/4→⋯→1n \\to n/2 \\to n/4 \\to \\dots \\to 1n→n/2→n/4→⋯→1. The number of steps is log⁡2n\\log\_2 nlog2​n. **Space Complexity:** O(log⁡n)O(\\log n)O(logn).
 
4. 4
 
 Step 4
 
 Calculate Stack Depth (Merge Sort)
 
 Merge sort also has a tree depth of log⁡n\\log nlogn. However, it also uses an auxiliary array of size nnn for merging. **Total Space Complexity:** O(n)O(n)O(n) (dominated by the array).
 

#### The Master Theorem Gap

Master's Theorem cannot solve recurrences where f(n)f(n)f(n) is not polynomially smaller/larger than nlog⁡ban^{\\log\_b a}nlogb​a. For example, T(n)\=2T(n/2)+nlog⁡nT(n) = 2T(n/2) + n \\log nT(n)\=2T(n/2)+nlogn. Here, nlog⁡ba\=n1n^{\\log\_b a} = n^1nlogb​a\=n1. f(n)\=nlog⁡nf(n) = n \\log nf(n)\=nlogn. Since nlog⁡nn \\log nnlogn is only 'logarithmically' larger than nnn, not 'polynomially' larger (n1+ϵn^{1+\\epsilon}n1+ϵ), the theorem fails. You must use the Recursion Tree method instead.

more...

### Knowledge Check

Question 1 of 3

Q1Single choice

What is the recurrence relation for a recursive algorithm that divides a problem of size n into 3 subproblems of size n/3 and spends O(n) time combining them?

T(n) = T(n/3) + n

T(n) = 3T(n/3) + 1

T(n) = 3T(n/3) + n

T(n) = T(n-3) + n

BackNext

[Recursion Stack and Space Complexity\\ \\ web](https://www.geeksforgeeks.org/practice-questions-time-complexity-analysis/)

[Previous\\ \\ Solving Recurrence Relations](https://coursify.hasanraiyan.me/course/design-and-analysis-of-algorithms-daa/solving-recurrence-relations) [Next\\ \\ PYQ Analysis & Exam Preparation — Module 1](https://coursify.hasanraiyan.me/course/design-and-analysis-of-algorithms-daa/pyq-analysis-exam-preparation-module-1)