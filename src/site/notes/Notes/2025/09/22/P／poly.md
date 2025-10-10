---
{"dg-publish":true,"permalink":"/notes/2025/09/22/p-poly/"}
---

#computational-complexity #complexity-theory #P-poly #non-uniform-computation
[[P／poly.canvas\|P／poly.canvas]]

# P/poly: Polynomial Time with Advice

## 1. Introduction

In [[Notes/2025/09/21/Computational Complexity\|computational complexity]] theory, **P/poly** (pronounced "P slash poly") is a fundamental complexity class that captures the power of efficient computation augmented with a piece of extra information, known as an "***advice string***." Formally, it is the class of decision problems that can be solved by a polynomial-time algorithm that has access to a polynomial-sized advice string, where **the advice depends only on the *length* of the input, not the input itself**.

The introduction of "advice" makes P/poly a **non-uniform** model of computation, distinguishing it from uniform classes like **P** and **NP**, where a single algorithm must work for all possible input lengths. This class is crucial for understanding the boundary between ***feasible and infeasible computation*** and has profound connections to circuit complexity, cryptography, and the theoretical foundations of machine learning.

## 2. Formal Definition

A language $L$ (a set of strings representing a decision problem) is in **P/poly** if there exists a [[Notes/2025/09/22/polynomial-time Turing machine\|polynomial-time Turing machine]] $M$ and a sequence of advice strings $A = \{a_0, a_1, a_2, \dots\}$, one for each possible input length, satisfying two conditions:

1. **Polynomial-Time Decidability**: For any input string $x$ of length $n$, the machine $M$ can correctly decide if $x \in L$ in time polynomial in $n$, given the advice string $a_n$. That is, $x \in L \iff M(x, a_n)$ accepts.
2. **Polynomial-Sized Advice**: The length of the advice string for inputs of length $n$, denoted $|a_n|$, is bounded by a polynomial in $n$. That is, there exists a polynomial $p$ such that $|a_n| \le p(n)$ for all $n \ge 0$.

### Key Components

- **The Algorithm ($M$)**: This is the **uniform** part of the model. It's a standard algorithm that runs efficiently (in polynomial time).
- **The Advice Sequence ($A$)**: This is the **non-uniform** part. The advice $a_n$ is a pre-computed "cheat sheet" tailored specifically for all inputs of length $n$. The definition of P/poly places no restriction on how the advice sequence is generated; it could be the result of an infinitely long or even uncomputable process. We only care that it *exists* and is not too long.

> **Analogy: The Expert Consultant**
> Imagine you have a very fast computer (the polynomial-time machine $M$) tasked with solving a class of problems. For each problem size (e.g., "all 50x50 matrices"), you are allowed to consult an expert who provides a single, concise summary (the advice string $a_{50}$). This summary is the same for all 50x50 matrices. With this summary, your computer can quickly solve any specific problem of that size. The expert might have spent years (or an eternity) preparing this summary, but that preparation time doesn't count against your computer's runtime.

## 3. Relationship with Other Complexity Classes

P/poly's position in the landscape of complexity classes reveals its unique power and limitations.

### P $\subseteq$ P/poly

The class **P** consists of problems solvable in polynomial time without any help. This is a subset of P/poly because any algorithm in **P** can be seen as a P/poly algorithm that simply ignores the advice string (or uses an empty advice string for all lengths).

### P/poly Contains Undecidable Languages

This is perhaps the most surprising property of P/poly. ***It can solve problems that are provably unsolvable by any standard algorithm (i.e., undecidable problems).***

**Example**: Consider an undecidable language $L_{halt}$ that contains a single string for each length $n$ if a specific [[Notes/2025/09/22/Turing machine\|Turing machine]] $M_n$ halts, and is empty otherwise. We can construct an advice string $a_n$ for each length $n$:
- If $L_{halt}$ contains a string of length $n$, let $a_n$ be that string.
- Otherwise, let $a_n$ be a special symbol indicating "no string."

A polynomial-time machine can then decide the language by simply checking if the input $x$ matches the advice string $a_{|x|}$. Since the advice exists (even if we can't compute it), this language is in P/poly. This demonstrates that P/poly is a significantly larger and more powerful class than **P**.

### Relationship with NP and the Polynomial Hierarchy

The relationship between **NP** and P/poly is a central open question in complexity theory.

- It is widely believed that **NP is not a subset of P/poly** ($NP \not\subseteq P/poly$).
- **The Karp-Lipton Theorem** provides strong evidence for this belief. It states that if $NP \subseteq P/poly$, then the **polynomial hierarchy collapses** to its second level ($\Sigma_2^p = \Pi_2^p$). Such a collapse is considered highly unlikely and would dramatically change our understanding of computational complexity.
- This assumption, $NP \not\subseteq P/poly$, is a cornerstone of modern complexity theory and is used to prove the limitations of certain computational models, as seen in the paper [[Notes/Arxiv/Limitations of Autoregressive Models and Their Alternatives (2010.11939v3)\|Limitations of Autoregressive Models and Their Alternatives (2010.11939v3)]].

## 4. P/poly and Non-Uniform Computation Models

P/poly is often defined in terms of two other equivalent models of non-uniform computation.

### Boolean Circuits

A language is in P/poly if and only if it can be decided by a family of **polynomial-sized Boolean circuits**. For each input length $n$, there exists a logic circuit $C_n$ with a number of gates polynomial in $n$. The circuit $C_n$ takes an $n$-bit input and outputs 1 if the input is in the language and 0 otherwise. The non-uniformity comes from the fact that there is a different, potentially unrelated, circuit for each input length.

### Machine Learning Models

The P/poly class provides a powerful lens for analyzing the theoretical capabilities of machine learning models.

> As stated in [[Notes/Arxiv/Limitations of Autoregressive Models and Their Alternatives (2010.11939v3)\|Limitations of Autoregressive Models and Their Alternatives (2010.11939v3)]], "The extra power of P/poly comes from its access to compact advice strings that do not have to be recursively enumerable, let alone efficient to find. This corresponds to statistical modeling, where the trained model has a computationally efficient architecture plus access to parameters that might have taken a long time to find."

- **Model Architecture as the TM ($M$)**: The architecture of a neural network (e.g., Transformer, RNN) defines the fixed, efficient computational procedure.
- **Learned Weights as the Advice ($\theta_n$)**: The training process finds a set of parameters (weights) $\theta_n$ that work well for inputs of a certain size. These weights are the "advice." The training itself can be extremely slow or even theoretically uncomputable, but once found, inference using these weights is fast.
- A model family where the parameter size $|\theta_n|$ grows polynomially with input length $n$ corresponds directly to the P/poly model.

## 5. Conclusion

**P/poly** represents a crucial theoretical concept that extends the notion of efficient computation to non-uniform settings. By allowing a polynomial-sized "advice string" for each input length, it captures the power of pre-computation and provides a formal link between uniform algorithms, Boolean circuits, and modern machine learning models.

Its key takeaways are:
- It formalizes **efficient computation with external help**.
- It is a **non-uniform** class, with a different "strategy" (advice) for each input size.
- It is strictly more powerful than **P**, even containing undecidable problems.
- The widely held belief that $NP \not\subseteq P/poly$ is a foundational assumption in complexity theory, with significant implications for cryptography and algorithm design.

Understanding P/poly is essential for appreciating the subtle but profound differences between what is computable in principle and what is feasibly computable in practice.
