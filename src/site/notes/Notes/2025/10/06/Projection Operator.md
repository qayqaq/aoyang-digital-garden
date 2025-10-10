---
{"dg-publish":true,"permalink":"/notes/2025/10/06/projection-operator/"}
---

#LinearAlgebra #QuantumMechanics #Mathematics

[[Projection Operator.canvas\|Projection Operator.canvas]]

# Projection Operator

## Introduction

In linear algebra and functional analysis, a **projection operator** (or simply a **projection**) is a linear transformation that maps a vector space onto a subspace of itself. Geometrically, it takes a vector and finds its "shadow" or component within a specified subspace. The defining characteristic of a projection is that if it is applied twice to a vector, the result is the same as applying it once.

Projection operators are fundamental tools in mathematics and physics. In quantum mechanics, they play a central role in the theory of measurement, providing the mathematical foundation for describing how a quantum state collapses to a specific outcome upon observation.

## Mathematical Definition and Properties

A linear operator $P$ acting on a vector space is defined as a **projection operator** if it is **idempotent**, meaning it is equal to its own square:

$$
P^2 = P
$$

This property captures the geometric intuition: once a vector has been projected into a subspace, projecting it again will not change it.

In the context of Hilbert spaces, which are central to quantum mechanics, we are typically concerned with **orthogonal projections**. An orthogonal projection operator must satisfy an additional condition: it must be **Hermitian** (or self-adjoint).

$$
P = P^\dagger
$$

where $P^\dagger$ is the conjugate transpose of $P$.

Therefore, an orthogonal projection operator is a linear operator that is both **idempotent and Hermitian**.

### Key Properties

1.  **Eigenvalues**: The eigenvalues of a projection operator can only be **0 or 1**.
    *   *Proof*: Let $|\psi\rangle$ be an eigenvector of $P$ with eigenvalue $\lambda$, so $P|\psi\rangle = \lambda|\psi\rangle$. Applying $P$ again gives $P^2|\psi\rangle = P(\lambda|\psi\rangle) = \lambda(P|\psi\rangle) = \lambda^2|\psi\rangle$. Since $P^2=P$, we have $\lambda|\psi\rangle = \lambda^2|\psi\rangle$, which implies $\lambda(\lambda-1)=0$. Thus, $\lambda=0$ or $\lambda=1$.

2.  **Complementary Projections**: If $P$ is a projection operator, then the operator $Q = I - P$ (where $I$ is the identity operator) is also a projection operator.
    *   $Q$ projects onto the subspace that is the orthogonal complement of the subspace projected onto by $P$.
    *   $P$ and $Q$ are mutually orthogonal, meaning $PQ = QP = 0$.

## Geometric Interpretation

The action of a projection operator has a clear geometric meaning. Let $V$ be a vector space and $W$ be a subspace of $V$. The orthogonal projection operator $P_W$ onto $W$ decomposes any vector $|\psi\rangle \in V$ into two orthogonal components:

$$
|\psi\rangle = P_W|\psi\rangle + (I - P_W)|\psi\rangle
$$

-   The first component, $|\psi_\parallel\rangle = P_W|\psi\rangle$, is the projection of $|\psi\rangle$ onto the subspace $W$. It lies entirely within $W$.
-   The second component, $|\psi_\perp\rangle = (I - P_W)|\psi\rangle$, is the projection of $|\psi\rangle$ onto the orthogonal complement of $W$. It is orthogonal to every vector in $W$.

![Projection of a vector](https://upload.wikimedia.org/wikipedia/commons/thumb/1/18/Vector_projection.svg/500px-Vector_projection.svg.png)
*Geometric visualization of projecting a vector **a** onto the line spanned by vector **b**.*

## Construction of Projection Operators

Projection operators can be constructed directly from the basis vectors of the subspace of interest.

### Projection onto a 1D Subspace

The simplest projection is onto a one-dimensional subspace, or a line, spanned by a single normalized vector $|u\rangle$ (where $\langle u|u\rangle = 1$). The projection operator is given by the outer product:

$$
P_u = |u\rangle\langle u|
$$

When this operator acts on an arbitrary vector $|\psi\rangle$, it yields $P_u|\psi\rangle = |u\rangle\langle u|\psi\rangle$. The term $\langle u|\psi\rangle$ is a scalar representing the component of $|\psi\rangle$ along the direction of $|u\rangle$.

### Projection onto a General Subspace

If a subspace $W$ is spanned by a set of orthonormal basis vectors $\{|u_1\rangle, |u_2\rangle, \dots, |u_k\rangle\}$, the projection operator onto $W$ is the sum of the individual projection operators for each basis vector:

$$
P_W = \sum_{i=1}^{k} |u_i\rangle\langle u_i|
$$

### The Completeness Relation

If the orthonormal basis $\{|u_i\rangle\}$ spans the entire vector space (i.e., it is a complete basis), then projecting onto the space spanned by this basis is equivalent to doing nothing. In this case, the sum of the projectors is the **identity operator**, a result known as the **completeness relation** or **resolution of identity**:

$$
\sum_{i=1}^{n} |u_i\rangle\langle u_i| = I
$$

## Role in Quantum Mechanics

Projection operators are indispensable in the formulation of quantum mechanics, particularly in the context of measurement.

### The Measurement Postulate

The postulates of quantum measurement are expressed using projection operators. For an observable represented by a Hermitian operator $A$, its spectral decomposition is:

$$
A = \sum_n a_n P_n
$$

where $a_n$ are the distinct eigenvalues (possible measurement outcomes) of $A$, and $P_n$ is the projection operator onto the eigenspace corresponding to the eigenvalue $a_n$.

1.  **Probability of Measurement**: The probability of measuring the value $a_n$ for a system in the state $|\psi\rangle$ is given by the expectation value of the corresponding projection operator:
    $$
    \text{Prob}(a_n) = \langle\psi|P_n|\psi\rangle = ||P_n|\psi\rangle||^2
    $$

2.  **State Collapse (Projection Postulate)**: If the measurement of $A$ yields the result $a_n$, the quantum state of the system instantaneously collapses from $|\psi\rangle$ to a new state $|\psi'\rangle$, which is the normalized projection of the original state onto the eigenspace of $a_n$:
    $$
    |\psi'\rangle = \frac{P_n|\psi\rangle}{\sqrt{\text{Prob}(a_n)}} = \frac{P_n|\psi\rangle}{||P_n|\psi\rangle||}
    $$

> **Example**: The density matrix for a pure state, $\rho = |\psi\rangle\langle\psi|$, is a projection operator onto the one-dimensional subspace spanned by $|\psi\rangle$.

## Conclusion

The projection operator is a simple yet powerful mathematical concept. Defined by the property of idempotence ($P^2=P$), it provides a rigorous way to describe the geometric act of projecting a vector onto a subspace. In quantum mechanics, its role is elevated to a cornerstone of the theory. Orthogonal projections form the language of the measurement postulates, defining both the probabilities of experimental outcomes and the process of state collapse. They provide the crucial link between the abstract Hilbert space formalism and the concrete, observable phenomena of the quantum world.

