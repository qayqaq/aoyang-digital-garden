---
{"dg-publish":true,"permalink":"/notes/2025/10/06/chi-squared-distribution/"}
---

#statistics #probability-theory #hypothesis-testing
[[Chi-Squared Distribution.canvas\|Chi-Squared Distribution.canvas]]

# Chi-Squared Distribution

## Introduction

The **Chi-Squared (or Chi-Square) distribution**, denoted as $\chi^2$, is one of the most fundamental and widely used probability distributions in statistics. It is a continuous probability distribution of a sum of squared random variables. Specifically, it arises from the sum of the squares of a set of independent **standard normal** random variables.

The significance of the chi-squared distribution lies in its central role in **inferential statistics**. It forms the basis for a class of powerful hypothesis tests, most notably the **chi-squared tests**, which are used to assess the "goodness of fit" between observed data and a theoretical model, and to test for the independence of categorical variables. It is also essential for constructing confidence intervals for the variance of a population.

## Mathematical Definition

The chi-squared distribution is defined by a single parameter: $k$, which represents the **degrees of freedom**.

> If $Z_1, Z_2, \dots, Z_k$ are $k$ independent random variables, each following the standard normal distribution (with mean 0 and variance 1), then the random variable $Q$ defined as the sum of their squares:
> $$
> Q = \sum_{i=1}^{k} Z_i^2
> $$
> is distributed according to the **chi-squared distribution with $k$ degrees of freedom**. This is written as $Q \sim \chi^2(k)$.

The probability density function (PDF) of the chi-squared distribution is given by:
$$
f(x; k) = \frac{1}{2^{k/2}\Gamma(k/2)} x^{\frac{k}{2}-1} e^{-\frac{x}{2}} \quad \text{for } x > 0
$$
where:
-   $x$ is the value of the chi-squared statistic (it must be non-negative).
-   $k$ is the number of degrees of freedom.
-   $\Gamma(k/2)$ is the gamma function, which is a generalization of the factorial function.

## Properties of the Chi-Squared Distribution

The degrees of freedom, $k$, entirely determine the shape and properties of the distribution.

-   **Shape**: The distribution is defined only for positive values and is always skewed to the right.
    -   For $k=1$ and $k=2$, the distribution is heavily skewed.
    -   As the degrees of freedom $k$ increase, the distribution becomes more symmetric and bell-shaped, approaching a normal distribution (a consequence of the Central Limit Theorem).

-   **Mean and Variance**: The mean and variance are directly related to the degrees of freedom:
    -   **Mean**: $\mu = k$
    -   **Variance**: $\sigma^2 = 2k$

-   **Additivity Property**: One of the most useful properties is that the sum of independent chi-squared variables is also a chi-squared variable. If $Q_1 \sim \chi^2(k_1)$ and $Q_2 \sim \chi^2(k_2)$ are independent, then:
    $$
    Q_1 + Q_2 \sim \chi^2(k_1 + k_2)
    $$

## Key Applications in Statistics

The chi-squared distribution is the cornerstone of several essential statistical tests.

### 1. Chi-Squared Goodness-of-Fit Test

This test is used to determine whether an observed frequency distribution of a categorical variable differs from a theoretical (expected) distribution.
-   **Null Hypothesis ($H_0$)**: The observed data follows the expected distribution.
-   **Test Statistic**: The test is based on the chi-squared statistic, which measures the discrepancy between observed frequencies ($O_i$) and expected frequencies ($E_i$) across $c$ categories:
    $$
    \chi^2 = \sum_{i=1}^{c} \frac{(O_i - E_i)^2}{E_i}
    $$
    This statistic approximately follows a $\chi^2(c-1)$ distribution. A large $\chi^2$ value indicates a poor fit and leads to the rejection of the null hypothesis.

### 2. Chi-Squared Test for Independence

This test is used to determine whether there is a significant association between two categorical variables. It is often used with data presented in a **contingency table**.
-   **Null Hypothesis ($H_0$)**: The two variables are independent.
-   **Test Statistic**: The formula is the same as above, but the expected frequency for each cell in a table with $r$ rows and $c$ columns is calculated under the assumption of independence:
    $$
    E_{ij} = \frac{(\text{Total of row } i) \times (\text{Total of column } j)}{\text{Grand Total}}
    $$
    The resulting statistic is compared to a $\chi^2$ distribution with $(r-1)(c-1)$ degrees of freedom.

### 3. Confidence Intervals for Population Variance

For a sample of size $n$ drawn from a normally distributed population, the chi-squared distribution can be used to estimate the population variance $\sigma^2$. The sample statistic:
$$
\frac{(n-1)s^2}{\sigma^2} \sim \chi^2(n-1)
$$
where $s^2$ is the sample variance, follows a chi-squared distribution with $n-1$ degrees of freedom. This relationship allows for the construction of confidence intervals for $\sigma^2$.

## Relationship to Other Distributions

-   **Normal Distribution**: The chi-squared distribution is derived directly from the standard normal distribution.
-   **Exponential Distribution**: A chi-squared distribution with 2 degrees of freedom, $\chi^2(2)$, is an **exponential distribution** with a rate parameter of $\lambda = 1/2$. The [[Notes/2025/10/06/Porter-Thomas distribution\|Porter-Thomas distribution]] used in quantum physics is a special case of this.
-   **Gamma Distribution**: The chi-squared distribution is a special case of the gamma distribution. Specifically, $\chi^2(k)$ is equivalent to a Gamma($\alpha=k/2$, $\beta=2$) distribution.
-   **F-distribution and Student's t-distribution**: These two crucial distributions, used in ANOVA and t-tests respectively, are derived from ratios of random variables that involve the chi-squared distribution.

## Conclusion

The chi-squared distribution is a pillar of modern statistical analysis. Born from the simple concept of summing squared normal variables, it provides a powerful and versatile tool for hypothesis testing. It allows statisticians to move from raw, categorical data to robust conclusions about how well a model fits reality and whether different variables influence one another. Its deep connections to other key distributions underscore its central place in the theory of statistical inference.

