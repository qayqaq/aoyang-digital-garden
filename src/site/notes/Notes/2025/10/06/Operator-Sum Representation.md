---
{"dg-publish":true,"permalink":"/notes/2025/10/06/operator-sum-representation/"}
---

#quantum-information #open-quantum-systems #quantum-mechanics
[[Operator-Sum Representation.canvas\|Operator-Sum Representation.canvas]]

# Operator-Sum Representation

## Introduction

The **Operator-Sum Representation (OSR)**, also known as the **Kraus Representation**, is a fundamental mathematical tool in quantum mechanics and quantum information theory. Its purpose is to describe the most general class of physical transformations that a quantum system can undergo. While the evolution of a perfectly isolated (closed) system is described by a single [[Notes/2025/10/06/Unitary Operator\|Unitary Operator]], this is an idealization. The OSR provides the framework for describing the dynamics of [[Notes/2025/10/06/Open Quantum System\|open quantum systems]], which interact with an environment.

This representation is the cornerstone for the theory of [[Notes/2025/10/06/Quantum Channels\|Quantum Channels]]. It allows for a unified description of diverse physical processes, including unitary evolution, [[Notes/2025/10/06/Measurements in Quantum Mechanics\|quantum measurement]], noise, and [[Notes/2025/10/06/Decoherence\|Decoherence]]. Its power lies in its ability to capture any transformation that is consistent with the laws of quantum mechanics, making it an indispensable tool for analyzing realistic quantum experiments and technologies.

## Mathematical Formulation

A general quantum operation is a map $\mathcal{E}$ that takes an initial density matrix $\rho$ to a final density matrix $\rho'$. The operator-sum representation expresses this map as a sum over a set of operators $\{E_k\}$, which are known as **Kraus operators**:

$$
\rho' = \mathcal{E}(\rho) = \sum_k E_k \rho E_k^\dagger
$$

The Kraus operators $E_k$ act on the Hilbert space of the system. They are not required to be unitary or Hermitian, but they must satisfy a single, crucial constraint known as the **completeness relation**:

$$
\sum_k E_k^\dagger E_k = I
$$

where $I$ is the identity operator on the system's Hilbert space.

> This completeness relation is the mathematical condition that ensures the transformation is **trace-preserving**. That is, $\text{Tr}(\rho') = \text{Tr}(\rho)$. Since the trace of a density matrix represents the total probability (which must be 1), this condition guarantees that the output of the map is a valid physical state.

## Physical Motivation: Derivation from Unitary Evolution

The operator-sum representation is not merely a mathematical convenience; it has a direct physical origin. It can be derived by considering a system of interest, $S$, interacting with a larger environment (or ancilla), $E$. The combined system $S+E$ is assumed to be closed, and thus its evolution is described by a single unitary operator $U_{SE}$.

The derivation proceeds as follows:
1. **Initial State**: Assume the system and environment are initially uncorrelated. The system is in state $\rho_S$, and the environment is in a known pure state, say $|e_0\rangle_E$. The total initial state is $\rho_{\text{total}} = \rho_S \otimes |e_0\rangle_E\langle e_0|_E$.

2. **Joint Unitary Evolution**: The combined system evolves according to the unitary operator $U_{SE}$:
    $$
    \rho'_{\text{total}} = U_{SE} (\rho_S \otimes |e_0\rangle_E\langle e_0|_E) U_{SE}^\dagger
    $$

3. **Tracing Out the Environment**: We are only interested in the final state of our system, $\rho'_S$. To obtain this, we trace over the environment's degrees of freedom. Let $\{|e_k\rangle_E\}$ be an orthonormal basis for the environment's Hilbert space.
    $$
    \rho'_S = \text{Tr}_E(\rho'_{\text{total}}) = \sum_k \langle e_k|_E \left( U_{SE} (\rho_S \otimes |e_0\rangle_E\langle e_0|_E) U_{SE}^\dagger \right) |e_k\rangle_E
    $$

4. **Defining the Kraus Operators**: We can define a set of operators $E_k$ that act only on the system's Hilbert space as follows:
    $$
    E_k = \langle e_k|_E U_{SE} |e_0\rangle_E
    $$
    Substituting this definition into the expression for $\rho'_S$ yields the operator-sum representation:
    $$
    \rho'_S = \sum_k E_k \rho_S E_k^\dagger
    $$

The **Stinespring Dilation Theorem** provides the formal guarantee that *any* physically valid quantum operation (specifically, any completely positive, trace-preserving map) can be represented in this way.

## Properties and Interpretation

### Complete Positivity and Trace Preservation

The operator-sum form automatically satisfies the two essential requirements for any physical map:
- **Trace-Preserving**: As shown by the completeness relation, probability is conserved.
    $$
    \text{Tr}(\mathcal{E}(\rho)) = \text{Tr}\left(\sum_k E_k \rho E_k^\dagger\right) = \sum_k \text{Tr}(E_k \rho E_k^\dagger) = \sum_k \text{Tr}(\rho E_k^\dagger E_k) = \text{Tr}\left(\rho \sum_k E_k^\dagger E_k\right) = \text{Tr}(\rho I) = \text{Tr}(\rho)
    $$
- **Complete Positivity**: The map is guaranteed to be **completely positive**, a strong condition ensuring that it produces a valid (positive semi-definite) density matrix even when applied to a subsystem of a larger entangled state. This is crucial for consistency with the theory of entanglement.

### Non-Uniqueness of Kraus Operators

The set of Kraus operators for a given quantum channel is not unique. If $\{E_k\}$ is a valid set of Kraus operators, then any other set $\{F_j\}$ related by a unitary matrix $u$ also describes the same channel:
$$
F_j = \sum_k u_{jk} E_k \quad \text{where} \quad U U^\dagger = I
$$
This freedom can be exploited to find a representation with the minimum number of Kraus operators or one that has a more direct physical interpretation.

### Connection to Generalized Measurement

The OSR is deeply connected to the theory of generalized quantum [[Notes/2025/10/06/Measurements in Quantum Mechanics\|measurements]] (POVMs). The index $k$ can be interpreted as the outcome of a measurement performed on the system-environment composite.
-   The probability of obtaining outcome $k$ is $p(k) = \text{Tr}(E_k \rho E_k^\dagger)$.
-   If outcome $k$ is obtained, the state of the system collapses to $\rho_k = \frac{E_k \rho E_k^\dagger}{p(k)}$.
This shows that the evolution of an open system can be viewed as a measurement process where the measurement results are discarded.

## Conclusion

The Operator-Sum Representation is a powerful and elegant formalism that provides a complete description of all physically permissible transformations in quantum mechanics. By capturing the effects of a system's interaction with its environment, it serves as the mathematical foundation for the study of open quantum systems, quantum noise, and decoherence. Its direct connection to the physics of system-environment coupling and generalized measurements makes it an indispensable tool in quantum information science, enabling the precise modeling and analysis of realistic quantum devices.

