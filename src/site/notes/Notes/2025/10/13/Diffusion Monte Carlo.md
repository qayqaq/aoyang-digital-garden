---
{"dg-publish":true,"permalink":"/notes/2025/10/13/diffusion-monte-carlo/","tags":["#computational_physics","#quantum_mechanics","#numerical_methods","#monte_carlo","#projector_methods"]}
---

#computational_physics #quantum_mechanics #numerical_methods #monte_carlo #projector_methods
[[Diffusion Monte Carlo.canvas\|Diffusion Monte Carlo.canvas]]

-   **Core Concept**: A highly accurate [[Notes/2025/10/13/Quantum Monte Carlo\|Quantum Monte Carlo]] algorithm that numerically solves the Schrödinger equation to find the exact ground-state properties of a [[Notes/2025/10/13/Quantum Many-Body System\|Quantum Many-Body System]].
-   **Mechanism**: It simulates the Schrödinger equation in imaginary time, where it becomes analogous to a classical diffusion-reaction process. A population of "walkers" (representing particle configurations) diffuses, drifts, and is replicated or eliminated ("branches") to converge on the ground-state distribution.
-   **Relationship to VMC**: DMC is a [[Notes/2025/10/13/Projector Quantum Monte Carlo\|Projector Quantum Monte Carlo]] method that systematically improves upon an initial guess. It uses a high-quality trial wavefunction from a [[Notes/2025/10/13/Variational Monte Carlo\|Variational Monte Carlo]] calculation for **importance sampling**, which guides the simulation and dramatically improves its efficiency.
-   **Key Advantage**: For bosonic systems, DMC is, in principle, an exact method, limited only by statistical and time-step errors. It is considered a benchmark for accuracy in computational physics.
-   **Primary Limitation**: For fermionic systems (like electrons), DMC is afflicted by the **fermion sign problem**. This is overcome using the **fixed-node approximation**, which makes the method variational but still exceptionally accurate, depending on the quality of the trial wavefunction's nodes.

# Diffusion Monte Carlo

## 1. Introduction

**Diffusion Monte Carlo (DMC)** is a premier computational algorithm in the [[Notes/2025/10/13/Quantum Monte Carlo\|Quantum Monte Carlo]] family, renowned for its ability to calculate the ground-state properties of [[Notes/2025/10/13/Quantum Many-Body System\|quantum many-body systems]] with exceptionally high accuracy. It belongs to the class of [[Notes/2025/10/13/Projector Quantum Monte Carlo\|Projector Quantum Monte Carlo]] methods, which are designed to stochastically project out the exact ground-state wavefunction from an approximate initial trial state.

The power of DMC lies in its direct numerical simulation of the Schrödinger equation, transformed into a diffusion-like process in imaginary time. By evolving a population of configurations, or "walkers," according to simple rules of diffusion, drift, and branching, the algorithm can filter out excited-state contributions and converge to the true ground state. While it is, in principle, an exact method for bosonic systems, its application to fermions requires the well-controlled **fixed-node approximation**, which nevertheless establishes DMC as a gold-standard benchmark for accuracy in quantum chemistry and condensed matter physics.

## 2. Theoretical Foundation: The Imaginary-Time Schrödinger Equation

The core principle of DMC is the formal analogy between the quantum mechanical Schrödinger equation and a classical diffusion equation. This connection is revealed by performing a Wick rotation into **imaginary time**, $\tau = it/\hbar$.

The time-dependent Schrödinger equation is:
$$
i\hbar \frac{\partial \Psi(\mathbf{R}, t)}{\partial t} = \hat{H}\Psi(\mathbf{R}, t)
$$
Substituting $\tau$ for $t$, the equation transforms into:
$$
-\frac{\partial \Psi(\mathbf{R}, \tau)}{\partial \tau} = \hat{H}\Psi(\mathbf{R}, \tau) = \left(-\frac{\hbar^2}{2m}\sum_i \nabla_i^2 + V(\mathbf{R})\right)\Psi(\mathbf{R}, \tau)
$$
This equation has the mathematical form of a classical reaction-diffusion equation. The wavefunction $\Psi(\mathbf{R}, \tau)$ can be interpreted as the density of a population of diffusing particles, where:
-   The **kinetic energy term** ($-\frac{\hbar^2}{2m}\sum_i \nabla_i^2$) acts as a **diffusion** operator, causing the particles to spread out via random walks.
-   The **potential energy term** ($V(\mathbf{R})$) acts as a position-dependent **reaction rate** or **branching** term, causing the population to grow in regions of low potential and shrink in regions of high potential.

As explained in [[Notes/2025/10/13/Projector Quantum Monte Carlo\|Projector Quantum Monte Carlo]], evolving any initial state forward in imaginary time using the operator $e^{-\tau\hat{H}}$ causes all higher-energy components to decay exponentially faster than the ground-state component. Therefore, the long-time distribution of the walker population governed by this equation will converge to the ground-state wavefunction $\Psi_0$.

## 3. The DMC Algorithm

The DMC algorithm simulates this imaginary-time evolution by manipulating an ensemble of **walkers**. Each walker represents a single point $\mathbf{R} = (\mathbf{r}_1, \dots, \mathbf{r}_N)$ in the $3N$-dimensional configuration space of the system. The simulation proceeds in discrete time steps $\Delta\tau$.

1.  **Initialization**: An initial population of walkers is generated, typically by sampling configurations from a [[Notes/2025/10/13/Variational Monte Carlo\|Variational Monte Carlo]] simulation according to the distribution $|\Psi_T(\mathbf{R})|^2$, where $\Psi_T$ is a high-quality trial wavefunction.

2.  **Iterative Evolution**: For a large number of time steps, the entire population of walkers is updated. For each walker, the following steps are performed:
    *   **Diffusion**: The walker's coordinates are displaced by a random vector drawn from a Gaussian distribution with zero mean and variance proportional to $\Delta\tau$. This step simulates the kinetic energy term.
    *   **Branching**: The walker is replicated or eliminated with a probability determined by its potential energy. A weight factor, $w = \exp\left(-\Delta\tau (V(\mathbf{R}) - E_{\text{ref}})\right)$, is calculated, where $E_{\text{ref}}$ is an estimate of the ground-state energy. The walker is then replaced by $\text{int}(w + \text{random number})$ copies of itself. This process selectively amplifies the population in low-energy regions.

3.  **Energy Update**: After each full step, the reference energy $E_{\text{ref}}$ is adjusted to keep the total walker population roughly constant. Once the system reaches a steady state, the average value of $E_{\text{ref}}$ provides a statistically precise estimate of the true ground-state energy, $E_0$.

## 4. Importance Sampling: Enhancing Efficiency

The "vanilla" DMC algorithm described above is numerically unstable for most realistic systems, as the potential energy $V(\mathbf{R})$ can diverge (e.g., Coulomb potential), causing wild fluctuations in the walker population. This is resolved using **importance sampling**.

Instead of simulating the wavefunction $\Psi$, the algorithm is modified to simulate the mixed distribution $f(\mathbf{R}, \tau) = \Psi_T(\mathbf{R})\Psi(\mathbf{R}, \tau)$, where $\Psi_T$ is the guiding wavefunction from VMC. The evolution equation for $f$ contains two crucial modifications:

1.  **Drift Term**: An additional deterministic velocity, or **drift**, term appears. This term, often called the "quantum force," is proportional to the gradient of the trial wavefunction, $\nabla \ln|\Psi_T(\mathbf{R})|$. It pushes walkers towards regions where the trial wavefunction has a larger amplitude, thus concentrating the computational effort in the most physically relevant areas.
2.  **Local Energy Branching**: The branching is no longer governed by the raw potential energy $V(\mathbf{R})$ but by the **local energy**, $E_L(\mathbf{R}) = \frac{\hat{H}\Psi_T(\mathbf{R})}{\Psi_T(\mathbf{R})}$. If $\Psi_T$ is a good approximation to the true ground state, $E_L(\mathbf{R})$ will be nearly constant across the configuration space. This dramatically reduces the fluctuations in the branching step, leading to a much more stable and efficient algorithm.

After the simulation, the distribution of walkers converges to $\Psi_T(\mathbf{R})\Psi_0(\mathbf{R})$, from which the exact ground-state energy $E_0$ can be extracted.

## 5. The Fixed-Node Approximation for Fermions

The DMC algorithm is, in principle, exact for bosons, whose ground-state wavefunction can always be chosen to be non-negative. For fermions, however, the Pauli exclusion principle requires the wavefunction to be antisymmetric, meaning it must have both positive and negative regions. This leads to the **fermion sign problem**: since the walker density must be positive, it cannot represent the true fermionic wavefunction.

The standard and highly successful solution is the **fixed-node approximation**.
> The **nodal surface** of a wavefunction is the high-dimensional surface where its value is exactly zero. These nodes separate the positive and negative regions. The fixed-node approximation assumes that the nodal surface of the true ground-state wavefunction is identical to that of the guiding trial wavefunction, $\Psi_T$.

The simulation is then confined to a single nodal region by imposing a boundary condition: any walker that attempts to cross a node is immediately removed from the simulation. This constraint solves the sign problem at the cost of introducing a systematic bias. The resulting **Fixed-Node DMC (FN-DMC)** energy is variational; it is an upper bound to the true ground-state energy. The accuracy of the result is therefore entirely dependent on the quality of the nodes provided by the trial wavefunction.

## 6. Conclusion

Diffusion Monte Carlo stands as one of the most powerful and accurate numerical methods for studying quantum ground states. By ingeniously mapping the Schrödinger equation onto a stochastic process, it provides a computational framework for solving the many-body problem with remarkable precision. Its synergy with [[Notes/2025/10/13/Variational Monte Carlo\|Variational Monte Carlo]] for importance sampling and the development of the fixed-node approximation have made it an indispensable tool for obtaining benchmark-quality results for a wide range of systems, from molecules and clusters to complex solids. Despite the inherent approximation for fermions, FN-DMC continues to push the frontiers of our understanding of strongly correlated quantum matter.
