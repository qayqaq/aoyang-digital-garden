---
{"dg-publish":true,"permalink":"/notes/2025/10/06/mixed-state/"}
---

#quantum-mechanics #quantum-information #density-matrix
[[Mixed State.canvas\|Mixed State.canvas]]

# Mixed State

## Introduction

In quantum mechanics, the state of a system encapsulates all knowable information about it. While an idealized, isolated system can be described by a single state vector $|\psi\rangle$ in a Hilbert space—a configuration known as a **pure state**—this description is often insufficient for realistic scenarios. A **mixed state** is a more general concept that describes a quantum system when there is classical uncertainty about its preparation or when it is entangled with another system that is not being observed.

Mixed states are essential for describing any quantum system that is not perfectly isolated, which includes virtually all systems in experimental and real-world settings. They are the fundamental language of **[[Notes/2025/10/06/Open Quantum System\|Open Quantum System]]**, [[Notes/2025/10/06/Quantum Thermodynamics\|Quantum Thermodynamics]], and quantum information theory, where processes like decoherence and noise are ubiquitous. The mathematical tool used to describe both pure and mixed states on an equal footing is the **density operator**, or **[[Notes/2025/10/06/Density Matrix\|density matrix]]**.

## The Density Matrix Formalism

A mixed state is not represented by a single state vector but by a statistical ensemble of pure states. An ensemble is a collection of quantum systems, where each system is in a pure state $|\psi_i\rangle$ with a corresponding classical probability $p_i$.

> A system is in a mixed state if it has a probability $p_1$ of being in the pure state $|\psi_1\rangle$, a probability $p_2$ of being in the pure state $|\psi_2\rangle$, and so on. The probabilities must sum to one: $\sum_i p_i = 1$.

The state of such an ensemble is described by the **density operator** $\rho$, defined as the weighted average of the projection operators for each pure state in the ensemble:

$$
\rho = \sum_i p_i |\psi_i\rangle\langle\psi_i|
$$

The density operator has three defining properties:
1. **Hermiticity**: It is self-adjoint, $\rho = \rho^\dagger$.
2. **Positive Semi-definiteness**: It has non-negative eigenvalues. This is equivalent to $\langle\phi|\rho|\phi\rangle \ge 0$ for any vector $|\phi\rangle$.
3. **Unit Trace**: The sum of its diagonal elements is one, $\text{Tr}(\rho) = 1$. This ensures the conservation of total probability.

Using the density operator, the expectation value of an observable $A$ is given by:
$$
\langle A \rangle = \text{Tr}(\rho \hat{A})
$$

## Distinguishing Pure and Mixed States: Purity

The density matrix formalism can also describe pure states. A pure state $|\psi\rangle$ is simply an ensemble with a single member, where $p_1=1$ for the state $|\psi\rangle$ and all other probabilities are zero. Its density matrix is $\rho = |\psi\rangle\langle\psi|$.

A key mathematical distinction between pure and mixed states is the **purity**, defined as $\text{Tr}(\rho^2)$.

- For a **pure state**, $\rho^2 = (|\psi\rangle\langle\psi|)(|\psi\rangle\langle\psi|) = |\psi\rangle\langle\psi|\psi\rangle\langle\psi| = |\psi\rangle\langle\psi| = \rho$. Therefore, the purity is:
    $$
    \text{Tr}(\rho^2) = \text{Tr}(\rho) = 1
    $$
- For a **mixed state**, the purity is always less than one:
    $$
    \text{Tr}(\rho^2) < 1
    $$

The state with the minimum possible purity is the **maximally mixed state**, where the system is in any of its basis states with equal probability. For a $d$-dimensional system (like a qudit), this state is $\rho = \frac{1}{d}I$, where $I$ is the identity matrix. Its purity is $\text{Tr}((\frac{1}{d}I)^2) = \frac{1}{d^2}\text{Tr}(I) = \frac{d}{d^2} = \frac{1}{d}$.

## Sources of Mixed States

There are two primary ways a system can end up in a mixed state.

1. **Imperfect Preparation (Classical Uncertainty)**: This occurs when the procedure for preparing a quantum state is not perfect. For example, a source might be designed to produce photons in the horizontally polarized state $|H\rangle$, but due to fluctuations, it produces $|H\rangle$ 95% of the time and the vertically polarized state $|V\rangle$ 5% of the time. The resulting state is a mixed state described by $\rho = 0.95 |H\rangle\langle H| + 0.05 |V\rangle\langle V|$.

2. **Entanglement with an Unobserved System (Quantum Uncertainty)**: This is a more profound, purely quantum source of mixedness. If a system $S$ is entangled with an environment $E$, the composite system $S+E$ can be in a pure state $|\Psi\rangle_{SE}$. However, if we only have access to system $S$, its state is found by taking the **partial trace** over the environment's degrees of freedom:
    $$
    \rho_S = \text{Tr}_E(|\Psi\rangle_{SE}\langle\Psi|_{SE})
    $$
    Even though the total state was pure, the resulting state $\rho_S$ of the subsystem is generally a mixed state. This is the fundamental mechanism behind **[[Notes/2025/10/06/Decoherence\|Decoherence]]**, where a system loses its "quantumness" through interaction with its environment.

## Mixed State vs. Superposition: A Critical Distinction

It is crucial not to confuse a mixed state with a superposition.
- A **superposition** is a **pure state**. For example, a qubit in the state $|\psi\rangle = \frac{1}{\sqrt{2}}(|0\rangle + |1\rangle)$ is in a definite state where it possesses properties of both $|0\rangle$ and $|1\rangle$ simultaneously. The phase relationship between the components is fixed, which allows for interference effects. Its density matrix has off-diagonal elements (coherences):
    $$
    \rho_{\text{superposition}} = |\psi\rangle\langle\psi| = \frac{1}{2} \begin{pmatrix} 1 & 1 \\ 1 & 1 \end{pmatrix}
    $$
- A **mixed state** represents a statistical mixture. For example, a qubit that is in state $|0\rangle$ with 50% probability and state $|1\rangle$ with 50% probability is described by the density matrix:
    $$
    \rho_{\text{mixed}} = \frac{1}{2}|0\rangle\langle0| + \frac{1}{2}|1\rangle\langle1| = \frac{1}{2} \begin{pmatrix} 1 & 0 \\ 0 & 1 \end{pmatrix}
    $$
    Here, the system is *either* in state $|0\rangle$ *or* in state $|1\rangle$; we just don't know which. There is no definite phase relationship and no interference between the components. The lack of off-diagonal elements reflects this absence of coherence.

## Conclusion

The concept of a mixed state, formalized through the density matrix, is an indispensable extension of the quantum state vector. It provides a complete and consistent framework for describing quantum systems under realistic conditions of uncertainty, environmental interaction, and entanglement. By distinguishing between the quantum uncertainty of superposition and the classical uncertainty of statistical ensembles, the density matrix allows us to precisely model the full spectrum of quantum phenomena, from the pristine coherence of isolated qubits to the complex dynamics of decoherence and thermal equilibrium.

