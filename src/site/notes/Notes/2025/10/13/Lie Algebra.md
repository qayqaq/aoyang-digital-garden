---
{"dg-publish":true,"permalink":"/notes/2025/10/13/lie-algebra/","tags":["#mathematics","#algebra","#LieTheory","#physics"]}
---

- A **Lie algebra** is a vector space equipped with a non-associative binary operation called the **Lie bracket**, which is anti-commutative and satisfies the Jacobi identity.
- It serves as the "infinitesimal" counterpart to a **Lie group**, describing the group's structure near its identity element.
- The most common example is the space of $n \times n$ matrices where the Lie bracket is the **commutator**: $[A, B] = AB - BA$.
- Lie algebras are fundamental tools in theoretical physics for describing symmetries (e.g., angular momentum in quantum mechanics, gauge symmetries in particle physics) and in differential geometry.

#mathematics #algebra #LieTheory #physics
[[Lie Algebra.canvas\|Lie Algebra.canvas]]
# Lie Algebra

## Introduction

A **Lie algebra** (pronounced /liː/ "lee") is a fundamental algebraic structure used to study continuous symmetries. While it is an object of study in its own right within abstract algebra, its primary significance comes from its intimate connection to **Lie groups**—smooth manifolds that are also groups. In essence, a Lie algebra captures the "infinitesimal" structure of a Lie group, much like a tangent plane approximates a smooth surface at a point. This connection allows complex problems in geometry and physics involving continuous transformations (like rotations or Lorentz transformations) to be analyzed using the more tractable tools of linear algebra.

## Formal Definition

A Lie algebra is a vector space $\mathfrak{g}$ over a field $F$ (typically $\mathbb{R}$ or $\mathbb{C}$), equipped with a binary operation called the **Lie bracket**,
$$
[\cdot, \cdot]: \mathfrak{g} \times \mathfrak{g} \to \mathfrak{g}
$$
which satisfies the following three axioms for all elements $X, Y, Z \in \mathfrak{g}$ and scalars $a, b \in F$:

1.  **Bilinearity**: The bracket is linear in each of its arguments.
    $$
    [aX + bY, Z] = a[X, Z] + b[Y, Z]
    $$
    $$
    [Z, aX + bY] = a[Z, X] + b[Z, Y]
    $$

2.  **Alternating Property (Anti-commutativity)**: The bracket of any element with itself is zero.
    $$
    [X, X] = 0
    $$
    > **Note:** This property implies anti-commutativity, $[X, Y] = -[Y, X]$. This can be seen by expanding $[X+Y, X+Y] = 0$ using bilinearity.

3.  **The Jacobi Identity**: This identity serves as a substitute for the associative law, which the Lie bracket generally does not satisfy.
    $$
    [X, [Y, Z]] + [Y, [Z, X]] + [Z, [X, Y]] = 0
    $$

## Key Examples

### 1. The Vector Cross Product in $\mathbb{R}^3$

The most intuitive example of a Lie algebra is the vector space $\mathbb{R}^3$ with the Lie bracket defined as the familiar **vector cross product**.
- **Vector Space**: $\mathfrak{g} = \mathbb{R}^3$
- **Lie Bracket**: $[u, v] = u \times v$

Let's verify the axioms:
- **Bilinearity**: The cross product is known to be bilinear.
- **Alternating**: For any vector $u \in \mathbb{R}^3$, $u \times u = 0$.
- **Jacobi Identity**: The cross product satisfies the vector identity $u \times (v \times w) + v \times (w \times u) + w \times (u \times v) = 0$.

This Lie algebra, denoted $\mathfrak{so}(3)$, corresponds to the Lie group $SO(3)$ of rotations in three dimensions.

### 2. The Commutator of Matrices

A vast and important class of Lie algebras is constructed from square matrices.
- **Vector Space**: The space of all $n \times n$ matrices with entries from a field $F$, denoted $\mathfrak{gl}(n, F)$.
- **Lie Bracket**: The **commutator** of two matrices $A$ and $B$.
  $$
  [A, B] = AB - BA
  $$
The commutator measures the degree to which matrix multiplication fails to be commutative. If $[A, B] = 0$, the matrices commute.

Verification of the axioms is straightforward:
- **Bilinearity**: Follows directly from the distributive property of matrix multiplication.
- **Alternating**: $[A, A] = AA - AA = 0$.
- **Jacobi Identity**: A direct calculation shows that $[A, [B, C]] + [B, [C, A]] + [C, [A, B]] = 0$.

This Lie algebra, $\mathfrak{gl}(n, F)$, is the Lie algebra of the **general linear group** $GL(n, F)$ of all invertible $n \times n$ matrices.

## The Connection to Lie Groups

The profound importance of Lie algebras stems from their role as the linear approximation of Lie groups.

- **Lie Group**: A **[[Notes/2025/10/13/Lie Group\|Lie group]]** $G$ is a smooth manifold that is also a group, such that the group operations (multiplication and inversion) are smooth maps. Examples include the rotation group $SO(n)$ and the special unitary group $SU(n)$.

- **Tangent Space**: The Lie algebra $\mathfrak{g}$ of a Lie group $G$ is defined as the **tangent space to the group at its identity element**, $T_eG$. The elements of the Lie algebra can be thought of as "infinitesimal generators" of transformations within the group.

- **The Exponential Map**: The primary bridge connecting a Lie algebra to its Lie group is the **exponential map**, $\exp: \mathfrak{g} \to G$. For matrix Lie groups, this corresponds to the standard matrix exponential:
  $$
  \exp(A) = I + A + \frac{A^2}{2!} + \frac{A^3}{3!} + \dots
  $$
  This map takes an element of the algebra (an infinitesimal generator) and produces an element of the group (a finite transformation). For example, an infinitesimal rotation (an element of $\mathfrak{so}(3)$) can be exponentiated to yield a finite rotation matrix (an element of $SO(3)$).

## Applications in Physics and Mathematics

Lie algebras are indispensable in modern science.

-   **Quantum Mechanics**: Physical observables like position, momentum, and angular momentum are represented by operators on a Hilbert space. The commutation relations between these operators form a Lie algebra. For instance, the angular momentum operators $L_x, L_y, L_z$ satisfy the commutation relations $[L_x, L_y] = i\hbar L_z$ (and cyclic permutations), which define the Lie algebra $\mathfrak{su}(2)$ (or $\mathfrak{so}(3)$).

-   **Particle Physics**: The Standard Model is built upon gauge symmetries described by the Lie group $SU(3) \times SU(2) \times U(1)$. The properties and interactions of elementary particles are classified according to representations of the corresponding Lie algebras.

-   **Differential Geometry**: The set of all smooth vector fields on a manifold forms an infinite-dimensional Lie algebra, where the Lie bracket is the Lie derivative of vector fields. This structure is central to understanding the geometry of the manifold.

## Conclusion

The Lie algebra is a powerful concept that linearizes the study of continuous symmetry. By abstracting the properties of operations like the vector cross product and the matrix commutator, it provides a unified framework for analyzing the local structure of Lie groups. Its axioms—bilinearity, anti-commutativity, and the Jacobi identity—are precisely what is needed to capture the essence of infinitesimal transformations. This deep connection between algebra and geometry makes Lie theory an essential tool in mathematics, physics, and engineering.

