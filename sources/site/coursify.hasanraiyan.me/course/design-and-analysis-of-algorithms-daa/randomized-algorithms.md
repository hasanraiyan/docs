# Source: https://coursify.hasanraiyan.me/course/design-and-analysis-of-algorithms-daa/randomized-algorithms

# Randomized Algorithms

40 mins

Discover how utilizing random numbers within an algorithm can significantly improve average-case time complexity, with a deep dive into Randomized Quick Sort.

### Learning Goals

- Define Randomized Algorithms and explain their benefits.
- Compare Las Vegas and Monte Carlo algorithms.
- Trace the Randomized Quick Sort algorithm and analyze its time complexity.

---

### What are Randomized Algorithms?

_(Answers 2024 Q9a i & 2024 Q1j)_

A **Randomized Algorithm** is an algorithm that employs a degree of randomness as part of its logic. It makes **random choices during execution** (such as picking a random pivot, or rolling a digital die) to decide what step to take next.

Unlike Deterministic algorithms (which always follow the exact same path for a given input), a randomized algorithm might take a completely different path every time you run it on the exact same input! We use them because they are often simpler to write and yield much faster **average-case** time complexities.

### Two Classes of Randomized Algorithms:

| Class | Accuracy | Time Complexity | Example |
| --- | --- | --- | --- |
| **Las Vegas** | **100% Guaranteed Correct** answer every time. | Running time varies randomly. Could be fast, could be slow. | Randomized Quick Sort |
| **Monte Carlo** | Might give the **Wrong Answer** with a small probability. | Running time is **strictly fixed/deterministic**. | Miller-Rabin Primality Test |

### Trace: Randomized Quick Sort

1. 1
 
 Step 1
 
 The Flaw of Standard Quick Sort
 
 In standard Deterministic Quick Sort, we usually pick the _first_ or _last_ element as the Pivot. If the array is already sorted (e.g., `[1, 2, 3, 4, 5]`), picking the last element means we split the array into size N−1N-1N−1 and 000 every single time, triggering the worst-case **O(N2)O(N^2)O(N2)** time complexity.
 
2. 2
 
 Step 2
 
 The Randomized Solution
 
 Instead of deterministically picking the last element, we generate a random number between 111 and NNN, and swap that random element with the last element. Then we proceed with standard partitioning. This guarantees that no specific input (like a sorted array) can force the worst-case scenario.
 
3. 3
 
 Step 3
 
 The Pseudocode Algorithm
 
 `1Algorithm Randomized_QuickSort(A, p, r): 2   if p < r: 3      // Step 1: Find a random pivot and partition 4      q = Randomized_Partition(A, p, r) 5       6      // Step 2: Recurse on left side 7      Randomized_QuickSort(A, p, q - 1) 8       9      // Step 3: Recurse on right side 10      Randomized_QuickSort(A, q + 1, r) 11 12Algorithm Randomized_Partition(A, p, r): 13   i = Random(p, r)  // Pick a random index 14   Swap(A[i], A[r])  // Swap it to the end 15   return Partition(A, p, r) // Standard partition`
 
4. 4
 
 Step 4
 
 Time Complexity Analysis
 
 **Expected (Average) Case:** Because the pivot is chosen uniformly at random, it will theoretically split the array roughly down the middle (like 25%-75% or 50%-50%) most of the time. This yields a recursion tree of height log⁡N\\log NlogN, giving an expected time complexity of **O(Nlog⁡N)O(N \\log N)O(NlogN)**.
 
 **Worst Case:** If you are incredibly unlucky, the random number generator might pick the absolute largest element as the pivot _every single time_. The worst-case is technically still **O(N2)O(N^2)O(N2)**, but the probability of this happening on a large array is astronomically close to zero.
 

### Knowledge Check

Question 1 of 2

Q1Single choice

Randomized algorithms make use of:

Deterministic input

Random choices during execution

Recursive backtracking

Fixed input-output pairs

BackNext

[Previous\\ \\ Approximation Algorithms](https://coursify.hasanraiyan.me/course/design-and-analysis-of-algorithms-daa/approximation-algorithms) [Next\\ \\ Complexity Classes Beyond NP: PSPACE](https://coursify.hasanraiyan.me/course/design-and-analysis-of-algorithms-daa/complexity-classes-beyond-np-pspace)