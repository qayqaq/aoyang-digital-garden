---
{"dg-publish":true,"permalink":"/notes/2025/09/22/knapsack-problem/"}
---

#combinatorial-optimization #np-complete #dynamic-programming #algorithms

[[Algorithms and Data Structures.canvas\|Algorithms and Data Structures.canvas]]

# Knapsack Problem

## 1. Introduction

The **Knapsack Problem** is a classic and fundamental problem in combinatorial optimization. It poses a simple, intuitive question: Given a set of items, each with a specific weight and a corresponding value, how do you determine the number of each item to include in a collection so that the total weight is less than or equal to a given limit and the total value is as large as possible?

The problem's name derives from the analogy of a hiker with a knapsack of a fixed size (or weight capacity) who must fill it with the most valuable items. It serves as a cornerstone for teaching and understanding key concepts in algorithm design and computational complexity, particularly **dynamic programming** and the theory of **[[Notes/2025/09/21/NP-Complete\|NP-completeness]]**.

## 2. Problem Formulation and Variations

While the core idea is simple, the Knapsack Problem has several variations, each with different constraints and solution methods.

### 2.1 The 0/1 Knapsack Problem

This is the most common version of the problem. For each item, you have only two choices: either take it or leave it. You cannot take a fraction of an item or multiple copies of the same item.

**Formal Definition:**
Given $n$ items, let:
-   $v_i$ be the value of the $i$-th item.
-   $w_i$ be the weight of the $i$-th item.
-   $W$ be the maximum weight capacity of the knapsack.

The goal is to choose a subset of items, represented by a binary variable $x_i \in \{0, 1\}$, to maximize the total value.

$$
\text{Maximize } \sum_{i=1}^{n} v_i x_i
$$

Subject to the constraint:

$$
\sum_{i=1}^{n} w_i x_i \le W
$$

### 2.2 Other Common Variations

-   **Bounded Knapsack Problem**: Each item $i$ has a limited quantity, $c_i$, that can be included in the knapsack. The decision variable $x_i$ can be an integer from $0$ to $c_i$.
-   **Unbounded Knapsack Problem**: There is an unlimited supply of each item. You can take as many copies of an item as you wish, as long as the total weight does not exceed the capacity.
-   **Fractional Knapsack Problem**: It is permissible to take fractions of items. This variation is significantly easier to solve and can be solved efficiently using a greedy approach.

## 3. Computational Complexity

The 0/1 Knapsack Problem is a classic example of an **NP-hard** problem.

-   **NP (Nondeterministic Polynomial-Time)**: This means that if someone gives you a proposed solution (a subset of items), you can *verify* in polynomial time whether it is valid (i.e., the total weight is within the limit) and calculate its total value.
-   **[[Notes/2025/09/21/NP-Hard\|NP-hard]]**: This means that there is no known algorithm that can find the optimal solution in polynomial time in the worst case. The time required by the best-known algorithms grows exponentially with the number of items ($n$).

The difficulty arises from the combinatorial nature of the problem. With $n$ items, there are $2^n$ possible subsets to choose from. A brute-force approach that checks every single subset is computationally infeasible for even a moderate number of items (e.g., $n=60$).

As illustrated in [[Notes/Arxiv/Limitations of Autoregressive Models and Their Alternatives (2010.11939v3)\|Limitations of Autoregressive Models and Their Alternatives (2010.11939v3)]], the Knapsack Problem exemplifies a class of problems where solutions are **hard to find but easy to check**.

## 4. Solution Approaches

### 4.1 Brute-Force Search

The most straightforward approach is to generate all $2^n$ subsets of items, calculate the total weight and value for each subset that respects the capacity constraint, and then select the one with the maximum value.
-   **Time Complexity**: $O(2^n n)$, which is highly inefficient.

### 4.2 Greedy Algorithm (for Fractional Knapsack)

A greedy strategy involves making the locally optimal choice at each step. For the Knapsack Problem, an intuitive greedy approach is to prioritize items that offer the most value per unit of weight.

1.  Calculate the value-to-weight ratio, $v_i / w_i$, for each item.
2.  Sort the items in descending order based on this ratio.
3.  Pack items into the knapsack in this order until the knapsack is full.

> **Important Note**: This greedy approach guarantees an optimal solution for the **Fractional Knapsack Problem**. However, it **does not** work for the 0/1 Knapsack Problem, as the locally optimal choice of taking the item with the highest value density may prevent the selection of other items that would lead to a better overall solution.

### 4.3 Dynamic Programming (for 0/1 Knapsack)

The standard and most efficient method for solving the 0/1 Knapsack Problem is **dynamic programming**. This approach breaks the problem down into a series of smaller, overlapping subproblems and builds up a solution from the bottom up.

**The Subproblem:**
Let `dp[i][w]` be the maximum value that can be achieved using a subset of the first `i` items (from 1 to `i`) with a knapsack of capacity `w`.

**The Recurrence Relation:**
For each item `i`, we have two choices:
1.  **Do not include item `i`**: In this case, the maximum value is the same as the maximum value achievable with the first `i-1` items and the same capacity `w`. The value is `dp[i-1][w]`.
2.  **Include item `i`** (only if its weight $w_i \le w$): In this case, the value is the value of item `i` ($v_i$) plus the maximum value achievable with the first `i-1` items and the remaining capacity `w - w_i`. The value is $v_i + \text{dp}[i-1][w - w_i]$.

We take the maximum of these two choices:
$$
\text{dp}[i][w] = \max(\text{dp}[i-1][w], v_i + \text{dp}[i-1][w - w_i])
$$

**Complexity:**
This approach requires building a table of size $n \times W$.
-   **Time Complexity**: $O(nW)$
-   **Space Complexity**: $O(nW)$ (can be optimized to $O(W)$)

This is a **pseudo-polynomial time** algorithm. Its runtime is polynomial in the number of items $n$ and the *numeric value* of the capacity $W$, but it is exponential in the *length of the input* used to represent $W$ (i.e., $\log W$). If $W$ is extremely large, this method becomes impractical.

## 5. Applications

The Knapsack Problem, despite its abstract formulation, models a wide range of real-world resource allocation problems, including:
-   **Finance**: Selecting investments for a portfolio to maximize returns without exceeding a risk budget.
-   **Logistics**: Deciding which items to load onto a cargo plane or truck to maximize profit without exceeding weight limits.
-   **Resource Allocation**: Assigning tasks to a processor or projects to a team to maximize output given limited time or budget.
-   **Cutting Stock**: Determining how to cut raw materials into smaller pieces to minimize waste.

## 6. Conclusion

The Knapsack Problem is a cornerstone of algorithm theory and combinatorial optimization. Its 0/1 variant is a classic NP-hard problem, beautifully illustrating the divide between problems that are easy to solve (P) and those that are hard to solve but easy to verify (NP). While a brute-force solution is infeasible, the dynamic programming approach provides an elegant and efficient pseudo-polynomial time solution, making it a powerful tool for solving practical optimization problems where constraints are reasonably bounded.

