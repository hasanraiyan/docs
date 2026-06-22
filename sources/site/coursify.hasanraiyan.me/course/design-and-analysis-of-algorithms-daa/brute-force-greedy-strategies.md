# Source: https://coursify.hasanraiyan.me/course/design-and-analysis-of-algorithms-daa/brute-force-greedy-strategies

# Brute-Force & Greedy Strategies

40 mins

Master the foundational algorithmic paradigms. Learn how Divide & Conquer powers Quick Sort, and how the Greedy Method solves the Fractional Knapsack and Huffman Coding problems while failing at others.

### Learning Goals

- Understand the time complexity and trace the partitioning step of Quick Sort.
- Define the Greedy strategy and explain mathematically why it fails for the 0/1 Knapsack problem.
- Perform a step-by-step trace of the Fractional Knapsack problem using Profit/Weight ratios.
- Apply the greedy approach to construct a Huffman Coding tree.

---

### Paradigms Overview: Brute Force vs. Divide & Conquer

Algorithmic paradigms are general frameworks used to design algorithms.

- **Brute Force:** The most straightforward approach. It tries every single possible combination or path until the solution is found. (e.g., Linear Search, checking every subset for Knapsack). It guarantees an optimal solution but is incredibly slow, often taking exponential time O(2n)O(2^n)O(2n).
- **Divide and Conquer:** Solves a problem by dividing it into smaller, independent subproblems, solving them recursively, and then combining the results.

### Quick Sort

Quick Sort is a classic Divide and Conquer algorithm. It selects a "pivot" element, partitions the array so that smaller elements are to the left of the pivot and larger elements are to the right, and then recursively sorts the two halves.

**Time Complexities:**

- **Best Case:** Ω(nlog⁡n)\\Omega(n \\log n)Ω(nlogn) — The pivot perfectly divides the array into two equal halves every time.
- **Average Case:** Θ(nlog⁡n)\\Theta(n \\log n)Θ(nlogn) — The pivot divides the array somewhat evenly on average.
- **Worst Case:** O(n2)O(n^2)O(n2) — The array is already sorted (or reverse sorted) and the algorithm picks the largest/smallest element as the pivot, resulting in an n−1n-1n−1 and 000 split.

**Advantages vs Disadvantages:**

- _Advantage:_ It is an **in-place** sorting algorithm. It requires strictly O(1)O(1)O(1) auxiliary space, making it vastly superior to Merge Sort (which requires O(n)O(n)O(n) space) for large datasets in memory.
- _Disadvantage:_ Its worst-case time complexity is O(n2)O(n^2)O(n2), making it vulnerable to worst-case inputs unless randomization is used. It is also an _unstable_ sort.

### Trace: Quick Sort Partitioning

1. 1
 
 Step 1
 
 Initialization
 
 Let's trace the Lomuto partition scheme for an array: `A = [10, 80, 30, 90, 40, 50, 70]`. The pivot is the last element: `pivot = 70`. We initialize a pointer `i` to track the boundary of elements smaller than the pivot. Initially, `i = -1` (before the first index).
 
2. 2
 
 Step 2
 
 Loop j = 0 to 4 (Elements smaller than pivot)
 
 For `j=0` (10), 10 < 70, so `i` increments to 0. Swap `A[0]` with `A[0]`. No change. Array: `[10, 80, 30, 90, 40, 50, 70]`. For `j=1` (80), 80 > 70. Do nothing. For `j=2` (30), 30 < 70, so `i` increments to 1. Swap `A[i]` (80) with `A[j]` (30). Array becomes: `[10, 30, 80, 90, 40, 50, 70]`.
 
3. 3
 
 Step 3
 
 Loop j = 3 to 5
 
 For `j=3` (90), 90 > 70. Do nothing. For `j=4` (40), 40 < 70, `i` increments to 2. Swap `A[2]` (80) with `A[4]` (40). Array: `[10, 30, 40, 90, 80, 50, 70]`. For `j=5` (50), 50 < 70, `i` increments to 3. Swap `A[3]` (90) with `A[5]` (50). Array: `[10, 30, 40, 50, 80, 90, 70]`.
 
4. 4
 
 Step 4
 
 Final Pivot Placement
 
 The loop finishes. We must place the pivot in its correct sorted position. We swap the pivot (at the last index) with the element at `i+1` (which is index 4, value 80). Array becomes: `[10, 30, 40, 50, 70, 90, 80]`.
 
5. 5
 
 Step 5
 
 Result
 
 The pivot `70` is now in its correct, final sorted position. All elements to the left `[10, 30, 40, 50]` are smaller. All elements to the right `[90, 80]` are larger. Quick sort will now recursively call itself on the left and right sub-arrays.
 

### String Matching: Brute Force vs. KMP Algorithm

String matching involves finding a pattern PPP of length mmm inside a text TTT of length nnn.

- **Brute Force String Matching:** Aligns the pattern at every possible index in the text and checks character by character. If a mismatch occurs, the pattern shifts by exactly 1 position and starts over. Worst-case time complexity: **O(n×m)O(n \\times m)O(n×m)**.
- **Knuth-Morris-Pratt (KMP) Algorithm:** Optimizes this by pre-processing the pattern to construct a **LPS (Longest Proper Prefix which is also Suffix)** array. When a mismatch occurs, KMP uses the LPS array to shift the pattern multiple positions at once, entirely avoiding the re-examination of previously matched characters. Worst-case time complexity: **O(n+m)O(n + m)O(n+m)**.

### Trace: KMP Algorithm

1. 1
 
 Step 1
 
 Compute the LPS (Pi) Table
 
 Given Pattern P\="ababaca"P = \\text{"ababaca"}P\="ababaca". We find the Longest Proper Prefix that is also a Suffix for every substring of PPP:
 
 - `a`   ⟹  0\\implies 0⟹0
 - `ab`   ⟹  0\\implies 0⟹0
 - `aba`   ⟹  1\\implies 1⟹1 (prefix 'a', suffix 'a')
 - `abab`   ⟹  2\\implies 2⟹2 (prefix 'ab', suffix 'ab')
 - `ababa`   ⟹  3\\implies 3⟹3 (prefix 'aba', suffix 'aba')
 - `ababac`   ⟹  0\\implies 0⟹0
 - `ababaca`   ⟹  1\\implies 1⟹1 **LPS Array:** `[0, 0, 1, 2, 3, 0, 1]`
 
2. 2
 
 Step 2
 
 Initialize Pointers
 
 Given Text S\="bacbabababacaab"S = \\text{"bacbabababacaab"}S\="bacbabababacaab" and Pattern P\="ababaca"P = \\text{"ababaca"}P\="ababaca". We use iii to iterate through SSS and jjj to iterate through PPP. Initially, i\=0,j\=0i = 0, j = 0i\=0,j\=0.
 
3. 3
 
 Step 3
 
 Trace the Matching Process (First shift)
 
 Compare S\[0\]S\[0\]S\[0\] ('b') with P\[0\]P\[0\]P\[0\] ('a'). Mismatch. Since j\=0j=0j\=0, we just increment iii. Compare S\[1\]S\[1\]S\[1\] ('a') with P\[0\]P\[0\]P\[0\] ('a'). Match! Increment both. Compare S\[2\]S\[2\]S\[2\] ('c') with P\[1\]P\[1\]P\[1\] ('b'). Mismatch. Since j\=1j=1j\=1, we look at `LPS[j-1]` which is `LPS[0] = 0`. So jjj becomes 0. We don't increment iii. Compare S\[2\]S\[2\]S\[2\] ('c') with P\[0\]P\[0\]P\[0\] ('a'). Mismatch. j\=0j=0j\=0, so increment iii to 3.
 
4. 4
 
 Step 4
 
 Finding the Substring
 
 At i\=3i=3i\=3, S\[3\]S\[3\]S\[3\] is 'b'. Mismatch with P\[0\]P\[0\]P\[0\] ('a'). Increment i\=4i=4i\=4. At i\=4i=4i\=4, S\[4\]S\[4\]S\[4\] is 'a'. We now match continuously: S\[4..8\]S\[4..8\]S\[4..8\] ('ababa') matches P\[0..4\]P\[0..4\]P\[0..4\] ('ababa'). So i\=9,j\=5i=9, j=5i\=9,j\=5. Compare S\[9\]S\[9\]S\[9\] ('b') with P\[5\]P\[5\]P\[5\] ('c'). Mismatch! Instead of starting over, KMP looks at `LPS[j-1] = LPS[4] = 3`. We set j\=3j=3j\=3. The pattern shifts, but we keep i\=9i=9i\=9!
 
5. 5
 
 Step 5
 
 The Final Match
 
 With j\=3j=3j\=3, we compare S\[9\]S\[9\]S\[9\] ('b') with P\[3\]P\[3\]P\[3\] ('b'). Match! We continue matching: S\[10\]S\[10\]S\[10\] ('a') with P\[4\]P\[4\]P\[4\] ('a'), S\[11\]S\[11\]S\[11\] ('c') with P\[5\]P\[5\]P\[5\] ('c'), S\[12\]S\[12\]S\[12\] ('a') with P\[6\]P\[6\]P\[6\] ('a'). Now j\=7j=7j\=7, which equals the length of the pattern. **Match found!** The pattern exists starting at index 12−7+1\=612 - 7 + 1 = 612−7+1\=6 in the text.
 

### The Greedy Method & Its Limitations

The Greedy strategy makes a locally optimal choice at each stage with the hope that these local choices will lead to a global optimum. It never reconsiders its choices; once a decision is made, it is locked in.

_Classic Greedy Algorithms:_ Fractional Knapsack, Dijkstra's Algorithm, Kruskal's Algorithm, Huffman Coding.

#### Why Greedy Fails for 0/1 Knapsack

In the **Fractional Knapsack** problem, you are allowed to break items into smaller pieces (like bags of sand or gold dust). The Greedy method works perfectly here: you calculate the `Profit/Weight` ratio for every item, sort them descending, and fill the bag. If an item doesn't completely fit, you take the exact fraction that fits, utilizing 100% of the knapsack's capacity.

In the **0/1 Knapsack** problem, items are indivisible (like laptops or TVs). You must take the whole item (1) or leave it (0). **Why Greedy Fails here:** If the greedy algorithm chooses an item with the highest `Profit/Weight` ratio, but that item takes up a massive amount of weight, it might leave a small, awkward gap in the knapsack. Because items cannot be broken, that gap remains empty space. A non-greedy combination of multiple slightly less profitable items might have fit perfectly and yielded a higher total profit.

_Therefore, 0/1 Knapsack must use Dynamic Programming to evaluate combinations and guarantee the global optimum._

### Trace: Fractional Knapsack

1. 1
 
 Step 1
 
 Calculate the Profit/Weight Ratio
 
 We have a capacity W\=15W=15W\=15. We calculate P/WP/WP/W for all 7 items: 1: 5/1 = 5 2: 10/3 = 3.33 3: 15/5 = 3 4: 7/4 = 1.75 5: 8/1 = 8 6: 9/3 = 3 7: 4/2 = 2
 
2. 2
 
 Step 2
 
 Sort Descending by Ratio
 
 Sort the items based on their ratio from highest to lowest: Item 5 (Ratio 8, W=1) Item 1 (Ratio 5, W=1) Item 2 (Ratio 3.33, W=3) Item 3 (Ratio 3, W=5) Item 6 (Ratio 3, W=3) Item 7 (Ratio 2, W=2) Item 4 (Ratio 1.75, W=4)
 
3. 3
 
 Step 3
 
 Greedily Fill the Knapsack
 
 Take Item 5: Cap left = 14. Profit = 8. Take Item 1: Cap left = 13. Profit = 8 + 5 = 13. Take Item 2: Cap left = 10. Profit = 13 + 10 = 23. Take Item 3: Cap left = 5. Profit = 23 + 15 = 38. Take Item 6: Cap left = 2. Profit = 38 + 9 = 47.
 
4. 4
 
 Step 4
 
 Take the Fraction
 
 The next item is Item 7 (Weight = 2). The capacity left is exactly 2! We can take the whole item. Take Item 7: Cap left = 0. Profit = 47 + 4 = **51**. The knapsack is completely full. We ignore the final item.
 
5. 5
 
 Step 5
 
 Conclusion
 
 The maximum profit obtained using the Greedy method is 51. The time complexity of this algorithm is dominated by the sorting step, making it **O(n log n)**.
 

### Trace: Huffman Coding

1. 1
 
 Step 1
 
 Setup the Initial Forest
 
 Given characters and frequencies: T(43), I(38), V(16), K(8), L(50), E(12), O(56), Z(13), P(22), R(7). Create a leaf node for each character. This is our forest. The greedy strategy is to always merge the two nodes with the lowest frequencies.
 
2. 2
 
 Step 2
 
 Merge 1 & 2
 
 The two minimum frequencies are R(7) and K(8). Merge them to create an internal node with frequency 15. The forest now contains this internal node (15) and the remaining letters.
 
3. 3
 
 Step 3
 
 Merge 3 & 4
 
 The two new minimums are E(12) and Z(13). Merge them to create an internal node with frequency 25.
 
4. 4
 
 Step 4
 
 Merge 5 & 6
 
 The two minimums are now the internal node (15) and V(16). Merge them to create an internal node with frequency 31.
 
5. 5
 
 Step 5
 
 Continue Building the Tree Bottom-Up
 
 This greedy process of extracting the two minimums, adding their frequencies, and inserting the combined node back into the pool continues until only one single root node remains (whose frequency equals the sum of all characters, 265). We use a **Min-Heap (Priority Queue)** to efficiently extract the minimums.
 
6. 6
 
 Step 6
 
 Extract the Codes
 
 Once the tree is built, assign a `0` to every left edge and a `1` to every right edge. To find the Huffman code for a character, traverse from the root to the leaf node, appending the edge bits. Because the most frequent characters (like O=56) were merged last, they end up closest to the root and receive the shortest binary codes, minimizing total file size.
 

### Knowledge Check

Question 1 of 3

Q1Single choice

Which of the following sorting algorithms has the best time complexity in the average case?

Bubble sort

Insertion sort

Quick sort

Selection sort

BackNext

[Huffman Coding Visualizer\\ \\ web](https://vanya.jp.net/vtree/huffman.html)

[Previous\\ \\ PYQ Analysis & Exam Preparation — Module 1](https://coursify.hasanraiyan.me/course/design-and-analysis-of-algorithms-daa/pyq-analysis-exam-preparation-module-1) [Next\\ \\ Dynamic Programming](https://coursify.hasanraiyan.me/course/design-and-analysis-of-algorithms-daa/dynamic-programming)