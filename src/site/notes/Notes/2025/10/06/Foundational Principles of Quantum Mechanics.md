---
{"dg-publish":true,"permalink":"/notes/2025/10/06/foundational-principles-of-quantum-mechanics/"}
---

#quantum-mechanics #physics #foundations-of-physics
[[Foundational Principles of Quantum Mechanics.canvas\|Foundational Principles of Quantum Mechanics.canvas]]

# Foundational Principles of Quantum Mechanics

## Introduction

[[Notes/2025/10/13/Quantum Mechanics\|Quantum Mechanics]] is the fundamental theory in physics that provides a description of the physical properties of nature at the scale of atoms and subatomic particles. It represents a profound departure from classical physics, introducing concepts such as quantization, wave-particle duality, superposition, and entanglement. The foundational principles, often presented as a set of postulates, form the mathematical and conceptual bedrock upon which the entire theory is built. These principles define how a physical system is described, how its properties are measured, and how it evolves over time.

## The Postulates of Quantum Mechanics

The core of quantum mechanics can be distilled into a set of fundamental postulates that provide a recipe for constructing the theory.

### 1. The State of a System

> **Postulate 1**: The state of any isolated physical system is described by a state vector (or "ket") $|\psi\rangle$, which is a vector in a complex vector space with an inner product, known as a **Hilbert space** $\mathcal{H}$.

This state vector $|\psi\rangle$ contains all the information that can be known about the system at a given time. A key implication of this postulate is the **superposition principle**: if $|\psi_1\rangle$ and $|\psi_2\rangle$ are two possible states of a system, then any linear combination of them is also a valid state:

$$
|\psi\rangle = c_1 |\psi_1\rangle + c_2 |\psi_2\rangle
$$

where $c_1$ and $c_2$ are complex numbers. This principle is responsible for many of the most counter-intuitive quantum phenomena, including interference. The state vector is typically required to be normalized, meaning its inner product with itself is one: $\langle\psi|\psi\rangle = 1$.

### 2. Observables and Operators

> **Postulate 2**: To every measurable physical quantity $A$ (an **observable**), there corresponds a **Hermitian operator** $\hat{A}$ that acts on the state vectors in the Hilbert space $\mathcal{H}$.

A Hermitian (or self-adjoint) operator is one that is equal to its own conjugate transpose, $\hat{A} = \hat{A}^\dagger$. This property ensures that the outcomes of measurements are real numbers, as expected for physical quantities.

-   **Examples of Observables and their Operators**:
    -   Energy is associated with the **Hamiltonian operator** $\hat{H}$.
    -   Position is associated with the **position operator** $\hat{X}$.
    -   Momentum is associated with the **momentum operator** $\hat{P}$.

The possible results of a measurement of the observable $A$ are the **eigenvalues** of the operator $\hat{A}$. The eigenvalues $\{a_n\}$ are the solutions to the eigenvalue equation:

$$
\hat{A} |a_n\rangle = a_n |a_n\rangle
$$

where $|a_n\rangle$ are the corresponding **eigenvectors**.

### 3. The Measurement Process

> **Postulate 3**: The measurement of an observable $A$ on a system in the state $|\psi\rangle$ yields one of the eigenvalues $\{a_n\}$ of the corresponding operator $\hat{A}$.

This postulate is composed of two critical parts:

#### a) The Born Rule

The probability of obtaining the eigenvalue $a_n$ as the outcome of the measurement is given by the square of the magnitude of the projection of the state vector $|\psi\rangle$ onto the corresponding eigenvector $|a_n\rangle$:

$$
P(a_n) = |\langle a_n | \psi \rangle|^2
$$

This rule provides the probabilistic link between the mathematical formalism and experimental results. It is the reason quantum mechanics is fundamentally a probabilistic theory.

#### b) State Collapse (Projection Postulate)

Immediately after a measurement of $A$ that yields the result $a_n$, the state of the system "collapses" from its initial state $|\psi\rangle$ to the corresponding normalized eigenvector $|a_n\rangle$:

$$
|\psi\rangle \xrightarrow{\text{measurement of A yields } a_n} \frac{|a_n\rangle}{\sqrt{\langle a_n | a_n \rangle}}
$$

This instantaneous and non-deterministic change is one of the most debated aspects of quantum theory.

### 4. Time Evolution of a System

> **Postulate 4**: The evolution of a closed quantum system over time is described by the **Schrödinger equation**:
> $$
> i\hbar \frac{d}{dt}|\psi(t)\rangle = \hat{H}|\psi(t)\rangle
> $$

where:
-   $i$ is the imaginary unit.
-   $\hbar$ is the reduced Planck constant.
-   $|\psi(t)\rangle$ is the state vector of the system at time $t$.
-   $\hat{H}$ is the **Hamiltonian operator** of the system, corresponding to its total energy.

For a closed system, the evolution is **unitary**. This means it is deterministic and reversible. The state at a later time $t$ can be found by applying a [[Notes/2025/10/06/Unitary Operator\|Unitary Operator]] $U(t, t_0)$ to the state at an initial time $t_0$:

$$
|\psi(t)\rangle = U(t, t_0) |\psi(t_0)\rangle
$$

where $U(t, t_0) = e^{-i\hat{H}(t-t_0)/\hbar}$ for a time-independent Hamiltonian.

### 5. Composite Systems

> **Postulate 5**: The Hilbert space of a composite system is the **tensor product** of the Hilbert spaces of its individual component systems.

If a system is composed of two subsystems, 1 and 2, with Hilbert spaces $\mathcal{H}_1$ and $\mathcal{H}_2$ respectively, then the Hilbert space of the total system is $\mathcal{H} = \mathcal{H}_1 \otimes \mathcal{H}_2$.

This postulate is the mathematical foundation for **quantum entanglement**, where the state of the composite system cannot be described as a simple product of the states of its individual parts. An entangled state for a two-qubit system might look like:

$$
|\Psi\rangle = \frac{1}{\sqrt{2}}(|0\rangle_1 \otimes |1\rangle_2 - |1\rangle_1 \otimes |0\rangle_2)
$$

In such a state, measuring a property of subsystem 1 instantly influences the properties of subsystem 2, regardless of the distance separating them.

## Conclusion

The foundational principles of quantum mechanics provide a complete and consistent framework for describing the microscopic world. Although they lead to phenomena that defy classical intuition—such as superposition, probabilistic measurement outcomes, and entanglement—they have been validated by countless experiments with extraordinary precision. These postulates not only form the basis of our understanding of matter and energy but also drive the development of transformative technologies like quantum computing, quantum cryptography, and advanced materials science.
