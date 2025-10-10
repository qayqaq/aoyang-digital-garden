---
{"dg-publish":true,"permalink":"/notes/2025/10/06/measurement-based-quantum-computing/"}
---

#QuantumComputing #QuantumAlgorithms #Entanglement

[[Measurement-Based Quantum Computing.canvas\|Measurement-Based Quantum Computing.canvas]]

# Measurement-Based Quantum Computing (MBQC)

## 1. Introduction

**Measurement-Based Quantum Computing (MBQC)**, also known as the **one-way quantum computer**, is a model of quantum computation that is fundamentally different from the more conventional circuit-based model. In the standard model, computation is realized by applying a sequence of unitary quantum gates to an initial state of qubits. In contrast, ***MBQC achieves computation through a sequence of adaptive single-qubit measurements performed on a highly entangled, universal resource state***.

The significance of MBQC is twofold. First, it is provably equivalent in computational power to the circuit model, meaning any quantum algorithm can be implemented within this paradigm. Second, it provides a profound shift in perspective, recasting **entanglement** not merely as a quantum phenomenon, but as the primary, consumable **resource** that drives computation. This model has inspired novel hardware architectures and theoretical concepts, including the [[Notes/2025/10/06/Instantaneously Deep Quantum Neural Network\|Instantaneously Deep Quantum Neural Network]].

## 2. The Core Principles

The MBQC model is built upon three fundamental components: ***a universal resource state, a sequence of measurements, and a classical feedforward mechanism.***

### 2.1. The Universal Resource State
The computation does not begin with a simple initial state like $|0\rangle^{\otimes n}$. Instead, it starts with the preparation of a specific, large, and highly entangled multi-qubit state. This state is universal, meaning the same type of resource state can be used to run any quantum algorithm.

The most common resource state is the **cluster state** (or more generally, a **graph state**). A cluster state can be visualized as a lattice of qubits, where each qubit is entangled with its nearest neighbors. For example, a 2D cluster state, which is a universal resource, is created by:
1. Initializing all qubits in the state $|+\rangle = \frac{1}{\sqrt{2}}(|0\rangle + |1\rangle)$.
2. Applying a Controlled-Z (CZ) gate between every pair of adjacent qubits on the lattice.

This preparation step, which can be resource-intensive, is performed once at the beginning of the computation.

### 2.2. Computation via Measurement
The "processing" in MBQC is performed by measuring individual qubits of the cluster state in specific bases (e.g., the computational basis $\{|0\rangle, |1\rangle\}$, the diagonal basis $\{|+\rangle, |-\rangle\}$, or more general rotated bases).

The act of measuring a qubit has two effects:
1. It projects the qubit into a definite classical state (0 or 1).
2. It alters the state of the remaining, unmeasured qubits, effectively "propagating" the computation through the cluster state. A measurement in a particular basis can be shown to be equivalent to applying a specific quantum gate.

### 2.3. Adaptivity and Classical Feedforward
Quantum measurements are inherently probabilistic. The outcome of measuring a qubit is random. This randomness would disrupt a deterministic computation if not corrected.

This is where **classical feedforward** becomes essential. The classical outcome of a measurement on one qubit is used in real-time to choose the measurement basis for a subsequent qubit. This **adaptive** nature of the measurements allows the system to correct for the randomness of previous outcomes, ensuring that the overall computation is deterministic and implements the desired algorithm. This flow of classical information is what "steers" the quantum computation.

## 3. The "One-Way" Nature of MBQC

MBQC is often called a "one-way" quantum computer because the measurement process irreversibly consumes the entanglement of the resource state. Each measurement disentangles the measured qubit from the rest of the cluster, effectively destroying a piece of the computational resource. Once used, the resource state cannot be reused for another computation. The computation flows in one direction, from the input qubits to the output qubits, consuming the entangled state along the way.

## 4. A Conceptual Walkthrough

A typical MBQC algorithm proceeds as follows:
1.  **Preparation**: A large cluster state is created, sufficient for the entire algorithm.
2.  **Input Encoding**: The input quantum state is encoded onto the first few qubits of the cluster, typically by entangling them with the cluster.
3.  **Sequential Measurement**: The qubits are measured in a predetermined sequence. The choice of measurement basis for qubit $k$ depends on the classical outcomes of measurements on qubits $1, \dots, k-1$.
4.  **Correction**: The classical feedforward loop applies corrections, ensuring the correct quantum gates are simulated. For example, a random measurement outcome might introduce an unwanted Pauli $Z$ or $X$ operator. The feedforward adjusts a future measurement basis to effectively commute this error past the logical output, or to apply an inverse operation.
5.  **Output**: The final qubits in the sequence, which are left unmeasured, hold the final quantum state—the result of the computation.

## 5. Advantages and Implications

### Advantages
-   **Separation of Concerns**: It decouples the difficult task of generating multi-qubit entanglement from the computational steps. This is particularly advantageous for physical systems like photonics, where creating entangled states is feasible but applying deterministic two-qubit gates is challenging.
-   **Potential for Robustness**: The model may offer advantages for fault-tolerant quantum computing architectures.

### Theoretical Implications
-   **Entanglement as a Resource**: MBQC provides a clear framework for quantifying entanglement as a computational resource.
-   **Inspiration for New Models**: It has inspired other computational models, such as the [[Notes/2025/10/06/Instantaneously Deep Quantum Neural Network\|Instantaneously Deep Quantum Neural Network]], which adapts the idea of using a shallow, entangled state to perform a powerful computation. The IDQNN uses parallel, non-adaptive measurements to probabilistically sample from deep circuits, a direct conceptual descendant of MBQC.

## 6. Conclusion

Measurement-Based Quantum Computing offers a powerful and elegant alternative to the standard circuit model. By placing entanglement at the forefront as a consumable resource, it fundamentally reframes our understanding of what drives a quantum computation. While the practical challenges of creating large-scale, high-fidelity resource states are significant, the MBQC paradigm remains a vital area of research, providing deep theoretical insights and inspiring novel approaches to building the quantum computers of the future.

