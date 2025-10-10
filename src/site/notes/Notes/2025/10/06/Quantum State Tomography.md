---
{"dg-publish":true,"permalink":"/notes/2025/10/06/quantum-state-tomography/"}
---

#QuantumComputing #QuantumTomography #QuantumInformation

[[Quantum State Tomography.canvas\|Quantum State Tomography.canvas]]

# Quantum State Tomography (QST)

## 1. Introduction

**Quantum State Tomography (QST)** is a comprehensive experimental procedure used to fully reconstruct the quantum state of a system. In essence, it is the process of "taking a picture" of a quantum state to determine its complete mathematical description. This description is captured by the **[[Notes/2025/10/06/Density Matrix\|density matrix]]**, $\rho$, which contains all knowable information about the state, including its purity, coherences, and populations.

QST is the gold standard for verifying the preparation of quantum states and for characterizing the output of quantum operations. By comparing the experimentally reconstructed state with the theoretically expected one, researchers can quantify the fidelity of their quantum hardware. However, while being exhaustive, standard QST is an extremely resource-intensive process, suffering from a fundamental limitation known as the "curse of dimensionality," which makes it impractical for large quantum systems.

## 2. The Objective: Reconstructing the Density Matrix

The state of any $n$-qubit quantum system, whether pure or mixed, can be described by a $2^n \times 2^n$ density matrix, $\rho$. This matrix has the following properties:
1. **Hermiticity**: $\rho = \rho^\dagger$.
2. **Positive Semi-definiteness**: $\langle \psi | \rho | \psi \rangle \ge 0$ for any state $|\psi\rangle$.
3. **Unit Trace**: $\text{Tr}(\rho) = 1$.

The goal of QST is to experimentally determine all the elements of this matrix. For an $n$-qubit system, this requires finding $4^n - 1$ independent real parameters.

## 3. The Tomographic Procedure

The core principle of QST is to ***measure the expectation values of a complete set of basis operators***. Any operator can be expressed as a linear combination of these basis operators; therefore, by knowing their expectation values, we can reconstruct the density matrix.

### 3.1. Single-Qubit Tomography: A Concrete Example
For a single qubit, the density matrix can be expanded in the basis of the Pauli matrices $\{I, \sigma_x, \sigma_y, \sigma_z\}$:
$$
\rho = \frac{1}{2} (I + \langle\sigma_x\rangle\sigma_x + \langle\sigma_y\rangle\sigma_y + \langle\sigma_z\rangle\sigma_z)
$$
Here, the coefficients $\langle\sigma_i\rangle = \text{Tr}(\rho \sigma_i)$ are the expectation values of the Pauli operators. The task of QST reduces to measuring these three real numbers. This is achieved through three distinct sets of experiments, each requiring many identical copies of the state $\rho$:

1. **Measure $\langle\sigma_z\rangle$**: Measure the qubit in the computational basis $\{|0\rangle, |1\rangle\}$ many times. The expectation value is the difference between the probability of measuring $|0\rangle$ and $|1\rangle$.
2. **Measure $\langle\sigma_x\rangle$**: Measure the qubit in the diagonal basis $\{|+\rangle, |-\rangle\}$. Experimentally, this is equivalent to applying a Hadamard gate ($H$) before the standard Z-basis measurement.
3. **Measure $\langle\sigma_y\rangle$**: Measure the qubit in the circular basis $\{|i\rangle, |-i\rangle\}$. This is equivalent to applying a phase gate followed by a Hadamard gate ($HS^\dagger$) before the Z-basis measurement.

Once these three expectation values are determined, the density matrix $\rho$ is fully reconstructed.

### 3.2. Multi-Qubit Tomography
The procedure generalizes to $n$ qubits by using the tensor products of Pauli matrices as the operator basis. There are $4^n$ such operators (e.g., $\sigma_x \otimes I \otimes \sigma_z, \dots$). To reconstruct the full density matrix, one must measure the expectation value of each of these basis operators.

This requires performing measurements in many different product bases. For example, to measure $\langle \sigma_x \otimes \sigma_z \rangle$, one would measure the first qubit in the X-basis and the second qubit in the Z-basis simultaneously. In total, this requires **$3^n$ different measurement settings**.

## 4. The Curse of Dimensionality: The Fundamental Limitation

The exponential scaling of QST with the number of qubits makes it fundamentally intractable for all but the smallest systems. This "curse of dimensionality" manifests in three ways:

1.  **Measurement Cost**: The number of required experimental configurations (measurement settings) grows exponentially as $3^n$.
2.  **Sampling Cost**: For each setting, a large number of repeated measurements are needed to estimate the expectation values to a sufficient statistical precision.
3.  **Classical Post-Processing Cost**: Storing the $2^n \times 2^n$ density matrix and performing the classical reconstruction from the raw measurement data (often using computationally intensive methods like maximum likelihood estimation) also scales exponentially.

Due to these exponential overheads, full quantum state tomography is practically limited to systems of approximately 10-12 qubits.

## 5. Modern Alternatives to Full Tomography

The severe limitations of QST have spurred the development of more scalable and targeted characterization methods. The key insight is that for many practical applications, one does not need to know *everything* about the state.

- **[[Notes/2025/10/06/Classical Shadow\|Classical Shadow]] Tomography**: This is a highly efficient, randomized measurement protocol. Instead of reconstructing the full density matrix, it creates a compact classical description (the "shadow") from which many properties (e.g., fidelities, expectation values) can be predicted with a number of measurements that scales polynomially with the number of qubits and logarithmically with the number of properties to be estimated.
- **Compressed Sensing Tomography**: If the quantum state is known to have some structure (e.g., it is a pure state or a low-rank mixed state), its density matrix can be reconstructed from far fewer measurements than standard QST would require.
- **Matrix Product State (MPS) Tomography**: For quantum states with low entanglement, which are common in one-dimensional physical systems, the state can be efficiently represented as an MPS. Tomography can then focus on learning the much smaller tensors that constitute the MPS.

## 6. Conclusion

Quantum State Tomography is the definitive method for completely characterizing a quantum state. It serves as an indispensable diagnostic tool for small-scale quantum processors and a crucial benchmark for verifying quantum operations. However, its exponential scaling in both measurement and computational resources renders it infeasible for the large quantum systems required for fault-tolerant quantum computing. The future of quantum system characterization lies in more scalable techniques like [[Notes/2025/10/06/Classical Shadow\|Classical Shadows]], which trade the goal of complete reconstruction for the practical ability to efficiently learn specific, relevant properties of a quantum state.

