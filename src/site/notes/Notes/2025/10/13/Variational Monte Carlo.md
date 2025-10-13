---
{"dg-publish":true,"permalink":"/notes/2025/10/13/variational-monte-carlo/"}
---

#computational_physics #quantum_mechanics #numerical_methods #monte_carlo #variational_methods
[[Variational Monte Carlo.canvas\|Variational Monte Carlo.canvas]]

-   **Core Concept**: A [[Notes/2025/10/13/Quantum Monte Carlo\|Quantum Monte Carlo]] method that approximates the ground-state properties of a [[Notes/2025/10/13/Quantum Many-Body System\|Quantum Many-Body System]].
-   **Underlying Principle**: It combines two fundamental ideas: the **variational principle** of quantum mechanics, which guarantees the calculated energy is an upper bound to the true ground-state energy, and **Monte Carlo integration**, which is used to evaluate the necessary high-dimensional integrals.
-   **How It Works**: The method involves (1) defining a physically-motivated, parameterized trial wavefunction, (2) using the Metropolis algorithm to sample configurations from the probability distribution defined by this wavefunction, and (3) optimizing the parameters to find the minimum possible energy for the chosen form of the wavefunction.
-   **Key Limitation**: The accuracy of the Variational Monte Carlo (VMC) method is entirely limited by the functional form of the trial wavefunction. It is a biased method whose quality depends on the user's ability to construct a good ansatz.
-   **Primary Role**: VMC is used both as a standalone method for efficient, approximate calculations and as an essential first step for more accurate but computationally intensive methods like [[Notes/2025/10/13/Diffusion Monte Carlo\|Diffusion Monte Carlo]].

# Variational Monte Carlo

## 1. Introduction

**Variational Monte Carlo (VMC)** is a foundational algorithm in the field of computational quantum physics, belonging to the broader class of [[Notes/2025/10/13/Quantum Monte Carlo\|Quantum Monte Carlo]] methods. Its purpose is to compute an approximate ground-state wavefunction and energy for a complex [[Notes/2025/10/13/Quantum Many-Body System\|Quantum Many-Body System]]. The method's power and elegance stem from its fusion of a core principle of quantum mechanics—the **variational principle**—with the numerical might of **Monte Carlo integration**.

VMC provides a direct and intuitive approach to tackling the "curse of dimensionality" that plagues many-body problems. By postulating a physically-motivated trial wavefunction, VMC uses stochastic sampling to efficiently evaluate the system's properties. The parameters within this trial wavefunction are then systematically optimized to find the best possible approximation to the true ground state. While its accuracy is inherently limited by the chosen form of the wavefunction, VMC is computationally robust and serves as an indispensable tool, often providing the starting point for more sophisticated QMC techniques.

## 2. Theoretical Foundation

The VMC method is built upon two key theoretical pillars: the variational principle and the use of Monte Carlo methods for high-dimensional integration.

### 2.1 The Variational Principle

The variational principle is a rigorous theorem in quantum mechanics that provides the formal basis for the entire method. It states that for any well-behaved trial wavefunction, $\Psi_T$, the expectation value of the energy calculated with this state is always greater than or equal to the true ground-state energy, $E_0$.

Mathematically, the variational energy, $E_V$, is given by the expectation value of the Hamiltonian operator, $\hat{H}$:
$$
E_V = \frac{\langle \Psi_T | \hat{H} | \Psi_T \rangle}{\langle \Psi_T | \Psi_T \rangle} \ge E_0
$$
This principle is immensely powerful. It transforms the problem of solving the Schrödinger equation into an optimization problem: by constructing a trial wavefunction $\Psi_T$ with a set of tunable parameters $\{\alpha\}$, we can systematically adjust these parameters to minimize $E_V$. The resulting minimized energy, $E_{\min}$, is the best possible approximation to $E_0$ that can be achieved with the chosen functional form of $\Psi_T$.

### 2.2 Monte Carlo Integration

For a many-body system of $N$ particles, the integrals in the expression for $E_V$ are $3N$-dimensional, making them impossible to solve analytically or with standard numerical quadrature. This is where Monte Carlo integration becomes essential.

First, we rewrite the variational energy expression in real-space coordinates $\mathbf{R} = (\mathbf{r}_1, \dots, \mathbf{r}_N)$:
$$
E_V = \frac{\int \Psi_T^*(\mathbf{R}) \hat{H} \Psi_T(\mathbf{R}) d\mathbf{R}}{\int |\Psi_T(\mathbf{R})|^2 d\mathbf{R}}
$$
We can rearrange this by defining a new quantity, the **local energy** $E_L(\mathbf{R})$:
$$
E_L(\mathbf{R}) = \frac{\hat{H}\Psi_T(\mathbf{R})}{\Psi_T(\mathbf{R})}
$$
The variational energy can now be expressed as the expectation value of the local energy, weighted by a probability distribution $P(\mathbf{R})$:
$$
E_V = \int \left( \frac{|\Psi_T(\mathbf{R})|^2}{\int |\Psi_T(\mathbf{R'})|^2 d\mathbf{R'}} \right) E_L(\mathbf{R}) d\mathbf{R} = \int P(\mathbf{R}) E_L(\mathbf{R}) d\mathbf{R}
$$
This form is perfectly suited for Monte Carlo evaluation. The integral is simply the average of the local energy, where the average is taken over a set of configurations $\{\mathbf{R}_i\}$ sampled from the probability distribution $P(\mathbf{R}) \propto |\Psi_T(\mathbf{R})|^2$.

## 3. The VMC Algorithm

A VMC simulation typically proceeds through four main steps, which are iterated until a converged solution is found.

1.  **Construct a Trial Wavefunction $\Psi_T(\mathbf{R}, \{\alpha\})$**
    This is the most critical part of the method, as the final accuracy depends entirely on the quality of this ansatz. The wavefunction must incorporate as much known physics as possible. For electronic systems, a common and highly effective choice is the **Slater-Jastrow wavefunction**:
    $$
    \Psi_T = D_{\uparrow} D_{\downarrow} \times e^{J}
    $$
    -   **Slater Determinants ($D_{\uparrow}, D_{\downarrow}$)**: These are determinants of single-particle orbitals (e.g., from a Hartree-Fock calculation). Their primary role is to enforce the Pauli exclusion principle, ensuring the wavefunction is antisymmetric under the exchange of identical fermions.
    -   **Jastrow Factor ($e^J$)**: This is an explicit, symmetric function of inter-particle distances (e.g., $J = \sum_{i<j} u(r_{ij})$). Its purpose is to model electron-electron correlations, which are missing from mean-field theories. It reduces the probability of two electrons getting close to each other, thereby lowering the potential energy.
    The parameters $\{\alpha\}$ to be optimized are contained within the orbitals and the Jastrow factor.

2.  **Sample Configurations via Monte Carlo**
    The goal is to generate a large number of particle configurations $\{\mathbf{R}_i\}$ that are distributed according to $P(\mathbf{R}) \propto |\Psi_T(\mathbf{R})|^2$. This is achieved using a Markov Chain Monte Carlo method, almost universally the **Metropolis-Hastings algorithm**. The algorithm generates a random walk in the configuration space such that the walkers eventually populate regions with a density proportional to $|\Psi_T|^2$.

3.  **Calculate the Variational Energy**
    Using the list of $M$ configurations generated in the previous step, the variational energy is estimated as the simple average of the local energy evaluated at each configuration:
    $$
    E_V(\{\alpha\}) \approx \frac{1}{M} \sum_{i=1}^{M} E_L(\mathbf{R}_i)
    $$
    Similarly, the expectation value of any other operator $\hat{O}$ can be computed as the average of its corresponding local value, $O_L(\mathbf{R}) = \frac{\hat{O}\Psi_T(\mathbf{R})}{\Psi_T(\mathbf{R})}$.

4.  **Optimize the Wavefunction Parameters**
    The final step is to minimize the calculated energy $E_V$ with respect to the parameters $\{\alpha\}$. This is a non-linear optimization problem. Various numerical methods can be used, such as stochastic gradient descent or the more robust and efficient "linear method." This step typically involves calculating the derivatives of the energy with respect to the parameters. The entire process (Steps 2-4) is repeated iteratively until the energy and its variance converge to a minimum.

## 4. Strengths and Limitations

### Strengths
-   **Computational Efficiency**: VMC scales polynomially with the number of particles (typically as $O(N^3)$ to $O(N^4)$), making it applicable to much larger systems than exact diagonalization methods, which scale exponentially.
-   **Explicit Correlations**: Unlike simpler methods like Hartree-Fock, VMC can explicitly and accurately model electron correlation through the Jastrow factor.
-   **Flexibility**: The method is highly flexible and can be applied to a wide variety of quantum systems in continuum space or on a lattice.

### Limitations
-   **Bias from the Trial Wavefunction**: This is the most significant weakness. The result is not the true ground-state energy but rather the best possible energy for the chosen functional form of $\Psi_T$. The method is inherently biased, and its accuracy is entirely dependent on the quality of the ansatz.
-   **Optimization Complexity**: For complex wavefunctions with many parameters, the optimization process can be challenging, with the risk of getting stuck in local minima in the parameter space.

## 5. Conclusion

Variational Monte Carlo is a cornerstone of modern computational physics. It provides an intuitive and powerful framework for approximating the ground state of quantum many-body systems by combining the rigor of the variational principle with the efficiency of Monte Carlo sampling. While its accuracy is fundamentally limited by the choice of the trial wavefunction, its favorable scaling and ability to explicitly treat correlations make it an invaluable tool. Furthermore, VMC is often the essential first step for more advanced and accurate techniques like [[Notes/2025/10/13/Diffusion Monte Carlo\|Diffusion Monte Carlo]], for which it provides the high-quality trial wavefunctions needed for importance sampling and the fixed-node approximation.

