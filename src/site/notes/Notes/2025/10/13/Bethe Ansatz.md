---
{"dg-publish":true,"permalink":"/notes/2025/10/13/bethe-ansatz/","tags":["#physics/condensed-matter","#quantum-mechanics","#integrable-systems","#statistical-mechanics"]}
---

#physics/condensed-matter #quantum-mechanics #integrable-systems #statistical-mechanics
[[Bethe Ansatz.canvas\|Bethe Ansatz.canvas]]

- **TLDR**: The Bethe Ansatz is an exact analytical method for solving certain one-dimensional quantum many-body systems, known as integrable systems.
- **TLDR**: It proposes a specific form (an "ansatz") for the many-body wavefunction, constructing it as a superposition of plane waves that accounts for particle interactions.
- **TLDR**: Interactions between particles are systematically handled as two-body scattering events, each contributing a specific phase shift to the wavefunction.
- **TLDR**: By applying periodic boundary conditions, the method yields a set of coupled, non-linear algebraic equations—the Bethe equations—whose solutions determine the allowed particle momenta and the system's energy spectrum.

# Bethe Ansatz

### Introduction

The **Bethe Ansatz** is a powerful and elegant mathematical technique used to find the exact energy eigenvalues and eigenstates of certain one-dimensional quantum many-body systems. First formulated by Hans Bethe in 1931 to solve the one-dimensional Heisenberg model of magnetism, it has since become a cornerstone of theoretical physics, particularly in the study of condensed matter and statistical mechanics. Its significance lies in its ability to provide exact, non-perturbative solutions for **integrable systems**—models where complex many-body interactions can be systematically decomposed into a series of two-body scattering events. This allows for a precise understanding of phenomena in strongly correlated systems, where approximation methods often fail.

---

## 1. The Core Idea: An Educated Guess for the Wavefunction

The term **"ansatz"** is German for "approach" or "educated guess." The Bethe Ansatz is fundamentally a specific, well-motivated guess for the mathematical form of a system's many-body wavefunction, $\Psi$.

For a system of $N$ non-interacting particles on a line, the wavefunction can be written as a simple product of plane waves, where each particle $j$ has a well-defined momentum $k_j$. When interactions are introduced, this simple picture breaks down.

The Bethe Ansatz proposes that the true wavefunction is a superposition of all possible plane waves corresponding to every permutation of the particle momenta. The key insight is that the coefficients of this superposition are not arbitrary; they are determined by the physics of two-particle scattering.

Consider two particles with momenta $k_1$ and $k_2$ at positions $x_1$ and $x_2$. The wavefunction in the region where $x_1 < x_2$ can be written as:

$$
\Psi(x_1, x_2) = A_{12} e^{i(k_1 x_1 + k_2 x_2)} + A_{21} e^{i(k_2 x_1 + k_1 x_2)}
$$

Here, the first term represents particles with momenta $k_1$ and $k_2$, while the second term represents the same particles having exchanged their momenta. The ratio of the amplitudes, $A_{21}/A_{12}$, defines the **two-body scattering matrix (S-matrix)**, often expressed as a pure phase factor for elastic scattering:

$$
S(k_1, k_2) = e^{i\theta(k_1, k_2)}
$$

The phase shift $\theta(k_1, k_2)$ encapsulates the entire effect of the interaction between the two particles. The Bethe Ansatz generalizes this idea to $N$ particles by asserting that any many-body scattering event can be factorized into a sequence of independent two-body scatterings. This factorization is a defining feature of integrable systems.

## 2. Application: The 1D Heisenberg Spin Chain

The original and most famous application of the Bethe Ansatz is the one-dimensional Heisenberg antiferromagnetic model. The Hamiltonian for a chain of $L$ spin-1/2 particles is:

$$
H = J \sum_{i=1}^{L} \vec{S}_i \cdot \vec{S}_{i+1} = J \sum_{i=1}^{L} \left( S_i^x S_{i+1}^x + S_i^y S_{i+1}^y + S_i^z S_{i+1}^z \right)
$$

where $J > 0$ for the antiferromagnetic case.

The problem is solved by considering excitations over a reference state. The simplest reference state is the ferromagnetic ground state where all spins point down, denoted $|\downarrow\downarrow\dots\downarrow\rangle$. An excitation, called a **magnon**, is created by flipping a single spin.

-   **One-Magnon State**: A single spin flip at site $j$ is not an eigenstate. The true eigenstate is a delocalized plane wave of a spin flip with momentum $k$:
    $$
    |k\rangle = \sum_{j=1}^{L} e^{ikj} |\dots\downarrow\uparrow_j\downarrow\dots\rangle
    $$
    The energy of this single magnon is $\epsilon(k) = J(1 - \cos k)$.

-   **Two-Magnon State**: For two magnons with momenta $k_1$ and $k_2$, the Bethe Ansatz for the wavefunction (coefficients of the state) at positions $j_1 < j_2$ is:
    $$
    \Psi(j_1, j_2) = e^{i(k_1 j_1 + k_2 j_2)} + e^{i\theta(k_1, k_2)} e^{i(k_2 j_1 + k_1 j_2)}
    $$
    By substituting this into the Schrödinger equation $H|\Psi\rangle = E|\Psi\rangle$, one can solve for the two-magnon scattering phase shift $\theta(k_1, k_2)$. For the Heisenberg model, it is found to be:
    $$
    \cot\left(\frac{\theta}{2}\right) = \frac{\cot(k_1/2) - \cot(k_2/2)}{2}
    $$

This process demonstrates how the interaction term in the Hamiltonian dictates the precise form of the scattering phase shift.

## 3. The Bethe Equations

The allowed values of the momenta $\{k_j\}$ are not continuous but are quantized by the system's boundary conditions. Typically, **periodic boundary conditions** are imposed, meaning the chain is treated as a closed ring ($S_{L+1} = S_1$).

This condition requires that when a particle (or magnon) travels around the entire ring of length $L$, its wavefunction must return to its original value. This journey imparts two types of phase shifts:
1.  A **kinematic phase** from its own momentum, $e^{ik_j L}$.
2.  A **scattering phase** from interacting with every other particle in the system, $\prod_{l \neq j} S(k_j, k_l)$.

For the wavefunction to be single-valued, these phases must cancel each other out. This leads to a set of coupled equations, one for each particle $j$:

$$
e^{ik_j L} \prod_{l \neq j}^{N} S(k_j, k_l) = 1 \quad \text{for } j = 1, \dots, N
$$

Taking the natural logarithm of this expression yields the famous **Bethe equations**:

$$
L k_j + \sum_{l \neq j}^{N} \theta(k_j, k_l) = 2\pi I_j
$$

Here, the $\{I_j\}$ are a set of distinct integers or half-integers known as **Bethe quantum numbers**, which label the specific many-body eigenstate.

> Solving this set of $N$ coupled, non-linear, transcendental equations for the $N$ unknown momenta $\{k_j\}$ is the central computational challenge of the method. Once a valid set of momenta is found, the total energy of the system is simply the sum of the individual particle energies:
> $$
> E = \sum_{j=1}^{N} \epsilon(k_j)
> $$

## 4. Generalizations and Broader Context

The principles of the Bethe Ansatz extend far beyond the Heisenberg model.
-   **Integrability and the Yang-Baxter Equation**: The reason the Bethe Ansatz works is that the underlying models are **integrable**. A key feature of such systems is that three-particle scattering can be consistently factorized into a product of two-particle scatterings. The mathematical expression of this consistency is the **Yang-Baxter equation**, which provides a powerful and abstract framework for identifying and solving integrable models.
-   **Other Models**: The technique has been successfully applied to other important 1D models, including the Lieb-Liniger model (interacting bosons), the Hubbard model, and various quantum field theories.
-   **Thermodynamics**: In the limit of an infinite number of particles, the Bethe equations can be used to derive the thermodynamics of the system, a method known as the Thermodynamic Bethe Ansatz (TBA).

### Conclusion

The Bethe Ansatz is a profound and beautiful method that provides a rare window into the exact behavior of interacting quantum many-body systems. By postulating a wavefunction built from two-body scattering phase shifts, it transforms a complex quantum problem into the task of solving a set of algebraic equations. While limited to one-dimensional integrable systems, the exact solutions it provides are invaluable benchmarks for numerical methods and have deeply shaped our understanding of magnetism, quantum liquids, and the fundamental principles of quantum statistical mechanics. Its legacy continues in modern physics, with connections to topics as diverse as cold atomic gases, string theory, and the mathematics of knot theory.

