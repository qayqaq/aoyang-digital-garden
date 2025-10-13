---
{"dg-publish":true,"permalink":"/notes/2025/10/13/hubbard-stratonovich-transformation/","tags":["#Physics","#QuantumMechanics","#CondensedMatter","#ComputationalPhysics","#ManyBodyTheory"]}
---

- The Hubbard-Stratonovich Transformation is a mathematical technique that converts a problem of interacting particles into an equivalent problem of non-interacting particles moving in a fluctuating "auxiliary" field.
- It linearizes interaction terms in the exponent of a partition function by replacing an exponential of a squared operator, like $e^{\hat{A}^2}$, with an integral over exponentials of a linear operator, such as $\int d\phi \, e^{-\phi^2 + \phi\hat{A}}$.
- Its primary application is in many-body physics, enabling numerical simulations like [[Notes/2025/10/13/Determinant Quantum Monte Carlo\|Determinant Quantum Monte Carlo]] for systems with two-body interactions, such as the Hubbard model.
- The transformation exists in both continuous (integral over a Gaussian field) and discrete (sum over an Ising-like field) forms, chosen based on the specific interaction term being decoupled.

#Physics #QuantumMechanics #CondensedMatter #ComputationalPhysics #ManyBodyTheory

[[Hubbard-Stratonovich Transformation.canvas\|Hubbard-Stratonovich Transformation.canvas]]

# Hubbard-Stratonovich Transformation

## 1. Introduction

The **Hubbard-Stratonovich (HS) Transformation**, also known as the Hubbard-Stratonovich trick, is a fundamental mathematical identity used extensively in quantum field theory, condensed matter physics, and statistical mechanics. Its primary function is to simplify calculations involving many-body systems by transforming a problem with two-body (or higher-order) interactions into an equivalent problem of non-interacting particles coupled to a fluctuating **auxiliary field**. This transformation is the cornerstone of many powerful numerical methods, most notably [[Notes/2025/10/13/Determinant Quantum Monte Carlo\|Determinant Quantum Monte Carlo]], as it makes intractable interacting problems amenable to computation.

In essence, the transformation linearizes an operator that appears quadratically in the exponent of a partition function or path integral, at the cost of introducing an integral over a new, fictitious field.

## 2. The Core Mathematical Principle

The HS transformation is rooted in a simple Gaussian integral identity. For a real number $a > 0$, we know that:
$$
\int_{-\infty}^{\infty} e^{-ax^2} dx = \sqrt{\frac{\pi}{a}}
$$
By completing the square, this identity can be generalized to include a linear term:
$$
\int_{-\infty}^{\infty} e^{-ax^2 + bx} dx = \sqrt{\frac{\pi}{a}} e^{b^2/4a}
$$
Rearranging this equation gives us the core of the transformation. By setting $a=1/2$ and $b=A$, we can express the exponential of a squared term as an integral:
$$
e^{A^2/2} = \frac{1}{\sqrt{2\pi}} \int_{-\infty}^{\infty} e^{-x^2/2 + xA} dx
$$
Here, the term $e^{A^2/2}$, which is quadratic in $A$, has been replaced by an integral over a new variable $x$ (the auxiliary field) where $A$ now appears linearly in the exponent ($e^{xA}$).

## 3. Generalization to Quantum Operators

The power of this technique becomes apparent when we generalize it from scalars to quantum operators. If $\hat{A}$ is a Hermitian operator, the identity holds in an analogous form:
$$
e^{\frac{1}{2}\hat{A}^2} = \frac{1}{\sqrt{2\pi}} \int_{-\infty}^{\infty} d\phi \, e^{-\frac{1}{2}\phi^2 + \phi\hat{A}}
$$
This is the central result. An exponential containing a **two-body interaction** (represented by the quadratic operator $\hat{A}^2$) is transformed into an integral over all possible configurations of an auxiliary field $\phi$. For each fixed value of $\phi$, the operator in the exponent, $\phi\hat{A}$, is a **one-body operator**. This effectively decouples the interacting particles, which now move independently within the external potential provided by the field $\phi$.

## 4. Application: The Hubbard Model

A canonical application of the HS transformation is in solving the Hubbard model, which describes interacting electrons on a lattice. The interaction term in the Hubbard Hamiltonian is $\hat{V} = U \sum_i \hat{n}_{i\uparrow} \hat{n}_{i\downarrow}$, where $\hat{n}_{i\sigma} = c_{i\sigma}^\dagger c_{i\sigma}$ is the number operator for an electron with spin $\sigma$ at site $i$. This term represents a four-fermion, or two-body, interaction.

In numerical methods like DQMC, the partition function $Z = \text{Tr}(e^{-\beta \hat{H}})$ is evaluated by splitting the inverse temperature $\beta$ into small imaginary time steps $\Delta\tau$. The interaction term for a single time step is $e^{-\Delta\tau U \hat{n}_{i\uparrow} \hat{n}_{i\downarrow}}$. This term can be decoupled using a **discrete** or **Ising** version of the HS transformation, which is often more convenient for computation.

A common form of the discrete HS transformation for the Hubbard interaction is:
$$
e^{-\Delta\tau U \hat{n}_{i\uparrow} \hat{n}_{i\downarrow}} = e^{-\frac{\Delta\tau U}{2}(\hat{n}_{i\uparrow} + \hat{n}_{i\downarrow})} \frac{1}{2} \sum_{s_{i,l}=\pm 1} e^{\lambda s_{i,l} (\hat{n}_{i\uparrow} - \hat{n}_{i\downarrow})}
$$
where:
- $s_{i,l}$ is a discrete (Ising-like) auxiliary field variable at lattice site $i$ and imaginary time slice $l$. It can take values $+1$ or $-1$.
- $\lambda$ is a constant defined by the relation $\cosh(\lambda) = e^{\Delta\tau U/2}$.

This transformation replaces the difficult four-fermion term with a sum over the auxiliary field configurations $\{s_{i,l}\}$. For any given configuration, the electrons are non-interacting and are only coupled to a space- and time-dependent magnetic field proportional to $s_{i,l}$.

## 5. Physical Interpretation and Computational Strategy

The HS transformation provides a powerful physical reinterpretation of interactions. Instead of particles interacting directly with each other, we can view them as non-interacting particles that communicate via a mediating field (the auxiliary field). The quantum mechanical path integral or partition function is then calculated by summing over all possible fluctuations and configurations of this mediating field.

This leads to a clear computational strategy for methods like Quantum Monte Carlo:
1.  **Represent the Interaction:** Express the partition function as a path integral over fermion fields and a sum/integral over auxiliary field configurations.
2.  **Integrate Out Fermions:** For a *fixed* configuration of the auxiliary field $\{s_{i,l}\}$, the problem is quadratic in the fermion operators (non-interacting), and the fermions can be integrated out exactly, typically resulting in a determinant.
3.  **Sample the Auxiliary Field:** The remaining task is to perform a high-dimensional sum or integral over all configurations of the auxiliary field. Since the number of configurations is exponentially large, this is done stochastically using Monte Carlo sampling methods.

## 6. Conclusion

The Hubbard-Stratonovich transformation is a versatile and indispensable tool in theoretical and computational physics. By converting quadratic operator terms into linear ones at the expense of introducing an auxiliary field, it transforms seemingly intractable many-body interaction problems into manageable problems of non-interacting particles in a fluctuating potential. This conceptual and mathematical simplification paves the way for powerful numerical algorithms that have become essential for studying strongly correlated quantum systems.
