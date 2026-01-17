---
{"dg-publish":true,"permalink":"/notes/2026/01/02/fundamentals-of-quantum-computing/"}
---

This post summarizes the core concepts of quantum computing, starting from classical reversible gates and moving through the fundamental postulates of quantum states and dynamics.

## 1. Classical Gates and Reversible Computing

### 1.1 Universality

A set of gates is called **universal** if it can compute any function $f: \{0,1\}^n \rightarrow \{0,1\}$.

- Examples of universal sets include $\{\text{AND}, \text{OR}, \text{NOT}\}, \{\text{AND}, \text{NOT}\}$, and the single gate $\{\text{NAND}\}$.

![image-5.png](/img/user/Assets/Images/image-5.png)

### 1.2 The Need for Reversibility

Standard classical gates like AND are not reversible because you cannot uniquely determine the inputs $x, y$ from the output $x \cdot y$. In quantum computing, evolution must be ***reversible***.

![image-4.png](/img/user/Assets/Images/image-4.png)

- *The Unitary Nature of Quantum Mechanics*: The time evolution of any closed quantum system is described by a **Unitary Operator** ($U$). In linear algebra, a matrix $U$ is unitary: $UU^\dagger = I$.
	- Because $U$ has an inverse ($U^\dagger$), you can always "undo" the operation.
	- The evolution $U$ is derived from the **Schrödinger Equation**. When the Hamiltonian ($H$) of a system is time-independent, the evolution is expressed as $e^{-iHt/\hbar}$, which is inherently a unitary (and thus reversible) operator.
	- Unitary transformations preserve the $L_2$-norm (the total probability) of the quantum state, ensuring it remains exactly 1 throughout the evolution.
- *Information Conservation*:  In classical computing, operations like **AND** are irreversible because they discard information.
	- **No Information Loss**: In a quantum system, information cannot be "deleted" or "lost" into thin air; it must be preserved within the system's state.
	- **The Toffoli Gate Example**: To perform classical-style logic (like AND) in a quantum way, we use reversible gates like the **Toffoli gate** (Controlled-Controlled-NOT) which is also universal. This gate uses an **Ancilla bit** to store the result while keeping the original inputs intact, allowing the entire process to be reversed.
	- Whenever we can compute $f(x)$ efficiently in polynomial time, we can efficiently compute the reversible mapping $(x, 0, 0) \mapsto (x, f(x), 0)$.

![image-6.png](/img/user/Assets/Images/image-6.png)

- *Physical Heat and Landauer's Principle*: the physical reason for pursuing reversibility is often related to energy.
	- **Heat Generation**: Landauer's Principle states that erasing 1 bit of information releases a specific amount of heat into the environment.
	- **Energy Efficiency**: Because quantum evolution is unitary (reversible), it theoretically does not require the erasure of information, which is a key requirement for building hardware that avoids the massive heat dissipation seen in classical high-performance chips.

## 2. Postulates of Quantum Computing: States

### 2.1 The Qubit

A qubit is represented by a complex vector in a two-dimensional Hilbert space:

$$|\psi\rangle = \begin{pmatrix} \alpha \\ \beta \end{pmatrix} = \alpha|0\rangle + \beta|1\rangle$$

where $\alpha, \beta \in \mathbb{C}$ are amplitudes satisfying the normalization condition $|\alpha|^2 + |\beta|^2 = 1$.

- **Computational Basis:** The vectors $|0\rangle = \binom{1}{0}$ and $|1\rangle = \binom{0}{1}$ form the standard basis for a qubit.
- **Dirac Notation:** 
	- **Ket** $|\psi\rangle$: A column vector.
	- **Bra** $\langle \psi |$: The conjugate transpose (dual vector) of a ket, represented as a row vector.
	- **Inner Product:** $\langle \psi |\phi \rangle = a_0^* b_0 + a_1^* b_1$.
	- **Outer Product:** $|0\rangle\langle 0| + |1\rangle\langle 1|= I$ (the Identity matrix).

### 2.2 The Bloch Sphere

Any single-qubit state can be visualized as a point on the **Bloch Sphere** using the following parameters:

$$|\psi\rangle = \cos\frac{\theta}{2}|0\rangle + e^{i\phi}\sin\frac{\theta}{2}|1\rangle$$

where $\theta$ and $\phi$ are real numbers defining the point's coordinates.

![image-3.png](/img/user/Assets/Images/image-3.png)

## 3. Quantum Dynamics

The time evolution of a closed quantum system is described by a **Unitary Transformation**.

- A matrix $U$ is unitary if $UU^\dagger = U^\dagger U = I$.
- This ensures that the state remains normalized: $\langle \psi | U^\dagger U | \psi \rangle = \langle \psi | \psi \rangle = 1$.

#### Common Single-Qubit Gates

- **Pauli Gates:** $X = \begin{pmatrix} 0 & 1 \\ 1 & 0 \end{pmatrix}$, $Y = \begin{pmatrix} 0 & -i \\ i & 0 \end{pmatrix}$, $Z = \begin{pmatrix} 1 & 0 \\ 0 & -1 \end{pmatrix}$.
    
- **Hadamard (H):** $H = \frac{1}{\sqrt{2}}\begin{pmatrix} 1 & 1 \\ 1 & -1 \end{pmatrix}$.
    
- **Phase Gates:** $S = \begin{pmatrix} 1 & 0 \\ 0 & i \end{pmatrix}$ (Note: Corrected from notes) and $T = \begin{pmatrix} 1 & 0 \\ 0 & e^{i\pi/4} \end{pmatrix}$.

## 4. Composite Systems and Entanglement

### 4.1 Tensor Products

The state space of a composite system is the **tensor product** of its individual component spaces. For example, if we have two qubits in states $|\psi\rangle$ and $|\phi\rangle$, the combined state is $|\psi\rangle \otimes |\phi\rangle$ (often written as $|\psi\phi\rangle$).

### 4.2 Quantum Entanglement

- **Product States:** States that can be written in the form $|\psi\rangle \otimes |\phi\rangle$.
- **Entangled States:** States that _cannot_ be decomposed into a product of individual qubit states.
    - **Example:** The state $\frac{1}{\sqrt{2}}(|00\rangle + |11\rangle)$ is entangled. Proof: Setting $\alpha_0\beta_1 = \alpha_1\beta_0 = 0$ while $\alpha_0\beta_0 = \alpha_1\beta_1 = \frac{1}{\sqrt{2}}$ leads to a contradiction.

## Practical Implementation

```
from qiskit import QuantumCircuit
from qiskit.quantum_info import Statevector

# 1. Create a Bell State (Entangled State)
qc = QuantumCircuit(2)
qc.h(0)     # Apply Hadamard to the first qubit
qc.cx(0, 1) # Apply CNOT (controlled by q0, targeting q1)

# View the statevector
state = Statevector.from_instruction(qc)
print("Bell State Vector:")
print(state.data)

# 2. Apply a gate to a subsystem: (I ⊗ X) acting on the Bell state
qc.x(1) 
final_state = Statevector.from_instruction(qc)
print("\nState after (I ⊗ X):")
print(final_state.data)
```
