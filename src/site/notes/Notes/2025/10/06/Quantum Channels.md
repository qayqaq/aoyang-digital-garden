---
{"dg-publish":true,"permalink":"/notes/2025/10/06/quantum-channels/"}
---

#quantum-information #quantum-mechanics #open-quantum-systems
[[Quantum Channels.canvas\|Quantum Channels.canvas]]

# Quantum Channels

## Introduction

In the theory of quantum information, a **quantum channel** is a mathematical construct that describes the most general physical transformations a quantum system can undergo. While the evolution of an idealized, perfectly isolated quantum system is described by a [[Notes/2025/10/06/Unitary Operator\|Unitary Operator]], real-world systems are never truly isolated. They interact with their surrounding environment, leading to processes like noise, decoherence, and information loss.

Quantum channels provide the essential framework for modeling these interactions. They represent the dynamics of **open quantum systems**, where a system of interest evolves while coupled to an external environment. This makes them indispensable tools for understanding and mitigating errors in quantum computation, analyzing the fidelity of quantum communication, and describing any realistic quantum process. In essence, a quantum channel is a map that transforms an initial quantum state (represented by a density matrix) into a final one, consistent with the laws of physics.

## From Unitary Evolution to Open Systems

The dynamics of a **closed quantum system** are reversible and are described by a unitary transformation. If the system is in a state described by the density matrix $\rho$, its evolution over time is given by:

$$
\rho' = U \rho U^\dagger
$$

where $U$ is a unitary operator ($U^\dagger U = I$). This transformation preserves the purity of the state; a pure state remains pure, and a mixed state's degree of mixture is unchanged.

However, this picture is incomplete. Consider a system of interest, $S$, interacting with a larger environment, $E$. The combined system, $S+E$, can be treated as a closed system, and its joint evolution is unitary.

1.  **Initial State**: Assume the system and environment are initially uncorrelated. The total state is a product state $\rho_{SE} = \rho_S \otimes \rho_E$, where $\rho_S$ is the initial state of our system and $\rho_E$ is the state of the environment.
2.  **Joint Unitary Evolution**: The combined system evolves under a global unitary operator $U_{SE}$:
    $$
    \rho'_{SE} = U_{SE} (\rho_S \otimes \rho_E) U_{SE}^\dagger
    $$
3.  **Tracing Out the Environment**: We are only interested in the final state of our system, $\rho'_S$. To obtain this, we must perform a **partial trace** over the environment's degrees of freedom:
    $$
    \rho'_S = \text{Tr}_E(\rho'_{SE}) = \text{Tr}_E \left( U_{SE} (\rho_S \otimes \rho_E) U_{SE}^\dagger \right)
    $$

The resulting transformation from $\rho_S$ to $\rho'_S$ is generally **not unitary**. This process, which maps the initial density matrix of the system to its final one, is what defines a quantum channel.

## Mathematical Formalism: The Operator-Sum Representation

A quantum channel is formally defined as a **completely positive and trace-preserving (CPTP)** map, denoted $\mathcal{E}$. The most common and useful way to describe such a map is the **Operator-Sum Representation**, also known as the **Kraus Representation**.

According to this representation, the action of any quantum channel $\mathcal{E}$ on a density matrix $\rho$ can be written as:

$$
\mathcal{E}(\rho) = \sum_{k} E_k \rho E_k^\dagger
$$

The operators $\{E_k\}$ are called **Kraus operators**. They act on the Hilbert space of the system and satisfy the **completeness relation**:

$$
\sum_{k} E_k^\dagger E_k = I
$$

where $I$ is the identity operator. This condition ensures that the channel is **trace-preserving** ($\text{Tr}(\mathcal{E}(\rho)) = \text{Tr}(\rho)$), which corresponds to the physical requirement that total probability is conserved.

> **Stinespring Dilation Theorem**: This fundamental theorem provides the physical justification for the operator-sum representation. It states that any valid quantum channel (a CPTP map) can be realized through the physical process described above: a unitary evolution on a larger system (system + environment) followed by a partial trace over the environment.

## Properties of Quantum Channels

To be a valid physical transformation, a quantum channel $\mathcal{E}$ must satisfy two key properties:

1.  **Trace-Preserving**: As enforced by the completeness relation, the trace of the output density matrix must equal the trace of the input. Since $\text{Tr}(\rho) = 1$ for any valid state, this ensures the output is also a valid state with total probability one.

2.  **Complete Positivity**: A map is **positive** if it sends positive operators (like density matrices) to other positive operators. A map is **completely positive** if it remains positive even when applied to a subsystem of a larger, potentially entangled system. This is a stronger condition that ensures the map produces valid physical states under all circumstances. The operator-sum form inherently guarantees complete positivity.

## Examples of Important Quantum Channels

Quantum channels are used to model various forms of quantum noise.

### 1. Depolarizing Channel

This channel models a scenario where the quantum state is either left alone with probability $1-p$ or replaced by the completely mixed state $\frac{I}{d}$ with probability $p$.
$$
\mathcal{E}(\rho) = (1-p)\rho + p \frac{I}{d}
$$
For a single qubit ($d=2$), its Kraus operators can be written as:
$E_0 = \sqrt{1-p}I$, $E_1 = \sqrt{p/3}X$, $E_2 = \sqrt{p/3}Y$, $E_3 = \sqrt{p/3}Z$, where $X, Y, Z$ are the Pauli matrices.

### 2. Amplitude Damping Channel

This channel models energy dissipation, such as a qubit in the excited state $|1\rangle$ decaying to the ground state $|0\rangle$. It is a crucial model for phenomena like spontaneous emission. For a decay probability $\gamma$, the Kraus operators are:
$$
E_0 = \begin{pmatrix} 1 & 0 \\ 0 & \sqrt{1-\gamma} \end{pmatrix}, \quad E_1 = \begin{pmatrix} 0 & \sqrt{\gamma} \\ 0 & 0 \end{pmatrix}
$$
The operator $E_1$ explicitly maps the state $|1\rangle$ to $|0\rangle$, representing the loss of an energy quantum.

### 3. Phase Damping (Dephasing) Channel

This channel describes the loss of quantum phase information without any loss of energy. It is responsible for the decay of superposition states into classical mixtures (decoherence). With a dephasing probability $p$, its Kraus operators are:
$$
E_0 = \sqrt{1-p} I = \begin{pmatrix} \sqrt{1-p} & 0 \\ 0 & \sqrt{1-p} \end{pmatrix}, \quad E_1 = \sqrt{p} Z = \begin{pmatrix} \sqrt{p} & 0 \\ 0 & -\sqrt{p} \end{pmatrix}
$$
This channel suppresses the off-diagonal elements of the density matrix, which encode the phase coherence of the state.

## Conclusion

Quantum channels provide a powerful and complete framework for describing the dynamics of quantum systems in realistic settings. By generalizing the concept of unitary evolution to include interactions with an environment, they allow for a rigorous mathematical treatment of noise, decoherence, and other irreversible processes. The operator-sum representation offers a versatile tool for analyzing these phenomena, making quantum channels a central concept in quantum information theory, quantum computing, and the study of open quantum systems. Understanding them is the first step toward developing strategies, such as quantum error correction, to overcome the challenges posed by environmental noise.
