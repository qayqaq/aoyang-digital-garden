---
{"dg-publish":true,"permalink":"/notes/2025/10/13/imaginary-time/","tags":["#Physics","#QuantumMechanics","#StatisticalMechanics","#ComputationalPhysics","#TheoreticalPhysics"]}
---

- Imaginary time, $\tau$, is a mathematical concept derived by performing a **Wick rotation** on real time, $t \rightarrow -i\tau$. It is not a time that can be physically experienced.
- This transformation converts the oscillatory quantum time evolution operator, $e^{-i\hat{H}t/\hbar}$, into a real, decaying exponential, $e^{-\hat{H}\tau/\hbar}$. This form is mathematically more stable and suitable for numerical calculations.
- Imaginary time provides a profound connection between quantum mechanics and statistical mechanics. The quantum evolution operator in imaginary time is formally identical to the statistical density matrix operator, $e^{-\beta \hat{H}}$, where the inverse temperature $\beta$ corresponds to the total imaginary time duration.
- In computational physics, evolving a quantum state in imaginary time acts as a filter that projects out the system's ground state, as higher-energy state components decay more rapidly. This is a core principle of projector Quantum Monte Carlo methods.

#Physics #QuantumMechanics #StatisticalMechanics #ComputationalPhysics #TheoreticalPhysics

[[Imaginary Time.canvas\|Imaginary Time.canvas]]
# Imaginary Time

## 1. Introduction

**Imaginary time** is a powerful and abstract mathematical concept used extensively in quantum mechanics, quantum field theory, and statistical mechanics. It is not a physical time that can be measured or experienced, but rather a formal tool derived from a mathematical procedure known as a **[[Notes/2025/10/13/Wick Rotation\|Wick Rotation]]**. By replacing the real-valued time variable $t$ with a purely imaginary one, $\tau = -it$, physicists can transform notoriously difficult problems involving quantum dynamics into more tractable problems in statistical mechanics. This transformation is fundamental to the path integral formulation of quantum mechanics and underpins many essential numerical techniques, such as [[Notes/2025/10/13/Determinant Quantum Monte Carlo\|Determinant Quantum Monte Carlo]].

## 2. The Wick Rotation: From Oscillations to Decay

The dynamics of a quantum system are governed by the Schrödinger equation, and the evolution of a quantum state $|\psi\rangle$ over time is described by the time evolution operator, $U(t) = e^{-i\hat{H}t/\hbar}$, where $\hat{H}$ is the Hamiltonian operator of the system. The presence of the imaginary unit $i$ in the exponent makes this a complex exponential, leading to oscillatory, wave-like behavior. While this is the physical essence of quantum mechanics, these oscillations make many calculations, particularly integrals over time, mathematically challenging and numerically unstable.

The **Wick rotation** is the formal substitution of real time $t$ with an imaginary counterpart. We define imaginary time $\tau$ via the relation:
$$
t = -i\tau
$$
Substituting this into the time evolution operator yields a dramatic change:
$$
U(t) = e^{-i\hat{H}t/\hbar} \quad \xrightarrow{\text{Wick Rotation}} \quad e^{-i\hat{H}(-i\tau)/\hbar} = e^{i^2\hat{H}\tau/\hbar} = e^{-\hat{H}\tau/\hbar}
$$
The resulting operator, $e^{-\hat{H}\tau/\hbar}$, is no longer a complex, oscillating function but a **real, decaying exponential**. This mathematical property is far more convenient for analytical and numerical work, as it suppresses fluctuations rather than propagating them.

## 3. The Bridge to Statistical Mechanics

One of the most profound consequences of introducing imaginary time is the formal connection it reveals between quantum mechanics and statistical mechanics. In statistical mechanics, the properties of a system in thermal equilibrium at a temperature $T$ are described by the **canonical [[Notes/2025/10/13/Partition Function\|partition function]]**:
$$
Z = \text{Tr}(e^{-\beta \hat{H}})
$$
where $\text{Tr}$ denotes the trace, and $\beta = 1/(k_B T)$ is the inverse temperature ($k_B$ is the Boltzmann constant). The operator $\rho = e^{-\beta \hat{H}}$ is the (unnormalized) density matrix, which contains all statistical information about the system.

By comparing the two expressions, we see a direct mathematical equivalence:
> The quantum time evolution operator in imaginary time, $e^{-\hat{H}\tau/\hbar}$, is formally identical to the statistical mechanical density matrix operator, $e^{-\beta \hat{H}}$, provided we make the identification:
> $$
\tau = \hbar\beta = \frac{\hbar}{k_B T}
$$

***This remarkable correspondence implies that calculating the properties of a quantum system evolving for a finite duration in imaginary time is equivalent to calculating the thermal properties of a corresponding classical system at a specific temperature. The duration of imaginary time evolution is directly proportional to the inverse temperature.***

## 4. Application in Path Integrals and Ground State Projection

### Path Integral Formulation

In Richard Feynman's path integral formulation, the probability amplitude for a particle to travel between two points is calculated by summing the contributions of all possible paths. Each path is weighted by a phase factor $e^{iS/\hbar}$, where $S$ is the classical action. The integral over all paths involves summing these rapidly oscillating phases, a task that is numerically intractable (this is often called the "sign problem").

Performing a Wick rotation transforms the action $S$ into the **Euclidean action** $S_E$, and the weighting factor becomes $e^{-S_E/\hbar}$. This is a real, positive weight that can be interpreted as a probability distribution, similar to the Boltzmann factor $e^{-E/k_B T}$ in statistical mechanics. This allows the path integral to be evaluated using powerful stochastic methods like Monte Carlo simulations, where paths are sampled according to their statistical weight.

### Ground State Projection

Imaginary time evolution provides a robust method for determining the ground state of a quantum system. Any arbitrary quantum state $|\psi\rangle$ can be expressed as a linear combination of the energy eigenstates $|E_n\rangle$:
$$
|\psi\rangle = \sum_{n=0}^{\infty} c_n |E_n\rangle
$$
where $|E_0\rangle$ is the ground state. Applying the imaginary time evolution operator to this state gives:
$$
e^{-\hat{H}\tau/\hbar} |\psi\rangle = \sum_{n=0}^{\infty} c_n e^{-\hat{H}\tau/\hbar} |E_n\rangle = \sum_{n=0}^{\infty} c_n e^{-E_n\tau/\hbar} |E_n\rangle
$$
As the imaginary time $\tau$ increases, the exponential terms $e^{-E_n\tau/\hbar}$ decay. Since the ground state energy $E_0$ is the lowest energy by definition ($E_n > E_0$ for $n>0$), its corresponding term $e^{-E_0\tau/\hbar}$ decays the slowest. In the limit of large imaginary time, all higher-energy components are exponentially suppressed relative to the ground state component.
$$
\lim_{\tau \to \infty} e^{-\hat{H}\tau/\hbar} |\psi\rangle = c_0 e^{-E_0\tau/\hbar} |E_0\rangle
$$
Thus, evolving any initial state (that has a non-zero overlap with the ground state) for a sufficiently long imaginary time will "project out" the ground state of the system. This is the foundational principle of **[[Notes/2025/10/13/Projector Quantum Monte Carlo\|Projector Quantum Monte Carlo]]** methods.

## 5. Conclusion

Imaginary time is a cornerstone of modern theoretical physics. While it lacks a direct physical interpretation, it serves as an indispensable mathematical bridge connecting the quantum dynamics of a system to its statistical thermal properties. By transforming oscillating complex exponentials into real decaying ones, it tames the mathematical complexities inherent in quantum mechanics, making path integrals computable and providing a powerful numerical scheme for finding the ground states of complex many-body systems.
