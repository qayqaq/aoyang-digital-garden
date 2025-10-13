---
{"dg-publish":true,"permalink":"/notes/2025/10/13/gibbs-paradox/","tags":["#statistical_mechanics","#thermodynamics","#quantum_mechanics","#paradox"]}
---

#statistical_mechanics #thermodynamics #quantum_mechanics #paradox
[[Gibbs Paradox.canvas\|Gibbs Paradox.canvas]]

*   **What It Is**: The Gibbs paradox is a famous inconsistency that arises from applying classical statistical mechanics to the thermodynamics of ideal gases.
*   **The Core Problem**: Classical theory incorrectly predicts that a significant increase in entropy occurs when two identical gases are mixed. This contradicts both experimental observation and the principles of thermodynamics, which state that mixing identical substances under the same conditions should result in zero entropy change.
*   **The Flawed Assumption**: The paradox stems from the classical assumption that individual particles of the same gas are fundamentally **distinguishable**. This leads to a massive overcounting of the system's microscopic states.
*   **The Resolution**: The paradox is resolved by incorporating the quantum mechanical principle of **indistinguishability**. Identical quantum particles are fundamentally indistinguishable, meaning that swapping two such particles does not create a new state.
*   **The Mathematical Fix**: The correction is implemented by dividing the classical [[Notes/2025/10/13/Partition Function\|Partition Function]] by $N!$ (the number of permutations of $N$ particles). This adjustment leads to the correct, **extensive** formula for entropy (the Sackur-Tetrode equation) and resolves the paradox.

# Gibbs Paradox

## Introduction

The **Gibbs paradox** is a foundational puzzle in statistical mechanics that reveals a deep-seated limitation of classical physics and highlights the necessity of a quantum mechanical description of matter. Named after Josiah Willard Gibbs, the paradox emerges from a simple thought experiment: the mixing of two gases.

When classical statistical mechanics is used to calculate the change in entropy upon mixing two identical gases, it predicts a non-zero increase in entropy. This result is counter-intuitive and thermodynamically incorrect, as the process of mixing two identical substances should be reversible and result in no change to the system's macroscopic state. The resolution of this paradox lies in the quantum mechanical concept of the **indistinguishability of identical particles**, a principle with no counterpart in the classical world.

## The Thought Experiment: Mixing Gases

To understand the paradox, we consider a box separated into two equal-volume chambers ($V$) by a removable partition. Both chambers are at the same temperature $T$ and pressure $P$.

### Case 1: Mixing Two Distinguishable Gases

First, let's imagine chamber A contains $N$ particles of an ideal gas A (e.g., Argon), and chamber B contains $N$ particles of a different ideal gas B (e.g., Neon).

1.  **Initial State**: The total initial entropy is the sum of the entropies of the two separate gases:
    $$
    S_{\text{initial}} = S_A(N, V, T) + S_B(N, V, T)
    $$
2.  **Mixing Process**: We remove the partition. The gases spontaneously mix and interdiffuse until each gas occupies the full volume $2V$.
3.  **Final State**: The final state is a uniform mixture of $N$ particles of gas A and $N$ particles of gas B in a total volume of $2V$. The final entropy is:
    $$
    S_{\text{final}} = S_A(N, 2V, T) + S_B(N, 2V, T)
    $$
4.  **Entropy Change**: The change in entropy, known as the **entropy of mixing**, is calculated as $\Delta S = S_{\text{final}} - S_{\text{initial}}$. Using the statistical mechanics formula for the entropy of an ideal gas, where entropy is proportional to $\ln V$, the change is:
    $$
    \Delta S = (S_A(2V) - S_A(V)) + (S_B(2V) - S_B(V)) = Nk_B \ln\left(\frac{2V}{V}\right) + Nk_B \ln\left(\frac{2V}{V}\right)
    $$
    $$
    \Delta S = 2Nk_B \ln 2
    $$
This result is positive ($\Delta S > 0$), which is physically correct. The mixing of two different gases is an irreversible process that increases the disorder (entropy) of the system.

### Case 2: Mixing Two Identical Gases (The Paradox)

Now, let's consider the crucial case where both chambers contain the **same** type of gas (e.g., Argon in both).

1.  **Initial State**: Chamber A has $N$ particles of gas A, and chamber B also has $N$ particles of gas A.
2.  **Mixing Process**: We remove the partition.
3.  **Final State**: The final state is simply $2N$ particles of gas A in a volume of $2V$ at temperature $T$.

**Physical Intuition**: From a thermodynamic perspective, removing the partition between two identical gases and then reinserting it is a completely reversible process. The macroscopic state of the system has not changed. Therefore, the change in entropy must be zero.
$$
\Delta S_{\text{identical}} = 0
$$

**The Paradoxical Calculation**: If we naively apply the same classical statistical mechanics formula used in Case 1, we are forced to treat the particles originally in chamber A as distinguishable from those in chamber B. The calculation proceeds identically, yielding the same incorrect, non-zero result:
$$
\Delta S_{\text{paradox}} = 2Nk_B \ln 2
$$
This is the **Gibbs paradox**: a direct contradiction between a seemingly rigorous theoretical calculation and fundamental thermodynamic principles.

## The Root of the Paradox: Distinguishability and Extensivity

The flaw lies in a core assumption of classical mechanics: that all particles are, in principle, **distinguishable**. Classical physics allows us to imagine "labeling" each particle and tracking its individual trajectory. This leads to an incorrect counting of the microscopic states (microstates) available to the system.

Specifically, swapping the positions of two identical particles is counted as a distinct microstate in the classical framework. This overcounting leads to a formula for entropy that is not **extensive**.

> An **extensive property** (like mass, volume, or entropy) is one that scales linearly with the size of the system. If you double the amount of substance, the property should also double.

The uncorrected classical entropy formula for an ideal gas is:
$$
S_{\text{classical}} = Nk_B \left[ \ln\left(V\left(\frac{2\pi mk_BT}{h^2}\right)^{3/2}\right) + \frac{3}{2} \right]
$$
This formula is not extensive. If we double the system size ($N \to 2N$, $V \to 2V$), the entropy does not simply double due to the $\ln V$ term. This failure of extensivity is the deep reason behind the paradox.

## The Resolution: Quantum Indistinguishability

The paradox is fundamentally resolved by [[Notes/2025/10/06/Foundational Principles of Quantum Mechanics\|quantum mechanics]], which posits that identical particles (e.g., two electrons, two helium atoms) are **fundamentally indistinguishable**. There is no conceivable experiment that can tell them apart or track them individually.

Therefore, a microstate in which two identical particles have been swapped is not a new state; it is the **exact same physical state**. The classical calculation overcounts the true number of distinct microstates by a factor of $N!$, which is the number of ways to permute $N$ particles.

### The Mathematical Correction

To fix the classical formulas, we must correct for this overcounting. This is achieved by dividing the total number of states, and thus the [[Notes/2025/10/13/Partition Function\|Partition Function]], by $N!$.

The corrected partition function for $N$ identical particles is:
$$
Z = \frac{1}{N!} z^N
$$
where $z$ is the single-particle partition function.

This correction factor carries through to the entropy. Using Stirling's approximation for the logarithm of the factorial ($\ln N! \approx N \ln N - N$), the corrected entropy formula becomes the celebrated **Sackur-Tetrode equation**:
$$
S = Nk_B \left[ \ln\left(\frac{V}{N}\left(\frac{2\pi mk_BT}{h^2}\right)^{3/2}\right) + \frac{5}{2} \right]
$$
This equation is now properly **extensive**, because the argument of the logarithm contains the intensive quantity $V/N$ (volume per particle).

### Resolving the Thought Experiment

With the correct, extensive Sackur-Tetrode equation, we can re-calculate the entropy change for mixing identical gases:
-   **Initial Entropy**: $S_{\text{initial}} = S(N, V) + S(N, V) = 2 \times S(N, V)$
-   **Final Entropy**: $S_{\text{final}} = S(2N, 2V)$

Since the entropy $S$ is now extensive, we know that $S(2N, 2V) = 2 \times S(N, V)$. Therefore:
$$
\Delta S = S_{\text{final}} - S_{\text{initial}} = S(2N, 2V) - 2S(N, V) = 2S(N, V) - 2S(N, V) = 0
$$
The paradox is resolved. The corrected formula correctly predicts zero entropy change, in perfect agreement with thermodynamics.

## Conclusion

The Gibbs paradox is more than a historical curiosity; it is a profound demonstration of the limits of classical intuition. It shows that a macroscopic property like entropy is deeply connected to the fundamental, quantum nature of matter. The resolution of the paradox—by acknowledging the indistinguishability of identical particles—was a major triumph for statistical mechanics and provided early, compelling evidence that the microscopic world operates by rules that are fundamentally different from our everyday classical experience.

