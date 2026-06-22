# Source: https://coursify.hasanraiyan.me/course/design-and-analysis-of-algorithms-daa/characteristics-of-algorithms-performance-measurements

# Characteristics of Algorithms & Performance Measurements

20 mins

An introduction to the fundamental properties of algorithms, theoretical versus empirical analysis, and the critical balance of time-space trade-offs.

### Learning Goals

- Define an algorithm and list its 5 mandatory properties.
- Differentiate between A Priori (theoretical) and A Posteriori (empirical) performance analysis.
- Understand the definitions of Time and Space complexity as tested in the university exams.
- Explain the Time-Space trade-off with a real-world example.

---

### What is an Algorithm?

An algorithm is a step-by-step, unambiguous set of instructions designed to perform a specific task or solve a particular problem. It is the logical blueprint that exists _before_ any code is written in a programming language like C++, Java, or Python.

### The 5 Mandatory Properties of an Algorithm

To be considered a valid algorithm, a sequence of steps must satisfy these five criteria:

1. **Input:** It must accept zero or more inputs supplied externally.
2. **Output:** It must produce at least one output (the result).
3. **Definiteness:** Every instruction must be absolutely clear and unambiguous. (e.g., "Add 5 to x" is definite; "Add a small number to x" is not).
4. **Finiteness:** If we trace out the instructions, the algorithm MUST terminate after a finite number of steps. It cannot loop infinitely.
5. **Effectiveness:** Every instruction must be basic enough to be carried out, in principle, by a person with only paper and pencil in a finite amount of time.

### Performance Measurement: How do we judge an algorithm?

Once an algorithm is designed, we need to know if it's "good." There are two ways to measure performance: **A Priori** (Before coding) and **A Posteriori** (After coding).

| Feature | A Priori Analysis (Theoretical) | A Posteriori Analysis (Empirical) |
| --- | --- | --- |
| **When is it done?** | Before implementation, on the algorithm itself. | After implementation, on the compiled code. |
| **Dependency** | Independent of hardware, OS, and programming language. | Highly dependent on CPU speed, RAM, compiler, and language. |
| **Measurement Unit** | Asymptotic notation (e.g., O(n)O(n)O(n), O(n2)O(n^2)O(n2)). | Exact time (seconds) and memory (megabytes). |
| **Use Case** | Used by computer scientists to compare different algorithms' efficiency as input size grows to infinity. | Used by software engineers to profile a specific application on a specific server. |

In Design and Analysis of Algorithms (DAA), we focus almost entirely on **A Priori Analysis**.

---

### Understanding Time and Space Complexity

> **Time Complexity** It is not the actual wall-clock time required to execute a program. Instead, it is the **number of basic operations** (like assignments or comparisons) performed by the algorithm as a function of the input size nnn.

> **Space Complexity** It is the total amount of **memory** required by the algorithm to run to completion. Space complexity is divided into two components:
> 
> 1. **Fixed Part:** Memory needed for the compiled code, constant variables, and fixed-size variables. (Independent of input size nnn).
> 2. **Variable Part:** Memory needed for dynamic allocations (e.g., arrays scaled by nnn) and the recursion stack (if the algorithm calls itself).

### The Time-Space Trade-off

In computer science, you can rarely have both the fastest speed and the lowest memory usage simultaneously. You often have to sacrifice one to improve the other.

**Example: Hashing vs. Linear Search** Imagine searching for a specific user ID in a database of 1 million users.

- **Linear Search (Save Space, Waste Time):** We check one by one. It uses almost zero extra memory (O(1)O(1)O(1) space), but it might take 1 million checks (O(n)O(n)O(n) time).
- **Hash Table (Save Time, Waste Space):** We create a massive array and map IDs directly to indices. It requires allocating a huge amount of memory upfront (O(n)O(n)O(n) extra space), but finding the user takes just 1 check (O(1)O(1)O(1) time).

### Tracing Complexity: Sum of an Array

1. 1
 
 Step 1
 
 Analyze the Fixed Space
 
 We have the input array `A` (size nnn), a variable `n`, a variable `total`, and a loop counter `i`. The fixed space is 1+1+1\=31 + 1 + 1 = 31+1+1\=3 units (for `n`, `total`, `i`).
 
2. 2
 
 Step 2
 
 Analyze the Variable Space
 
 The array `A` takes nnn units of space. Since there is no recursion or dynamic memory allocation inside the loop, the variable space is exactly nnn. **Total Space Complexity:** S(n)\=n+3  ⟹  O(n)S(n) = n + 3 \\implies O(n)S(n)\=n+3⟹O(n).
 
3. 3
 
 Step 3
 
 Count the Basic Operations (Time)
 
 Line 1 (`total = 0`) executes 1 time. Line 2 (`for i = 1 to n`) checks condition n+1n+1n+1 times. Line 3 (`total = total + A[i]`) executes exactly nnn times. Line 4 (`return total`) executes 1 time.
 
4. 4
 
 Step 4
 
 Calculate Final Time Complexity
 
 Total operations = 1+(n+1)+n+1\=2n+31 + (n + 1) + n + 1 = 2n + 31+(n+1)+n+1\=2n+3. Dropping constants and lower-order terms gives us the final asymptotic bound. **Total Time Complexity:** T(n)\=O(n)T(n) = O(n)T(n)\=O(n).
 

### Knowledge Check

Question 1 of 3

Q1Single choice

Which property of an algorithm dictates that every instruction must be perfectly clear and unambiguous?

Finiteness

Definiteness

Effectiveness

Output

BackNext

[Abdul Bari: Introduction to Algorithms\\ \\ web](https://www.youtube.com/watch?v=0IAPZzGSbME)

[Next\\ \\ Asymptotic Analysis & Complexity Bounds](https://coursify.hasanraiyan.me/course/design-and-analysis-of-algorithms-daa/asymptotic-analysis-complexity-bounds)