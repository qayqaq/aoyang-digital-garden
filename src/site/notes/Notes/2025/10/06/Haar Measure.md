---
{"dg-publish":true,"permalink":"/notes/2025/10/06/haar-measure/"}
---

#mathematics #measure-theory #group-theory #topology
[[Haar Measure.canvas\|Haar Measure.canvas]]

# Haar Measure

### Introduction

The **Haar measure** is a fundamental concept in mathematical analysis, group theory, and topology that provides a way to define a notion of "volume" or "size" for subsets of a **locally compact topological group**. Its defining characteristic is its **invariance under group translation**, which generalizes the familiar property of the Lebesgue measure on Euclidean space, where the length, area, or volume of a set does not change when it is shifted.

Named after Alfréd Haar, who introduced it in 1933, the Haar measure is indispensable for performing calculus—specifically, integration—on groups. It forms the foundation for harmonic analysis on groups, representation theory, and has significant applications in number theory, probability, and physics. The existence and essential uniqueness of such a measure for any locally compact group is a powerful and non-trivial result that allows for a consistent theory of integration over these abstract spaces.

---

## 1. Formal Definition

To formally define the Haar measure, we must first specify the context. Let $G$ be a **locally compact topological group**. This is a group equipped with a topology such that the group operations (multiplication and inversion) are continuous, and every point has a compact neighborhood.

A **left Haar measure** on $G$ is a measure $\mu$ defined on the Borel $\sigma$-algebra of $G$ that satisfies the following properties:

1.  **Non-triviality**: The measure is not identically zero. That is, there exists at least one Borel set $E \subseteq G$ such that $\mu(E) > 0$.
2.  **Regularity**: The measure is a regular measure, a technical condition ensuring it behaves well with respect to the topology.
3.  **Left-Translation Invariance**: For any element $g \in G$ and any Borel set $E \subseteq G$, the measure of the translated set is equal to the measure of the original set. The left translation of $E$ by $g$ is the set $gE = \{gh \mid h \in E\}$. Formally:
    $$
    \mu(gE) = \mu(E)
    $$

This invariance property is the cornerstone of the definition. It can also be expressed in terms of integration. For any non-negative, measurable function $f: G \to \mathbb{R}$:
$$
\int_G f(gx) \, d\mu(x) = \int_G f(x) \, d\mu(x)
$$

Similarly, a **right Haar measure** $\nu$ is a measure that is invariant under right translation:
$$
\nu(Eg) = \nu(E) \quad \text{for all } g \in G, E \subseteq G
$$
where $Eg = \{hg \mid h \in E\}$.

---

## 2. Existence and Uniqueness

The central theorem concerning the Haar measure guarantees its existence and uniqueness in a specific sense.

> **Theorem (Haar-von Neumann-Weil)**: For any locally compact topological group $G$, a left Haar measure exists. Furthermore, this measure is unique up to a positive multiplicative constant.

The uniqueness part means that if $\mu_1$ and $\mu_2$ are two left Haar measures on the same group $G$, then there exists a constant $c > 0$ such that $\mu_1 = c \mu_2$. The same theorem holds for right Haar measures.

This result is profound because it ensures that integration over such groups is well-defined, regardless of the specific construction of the measure, apart from a choice of normalization.

---

## 3. Examples

### 3.1. Abelian Groups
- **The Real Line $(\mathbb{R}, +)$**: The group of real numbers under addition. The Haar measure is the standard **Lebesgue measure**. The length of an interval $[a, b]$ is $b-a$, and the length of its translation $[a+c, b+c]$ is $(b+c)-(a+c) = b-a$.
- **The Circle Group $(\mathbb{T}, \times)$**: The group of complex numbers of modulus 1, often identified with the interval $[0, 2\pi)$ with addition modulo $2\pi$. The Haar measure is proportional to the Lebesgue measure on the angle, $d\theta$. If normalized to be a probability measure, the total measure is 1, so $d\mu = \frac{1}{2\pi}d\theta$.

### 3.2. Non-Abelian Groups
- **General Linear Group $GL(n, \mathbb{R})$**: The group of invertible $n \times n$ real matrices. This is a non-compact, non-abelian group. A left and right Haar measure is given by the differential form:
  $$
  d\mu(A) = \frac{1}{|\det(A)|^n} \prod_{i,j=1}^n dA_{ij}
  $$
  where $dA_{ij}$ is the Lebesgue measure on the matrix entries.

### 3.3. Discrete Groups
- **The Integers $(\mathbb{Z}, +)$**: For any discrete group, the Haar measure is simply the **counting measure**. The "volume" of a set is the number of elements it contains. Translating a finite set does not change the number of elements.

---

## 4. The Modular Function and Unimodular Groups

A left Haar measure on a group is not necessarily a right Haar measure. The relationship between them is captured by the **modular function**.

Let $\mu$ be a left Haar measure on $G$. For any fixed $g \in G$, one can define a new measure $\mu_g$ by $\mu_g(E) = \mu(Eg)$. It can be shown that $\mu_g$ is also a left Haar measure. By the uniqueness theorem, there must be a positive constant, which we denote $\Delta(g)$, such that:
$$
\mu(Eg) = \Delta(g) \mu(E)
$$
The function $\Delta: G \to \mathbb{R}^+$ is called the **modular function** or **modular character** of $G$. It is a continuous group homomorphism.

A group $G$ is called **unimodular** if its modular function is identically 1, i.e., $\Delta(g) = 1$ for all $g \in G$. For unimodular groups, every left Haar measure is also a right Haar measure.

Important classes of unimodular groups include:
- **Abelian groups**: Since $gE = Eg$, they are always unimodular.
- **Compact groups**: Such as the special orthogonal group $SO(n)$ or the special unitary group $SU(n)$.
- **Discrete groups**.
- **Semisimple Lie groups**: Such as the special linear group $SL(n, \mathbb{R})$.

---

## 5. Applications

The Haar measure is a cornerstone of several advanced mathematical and physical theories.

- **Harmonic Analysis**: It is used to define the Fourier transform and convolution on general locally compact groups, extending these concepts beyond Euclidean space. It allows for the construction of function spaces like $L^p(G)$.
- **Representation Theory**: The Haar measure is essential for proving the Schur orthogonality relations for representations of compact groups, a key result in the theory. Integrals over the group, which rely on the Haar measure, are ubiquitous.
- **Probability Theory**: On a compact group, the Haar measure can be normalized to have total measure 1, turning it into a probability measure. This defines the **uniform distribution** on the group and is fundamental to fields like random matrix theory.
- **Physics**: In quantum field theory and particle physics, path integrals often involve integrating over symmetry groups (e.g., gauge groups like $SU(3)$). This integration is performed with respect to the Haar measure on the group.

---

## Conclusion

The Haar measure provides a powerful and consistent way to define an invariant volume on locally compact topological groups, thereby generalizing the Lebesgue measure. Its guaranteed existence and uniqueness (up to a constant) make it a reliable tool for analysis on groups. By enabling integration, it opens the door to harmonic analysis, representation theory, and probability on a vast class of abstract spaces, cementing its role as a fundamental concept in modern mathematics and theoretical physics.
