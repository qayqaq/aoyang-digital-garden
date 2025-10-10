---
{"dg-publish":true,"permalink":"/notes/2025/10/06/completely-positive-trace-preserving-map/"}
---

#QuantumInformation #QuantumMechanics #LinearAlgebra #Mathematics

[[Completely Positive Trace-Preserving Map.canvas\|Completely Positive Trace-Preserving Map.canvas]]

# Completely Positive Trace-Preserving (CPTP) Map

## Introduction

In quantum mechanics and quantum information theory, a **Completely Positive Trace-Preserving (CPTP) map** is the most general mathematical description of a physical process that a quantum system can undergo. These maps, also known as **quantum operations** or **[[Notes/2025/10/06/Quantum Channels\|quantum channels]]**, provide a unified framework for describing all possible transformations of a [[Notes/2025/10/06/Quantum State\|quantum state]]. This includes the *idealized, reversible evolution of a closed system (unitary evolution)* as well as the more *realistic, irreversible dynamics of an open system that interacts with its environment, leading to noise, [[Notes/2025/10/06/Decoherence\|decoherence]], and measurement*.

The name itself encapsulates the two fundamental physical constraints that any valid quantum evolution must satisfy:
1. **Trace-Preserving (TP)**: This condition ensures that probability is conserved.
2. **Completely Positive (CP)**: This condition ensures that the map is physically valid even when the system is entangled with other systems.

Understanding CPTP maps is essential for modeling realistic quantum computers, analyzing quantum communication protocols, and studying the fundamental nature of open quantum systems.

## Deconstructing the Definition

To understand a CPTP map, we must analyze its two defining properties separately. Let $\mathcal{E}$ be a map that takes an initial [[Notes/2025/10/06/Density Matrix\|density matrix]] $\rho$ to a final density matrix $\rho' = \mathcal{E}(\rho)$.

### 1. The Trace-Preserving (TP) Property

A map $\mathcal{E}$ is **trace-preserving** if the trace of the output density matrix is the same as the trace of the input density matrix for any state $\rho$.

$$
\text{Tr}(\mathcal{E}(\rho)) = \text{Tr}(\rho)
$$

**Physical Significance**:
In quantum mechanics, the density matrix $\rho$ must have a trace of one ($\text{Tr}(\rho) = 1$). This mathematical condition corresponds to the physical fact that the sum of probabilities of all possible outcomes of a measurement must be 1. The trace-preserving property ensures that this fundamental rule is upheld during the system's evolution. In short, it guarantees the **conservation of probability**.

> **Note**: Maps that are not trace-preserving can still be physically meaningful. For example, a map describing a single outcome of a measurement is typically trace-reducing, as it corresponds to a probabilistic event. The full set of maps for all possible measurement outcomes must sum to a trace-preserving map.

### 2. The Positive and Completely Positive (CP) Property

This property is more subtle but is crucial for ensuring that the map is physically realistic in all possible scenarios, especially those involving entanglement.

#### Positive Maps

A map $\mathcal{E}$ is **positive** if it maps any positive semi-definite operator to another positive semi-definite operator.

**Physical Significance**:
A density matrix must be a positive semi-definite operator to be physically valid. This ensures that the probabilities calculated from it are non-negative. A positive map guarantees that if you start with a valid physical state, you will end up with a valid physical state.

#### Why "Completely" Positive?

It turns out that positivity alone is not a strong enough condition. A map might be positive when acting on an isolated system but fail to be physical when that system is entangled with another system (an "ancilla" or environment).

A map $\mathcal{E}$ is **completely positive** if, for any auxiliary system (ancilla) of any dimension $k$, the extended map $\mathcal{E} \otimes I_k$ is also positive. Here, $I_k$ is the identity map acting on the $k$-dimensional ancilla.

**Physical Significance**:
This is the key physical requirement. It ensures that the map remains valid even when applied to a subsystem that is part of a larger, entangled quantum state. If a map were only positive but not completely positive, it could transform a valid entangled state of the composite system into an unphysical state with negative probabilities. Therefore, complete positivity guarantees that a process is universally valid across all contexts in quantum mechanics.

> **Example of a Positive but not Completely Positive Map**: The matrix transpose operation, $T(\rho) = \rho^T$, is a classic example. It is a positive map, but it is not completely positive. Applying it to one qubit of a two-qubit entangled state can result in an operator that is not positive semi-definite, violating the laws of quantum mechanics. This proves that the transpose is not a physically realizable quantum operation on its own.

## Mathematical Representation: The Kraus Operator-Sum Formalism

A cornerstone result in quantum information theory, known as **Choi's theorem** or the **Kraus representation theorem**, states that a map is completely positive if and only if it can be expressed in a specific form called the **[[Notes/2025/10/06/Operator-Sum Representation\|Operator-Sum Representation]] (OSR)**.

Any CPTP map $\mathcal{E}$ can be written as:

$$
\mathcal{E}(\rho) = \sum_k E_k \rho E_k^\dagger
$$

- The operators $\{E_k\}$ are called **Kraus operators**. They act on the Hilbert space of the system.
- The map is trace-preserving if and only if the Kraus operators satisfy the **completeness relation**:
    $$
    \sum_k E_k^\dagger E_k = I
    $$

This representation is extremely powerful because it provides a concrete mathematical structure for any physically allowed quantum process. Each Kraus operator can be thought of as representing one possible "path" or "effect" of the interaction with the environment, and the sum represents the total evolution, averaging over all possibilities.

## Conclusion

The Completely Positive Trace-Preserving (CPTP) map is the mathematical embodiment of a general physical process in quantum mechanics. It provides the rigorous framework necessary to describe the evolution of quantum states under the most general conditions.

-   The **trace-preserving** condition upholds the conservation of probability.
-   The **completely positive** condition ensures physical validity, even in the presence of entanglement, by guaranteeing that valid states always map to valid states.

The equivalence of CPTP maps to the operator-sum (Kraus) representation gives us a practical and powerful tool to model and analyze everything from perfect unitary evolution to the noisy, decoherent dynamics of real-world quantum systems. As such, CPTP maps are a fundamental concept in the theory and practice of quantum computation, communication, and metrology.

