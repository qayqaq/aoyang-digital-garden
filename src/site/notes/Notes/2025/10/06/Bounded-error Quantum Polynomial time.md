---
{"dg-publish":true,"permalink":"/notes/2025/10/06/bounded-error-quantum-polynomial-time/"}
---

#ComplexityTheory #QuantumComputing #ComputerScience

[[Bounded-error Quantum Polynomial time.canvas\|Bounded-error Quantum Polynomial time.canvas]]

# Bounded-error Quantum Polynomial time (BQP)

## Introduction

In the field of computational complexity theory, **Bounded-error Quantum Polynomial time (BQP)** is the fundamental complexity class that captures the power of an ideal quantum computer. It represents the set of all **decision problems** that can be solved by a quantum algorithm in a number of steps that is a polynomial function of the input size, with a high probability of producing the correct answer.

BQP is the quantum analogue of the classical complexity class **BPP (Bounded-error Probabilistic Polynomial time)**. Just as BPP is considered the class of problems that are "efficiently solvable" by a classical probabilistic computer, BQP represents the class of problems considered "efficiently solvable" by a quantum computer. The study of BQP and its relationship to classical complexity classes is central to understanding the potential for **quantum advantage**—the ability of quantum computers to solve problems that are intractable for even the most powerful classical supercomputers.

## Formal Definition

A decision problem (a problem with a "yes" or "no" answer) is in the complexity class BQP if there exists a quantum algorithm, represented by a uniform family of quantum circuits, that solves it with the following properties:

1.  **Polynomial Time**: The quantum circuit for an input of size $n$ consists of a number of elementary quantum gates that is bounded by a polynomial in $n$.
2.  **Bounded Error Probability**: The algorithm's output is correct with a high probability. Specifically, there is a constant $\epsilon > 0$ such that:
    *   **Completeness**: If the correct answer is "YES" (the input string is in the language), the algorithm outputs 1 with a probability of at least $\frac{1}{2} + \epsilon$.
    *   **Soundness**: If the correct answer is "NO" (the input string is not in the language), the algorithm outputs 1 with a probability of at most $\frac{1}{2} - \epsilon$.

By convention, the probability bounds are often set to $2/3$ and $1/3$:
-   If the answer is YES, the probability of measuring 1 is $P(1) \ge 2/3$.
-   If the answer is NO, the probability of measuring 1 is $P(1) \le 1/3$.

> The specific choice of $2/3$ and $1/3$ is arbitrary. Any pair of constants $c$ and $s$ such that $0 \le s < c \le 1$ and the gap $c-s$ is separated from zero by an inverse polynomial would suffice. The error can be reduced to an arbitrarily small value through a process called probability amplification.

### Probability Amplification

A key feature of BQP (and BPP) is that the error probability can be made exponentially small without a significant increase in computational cost. This is achieved by running the quantum algorithm $k$ times and taking the majority vote of the outcomes.

By using a mathematical tool called the **Chernoff bound**, it can be shown that running the algorithm a polynomial number of times, e.g., $k = \text{poly}(n)$, reduces the probability of a majority error to a value that is exponentially small, such as $2^{-n}$. This makes BQP a robust and practical class for computation, as the confidence in the result can be made arbitrarily high with only a polynomial overhead.

## Relationship with Other Complexity Classes

Understanding where BQP sits in the landscape of complexity classes is crucial for appreciating the power of quantum computation.

![Complexity Class Diagram](https://upload.wikimedia.org/wikipedia/commons/thumb/8/88/BQP_complexity_class_diagram.svg/500px-BQP_complexity_class_diagram.svg.png)

-   **P $\subseteq$ BQP**: Any problem that can be solved efficiently by a deterministic classical computer can also be solved efficiently by a quantum computer. A quantum computer can simply execute the classical algorithm without using superposition or entanglement.

-   **BPP $\subseteq$ BQP**: Any problem that can be solved efficiently by a probabilistic classical computer can also be solved efficiently by a quantum computer. A quantum computer can simulate classical randomness, for example, by applying a Hadamard gate to a qubit in the $|0\rangle$ state to generate a random bit.

-   **BQP $\subseteq$ PSPACE**: Any problem in BQP can be solved by a classical computer using a polynomial amount of memory (but potentially exponential time). A classical simulation of an $n$-qubit quantum circuit requires tracking the complex amplitudes of all $2^n$ basis states. While this takes exponential time, calculating the final probability of a specific outcome can be done by summing over all computational paths, which can be implemented in polynomial space.

### The Major Open Questions

The precise relationship between BQP and major classical classes like **NP** remains one of the most significant open questions in computer science.

-   **Is P = BQP?** It is widely conjectured that **P $\neq$ BQP**, meaning that quantum computers are strictly more powerful than their classical counterparts. The existence of algorithms like Shor's algorithm provides strong evidence for this separation.

-   **Is NP $\subseteq$ BQP?** It is generally believed that **NP is not contained in BQP**. This implies that quantum computers are not expected to be able to solve all NP-complete problems (like the traveling salesman problem or 3-SAT) in polynomial time. While Grover's search algorithm provides a quadratic speedup for unstructured search problems, this is not enough to make the exponential complexity of NP-complete problems polynomial.

## Key Problems in BQP

The most compelling evidence for the power of quantum computers comes from problems that are known to be in BQP but are not known to be in BPP.

1.  **Integer Factorization**: Given a large integer, find its prime factors. **Shor's algorithm** solves this problem in polynomial time. The best-known classical algorithms are super-polynomial. The presumed difficulty of this problem is the foundation of modern cryptography (e.g., RSA).

2.  **Discrete Logarithm Problem**: Also solved efficiently by a variant of Shor's algorithm. This problem also underlies several cryptographic systems.

3.  **Quantum Simulation**: Simulating the time evolution of a quantum mechanical system. This was the original motivation for quantum computers proposed by Richard Feynman. It is believed to be hard for classical computers because the complexity of the system grows exponentially with the number of particles. This has major applications in materials science, drug discovery, and fundamental physics.

## Conclusion

BQP is the complexity class that formally defines the computational power of a quantum computer. It contains all the problems that classical computers can solve efficiently (P and BPP) and is itself contained within the classical class PSPACE. The existence of problems like integer factorization, which are in BQP but are believed to be outside BPP, provides strong theoretical evidence that quantum computers can offer a profound computational advantage. The ultimate goal of experimental quantum computing is to build fault-tolerant devices capable of solving these BQP-complete problems, thereby unlocking solutions to some of the most challenging problems in science and technology.

