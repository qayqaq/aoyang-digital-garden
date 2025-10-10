---
{"dg-publish":true,"permalink":"/notes/2025/09/08/form/"}
---

In the context of a **differential manifold**, a "form" is more formally called a **[[Notes/2025/09/08/Differential Form\|differential form]]** or, more generally, a **tensor field**.

Let's break this down, building on the concepts from your notes.

### The Building Blocks on a Manifold

As established in the note [[Notes/2025/09/05/Riemannian Geometry\|Riemannian Geometry]], a smooth manifold $M$ has a **tangent space** $T_pM$ at each point $p$. This tangent space is a vector space containing all the possible velocity vectors at that point.

### 1. The Simplest Form: The 1-Form (or Covector)

A **1-form** (also called a **covector**) is the most fundamental type of "form" on a manifold.

> A **1-form field**, denoted $\omega$, is a smooth assignment of a linear map $\omega_p: T_pM \to \mathbb{R}$ to each point $p \in M$.

In simpler terms, a 1-form is an object that "eats" one tangent vector at a point and spits out a real number, and it does so linearly and smoothly across the entire manifold.

*   **Example**: The differential of a smooth function $f: M \to \mathbb{R}$, denoted $df$, is a 1-form. At each point $p$, $(df)_p$ takes a tangent vector $X \in T_pM$ and gives the directional derivative of $f$ in the direction of $X$.

### 2. Generalizing to Bilinear Forms and Tensors

Now we can generalize this idea. What if our object "eats" more than one vector?

This leads us to the concept of a **tensor field**. A tensor field is a smooth assignment of a tensor to each point's tangent space. The "bilinear form" you asked about is a specific type of tensor.

> A **(0, k)-tensor field** on a manifold $M$ is a smooth assignment of a multilinear map $T_p: \underbrace{T_pM \times \dots \times T_pM}_{k \text{ times}} \to \mathbb{R}$ to each point $p \in M$.

Let's connect this directly to your note [[Notes/2025/09/05/Hessian Metric\|Hessian Metric]]:

*   A **bilinear form** on a manifold is a **(0, 2)-tensor field**.
*   At each point $p$, it's a bilinear map that takes **two** tangent vectors $X, Y \in T_pM$ as input and produces a scalar $T_p(X, Y)$.
*   The **Hessian metric** $g$ is a perfect example. It is a (0, 2)-tensor field. For any point $p$, $g_p$ is the specific bilinear form (an inner product) on the tangent space $T_pM$. The fact that it's defined at *every* point and varies smoothly makes it a tensor **field**, or a "form" in the manifold context.

### Hierarchy of Forms on a Manifold

Here is a simple hierarchy to clarify the terminology:

| Type | What it is at a single point `p` | What it does | Example from your notes |
| :--- | :--- | :--- | :--- |
| **0-form** | A scalar (a number) | Assigns a number to each point | A smooth function $\phi: M \to \mathbb{R}$ |
| **1-form** | A linear map $T_pM \to \mathbb{R}$ | "Eats" one tangent vector | The differential of a function, $df$ |
| **Bilinear Form** | A bilinear map $T_pM \times T_pM \to \mathbb{R}$ | "Eats" two tangent vectors | The **Hessian metric** $g$ |

### Important Distinction: "Bilinear Form" vs. "Differential 2-Form"

In differential geometry, there's a subtle but critical distinction. The term **"differential k-form"** specifically refers to an **alternating** (or antisymmetric) (0, k)-tensor.
*   A **differential 2-form** $\omega$ must satisfy $\omega(X, Y) = -\omega(Y, X)$.
*   A **bilinear form** like the Riemannian metric $g$ is **symmetric**: $g(X, Y) = g(Y, X)$.

Therefore, while the Hessian metric is a bilinear form (a (0,2)-tensor field), it is **not** a differential 2-form. The term "form" in "symmetric, positive-definite bilinear form" is used in the broader sense of a multilinear map, not in the narrow sense of an antisymmetric differential form.

### Summary

In the context of a differential manifold, a **"form"** is a **tensor field**—a smoothly varying assignment of a multilinear map to the tangent space at each point. The "symmetric, positive-definite bilinear form" mentioned in your note [[Notes/2025/09/05/Hessian Metric\|Hessian Metric]] is specifically a **symmetric (0,2)-tensor field**, which serves as the Riemannian metric for the manifold.

