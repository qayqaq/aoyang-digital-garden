---
{"dg-publish":true,"permalink":"/notes/2026/01/02/measurement-protocols-circuits/"}
---

## 1. Quantum Measurement

Quantum measurement is the process of extracting classical information from a quantum state.

### 1.1 Orthonormal Basis

An orthonormal basis is a set of vectors $\{|\varphi_i\rangle\}$ such that their inner product satisfies:

$$\langle \varphi_i |\varphi_j \rangle = \delta_{ij} = \begin{cases} 1 & i=j \\ 0 & i \ne j \end{cases}$$

**Examples for a 1-qubit system:**

- **Computational Basis:** $\{|0\rangle, |1\rangle\}$
- **Hadamard Basis:** $\{|+\rangle, |-\rangle\}$, where:
    - $|+\rangle = \frac{1}{\sqrt{2}}(|0\rangle + |1\rangle)$
    - $|-\rangle = \frac{1}{\sqrt{2}}(|0\rangle - |1\rangle)$

For a 2-qubit system, the basis expands to $\{|00\rangle, |01\rangle, |10\rangle, |11\rangle\}$.

### 1.2 Measurement Postulates

Let $B=\{|\varphi_i\rangle\}$ be an orthonormal basis. If a system is in state $|\psi\rangle = \sum_i a_i |\varphi_i\rangle$:

1. The output "$i$" occurs with probability $Pr(i) = |a_i|^2$.
2. The measurement collapses the system into the state $|\varphi_i\rangle$.

**Important Note:** The global phase does not matter, as $|a_i|^2 = |e^{i\theta} a_i|^2$.

**Example:** Measuring $|\psi\rangle = \frac{1}{2}|0\rangle + \frac{\sqrt{3}}{2}|1\rangle$ in the $\{|+\rangle, |-\rangle\}$ basis:

- $\langle + | \psi \rangle = \frac{1+\sqrt{3}}{2\sqrt{2}}$, so $Pr(+) = |\langle + | \psi \rangle|^2 = \frac{2+\sqrt{3}}{4}$.
- $\langle - | \psi \rangle = \frac{1-\sqrt{3}}{2\sqrt{2}}$, so $Pr(-) = \frac{2-\sqrt{3}}{4}$.

### 1.3 Partial Measurement

When measuring only the first qubit of a multi-qubit system:

Given $|\psi\rangle = \sqrt{\frac{1}{10}}|00\rangle + \sqrt{\frac{2}{10}}|01\rangle + \sqrt{\frac{3}{10}}|10\rangle + \sqrt{\frac{4}{10}}|11\rangle$:

- Grouping by the first qubit: $|\psi\rangle = \sqrt{\frac{3}{10}}|0\rangle \otimes (\sqrt{\frac{1}{3}}|0\rangle + \sqrt{\frac{2}{3}}|1\rangle) + \sqrt{\frac{7}{10}}|1\rangle \otimes (\sqrt{\frac{3}{7}}|0\rangle + \sqrt{\frac{4}{7}}|1\rangle)$.
- $Pr(0) = \frac{3}{10}$; State becomes $|0\rangle \otimes (\sqrt{\frac{1}{3}}|0\rangle + \sqrt{\frac{2}{3}}|1\rangle)$.
- $Pr(1) = \frac{7}{10}$; State becomes $|1\rangle \otimes (\sqrt{\frac{3}{7}}|0\rangle + \sqrt{\frac{4}{7}}|1\rangle)$.

## 2. Superdense Coding

Superdense coding allows Alice to send **two classical bits** to Bob by sending only **one qubit**, provided they share an entangled pair (ebit).

**The Procedure:**
1. **Initial State:** Alice and Bob share $|\beta_{00}\rangle = \frac{1}{\sqrt{2}}(|00\rangle + |11\rangle)$.
2. **Alice's Operation:** Depending on the bits $(xy)$ she wants to send, Alice applies a gate to her qubit:
    - `00`: Apply $I \rightarrow |\beta_{00}\rangle = \frac{1}{\sqrt{2}}(|00\rangle + |11\rangle)$.
    - `01`: Apply $X \rightarrow |\beta_{01}\rangle = \frac{1}{\sqrt{2}}(|10\rangle + |01\rangle)$.
    - `10`: Apply $Z \rightarrow |\beta_{10}\rangle = \frac{1}{\sqrt{2}}(|00\rangle - |11\rangle)$.
    - `11`: Apply $iY$ (or $ZX$) $\rightarrow |\beta_{11}\rangle = \frac{1}{\sqrt{2}}(|01\rangle - |10\rangle)$.
3. **Transmission:** Alice sends her qubit to Bob.
4. **Decoding:** Bob measures both qubits in the **Bell basis** to retrieve $xy$.

## 3. Quantum Teleportation

Teleportation is the reverse: moving a quantum state $|\psi\rangle$ using **two classical bits** and **one ebit**.

**The Procedure:**
1. **Setup:** Alice has a qubit in state $|\psi\rangle = a_0|0\rangle + a_1|1\rangle$ and shares $|\beta_{00}\rangle$ with Bob.
2. **Alice's Measurement:** Alice performs a Bell measurement on her two qubits (the unknown state and her half of the ebit).
3. **The State Shift:** The total state can be rewritten such that Bob’s qubit is in one of four states: $|\psi\rangle$, $X|\psi\rangle$, $Z|\psi\rangle$, or $XZ|\psi\rangle$, depending on Alice's outcome.
4. **Correction:** Alice sends her classical outcomes (2 bits) to Bob. Bob applies the corresponding Pauli gates ($Z^a X^b$) to recover exactly $|\psi\rangle$.

## 4. Quantum Circuits and the Bloch Sphere

### 4.1 The Bloch Sphere

Any single-qubit state can be represented as a point on the Bloch Sphere:

$$|\psi\rangle = \cos\frac{\theta}{2}|0\rangle + e^{i\phi}\sin\frac{\theta}{2}|1\rangle $$
### 4.2 Single-Qubit Rotation Gates

Gates rotate the state vector around axes on the Bloch Sphere:

- $R_x(\theta) = e^{-i\theta X/2} = \begin{pmatrix} \cos\frac{\theta}{2} & -i\sin\frac{\theta}{2} \\ -i\sin\frac{\theta}{2} & \cos\frac{\theta}{2} \end{pmatrix}$
    
- $R_y(\theta) = \begin{pmatrix} \cos\frac{\theta}{2} & -\sin\frac{\theta}{2} \\ \sin\frac{\theta}{2} & \cos\frac{\theta}{2} \end{pmatrix}$
    
- $R_z(\theta) = \begin{pmatrix} e^{-i\theta/2} & 0 \\ 0 & e^{i\theta/2} \end{pmatrix}$

### 4.3 Multi-Qubit Gates

- **CNOT Gate:** Flips the target qubit if the control qubit is $|1\rangle$.
    - $|0\rangle|\psi\rangle \rightarrow |0\rangle|\psi\rangle$
    - $|1\rangle|\psi\rangle \rightarrow |1\rangle X|\psi\rangle$
- **Creating Entanglement:** A Hadamard gate (H) followed by a CNOT gate converts $|00\rangle$ into the Bell state $|\beta_{00}\rangle$.

