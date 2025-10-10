---
{"dg-publish":true,"permalink":"/notes/2025/09/08/tangent-space/"}
---

#differential_geometry #manifold_theory #mathematics
[[Tangent Space.canvas\|Tangent Space.canvas]]

# Tangent Space

## I. Introduction: Linearizing Curved Space

In differential geometry, the **tangent space** is a fundamental concept that ***provides a linear approximation of a manifold at a specific point***. A manifold is a space that may be globally curved (like a sphere), but it locally resembles flat Euclidean space. The tangent space is precisely this local, flat, Euclidean-like approximation.

Intuitively, for a curve in a plane, the tangent space at a point is the tangent line at that point. For a surface in 3D space, it is the tangent plane. The tangent space generalizes this idea to manifolds of any dimension. ***Its primary importance lies in its role as the domain for calculus on manifolds; it is the space where we can define derivatives, velocities, and other vector-like quantities*** in a rigorous manner.

The set of all tangent vectors at a point $p$ on a manifold $M$ forms a real vector space, denoted $T_pM$, called the tangent space of $M$ at $p$.

## II. Intuitive Development

To build an intuition for the tangent space, we can consider familiar examples:

1. **Curve in $\mathbb{R}^2$**: For a smooth curve, the tangent line at a point $p$ represents the direction and speed of a particle moving along the curve at that instant. The collection of all possible velocity vectors at $p$ forms a one-dimensional vector space: the tangent space $T_pM$.

2. **Surface in $\mathbb{R}^3$**: For a smooth surface like a sphere, the tangent plane at a point $p$ is the plane that "just touches" the surface at that point. This plane is the best two-dimensional linear approximation of the surface near $p$. All possible velocity vectors of paths on the surface passing through $p$ lie within this plane. This plane, viewed as a vector space centered at the origin, is the tangent space $T_pM$.

While these examples are helpful, they rely on the manifold being embedded in a higher-dimensional Euclidean space. The modern definition of a tangent space is intrinsic, meaning it does not depend on any such embedding.

## III. Formal Definitions of Tangent Vectors

There are two common and equivalent ways to formally define tangent vectors intrinsically.

### A. Tangent Vectors as Equivalence Classes of Curves

A tangent vector can be thought of as the "velocity" of a curve passing through a point.

Let $M$ be a [[Notes/2025/09/08/Smooth Manifold\|Smooth Manifold]] and $p \in M$. Consider all smooth curves $\gamma: (-\epsilon, \epsilon) \to M$ such that $\gamma(0) = p$. We define an equivalence relation $\sim$ on the set of these curves. Two curves $\gamma_1$ and $\gamma_2$ are said to be equivalent, $\gamma_1 \sim \gamma_2$, if they have the same "velocity" at $p$. Formally, in any local coordinate chart $(U, \phi)$ around $p$, their derivatives at $t=0$ are equal:
$$
\frac{d}{dt}(\phi \circ \gamma_1)(t)\bigg|_{t=0} = \frac{d}{dt}(\phi \circ \gamma_2)(t)\bigg|_{t=0}
$$
> A **tangent vector** at $p$ is ***an equivalence class of such curves under the relation $\sim$. The tangent space $T_pM$ is the set of all such equivalence classes***.

### B. Tangent Vectors as Derivations

This is a more abstract but often more powerful definition. It **defines a tangent vector by what it *does* to functions**: it computes a directional derivative.

Let $C^\infty(M)$ be the set of all smooth, real-valued functions on the manifold $M$.

> A **tangent vector** $v$ at a point $p \in M$ is a **derivation** at $p$. A derivation is a linear map $v: C^\infty(M) \to \mathbb{R}$ that satisfies the **Leibniz rule** (product rule):
> $$
> v(fg) = f(p)v(g) + g(p)v(f)
> $$
> for all functions $f, g \in C^\infty(M)$.

The linearity property means $v(af+bg) = av(f) + bv(g)$ for constants $a, b \in \mathbb{R}$. The Leibniz rule ensures that the vector only depends on the behavior of the functions infinitesimally close to the point $p$. The set of all such derivations at $p$ is the tangent space $T_pM$.

## IV. The Basis of the Tangent Space

The tangent space $T_pM$ is a real vector space with a dimension equal to the dimension of the manifold, $n$. In any local coordinate system $(x^1, \dots, x^n)$ defined in a neighborhood of $p$, we can construct a natural basis for $T_pM$.

This basis is given by the set of partial derivative operators evaluated at $p$:
$$
\left\{ \frac{\partial}{\partial x^1}\bigg|_p, \frac{\partial}{\partial x^2}\bigg|_p, \dots, \frac{\partial}{\partial x^n}\bigg|_p \right\}
$$
Each operator $\frac{\partial}{\partial x^i}\big|_p$ is a derivation and thus a valid tangent vector. For any smooth function $f$, it is defined as:
$$
\frac{\partial}{\partial x^i}\bigg|_p (f) = \frac{\partial (f \circ \phi^{-1})}{\partial y^i}\bigg|_{\phi(p)}
$$
where $(y^1, \dots, y^n)$ are the coordinates in $\mathbb{R}^n$ corresponding to the chart $\phi$.

Any tangent vector $v \in T_pM$ can be uniquely expressed as a linear combination of these basis vectors:
$$
v = \sum_{i=1}^n v^i \frac{\partial}{\partial x^i}\bigg|_p
$$
The coefficients $(v^1, \dots, v^n)$ are the **components** of the vector $v$ in this coordinate basis.

## V. The Tangent Bundle

While the tangent space $T_pM$ exists at a single point, we can consider the collection of all tangent spaces for all points on the manifold.

The **tangent bundle**, denoted $TM$, is the disjoint union of all tangent spaces:
$$
TM = \bigsqcup_{p \in M} T_pM
$$
The tangent bundle is not just a set; it is itself a smooth manifold of dimension $2n$ (where $n$ is the dimension of $M$). A point in $TM$ is a pair $(p, v)$ where $p \in M$ and $v \in T_pM$.

A **vector field** is a smooth assignment of a tangent vector to each point on the manifold. More formally, a vector field is a smooth map $X: M \to TM$ such that for every $p \in M$, $X(p) \in T_pM$.

## VI. Conclusion and Significance

The tangent space is a cornerstone of differential geometry, serving as the bridge between the potentially complex global structure of a manifold and the familiar, linear world of vector spaces.

* **Foundation for Calculus**: It allows for the definition of derivatives of functions and curves on manifolds.
* **Domain for Tensors**: It is the fundamental space upon which tensors are defined. For example, a [[Notes/2025/09/08/Riemannian Metric\|Riemannian metric]] is an inner product defined on the tangent space at each point, and a [[Notes/2025/09/08/Differential Form\|differential form]] is a multilinear map on the tangent space.
* **Applications in Physics**: In physics, tangent spaces are indispensable. In classical mechanics, the state of a system is a point in a phase space manifold, and its velocity is a vector in the tangent space. In General Relativity, spacetime is a manifold, and the four-velocity of an object is a tangent vector.

In summary, the tangent space linearizes a manifold locally, providing a rigorous framework to apply the tools of linear algebra and calculus to the study of curved spaces.

