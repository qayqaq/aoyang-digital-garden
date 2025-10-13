---
{"dg-publish":true,"permalink":"/notes/2025/10/13/lie-group/","tags":["#mathematics","#algebra","#geometry","#LieTheory","#physics"]}
---

- A **Lie group** is a mathematical object that is simultaneously a **group** and a **smooth manifold**, where the group operations (multiplication and inversion) are smooth functions.
- It is the fundamental framework for describing **continuous symmetries**, such as rotations and translations.
- Every Lie group has an associated [[Notes/2025/10/13/Lie Algebra\|Lie Algebra]], which is its tangent space at the identity element and represents the group's "infinitesimal generators."
- The relationship between a Lie group and its Lie algebra, bridged by the **exponential map**, allows complex non-linear problems on the group to be studied using the tools of linear algebra.

#mathematics #algebra #geometry #LieTheory #physics
[[Lie Group.canvas\|Lie Group.canvas]]

# Lie Group

## Introduction

A **Lie group** (pronounced /liː/ "lee") represents a profound synthesis of algebra and geometry. It is an object that is both a **group**, satisfying the axioms of abstract algebra, and a **smooth (or differentiable) manifold**, an object that locally resembles Euclidean space. The crucial feature connecting these two structures is that the group operations—multiplication and inversion—are smooth functions. This unique combination makes Lie groups the natural mathematical language for describing **continuous symmetries**, which are ubiquitous in physics, mathematics, and engineering.

Whereas discrete groups describe symmetries like reflections or finite rotations, Lie groups capture the essence of continuous transformations, such as the seamless rotation of an object through any angle or its smooth translation through space.

## Formal Definition

A set $G$ is a **Lie group** if it satisfies the following conditions:

1.  **Group Structure**: $G$ is a group. It is equipped with a binary operation (multiplication) that satisfies:
    *   **Closure**: For all $g_1, g_2 \in G$, the product $g_1 g_2$ is also in $G$.
    *   **Associativity**: For all $g_1, g_2, g_3 \in G$, $(g_1 g_2) g_3 = g_1 (g_2 g_3)$.
    *   **Identity Element**: There exists an identity element $e \in G$ such that for every $g \in G$, $e g = g e = g$.
    *   **Inverse Element**: For each $g \in G$, there exists an inverse $g^{-1} \in G$ such that $g g^{-1} = g^{-1} g = e$.

2.  **Manifold Structure**: $G$ is a smooth (infinitely differentiable) manifold. This means that locally, around any point, $G$ "looks like" an open subset of a Euclidean space $\mathbb{R}^n$ for some fixed dimension $n$.

3.  **Smoothness of Group Operations**: The group operations are smooth maps. Specifically:
    *   The multiplication map $m: G \times G \to G$, defined by $m(g_1, g_2) = g_1 g_2$, is smooth.
    *   The inversion map $i: G \to G$, defined by $i(g) = g^{-1}$, is smooth.

This final condition ensures that the algebraic and geometric structures are compatible, allowing the powerful tools of calculus to be applied to the study of the group.

## Key Examples

### 1. The Real Numbers under Addition
The set of real numbers $\mathbb{R}$ with the operation of addition forms the simplest non-trivial Lie group.
- **Group**: $(\mathbb{R}, +)$ is an abelian group with identity 0 and inverse $-x$.
- **Manifold**: $\mathbb{R}$ is a one-dimensional manifold (a line).
- **Smoothness**: The maps $m(x, y) = x+y$ and $i(x) = -x$ are smooth functions.

### 2. The Circle Group $U(1)$
The set of complex numbers with modulus 1, denoted $U(1)$ or $S^1$.
- **Group**: Elements can be written as $e^{i\theta}$ for $\theta \in \mathbb{R}$. The group operation is multiplication: $e^{i\theta_1} e^{i\theta_2} = e^{i(\theta_1+\theta_2)}$. The identity is $1 = e^{i0}$, and the inverse of $e^{i\theta}$ is $e^{-i\theta}$.
- **Manifold**: Geometrically, this is the unit circle in the complex plane, which is a one-dimensional manifold.
- **Significance**: This is the simplest example of a **compact** Lie group. It describes the symmetry group for phase transformations in quantum mechanics.

### 3. The General Linear Group $GL(n, \mathbb{R})$
The set of all invertible $n \times n$ matrices with real entries.
- **Group**: The operation is matrix multiplication, which is associative. The identity is the identity matrix $I$, and the inverse is the matrix inverse.
- **Manifold**: The set of $n \times n$ matrices can be identified with $\mathbb{R}^{n^2}$. The condition that a matrix is invertible is $\det(A) \neq 0$. Since the determinant is a continuous function, $GL(n, \mathbb{R})$ is an open subset of $\mathbb{R}^{n^2}$ and is therefore a manifold of dimension $n^2$.

### 4. The Special Orthogonal Group $SO(n)$
The group of rotations in $n$-dimensional Euclidean space.
- **Group**: It consists of all $n \times n$ real matrices $R$ such that $R^T R = I$ (orthogonality) and $\det(R) = 1$ (orientation-preserving).
- **Manifold**: This is a compact, connected Lie group. For $n=3$, $SO(3)$ is the group of rotations in 3D space, which has dimension 3 (e.g., specified by three Euler angles).

## The Lie Group–Lie Algebra Correspondence

The most powerful concept in the theory is the intimate relationship between a Lie group and its associated [[Notes/2025/10/13/Lie Algebra\|Lie Algebra]].

-   **The Lie Algebra $\mathfrak{g}$**: The [[Notes/2025/10/13/Lie Algebra\|Lie Algebra]] of a Lie group $G$, denoted $\mathfrak{g}$, is defined as the **tangent space to the manifold $G$ at the identity element $e$**.
    $$
    \mathfrak{g} = T_eG
    $$
-   **Infinitesimal Generators**: The elements of the [[Notes/2025/10/13/Lie Algebra\|Lie Algebra]] can be thought of as "infinitesimal generators." They describe the possible directions and speeds of motion starting from the identity. For example, the [[Notes/2025/10/13/Lie Algebra\|Lie Algebra]] of the rotation group $SO(3)$ is the set of infinitesimal rotations, which corresponds to angular velocity vectors in $\mathbb{R}^3$.

-   **The Exponential Map**: The connection from the algebra back to the group is provided by the **exponential map**, $\exp: \mathfrak{g} \to G$. This map takes an infinitesimal generator in $\mathfrak{g}$ and maps it to a finite transformation in $G$. For matrix Lie groups, this is simply the matrix exponential:
    $$
    \exp(X) = \sum_{k=0}^{\infty} \frac{X^k}{k!}
    $$

This correspondence is incredibly powerful because it allows us to study the complex, non-linear global structure of a Lie group $G$ by analyzing its [[Notes/2025/10/13/Lie Algebra\|Lie Algebra]] $\mathfrak{g}$, which is a linear vector space. Many properties of the group can be understood by studying the simpler, linear structure of its algebra.

## Applications

Lie groups are fundamental to modern science.

-   **Physics**: According to Noether's theorem, every continuous symmetry of a physical system corresponds to a conserved quantity. These symmetries are described by Lie groups.
    -   **Rotational Invariance ($SO(3)$)** implies conservation of **angular momentum**.
    -   **Translational Invariance ($\mathbb{R}^3$)** implies conservation of **linear momentum**.
    -   **Time Invariance ($\mathbb{R}$)** implies conservation of **energy**.
    -   The **Standard Model of Particle Physics** is a gauge theory based on the Lie group $SU(3) \times SU(2) \times U(1)$.

-   **Robotics and Computer Vision**: The group of rigid body motions in 3D space, the special Euclidean group $SE(3)$, is a Lie group used to describe the position and orientation of robots and objects.

-   **Differential Geometry**: Lie groups are themselves prime examples of manifolds, and their theory is deeply intertwined with the study of geometric structures.

## Conclusion

Lie groups provide a unified and elegant framework for studying continuous symmetry by merging the concepts of groups and smooth manifolds. The ability to linearize problems via the Lie group–Lie algebra correspondence is a tool of unparalleled power, allowing complex geometric and algebraic questions to be addressed with the methods of linear algebra. From the fundamental laws of particle physics to the practical control of robotic arms, the influence of Lie theory is both deep and pervasive.
