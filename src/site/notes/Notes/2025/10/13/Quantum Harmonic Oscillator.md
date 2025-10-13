---
{"dg-publish":true,"permalink":"/notes/2025/10/13/quantum-harmonic-oscillator/"}
---

#quantum-mechanics #physics #harmonic-oscillator

[[Quantum Harmonic Oscillator.canvas\|Quantum Harmonic Oscillator.canvas]]

> - The Quantum Harmonic Oscillator (QHO) is a cornerstone model in quantum mechanics, describing a particle subject to a quadratic potential, analogous to a mass on a spring.
> - Its energy levels are quantized (discrete) and equally spaced, with the energy of the $n$-th state given by $E_n = \hbar\omega(n + 1/2)$.
> - A key feature is the non-zero ground state energy, $E_0 = \frac{1}{2}\hbar\omega$, known as the zero-point energy, a direct consequence of the Heisenberg Uncertainty Principle.
> - The problem is most elegantly solved using the algebraic method, which introduces [[Notes/2025/10/13/Creation and Annihilation Operators\|Creation and Annihilation Operators]] that move the system between energy levels.
> - The QHO serves as a fundamental approximation for a vast range of physical systems near a stable equilibrium, including molecular vibrations, lattice vibrations in solids (phonons), and modes of the electromagnetic field (photons).

# The Quantum Harmonic Oscillator

### Introduction

The Quantum Harmonic Oscillator (QHO) is one of the most important model systems in quantum mechanics. It is the quantum-mechanical analogue of the classical harmonic oscillator, which describes any system that experiences a restoring force proportional to its displacement from an equilibrium position (like a mass on a spring). Its significance stems from two main facts: it is one of the few quantum-mechanical systems for which an exact, analytical solution is known, and it serves as an excellent approximation for a wide variety of physical phenomena. Any system near a point of stable equilibrium can be approximated as a harmonic oscillator. This makes the QHO indispensable for understanding phenomena such as the vibrations of atoms in molecules and crystal lattices, and the quantization of fields, like the electromagnetic field in quantum field theory.

This note will explore the QHO, focusing on the powerful algebraic method that not only solves the system but also provides deep physical insight into its structure.

### The Hamiltonian and the Schrödinger Equation

In classical mechanics, the Hamiltonian (total energy) for a one-dimensional harmonic oscillator is given by the sum of its kinetic and potential energies:
$$
H = \frac{p^2}{2m} + \frac{1}{2}kx^2
$$
Using the relationship between the spring constant $k$ and the angular frequency $\omega$ ($k = m\omega^2$), this can be rewritten as:
$$
H = \frac{p^2}{2m} + \frac{1}{2}m\omega^2x^2
$$

To transition to quantum mechanics, we promote the position $x$ and momentum $p$ to their corresponding operators, $\hat{x}$ and $\hat{p}$. Following the [[Notes/2025/10/06/Foundational Principles of Quantum Mechanics\|Foundational Principles of Quantum Mechanics]], the Hamiltonian operator becomes:
$$
\hat{H} = \frac{\hat{p}^2}{2m} + \frac{1}{2}m\omega^2\hat{x}^2
$$
The energy levels of the system are the eigenvalues $E$ found by solving the time-independent Schrödinger equation, $\hat{H}|\psi\rangle = E|\psi\rangle$. In the position representation, where $\hat{x} = x$ and $\hat{p} = -i\hbar\frac{d}{dx}$, this becomes a second-order differential equation:
$$
\left(-\frac{\hbar^2}{2m}\frac{d^2}{dx^2} + \frac{1}{2}m\omega^2x^2\right)\psi(x) = E\psi(x)
$$
While this equation can be solved directly (yielding solutions involving Hermite polynomials and Gaussian functions), a far more elegant and insightful approach is the algebraic method.

### The Algebraic Method: Creation and Annihilation Operators

The algebraic method reformulates the problem in terms of two non-Hermitian operators, known as **ladder operators**. As detailed in [[Notes/2025/10/13/Creation and Annihilation Operators\|Creation and Annihilation Operators]], we define the **annihilation operator** $\hat{a}$ and the **creation operator** $\hat{a}^\dagger$:
$$
\hat{a} = \sqrt{\frac{m\omega}{2\hbar}}\left(\hat{x} + \frac{i}{m\omega}\hat{p}\right)
$$
$$
\hat{a}^\dagger = \sqrt{\frac{m\omega}{2\hbar}}\left(\hat{x} - \frac{i}{m\omega}\hat{p}\right)
$$
These operators are adjoints of each other. Their fundamental property is their commutation relation, which can be derived from the canonical commutation relation $[\hat{x}, \hat{p}] = i\hbar$:
$$
[\hat{a}, \hat{a}^\dagger] = 1
$$
The power of this formalism is revealed when the Hamiltonian is expressed in terms of $\hat{a}$ and $\hat{a}^\dagger$. After some algebra, we find a remarkably simple form:
$$
\hat{H} = \hbar\omega\left(\hat{a}^\dagger\hat{a} + \frac{1}{2}\right)
$$
This algebraic structure simplifies the problem of finding the energy eigenvalues immensely.

### Energy Eigenstates and Quantization

To find the energy spectrum, we introduce the **number operator**, $\hat{N} = \hat{a}^\dagger\hat{a}$. The Hamiltonian can then be written as:
$$
\hat{H} = \hbar\omega\left(\hat{N} + \frac{1}{2}\right)
$$
Since $\hat{H}$ and $\hat{N}$ commute, they share a common set of eigenstates. Let's denote an eigenstate of $\hat{N}$ as $|n\rangle$ with a corresponding eigenvalue $n$:
$$
\hat{N}|n\rangle = n|n\rangle
$$
Applying the Hamiltonian to this state gives:
$$
\hat{H}|n\rangle = \hbar\omega\left(\hat{N} + \frac{1}{2}\right)|n\rangle = \hbar\omega\left(n + \frac{1}{2}\right)|n\rangle
$$
This equation immediately reveals the energy eigenvalues of the Quantum Harmonic Oscillator:
$$
E_n = \hbar\omega\left(n + \frac{1}{2}\right), \quad \text{for } n = 0, 1, 2, \dots
$$
This result has profound physical implications:
1.  **Energy Quantization**: The energy of the oscillator cannot take any continuous value; it is restricted to a discrete set of levels.
2.  **Equal Spacing**: The energy levels are equally spaced, with a separation of $\Delta E = \hbar\omega$.
3.  **Zero-Point Energy**: The lowest possible energy state, or **ground state** ($n=0$), has a non-zero energy $E_0 = \frac{1}{2}\hbar\omega$. This "zero-point energy" is a purely quantum effect, a direct consequence of the Heisenberg Uncertainty Principle. A particle in a potential well can never be perfectly still at the bottom, as this would imply precise knowledge of both its position and momentum.

### The Ladder of States

The names "creation" and "annihilation" operators come from their effect on the energy eigenstates. It can be shown that:
-   **Annihilation**: $\hat{a}|n\rangle = \sqrt{n}|n-1\rangle$. The operator $\hat{a}$ lowers the state by one energy level, destroying one quantum of energy $\hbar\omega$.
-   **Creation**: $\hat{a}^\dagger|n\rangle = \sqrt{n+1}|n+1\rangle$. The operator $\hat{a}^\dagger$ raises the state by one energy level, creating one quantum of energy.

This "ladder" of states must have a bottom rung. The ground state $|0\rangle$ is defined as the state that cannot be lowered further, which means it must be annihilated by the annihilation operator:
$$
\hat{a}|0\rangle = 0
$$
All other energy eigenstates, the **excited states**, can be generated by repeatedly applying the creation operator to the ground state:
$$
|n\rangle = \frac{(\hat{a}^\dagger)^n}{\sqrt{n!}}|0\rangle
$$

### Conclusion

The Quantum Harmonic Oscillator is a pillar of modern physics. Its exact solution provides a deep understanding of energy quantization and the existence of zero-point energy. The elegant algebraic method, centered on creation and annihilation operators, not only simplifies the mathematics but also introduces a powerful formalism that is central to quantum field theory, where these operators are used to create and destroy particles. From the vibrations of a single molecule to the quantum nature of light itself, the principles of the QHO provide the fundamental language for describing the quantized world.

