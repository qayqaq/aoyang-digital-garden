---
{"dg-publish":true,"permalink":"/notes/2025/09/08/cumulant-generating-function/"}
---

#ProbabilityTheory #Statistics #MathematicalFunctions
[[Cumulant-Generating Function.canvas\|Cumulant-Generating Function.canvas]]

# Cumulant-Generating Function

## I. Introduction

In probability theory and statistics, the **Cumulant-Generating Function (CGF)** is a powerful tool used to analyze the properties of a probability distribution. It is defined as the natural logarithm of the [[Notes/2025/09/08/Moment-Generating Function\|Moment-Generating Function]] (MGF). While the MGF generates the moments of a distribution, the CGF, as its name suggests, generates the **cumulants**.

The primary significance of the CGF lies in its elegant properties, particularly concerning the sums of independent random variables. Its use simplifies many theoretical derivations and provides a deeper insight into the structure of distributions, connecting them to concepts in statistical physics and information theory.

## II. Formal Definition

Let $X$ be a random variable. Its **Moment-Generating Function (MGF)**, if it exists, is defined as:
$$
M_X(t) = E[e^{tX}]
$$
where $E[\cdot]$ denotes the expected value.

The **Cumulant-Generating Function**, $K_X(t)$, is the natural logarithm of the MGF:
$$
K_X(t) = \log(M_X(t)) = \log(E[e^{tX}])
$$
The function is defined for all real values of $t$ for which the MGF exists and is positive.

## III. Generating Cumulants

The central purpose of the CGF is to provide a straightforward method for calculating the cumulants of a distribution. The **cumulants**, denoted by $\kappa_n$, are a set of parameters that characterize a probability distribution. They are obtained by taking successive derivatives of the CGF and evaluating them at $t=0$.

Specifically, ***the $n$-th cumulant is the $n$-th derivative of the CGF at the origin***:
$$
\kappa_n = \frac{d^n}{dt^n} K_X(t) \bigg|_{t=0}
$$

### Relationship Between Cumulants and Moments

The first few cumulants are directly related to the more familiar central moments (mean, variance, skewness, etc.).

-   **First Cumulant ($\kappa_1$)**: The **mean** of the distribution.
    $$
    \kappa_1 = K'_X(0) = \mu
    $$
-   **Second Cumulant ($\kappa_2$)**: The **variance** of the distribution.
    $$
    \kappa_2 = K''_X(0) = \sigma^2
    $$
-   **Third Cumulant ($\kappa_3$)**: The third central moment, used to define **skewness**.
    $$
    \kappa_3 = K'''_X(0) = E[(X-\mu)^3]
    $$
-   **Fourth Cumulant ($\kappa_4$)**: Related to the fourth central moment and **kurtosis**.
    $$
    \kappa_4 = K^{(4)}_X(0) = E[(X-\mu)^4] - 3(\sigma^2)^2
    $$
    This is also known as the **excess kurtosis**.

> **Note**: For the normal distribution, all cumulants of order higher than two are zero ($\kappa_n = 0$ for $n > 2$). This is a unique and defining property of the Gaussian distribution.

## IV. Fundamental Properties

The CGF possesses several properties that make it exceptionally useful in theoretical analysis.

### 1. Additivity for Independent Random Variables

This is arguably the most important property of the CGF. If $X_1, X_2, \dots, X_n$ are independent random variables, the CGF of their sum $S_n = X_1 + X_2 + \dots + X_n$ is the sum of their individual CGFs.

$$
K_{S_n}(t) = K_{X_1}(t) + K_{X_2}(t) + \dots + K_{X_n}(t)
$$

This follows directly from the property that the MGF of a sum of independent variables is the product of their MGFs:
$M_{S_n}(t) = M_{X_1}(t) \cdot M_{X_2}(t) \cdots M_{X_n}(t)$. Taking the logarithm of both sides yields the additive property for the CGF.

An immediate consequence is that the cumulants are also additive for independent random variables:
$$
\kappa_k(S_n) = \sum_{i=1}^{n} \kappa_k(X_i)
$$

### 2. Behavior under Affine Transformations

If we have a random variable $Y = aX + b$, where $a$ and $b$ are constants, its CGF is related to the CGF of $X$ as follows:
$$
K_Y(t) = K_{aX+b}(t) = bt + K_X(at)
$$
This property allows for a simple transformation of the cumulants:
-   $\kappa_1(Y) = a\kappa_1(X) + b$
-   $\kappa_n(Y) = a^n \kappa_n(X)$ for $n \ge 2$

## V. Example: The Normal Distribution

Let $X \sim \mathcal{N}(\mu, \sigma^2)$ be a normally distributed random variable.

1.  **Moment-Generating Function (MGF)**:
    The MGF for the normal distribution is well-known:
    $$
    M_X(t) = \exp\left(\mu t + \frac{1}{2}\sigma^2 t^2\right)
    $$

2.  **Cumulant-Generating Function (CGF)**:
    Taking the natural logarithm of the MGF gives the CGF:
    $$
    K_X(t) = \log(M_X(t)) = \mu t + \frac{1}{2}\sigma^2 t^2
    $$

3.  **Calculating Cumulants**:
    We now differentiate $K_X(t)$ with respect to $t$ and evaluate at $t=0$.
    -   **First Derivative**: $K'_X(t) = \mu + \sigma^2 t$
        $$ \kappa_1 = K'_X(0) = \mu $$
    -   **Second Derivative**: $K''_X(t) = \sigma^2$
        $$ \kappa_2 = K''_X(0) = \sigma^2 $$
    -   **Higher-Order Derivatives**: For any $n > 2$, the $n$-th derivative is zero.
        $$ \kappa_n = K^{(n)}_X(0) = 0 \quad \text{for } n \ge 3 $$
    This confirms that for a normal distribution, the mean is $\mu$, the variance is $\sigma^2$, and all higher-order cumulants are zero.

## VI. Conclusion and Significance

The Cumulant-Generating Function is a fundamental concept in probability theory that offers a powerful alternative to the Moment-Generating Function. Its defining feature—the additivity of cumulants for sums of independent random variables—makes it an indispensable tool for proving limit theorems, such as the Central Limit Theorem, and for analyzing complex systems in fields like statistical mechanics, where it is analogous to the free energy. By providing a direct pathway to the cumulants, the CGF illuminates the essential structural properties of probability distributions in a manner that is both mathematically elegant and practically profound.



