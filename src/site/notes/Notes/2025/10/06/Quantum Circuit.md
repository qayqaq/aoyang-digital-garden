---
{"dg-publish":true,"permalink":"/notes/2025/10/06/quantum-circuit/"}
---

#QuantumComputing #QuantumInformation #ComputerScience

[[Quantum Circuit.canvas\|Quantum Circuit.canvas]]

# Quantum Circuit

## Introduction

A **quantum circuit** is the standard model for quantum computation, analogous to a classical circuit in conventional computing. While classical circuits operate on bits using logic gates like AND, OR, and NOT, quantum circuits operate on **qubits** using **quantum gates**. A quantum circuit provides a visual and mathematical framework for describing a sequence of quantum operations, forming the basis for designing and implementing quantum algorithms.

The model consists of three fundamental components:
1.  A register of qubits that carry and store quantum information.
2.  A sequence of quantum gates that manipulate the state of the qubits.
3.  A set of measurements to extract classical information from the final state of the qubits.

By orchestrating these components, a quantum circuit can perform computations that harness the principles of superposition and entanglement, enabling it to solve certain problems that are intractable for even the most powerful classical supercomputers.

## Core Components and Structure

A quantum circuit diagram is read from left to right, representing the temporal sequence of operations.

![Quantum Circuit Diagram](https://upload.wikimedia.org/wikipedia/commons/thumb/c/c9/Quantum_circuit_for_Bell_state.svg/400px-Quantum_circuit_for_Bell_state.svg.png)
*A simple quantum circuit that creates an entangled Bell state.*

### 1. Qubits and Wires

-   **Qubits**: The fundamental unit of quantum information. A qubit's state can be a superposition of two basis states, $|0\rangle$ and $|1\rangle$.
-   **Wires**: In a circuit diagram, each qubit is represented by a horizontal line, or "wire." The state of the qubit evolves as it passes through the gates arranged along its wire. A set of parallel wires represents a **quantum register**. By convention, the top wire is often the most significant qubit.

### 2. Quantum Gates

-   **Definition**: A **quantum gate** is an operation that acts on one or more qubits. Mathematically, every quantum gate corresponds to a **unitary transformation**.
-   **Unitary Property**: A matrix $U$ is unitary if its conjugate transpose $U^\dagger$ is also its inverse, i.e., $U^\dagger U = UU^\dagger = I$. This property is essential because it ensures that the evolution is reversible and preserves the normalization of the quantum state (i.e., the sum of probabilities remains 1).
-   **Representation**: Gates are represented by blocks or symbols placed on the qubit wires.

### 3. Measurement

-   **Purpose**: Measurement is the process of extracting classical information from a quantum system. It is an irreversible operation that bridges the quantum and classical worlds.
-   **Representation**: It is typically denoted by a meter symbol at the end of a qubit wire.
-   **State Collapse**: When a qubit in a superposition state $|\psi\rangle = \alpha|0\rangle + \beta|1\rangle$ is measured in the computational basis, its state collapses to either $|0\rangle$ with probability $|\alpha|^2$ or $|1\rangle$ with probability $|\beta|^2$. The outcome is probabilistic, governed by the **Born rule**.

## Common Quantum Gates

Quantum gates are the building blocks of quantum algorithms. They can be categorized by the number of qubits they act upon.

### Single-Qubit Gates

These gates act on a single qubit and are represented by $2 \times 2$ unitary matrices.

-   **Pauli-X Gate (NOT Gate)**: Flips the state of a qubit. $X|0\rangle = |1\rangle$ and $X|1\rangle = |0\rangle$.
    $$
    X = \begin{pmatrix} 0 & 1 \\ 1 & 0 \end{pmatrix}
    $$
-   **Hadamard Gate (H)**: Creates an equal superposition of $|0\rangle$ and $|1\rangle$. It is one of the most important gates in quantum computing.
    $$
    H = \frac{1}{\sqrt{2}}\begin{pmatrix} 1 & 1 \\ 1 & -1 \end{pmatrix}
    $$
-   **Pauli-Z Gate**: Applies a phase flip to the $|1\rangle$ state. $Z|0\rangle = |0\rangle$ and $Z|1\rangle = -|1\rangle$.
    $$
    Z = \begin{pmatrix} 1 & 0 \\ 0 & -1 \end{pmatrix}
    $$

### Multi-Qubit Gates

These gates act on two or more qubits and are essential for creating entanglement.

-   **Controlled-NOT Gate (CNOT)**: This is a two-qubit gate. It flips the state of the **target qubit** if and only if the **control qubit** is in the state $|1\rangle$. It is fundamental for creating entanglement.
    $$
    \text{CNOT} = \begin{pmatrix} 1 & 0 & 0 & 0 \\ 0 & 1 & 0 & 0 \\ 0 & 0 & 0 & 1 \\ 0 & 0 & 1 & 0 \end{pmatrix}
    $$
-   **Toffoli Gate (CCNOT)**: A three-qubit gate that is a "controlled-controlled-NOT." It flips the target qubit if and only if both control qubits are in the state $|1\rangle$. It is universal for classical reversible computation.

## Example Circuit: Creating a Bell State

The circuit shown in the introduction is a canonical example of how to generate an entangled state, specifically the Bell state $|\Phi^+\rangle$. Let's trace the evolution of the two-qubit system, starting from the initial state $|00\rangle$.

1.  **Initial State**: The system starts with both qubits in the state $|0\rangle$.
    $$
    |\psi_0\rangle = |0\rangle \otimes |0\rangle = |00\rangle
    $$

2.  **Apply Hadamard Gate to Qubit 1**: The H-gate is applied to the first qubit, putting it into a superposition.
    $$
    |\psi_1\rangle = (H \otimes I)|\psi_0\rangle = \left(\frac{1}{\sqrt{2}}(|0\rangle + |1\rangle)\right) \otimes |0\rangle = \frac{1}{\sqrt{2}}(|00\rangle + |10\rangle)
    $$

3.  **Apply CNOT Gate**: The CNOT gate is applied with qubit 1 as the control and qubit 2 as the target. It acts on the state $|\psi_1\rangle$.
    -   The $|00\rangle$ component is unchanged because the control qubit is $|0\rangle$.
    -   The $|10\rangle$ component becomes $|11\rangle$ because the control qubit is $|1\rangle$, flipping the target.
    $$
    |\psi_2\rangle = \text{CNOT}|\psi_1\rangle = \frac{1}{\sqrt{2}}(\text{CNOT}|00\rangle + \text{CNOT}|10\rangle) = \frac{1}{\sqrt{2}}(|00\rangle + |11\rangle)
    $$
The final state is the maximally entangled Bell state $|\Phi^+\rangle$.

## Universality

Just as classical circuits can be built from a small set of universal gates (like NAND), quantum circuits have universal gate sets. A set of gates is **universal for quantum computation** if any unitary operation on any number of qubits can be approximated to arbitrary accuracy by a quantum circuit consisting only of gates from that set.

> A common universal gate set is the set of all single-qubit gates combined with the two-qubit CNOT gate. It has been proven that an even smaller discrete set, such as **{Hadamard, S, T, CNOT}**, is also universal.

The existence of universal gate sets is profoundly important, as it implies that a quantum computer capable of implementing just a few types of gates can, in principle, execute any quantum algorithm.

## Conclusion

The quantum circuit model provides a clear, structured, and powerful language for quantum computation. It allows us to translate abstract quantum algorithms into a concrete sequence of physical operations on qubits. By composing single-qubit gates to manipulate superposition and multi-qubit gates to generate entanglement, quantum circuits form the blueprint for harnessing the unique capabilities of quantum mechanics to solve complex problems. As such, they are the central paradigm in the design of quantum software and the physical implementation of quantum computers.
