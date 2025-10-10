---
{"dg-publish":true,"permalink":"/notes/2025/10/06/open-quantum-system/"}
---

#quantum-mechanics #open-quantum-systems #quantum-information
[[Open Quantum System.canvas\|Open Quantum System.canvas]]

# Open Quantum System

## Introduction

An **open quantum system** is a quantum system that interacts with an external quantum system, known as the **environment** or **bath**. This stands in contrast to a **closed quantum system**, an idealized construct that is perfectly isolated from its surroundings and whose evolution is governed by the reversible, unitary dynamics of the Schrödinger equation.

In reality, no quantum system is ever perfectly isolated. The theory of open quantum systems provides the essential and realistic framework for describing how quantum systems behave when they are subject to the unavoidable influence of their environment. This interaction leads to fundamentally new phenomena that are not present in closed systems, most notably **decoherence**, **dissipation**, and **noise**. Understanding open quantum systems is therefore critical for the development of quantum technologies like quantum computers, where environmental interactions are the primary obstacle, as well as for describing natural processes ranging from quantum optics to quantum biology.

## Conceptual Framework: From a Closed Universe to an Open System

The core idea behind the theory of open quantum systems is to consider the system of interest ($S$) and its environment ($E$) together as a single, larger, closed quantum system ($S+E$). The dynamics of this total system are unitary and reversible.

The total Hamiltonian can be written as:
$$
H_{\text{total}} = H_S + H_E + H_{\text{int}}
$$
where:
-   $H_S$ is the Hamiltonian of the system alone.
-   $H_E$ is the Hamiltonian of the environment alone.
-   $H_{\text{int}}$ is the interaction Hamiltonian describing the coupling between the system and the environment.

The evolution of the total system is described by a global unitary operator $U_{\text{total}}(t)$. If the initial state of the total system is $\rho_{\text{total}}(0)$, its state at a later time $t$ is:
$$
\rho_{\text{total}}(t) = U_{\text{total}}(t) \rho_{\text{total}}(0) U_{\text{total}}^\dagger(t)
$$

However, we are typically only interested in the state of our system $S$, not the environment. To obtain the state of the system, $\rho_S(t)$, we must discard the information about the environment by performing a **partial trace** over the environment's degrees of freedom:
$$
\rho_S(t) = \text{Tr}_E[\rho_{\text{total}}(t)]
$$

> This tracing-out procedure is the source of all non-unitary behavior in the open system. Information and quantum coherence can "leak" from the system into the environment, and this loss of information results in dynamics for $\rho_S(t)$ that are generally irreversible and non-unitary.

## Key Phenomena in Open Quantum Systems

The interaction with an environment induces several critical processes.

### 1. Decoherence

Decoherence is the process by which a system loses its quantum coherence, meaning the definite phase relationships between the states in a superposition are lost. This is the primary mechanism for the quantum-to-classical transition.
-   **Mechanism**: The system becomes entangled with the environment. Different states of the system lead to different, distinguishable states of the environment. As information about the system's state is imprinted onto the environment, the superposition within the system is effectively destroyed from the perspective of a local observer.
-   **Effect**: In the density matrix representation, decoherence manifests as the rapid decay of the off-diagonal elements (the "coherences"). A pure superposition state like $\frac{1}{\sqrt{2}}(|0\rangle + |1\rangle)$ evolves into a classical statistical [[Notes/2025/10/06/Mixed State\|Mixed State]] like $\frac{1}{2}|0\rangle\langle0| + \frac{1}{2}|1\rangle\langle1|$.

### 2. Dissipation and Relaxation

Dissipation is the process by which the system loses energy to its environment, eventually approaching a steady state, often a thermal equilibrium state.
-   **Example**: An excited atom in a vacuum (the environment) will spontaneously emit a photon and decay to its ground state. This is an irreversible, dissipative process.
-   **Effect**: The populations of the system's energy levels (the diagonal elements of the density matrix) change over time until they reach a stable configuration determined by the properties of the environment (e.g., its temperature).

## Mathematical Description of Open System Dynamics

Because the evolution is non-unitary, the Schrödinger equation is insufficient. Instead, the dynamics are described by maps on density matrices.

### 1. Quantum Channels (CPTP Maps)

For describing a transformation over a discrete time interval, the evolution of an open system is given by a [[Notes/2025/10/06/Quantum Channels\|quantum channel]], which is a **completely positive and trace-preserving (CPTP)** map $\mathcal{E}$. Its action can be written using the **operator-sum representation**:
$$
\rho_S(t) = \mathcal{E}(\rho_S(0)) = \sum_k E_k \rho_S(0) E_k^\dagger
$$
where the [[Notes/2025/10/06/Kraus Operator\|Kraus Operator]]s $\{E_k\}$ encapsulate the total effect of the interaction and satisfy $\sum_k E_k^\dagger E_k = I$.

### 2. Quantum Master Equations

For continuous time evolution, the dynamics are described by a **quantum master equation**, which is a differential equation for the density matrix $\rho_S(t)$.

Under the **Markovian approximation** (assuming the environment has no memory and reacts much faster than the system evolves), the most general form of the master equation is the **Lindblad-Görini-Kossakowski-Sudarshan (LGKS) equation**, often called the **Lindblad master equation**:

$$
\frac{d\rho_S}{dt} = -\frac{i}{\hbar}[H_S, \rho_S] + \mathcal{D}(\rho_S)
$$
where the dissipator $\mathcal{D}(\rho_S)$ is given by:
$$
\mathcal{D}(\rho_S) = \sum_k \gamma_k \left( L_k \rho_S L_k^\dagger - \frac{1}{2}\{L_k^\dagger L_k, \rho_S\} \right)
$$

-   The first term, $-\frac{i}{\hbar}[H_S, \rho_S]$, is the standard unitary evolution of the isolated system.
-   The dissipator $\mathcal{D}(\rho_S)$ describes all the non-unitary effects of the environment.
-   The $L_k$ are **Lindblad operators** (or quantum jump operators), which model the specific physical processes through which the system interacts with the environment (e.g., photon emission, dephasing).
-   The $\gamma_k \ge 0$ are the rates at which these processes occur.

When the Markovian approximation is not valid, the dynamics are said to be **non-Markovian**. In this case, the environment has a memory, and information can flow back from the environment to the system, leading to more complex dynamics that are much harder to model.

## Conclusion

The theory of open quantum systems is the bridge between the abstract formalism of quantum mechanics and the reality of experimental physics and technology. It explains why quantum phenomena are so fragile and provides the tools to analyze and control them. By treating any system of interest as fundamentally coupled to an environment, it accounts for the irreversible processes of decoherence and dissipation that govern the behavior of all real-world quantum systems. This framework is not only essential for overcoming the challenges in quantum computing but also provides deep insights into the foundations of statistical mechanics and the emergence of the classical world from the quantum substrate.

