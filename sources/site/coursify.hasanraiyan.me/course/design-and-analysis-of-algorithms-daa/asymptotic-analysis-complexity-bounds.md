# Source: https://coursify.hasanraiyan.me/course/design-and-analysis-of-algorithms-daa/asymptotic-analysis-complexity-bounds

# Asymptotic Analysis & Complexity Bounds

25 mins

Master the mathematical tools used to describe algorithm efficiency. Learn to differentiate Best, Worst, and Average cases using Linear Search, and deeply understand Big-O, Big-Omega, and Big-Theta notations.

### Learning Goals

- Differentiate between Best, Worst, and Average-case scenarios with practical examples.
- Understand why the Worst-Case analysis is the industry standard.
- Formally define and graph Big-O, Big-Omega, and Big-Theta asymptotic notations.
- Apply these notations to calculate the upper and lower bounds of polynomial functions.

---

### Understanding the Three Scenarios

When analyzing an algorithm theoretically, its performance usually depends heavily on the _nature_ of the input, not just the size. Because of this, we categorize performance into three scenarios:

1. **Best Case (Minimum Time):** The input configuration that causes the algorithm to execute the absolute minimum number of operations. It is often unrealistic and not useful for practical guarantees.
2. **Worst Case (Maximum Time):** The input configuration that forces the algorithm to execute the maximum possible number of operations. **This is the industry standard.** It provides a critical mathematical guarantee that the algorithm will _never_ take longer than this bound.
3. **Average Case (Expected Time):** The expected number of operations over all possible valid inputs, assuming a uniform probability distribution. It provides a realistic view of daily performance but is often mathematically difficult to compute.

### Tracing Scenarios: The Linear Search Example

1. 1
 
 Step 1
 
 The Algorithm Logic
 
 Start at index `0`. Compare A\[i\]A\[i\]A\[i\] to xxx. If they match, return `i`. If not, move to the next index. If the loop finishes without finding xxx, return `-1`.
 
2. 2
 
 Step 2
 
 Trace the Best Case
 
 Imagine we are searching for the number `5`, and the array is `[5, 8, 2, 9]`. The algorithm finds the target on the very first comparison. It doesn't matter if the array has 4 elements or 4 million elements; it takes exactly 1 step. **Time Complexity:** Ω(1)\\Omega(1)Ω(1) (Constant time).
 
3. 3
 
 Step 3
 
 Trace the Worst Case
 
 Imagine we are searching for the number `9`, or a number not in the array like `100`. The algorithm must check every single element in the array from start to finish. If the array size is nnn, it makes exactly nnn comparisons. **Time Complexity:** O(n)O(n)O(n) (Linear time).
 
4. 4
 
 Step 4
 
 Trace the Average Case
 
 Assuming the target xxx is somewhere in the array, on average, we will find it halfway through the array. It will take n/2n/2n/2 comparisons. In asymptotic analysis, we drop the constant 1/21/21/2. **Time Complexity:** Θ(n)\\Theta(n)Θ(n) (Linear time).
 

### The 3 Asymptotic Notations

Asymptotic notations are mathematical tools used to represent the time and space complexity of algorithms as the input size nnn approaches infinity.

#### 1\. Big-O (OOO) Notation: Asymptotic Upper Bound

Big-O describes the **worst-case** scenario. It guarantees that the function will never grow faster than a specific rate.

- **Definition:** f(n)\=O(g(n))f(n) = O(g(n))f(n)\=O(g(n)) if there exist positive constants ccc and n0n\_0n0​ such that: 0≤f(n)≤c⋅g(n)0 \\le f(n) \\le c \\cdot g(n)0≤f(n)≤c⋅g(n) for all n≥n0n \\ge n\_0n≥n0​.
- **Meaning:** f(n)f(n)f(n) is bounded _above_ by g(n)g(n)g(n).

#### 2\. Big-Omega (Ω\\OmegaΩ) Notation: Asymptotic Lower Bound

Big-Omega describes the **best-case** scenario. It guarantees that the function will take _at least_ this much time.

- **Definition:** f(n)\=Ω(g(n))f(n) = \\Omega(g(n))f(n)\=Ω(g(n)) if there exist positive constants ccc and n0n\_0n0​ such that: 0≤c⋅g(n)≤f(n)0 \\le c \\cdot g(n) \\le f(n)0≤c⋅g(n)≤f(n) for all n≥n0n \\ge n\_0n≥n0​.
- **Meaning:** f(n)f(n)f(n) is bounded _below_ by g(n)g(n)g(n).

#### 3\. Big-Theta (Θ\\ThetaΘ) Notation: Asymptotic Tight Bound

Big-Theta describes the **average-case** or exact bound. It means the algorithm grows at exactly the same rate as the bound.

- **Definition:** f(n)\=Θ(g(n))f(n) = \\Theta(g(n))f(n)\=Θ(g(n)) if there exist positive constants c1,c2c\_1, c\_2c1​,c2​, and n0n\_0n0​ such that: 0≤c1⋅g(n)≤f(n)≤c2⋅g(n)0 \\le c\_1 \\cdot g(n) \\le f(n) \\le c\_2 \\cdot g(n)0≤c1​⋅g(n)≤f(n)≤c2​⋅g(n) for all n≥n0n \\ge n\_0n≥n0​.
- **Meaning:** f(n)f(n)f(n) is sandwiched perfectly between c1⋅g(n)c\_1 \\cdot g(n)c1​⋅g(n) and c2⋅g(n)c\_2 \\cdot g(n)c2​⋅g(n).

#### Summary Table

| Notation | Name | Bound Type | Use Case | Mathematical Condition |
| --- | --- | --- | --- | --- |
| **OOO** | Big-O | Upper Bound | Worst-Case | f(n)≤c⋅g(n)f(n) \\le c \\cdot g(n)f(n)≤c⋅g(n) |
| **Ω\\OmegaΩ** | Big-Omega | Lower Bound | Best-Case | f(n)≥c⋅g(n)f(n) \\ge c \\cdot g(n)f(n)≥c⋅g(n) |
| **Θ\\ThetaΘ** | Big-Theta | Tight Bound | Average-Case | c1⋅g(n)≤f(n)≤c2⋅g(n)c\_1 \\cdot g(n) \\le f(n) \\le c\_2 \\cdot g(n)c1​⋅g(n)≤f(n)≤c2​⋅g(n) |

### Knowledge Check

Question 1 of 3

Q1Single choice

Which of the following notations is used to represent the worst-case time complexity of an algorithm?

O-notation

Ω-notation

Θ-notation

δ-notation

BackNext

[Asymptotic Notations Explained\\ \\ web](https://www.geeksforgeeks.org/analysis-of-algorithms-set-3asymptotic-notations/)

[Previous\\ \\ Characteristics of Algorithms & Performance Measurements](https://coursify.hasanraiyan.me/course/design-and-analysis-of-algorithms-daa/characteristics-of-algorithms-performance-measurements) [Next\\ \\ Complexity Analysis and Time-Space Trade-offs](https://coursify.hasanraiyan.me/course/design-and-analysis-of-algorithms-daa/complexity-analysis-and-time-space-trade-offs)