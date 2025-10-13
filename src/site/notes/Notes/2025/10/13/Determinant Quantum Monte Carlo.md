---
{"dg-publish":true,"permalink":"/notes/2025/10/13/determinant-quantum-monte-carlo/","tags":["#computational_physics","#condensed_matter","#quantum_mechanics","#monte_carlo","#fermions"]}
---

#computational_physics #condensed_matter #quantum_mechanics #monte_carlo #fermions
[[Determinant Quantum Monte Carlo.canvas\|Determinant Quantum Monte Carlo.canvas]]

*   **What it is**: Determinant Quantum Monte Carlo (DQMC) is a powerful, numerically exact simulation method for quantum systems of interacting fermions (like electrons on a [[Notes/2025/10/13/Crystal Lattice\|Crystal Lattice]]). It is a key tool in [[Notes/2025/10/13/Condensed Matter Physics\|Condensed Matter Physics]] for studying emergent phenomena like magnetism and superconductivity.
*   **Core Idea**: It transforms an intractable [[Notes/2025/10/13/Quantum Many-Body System\|Quantum Many-Body System]] into a classical statistical mechanics problem. This is achieved by discretizing imaginary time (Trotter-Suzuki decomposition) and using a Hubbard-Stratonovich transformation to decouple fermion interactions.
*   **The "Determinant"**: After the transformation, the fermionic degrees of freedom are integrated out analytically. Their entire contribution to the statistical weight of a given classical configuration is encapsulated in the determinant of a matrix, which is then sampled using Monte Carlo methods.
*   **Main Challenge**: The method's primary limitation is the **fermion sign problem**. In many systems, the determinant can be negative, preventing it from being used as a probability. This leads to numerical instability, especially at low temperatures, restricting the algorithm's applicability.

# Determinant Quantum Monte Carlo

## Introduction

**Determinant Quantum Monte Carlo (DQMC)** is a powerful and widely used numerical method for simulating quantum systems of interacting fermions, such as electrons in a crystal lattice. It falls under the broader category of [[Notes/2025/10/13/Quantum Monte Carlo\|Quantum Monte Carlo]] methods, specifically as a type of Path-Integral Monte Carlo tailored for lattice fermions. Its primary application is in [[Notes/2025/10/13/Condensed Matter Physics\|Condensed Matter Physics]], where it provides a way to study the collective behavior of electrons that gives rise to complex phenomena like magnetism, metal-insulator transitions, and superconductivity.

The core idea of DQMC is to transform a quantum many-body problem, which is defined in an exponentially large Hilbert space, into a problem of classical statistical mechanics that can be solved using Monte Carlo techniques. The name "Determinant" arises because the contribution of the fermions to the statistical weight of each classical configuration is encapsulated in the determinant of a matrix. This method is considered numerically exact, meaning its results are subject only to controllable statistical and systematic errors.

## Theoretical Foundation

The derivation of the DQMC algorithm involves several key conceptual and mathematical steps that map the quantum partition function onto a form suitable for classical simulation.

### 1. The Many-Fermion Problem and the Partition Function

We typically start with a model Hamiltonian, $\hat{H}$, that describes the system. A canonical example is the **Hubbard model**, which captures the competition between electron hopping (kinetic energy) and on-site Coulomb repulsion (potential energy):
$$
\hat{H} = \hat{K} + \hat{V} = -t \sum_{\langle i,j \rangle, \sigma} (c_{i\sigma}^\dagger c_{j\sigma} + c_{j\sigma}^\dagger c_{i\sigma}) + U \sum_i \hat{n}_{i\uparrow} \hat{n}_{i\downarrow}
$$
Here, $c_{i\sigma}^\dagger$ ($c_{i\sigma}$) creates (annihilates) an electron of spin $\sigma$ at site $i$, $t$ is the hopping amplitude, $U$ is the on-site repulsion strength, and $\hat{n}_{i\sigma} = c_{i\sigma}^\dagger c_{i\sigma}$ is the number operator.

The goal is to compute thermodynamic properties, which can be derived from the **[[Notes/2025/10/13/Partition Function\|Partition Function]]**:
$$
Z = \text{Tr}(e^{-\beta \hat{H}})
$$
where $\beta = 1/(k_B T)$ is the inverse temperature and $\text{Tr}$ denotes the trace over all quantum states. The direct evaluation of this trace is computationally intractable for all but the smallest systems due to the exponential size of the Hilbert space.

### 2. Path Integral Formulation: Trotter-Suzuki Decomposition

To make progress, we discretize the "imaginary time" $\beta$ into $L$ small time slices of duration $\Delta\tau = \beta/L$. The exponential operator is then broken apart using the **[[Notes/2025/10/13/Trotter-Suzuki Decomposition\|Trotter-Suzuki Decomposition]]**:
$$
e^{-\beta \hat{H}} = e^{-\beta (\hat{K} + \hat{V})} \approx (e^{-\Delta\tau \hat{K}} e^{-\Delta\tau \hat{V}})^L
$$
This approximation, which relies on the fact that $\hat{K}$ and $\hat{V}$ do not commute, becomes exact in the limit $\Delta\tau \to 0$. The partition function now looks like a product of many simple evolution operators, resembling a path integral.
$$
Z \approx \text{Tr}[e^{-\Delta\tau \hat{K}} e^{-\Delta\tau \hat{V}} \cdots e^{-\Delta\tau \hat{K}} e^{-\Delta\tau \hat{V}}]
$$

### 3. Hubbard-Stratonovich Transformation

The interaction term $\hat{V}$ contains a four-fermion operator ($\hat{n}_{i\uparrow} \hat{n}_{i\downarrow} = c_{i\uparrow}^\dagger c_{i\uparrow} c_{i\downarrow}^\dagger c_{i\downarrow}$), which makes the problem difficult. The crucial step in DQMC is to decouple this term using the **[[Notes/2025/10/13/Hubbard-Stratonovich Transformation\|Hubbard-Stratonovich Transformation]]**. This mathematical identity allows us to express the two-body interaction exponential as an average over a one-body term coupled to a fluctuating **auxiliary field**.

For the Hubbard interaction term, a discrete HS transformation can be used:
$$
e^{-\Delta\tau U \hat{n}_{i\uparrow} \hat{n}_{i\downarrow}} = e^{-\frac{\Delta\tau U}{2}(\hat{n}_{i\uparrow} + \hat{n}_{i\downarrow})} \frac{1}{2} \sum_{s_{i,l}=\pm 1} e^{\lambda s_{i,l} (\hat{n}_{i\uparrow} - \hat{n}_{i\downarrow})}
$$
where $\cosh(\lambda) = e^{\Delta\tau U/2}$ and $s_{i,l}$ is an Ising-like auxiliary field variable at each lattice site $i$ and imaginary time slice $l$.

By applying this transformation at every site and every time slice, we replace the interacting fermion problem with a system of non-interacting fermions moving in a space- and time-dependent potential determined by the configuration of the auxiliary field $\{s_{i,l}\}$.

**Derivation: Hubbard-Stratonovich Decomposition for the DQMC Interaction Term**
#### 4.1 Starting Point

Our goal is to decompose the interaction term for a single imaginary time slice `l`:
$$
e^{-\Delta\tau \hat{V}} = e^{-\Delta\tau U \sum_{i=1}^N \hat{n}_{i\uparrow} \hat{n}_{i\downarrow}}
$$
where `N` is the number of spatial lattice sites.

#### 4.2 Step-by-Step Derivation

##### a. Split the Operator by Site

Since operators on different sites commute (i.e., $[\hat{n}_{i\sigma}, \hat{n}_{j\sigma'}] = 0$ for $i \neq j$), the exponential of the sum can be written as a product of exponentials:
$$
e^{-\Delta\tau U \sum_{i=1}^N \hat{n}_{i\uparrow} \hat{n}_{i\downarrow}} = \prod_{i=1}^N e^{-\Delta\tau U \hat{n}_{i\uparrow} \hat{n}_{i\downarrow}}
$$

##### b. Apply the Discrete Hubbard-Stratonovich (HS) Transformation

We apply the discrete (Ising) HS identity to each term in the product. The identity states:
$$
e^{\alpha \hat{A}^2} = \frac{1}{2} \sum_{s=\pm 1} e^{\gamma s \hat{A}} \quad \text{where} \quad e^{\alpha} = \cosh(\gamma)
$$
In our case, we have previously shown that for the Hubbard interaction, this can be written as:
$$
e^{-\Delta\tau U \hat{n}_{i\uparrow} \hat{n}_{i\downarrow}} = \frac{1}{2} \sum_{s_{i,l}=\pm 1} e^{-\frac{\Delta\tau U}{2}(\hat{n}_{i\uparrow} + \hat{n}_{i\downarrow})} e^{\lambda s_{i,l} (\hat{n}_{i\uparrow} - \hat{n}_{i\downarrow})}
$$
where the auxiliary field $s_{i,l}$ is an Ising variable for site `i` and time slice `l`, and the constant $\lambda$ is defined by $\cosh(\lambda) = e^{\Delta\tau U/2}$.

##### c. Recombine the Full Expression

Substituting the single-site decomposition back into the product:
$$
e^{-\Delta\tau \hat{V}} = \prod_{i=1}^N \left[ \frac{1}{2} \sum_{s_{i,l}=\pm 1} e^{-\frac{\Delta\tau U}{2}(\hat{n}_{i\uparrow} + \hat{n}_{i\downarrow})} e^{\lambda s_{i,l} (\hat{n}_{i\uparrow} - \hat{n}_{i\downarrow})} \right]
$$
We can rearrange this expression by moving all sums over the auxiliary fields to the front. A product of sums is a sum over all combinations of the product terms. Let $\mathbf{s}_l = (s_{1,l}, s_{2,l}, \dots, s_{N,l})$ denote a complete configuration of the auxiliary fields on the spatial lattice at time slice `l`.
$$
e^{-\Delta\tau \hat{V}} = \left(\frac{1}{2}\right)^N \sum_{\mathbf{s}_l} \prod_{i=1}^N \left[ e^{-\frac{\Delta\tau U}{2}(\hat{n}_{i\uparrow} + \hat{n}_{i\downarrow})} e^{\lambda s_{i,l} (\hat{n}_{i\uparrow} - \hat{n}_{i\downarrow})} \right]
$$
Now, we can combine the product of exponentials into a single exponential of a sum:
$$
e^{-\Delta\tau \hat{V}} = \left(\frac{1}{2}\right)^N \sum_{\mathbf{s}_l} \exp\left( \sum_{i=1}^N \left[ -\frac{\Delta\tau U}{2}(\hat{n}_{i\uparrow} + \hat{n}_{i\downarrow}) + \lambda s_{i,l} (\hat{n}_{i\uparrow} - \hat{n}_{i\downarrow}) \right] \right)
$$

##### d. Regroup Terms by Spin

Finally, we regroup the terms in the exponent based on the spin of the electron they act upon:
$$
\sum_{i=1}^N \left[ \left(-\frac{\Delta\tau U}{2} + \lambda s_{i,l}\right) \hat{n}_{i\uparrow} + \left(-\frac{\Delta\tau U}{2} - \lambda s_{i,l}\right) \hat{n}_{i\downarrow} \right]
$$

#### 4.3 Final Decomposed Form

The interaction operator is transformed into a sum over all possible configurations of the classical auxiliary field. Each term in the sum corresponds to a one-body operator describing non-interacting fermions.

The final form is:
$$
e^{-\Delta\tau \hat{V}} = C \sum_{\mathbf{s}_l} e^{\hat{V}_l(\mathbf{s}_l)}
$$
where:
* **`C`** is a constant prefactor, $C = \left(\frac{1}{2}\right)^N$.
* **$\sum_{\mathbf{s}_l}$** is the sum over all $2^N$ possible configurations of the Ising auxiliary field on the spatial lattice at time slice `l`.
* **$\hat{V}_l(\mathbf{s}_l)$** is the effective **one-body operator** for a given field configuration $\mathbf{s}_l$:
    $$
    \hat{V}_l(\mathbf{s}_l) = \sum_{i=1}^N \sum_{\sigma \in \{\uparrow, \downarrow\}} V_{i,\sigma}(s_{i,l}) \hat{n}_{i\sigma}
    $$
* **$V_{i,\sigma}(s_{i,l})$** is the effective potential experienced by an electron with spin $\sigma$ at site `i`:
    $$
    V_{i,\uparrow}(s_{i,l}) = -\frac{\Delta\tau U}{2} + \lambda s_{i,l}
    $$
    $$
    V_{i,\downarrow}(s_{i,l}) = -\frac{\Delta\tau U}{2} - \lambda s_{i,l}
    $$
* The constant **$\lambda$** is defined by the relation $\cosh(\lambda) = e^{\Delta\tau U/2}$.

This final expression replaces the difficult many-body interaction with a statistical sum over tractable one-body problems, which is the foundational step for the DQMC simulation.

### 4. Integrating Out the Fermions

For any *fixed* configuration of the auxiliary field $\{s\}$, the total Hamiltonian becomes quadratic in the fermion operators. For such non-interacting systems, a powerful theorem allows us to perform the trace over the fermionic degrees of freedom analytically. The result of this integration is the determinant of a matrix $M[\{s\}]$ whose dimensions are $N \times N$ (where $N$ is the number of spatial sites).

Since the Hubbard Hamiltonian conserves spin, this can be done independently for spin-up and spin-down electrons. The partition function is transformed into a sum over all possible configurations of the classical auxiliary field:
$$
Z = \sum_{\{s\}} \det(M_{\uparrow}[\{s\}]) \det(M_{\downarrow}[\{s\}])
$$
The matrix $M_{\sigma}$ is a function of the kinetic hopping parameters and the specific configuration of the auxiliary field $\{s\}$. It can be written as a product of matrices: $M_{\sigma} = I + B_{L,\sigma} B_{L-1,\sigma} \cdots B_{1,\sigma}$, where each $B_{l,\sigma}$ represents the evolution over one time slice $\Delta\tau$ under the influence of the auxiliary field.

**DQMC Derivation: Integrating Out the Fermionic Degrees of Freedom**

#### 4.1 The Starting Point: The Partition Function for a Fixed Field

After the Trotter-Suzuki and Hubbard-Stratonovich transformations, the partition function $Z$ is expressed as a sum over all possible configurations of the auxiliary field $\{s\}$. Our task is to solve the term inside the sum for a *single, fixed configuration* of $\{s\}$. This term, which we call $Z(\{s\})$, involves a trace over the many-body fermionic Fock space ($\text{Tr}_c$):

$$
Z(\{s\}) = \text{Tr}_c \left[ \left(e^{-\Delta\tau \hat{K}} e^{\hat{V}_L(\mathbf{s}_L)}\right) \left(e^{-\Delta\tau \hat{K}} e^{\hat{V}_{L-1}(\mathbf{s}_{L-1})}\right) \cdots \left(e^{-\Delta\tau \hat{K}} e^{\hat{V}_1(\mathbf{s}_1)}\right) \right]
$$

The direct computation of this trace is impossible, as the dimension of the Fock space is exponential in the system size $N$.

#### 4.2 The Core Theorem: The Trace Formula for Free Fermions

The solution relies on a fundamental theorem for non-interacting (quadratic) fermion systems.

**Theorem:** For any many-body operator $\hat{\mathcal{U}}$ that is quadratic in the fermion operators (i.e., constructed from operators of the form $c^\dagger c$), the trace over the many-body Fock space is given by the determinant of a matrix in the single-particle Hilbert space.
$$
\text{Tr}_c(\hat{\mathcal{U}}) = \det(I + U)
$$
Here, $U$ is the $N \times N$ single-particle matrix that uniquely corresponds to the many-body operator $\hat{\mathcal{U}}$.

#### 4.3 Step-by-Step Derivation for the DQMC Case

We will now apply this theorem to our expression for $Z(\{s\})$.

##### 4.3.1 Separation by Spin

The Hubbard model conserves the number of spin-up and spin-down electrons independently. This means the Hamiltonian does not contain any terms that flip an electron's spin. Consequently, the total Fock space is a tensor product of the spin-up and spin-down Fock spaces ($\mathcal{F} = \mathcal{F}_\uparrow \otimes \mathcal{F}_\downarrow$), and the trace can be factorized:

$$
Z(\{s\}) = \text{Tr}_{c_{\uparrow}}(\dots_{\uparrow}) \cdot \text{Tr}_{c_{\downarrow}}(\dots_{\downarrow})
$$

We can perform the derivation for the spin-up part, $Z_{\uparrow}(\{s\})$, and the result for the spin-down part will be analogous.

##### 4.3.2: From Many-Body Operators to Single-Particle Matrices

The key is to establish the correspondence between the operators in the trace and their matrix representations in the single-particle space.

Let's define the many-body operator for a single time slice `l` and a single spin species $\sigma$:
$$
\hat{U}_{l,\sigma} \equiv e^{-\Delta\tau \hat{K}_{\sigma}} e^{\hat{V}_{l,\sigma}(\mathbf{s}_l)}
$$
Since both $\hat{K}_{\sigma}$ and $\hat{V}_{l,\sigma}(\mathbf{s}_l)$ are quadratic operators, their exponentials are also quadratic operators. Each corresponds to an $N \times N$ matrix:
-   $e^{-\Delta\tau \hat{K}_{\sigma}}$ corresponds to the matrix $K_\sigma = e^{-\Delta\tau k_\sigma}$.
-   $e^{\hat{V}_{l,\sigma}(\mathbf{s}_l)}$ corresponds to the matrix $V_{l,\sigma} = e^{v_{l,\sigma}(\mathbf{s}_l)}$.

A fundamental property is that the composition of many-body quadratic operators corresponds to the matrix product of their single-particle representations. Therefore, the single-particle matrix corresponding to $\hat{U}_{l,\sigma}$ is the product of the individual matrices. This is the standard **B-matrix** in DQMC:
$$
B_{l,\sigma}(\mathbf{s}_l) \equiv K_\sigma V_{l,\sigma} = e^{-\Delta\tau k_\sigma} e^{v_{l,\sigma}(\mathbf{s}_l)}
$$

##### 4.3.3: Applying the General Trace Formula

Now we can rewrite the expression for the spin-up partition function:
$$
Z_{\uparrow}(\{s\}) = \text{Tr}_{c_{\uparrow}} \left[ \hat{U}_{L,\uparrow} \hat{U}_{L-1,\uparrow} \cdots \hat{U}_{1,\uparrow} \right]
$$
Let's define the total many-body evolution operator for the spin-up sector as:
$$
\hat{\mathcal{U}}_{\text{total},\uparrow} = \hat{U}_{L,\uparrow} \hat{U}_{L-1,\uparrow} \cdots \hat{U}_{1,\uparrow}
$$
Based on the correspondence established in Step 3.2, the single-particle matrix corresponding to this total evolution operator is simply the product of all the B-matrices:
$$
U_{\text{total},\uparrow} = B_{L,\uparrow} B_{L-1,\uparrow} \cdots B_{1,\uparrow}
$$
Now we can apply the general theorem from Section 2. We set $\hat{\mathcal{U}} = \hat{\mathcal{U}}_{\text{total},\uparrow}$ and $U = U_{\text{total},\uparrow}$:
$$
\text{Tr}_{c_{\uparrow}}(\hat{\mathcal{U}}_{\text{total},\uparrow}) = \det(I + U_{\text{total},\uparrow})
$$
Substituting our DQMC expressions back in, we arrive at the result for the spin-up trace:
$$
Z_{\uparrow}(\{s\}) = \det(I + B_{L,\uparrow}(\mathbf{s}_L) B_{L-1,\uparrow}(\mathbf{s}_{L-1}) \cdots B_{1,\uparrow}(\mathbf{s}_1))
$$

#### 4.4 The Final Result and its Significance

We perform the same procedure for the spin-down electrons. The final result for the fermionic trace for a fixed configuration $\{s\}$ is the product of the two determinants.

Let's define the **DQMC matrix** $M_\sigma(\{s\})$ as:
$$
M_\sigma(\{s\}) \equiv I + \prod_{l=L}^{1} B_{l,\sigma}(\mathbf{s}_l)
$$
Then, the trace is:
$$
Z(\{s\}) = \det(M_\uparrow[\{s\}]) \cdot \det(M_\downarrow[\{s\}])
$$
Finally, the full partition function of the original interacting system is given by summing this result over all possible classical auxiliary field configurations:
$$
Z = \sum_{\{s\}} \det(M_\uparrow[\{s\}]) \det(M_\downarrow[\{s\}])
$$

**Significance:** This procedure achieves a monumental simplification. It replaces an intractable trace over a many-body Fock space, with a dimension that scales as $4^N$, with the computation of determinants of $N \times N$ matrices. This converts an exponentially hard quantum problem into a problem of statistical sampling of determinants, which is computationally feasible.

## The Monte Carlo Method

The problem is now in the form of a classical statistical mechanics model. The configurations are defined by the set of all values $\{s_{i,l}\}$, and the statistical weight for each configuration is:
$$
W(\{s\}) = \det(M_{\uparrow}[\{s\}]) \det(M_{\downarrow}[\{s\}])
$$

### Importance Sampling

The number of auxiliary field configurations is astronomical (e.g., $2^{N \times L}$), so an exhaustive summation is impossible. Instead, we use **importance sampling** algorithms, such as the Metropolis-Hastings algorithm, to generate a sequence of configurations. The algorithm is designed to visit a configuration $\{s\}$ with a probability proportional to its weight $|W(\{s\})|$. Physical observables are then calculated as weighted averages over the sampled configurations.

### The Fermion Sign Problem

A major challenge in DQMC is the **fermion sign problem**. For many interesting physical systems (e.g., the Hubbard model away from half-filling, or with frustrating interactions), the weight $W(\{s\})$ can be negative. This prevents us from interpreting it as a true probability.

The standard workaround is to sample configurations with probability proportional to the absolute value of the weight, $|W(\{s\})|$, and include the sign of the weight in the measurement of an observable $\hat{O}$:
$$
\langle \hat{O} \rangle = \frac{\sum_{\{s\}} O(\{s\}) W(\{s\})}{\sum_{\{s\}} W(\{s\})} = \frac{\langle O \cdot \text{sign}(W) \rangle_{|W|}}{\langle \text{sign}(W) \rangle_{|W|}}
$$
The simulation becomes numerically unstable when the average sign $\langle \text{sign}(W) \rangle$ approaches zero, which typically occurs at low temperatures or for strong interactions. In this regime, the statistical error explodes, rendering the results unreliable. The absence of a sign problem in certain cases (like the repulsive Hubbard model on a bipartite lattice at half-filling) is a key reason for the success of DQMC in those specific areas.

## Algorithm Outline

A typical DQMC simulation proceeds as follows:
1. **Initialization**: Start with a random configuration of the auxiliary field $\{s_{i,l}\}$.
2. **Thermalization**: Perform a number of Monte Carlo sweeps to allow the system to reach equilibrium. In each sweep:
    * Iterate through all sites $(i,l)$ of the space-time lattice.
    * Propose a local update (e.g., flip the spin $s_{i,l} \to -s_{i,l}$).
    * Calculate the ratio of weights $R = W_{\text{new}} / W_{\text{old}}$. This can be done efficiently in $O(N^2)$ operations without recomputing the full $O(N^3)$ determinant.
    * Accept the flip with probability $P_{\text{acc}} = \min(1, |R|)$.
3. **Measurement**: After thermalization, continue performing sweeps. Periodically measure physical observables (e.g., energy, correlation functions) on the current configuration.
4. **Averaging**: Average the measurements over many independent configurations to obtain final estimates with statistical error bars.

## Applications

DQMC is a workhorse algorithm for studying strongly correlated electron systems. Its applications include:
- **The Hubbard Model**: Investigating the Mott metal-insulator transition, antiferromagnetism, and d-wave pairing tendencies.
- **High-Temperature Superconductivity**: Exploring models believed to capture the essential physics of cuprate and iron-based superconductors.
- **Quantum Phase Transitions**: Mapping out the phase diagrams of various lattice models as a function of temperature, interaction strength, or doping.
- **Ultracold Atoms**: Simulating fermionic atoms in optical lattices, which serve as highly controllable "quantum simulators" of condensed matter models.

## Conclusion

Determinant Quantum Monte Carlo provides a powerful and formally exact framework for solving quantum many-fermion problems. By mapping the quantum system onto a classical statistical problem via the Hubbard-Stratonovich transformation, it allows for the direct numerical simulation of complex collective phenomena. While its applicability is severely limited by the fermion sign problem in many cases, its success in sign-problem-free regimes has yielded profound insights into the nature of strongly correlated matter. The ongoing effort to mitigate or solve the sign problem remains one of the most significant challenges in computational physics.

