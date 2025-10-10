---
{"dg-publish":true,"permalink":"/notes/2025/10/06/pauli-matrices/"}
---

#quantum-mechanics #linear-algebra #matrix-theory
[[Pauli Matrices.canvas\|Pauli Matrices.canvas]]

# Pauli Matrices

## 1. Introduction

The **Pauli matrices**, named after the physicist Wolfgang Pauli, are a set of three 2x2 complex matrices that are fundamental to the mathematical formulation of quantum mechanics. They are denoted by the Greek letter sigma ($\sigma$) and are often indexed as $\sigma_1, \sigma_2, \sigma_3$ or, more physically, as $\sigma_x, \sigma_y, \sigma_z$.

These matrices are indispensable for describing systems with two possible states, most notably the intrinsic angular momentum, or **spin**, of a spin-1/2 particle such as an electron, proton, or neutron. Their algebraic properties form the basis of the Lie algebra $\mathfrak{su}(2)$, which is central to the theory of angular momentum in quantum mechanics and the representation theory of the special unitary group SU(2). Beyond quantum mechanics, they find applications in quantum computing, where they represent fundamental quantum logic gates.

## 2. Mathematical Definition

The three Pauli matrices are defined as follows:

$$
\sigma_1 = \sigma_x = \begin{pmatrix} 0 & 1 \\ 1 & 0 \end{pmatrix}
$$

$$
\sigma_2 = \sigma_y = \begin{pmatrix} 0 & -i \\ i & 0 \end{pmatrix}
$$

$$
\sigma_3 = \sigma_z = \begin{pmatrix} 1 & 0 \\ 0 & -1 \end{pmatrix}
$$

where $i = \sqrt{-1}$ is the imaginary unit.

Occasionally, a fourth matrix, $\sigma_0$, is included in the set. This is simply the 2x2 identity matrix, $I$.

$$
\sigma_0 = I = \begin{pmatrix} 1 & 0 \\ 0 & 1 \end{pmatrix}
$$

## 3. Core Properties

The Pauli matrices possess a set of remarkable mathematical properties that make them uniquely suited for their role in physics.

### 3.1. Hermitian and Unitary Nature

- **Hermitian**: The Pauli matrices are **Hermitian**, meaning each matrix is equal to its own conjugate transpose ($\sigma_i^\dagger = \sigma_i$). This property is crucial because in quantum mechanics, ***operators corresponding to physical observables must be Hermitian***, *ensuring that their eigenvalues (the possible measurement outcomes) are real numbers*.
- **Unitary**: They are also **unitary**, meaning that the product of a matrix with its conjugate transpose is the identity matrix ($\sigma_i^\dagger \sigma_i = I$). Since they are Hermitian, this simplifies to $\sigma_i^2 = I$. ***Unitary operators preserve the norm of vectors***, which corresponds to the *conservation of probability in quantum mechanics*.

### 3.2. Algebraic Properties

- **Involutory**: As a direct consequence of being both Hermitian and unitary, the square of each Pauli matrix is the identity matrix:
    $$
    \sigma_1^2 = \sigma_2^2 = \sigma_3^2 = I = \begin{pmatrix} 1 & 0 \\ 0 & 1 \end{pmatrix}
    $$
- **Trace**: The trace (the sum of the diagonal elements) of each Pauli matrix is zero:
    $$
    \text{Tr}(\sigma_i) = 0 \quad \text{for } i = 1, 2, 3
    $$
- **Determinant**: The determinant of each Pauli matrix is -1:
    $$
    \det(\sigma_i) = -1 \quad \text{for } i = 1, 2, 3
    $$

### 3.3. Eigenvalues and Eigenvectors

Each Pauli matrix has the eigenvalues **+1** and **-1**. The corresponding normalized eigenvectors are:

-   For $\sigma_1 (\sigma_x)$:
    -   Eigenvalue +1: $v_{+1} = \frac{1}{\sqrt{2}} \begin{pmatrix} 1 \\ 1 \end{pmatrix}$
    -   Eigenvalue -1: $v_{-1} = \frac{1}{\sqrt{2}} \begin{pmatrix} 1 \\ -1 \end{pmatrix}$
-   For $\sigma_2 (\sigma_y)$:
    -   Eigenvalue +1: $v_{+1} = \frac{1}{\sqrt{2}} \begin{pmatrix} 1 \\ i \end{pmatrix}$
    -   Eigenvalue -1: $v_{-1} = \frac{1}{\sqrt{2}} \begin{pmatrix} 1 \\ -i \end{pmatrix}$
-   For $\sigma_3 (\sigma_z)$:
    -   Eigenvalue +1: $v_{+1} = \begin{pmatrix} 1 \\ 0 \end{pmatrix}$ (spin up)
    -   Eigenvalue -1: $v_{-1} = \begin{pmatrix} 0 \\ 1 \end{pmatrix}$ (spin down)

## 4. Fundamental Algebraic Relations

The algebraic structure of the Pauli matrices is defined by their commutation and anticommutation relations.

### 4.1. Commutation Relations

The **commutator** of two matrices, $[A, B] = AB - BA$, quantifies how they fail to commute. The Pauli matrices obey the following commutation relation:

$$
[\sigma_i, \sigma_j] = 2i \sum_{k=1}^3 \epsilon_{ijk} \sigma_k
$$

where $\epsilon_{ijk}$ is the **Levi-Civita symbol**, which is +1 for an even permutation of (1,2,3), -1 for an odd permutation, and 0 otherwise. Explicitly, this gives:

-   $[\sigma_1, \sigma_2] = 2i\sigma_3$
-   $[\sigma_2, \sigma_3] = 2i\sigma_1$
-   $[\sigma_3, \sigma_1] = 2i\sigma_2$

These relations are the defining structure of the **Lie algebra $\mathfrak{su}(2)$**.

### 4.2. Anticommutation Relations

The **anticommutator**, $\{A, B\} = AB + BA$, is also important. The Pauli matrices' anticommutation relation is:

$$
\{\sigma_i, \sigma_j\} = 2\delta_{ij}I
$$

where $\delta_{ij}$ is the **Kronecker delta**, which is 1 if $i=j$ and 0 otherwise. This relation concisely expresses that the matrices are involutory ($\sigma_i^2 = I$) and that distinct matrices anticommute ($\sigma_i \sigma_j = -\sigma_j \sigma_i$ for $i \neq j$).

### 4.3. Pauli Identity

Combining the commutation and anticommutation relations yields a powerful identity for the product of any two Pauli matrices:

$$
\sigma_i \sigma_j = \delta_{ij}I + i \sum_{k=1}^3 \epsilon_{ijk} \sigma_k
$$

This identity is extremely useful for simplifying expressions involving products of Pauli matrices.

## 5. Applications in Physics and Computing

### 5.1. Quantum Spin

The primary application of the Pauli matrices is in describing the **spin angular momentum** of a spin-1/2 particle. The spin operator $\vec{S}$ is a vector operator whose components are given by:

$$
S_i = \frac{\hbar}{2} \sigma_i
$$

where $\hbar$ is the reduced Planck constant. The components $S_x, S_y, S_z$ represent measurements of spin along the respective axes. Their eigenvalues are $\pm\frac{\hbar}{2}$, corresponding to the "spin up" and "spin down" states of the particle. The commutation relations of the spin operators, derived directly from those of the Pauli matrices, are fundamental to the theory of angular momentum.

### 5.2. Quantum Computing

In the field of quantum computing, the Pauli matrices (often denoted X, Y, and Z) are fundamental single-qubit **quantum gates**:

-   **Pauli-X Gate ($\sigma_x$)**: Acts as a quantum equivalent of the classical NOT gate, performing a bit-flip: $|0\rangle \leftrightarrow |1\rangle$.
-   **Pauli-Y Gate ($\sigma_y$)**: Performs both a bit-flip and a phase-flip.
-   **Pauli-Z Gate ($\sigma_z$)**: Acts as a phase-flip gate, leaving $|0\rangle$ unchanged and mapping $|1\rangle \to -|1\rangle$.

Together with the identity matrix $I$, the Pauli matrices form a basis for the vector space of all 2x2 Hermitian matrices. This means any single-qubit operation can be expressed as a linear combination of these matrices.

## 6. Conclusion

The Pauli matrices are far more than a mere mathematical curiosity. They provide the essential language for describing two-level quantum systems, forming a bridge between the abstract algebra of SU(2) and the concrete physical reality of particle spin. Their elegant properties—being Hermitian, unitary, and obeying specific commutation and anticommutation rules—make them a cornerstone of quantum mechanics and a fundamental tool in the burgeoning field of quantum information science. Their study offers deep insights into the mathematical structure that underpins the quantum world.

