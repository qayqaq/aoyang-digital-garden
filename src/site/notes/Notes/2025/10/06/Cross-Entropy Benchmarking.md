---
{"dg-publish":true,"permalink":"/notes/2025/10/06/cross-entropy-benchmarking/"}
---

#quantum-computing #benchmarking #quantum-advantage
[[Cross-Entropy Benchmarking.canvas\|Cross-Entropy Benchmarking.canvas]]

# Cross-Entropy Benchmarking

## Introduction

**Cross-Entropy Benchmarking (XEB)** is a powerful statistical method used to quantify the performance and fidelity of a quantum computer. It is particularly significant for assessing the capabilities of [[Notes/2025/10/06/Noisy Intermediate-Scale Quantum\|Noisy Intermediate-Scale Quantum]] (NISQ) devices, especially in the context of demonstrating **quantum advantage**—the point at which a quantum processor can perform a computational task that is intractable for even the most powerful classical supercomputers.

The core purpose of XEB is to provide a holistic, system-level score that measures how closely the experimental output distribution of a quantum circuit matches the ideal, theoretical distribution that a perfect, noiseless device would produce. It was famously used in Google's 2019 Sycamore experiment to provide evidence of quantum supremacy. XEB is designed for tasks like **[[Notes/2025/10/06/Random Circuit Sampling\|random circuit sampling]]**, which are believed to be classically hard but are native to the operation of quantum computers.

## The Core Principle: Comparing to the Ideal

The fundamental idea behind XEB is to test a quantum computer's ability to reproduce the highly structured, "speckled" probability distribution that results from a random quantum circuit.

1. **The Task**: A quantum computer is programmed to execute a specific, typically random, quantum circuit.
2. **Ideal Distribution**: For a random quantum circuit, the probability of measuring any given output bitstring is not uniform. Due to quantum interference, some bitstrings will have a significantly higher probability of being measured than others. This creates a complex, spiky probability landscape. A classical supercomputer can, for a limited number of qubits, calculate this entire ideal probability distribution, $p(s)$, for every possible bitstring $s$.
3. **Experimental Sampling**: The quantum computer is run many times, and each run is terminated with a measurement, yielding a collection of output bitstrings. This set of samples constitutes the experimental distribution, $E$.
4. **The Comparison**: XEB measures the correlation between the experimental samples and the ideal distribution. A high-fidelity quantum computer will be more likely to produce the bitstrings that have a high ideal probability. In contrast, a very noisy device will lose the quantum interference pattern, and its output will look more like a flat, uniform distribution of random bitstrings.

> In essence, XEB asks the question: "Of the bitstrings my quantum computer produced, what was their average probability of occurring according to the ideal, noiseless theory?" A high average probability indicates high performance.

## Mathematical Formulation

The performance of the quantum device is quantified by the **Linear Cross-Entropy Benchmarking Fidelity**, denoted $\mathcal{F}_{\mathrm{XEB}}$. It is defined as a normalized correlation between the experimental and ideal distributions.

The full definition of the fidelity is:
$$
\mathcal{F}_{\mathrm{XEB}}(E)=\frac{\langle p(s)\rangle_{s \in E}-\langle p(s)\rangle_{s \in \mathcal{U}}}{\langle p(s)\rangle_{s \in p}-\langle p(s)\rangle_{s \in \mathcal{U}}}
$$
where:
- $E$ is the distribution of experimentally measured bitstrings.
- $p$ is the ideal probability distribution from a noiseless simulation.
- $\mathcal{U}$ is the uniform distribution over all possible bitstrings.
- $\langle p(s)\rangle_{s \in S}$ denotes the average of the ideal probabilities $p(s)$ over samples $s$ drawn from a distribution $S$.

The key terms are:
-   $\langle p(s)\rangle_{s \in E}$: The average ideal probability of the bitstrings that were **actually measured** in the experiment. This is the central quantity being calculated.
-   $\langle p(s)\rangle_{s \in \mathcal{U}}$: The average ideal probability if one were to just guess bitstrings uniformly at random. This serves as the baseline for zero fidelity.
-   $\langle p(s)\rangle_{s \in p}$: The average ideal probability over the ideal distribution itself. This normalizes the metric so that a perfect device achieves a fidelity of 1.

### Simplified Form for Large Systems

In the limit of a large number of qubits $n$, the expression simplifies significantly. For chaotic circuits, the ideal probabilities follow a [[Notes/2025/10/06/Porter-Thomas distribution\|Porter-Thomas distribution]], and the formula converges to a much simpler and more common expression:
$$
\mathcal{F}_{\mathrm{XEB}}(E) \approx \left\langle 2^{n} p(s)-1\right\rangle_{s \in E}
$$
where $n$ is the number of qubits.

**Interpretation of the Fidelity Score:**
-   $\mathcal{F}_{\mathrm{XEB}} = 1$: Perfect correspondence. The experimental device is performing exactly as the ideal, noiseless theory predicts.
-   $\mathcal{F}_{\mathrm{XEB}} = 0$: No correspondence. The device's output is indistinguishable from random noise (the uniform distribution).

## Advantages and Limitations

### Advantages
- **Holistic Benchmark**: XEB provides a single metric that is sensitive to all sources of error in a quantum computation—gate errors, qubit decoherence, crosstalk, and readout errors.
- **Scalability**: It is designed to work in a regime where the number of qubits makes classical simulation extremely demanding, making it a suitable tool for demonstrating quantum advantage.
- **Sensitivity to Errors**: It is a stringent test. Any small, incoherent error will degrade the interference pattern and lower the XEB fidelity.

### Limitations
- **Classical Simulation Bottleneck**: The primary drawback is the requirement to classically compute the ideal probabilities $p(s)$. This becomes exponentially difficult with the number of qubits and is precisely the reason random circuit sampling is a good candidate for quantum advantage. This limits direct XEB validation to the boundary of what classical supercomputers can handle (around 50-60 qubits).
- **Task Specificity**: XEB benchmarks performance on a highly specific and abstract task. High fidelity in random circuit sampling does not automatically imply that the device will perform well on structured algorithms with practical applications, such as Shor's algorithm for factoring.
- **Requires Ideal Probabilities**: The method relies on having access to the ideal distribution. For verification beyond the classical simulation limit, one can use circuits where the probabilities are easy to compute, such as Clifford circuits, to benchmark the device's performance on a classically tractable problem.

## Conclusion

Cross-Entropy Benchmarking is a cornerstone technique for validating and assessing the performance of near-term quantum processors. It provides a robust, system-level fidelity metric that is uniquely suited to the task of demonstrating quantum advantage through random circuit sampling. While its reliance on classical simulation poses a fundamental limitation, XEB remains a critical and widely accepted standard in the field, offering one of the most compelling methods for probing the boundary between classical and quantum computational power.

