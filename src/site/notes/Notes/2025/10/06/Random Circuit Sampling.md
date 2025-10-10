---
{"dg-publish":true,"permalink":"/notes/2025/10/06/random-circuit-sampling/"}
---

#quantum-computing #benchmarking #quantum-advantage #computational-complexity
[[Random Circuit Sampling.canvas\|Random Circuit Sampling.canvas]]

# Random Circuit Sampling

## Introduction

**Random Circuit Sampling (RCS)** is a computational problem that has become a cornerstone for benchmarking near-term quantum computers and a primary vehicle for demonstrating **quantum advantage** (also known as quantum supremacy). The task is simple to state: to produce a collection of bitstring samples from the output probability distribution of a randomly generated quantum circuit.

While this task may seem abstract and without immediate practical application, its significance lies in its computational complexity. It is strongly believed to be a problem that is fundamentally easy for a quantum computer to perform but exponentially difficult for even the most powerful classical supercomputers. This makes RCS an ideal "stress test" for a quantum processor, as it exercises the entire system in a way that leverages the core principles of quantum mechanics—superposition and interference—to create a computational challenge that is classically intractable.

## The Computational Task

The process of random circuit sampling involves three main steps: constructing a random circuit, executing it on a quantum processor, and collecting the measurement outcomes.

### 1. Circuit Construction

A random quantum circuit is built by applying a sequence of quantum gates, chosen randomly from a specific set, to a register of qubits. A typical construction is as follows:
- **Initialization**: All $n$ qubits are initialized in a simple product state, usually $|00...0\rangle$.
- **Layered Gates**: The circuit consists of multiple layers or "cycles." Each layer is composed of:
    1. A round of **single-qubit gates** applied to every qubit. Each gate is chosen randomly from a universal set (e.g., Hadamard, $\sqrt{X}$, $\sqrt{Y}$).
    2. A round of **two-qubit entangling gates** (e.g., CNOT, iSWAP, or Sycamore gates) applied to a specific pattern of neighboring qubits.
- **Final Measurement**: After a certain number of layers (the "depth" of the circuit), all qubits are measured in the computational basis to produce an $n$-bit string.

The specific choice of gates and their arrangement is fixed for a given instance of the problem but is chosen randomly to create a "generic" or chaotic quantum evolution.

### 2. Execution and Sampling

The quantum computer is programmed with this specific random circuit. The circuit is then executed, and the final measurement yields a single bitstring. This process is repeated thousands or millions of times, with each execution producing a new sample bitstring. The goal is to collect a representative sample from the circuit's output distribution.

## The Classical Hardness of the Problem

The difficulty for a classical computer arises from the nature of the quantum state that the random circuit produces.

### The Exponential Cost of Simulation

To simulate the quantum circuit classically, one must track the state vector $|\psi\rangle$, which is a vector of $2^n$ complex amplitudes. Applying each gate corresponds to multiplying this enormous vector by a sparse matrix.
- **Memory**: Storing the state vector requires $2^n \times (\text{size of complex number})$ bytes of memory, which quickly exceeds the capacity of any supercomputer for $n > 50$.
- **Computation**: The number of operations scales with the number of gates and the size of the state vector.

The final step, calculating the probability of a specific output bitstring $s$, requires computing the squared magnitude of the corresponding amplitude: $p(s) = |\langle s | \psi \rangle|^2$. Calculating the entire probability distribution is computationally infeasible.

### The Porter-Thomas Distribution

Due to the chaotic nature of the random circuit, the [[Notes/2025/10/06/Quantum Interference\|Quantum Interference]] between the $2^n$ computational basis states is highly complex. This leads to a final probability distribution that is far from uniform. The probabilities $p(s)$ themselves are predicted to follow a specific statistical distribution known as the **[[Notes/2025/10/06/Porter-Thomas distribution\|Porter-Thomas distribution]]**, which is an exponential distribution:
$$
P(p) = d \cdot e^{-d \cdot p}
$$
where $d=2^n$ is the dimension of the Hilbert space.

This distribution has a characteristic "spiky" or "speckled" appearance. A few output bitstrings have a high probability of occurring, while the vast majority have a near-zero probability. It is this complex, interference-generated pattern that a classical computer struggles to reproduce. Any classical algorithm that attempts to sample from this distribution without performing the full, exponentially costly simulation is believed to fail.

## The Quantum Easiness of the Problem

In stark contrast to the classical difficulty, random circuit sampling is a task that is native to a quantum computer.
-   **Natural Evolution**: A quantum computer is a physical device that evolves according to the laws of quantum mechanics. Executing a circuit is simply guiding this natural evolution.
-   **Direct Sampling**: When the quantum computer is measured at the end of the circuit's execution, it naturally produces a sample from the very distribution that is so hard to calculate classically. The device does not need to compute the probabilities; it simply embodies them.

## Role in Demonstrating Quantum Advantage

Random circuit sampling was specifically designed as a benchmark for demonstrating that a quantum processor can outperform any classical machine on a well-defined computational task.

### A Benchmark for Quantum Supremacy

The 2019 Google AI Quantum experiment, using the 53-qubit **Sycamore** processor, is the most famous application of RCS.
-   The team executed a random circuit sampling task that produced 1 million samples in approximately 200 seconds.
-   They estimated that the most powerful classical supercomputer at the time (IBM's Summit) would require approximately 10,000 years to perform the equivalent task of calculating the probabilities for the experimental samples to verify the result.
-   This was presented as the first experimental demonstration of quantum advantage.

### Verification with Cross-Entropy Benchmarking

A crucial component of these experiments is verifying that the quantum computer is actually performing the task correctly and not just producing random noise. This is done using [[Notes/2025/10/06/Cross-Entropy Benchmarking\|Cross-Entropy Benchmarking]] (XEB), which statistically compares the experimentally obtained samples to the theoretically predicted probabilities. A high XEB fidelity confirms that the device is genuinely sampling from the classically-hard-to-simulate distribution.

## Conclusion

Random Circuit Sampling is a foundational benchmark in the era of noisy intermediate-scale quantum (NISQ) computing. It serves as a powerful diagnostic tool by testing the collective performance of all components of a quantum processor in a complex, chaotic regime. While it does not solve a problem of practical utility, its value lies in its carefully engineered computational hardness for classical machines. As such, it provides a clear, albeit abstract, milestone for charting the progress of quantum hardware and serves as the primary method for demonstrating the point at which quantum devices can enter a computational realm beyond the reach of classical simulation.

