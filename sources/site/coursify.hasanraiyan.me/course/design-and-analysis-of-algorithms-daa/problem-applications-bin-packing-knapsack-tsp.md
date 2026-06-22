# Source: https://coursify.hasanraiyan.me/course/design-and-analysis-of-algorithms-daa/problem-applications-bin-packing-knapsack-tsp

# Problem Applications: Bin Packing, Knapsack & TSP

25 mins

A capstone review of how different algorithmic strategies tackle the most famous combinatorial problems, including a deep dive into the Bin Packing heuristics (Next Fit, First Fit, Best Fit).

### Learning Goals

- Understand the Bin Packing problem and differentiate between its approximation heuristics.
- Compare how the Greedy method and Dynamic Programming approach the Knapsack problem.
- Review the Traveling Salesperson Problem constraints.

---

### The Bin Packing Problem

The **Bin Packing Problem** is a classic optimization problem. Given a set of items, each with a specific size or weight, and an infinite number of bins, each with a fixed capacity VVV, the objective is to pack all items into the **minimum possible number of bins**.

Because finding the exact optimal solution is **NP-Hard** (it would require trying every combination via brute force), we use **Approximation Heuristics** to find a "good enough" solution quickly in polynomial time.

#### The 3 Core Heuristics:

1. **Next Fit (NF):**
 
 - _Logic:_ Take the current item. If it fits in the current open bin, put it there. If it doesn't fit, close the bin forever, open a brand new bin, and put it there.
 - _Advantage:_ Extremely fast O(n)O(n)O(n).
 - _Disadvantage:_ Wastes the most space because it never looks back at older bins that might still have room.
2. **First Fit (FF):**
 
 - _Logic:_ Take the current item. Scan through all previously opened bins from left to right. Place the item in the _first_ bin that has enough space. Only open a new bin if it doesn't fit in any existing bin.
 - _Advantage:_ More efficient use of space than Next Fit.
 - _Complexity:_ O(n2)O(n^2)O(n2) or O(nlog⁡n)O(n \\log n)O(nlogn) if using specialized data structures.
3. **Best Fit (BF):**
 
 - _Logic:_ Take the current item. Scan all opened bins and place the item in the bin that will leave the **least amount of empty space left over**. If it fits nowhere, open a new bin.
 - _Advantage:_ Leaves the smallest gaps, generally producing the tightest packing.
 - _Complexity:_ O(n2)O(n^2)O(n2) or O(nlog⁡n)O(n \\log n)O(nlogn).

_(Pro-tip for exams: Sorting the items from largest to smallest before applying First Fit or Best Fit significantly improves the packing density. This is called First Fit Decreasing or Best Fit Decreasing)._

### The Multi-Paradigm Problems: A Summary

Throughout Module 2, we saw that the same underlying problem can be solved using different algorithmic strategies depending on the strictness of the constraints.

#### 1\. The Knapsack Problem

The problem asks us to maximize the profit of items placed into a bag with a strict weight capacity.

- **Fractional Knapsack (Items can be cut):** We use the **Greedy Method**. By sorting items by their Profit/WeightProfit/WeightProfit/Weight ratio, we can pack the absolute maximum value efficiently in O(nlog⁡n)O(n \\log n)O(nlogn) time.
- **0/1 Knapsack (Items are indivisible):** The Greedy method fails because it leaves empty gaps. We must use **Dynamic Programming (Tabulation)** to evaluate overlapping combinations and guarantee the global optimal profit in O(n×W)O(n \\times W)O(n×W) time.

#### 2\. The Traveling Salesperson Problem (TSP)

The problem asks us to find the shortest possible route that visits every city exactly once and returns to the origin.

- **Backtracking:** We can use Depth-First Search to explore every possible valid tour. This finds all solutions but is incredibly slow (O(n!)O(n!)O(n!) time).
- **Branch and Bound:** We use this to find the _single optimal_ (shortest) path. By calculating a lower bound matrix at each city, we can prune expensive branches early, drastically reducing computation time compared to pure backtracking.

### Knowledge Check

Question 1 of 2

Q1Single choice

Which Bin Packing heuristic never looks back at previously opened bins?

First Fit

Best Fit

Next Fit

Worst Fit

BackNext

[Previous\\ \\ Backtracking & Branch and Bound](https://coursify.hasanraiyan.me/course/design-and-analysis-of-algorithms-daa/backtracking-branch-and-bound) [Next\\ \\ PYQ Analysis & Exam Preparation — Module 2](https://coursify.hasanraiyan.me/course/design-and-analysis-of-algorithms-daa/pyq-analysis-exam-preparation-module-2)