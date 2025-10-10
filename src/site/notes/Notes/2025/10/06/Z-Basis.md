---
{"dg-publish":true,"permalink":"/notes/2025/10/06/z-basis/"}
---

#QuantumComputing #QuantumInformation #LinearAlgebra

[[Z-basis.canvas\|Z-basis.canvas]]

# Z-basis

## 1. Introduction

The **Z-basis**, more commonly known as the **computational basis** or **standard basis**, is the most fundamental and widely used basis for describing the state of qubits in quantum computing. It is the quantum analogue of the binary states `0` and `1` used in classical computing, providing a direct and intuitive framework for representing and processing information.

The significance of the Z-basis stems from its dual role: it serves as the default language for defining quantum states and algorithms, and it is the basis in which standard quantum measurements are performed. Its name originates from the fact that its basis vectors are the eigenstates of the **Pauli-Z operator**, a fundamental quantum gate. Understanding the Z-basis is the first and most crucial step in comprehending the representation of quantum information.

## 2. Mathematical Definition

The Z-basis for a single qubit is an orthonormal basis spanning the two-dimensional complex vector space (Hilbert space) of the qubit. It consists of two basis vectors, denoted by the kets $|0\rangle$ and $|1\rangle$.

In vector notation, they are represented as:
$$
|0\rangle = \begin{pmatrix} 1 \\ 0 \end{pmatrix} \quad \text{and} \quad |1\rangle = \begin{pmatrix} 0 \\ 1 \end{pmatrix}
$$
These vectors form an **orthonormal basis**, which means they satisfy two key properties:
- **Orthogonality**: They are mutually perpendicular, meaning their inner product is zero: $\langle 0 | 1 \rangle = 0$.
- **Normalization**: They are unit vectors, meaning their inner product with themselves is one: $\langle 0 | 0 \rangle = 1$ and $\langle 1 | 1 \rangle = 1$.

Any arbitrary pure state of a single qubit, $|\psi\rangle$, can be expressed as a linear combination (a superposition) of these two basis vectors:
$$
|\psi\rangle = \alpha|0\rangle + \beta|1\rangle
$$
where $\alpha$ and $\beta$ are complex numbers called **probability amplitudes**, satisfying the normalization condition $|\alpha|^2 + |\beta|^2 = 1$.

## 3. The Eigenbasis of the Pauli-Z Operator

The name "Z-basis" is derived from the **Pauli-Z operator**, one of the three fundamental Pauli matrices, represented as:
$$
\sigma_z = Z = \begin{pmatrix} 1 & 0 \\ 0 & -1 \end{pmatrix}
$$
The basis vectors $|0\rangle$ and $|1\rangle$ are the **eigenstates** of the Z operator, with corresponding **eigenvalues** $+1$ and $-1$, respectively. This relationship is shown by the following eigenvalue equations:
$$
Z|0\rangle = \begin{pmatrix} 1 & 0 \\ 0 & -1 \end{pmatrix} \begin{pmatrix} 1 \\ 0 \end{pmatrix} = \begin{pmatrix} 1 \\ 0 \end{pmatrix} = +1 \cdot |0\rangle
$$
$$
Z|1\rangle = \begin{pmatrix} 1 & 0 \\ 0 & -1 \end{pmatrix} \begin{pmatrix} 0 \\ 1 \end{pmatrix} = \begin{pmatrix} 0 \\ -1 \end{pmatrix} = -1 \cdot |1\rangle
$$
This property is physically significant: when a measurement corresponding to the Z observable is performed, the quantum state is projected onto one of these two eigenstates.

## 4. The Role in Quantum Measurement

In the context of quantum computation, a **measurement in the computational basis** is the standard procedure for extracting classical information from a qubit.
> According to the **Born rule**, when a qubit in the state $|\psi\rangle = \alpha|0\rangle + \beta|1\rangle$ is measured in the Z-basis, its state instantaneously collapses to one of the two basis states.

The probabilities of the two possible outcomes are:
-   The probability of measuring the outcome `0` (and the state collapsing to $|0\rangle$) is $P(0) = |\alpha|^2$.
-   The probability of measuring the outcome `1` (and the state collapsing to $|1\rangle$) is $P(1) = |\beta|^2$.

This measurement process is the bridge between the quantum world of superposition and the classical world of definite bit values.

## 5. Generalization to Multi-Qubit Systems

The concept of the computational basis extends naturally to systems of multiple qubits through the **tensor product**. For an $n$-qubit system, the computational basis consists of $2^n$ orthonormal basis vectors, each represented by a binary string of length $n$.

For a two-qubit system, the four basis vectors are:
-   $|00\rangle = |0\rangle \otimes |0\rangle = (1, 0, 0, 0)^T$
-   $|01\rangle = |0\rangle \otimes |1\rangle = (0, 1, 0, 0)^T$
-   $|10\rangle = |1\rangle \otimes |0\rangle = (0, 0, 1, 0)^T$
-   $|11\rangle = |1\rangle \otimes |1\rangle = (0, 0, 0, 1)^T$

Any state of an $n$-qubit register can be written as a superposition of these $2^n$ basis states.

## 6. Relationship to Other Bases

While the Z-basis is the standard, other bases are crucial for quantum algorithms and tomography. The most common are the **X-basis** and **Y-basis**, which are the eigenbases of the Pauli-X and Pauli-Y operators, respectively.

-   **X-basis (Hadamard/Diagonal Basis)**: $\{|+\rangle, |-\rangle\}$
    -   $|+\rangle = \frac{1}{\sqrt{2}}(|0\rangle + |1\rangle)$
    -   $|-\rangle = \frac{1}{\sqrt{2}}(|0\rangle - |1\rangle)$
-   **Y-basis (Circular Basis)**: $\{|i\rangle, |-i\rangle\}$
    -   $|i\rangle = \frac{1}{\sqrt{2}}(|0\rangle + i|1\rangle)$
    -   $|-i\rangle = \frac{1}{\sqrt{2}}(|0\rangle - i|1\rangle)$

Measurements in these other bases are performed by applying a change-of-basis unitary transformation (e.g., a Hadamard gate to switch between the Z and X bases) immediately before a standard Z-basis measurement.

## 7. Conclusion

The Z-basis is the bedrock of quantum computation. It provides the foundational language for representing quantum states, defining the action of quantum gates, and, most critically, interpreting the results of quantum measurements. Its direct correspondence with classical bits makes it an indispensable tool for designing and understanding quantum algorithms. While computation and analysis often require transformations to other bases, the journey of quantum information almost always begins and ends in the familiar and essential framework of the computational basis.

