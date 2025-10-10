---
{"dg-publish":true,"permalink":"/notes/2025/10/06/entangled-state/"}
---

#QuantumMechanics #QuantumInformation #Physics

[[Entangled State.canvas\|Entangled State.canvas]]

# Entangled State

## Introduction

An **entangled state** is a quantum mechanical phenomenon in which the quantum states of two or more objects are linked in such a way that they must be described with reference to each other, even though the individual objects may be spatially separated. This interconnection leads to correlations between observable physical properties of the systems that are stronger than any correlations possible in classical physics. Albert Einstein famously described entanglement as *"spukhafte Fernwirkung"* or **"spooky action at a distance,"** highlighting its profoundly counter-intuitive nature. Far from being a mere theoretical curiosity, entanglement is a cornerstone of quantum mechanics and a critical resource for transformative technologies like quantum computing and quantum cryptography.

## Mathematical Definition: Separability vs. Entanglement

To formally define an entangled state, it is first necessary to understand what it is not: a **separable state**.

### Separable (Product) States

Consider a composite quantum system made up of two subsystems, A and B (for example, two qubits). The state of the composite system is described by a state vector in the tensor product of the individual Hilbert spaces, $\mathcal{H}_{AB} = \mathcal{H}_A \otimes \mathcal{H}_B$.

A state $|\psi\rangle_{AB}$ is called **separable** or a **product state** if it can be written as the tensor product of the individual states of its subsystems:

$$
|\psi\rangle_{AB} = |\psi\rangle_A \otimes |\psi\rangle_B
$$

In a separable state, each subsystem has its own definite quantum state, independent of the other. Measuring a property of subsystem A provides no information about the outcome of a measurement on subsystem B.

### Entangled States

An **entangled state** is defined as any state of a composite system that is **not separable**. It cannot be factored into a simple product of the states of its individual components.

$$
|\psi\rangle_{AB} \neq |\psi\rangle_A \otimes |\psi\rangle_B
$$

In an entangled state, the individual subsystems do not possess their own well-defined quantum states. The system as a whole is in a definite state, but the properties of the parts are only defined in relation to one another.

### The Bell States: Canonical Examples

The most famous examples of entangled states are the four **Bell states**, which form a maximally entangled basis for a two-qubit system:

1.  **$|\Phi^+\rangle = \frac{1}{\sqrt{2}}(|00\rangle + |11\rangle)$**
2.  **$|\Phi^-\rangle = \frac{1}{\sqrt{2}}(|00\rangle - |11\rangle)$**
3.  **$|\Psi^+\rangle = \frac{1}{\sqrt{2}}(|01\rangle + |10\rangle)$**
4.  **$|\Psi^-\rangle = \frac{1}{\sqrt{2}}(|01\rangle - |10\rangle)$**

Let's analyze the state $|\Phi^+\rangle$. This state is a superposition of two possibilities: both qubits are in the state $|0\rangle$, or both are in the state $|1\rangle$. If we measure the first qubit and find it to be in state $|0\rangle$, the quantum state of the system instantaneously collapses, and we know with 100% certainty that a measurement of the second qubit will yield the result $|0\rangle$. Similarly, if the first is measured as $|1\rangle$, the second will be $|1\rangle$. The measurement outcomes are perfectly correlated, regardless of the distance separating the qubits.

## Core Properties and Paradoxes

### Non-Locality and Correlations

The correlations exhibited by entangled particles are **non-local**. This means the outcome of a measurement on one particle appears to instantaneously influence the state of the other, violating the classical intuition that an object can only be influenced by its immediate surroundings (the principle of locality).

> **Important Note: No Faster-Than-Light Communication**
> Despite this instantaneous correlation, entanglement cannot be used to transmit information faster than the speed of light. An observer measuring one particle of an entangled pair sees a completely random outcome. It is only by classically communicating and comparing their measurement results that two observers can discover the correlations. The randomness at each end prevents the encoding of a deliberate message.

### The EPR Paradox and Bell's Theorem

The strange nature of entanglement led to one of the most significant debates in the history of physics.

1.  **The EPR Paradox (1935)**: Albert Einstein, Boris Podolsky, and Nathan Rosen argued that the non-local nature of entanglement implied that quantum mechanics was an incomplete theory. They proposed that the correlated outcomes must be predetermined by "local hidden variables"—unknown properties of the particles that were set at the moment of their creation.

2.  **Bell's Theorem (1964)**: John Stewart Bell devised a mathematical framework to experimentally test the idea of local hidden variables. He derived an inequality, now known as **Bell's inequality**, which must be satisfied by any theory based on locality and realism. Bell showed that the statistical predictions of quantum mechanics for entangled systems would *violate* this inequality.

3.  **Experimental Confirmation**: Beginning in the 1970s and 1980s, experiments conducted by physicists like John Clauser, Alain Aspect, and Anton Zeilinger have overwhelmingly confirmed the predictions of quantum mechanics. They have demonstrated consistent violations of Bell's inequality, thereby ruling out the existence of local hidden variables and proving that the "spooky action at a distance" is a real and fundamental feature of our universe.

## Applications of Entanglement

Entanglement is not just a philosophical puzzle; it is a powerful physical resource that is being harnessed to build revolutionary technologies.

-   **Quantum Computing**: Entanglement is a key ingredient that enables the immense processing power of quantum computers. It allows for the creation of complex superpositions of many qubits, providing a massive computational space for algorithms to operate in, leading to exponential speedups for certain problems.
-   **Quantum Cryptography**: Protocols like **Quantum Key Distribution (QKD)** use entangled particles to share a secret key between two parties with provable security. Any attempt by an eavesdropper to intercept and measure the particles would disturb the entanglement, which would be immediately detectable by the legitimate users.
-   **Quantum Teleportation**: This is a process that uses a pre-shared entangled pair and classical communication to transmit the exact quantum state of a particle from one location to another, without physically moving the particle itself.

## Conclusion

The entangled state represents one of the most profound departures of quantum mechanics from the classical world. It challenges our fundamental intuitions about locality and reality, revealing a deeply interconnected universe where the whole can be more definite than its parts. Once a source of paradox, entanglement is now understood as a fundamental and exploitable property of nature, driving the ongoing second quantum revolution and paving the way for technologies that were once the exclusive domain of science fiction.

