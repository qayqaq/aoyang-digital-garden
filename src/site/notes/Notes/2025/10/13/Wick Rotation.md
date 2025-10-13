---
{"dg-publish":true,"permalink":"/notes/2025/10/13/wick-rotation/","tags":["#Physics","#QuantumFieldTheory","#StatisticalMechanics","#TheoreticalPhysics","#Mathematics"]}
---

- The Wick rotation is a mathematical transformation, not a physical process, that treats time as a complex variable and rotates its axis by 90 degrees in the complex plane.
- This rotation is achieved by substituting real time $t$ with imaginary time $\tau$ through the relation $t \rightarrow -i\tau$.
- Its primary effect is to change the spacetime metric from the pseudo-Riemannian Minkowski metric ($ds^2 = -c^2dt^2 + d\mathbf{x}^2$) to a four-dimensional Euclidean metric ($ds_E^2 = c^2d\tau^2 + d\mathbf{x}^2$).
- This transformation converts oscillatory integrals found in quantum mechanics (e.g., path integrals with weight $e^{iS/\hbar}$) into decaying, real exponential integrals ($e^{-S_E/\hbar}$), which are mathematically better behaved and suitable for numerical methods like Monte Carlo simulations.
- It establishes a profound formal equivalence between quantum field theory in Euclidean spacetime and statistical mechanics, where the imaginary time duration corresponds to the inverse temperature.
  
#Physics #QuantumFieldTheory #StatisticalMechanics #TheoreticalPhysics #Mathematics

[[Wick rotation.canvas\|Wick rotation.canvas]]

# Wick Rotation

## 1. Introduction

The **Wick rotation**, named after physicist Gian-Carlo Wick, is a fundamental mathematical method used in theoretical physics, particularly in quantum field theory and statistical mechanics. It is not a physical transformation but rather a powerful calculational "trick" that simplifies problems by treating the time coordinate as a complex variable. The procedure involves rotating the contour of integration in the complex time plane by 90 degrees, effectively replacing real time with [[Notes/2025/10/13/Imaginary Time\|Imaginary Time]]. This transformation has profound consequences, most notably changing the geometry of spacetime from Minkowskian to Euclidean, which in turn converts difficult oscillatory integrals into more manageable real exponential integrals.

## 2. The Mathematical Procedure

The core of the Wick rotation is the analytic continuation of time into the complex plane. We consider the time variable $t$ to be a complex number. The rotation itself is a specific substitution:
$$
t \rightarrow -i\tau
$$
where $t$ is the conventional real time coordinate and $\tau$ is a new real parameter known as **imaginary time**.

This can be visualized in the complex plane. If the real axis represents ordinary time $t$, the Wick rotation corresponds to rotating the axis of integration counter-clockwise by an angle of $\pi/2$ (90 degrees) so that it aligns with the imaginary axis. For this rotation of the integration contour to be mathematically valid, the function being integrated must be analytic in the region swept by the rotation and must vanish sufficiently quickly at infinity, as guaranteed by Cauchy's integral theorem.

## 3. From Minkowski to Euclidean Spacetime

The most significant physical consequence of the Wick rotation is its effect on the metric of spacetime. In special relativity, events are described within a four-dimensional **Minkowski spacetime**, characterized by the metric:
$$
ds^2 = -(c\,dt)^2 + dx^2 + dy^2 + dz^2 = -(c\,dt)^2 + |d\mathbf{x}|^2
$$
The negative sign preceding the time component is crucial; it distinguishes time from space and gives spacetime a **pseudo-Riemannian** or **hyperbolic** geometry. This minus sign is the source of many mathematical complexities, including the potential for non-positive definite norms.

When we perform a Wick rotation, we substitute $dt \rightarrow -i\,d\tau$. The line element transforms as follows:
$$
ds^2 \rightarrow -(c(-i\,d\tau))^2 + |d\mathbf{x}|^2 = -c^2(i^2)(d\tau)^2 + |d\mathbf{x}|^2 = -c^2(-1)(d\tau)^2 + |d\mathbf{x}|^2
$$
This results in a new metric, known as the **Euclidean metric**:
$$
ds_E^2 = (c\,d\tau)^2 + |d\mathbf{x}|^2
$$
In this Euclidean spacetime, the time coordinate $(c\tau)$ and the three spatial coordinates are on equal footing. The metric is positive-definite, just like the familiar metric of three-dimensional Euclidean space. This simplification removes many of the difficulties associated with Minkowski space and makes calculations significantly more straightforward.

## 4. Applications and Physical Implications

### 4.1 Simplifying Path Integrals

In the Feynman path integral formulation of quantum mechanics, the probability amplitude for a process is a sum over all possible histories (paths), where each path is weighted by a complex phase factor $e^{iS/\hbar}$, where $S$ is the classical action.
$$
\text{Amplitude} = \int \mathcal{D}[\text{path}] \, e^{iS/\hbar}
$$
The imaginary exponent leads to rapid oscillations, making the integral mathematically ill-defined and numerically intractable (the "sign problem").

After a Wick rotation, the action $S$ transforms into the **Euclidean action** $S_E$, and the weighting factor becomes:
$$
e^{iS/\hbar} \quad \xrightarrow{\text{Wick Rotation}} \quad e^{-S_E/\hbar}
$$
The path integral is now over a real, decaying exponential. This new form is mathematically analogous to the Boltzmann factor $e^{-\beta E}$ in statistical mechanics. It can be interpreted as a probability weight, allowing the use of powerful stochastic sampling techniques like Monte Carlo methods to evaluate the integral. This is the basis for lattice quantum chromodynamics (Lattice QCD) and [[Notes/2025/10/13/Determinant Quantum Monte Carlo\|Determinant Quantum Monte Carlo]].

### 4.2 Connecting Quantum Field Theory and Statistical Mechanics

The Wick rotation establishes a deep and formal connection between quantum field theory (QFT) and classical statistical mechanics. The central objects of each theory become mathematically equivalent after the rotation:

| Quantum Field Theory (Minkowski) | Wick Rotation | Statistical Mechanics / QFT (Euclidean) |
| :--- | :---: | :--- |
| Generating Functional $\int \mathcal{D}\phi \, e^{iS[\phi]/\hbar}$ | $t \rightarrow -i\tau$ | Partition Function $Z = \int \mathcal{D}\phi \, e^{-S_E[\phi]/\hbar}$ |
| Time Evolution Operator $e^{-i\hat{H}t/\hbar}$ | $t \rightarrow -i\tau$ | Density Matrix Operator $e^{-\hat{H}\tau/\hbar} \equiv e^{-\beta \hat{H}}$ |

This correspondence allows concepts and techniques to be transferred between the two fields. For instance, phenomena like phase transitions from statistical mechanics have direct analogues in QFT, and powerful techniques like the renormalization group can be applied in both contexts. The duration of imaginary time evolution, $\tau$, is identified with the inverse temperature, $\beta = 1/(k_B T)$.

## 5. Conclusion

The Wick rotation is an elegant and indispensable mathematical tool in modern physics. By rotating the time axis into the complex plane, it transforms the hyperbolic geometry of Minkowski spacetime into a much simpler Euclidean geometry. This procedure tames the oscillatory behavior inherent in quantum mechanics, making path integrals well-defined and computationally accessible. Furthermore, it reveals a profound and fruitful connection between the quantum dynamics of fields and the thermal fluctuations of statistical systems. While it is a purely formal device, the Wick rotation provides a crucial bridge for both conceptual understanding and practical calculation, allowing physicists to solve problems that would otherwise be intractable.


