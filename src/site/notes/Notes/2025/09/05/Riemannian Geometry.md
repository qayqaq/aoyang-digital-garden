---
{"dg-publish":true,"permalink":"/notes/2025/09/05/riemannian-geometry/"}
---

#mathematics #geometry #differential_geometry #relativity

[[Riemannian Geometry.canvas\|Riemannian Geometry.canvas]]

# Riemannian Geometry

## I. Introduction to Riemannian Geometry

**Riemannian Geometry** is a branch of differential geometry that studies **Riemannian manifolds**, which are smooth manifolds equipped with a **Riemannian metric**. In essence, it is the study of curved spaces, generalizing the principles of Euclidean geometry to contexts where the familiar axioms of "flat" space no longer hold.

The central idea is to define geometric properties—such as length, angle, area, and volume—on a locally defined basis. At each point on a curved surface or in a higher-dimensional space, one can define a local "flat" space (the tangent space) where an inner product is specified. The Riemannian metric is the field of these inner products, varying smoothly from point to point. This framework allows for the analysis of intrinsic geometry, meaning the properties of a space that can be determined by measurements made entirely within that space.

Its significance is profound, most notably providing the mathematical language for Albert Einstein's **theory of general relativity**, where gravity is not a force but a manifestation of the curvature of spacetime.

## II. Foundational Concepts

### A. Smooth Manifolds and Tangent Spaces

Before defining a Riemannian metric, one must first understand the space on which it is defined.

-   **Smooth Manifold**: A **smooth manifold** is a topological space that, on a local scale, resembles Euclidean space ($ \mathbb{R}^n $). This means that for any point on the manifold, there exists a neighborhood around it that is topologically equivalent (homeomorphic) to an open subset of $ \mathbb{R}^n $. These local coordinate systems are called **charts**, and a collection of charts covering the entire manifold is an **atlas**. The "smooth" property ensures that transitions between overlapping charts are differentiable to any order.

-   **Tangent Space**: At each point $p$ on a smooth manifold $M$, we can define the **tangent space**, denoted $T_pM$. This is an $n$-dimensional vector space that consists of all possible "velocities" or tangent vectors to curves passing through $p$. It can be visualized as the plane (or hyperplane) that best approximates the manifold at that point.

### B. The Riemannian Metric

The core object of study in Riemannian geometry is the **Riemannian metric**.

> A **Riemannian metric**, denoted by $g$, is a smoothly varying choice of an inner product on the tangent space $T_pM$ at each point $p \in M$.

Formally, the metric $g$ is a symmetric, positive-definite (0,2)-tensor field. This means for any two tangent vectors $X, Y \in T_pM$, the metric $g_p(X, Y)$ is a real number satisfying:
1.  **Bilinearity**: Linear in both $X$ and $Y$.
2.  **Symmetry**: $g_p(X, Y) = g_p(Y, X)$.
3.  **Positive-definiteness**: $g_p(X, X) \geq 0$, with equality if and only if $X = 0$.

In a local coordinate system $(x^1, \dots, x^n)$, the metric is represented by a matrix of functions, $g_{ij}(p)$, where:
$$
g_{ij}(p) = g_p\left(\frac{\partial}{\partial x^i}, \frac{\partial}{\partial x^j}\right)
$$
The pair $(M, g)$ is called a **Riemannian manifold**.

## III. Core Geometric Measurements

The Riemannian metric provides the tools to define fundamental geometric quantities.

### A. Length of a Curve

The length of a smooth curve $\gamma: [a, b] \to M$ is calculated by integrating the norm of its velocity vector $\gamma'(t) = \frac{d\gamma}{dt}$. The norm is defined by the metric.

The length $L(\gamma)$ is given by the integral:
$$
L(\gamma) = \int_a^b \sqrt{g_{\gamma(t)}(\gamma'(t), \gamma'(t))} \, dt
$$
In local coordinates, this becomes the familiar arc length formula, generalized for a curved space:
$$
L(\gamma) = \int_a^b \sqrt{\sum_{i,j=1}^n g_{ij}(\gamma(t)) \frac{dx^i}{dt} \frac{dx^j}{dt}} \, dt
$$

### B. Angles Between Vectors

The angle $\theta$ between two non-zero tangent vectors $X, Y \in T_pM$ is defined using the inner product provided by the metric, analogous to the dot product in Euclidean space:
$$
\cos \theta = \frac{g_p(X, Y)}{\sqrt{g_p(X, X)} \sqrt{g_p(Y, Y)}}
$$

### C. Geodesics

In Euclidean space, the shortest path between two points is a straight line. In a Riemannian manifold, the concept of a "straight line" is replaced by a **geodesic**.

> A **geodesic** is a curve that locally minimizes distance. It is the "straightest possible" path on the manifold.

A key property of a geodesic is that its tangent vector is **parallel transported** along itself. This means the vector's direction does not change with respect to the manifold's local geometry. The path of a geodesic is determined by the **geodesic equation**, a system of second-order differential equations involving the metric and its derivatives (specifically, the **Christoffel symbols**).

## IV. Curvature: The Essence of Curved Space

The defining feature that distinguishes Riemannian geometry from flat Euclidean geometry is **curvature**. Curvature quantifies how the geometry of a manifold deviates from being flat.

### A. Parallel Transport and Holonomy

Imagine moving a vector along a closed loop on a surface while keeping it "as straight as possible" (parallel transport).
-   On a flat plane, the vector will return to its starting point unchanged.
-   On a curved surface, like a sphere, the vector will return rotated relative to its initial orientation.

This phenomenon, where path-dependent orientation changes occur, is called **holonomy**, and it is a direct consequence of curvature.

### B. The Riemann Curvature Tensor

The **Riemann curvature tensor**, denoted $R$, is the central tool for measuring the intrinsic curvature of a manifold. It precisely quantifies the failure of parallel transport to be path-independent.

Given three vector fields $X, Y, Z$, the curvature tensor $R(X, Y)Z$ measures the failure of the second covariant derivatives (a generalization of partial derivatives to manifolds) to commute. It can be interpreted as the infinitesimal change in a vector $Z$ when it is parallel transported around a tiny parallelogram defined by vectors $X$ and $Y$.

A manifold is **flat** (locally isometric to Euclidean space) if and only if its Riemann curvature tensor is zero everywhere.

### C. Ricci and Scalar Curvature

The Riemann tensor contains a vast amount of information. By contracting it, we obtain simpler, yet still powerful, measures of curvature.

-   **Ricci Curvature Tensor ($Ric$)**: This is a (0,2)-tensor obtained by tracing one component of the Riemann tensor. In a given direction, it measures the rate at which the volume of a small cone of geodesics deviates from the volume of a similar cone in flat space. It captures information about how volume is distorted by curvature.

-   **Scalar Curvature ($R$)**: This is a single function on the manifold obtained by tracing the Ricci tensor with respect to the metric. It represents the average Ricci curvature over all directions at a point, providing a single number that describes the local intrinsic curvature.

## V. Applications in Physics and Beyond

### A. General Relativity

The most celebrated application of Riemannian geometry is in Einstein's theory of **general relativity**.
-   **Spacetime as a Manifold**: Spacetime is modeled as a 4-dimensional, smooth manifold with a **Lorentzian metric** (a variant of the Riemannian metric where the signature is not positive-definite, allowing for the concept of time).
-   **Gravity as Curvature**: The presence of mass and energy curves spacetime. The gravitational field is identified with the metric tensor $g_{\mu\nu}$.
-   **Einstein's Field Equations**: This set of equations relates the geometry of spacetime to its matter-energy content:
    $$
    R_{\mu\nu} - \frac{1}{2} R g_{\mu\nu} = \frac{8\pi G}{c^4} T_{\mu\nu}
    $$
    Here, the left side describes the curvature of spacetime (using the Ricci tensor $R_{\mu\nu}$ and scalar curvature $R$), while the right side describes the distribution of matter and energy ($T_{\mu\nu}$ is the stress-energy tensor).
-   **Motion of Particles**: Freely falling particles and light rays travel along geodesics of this curved spacetime.

### B. Other Fields

Riemannian geometry also finds applications in:
-   **Information Geometry**: The space of probability distributions can be treated as a Riemannian manifold where the metric is the **Fisher information metric**.
-   **Computer Vision and Graphics**: Used for shape analysis, surface matching, and creating physically realistic animations on curved surfaces.
-   **Robotics**: Helps in planning the motion of robotic arms and navigating complex, constrained spaces.

## VI. Conclusion

Riemannian geometry provides a robust and elegant mathematical framework for studying curved spaces. By equipping a smooth manifold with a metric tensor, it allows for the generalization of fundamental geometric concepts like distance, angle, and straightness. Its central concept, curvature, captured by the Riemann tensor, precisely describes how a space deviates from being flat. Beyond its foundational role in modern physics, particularly general relativity, its principles are increasingly vital in diverse fields ranging from data science to robotics, demonstrating its enduring power and versatility.

