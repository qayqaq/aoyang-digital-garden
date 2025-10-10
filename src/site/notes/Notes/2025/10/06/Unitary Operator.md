---
{"dg-publish":true,"permalink":"/notes/2025/10/06/unitary-operator/"}
---

#quantum-mechanics #linear-algebra #operator-theory
[[Unitary Operator.canvas\|Unitary Operator.canvas]]

# Unitary Operator

## Introduction

In quantum mechanics and linear algebra, a **unitary operator** is a fundamental concept representing a transformation that preserves the fundamental structure of a system. Specifically, it is a bounded linear operator on a complex Hilbert space that preserves the inner product, and consequently, the length (or norm) of vectors.

The significance of unitary operators is paramount in quantum theory. They describe the **time evolution of a closed quantum system**, ensuring that the total probability of finding the system in any state remains constant (i.e., equal to one). This property of probability conservation is a cornerstone of quantum mechanics. Furthermore, unitary operators represent symmetry transformations, such as rotations and translations, and form the mathematical basis for **quantum gates** in quantum computing.

## Mathematical Definition

A linear operator $U$ acting on a Hilbert space $\mathcal{H}$ is defined as **unitary** if its adjoint, denoted $U^\dagger$, is also its inverse, $U^{-1}$. This relationship is expressed by the equation:

$$
U^\dagger U = U U^\dagger = I
$$

where:
-   $U^\dagger$ is the **Hermitian adjoint** (or conjugate transpose) of $U$.
-   $I$ is the **identity operator**, which leaves any vector unchanged.

This definition implies that applying a unitary operator is a reversible process; its inverse $U^\dagger$ can perfectly undo the transformation.

## Core Properties of Unitary Operators

The defining equation of a unitary operator gives rise to several crucial properties that are essential for its physical interpretation.

### 1. Preservation of the Inner Product

The most fundamental property of a unitary operator is that it preserves the inner product between any two vectors (states) $|\psi\rangle$ and $|\phi\rangle$ in the Hilbert space.

> If we transform both vectors by $U$, their inner product remains unchanged:
> $$
> \langle U\psi | U\phi \rangle = \langle \psi | U^\dagger U | \phi \rangle = \langle \psi | I | \phi \rangle = \langle \psi | \phi \rangle
> $$

This property ensures that the geometric relationships (i.e., the "angles") between quantum states are maintained under unitary evolution.

### 2. Preservation of the Norm

A direct consequence of preserving the inner product is the preservation of the norm (length) of any vector. The squared norm of a vector $|\psi\rangle$ is given by $\langle\psi|\psi\rangle$. For a transformed vector $U|\psi\rangle$, the norm is:

$$
||U\psi||^2 = \langle U\psi | U\psi \rangle = \langle \psi | \psi \rangle = ||\psi||^2
$$

In quantum mechanics, the squared norm of a state vector represents the total probability of the system. The preservation of the norm thus guarantees the **conservation of probability**, a physical necessity. If a state is normalized ($||\psi||=1$), any state evolved under a unitary operator will also be normalized.

### 3. Eigenvalues and Eigenvectors

The eigenvalues of a unitary operator are complex numbers that must have a magnitude of 1.
If $|\lambda\rangle$ is an eigenvector of $U$ with eigenvalue $\lambda$, then $U|\lambda\rangle = \lambda|\lambda\rangle$. Using the norm-preserving property:

$$
\langle \lambda | \lambda \rangle = \langle U\lambda | U\lambda \rangle = \langle \lambda | U^\dagger U | \lambda \rangle = \langle \lambda | (\lambda^* \lambda) | \lambda \rangle = |\lambda|^2 \langle \lambda | \lambda \rangle
$$

This implies that $|\lambda|^2 = 1$. Therefore, any eigenvalue $\lambda$ can be written in the form $e^{i\theta}$ for some real number $\theta$.

## Role in Quantum Mechanics

Unitary operators are not just mathematical abstractions; they are central to the physical description of the quantum world.

### Time Evolution of Closed Systems

The evolution of a quantum state $|\psi(t)\rangle$ over time is governed by the **Schrödinger equation**. For a closed system with a time-independent Hamiltonian $H$, the solution can be expressed using a unitary time-evolution operator, $U(t)$:

$$
|\psi(t)\rangle = U(t) |\psi(t_0)\rangle
$$

This operator is defined by the exponential of the Hamiltonian:

$$
U(t) = e^{-iHt/\hbar}
$$

Here, $H$ is a **Hermitian operator** corresponding to the total energy of the system, and $\hbar$ is the reduced Planck constant. The exponential of an anti-Hermitian operator (like $-iH$) is always unitary, ensuring that the evolution it describes is physically valid (i.e., conserves probability).

### Symmetry Transformations

Symmetries play a crucial role in physics, as they are linked to conservation laws (by Noether's theorem). In quantum mechanics, symmetry operations—such as spatial translation, rotation, or parity inversion—are represented by unitary operators. For example:
-   The **translation operator** shifts the position of a system. Its unitarity ensures that the laws of physics are the same everywhere.
-   The **rotation operator** changes the orientation of a system. Its unitarity ensures that physics is independent of direction.

### Quantum Gates in Quantum Computing

In the field of quantum computing, computations are performed by applying a sequence of **quantum gates** to a register of qubits. Each quantum gate must be a unitary transformation. This is because quantum computation must be reversible to prevent information loss and maintain the coherence of the quantum state.

**Examples of Unitary Gates:**
-   **Pauli-X Gate (NOT Gate)**:
    $$
    X = \begin{pmatrix} 0 & 1 \\ 1 & 0 \end{pmatrix}, \quad X^\dagger X = I
    $$
-   **Hadamard Gate**:
    $$
    H = \frac{1}{\sqrt{2}} \begin{pmatrix} 1 & 1 \\ 1 & -1 \end{pmatrix}, \quad H^\dagger H = I
    $$

## Distinction from Non-Unitary Operators

While unitary evolution describes idealized, closed systems, real-world quantum systems are often **open**—they interact with an external environment. Such interactions lead to processes like decoherence and dissipation, which cannot be described by unitary operators alone.

The evolution of open quantum systems is described by a more general class of transformations known as **quantum channels** or **quantum operations**. These are represented by [[Notes/2025/10/06/Kraus Operator\|Kraus Operator]]s in an operator-sum representation. While these transformations must preserve the trace of the density matrix (a generalization of probability conservation), the evolution of a pure state is not necessarily unitary.

## Conclusion

The unitary operator is a cornerstone of quantum theory, providing the mathematical framework for describing change in a manner consistent with the fundamental principles of physics. Its defining property—the preservation of the inner product—guarantees the conservation of probability, making it the unique descriptor for the deterministic and reversible evolution of isolated quantum systems. From the continuous flow of time governed by the Schrödinger equation to the discrete operations of a quantum computer, unitary transformations are the language of quantum dynamics.
