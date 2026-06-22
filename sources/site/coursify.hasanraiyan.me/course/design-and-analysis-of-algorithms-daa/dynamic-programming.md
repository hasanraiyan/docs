# Source: https://coursify.hasanraiyan.me/course/design-and-analysis-of-algorithms-daa/dynamic-programming

# Dynamic Programming

60 mins

Conquer the most mathematically intensive algorithmic strategy. Learn how to solve the 0/1 Knapsack problem using tabulation, and master the heavily-tested Matrix Chain Multiplication numericals.

### Learning Goals

- Define the two strict requirements for Dynamic Programming: Overlapping Subproblems and Optimal Substructure.
- Explain how a 2D matrix solves the 0/1 Knapsack problem where the Greedy method fails.
- Memorize the Recurrence Relation for Matrix Chain Multiplication (MCM).
- Perform a flawless, mathematically rigorous step-by-step trace of an MCM numerical.

---

### The Two Pillars of Dynamic Programming

Dynamic Programming (DP) is a strategy used to solve optimization problems by breaking them down into simpler subproblems. Unlike Divide and Conquer (which divides problems into _independent_ subproblems), DP is used when subproblems are **dependent** and repeat themselves.

To use DP, a problem must exhibit two core properties:

1. **Overlapping Subproblems:** The problem can be broken down into subproblems which are reused multiple times. Instead of recalculating the same subproblem (which causes exponential time), DP stores the result in a table (memoization or tabulation) and reuses it in O(1)O(1)O(1) time. _Example: In Fibonacci, calculating F(4)F(4)F(4) requires F(3)F(3)F(3) and F(2)F(2)F(2), but F(3)F(3)F(3) also requires F(2)F(2)F(2). F(2)F(2)F(2) is overlapping._
2. **Optimal Substructure:** The optimal solution to the overall problem can be constructed directly from the optimal solutions of its subproblems. If you make the best choice at each step, you are guaranteed the global best choice.

### Solving 0/1 Knapsack using DP

1. 1
 
 Step 1
 
 Why Greedy Fails
 
 In 0/1 Knapsack, items cannot be broken into fractions. You must take the whole item or leave it. The Greedy method fails because picking an item with the highest Profit/Weight ratio might leave a large, awkward gap in the knapsack that cannot be filled, wasting capacity. We must evaluate combinations to guarantee the global optimum.
 
2. 2
 
 Step 2
 
 The Tabulation Matrix
 
 We create a 2D matrix `dp[i][w]`. `i` represents the items considered so far (from 1 to N). `w` represents the current capacity of the knapsack (from 0 to total capacity W). `dp[i][w]` stores the **maximum profit** we can achieve using the first `i` items with a weight limit of `w`.
 
3. 3
 
 Step 3
 
 The DP Recurrence Relation
 
 For each cell, we have two choices for the current item `i` (with weight `W[i]` and profit `P[i]`):
 
 1. **Leave it:** The profit is the same as if we didn't have this item: `dp[i-1][w]`.
 2. **Take it:** We add `P[i]` to our profit, but we must subtract `W[i]` from our capacity: `P[i] + dp[i-1][w - W[i]]`. We take the maximum of these two choices.
 
4. 4
 
 Step 4
 
 The Algorithm
 
 `1For i = 1 to N: 2   For w = 1 to W: 3      If W[i] <= w: 4         dp[i][w] = MAX( dp[i-1][w] , P[i] + dp[i-1][w - W[i]] ) 5      Else: 6         dp[i][w] = dp[i-1][w]`
 
5. 5
 
 Step 5
 
 Complexity
 
 We fill a table of size `N` (items) by `W` (capacity). Therefore, the Time Complexity is **O(N \* W)** and the Space Complexity is **O(N \* W)**.
 

### Matrix Chain Multiplication (MCM)

Matrix Chain Multiplication is the most frequently tested DP problem in the exams. **Objective:** We are _not_ actually multiplying the matrices. We are trying to find the most efficient way to place parentheses around the matrices to minimize the total number of scalar multiplications.

_Rule:_ Multiplying a matrix of size (p×q)(p \\times q)(p×q) with a matrix of size (q×r)(q \\times r)(q×r) costs **p×q×rp \\times q \\times rp×q×r** operations, and the resulting matrix is size (p×r)(p \\times r)(p×r).

**The MCM Recurrence Relation:** To find the minimum cost to multiply a chain of matrices from iii to jjj, we split the chain at some matrix kkk. m\[i,j\]\=min⁡i≤k<j{m\[i,k\]+m\[k+1,j\]+Pi−1PkPj}m\[i, j\] = \\min\_{i \\le k < j} \\{ m\[i, k\] + m\[k+1, j\] + P\_{i-1} P\_k P\_j \\}m\[i,j\]\=mini≤k<j​{m\[i,k\]+m\[k+1,j\]+Pi−1​Pk​Pj​}

- m\[i,k\]m\[i, k\]m\[i,k\]: Cost of multiplying the left half.
- m\[k+1,j\]m\[k+1, j\]m\[k+1,j\]: Cost of multiplying the right half.
- Pi−1PkPjP\_{i-1} P\_k P\_jPi−1​Pk​Pj​: Cost of multiplying the resulting left matrix with the resulting right matrix.

### Trace: Matrix Chain Multiplication

1. 1
 
 Step 1
 
 Extract the Dimension Array (P)
 
 Given matrices: A1(10×20)A\_1(10 \\times 20)A1​(10×20), A2(20×50)A\_2(20 \\times 50)A2​(20×50), A3(50×1)A\_3(50 \\times 1)A3​(50×1), A4(1×100)A\_4(1 \\times 100)A4​(1×100). We extract the common dimensions into an array PPP. P0\=10,P1\=20,P2\=50,P3\=1,P4\=100P\_0 = 10, P\_1 = 20, P\_2 = 50, P\_3 = 1, P\_4 = 100P0​\=10,P1​\=20,P2​\=50,P3​\=1,P4​\=100.
 
2. 2
 
 Step 2
 
 Chain Length = 1 (Main Diagonal)
 
 Multiplying a single matrix by itself costs 0 operations. m\[1,1\]\=0m\[1,1\] = 0m\[1,1\]\=0 m\[2,2\]\=0m\[2,2\] = 0m\[2,2\]\=0 m\[3,3\]\=0m\[3,3\] = 0m\[3,3\]\=0 m\[4,4\]\=0m\[4,4\] = 0m\[4,4\]\=0
 
3. 3
 
 Step 3
 
 Chain Length = 2 (Adjacent Pairs)
 
 We calculate m\[i,j\]m\[i, j\]m\[i,j\] where j−i\=1j - i = 1j−i\=1. m\[1,2\]\=P0×P1×P2\=10×20×50\=10000m\[1,2\] = P\_0 \\times P\_1 \\times P\_2 = 10 \\times 20 \\times 50 = 10000m\[1,2\]\=P0​×P1​×P2​\=10×20×50\=10000 m\[2,3\]\=P1×P2×P3\=20×50×1\=1000m\[2,3\] = P\_1 \\times P\_2 \\times P\_3 = 20 \\times 50 \\times 1 = 1000m\[2,3\]\=P1​×P2​×P3​\=20×50×1\=1000 m\[3,4\]\=P2×P3×P4\=50×1×100\=5000m\[3,4\] = P\_2 \\times P\_3 \\times P\_4 = 50 \\times 1 \\times 100 = 5000m\[3,4\]\=P2​×P3​×P4​\=50×1×100\=5000
 
4. 4
 
 Step 4
 
 Chain Length = 3
 
 **Calculate m\[1,3\]m\[1,3\]m\[1,3\]:** We can split at k\=1k=1k\=1 or k\=2k=2k\=2. If k\=1k=1k\=1: m\[1,1\]+m\[2,3\]+P0P1P3\=0+1000+(10×20×1)\=1200m\[1,1\] + m\[2,3\] + P\_0 P\_1 P\_3 = 0 + 1000 + (10 \\times 20 \\times 1) = 1200m\[1,1\]+m\[2,3\]+P0​P1​P3​\=0+1000+(10×20×1)\=1200. If k\=2k=2k\=2: m\[1,2\]+m\[3,3\]+P0P2P3\=10000+0+(10×50×1)\=10500m\[1,2\] + m\[3,3\] + P\_0 P\_2 P\_3 = 10000 + 0 + (10 \\times 50 \\times 1) = 10500m\[1,2\]+m\[3,3\]+P0​P2​P3​\=10000+0+(10×50×1)\=10500. Minimum is **1200** (split at k\=1k=1k\=1).
 
 **Calculate m\[2,4\]m\[2,4\]m\[2,4\]:** We can split at k\=2k=2k\=2 or k\=3k=3k\=3. If k\=2k=2k\=2: m\[2,2\]+m\[3,4\]+P1P2P4\=0+5000+(20×50×100)\=105000m\[2,2\] + m\[3,4\] + P\_1 P\_2 P\_4 = 0 + 5000 + (20 \\times 50 \\times 100) = 105000m\[2,2\]+m\[3,4\]+P1​P2​P4​\=0+5000+(20×50×100)\=105000. If k\=3k=3k\=3: m\[2,3\]+m\[4,4\]+P1P3P4\=1000+0+(20×1×100)\=3000m\[2,3\] + m\[4,4\] + P\_1 P\_3 P\_4 = 1000 + 0 + (20 \\times 1 \\times 100) = 3000m\[2,3\]+m\[4,4\]+P1​P3​P4​\=1000+0+(20×1×100)\=3000. Minimum is **3000** (split at k\=3k=3k\=3).
 
5. 5
 
 Step 5
 
 Chain Length = 4 (Final Answer)
 
 **Calculate m\[1,4\]m\[1,4\]m\[1,4\]:** We can split at k\=1,2,k=1, 2,k\=1,2, or 333. If k\=1k=1k\=1: m\[1,1\]+m\[2,4\]+P0P1P4\=0+3000+(10×20×100)\=23000m\[1,1\] + m\[2,4\] + P\_0 P\_1 P\_4 = 0 + 3000 + (10 \\times 20 \\times 100) = 23000m\[1,1\]+m\[2,4\]+P0​P1​P4​\=0+3000+(10×20×100)\=23000. If k\=2k=2k\=2: m\[1,2\]+m\[3,4\]+P0P2P4\=10000+5000+(10×50×100)\=65000m\[1,2\] + m\[3,4\] + P\_0 P\_2 P\_4 = 10000 + 5000 + (10 \\times 50 \\times 100) = 65000m\[1,2\]+m\[3,4\]+P0​P2​P4​\=10000+5000+(10×50×100)\=65000. If k\=3k=3k\=3: m\[1,3\]+m\[4,4\]+P0P3P4\=1200+0+(10×1×100)\=2200m\[1,3\] + m\[4,4\] + P\_0 P\_3 P\_4 = 1200 + 0 + (10 \\times 1 \\times 100) = 2200m\[1,3\]+m\[4,4\]+P0​P3​P4​\=1200+0+(10×1×100)\=2200. Minimum operations = **2200** (split at k\=3k=3k\=3).
 
6. 6
 
 Step 6
 
 Conclusion & Complexity
 
 The minimum number of operations is **2200**. Because the final split was at k\=3k=3k\=3, the optimal parenthesization is (A1(A2A3))A4(A\_1 (A\_2 A\_3)) A\_4(A1​(A2​A3​))A4​. The Time Complexity for MCM is **O(n3)O(n^3)O(n3)** and Space Complexity is **O(n2)O(n^2)O(n2)** to store the mmm table.
 

### Knowledge Check

Question 1 of 3

Q1Single choice

What is the primary advantage of dynamic programming over brute-force algorithms?

Dynamic programming guarantees finding the global optimum.

Dynamic programming reduces the time complexity by avoiding redundant computations.

Dynamic programming simplifies the problem by dividing it into smaller subproblems.

Dynamic programming is more intuitive to implement.

BackNext

[Abdul Bari: Matrix Chain Multiplication (Watch this to guarantee 7 marks)\\ \\ web](https://www.youtube.com/watch?v=prx1psByp7U)

[Previous\\ \\ Brute-Force & Greedy Strategies](https://coursify.hasanraiyan.me/course/design-and-analysis-of-algorithms-daa/brute-force-greedy-strategies) [Next\\ \\ Backtracking & Branch and Bound](https://coursify.hasanraiyan.me/course/design-and-analysis-of-algorithms-daa/backtracking-branch-and-bound)