---
{"dg-publish":true,"permalink":"/notes/2025/10/13/fock-space/"}
---

#quantum-mechanics #quantum-field-theory #many-body-physics

[[Fock Space.canvas\|Fock Space.canvas]]

- **TLDR:** Fock space is a mathematical framework in quantum mechanics designed to describe systems where the number of particles is not constant but can change.
- **TLDR:** It is constructed as a "sum" (direct sum) of Hilbert spaces, one for each possible number of particles (zero, one, two, etc.), providing a unified space for states with any particle count.
- **TLDR:** The structure of Fock space fundamentally depends on particle statistics, leading to separate constructions for bosons (symmetric states) and fermions (antisymmetric states), which embodies the Pauli exclusion principle for the latter.
- **TLDR:** It is the foundational state space for Quantum Field Theory (QFT), where particles are treated as excitations of a field, and is operated on by creation and annihilation operators that add or remove particles from a state.

# Fock Space

### Introduction

In elementary quantum mechanics, systems are typically analyzed with a fixed number of particles, such as the single electron in a hydrogen atom. However, many phenomena in modern physics, particularly in high-energy particle physics and condensed matter theory, involve processes where particles are created and destroyed. To describe such systems, a more sophisticated mathematical structure is required. The **Fock space** is an algebraic construction, specifically a Hilbert space, that provides the state space for a quantum mechanical system with a variable or undefined number of particles. It is the bedrock upon which [[Notes/2025/10/06/Foundational Principles of Quantum Mechanics\|second quantization]] and Quantum Field Theory (QFT) are built.

---

## I. Construction of the Fock Space

The core idea behind Fock space is to combine the state spaces for all possible particle numbers into a single, larger space.

1.  **Single-Particle Hilbert Space ($\mathcal{H}_1$)**: We begin with the standard Hilbert space for a single particle, $\mathcal{H}_1$. A vector (or "ket") $|\psi\rangle \in \mathcal{H}_1$ describes the complete state of one particle.

2.  **N-Particle Hilbert Space ($\mathcal{H}_N$)**: The state of a system with $N$ distinguishable particles is described by the tensor product of $N$ single-particle spaces: $\mathcal{H}_N = \mathcal{H}_1^{\otimes N} = \mathcal{H}_1 \otimes \mathcal{H}_1 \otimes \cdots \otimes \mathcal{H}_1$.

3.  **The Vacuum State ($\mathcal{H}_0$)**: We must also account for the possibility of having zero particles. This state, known as the **vacuum state**, is denoted by $|0\rangle$ or $|\text{vac}\rangle$. It is a normalized vector that spans a one-dimensional complex Hilbert space, $\mathcal{H}_0 \cong \mathbb{C}$.

4.  **The Full Fock Space ($\mathcal{F}$)**: The Fock space is constructed as the **direct sum** of the Hilbert spaces for each particle number $N$, from zero to infinity.

    $$
    \mathcal{F} = \mathcal{H}_0 \oplus \mathcal{H}_1 \oplus \mathcal{H}_2 \oplus \cdots = \bigoplus_{N=0}^{\infty} \mathcal{H}_N
    $$

A general state $|\Psi\rangle$ in the Fock space is a superposition of states with different, definite particle numbers: $|\Psi\rangle = c_0|0\rangle + c_1|\psi_1\rangle + c_2|\psi_2\rangle + \dots$, where $|\psi_N\rangle \in \mathcal{H}_N$.

---

## II. Particle Statistics: Bosons and Fermions

For systems of **identical particles**, the simple tensor product construction is insufficient because it includes states that are not physically realized. The wavefunctions of identical particles must exhibit specific symmetries upon particle exchange.

### 1. Bosonic Fock Space ($\mathcal{F}_S$)

For **bosons** (particles with integer spin, e.g., photons, gluons), the multi-particle state vector must be **symmetric** under the exchange of any two particles. We therefore replace the simple tensor product space $\mathcal{H}_N$ with its symmetric subspace, $\mathcal{H}_N^{(S)}$.

The bosonic Fock space is then the direct sum of these symmetric N-particle spaces:

$$
\mathcal{F}_S = \bigoplus_{N=0}^{\infty} \mathcal{H}_N^{(S)}
$$

### 2. Fermionic Fock Space ($\mathcal{F}_A$)

For **fermions** (particles with half-integer spin, e.g., electrons, quarks), the multi-particle state vector must be **antisymmetric** under the exchange of any two particles. This mathematical requirement is the origin of the **Pauli Exclusion Principle**. We replace $\mathcal{H}_N$ with its antisymmetric subspace, $\mathcal{H}_N^{(A)}$.

The fermionic Fock space is the direct sum of these antisymmetric N-particle spaces:

$$
\mathcal{F}_A = \bigoplus_{N=0}^{\infty} \mathcal{H}_N^{(A)}
$$

> **Note:** The antisymmetry requirement for fermions implies that if two particles were to occupy the same single-particle state, the total state vector would be zero. This is the formal statement of the Pauli Exclusion Principle: no two identical fermions can occupy the same quantum state.

---

## III. Occupation Number Representation

A more intuitive and practical basis for the Fock space is the **occupation number representation**. We start by choosing a complete orthonormal basis $\{|\phi_1\rangle, |\phi_2\rangle, \dots\}$ for the single-particle Hilbert space $\mathcal{H}_1$. Any N-particle state can then be uniquely specified by stating the number of particles, $n_k$, that occupy each single-particle state $|\phi_k\rangle$.

A basis vector in the Fock space is written as:

$$
|n_1, n_2, n_3, \dots \rangle
$$

where $n_k$ is the occupation number of the $k$-th state. The total number of particles is $N = \sum_k n_k$.

*   For **bosons**, any occupation number is allowed: $n_k \in \{0, 1, 2, \dots\}$.
*   For **fermions**, the Pauli exclusion principle restricts the occupation numbers to $n_k \in \{0, 1\}$.

---

## IV. Creation and Annihilation Operators

The true power of the Fock space formalism is realized through the introduction of operators that change the particle number.

*   **Annihilation Operator ($a_k$)**: Removes (annihilates) one particle from the single-particle state $|\phi_k\rangle$.
*   **Creation Operator ($a_k^\dagger$)**: Adds (creates) one particle in the single-particle state $|\phi_k\rangle$.

These operators are defined by their action on the occupation number basis states. For bosons:
$a_k |n_1, \dots, n_k, \dots \rangle = \sqrt{n_k} |n_1, \dots, n_k-1, \dots \rangle$
$a_k^\dagger |n_1, \dots, n_k, \dots \rangle = \sqrt{n_k+1} |n_1, \dots, n_k+1, \dots \rangle$

The entire Fock space can be generated by repeatedly applying creation operators to the vacuum state, which is defined as the state annihilated by all annihilation operators: $a_k |0\rangle = 0$ for all $k$.

### Commutation and Anticommutation Relations

The fundamental nature of the particles is encoded in the algebraic relations these operators satisfy.

*   **For Bosons**, they obey **canonical commutation relations**:
    $$
    [a_i, a_j] = 0, \quad [a_i^\dagger, a_j^\dagger] = 0, \quad [a_i, a_j^\dagger] = \delta_{ij}
    $$
*   **For Fermions**, they obey **canonical anticommutation relations**:
    $$
    \{c_i, c_j\} = 0, \quad \{c_i^\dagger, c_j^\dagger\} = 0, \quad \{c_i, c_j^\dagger\} = \delta_{ij}
    $$
    where $\{A, B\} = AB + BA$ is the anticommutator. The relation $\{c_i^\dagger, c_i^\dagger\} = 2(c_i^\dagger)^2 = 0$ is another way of stating the Pauli principle: one cannot create two identical fermions in the same state.

---

### Conclusion

Fock space provides an elegant and indispensable mathematical framework for describing quantum systems where particle number is not conserved. By combining the state spaces for all possible particle counts and properly accounting for particle statistics, it allows for a consistent description of particle creation and annihilation. This formalism is not merely a mathematical convenience; it is the essential language of quantum field theory, condensed matter physics, and quantum optics, enabling the description of phenomena ranging from particle collisions in the [[Notes/2025/10/13/Standard Model\|Standard Model]] to collective excitations in solids and the quantum nature of light.
