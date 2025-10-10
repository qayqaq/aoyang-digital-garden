---
{"dg-publish":true,"permalink":"/notes/2025/09/08/moment-generating-function/"}
---

#ProbabilityTheory #Statistics #MathematicalFunctions
[[Moment-Generating Function.canvas\|Moment-Generating Function.canvas]]

# Moment-Generating Function

## I. Introduction

In probability theory and statistics, the **Moment-Generating Function (MGF)** is a function associated with a real-valued random variable that provides an alternative and often powerful way to analyze its probability distribution. Its primary purpose, as suggested by its name, is to **generate the moments** of the distribution, such as the mean and variance.

The significance of the MGF extends beyond just calculating moments. It possesses a unique property that allows it to completely determine a probability distribution. Furthermore, it greatly simplifies the analysis of sums of independent random variables, transforming complex convolution operations into simple products.

## II. Formal Definition

Let $X$ be a random variable. Its **Moment-Generating Function**, denoted by $M_X(t)$, is defined as the expected value of $e^{tX}$, provided this expectation exists for values of $t$ in some open interval containing zero.

$$
M_X(t) = E[e^{tX}]
$$

The definition can be expressed more explicitly depending on whether the random variable is discrete or continuous:

-   **For a discrete random variable** with probability mass function $p(x)$:
    $$
    M_X(t) = \sum_{x} e^{tx} p(x)
    $$
-   **For a continuous random variable** with probability density function $f(x)$:
    $$
    M_X(t) = \int_{-\infty}^{\infty} e^{tx} f(x) \,dx
    $$

> **Note on Existence**: The MGF does not exist for all distributions. For the MGF to be well-defined, the sum or integral must converge for all $t$ in an interval $(-h, h)$ for some $h > 0$. Distributions with "heavy tails," like the Cauchy distribution, do not have a defined MGF.

## III. Generating Moments

The central utility of the MGF is its ability to produce the moments of a distribution through differentiation. The **$n$-th moment about the origin**, $E[X^n]$, is obtained by taking the $n$-th derivative of the MGF with respect to $t$ and then evaluating the result at $t=0$.

$$
E[X^n] = \frac{d^n}{dt^n} M_X(t) \bigg|_{t=0}
$$

This property arises from the Taylor series expansion of $e^{tX}$:
$$
e^{tX} = 1 + tX + \frac{(tX)^2}{2!} + \frac{(tX)^3}{3!} + \dots
$$
Taking the expectation of both sides yields the Taylor series for the MGF itself:
$$
M_X(t) = E[e^{tX}] = 1 + tE[X] + \frac{t^2}{2!}E[X^2] + \frac{t^3}{3!}E[X^3] + \dots
$$
By repeatedly differentiating this series with respect to $t$ and setting $t=0$, we can isolate each moment.

-   **First Moment (Mean)**:
    $$
    E[X] = M'_X(0)
    $$
-   **Second Moment**:
    $$
    E[X^2] = M''_X(0)
    $$
From these, the variance can be calculated as $\text{Var}(X) = E[X^2] - (E[X])^2$.

## IV. Fundamental Properties

The MGF has several key properties that make it a cornerstone of theoretical statistics.

### 1. Uniqueness Property
If two random variables have MGFs that are equal in an open interval around $t=0$, then they must have the same probability distribution. This property is extremely powerful, as it allows us to identify an unknown distribution simply by deriving its MGF and matching it to a known form.

### 2. Sums of Independent Random Variables
If $X_1, X_2, \dots, X_n$ are independent random variables, the MGF of their sum $S_n = X_1 + X_2 + \dots + X_n$ is the **product** of their individual MGFs.
$$
M_{S_n}(t) = M_{X_1}(t) \cdot M_{X_2}(t) \cdots M_{X_n}(t)
$$
This property is invaluable because it converts the difficult operation of convolution of probability densities into a simple multiplication of their corresponding MGFs.

### 3. Affine Transformations
If $Y = aX + b$ for constants $a$ and $b$, the MGF of $Y$ is related to the MGF of $X$ by:
$$
M_Y(t) = E[e^{t(aX+b)}] = e^{bt}E[e^{(at)X}] = e^{bt} M_X(at)
$$

## V. Example: The Exponential Distribution

Let $X$ be an exponentially distributed random variable with rate parameter $\lambda$, denoted $X \sim \text{Exp}(\lambda)$. Its probability density function is $f(x) = \lambda e^{-\lambda x}$ for $x \ge 0$.

1.  **Calculate the MGF**:
    $$
    M_X(t) = \int_0^{\infty} e^{tx} (\lambda e^{-\lambda x}) \,dx = \lambda \int_0^{\infty} e^{(t-\lambda)x} \,dx
    $$
    This integral converges only if $t - \lambda < 0$, i.e., $t < \lambda$.
    $$
    M_X(t) = \lambda \left[ \frac{e^{(t-\lambda)x}}{t-\lambda} \right]_0^{\infty} = \lambda \left( 0 - \frac{1}{t-\lambda} \right) = \frac{\lambda}{\lambda - t}
    $$

2.  **Generate Moments**:
    -   **First Derivative**:
        $$ M'_X(t) = \frac{d}{dt} \left( \frac{\lambda}{\lambda-t} \right) = \frac{\lambda}{(\lambda-t)^2} $$
        The mean is $E[X] = M'_X(0) = \frac{\lambda}{\lambda^2} = \frac{1}{\lambda}$.
    -   **Second Derivative**:
        $$ M''_X(t) = \frac{d}{dt} \left( \frac{\lambda}{(\lambda-t)^2} \right) = \frac{2\lambda}{(\lambda-t)^3} $$
        The second moment is $E[X^2] = M''_X(0) = \frac{2\lambda}{\lambda^3} = \frac{2}{\lambda^2}$.

3.  **Calculate Variance**:
    $$
    \text{Var}(X) = E[X^2] - (E[X])^2 = \frac{2}{\lambda^2} - \left(\frac{1}{\lambda}\right)^2 = \frac{1}{\lambda^2}
    $$

## VI. Relationship with Other Functions

-   **[[Notes/2025/09/08/Cumulant-Generating Function\|Cumulant-Generating Function]] (CGF)**: The CGF is the natural logarithm of the MGF, $K_X(t) = \log(M_X(t))$. It generates cumulants instead of moments, and it has the convenient property of being additive for sums of independent random variables.
-   **[[Notes/2025/09/08/Characteristic Function\|Characteristic Function]]**: The characteristic function, $\phi_X(t) = E[e^{itX}]$, is closely related to the MGF but uses an imaginary argument. Its primary advantage is that it exists for *every* probability distribution, unlike the MGF.

## VII. Conclusion and Significance

The Moment-Generating Function is a fundamental tool in probability and statistics that provides a complete characterization of a distribution. Its ability to generate moments through differentiation, uniquely identify distributions, and simplify the analysis of sums of independent variables makes it indispensable for theoretical work, including the proof of the Central Limit Theorem. While its non-existence for certain distributions is a limitation, its elegance and power where it does apply secure its place as a key concept in the field.

