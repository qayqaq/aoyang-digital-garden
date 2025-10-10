---
{"dg-publish":true,"permalink":"/notes/2025/10/06/kraus-operator/"}
---

#QuantumMechanics #QuantumInformation #OpenQuantumSystems

[[Kraus Operator.canvas\|Kraus Operator.canvas]]

# Kraus Operator

## Introduction

In the theory of quantum mechanics, the evolution of a closed, isolated quantum system is described by a unitary transformation. However, no real-world system is perfectly isolated; all quantum systems interact to some extent with their surrounding environment. This interaction leads to processes like decoherence and dissipation, which cannot be described by unitary evolution alone.

The **Kraus operators** provide the mathematical foundation for describing the dynamics of such **open quantum systems**. They are the elements of the **operator-sum representation (OSR)**, a powerful formalism that characterizes the most general physical transformations a quantum state can undergo. This framework, also known as a **quantum channel** or **quantum operation**, is indispensable in quantum information theory for modeling noise, decoherence, and the effects of measurement on quantum systems.

## The Operator-Sum Representation

A general quantum operation is a map $\mathcal{E}$ that takes a density matrix $\rho$ describing the initial state of a system to a new density matrix $\rho'$ describing the final state. This transformation can be expressed as a sum involving a set of operators $\{E_k\}$, which are the Kraus operators:

$$
\rho' = \mathcal{E}(\rho) = \sum_k E_k \rho E_k^\dagger
$$

The operators $E_k$ act on the Hilbert space of the system and are not necessarily unitary or Hermitian. They must, however, satisfy a crucial constraint known as the **completeness relation**:

$$
\sum_k E_k^\dagger E_k = I
$$

where $I$ is the identity operator. This condition ensures that the transformation is trace-preserving, i.e., $\text{Tr}(\rho') = \text{Tr}(\rho) = 1$. This is a physical requirement, as the trace of the density matrix represents the total probability, which must be conserved.

## Physical Origin and Interpretation

The Kraus operator formalism is not an ad-hoc mathematical construction; it arises naturally from considering the system of interest as part of a larger, closed system that includes an environment.

1.  **System-Environment Model**: We model the open system (S) and its environment (E) as a single, combined closed system (SE). The total system evolves unitarily under an operator $U_{SE}$.

2.  **Initial State**: We assume the system and environment are initially uncorrelated. The initial state of the combined system is a product state $\rho_{SE} = \rho_S \otimes \rho_E$. For simplicity, we can assume the environment starts in a known pure state, $|e_0\rangle$, so $\rho_E = |e_0\rangle\langle e_0|$.

3.  **Unitary Evolution**: The combined system evolves to a final state:
    $$
    \rho'_{SE} = U_{SE} (\rho_S \otimes |e_0\rangle\langle e_0|) U_{SE}^\dagger
    $$

4.  **Tracing Out the Environment**: Since we are only interested in the final state of our system S, we "trace out" the environmental degrees of freedom by performing a partial trace over the environment's Hilbert space:
    $$
    \rho'_S = \text{Tr}_E(\rho'_{SE})
    $$

By expanding this expression in a basis $\{|e_k\rangle\}$ for the environment, we arrive at the operator-sum representation. The Kraus operators are defined by the matrix elements of the total unitary operator $U_{SE}$:

$$
E_k \equiv \langle e_k | U_{SE} | e_0 \rangle
$$

Each Kraus operator $E_k$ is an operator that acts solely on the system's Hilbert space. It can be interpreted as describing one possible "path" of evolution for the system, corresponding to a particular final state $|e_k\rangle$ of the environment. The sum in the operator-sum representation reflects our ignorance about the final state of the environment; we sum over all possibilities to find the resulting state of our system.

## Examples of Quantum Channels

### 1. Unitary Evolution

The evolution of a closed system is a special case of the OSR with only a single Kraus operator, $E_0 = U$. The completeness relation becomes $U^\dagger U = I$, which is the definition of a unitary operator. The evolution is simply:
$$
\rho' = U \rho U^\dagger
$$

### 2. Bit Flip Channel

This channel models a common type of noise where a qubit is flipped ($|0\rangle \leftrightarrow |1\rangle$) with some probability $p$.
-   With probability $1-p$, nothing happens.
-   With probability $p$, a Pauli-X gate is applied.

The Kraus operators are:
-   $E_0 = \sqrt{1-p} \cdot I = \sqrt{1-p} \begin{pmatrix} 1 & 0 \\ 0 & 1 \end{pmatrix}$
-   $E_1 = \sqrt{p} \cdot X = \sqrt{p} \begin{pmatrix} 0 & 1 \\ 1 & 0 \end{pmatrix}$

The completeness relation is satisfied: $E_0^\dagger E_0 + E_1^\dagger E_1 = (1-p)I + pX^2 = (1-p)I + pI = I$.
The transformation is:
$$
\mathcal{E}(\rho) = (1-p)\rho + pX\rho X
$$

### 3. Amplitude Damping Channel

This channel models the process of energy dissipation, such as a photon being lost from an optical cavity or an excited atom decaying to its ground state. For a single qubit, it is described by the Kraus operators:
-   $E_0 = \begin{pmatrix} 1 & 0 \\ 0 & \sqrt{1-\gamma} \end{pmatrix}$
-   $E_1 = \begin{pmatrix} 0 & \sqrt{\gamma} \\ 0 & 0 \end{pmatrix}$

Here, $\gamma$ is the probability of losing a quantum of energy. $E_1$ represents the process of the qubit transitioning from $|1\rangle$ to $|0\rangle$, while $E_0$ describes the complementary process.

## Non-Uniqueness of the Representation

An important feature of the operator-sum representation is that the set of Kraus operators for a given quantum channel $\mathcal{E}$ is not unique. If $\{E_k\}$ is one set of Kraus operators describing $\mathcal{E}$, then any other set $\{F_j\}$ related by a unitary transformation $F_j = \sum_k u_{jk} E_k$ (where $U = (u_{jk})$ is a unitary matrix) will describe the exact same channel:
$$
\sum_j F_j \rho F_j^\dagger = \sum_k E_k \rho E_k^\dagger = \mathcal{E}(\rho)
$$
This freedom corresponds to the freedom of choosing a different basis for the environment in the physical derivation.

## Conclusion

Kraus operators and the operator-sum representation provide a complete and mathematically rigorous framework for describing the dynamics of open quantum systems. They generalize the concept of unitary evolution to include non-unitary processes like noise, decoherence, and measurement, which are unavoidable in any practical quantum system. By modeling the interaction with an environment, this formalism bridges the gap between the idealized theory of closed quantum systems and the complex reality of experimental quantum information processing, making it a cornerstone of modern quantum physics.
