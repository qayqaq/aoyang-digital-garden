---
{"dg-publish":true,"permalink":"/notes/2025/10/06/shor-code/"}
---

#quantum-computing #error-correction #quantum-codes

[[Shor Code.canvas\|Shor Code.canvas]]

# The Shor Code

## 1. Introduction

The **Shor code**, developed by Peter Shor in 1995, holds a landmark status in the field of quantum information science as the first practical example of a **quantum error correction (QEC)** code. Its primary significance lies in demonstrating that it is possible to protect a quantum state from arbitrary errors affecting a single qubit.

The code provides a method to encode one **logical qubit** (the unit of information we wish to protect) into a highly entangled state of nine **physical qubits** (the actual, error-prone hardware components). By distributing the information in this redundant manner, the Shor code can detect and correct for bit-flip errors, phase-flip errors, or any combination thereof on any one of its nine physical qubits. While not the most efficient code by modern standards, its conceptual framework laid the foundation for the entire field of fault-tolerant quantum computation.

## 2. The Core Principle: Concatenation

The elegance of the Shor code lies in its structure as a **concatenated code**. It does not solve the problem of arbitrary error correction in a single, complex step. Instead, it combines two simpler, specialized codes:

1. A **three-qubit bit-flip code** to handle errors analogous to classical bit flips ($X$ errors).
2. A **three-qubit phase-flip code** to handle uniquely quantum phase errors ($Z$ errors).

By applying these codes in sequence—one nested inside the other—the resulting nine-qubit code can correct for any arbitrary single-qubit error. This is because any such error can be expressed as a linear combination of the identity ($I$), bit-flip ($X$), phase-flip ($Z$), and combined bit-and-phase-flip ($Y$) operations.

## 3. Component 1: The Three-Qubit Bit-Flip Code

This code protects a quantum state against an $X$ error, which swaps the amplitudes of the $|0\rangle$ and $|1\rangle$ states.

#### Encoding

The encoding is a direct quantum analogue of the classical three-bit repetition code. A single logical qubit state $|\psi\rangle_L = \alpha|0\rangle + \beta|1\rangle$ is encoded into a three-qubit entangled state:

$$
|0\rangle_L = |000\rangle
$$
$$
|1\rangle_L = |111\rangle
$$

Therefore, the general encoded state is:
$$
|\psi\rangle_{L} = \alpha|000\rangle + \beta|111\rangle
$$

#### Error Detection and Correction

Suppose a bit-flip error $X_1$ occurs on the first qubit. The state becomes:
$$
X_1|\psi\rangle_{L} = \alpha|100\rangle + \beta|011\rangle
$$
To detect this error without measuring (and thus collapsing) the logical state, we measure the **parity** between adjacent qubits. This is done using ancillary qubits to measure the eigenvalues of the stabilizer operators $Z_1Z_2$ and $Z_2Z_3$.

-   **No Error**: In the state $\alpha|000\rangle + \beta|111\rangle$, the parities are even (000, 111). The syndrome is (0, 0).
-   **$X_1$ Error**: In the state $\alpha|100\rangle + \beta|011\rangle$, the parity of the first two qubits is odd, while the second and third are even. The syndrome is (1, 0), indicating an error on the first qubit.
-   **$X_2$ Error**: The syndrome would be (1, 1).
-   **$X_3$ Error**: The syndrome would be (0, 1).

Once the location of the error is identified via the syndrome, a corrective $X$ gate is applied to that specific qubit, restoring the original encoded state.

## 4. Component 2: The Three-Qubit Phase-Flip Code

This code protects against a $Z$ error, which introduces a relative phase shift: $\alpha|0\rangle + \beta|1\rangle \rightarrow \alpha|0\rangle - \beta|1\rangle$.

#### Encoding

A phase-flip error in the computational basis ($\{|0\rangle, |1\rangle\}$) is equivalent to a bit-flip error in the Hadamard basis ($\{|+\rangle, |-\rangle\}$), where:
$$
|+\rangle = \frac{1}{\sqrt{2}}(|0\rangle + |1\rangle) \quad \text{and} \quad |-\rangle = \frac{1}{\sqrt{2}}(|0\rangle - |1\rangle)
$$
The code leverages this duality. The logical states are encoded using the Hadamard basis states in a repetition code:
$$
|0\rangle_L \rightarrow |+++\rangle = \frac{1}{2\sqrt{2}}(|0\rangle+|1\rangle)(|0\rangle+|1\rangle)(|0\rangle+|1\rangle)
$$
$$
|1\rangle_L \rightarrow |---\rangle = \frac{1}{2\sqrt{2}}(|0\rangle-|1\rangle)(|0\rangle-|1\rangle)(|0\rangle-|1\rangle)
$$

#### Error Detection and Correction

A $Z$ error on one of the physical qubits flips the sign of that qubit's state in the Hadamard basis (e.g., $Z_1|+++\rangle = |-++\rangle$). This is detected by measuring stabilizers like $X_1X_2$ and $X_2X_3$. The resulting syndrome identifies which qubit experienced the phase-flip, and a corrective $Z$ gate is applied.

## 5. Concatenation: Constructing the Nine-Qubit Shor Code

The Shor code is constructed by nesting these two codes.

1.  **Outer Code (Phase-Flip Protection)**: First, we encode the logical qubit using the three-qubit phase-flip code.
    $$
    |\psi\rangle = \alpha|0\rangle + \beta|1\rangle \quad \rightarrow \quad \alpha|+++\rangle + \beta|---\rangle
    $$
2.  **Inner Code (Bit-Flip Protection)**: Next, each of the three qubits in the state above is individually encoded using the three-qubit bit-flip code. We replace:
    -   $|+\rangle$ with $\frac{1}{\sqrt{2}}(|000\rangle + |111\rangle)$
    -   $|-\rangle$ with $\frac{1}{\sqrt{2}}(|000\rangle - |111\rangle)$

This two-step process yields the final nine-qubit encoded states:
$$
|0\rangle_L \rightarrow \left[\frac{1}{\sqrt{2}}(|000\rangle+|111\rangle)\right] \otimes \left[\frac{1}{\sqrt{2}}(|000\rangle+|111\rangle)\right] \otimes \left[\frac{1}{\sqrt{2}}(|000\rangle+|111\rangle)\right]
$$
$$
|1\rangle_L \rightarrow \left[\frac{1}{\sqrt{2}}(|000\rangle-|111\rangle)\right] \otimes \left[\frac{1}{\sqrt{2}}(|000\rangle-|111\rangle)\right] \otimes \left[\frac{1}{\sqrt{2}}(|000\rangle-|111\rangle)\right]
$$

## 6. How the Shor Code Corrects Arbitrary Errors

The concatenated structure allows for a two-stage correction process that can handle any single-qubit error.

-   **Correcting Bit-Flips**: A bit-flip ($X$) on any of the nine physical qubits will be detected and corrected by the inner bit-flip code within one of the three blocks of three qubits. The syndrome measurement for bit-flips identifies which of the nine qubits was flipped.
-   **Correcting Phase-Flips**: A phase-flip ($Z$) on any physical qubit will introduce a phase error in one of the three blocks. This is detected by the outer phase-flip code. The syndrome measurement for phase-flips identifies which *block* of three qubits contains the error. A $Z$ gate can then be applied to that qubit to correct it.
-   **Correcting Y-Flips**: A $Y$ error is equivalent to $iXZ$. The code corrects the $X$ and $Z$ components independently, thereby correcting the full error.

## 7. Conclusion

The Shor code was a monumental theoretical achievement. It provided the first concrete proof that quantum systems could be shielded from the debilitating effects of noise, making the prospect of large-scale quantum computation a tangible possibility. Although its resource overhead (9 physical qubits for 1 logical qubit) makes it impractical for current hardware, its principles of concatenation and leveraging basis duality remain central concepts in the ongoing development of more advanced and efficient QEC codes, such as the [[Notes/2025/10/06/Surface Code\|Surface Code]]. The Shor code is, therefore, best understood not as a practical blueprint for today's quantum computers, but as the foundational pillar upon which the entire field of quantum fault tolerance was built.
