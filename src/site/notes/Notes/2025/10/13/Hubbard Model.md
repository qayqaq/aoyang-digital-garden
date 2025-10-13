---
{"dg-publish":true,"permalink":"/notes/2025/10/13/hubbard-model/"}
---

#condensed_matter_physics #quantum_mechanics #many_body_problem #strongly_correlated_systems
[[Hubbard model.canvas\|Hubbard model.canvas]]

- The **Hubbard model** is a foundational, simplified model in condensed matter physics that describes interacting particles (typically electrons) on a lattice.
-   It captures the fundamental competition between two effects: the **kinetic energy** ($t$), which allows particles to hop between lattice sites, and the **on-site potential energy** ($U$), which represents the Coulomb repulsion when two particles occupy the same site.
-   The model successfully explains the transition from a **metal** (where electrons are delocalized and conduct electricity) to a **Mott insulator** (where strong repulsion localizes electrons, preventing conduction), a phenomenon that cannot be described by classical band theory.
-   Despite its simplicity, the Hubbard model is believed to contain the essential physics for complex phenomena like **antiferromagnetism** and **high-temperature superconductivity**, but it is notoriously difficult to solve exactly in dimensions greater than one.

# The Hubbard Model

## Introduction

The **Hubbard model** is one of the most important and intensely studied models in theoretical [[Notes/2025/10/13/Condensed Matter Physics\|condensed matter physics]]. Proposed in the 1960s by John Hubbard, Martin Gutzwiller, and Junjiro Kanamori, it provides a simplified yet powerful framework for *understanding the behavior of interacting electrons in a [[Notes/2025/10/13/Crystal Lattice\|Crystal Lattice]]*. Its significance lies in its ability to capture the essential physics of **[[Notes/2025/10/13/Electron Correlation\|Electron Correlation]]**—the idea that the motion of any single electron is strongly influenced by the presence of all other electrons.

At its core, the model describes a competition between two fundamental processes: *the tendency of electrons to delocalize and lower their kinetic energy by hopping between atomic sites*, and *the tendency to localize to avoid the high energy cost of occupying the same site as another electron due to Coulomb repulsion*. This simple-sounding conflict gives rise to a rich spectrum of complex phenomena, including metal-insulator transitions, magnetism, and potentially high-temperature superconductivity, making the Hubbard model a cornerstone for the study of strongly correlated systems.

## The Hamiltonian

The Hubbard model is defined by a deceptively simple Hamiltonian, which is an operator representing the total energy of the system. It consists of two main parts: a kinetic term and a potential (interaction) term.

$$
\hat{H} = -t \sum_{\langle i,j \rangle, \sigma} (c_{i\sigma}^\dagger c_{j\sigma} + c_{j\sigma}^\dagger c_{i\sigma}) + U \sum_i \hat{n}_{i\uparrow} \hat{n}_{i\downarrow}
$$

Let's break down each component:

1. **The Kinetic (Hopping) Term**:
    $$
    \hat{K} = -t \sum_{\langle i,j \rangle, \sigma} (c_{i\sigma}^\dagger c_{j\sigma} + c_{j\sigma}^\dagger c_{i\sigma})
    $$
    * $c_{i\sigma}^\dagger$ and $c_{j\sigma}$ are the **[[Notes/2025/10/13/Creation and Annihilation Operators\|Creation and Annihilation Operators]]**, respectively. $c_{i\sigma}^\dagger$ creates an electron with spin $\sigma$ (either $\uparrow$ or $\downarrow$) at lattice site $i$, while $c_{j\sigma}$ destroys an electron with the same spin at site $j$.
    * The sum $\sum_{\langle i,j \rangle}$ runs over all pairs of **nearest-neighbor** sites on the lattice.
    * The parameter $t$ is the **hopping amplitude**. It quantifies the kinetic energy gained when an electron moves from one site to an adjacent one. A larger $t$ means electrons are more mobile and delocalized. This term promotes metallic behavior.

2.  **The Potential (On-site Repulsion) Term**:
    $$
    \hat{V} = U \sum_i \hat{n}_{i\uparrow} \hat{n}_{i\downarrow}
    $$
    *   $\hat{n}_{i\sigma} = c_{i\sigma}^\dagger c_{i\sigma}$ is the **number operator**, which counts the number of electrons with spin $\sigma$ at site $i$.
    *   The product $\hat{n}_{i\uparrow} \hat{n}_{i\downarrow}$ is only non-zero if site $i$ is occupied by both a spin-up and a spin-down electron (i.e., it is doubly occupied).
    *   The parameter $U$ is the **on-site Coulomb repulsion**. It represents the energy cost of placing two electrons on the same lattice site. A larger $U$ means stronger repulsion. This term promotes electron localization.

The physics of the Hubbard model is governed by the ratio of these two parameters, $U/t$.

## Key Physical Phenomena

The competition between hopping ($t$) and repulsion ($U$) leads to distinct physical regimes.

### The Metal-Insulator Transition (Mott Transition)

Consider a system with an average of one electron per site (known as **half-filling**).
*   **Weak Correlation ($U/t \ll 1$)**: When the repulsion is weak, the kinetic term dominates. Electrons can easily hop from site to site, delocalizing throughout the lattice to form wide energy bands. The system behaves like a **metal**, as predicted by conventional band theory.
*   **Strong Correlation ($U/t \gg 1$)**: When the repulsion is strong, the energy cost $U$ to doubly occupy a site is prohibitive. Each electron becomes effectively locked to its own lattice site to avoid this penalty. Electron motion is suppressed, and the system becomes an electrical insulator. This state is known as a **Mott insulator**.

> The existence of a Mott insulator is a profound result of electron correlation. Standard band theory, which ignores interactions, would incorrectly predict that a system with a half-filled band should always be a metal. The Hubbard model provides the simplest explanation for why materials like NiO are insulators.

### Antiferromagnetism

In the strong-coupling limit ($U/t \gg 1$) at half-filling, the Hubbard model gives rise to magnetism. Since each site is occupied by one electron, the only remaining degree of freedom is its spin. While electrons cannot easily hop to occupied neighboring sites, they can do so through a "virtual" quantum process: an electron briefly hops to a neighbor (costing energy $U$), and then hops back.

This process, known as **superexchange**, results in an effective interaction between the spins on neighboring sites. The total energy of the system is lowered if adjacent spins are anti-aligned (antiparallel). This leads to an **antiferromagnetic** ground state, where spins on the lattice order in a checkerboard pattern ($\uparrow \downarrow \uparrow \downarrow \dots$).

### High-Temperature Superconductivity

The two-dimensional Hubbard model is widely considered a minimal model for understanding high-temperature superconductivity in cuprate materials. The physics of these materials is thought to originate in the copper-oxide planes, which can be modeled as a 2D square lattice.

The parent compounds of cuprates are Mott insulators. When they are doped (by adding or removing electrons, moving the system away from half-filling), antiferromagnetism is suppressed and unconventional **d-wave superconductivity** emerges. It is hypothesized that the same magnetic fluctuations that cause antiferromagnetism at half-filling might mediate the pairing of electrons that leads to superconductivity when the system is doped. Proving this connection remains one of the most significant unsolved problems in condensed matter physics.

## Solving the Hubbard Model

Despite its simple form, solving the Hubbard model is extremely challenging due to its quantum many-body nature.
-   **Exact Solutions**: An exact solution using the Bethe Ansatz exists only for the one-dimensional case. No general exact solution is known for two or three dimensions.
-   **Numerical Methods**: For higher dimensions, physicists rely on sophisticated numerical techniques:
    -   **Exact Diagonalization**: Can solve the model exactly but is limited to very small systems (around 20-30 sites) due to the exponential growth of the Hilbert space.
    -   **Quantum Monte Carlo (QMC)**: A powerful method, particularly [[Notes/2025/10/13/Determinant Quantum Monte Carlo\|Determinant Quantum Monte Carlo]], that can simulate larger systems. However, it often suffers from the "fermion sign problem" away from half-filling, which makes simulations at low temperatures numerically unstable.
    -   **Density Matrix Renormalization Group (DMRG)**: Extremely accurate for 1D systems and quasi-1D systems (ladders and strips).
    -   **Dynamical Mean-Field Theory (DMFT)**: An approximation that becomes exact in the limit of infinite dimensions and provides valuable insights for 3D systems.

## Conclusion

The Hubbard model stands as a paradigm of "simple models, complex physics." It distills the intricate problem of interacting electrons in solids into a manageable form that captures the essence of electron correlation. It provides the theoretical foundation for understanding Mott insulators and antiferromagnetism and remains the leading candidate for explaining the mystery of high-temperature superconductivity. Its continued study, both through theoretical analysis and through experimental realizations using ultracold atoms in optical lattices, pushes the frontiers of our understanding of quantum matter.

