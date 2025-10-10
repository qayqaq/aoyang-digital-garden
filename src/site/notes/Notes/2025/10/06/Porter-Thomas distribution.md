---
{"dg-publish":true,"permalink":"/notes/2025/10/06/porter-thomas-distribution/"}
---

#quantum-mechanics #statistical-physics #quantum-computing #random-matrix-theory
[[Porter-Thomas distribution.canvas\|Porter-Thomas distribution.canvas]]

# Porter-Thomas Distribution

## Introduction

The **Porter-Thomas distribution** is a fundamental probability distribution that arises in the study of complex, chaotic quantum systems. Originally formulated in the context of nuclear physics, it has become a cornerstone of **[[Notes/2025/10/06/Random Matrix Theory\|Random Matrix Theory]] (RMT)** and has found a crucial modern application in the benchmarking of quantum computers, particularly in the task of [[Notes/2025/10/06/Random Circuit Sampling\|Random Circuit Sampling]].

In essence, the Porter-Thomas distribution describes the ***statistical fluctuations of the squared components of a random vector in a high-dimensional space***. In the context of quantum mechanics, it predicts the probability distribution of measurement outcomes from a sufficiently complex or "chaotic" quantum evolution. Its emergence is a universal signature of [[Notes/2025/10/06/Quantum Chaos\|Quantum Chaos]], and its ***characteristic "spiky"*** profile provides a powerful tool for verifying the correct operation of quantum processors.

## Mathematical Formulation

The Porter-Thomas distribution is a specific case of the [[Notes/2025/10/06/Chi-Squared Distribution\|Chi-Squared Distribution]] with one degree of freedom ($\chi_1^2$), which is equivalent to an exponential distribution. It describes the probability density $P(x)$ of a variable $x$. In the context of quantum circuits, $x$ represents the probability of measuring a specific output state.

The distribution is given by:
$$
P(x) = N e^{-Nx}
$$
where:
- $x$ is the probability of a single measurement outcome (e.g., $p(s) = |\langle s|\psi\rangle|^2$).
- $N$ is the dimension of the Hilbert space of the system. For a system of $n$ qubits, $N = 2^n$.

This distribution is normalized such that $\int_0^\infty P(x) dx = 1$. It implies that outcomes with very small probabilities are extremely common, while outcomes with large probabilities are exponentially rare.

## Origin and Derivation from Random Unitary Matrices

The Porter-Thomas distribution was first introduced in a 1956 paper by C. E. Porter and R. G. Thomas to describe fluctuations in the resonance widths of heavy atomic nuclei. The underlying physics is that of a complex, many-body quantum system whose dynamics are chaotic. The modern derivation, highly relevant to quantum computing, comes from considering the properties of large random unitary matrices, which are used to model the evolution of a random quantum circuit.

Let's consider a random quantum circuit on $n$ qubits, which implements a random unitary operator $U$ of dimension $N \times N$, where $N=2^n$. If we start in the initial state $|0^n\rangle$, the probability of measuring a specific output bitstring $|z\rangle$ is given by the squared magnitude of a single matrix element:
$$
x = p(z) = |\langle z | U | 0^n \rangle|^2 = |U_{z0}|^2
$$
***The Porter-Thomas distribution, therefore, describes the distribution of these probability values, $x$, across all possible outputs $z$.***

The derivation proceeds as follows:
1. **Unitary Constraint**: The columns of a unitary matrix are normalized vectors. For the first column (corresponding to the initial state $|0^n\rangle$), this means:
    $$
    \sum_{z=0}^{N-1} |U_{z0}|^2 = 1
    $$
2. **Joint Probability**: This normalization constrains the joint probability of all the elements in the column. Assuming a uniform distribution over the space of all possible unitary matrices (the [[Notes/2025/10/06/Haar Measure\|Haar Measure]]), the joint probability of the column's elements is proportional to a delta function enforcing this constraint:$$
	    P(U_{00}, \dots, U_{(N-1)0}) \propto \delta\left(1 - \sum_{j=0}^{N-1} |U_{j0}|^2\right)
	    $$
	1. We can integrate, for example, the last element $U_{iN}$​, to get a marginal on the remainder of the matrix elements.$$
		P\left(U_{k 1}, \ldots, U_{k 2}, U_{k(N-1)}\right)=\int d(x) P\left(U_{k 1}, \ldots, U_{k 2}, U_{k(N-1)}, x\right)
		$$
	2. Realizing that the integral of delta function is the [[Notes/2025/10/06/Heaviside Theta function\|Heaviside Theta function]], we get something like the following$$
		P\left(U_{k 1}, \ldots, U_{k 2}, U_{k(N-1)}\right) \propto \theta\left(1-\sum_{j=1}^{N-1}\left|U_{k j}\right|^2\right) .
		$$
	3. Calculating further marginals is a bit tricky. We can verify the following property for Heaviside-theta functions.$$
		\int_0^{\infty} \theta\left(1-x^2-a^2\right) d x \propto \sqrt{1-\alpha^2} \theta\left(1-\alpha^2\right)
		$$
	4. Using this, we can integrate over one more matrix element $U_{k(N−1)}$​, we get something of the form$$
			P\left(U_{k 1}, \ldots, U_{k 2}, U_{k(N-2)}\right) \propto\left(1-\sum_{j=1}^{N-2}\left|U_{k j}\right|^2\right) \theta\left(1-\sum_{j=1}^{N-2}\left|U_{k j}\right|^2\right)
			$$
3. **Marginal Distribution**: To find the probability distribution for a single element, say $U_{k0}$, we must integrate out all other $N-1$ elements. This is a high-dimensional integral. By iteratively integrating out the variables, one can show that the marginal distribution for the squared magnitude $x = |U_{k0}|^2$ is:
    $$
    P(x) \propto (1-x)^{N-2}
    $$
4.  **Large N Approximation**: In the limit of a large Hilbert space ($N \gg 1$), which is typical for quantum advantage experiments, and for small values of $x$ (which are the most probable), this expression can be approximated by an exponential function:
    $$
    (1-x)^{N-2} \approx \left(1 - \frac{Nx}{N}\right)^{N-2} \approx e^{-Nx}
    $$
5.  **Normalization**: To get the final probability distribution, we introduce a normalization constant $C$ and ensure the integral over all possible values is 1.
    $$
    \int_0^1 C e^{-Nx} dx = 1 \implies C \approx N
    $$
    This gives the final, celebrated result:
    $$
    P(x) \approx N e^{-Nx}
    $$

## Application in Quantum Computing

The Porter-Thomas distribution is the theoretical foundation for the task of [[Notes/2025/10/06/Random Circuit Sampling\|Random Circuit Sampling]], which is used to benchmark quantum computers.

### The "Speckle" Signature of Quantum Interference

When a deep, chaotic quantum circuit is executed, the output probabilities are not uniform. The Porter-Thomas distribution predicts that the probability landscape will be highly "spiky" or "speckled."
- The vast majority of the $2^n$ possible output bitstrings will have a near-zero probability of being measured.
- A small number of bitstrings will have a significantly higher-than-average probability.

This speckle pattern is a direct consequence of the complex, multi-path quantum interference occurring within the circuit. It is a unique fingerprint of a correctly functioning, coherent quantum computation. A noisy or faulty quantum computer would fail to produce this delicate interference pattern, leading to a flatter, more uniform output distribution that resembles random noise.

### Benchmarking and Quantum Advantage

This predictable statistical signature is exploited in [[Notes/2025/10/06/Cross-Entropy Benchmarking\|Cross-Entropy Benchmarking]] (XEB).
- A classical computer simulates the random circuit (for a small enough number of qubits) to calculate the ideal Porter-Thomas distribution of probabilities.
- The quantum computer is then run many times to collect experimental samples.
- If the quantum computer is working correctly, the bitstrings it produces should be preferentially drawn from the "spikes" of the theoretical distribution.
- The XEB fidelity metric quantifies this correlation. A high fidelity confirms that the device is generating the classically intractable speckle pattern, providing strong evidence of its quantum capabilities.

## Conclusion

The Porter-Thomas distribution is a powerful and universal statistical law that governs the behavior of complex quantum systems. What began as a tool to understand the chaotic energy levels of atomic nuclei has become a central concept in the quest for quantum advantage. It provides a clear, quantitative signature of quantum chaos, allowing physicists to verify that a quantum processor is performing a computation so complex that it lies beyond the reach of classical simulation.

