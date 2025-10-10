---
{"dg-publish":true,"permalink":"/notes/2025/10/06/density-matrix/"}
---

#QuantumMechanics #StatisticalMechanics #Physics

[[Density Matrix.canvas\|Density Matrix.canvas]]

# Density Matrix

## Introduction

In quantum mechanics, the **density matrix**, or **density operator**, is a mathematical tool used to describe the state of a quantum system. While a state vector (or "ket") $|\psi\rangle$ provides a complete description of a system in a **pure state**, it is insufficient for systems whose state is not perfectly known. The density matrix formalism generalizes the concept of a quantum state to include **mixed states**, which are statistical ensembles of pure states. This makes it an indispensable tool in quantum statistical mechanics, quantum information theory, and the study of open quantum systems that interact with an environment.

The density matrix, typically denoted by $\rho$, provides a unified framework for describing any quantum state, whether pure or mixed, and allows for the calculation of observable properties in a consistent manner.

## Mathematical Formulation

The construction of the density matrix depends on whether the system is in a pure state or a mixed state.

### Pure States

For a quantum system in a known pure state described by the normalized state vector $|\psi\rangle$, the density matrix is defined as the outer product of the state vector with itself:

$$
\rho = |\psi\rangle\langle\psi|
$$

In this case, the density matrix is a projection operator onto the state $|\psi\rangle$. All the information contained in the state vector is also contained in its corresponding density matrix.

**Example**: A qubit in the state $|\psi\rangle = \alpha|0\rangle + \beta|1\rangle$ has the density matrix:
$$
\rho = \begin{pmatrix} \alpha \\ \beta \end{pmatrix} \begin{pmatrix} \alpha^* & \beta^* \end{pmatrix} = \begin{pmatrix} |\alpha|^2 & \alpha\beta^* \\ \beta\alpha^* & |\beta|^2 \end{pmatrix}
$$

### Mixed States

A **mixed state** arises when there is classical uncertainty about the quantum state of a system. It is described as a statistical ensemble, where the system has a classical probability $p_i$ of being in the pure state $|\psi_i\rangle$. The density matrix for such a mixed state is the weighted average of the projection operators for each pure state in the ensemble:

$$
\rho = \sum_i p_i |\psi_i\rangle\langle\psi_i|
$$

The coefficients $p_i$ are real, non-negative probabilities that must sum to one: $\sum_i p_i = 1$.

**Example**: Consider a qubit that has a 50% probability of being in state $|0\rangle$ and a 50% probability of being in state $|1\rangle$. This is a mixed state. Its density matrix is:
$$
\rho = \frac{1}{2}|0\rangle\langle0| + \frac{1}{2}|1\rangle\langle1| = \frac{1}{2}\begin{pmatrix} 1 & 0 \\ 0 & 0 \end{pmatrix} + \frac{1}{2}\begin{pmatrix} 0 & 0 \\ 0 & 1 \end{pmatrix} = \begin{pmatrix} 1/2 & 0 \\ 0 & 1/2 \end{pmatrix} = \frac{1}{2}I
$$
This is known as the **maximally mixed state**, as it represents a state of complete ignorance about the qubit's orientation.

## Properties of the Density Matrix

Any valid density matrix $\rho$ must satisfy three fundamental properties:

1.  **Hermiticity**: The density matrix is a Hermitian operator, meaning it is equal to its own conjugate transpose ($\rho = \rho^\dagger$). This ensures that its eigenvalues are real, which is necessary as they can be interpreted as probabilities.
2.  **Positive Semi-Definiteness**: The density matrix is a positive semi-definite operator. This means that for any state vector $|\phi\rangle$, the expectation value $\langle\phi|\rho|\phi\rangle \ge 0$. This ensures that its eigenvalues are non-negative.
3.  **Trace Condition**: The trace of the density matrix is equal to one ($\text{Tr}(\rho) = 1$). The trace is the sum of the diagonal elements of the matrix, which is also the sum of its eigenvalues. This property is the quantum mechanical equivalent of the statement that the sum of all probabilities must be one.

## Distinguishing Pure and Mixed States

The density matrix formalism provides a simple and elegant criterion to distinguish between pure and mixed states using the concept of **purity**. The purity of a state is defined as the trace of the square of its density matrix, $\text{Tr}(\rho^2)$.

-   For a **pure state**, the purity is exactly 1:
    $$
    \text{Tr}(\rho^2) = 1
    $$
    *Proof*: If $\rho = |\psi\rangle\langle\psi|$, then $\rho^2 = (|\psi\rangle\langle\psi|)(|\psi\rangle\langle\psi|) = |\psi\rangle(\langle\psi|\psi\rangle)\langle\psi| = |\psi\rangle\langle\psi| = \rho$. Therefore, $\text{Tr}(\rho^2) = \text{Tr}(\rho) = 1$.

-   For a **mixed state**, the purity is strictly less than 1:
    $$
    \text{Tr}(\rho^2) < 1
    $$
    The minimum purity is $1/d$ for a maximally mixed state in a $d$-dimensional Hilbert space.

## Applications and Physical Interpretation

### Calculating Expectation Values

The density matrix provides a general formula for calculating the expectation value of any observable, represented by an operator $A$. For a system described by the density matrix $\rho$, the expectation value of $A$ is:

$$
\langle A \rangle = \text{Tr}(\rho A)
$$

This formula correctly reduces to the familiar form $\langle A \rangle = \langle\psi|A|\psi\rangle$ for a pure state.

### Time Evolution: The Liouville-von Neumann Equation

For a closed quantum system, the time evolution of the density matrix is governed by the **Liouville-von Neumann equation**, which is the generalization of the Schrödinger equation:

$$
i\hbar \frac{d\rho}{dt} = [H, \rho] = H\rho - \rho H
$$

Here, $H$ is the Hamiltonian operator of the system and $[H, \rho]$ is the commutator. This equation describes the unitary evolution of the system. For open systems interacting with an environment, more complex master equations are required.

### Describing Subsystems and Entanglement

One of the most powerful applications of the density matrix is in describing subsystems of a larger composite system. If a composite system AB is in a pure entangled state, the state of subsystem A alone cannot be described by a state vector; it is necessarily in a mixed state.

To find the state of subsystem A, one computes the **reduced density matrix** $\rho_A$ by taking the **partial trace** over subsystem B:

$$
\rho_A = \text{Tr}_B(\rho_{AB})
$$

This operation effectively "traces out" or averages over the degrees of freedom of subsystem B, leaving a complete description of subsystem A. The fact that a pure entangled state of a global system leads to mixed states for its local subsystems is a defining characteristic of quantum entanglement.

## Conclusion

The density matrix is a fundamental and powerful concept in quantum mechanics that generalizes the state vector description. It provides a unified mathematical framework for handling both pure states and the statistical ensembles known as mixed states. Its utility is essential for understanding quantum statistical mechanics, the dynamics of open quantum systems, and the nature of entanglement. By allowing us to describe systems with incomplete information and to analyze the properties of subsystems, the density matrix serves as a cornerstone of modern quantum theory and its applications.
