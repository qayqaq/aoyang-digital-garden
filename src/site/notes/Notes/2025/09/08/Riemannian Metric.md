---
{"dg-publish":true,"permalink":"/notes/2025/09/08/riemannian-metric/"}
---

#differential_geometry #riemannian_manifold #mathematics
[[Riemannian metric.canvas\|Riemannian metric.canvas]]

# Riemannian Metric

## I. Introduction to the Riemannian Metric

The **Riemannian metric** is the central object of study in [[Notes/2025/09/05/Riemannian Geometry\|Riemannian geometry]]. It is a mathematical tool that equips a ***smooth manifold***—a space that locally resembles Euclidean space—with a notion of geometry. In essence, a Riemannian metric provides a consistent way to define geometric concepts such as **length, angle, area, and volume** on curved spaces.

At its core, a Riemannian metric is a smoothly varying choice of an **inner product** (a generalization of the dot product) on the tangent space at every point of the manifold. This allows for local measurements to be made, which can then be integrated to yield global geometric information. The concept is a profound generalization of the geometry of surfaces in three-dimensional Euclidean space and provides the essential mathematical framework for Albert Einstein's theory of general relativity.

A smooth manifold endowed with a Riemannian metric is called a **Riemannian manifold**.

## II. Formal Definition

Let $M$ be a smooth manifold. At each point $p \in M$, there exists a vector space called the **[[Notes/2025/09/08/Tangent Space\|Tangent Space]]**, denoted $T_pM$, which consists of all possible "velocity vectors" at that point.

> A **Riemannian metric**, denoted by $g$, is a symmetric, positive-definite (0,2)-tensor field on $M$. This means that for each point $p \in M$, $g$ provides an inner product $g_p$ on the tangent space $T_pM$.

This inner product $g_p: T_pM \times T_pM \to \mathbb{R}$ must satisfy the following properties for any tangent vectors $X, Y, Z \in T_pM$ and any real number $a \in \mathbb{R}$:

1.  **Bilinearity**: The map is linear in each argument.
    *   $g_p(aX + Y, Z) = a g_p(X, Z) + g_p(Y, Z)$
    *   $g_p(X, aY + Z) = a g_p(X, Y) + g_p(X, Z)$

2.  **Symmetry**: The order of the arguments does not matter.
    $$
    g_p(X, Y) = g_p(Y, X)
    $$

3.  **Positive-definiteness**: The inner product of a non-zero vector with itself is always positive.
    $$
    g_p(X, X) > 0 \quad \text{for all } X \neq 0
    $$

The collection of these inner products, varying smoothly from point to point, constitutes the Riemannian metric $g$.

## III. Representation in Local Coordinates

In practice, a Riemannian metric is often described by its components in a local coordinate system. Let $(x^1, \dots, x^n)$ be a set of local coordinates on an open subset of the manifold $M$. The tangent space at any point in this region has a natural basis given by the partial derivative operators $\left\{ \frac{\partial}{\partial x^1}, \dots, \frac{\partial}{\partial x^n} \right\}$.

The components of the metric tensor, denoted $g_{ij}$, are defined as the inner product of these basis vectors:
$$
g_{ij}(p) = g_p\left(\frac{\partial}{\partial x^i}, \frac{\partial}{\partial x^j}\right)
$$
These components $g_{ij}$ are smooth functions of the coordinates $(x^1, \dots, x^n)$ and can be arranged into an $n \times n$ symmetric, positive-definite matrix $[g_{ij}]$. This matrix is the local representation of the metric.

## IV. Geometric Quantities Derived from the Metric

The power of the Riemannian metric lies in its ability to define fundamental geometric quantities.

* **Length of a Vector**: The length (or norm) of a tangent vector $X \in T_pM$ is defined as:
    $$
    \|X\| = \sqrt{g_p(X, X)}
    $$

* **Angle Between Vectors**: The angle $\theta$ between two non-zero tangent vectors $X, Y \in T_pM$ is defined by:
    $$
    \cos \theta = \frac{g_p(X, Y)}{\|X\| \|Y\|}
    $$

* **Length of a Curve**: For a smooth curve $\gamma: [a, b] \to M$, its length $L(\gamma)$ is found by integrating its speed, $\|\gamma'(t)\|$, over the interval:
    $$
    L(\gamma) = \int_a^b \|\gamma'(t)\| dt = \int_a^b \sqrt{g_{\gamma(t)}(\gamma'(t), \gamma'(t))} dt
    $$

* **Area and Volume**: The metric defines a natural **[[Notes/2025/09/08/Volume Element\|Volume Element]]** (or volume form) on the manifold, which can be integrated to compute the volume of regions. In local coordinates, the volume element $dV$ is given by:
    $$
    dV = \sqrt{\det(g)} \, dx^1 \wedge \dots \wedge dx^n
    $$
    where $\det(g)$ is the determinant of the metric tensor matrix $[g_{ij}]$.

## V. Fundamental Examples

### A. Euclidean Space

The simplest example is Euclidean space $\mathbb{R}^n$. The standard Riemannian metric is simply the dot product. In Cartesian coordinates $(x^1, \dots, x^n)$, the metric components are given by the Kronecker delta:
$$
g_{ij} = \delta_{ij} = \begin{cases} 1 & \text{if } i=j \\ 0 & \text{if } i \neq j \end{cases}
$$
The metric tensor is the identity matrix. This is known as a **flat metric**, as its intrinsic curvature is zero.

### B. The 2-Sphere ($S^2$)

A canonical example of a curved space is the sphere of radius $R$ embedded in $\mathbb{R}^3$. Using spherical coordinates $(\theta, \phi)$, where $\theta$ is the polar angle and $\phi$ is the azimuthal angle, the metric (often written as the line element $ds^2$) is:
$$
ds^2 = R^2 d\theta^2 + R^2 \sin^2\theta \, d\phi^2
$$
The corresponding metric tensor matrix is:
$$
[g_{ij}] = \begin{pmatrix} R^2 & 0 \\ 0 & R^2 \sin^2\theta \end{pmatrix}
$$
Since the components of the metric are not constant, this indicates the presence of curvature.

## VI. Significance and Conclusion

The Riemannian metric is a cornerstone of modern geometry. It provides a rigorous and flexible framework for analyzing the intrinsic properties of spaces, independent of any embedding in a higher-dimensional space. Its importance extends far beyond pure mathematics:

* In **General Relativity**, spacetime is modeled as a 4-dimensional pseudo-Riemannian manifold, where the metric tensor acts as the gravitational potential, and its curvature dictates the motion of objects.
* In **Information Geometry**, the space of probability distributions is treated as a Riemannian manifold where the metric is the [[Notes/2025/09/05/Fisher Metric\|Fisher metric]], providing geometric insights into statistical inference.
* In fields like **Computer Graphics** and **Robotics**, Riemannian metrics are used for shape analysis, path planning, and understanding complex configuration spaces.

In summary, the Riemannian metric generalizes the familiar concepts of Euclidean geometry to a vast array of abstract and applied contexts, providing a unified language to describe the geometry of curved spaces.
