---
{"dg-publish":true,"permalink":"/notes/2025/10/06/stabilizer-code/"}
---

#quantum-computing #error-correction #quantum-information

[[Stabilizer Code.canvas\|Stabilizer Code.canvas]]

# Stabilizer Codes

## 1. Introduction

**Stabilizer codes** represent a powerful and systematic framework for constructing and understanding the majority of **quantum error correction (QEC)** codes. This formalism, rooted in group theory, provides an elegant algebraic structure that simplifies the design and analysis of codes capable of protecting quantum information from noise.

The central idea of the stabilizer formalism is to define the protected quantum state space (the **code space**) not by explicitly writing out its basis vectors, but by ***describing it implicitly as the common +1 eigenspace of a set of commuting operators***. These operators form a mathematical structure called the **stabilizer group**. Many of the most important QEC codes, including the [[Notes/2025/10/06/Shor Code\|Shor Code]] and the [[Notes/2025/10/06/Surface Code\|Surface Code]], are instances of stabilizer codes.

## 2. The Pauli Group: The Building Blocks

The foundation of stabilizer codes is the **$n$-qubit Pauli group**, $\mathcal{P}_n$. This group consists of all possible $n$-fold tensor products of the single-qubit Pauli matrices, along with multiplicative factors of $\{\pm 1, \pm i\}$.

- **Single-Qubit Pauli Matrices**:
    $$
    I = \begin{pmatrix} 1 & 0 \\ 0 & 1 \end{pmatrix}, \quad X = \begin{pmatrix} 0 & 1 \\ 1 & 0 \end{pmatrix}, \quad Y = \begin{pmatrix} 0 & -i \\ i & 0 \end{pmatrix}, \quad Z = \begin{pmatrix} 1 & 0 \\ 0 & -1 \end{pmatrix}
    $$
- **$n$-Qubit Pauli Operators**: An element of $\mathcal{P}_n$ is of the form $P = c \cdot P_1 \otimes P_2 \otimes \dots \otimes P_n$, where $c \in \{\pm 1, \pm i\}$ and each $P_i \in \{I, X, Y, Z\}$. For example, $X \otimes I \otimes Z$ (often written as $X_1Z_3$) is an element of $\mathcal{P}_3$.

A crucial property of Pauli operators is that any two of them either **commute** ($AB = BA$) or **anti-commute** ($AB = -BA$). This binary relationship is the key to error detection.

## 3. Defining the Code Space

A stabilizer code is defined by choosing a specific subgroup of the Pauli group.

### 3.1. The Stabilizer Group

The **stabilizer group**, denoted $S$, is an Abelian (mutually commuting) subgroup of the $n$-qubit Pauli group $\mathcal{P}_n$ that does not contain $-I$.

> **Definition**: A quantum state $|\psi\rangle$ is said to be **stabilized** by an operator $S_i$ if it is an eigenvector of $S_i$ with an eigenvalue of +1.
> $$
 S_i |\psi\rangle = |\psi\rangle
 $$

### 3.2. The Code Space

The **code space**, $V_S$, is the subspace of the full $n$-qubit Hilbert space containing all states that are simultaneously stabilized by every operator in the stabilizer group $S$.

In practice, we do not need to list every operator in $S$. Instead, we can define the group using a smaller set of **independent generators**, $\{S_1, S_2, \dots, S_{n-k}\}$. Any element in $S$ can be formed by taking products of these generators.

If we use $n-k$ independent generators to stabilize an $n$-qubit system, the resulting code space has a dimension of $2^k$. This means the ***code uses $n$ physical qubits to encode $k$ logical qubits***. Such a code is referred to as an $[[n, k, d\|n, k, d]]$ code, where $d$ is the code distance.

## 4. Error Detection and Syndrome Measurement

The stabilizer formalism provides a direct mechanism for detecting errors. Let $|\psi\rangle$ be a state in the code space, such that $S_i|\psi\rangle = |\psi\rangle$ for all generators $S_i$. Now, suppose an error $E \in \mathcal{P}_n$ occurs, transforming the state to $E|\psi\rangle$.

To detect the error, we measure the eigenvalues of the stabilizer generators.
1. **If $E$ commutes with $S_i$**: The measurement outcome for $S_i$ is unchanged.
    $$
    S_i(E|\psi\rangle) = E S_i |\psi\rangle = E|\psi\rangle \quad (\text{Eigenvalue is +1})
    $$
2. **If $E$ anti-commutes with $S_i$**: The measurement outcome for $S_i$ flips.
    $$
    S_i(E|\psi\rangle) = -E S_i |\psi\rangle = -E|\psi\rangle \quad (\text{Eigenvalue is -1})
    $$

The set of measurement outcomes for all generators forms the **error syndrome**, which is a classical bit string (e.g., '0' for +1, '1' for -1). Each correctable error corresponds to a unique syndrome, allowing us to diagnose the error and apply a corrective operation. Crucially, this measurement reveals information about the error, not the encoded logical state, thus preserving the quantum information.

## 5. Logical Operators and Code Distance

While the stabilizer generators act trivially on the code space (leaving states unchanged), **logical operators** are operators that transform one valid codeword into another.

- **Definition**: *A logical operator is an $n$-qubit Pauli operator that commutes with every element of the stabilizer group $S$ but is not itself an element of $S$.*
- **Function**: For a code encoding a single logical qubit ($k=1$), we can define a logical $X$ operator, $X_L$, and a logical $Z$ operator, $Z_L$. These operators behave like Pauli matrices on the encoded logical states.

An error $E$ is undetectable if it commutes with all stabilizers but is not a stabilizer itself. Such an error is a logical operator and will corrupt the encoded information. The **code distance, $d$**, is defined as the **weight** (*the number of non-identity terms*) of the lowest-weight non-trivial logical operator. A code with distance $d$ can correct any error affecting up to $t = \lfloor (d-1)/2 \rfloor$ qubits, but can detect $d-1$ qubits.

### Example: The Five-Qubit Code $[[5, 1, 3\|5, 1, 3]]$

This is the smallest code capable of correcting any arbitrary single-qubit error.
-   **$n=5$ physical qubits, $k=1$ logical qubit.**
-   **$n-k=4$ stabilizer generators**:
    -   $S_1 = X \otimes Z \otimes Z \otimes X \otimes I$
    -   $S_2 = I \otimes X \otimes Z \otimes Z \otimes X$
    -   $S_3 = X \otimes I \otimes X \otimes Z \otimes Z$
    -   $S_4 = Z \otimes X \otimes I \otimes X \otimes Z$
-   **Logical Operators**:
    -   $X_L = X \otimes X \otimes X \otimes X \otimes X$
    -   $Z_L = Z \otimes Z \otimes Z \otimes Z \otimes Z$
-   **Distance**: The lowest-weight logical operator has weight 5, but there are logical operators of weight 3 (e.g., $X_L S_1 = I \otimes Z \otimes Z \otimes I \otimes X$). Thus, $d=3$, and the code can correct $t = \lfloor (3-1)/2 \rfloor = 1$ arbitrary single-qubit error.

## 6. Conclusion

The stabilizer formalism is a cornerstone of modern quantum error correction. It provides a powerful and efficient mathematical language for designing, describing, and analyzing QEC codes. By defining a protected subspace through a set of commuting Pauli operators, it transforms the complex problem of quantum error correction into a more manageable algebraic task of measuring syndromes and identifying errors. This framework not only encompasses many of the most important known codes but also provides a clear recipe for discovering new ones, making it an indispensable tool in the quest for fault-tolerant quantum computation.

