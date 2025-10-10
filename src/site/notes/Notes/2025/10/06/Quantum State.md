---
{"dg-publish":true,"permalink":"/notes/2025/10/06/quantum-state/"}
---

#QuantumMechanics #QuantumComputing #Physics

[[Quantum State.canvas\|Quantum State.canvas]]

# Quantum State

## Introduction

In the realm of quantum mechanics, the **quantum state** is the central mathematical object used to provide a complete description of a physical system. Unlike in classical mechanics, where a system's state is defined by precise values of position and momentum, a quantum state encapsulates all the information about a system's properties, which are often probabilistic in nature. The state contains the probabilities for all possible outcomes of any measurement that could be performed on the system. Understanding the quantum state is fundamental to grasping the principles of superposition, entanglement, and quantum computation.

## Mathematical Formalism of a Quantum State

The description of a quantum state is rooted in the mathematics of linear algebra, specifically within the framework of Hilbert spaces.

### State Vectors and Hilbert Space

A quantum state is represented by a **state vector** in a complex vector space known as a **Hilbert space**. This vector contains all the knowable information about the quantum system.

- **Dirac Notation**: For convenience, state vectors are typically written using **Dirac notation**, or bra-ket notation. A state vector is denoted by a "ket," $|\psi\rangle$.
- **Hilbert Space ($\mathcal{H}$)**: This is an abstract vector space where the state vectors "live." The dimensionality of the Hilbert space is determined by the number of distinct, measurable outcomes of the system. For example, the spin of an electron, which can be measured as "up" or "down," is described by a two-dimensional Hilbert space.

### The Superposition Principle

One of the most counter-intuitive yet [[Notes/2025/10/06/Foundational Principles of Quantum Mechanics\|Foundational Principles of Quantum Mechanics]] is **superposition**. This principle states that if a quantum system can exist in multiple states, it can also exist in any linear combination of those states simultaneously.

A general quantum state $|\psi\rangle$ can be expressed as a superposition of a set of **basis states** $\{|\phi_1\rangle, |\phi_2\rangle, \dots, |\phi_n\rangle\}$:

$$
|\psi\rangle = c_1|\phi_1\rangle + c_2|\phi_2\rangle + \dots + c_n|\phi_n\rangle = \sum_{i=1}^{n} c_i|\phi_i\rangle
$$

- The basis states, $|\phi_i\rangle$, represent the possible outcomes of a measurement (e.g., spin up and spin down).
- The coefficients, $c_i$, are complex numbers called **probability amplitudes**.

The square of the absolute value of a probability amplitude, $|c_i|^2$, gives the probability of measuring the system and finding it in the corresponding basis state $|\phi_i\rangle$.

### Normalization

Since the sum of probabilities for all possible outcomes must equal 1, the state vector must be normalized. This leads to the **normalization condition**:

$$
\sum_{i=1}^{n} |c_i|^2 = 1
$$

In Dirac notation, this is expressed using the inner product of the state with itself. The "bra" $\langle\psi|$ is the conjugate transpose of the ket $|\psi\rangle$. The normalization condition is therefore $\langle\psi|\psi\rangle = 1$.

## Types of Quantum States

Quantum states can be broadly classified into two categories, depending on the completeness of our knowledge about the system.

### Pure States

A **pure state** is a quantum state that is known with certainty. It can be described by a single state vector $|\psi\rangle$. A system in a pure state represents a scenario where we have the maximum possible information allowed by quantum mechanics. For example, a qubit prepared definitively in the state $|\psi\rangle = \frac{1}{\sqrt{2}}(|0\rangle + |1\rangle)$ is in a pure state.

### Mixed States

A **[[Notes/2025/10/06/Mixed State\|Mixed State]]** represents a statistical ensemble of several pure states. This is used when there is classical uncertainty about which pure state the system is in. A mixed state cannot be described by a single ket vector. Instead, it is described by a **[[Notes/2025/10/06/Density Matrix\|density matrix]]** (or density operator), denoted by $\rho$.

The density matrix for a mixed state is given by:

$$
\rho = \sum_i p_i |\psi_i\rangle\langle\psi_i|
$$

Here, $p_i$ is the classical probability that the system is in the pure state $|\psi_i\rangle$, and $\sum_i p_i = 1$.

> **Note**: Even a pure state $|\psi\rangle$ can be represented by a density matrix, $\rho = |\psi\rangle\langle\psi|$. A key distinction is that for a pure state, the trace of the square of its density matrix is one ($\text{Tr}(\rho^2) = 1$), whereas for a mixed state, it is less than one ($\text{Tr}(\rho^2) < 1$).

## Representation and Dynamics

### The Qubit: A Canonical Example

The **qubit** (quantum bit) is the fundamental unit of quantum information and serves as the simplest non-trivial example of a quantum state. Its state is a superposition of two basis states, denoted $|0\rangle$ and $|1\rangle$.

A general qubit state $|\psi\rangle$ is written as:

$$
|\psi\rangle = \alpha|0\rangle + \beta|1\rangle
$$

where $\alpha$ and $\beta$ are complex probability amplitudes satisfying the normalization condition $|\alpha|^2 + |\beta|^2 = 1$.

### The Bloch Sphere

The state of a single qubit can be visualized geometrically as a point on the surface of a three-dimensional sphere called the **Bloch sphere**.

-   The North and South poles of the sphere correspond to the basis states $|0\rangle$ and $|1\rangle$, respectively.
-   Any pure state of the qubit corresponds to a unique point on the surface of the sphere.
-   Mixed states are represented by points *inside* the sphere.
![image-1.png|236x250](/img/user/Assets/Images/image-1.png)
### Time Evolution and Measurement

The quantum state of a system is not static. Its evolution is governed by two distinct processes:

1.  **Unitary Evolution**: When a quantum system is isolated and not being observed, its state evolves smoothly and deterministically according to the **Schrödinger equation**:
    $$
    i\hbar \frac{d}{dt}|\psi(t)\rangle = \hat{H}|\psi(t)\rangle
    $$
    where $\hat{H}$ is the Hamiltonian operator of the system and $\hbar$ is the reduced Planck constant. This evolution is **unitary**, meaning it is reversible and preserves the normalization of the state.

2.  **Measurement and State Collapse**: When a measurement is performed on the system, the superposition is instantaneously destroyed, and the state "collapses" into one of the basis states corresponding to the observable being measured. This process is probabilistic and irreversible. The probability of collapsing to a particular basis state $|\phi_i\rangle$ is given by the **Born rule**, $P(i) = |\langle\phi_i|\psi\rangle|^2$.

## Multi-Particle Systems and Entanglement

When dealing with systems of more than one particle, the concept of the quantum state extends through the use of tensor products, leading to the profound phenomenon of entanglement.

-   **Tensor Product**: The state space of a composite system is the tensor product of the individual Hilbert spaces of its components. For a two-qubit system, the basis states are $|00\rangle, |01\rangle, |10\rangle,$ and $|11\rangle$.

-   **Entanglement**: An **[[Notes/2025/10/06/Entangled State\|Entangled State]]** is a multi-particle state that cannot be written as a simple product of the states of its individual constituents. For example, the Bell state $|\Phi^+\rangle = \frac{1}{\sqrt{2}}(|00\rangle + |11\rangle)$ is entangled. In this state, the two qubits are intrinsically linked; if the first qubit is measured to be in state $|0\rangle$, the second is instantaneously found to be in state $|0\rangle$, regardless of the distance separating them.

## Conclusion

The quantum state is the cornerstone of quantum theory, providing a complete probabilistic description of a physical system. It replaces the deterministic certainty of classical physics with a framework of superposition and probability amplitudes, governed by the mathematics of Hilbert spaces. Core concepts such as the state vector, superposition, measurement-induced collapse, and entanglement all stem from the nature of the quantum state. Its manipulation and control are at the heart of emerging technologies like quantum computing and quantum communication, promising to revolutionize science and technology.

