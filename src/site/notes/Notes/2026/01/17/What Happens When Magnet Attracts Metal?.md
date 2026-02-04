---
{"dg-publish":true,"permalink":"/notes/2026/01/17/what-happens-when-magnet-attracts-metal/"}
---

（待润色）

When you witness a magnet pulling a piece of iron, you are seeing one of the most profound "glitches" in classical physics. To understand why that piece of metal moves, we must dismantle our classical intuition and rebuild it using the tools of Dirac, Pauli, and Heisenberg.

## 1. The Paradox: Why the Lorentz Force is "Lazy"

In classical electromagnetism, the force exerted on a charge $q$ moving with velocity $\vec{v}$ in a magnetic field $\vec{B}$ is given by the Lorentz force law:
$$\vec{F}_{mag} = q(\vec{v} \times \vec{B})$$
By definition, this force is always perpendicular to the velocity vector ($\vec{F} \cdot \vec{v} = 0$). Since power is defined as the rate of doing work ($P = \vec{F} \cdot \vec{v}$), **the magnetic force performs zero work**.

Yet, when a magnet attracts a piece of metal, the metal clearly gains kinetic energy. If the magnetic force cannot do work, what is actually pulling the metal? The answer lies in the fact that magnetism is not merely a classical force, but a **quantum relativistic correction**.

## 2. The Dead End: The Bohr-van Leeuwen Theorem

Before we find the solution, we must prove that classical physics is incapable of producing magnetism. This is the **Bohr-van Leeuwen Theorem**.

Consider a system of $N$ electrons. The magnetic moment $\vec{\mu}$ is defined by the orbital motion of charges:
$$\vec{\mu} = \frac{q}{2} \vec{r} \times \vec{v} = \frac{q}{2m}(\vec{r} \times m\vec{v}) = \frac{q}{2m}\vec{L}$$
Crucially, the total magnetization in the $z$-direction is a linear function of the generalized velocities $\dot{q}_i$:
$$M_z = \sum_{i=1}^{3N} a_i(q_1, \dots, q_{3N}) \dot{q}_i$$
In an electromagnetic field, the Hamiltonian $H$ (total energy) is given by:
$$H = \sum_{i=1}^N \frac{(\vec{p}_i - q \vec{A})^2}{2m} + q V(q_1, \dots, q_N)$$
Using Hamilton’s equations of motion, we have $\dot{q}_i = \frac{\partial H}{\partial p_i}$. The thermal average of the magnetization $\langle M_z \rangle$ is calculated via the canonical partition function:
$$\langle M_z \rangle = \frac{\int dq_1 \dots dq_{3N} \int dp_1 \dots dp_{3N} M_z e^{-H/k_B T}}{\int dq_1 \dots dq_{3N} \int dp_1 \dots dp_{3N} e^{-H/k_B T}}$$
Let us focus on the momentum integral for a single term $a_i \dot{q}_i$. Since $a_i$ depends only on coordinates, we can pull it out and integrate over the momentum $p_i$:
$$\int_{-\infty}^{+\infty} dp_i \dot{q}_i e^{-H/k_B T} = \int_{-\infty}^{+\infty} dp_i \frac{\partial H}{\partial p_i} e^{-H/k_B T}$$
This integral is mathematically equivalent to integrating a total derivative. By recognizing that $\frac{\partial H}{\partial p_i} e^{-\beta H} = -\frac{1}{\beta} \frac{\partial}{\partial p_i} (e^{-\beta H})$ (where $\beta = 1/k_B T$), we have:
$$ \int_{H(p=-\infty)}^{H(p=+\infty)} dH e^{-H/k_B T} = \left[ -k_B T e^{-H/k_B T} \right]_{p_i=-\infty}^{p_i=+\infty}$$
Since the kinetic energy term $\frac{(p-qA)^2}{2m}$ goes to infinity as momentum $p \to \pm \infty$, the Boltzmann factor $e^{-H/k_B T}$ vanishes at the boundaries. Thus:
$$\left[ -k_B T e^{-H/k_B T} \right]_{-\infty}^{+\infty} = 0 - 0 = 0$$
**Result:** $\langle M \rangle = 0$. The physics is merciless: The vector potential $\vec{A}$ shifts the momentum, but since we integrate over all possible momenta from $-\infty$ to $+\infty$, this shift contributes nothing to the total integral. **Classical physics predicts that magnets cannot exist.**

## 3. Beyond the Schrödinger Equation

The Schrödinger equation is built upon the non-relativistic energy-momentum relation $E = \vec{p}^2/2m$. If we attempt to use the relativistic relation $E^2 = c^2\vec{p}^2 + m^2c^4$ by substituting quantum operators $E \to i\hbar \partial_t$ and $\vec{p} \to -i\hbar \nabla$, we obtain the **Klein-Gordon Equation**:
$$\frac{1}{c^2} \frac{\partial^2 \psi}{\partial t^2} - \nabla^2 \psi + \left( \frac{mc}{\hbar} \right)^2 \psi = 0$$
This equation can be written more compactly using the **d'Alembertian operator**, $\Box = \frac{1}{c^2}\frac{\partial^2}{\partial t^2} - \nabla^2$, which is the Minkowski spacetime generalization of the Laplacian operator:
$$\left(\Box + \left(\frac{mc}{\hbar}\right)^2\right) \psi = 0$$
However, when first proposed, the Klein-Gordon equation was nearly abandoned due to two significant conceptual problems that arose from interpreting $\psi$ as a single-particle wave function, analogous to its role in the Schrödinger equation.

On one hand, the relativistic energy-momentum relation is quadratic in energy, leading to two solutions: $E = \pm \sqrt{(pc)^2 + (mc^2)^2}$. The existence of **negative energy states** was deeply problematic. It implied that a particle could continuously radiate energy by transitioning to ever-lower negative energy levels, suggesting that no stable ground state existed for matter.

On the other hand, the wave function in quantum mechanics is used to construct a conserved probability current, $j^\mu = (\rho, \mathbf{j})$, where $\rho$ is the probability density. For the Schrödinger equation, the probability density $\rho = |\psi|^2$ is always non-negative. For the Klein-Gordon equation, the derived conserved density is:
$$\rho = \frac{i\hbar}{2mc^2} \left( \psi^* \frac{\partial \psi}{\partial t} - \psi \frac{\partial \psi^*}{\partial t} \right)$$
Because the equation is second-order in time, the values of $\psi$ and $\frac{\partial \psi}{\partial t}$ can be chosen independently at any given initial time. This allows for conditions where $\rho$ can be **negative**, which is nonsensical for a probability density. A particle cannot have a negative probability of being found somewhere.

These problems stem from the second-order nature of the time derivative. Dirac's goal was to find a new equation that was simultaneously **first-order in time** (like the Schrödinger equation) and **relativistically covariant**. The natural approach is to write a Hamiltonian linear in momentum with to-be-defined coefficients:
$$\hat{H} = c(\alpha_x \hat{p}_x + \alpha_y \hat{p}_y + \alpha_z \hat{p}_z) + \beta m c^2$$
where $\hat{p}_k = -i\hbar \frac{\partial}{\partial x_k}$ are the momentum operators. The corresponding wave equation is:
$$i\hbar \frac{\partial \psi}{\partial t} = \hat{H}\psi = \left( -i\hbar c \sum_{k=1}^3 \alpha_k \frac{\partial}{\partial x^k} + \beta m c^2 \right) \psi = (-i\hbar c \vec{\alpha} \cdot \nabla + \beta mc^2) \psi$$
For this equation to be relativistically consistent, any free-particle solution to it must also satisfy the relativistic energy-momentum relation (i.e., the Klein-Gordon equation). This requires that when the Dirac operator is applied twice ("squaring" the equation), it yields the Klein-Gordon operator:
$$(c\sum \alpha_i p_i + \beta mc^2)^2 = c^2 \sum p_i^2 + m^2 c^4$$
Expanding the left side (noting that $p_i$ commute with each other, but the coefficient matrices $\alpha_i, \beta$ do not necessarily commute):
$$c^2 \sum_i \alpha_i^2 p_i^2 + c^2 \sum_{i < j} \{\alpha_i, \alpha_j\} p_i p_j + mc^3 \sum_i \{\alpha_i, \beta\} p_i + \beta^2 m^2 c^4$$
Comparing the coefficients on both sides, we derive the algebraic requirements for $\alpha_i$ and $\beta$, known as the **Clifford Algebra**:
1. $\alpha_i^2 = I$
2. $\beta^2 = I$
3. $\{\alpha_i, \alpha_j\} = 0 \quad (i \neq j)$
4. $\{\alpha_i, \beta\} = 0$

To make the equation manifestly covariant under Lorentz transformations, we define the Gamma matrices $\gamma^\mu$:
- **$\gamma^0 = \beta$**
- **$\gamma^i = \beta \alpha_i$** ($i=1,2,3$)

Substituting these back, we obtain the concise covariant form:
$$(i \gamma^\mu \partial_\mu - \frac{mc}{\hbar}) \psi = 0,\quad \text{where } \partial_\mu = (\frac{1}{c}\partial_t, \nabla)$$
Using the properties of $\alpha_i$ and $\beta$, we can derive the core properties of $\gamma^\mu$:
- **Time component:** $(\gamma^0)^2 = \beta^2 = I$
- **Space components:** $(\gamma^i)^2 = (\beta \alpha_i)(\beta \alpha_i) = -\beta^2 \alpha_i^2 = -I$
- **Mixed terms ($\mu \neq \nu$):**
    $\{\gamma^0, \gamma^i\} = \beta (\beta \alpha_i) + (\beta \alpha_i) \beta = \alpha_i - \alpha_i = 0$
    $\{\gamma^i, \gamma^j\} = (\beta \alpha_i)(\beta \alpha_j) + (\beta \alpha_j)(\beta \alpha_i) = -\beta^2 \{\alpha_i, \alpha_j\} = 0$

Combining these results, the Gamma matrices satisfy the famous **Anti-commutation Relation**:
$$\{\gamma^\mu, \gamma^\nu\} = 2\eta^{\mu\nu} I$$
where $\eta^{\mu\nu} = \text{diag}(1, -1, -1, -1)$ is the Minkowski metric.

The smallest irreducible representation satisfying this algebra involves $4 \times 4$ matrices. We can deduce this by elimination:
- **1D (Scalar):** Impossible. Scalars commute, so they cannot satisfy anti-commutation relations like $\gamma^0\gamma^1 = -\gamma^1\gamma^0$ unless they are zero, but $\gamma^2 = \pm I$ forbids that.
- **2D:** We can find at most 3 anti-commuting matrices (the Pauli matrices $\sigma_x, \sigma_y, \sigma_z$). However, we need **4** anti-commuting matrices ($\gamma^0$ to $\gamma^3$).
- **3D:** Since $\text{Tr}(\gamma^\mu) = 0$ and $\gamma^2 = \pm I$, the eigenvalues must come in pairs of $+1$ and $-1$. This implies the dimension $n$ of the matrix must be **even**.
- **4D:** This is the first even dimension that can accommodate more than 3 anti-commuting matrices. In 4D space, we can construct up to 5 mutually anti-commuting matrices ($\gamma^0, \gamma^1, \gamma^2, \gamma^3$, and $\gamma^5$).

In 4D, the most common choice is the **Dirac Representation** (Standard Representation), which uses the $2 \times 2$ identity matrix $I$ and Pauli matrices $\sigma_i$:
$$\begin{aligned}\gamma^0 & = \begin{pmatrix} I & 0 \\ 0 & -I \end{pmatrix}, \quad \gamma^i = \begin{pmatrix} 0 & \sigma_i \\ -\sigma_i & 0 \end{pmatrix},\quad \\\gamma^i  & = \beta \alpha_i  = \begin{pmatrix} I & 0 \\ 0 & -I \end{pmatrix} \begin{pmatrix} 0 & \sigma_i \\ \sigma_i & 0 \end{pmatrix} = \begin{pmatrix} 0 & \sigma_i \\ -\sigma_i & 0 \end{pmatrix} \\ \sigma_x& =\left(\begin{array}{ll}
0 & 1 \\
1 & 0
\end{array}\right), \sigma_y=\left(\begin{array}{cc}
0 & -i \\
+i & 0
\end{array}\right),\sigma_z=\left(\begin{array}{ll}
1 & 0 \\
0 & -1
\end{array}\right) \end{aligned} $$

This is a profound result: the requirement for a linear, relativistic wave equation forces the wave function $\psi$ to have four components, which we now understand as describing the electron (spin up/down) and its antiparticle, the positron (spin up/down). Dirac attempted to solve the negative probability problem but inadvertently unlocked the door to spin. This demonstrates that **magnetism is not an added property of matter, but an inevitable consequence of spacetime symmetry.**

## 4. Coupling with Electromagnetic Field

Now we consider the case with an electromagnetic potential $A^\mu = (\Phi/c, \vec{A})$. We need to perform a local gauge transformation in the Dirac equation. **Momentum substitution:** Replace momentum $\vec{p}$ with the Kinetic Momentum: $\vec{p} \to \vec{p} - q\vec{A}$, where $\vec{A}$ is the magnetic vector potential. **Energy substitution:** Replace the energy operator $i\hbar \frac{\partial}{\partial t}$ with: $i\hbar \frac{\partial}{\partial t} \to i\hbar \frac{\partial}{\partial t} - q\Phi$, where $\Phi$ is the electric scalar potential. The equation becomes:
$$i\hbar \frac{\partial \psi}{\partial t} = [c \vec{\alpha} \cdot (\vec{p} - q\vec{A}) + \beta m c^2 + q\Phi] \psi$$
To handle 4D spacetime more intuitively, we usually write this in covariant form. Introducing the Gamma matrix definitions $\gamma^0 = \beta, \gamma^i = \beta \alpha_i$, and combining the 4-momentum operator $p_\mu = i\hbar \partial_\mu = (i\hbar \frac{1}{c}\partial_t, -i\hbar \nabla)$ with the 4-potential $A_\mu = (\Phi/c, -\vec{A})$, the equation can be rearranged as:
$$\gamma^0 (i\hbar \frac{1}{c} \partial_t - \frac{q\Phi}{c}) \psi + \vec{\gamma} \cdot (i\hbar \nabla + q\vec{A}) \psi - mc \psi = 0$$
Using the covariant derivative $D_\mu = \partial_\mu + \frac{iq}{\hbar} A_\mu$, it can be written in the minimalist form:
$$(i\hbar \gamma^\mu D_\mu - mc) \psi = 0\quad \text{or}\quad \gamma^\mu (p_\mu - qA_\mu) \psi = mc \psi$$
We now wish to solve this four-component spinor equation. The simple block form of the gamma matrices allows us to group the four components into pairs. Furthermore, in the non-relativistic limit, the rest energy $mc^2$ is the dominant term. We write the wavefunction as a combination of a "large component" $\phi$ and a "small component" $\chi$ (both are 2-component spinors), explicitly extracting the time evolution of the rest energy:
$$\psi(\vec{r}, t) = \begin{pmatrix} \phi(\vec{r}, t) \\ \chi(\vec{r}, t) \end{pmatrix} e^{-imc^2t/\hbar}$$
Applying the product rule to the time derivative on the left side:
$$i\hbar \frac{\partial \psi}{\partial t} = \left( i\hbar \frac{\partial}{\partial t} \begin{pmatrix} \phi \\ \chi \end{pmatrix} + mc^2 \begin{pmatrix} \phi \\ \chi \end{pmatrix} \right) e^{-imc^2t/\hbar}$$
Substituting this into the Dirac equation and using the matrix form in the standard Dirac representation, we cancel the exponential term on both sides to obtain:
$$i\hbar \frac{\partial}{\partial t} \begin{pmatrix} \phi \\ \chi \end{pmatrix} + mc^2 \begin{pmatrix} \phi \\ \chi \end{pmatrix} = c \begin{pmatrix} 0 & \vec{\sigma} \\ \vec{\sigma} & 0 \end{pmatrix} \cdot \vec{\pi} \begin{pmatrix} \phi \\ \chi \end{pmatrix} + \begin{pmatrix} mc^2 & 0 \\ 0 & -mc^2 \end{pmatrix} \begin{pmatrix} \phi \\ \chi \end{pmatrix} + q\Phi \begin{pmatrix} \phi \\ \chi \end{pmatrix}$$
where $\vec{\pi} = \vec{p} - q\vec{A}$ is the kinetic momentum. We decompose the above equation into two coupled equations:
$$\begin{aligned} & i \hbar \frac{\partial \phi}{\partial t}+m c^2 \phi=c(\vec{\sigma} \cdot \vec{\pi}) \chi+m c^2 \phi+q \Phi \phi \\ & i \hbar \frac{\partial \chi}{\partial t}+m c^2 \chi=c(\vec{\sigma} \cdot \vec{\pi}) \phi-m c^2 \chi+q \Phi \chi \end{aligned}$$
In the non-relativistic limit, the electron's kinetic and potential energies are much smaller than its rest energy, i.e., $|i\hbar \partial_t \chi| \ll |2mc^2\chi|$ and $|q\Phi \chi| \ll |2mc^2\chi|$. Thus, the equation for the small component approximates to:
$$2mc^2 \chi \approx c(\vec{\sigma} \cdot \vec{\pi})\phi \implies \chi \approx \frac{\vec{\sigma} \cdot \vec{\pi}}{2mc} \phi$$
This explains why $\chi$ is called the "small component": its magnitude is roughly $v/c$ times that of the large component. Substituting the expression for $\chi$ back into the equation for the large component $\phi$:
$$i\hbar \frac{\partial \phi}{\partial t} = \left[ \frac{(\vec{\sigma} \cdot \vec{\pi})^2}{2m} + q\Phi \right] \phi$$
Here lies the key to the emergence of spin. Using the Pauli matrix identity $(\vec{\sigma} \cdot \vec{A})(\vec{\sigma} \cdot \vec{B}) = \vec{A} \cdot \vec{B} + i\vec{\sigma} \cdot (\vec{A} \times \vec{B})$:
$$(\vec{\sigma} \cdot \vec{\pi})^2 = \vec{\pi} \cdot \vec{\pi} + i\vec{\sigma} \cdot (\vec{\pi} \times \vec{\pi})$$
We calculate the operator cross product $\vec{\pi} \times \vec{\pi}$ acting on a test function $f$:
$$(\vec{\pi} \times \vec{\pi})f = (\vec{p} - q\vec{A}) \times (\vec{p} - q\vec{A})f= (\vec{p} \times \vec{p} - q\vec{p} \times \vec{A} - q\vec{A} \times \vec{p} + q^2\vec{A} \times \vec{A})f$$
Since $\vec{p} \times \vec{p} = 0$ and $\vec{A} \times \vec{A} = 0$, the remaining terms are:
$$\begin{aligned}-q(\vec{p} \times \vec{A} & + \vec{A} \times \vec{p})f = -q \left[ (-i\hbar \nabla) \times (\vec{A}f) + \vec{A} \times (-i\hbar \nabla f) \right]\\&= i\hbar q \left[ (\nabla \times \vec{A})f - \vec{A} \times (\nabla f) + \vec{A} \times (\nabla f) \right]= i\hbar q (\nabla \times \vec{A})f = i\hbar q \vec{B} f\end{aligned}$$
Therefore:
$$(\vec{\sigma} \cdot \vec{\pi})^2 = \vec{\pi}^2 + i\vec{\sigma} \cdot (i\hbar q \vec{B}) = \vec{\pi}^2 - \hbar q \vec{\sigma} \cdot \vec{B}$$
Finally, we have fully derived the Pauli Equation, which explicitly includes the Zeeman term $U = -\vec{\mu} \cdot \vec{B}$:
$$i\hbar \frac{\partial \phi}{\partial t} = \left[ \frac{(\vec{p}-q\vec{A})^2}{2m} + q\Phi - \frac{q\hbar}{2m} \vec{\sigma} \cdot \vec{B} \right] \phi$$
Clearly, an extra term has appeared in the Hamiltonian:
$$H = \frac{(\vec{p}-q\vec{A})^2}{2m} + q\Phi - \frac{q\hbar}{2m} \vec{\sigma} \cdot \vec{B}$$
This is the origin of spin. If we hadn't introduced the $\vec{\sigma}$ matrices (i.e., the Spin-0 Klein-Gordon case), the kinetic operator term would simply be $\vec{\pi}^2$. This term would not produce a linear coupling with the magnetic field $\vec{B}$, degenerating instead into the standard electromagnetic coupling Hamiltonian for a spinless particle: $H_{Spin-0} = \frac{(\vec{p}-q\vec{A})^2}{2m} + q\Phi$. It is precisely because the relativistic covariance of the electron wavefunction requires a matrix structure that the non-commutativity of $\vec{\pi}$ is transformed into a magnetic energy term. In simple terms: introducing the $\vec{\sigma}$ matrix mathematically adds an "internal axis of rotation" to the particle. Without it, the particle is a completely "isotropic" point in space. The $\vec{\sigma}$ matrix defines the non-commutativity of operators; in a Spin-0 world, the three components of momentum $\pi_x, \pi_y, \pi_z$ do not commute in a magnetic field, but their effect is "external" (changing the particle's trajectory). Introducing the $\vec{\sigma}$ matrix directly couples this non-commutativity (the magnetic field strength $\vec{B}$) to the internal dimensions of the wavefunction.

## 5. Universal Covering between SU2 and SO3

We have already observed the "emergence" of spin from the dynamical level. However, as an intrinsic property, spin should theoretically not require an external electromagnetic field to manifest; fundamentally, its existence must be linked to symmetry and transformation. Why must the wavefunction be operated on by $\vec{\sigma}$ matrices? Why is it a two-component spinor? This requires us to delve into the kinematic underpinnings—specifically, the **group-theoretical basis of spacetime symmetry**. Even without considering electromagnetic fields, as a physical object, when we rotate the laboratory coordinate system by an angle $\theta$, the electron's wavefunction $\psi$ must inevitably change. It is precisely this "transformation rule under rotation" that defines spin. Before diving into the physics, let us briefly introduce the most important groups: SU(2) and SO(3). These are Lie groups and hold an extremely important place in physics.

The basic definition of SU(2) is:
$$\begin{aligned} \mathrm{SU}(2) & \equiv\left\{U\left|U \in \mathrm{GL}(2, \mathbb{C}), U^{\dagger} U=1_{2 \times 2},|U|=1\right\}\right. \\  & \equiv\left\{\left[\begin{array}{cc} a & b \\ -b^* & a^* \end{array}\right]\left|a, b \in \mathbb{C},|a|^2+|b|^2=1\right\}\right. \\ & \equiv\left\{\left.U(\vec{n}, \omega)=e^{i \frac{\omega}{2} \vec{n} \cdot \vec{\sigma}} \right\rvert\, \omega \in[0, \pi], \vec{n} \text { is the set of all 3D real unit vectors }\right\} \end{aligned}$$
If we use real parameters $x_i\in\mathbb{R}$ and let $a=x_4+ix_3, b=x_2+ix_1$ to describe it: $$\begin{aligned}U=\left[\begin{array}{cc}a & b \\-b^* & a^*\end{array}\right]=\left[\begin{array}{cc}x_4+i x_3 & x_2+i x_1 \\-x_2+i x_1 & x_4-i x_3\end{array}\right]\end{aligned}$$The constraint becomes $x_1^2+x_2^2+x_3^2+x_4^2=1$, indicating that SU(2) as a manifold is $S^3$, a 3-sphere (hypersphere). Its $T^2$-fibration is described as:
$$\left\{\begin{array}{l} x_1=\sin \theta \cos \varphi \\ x_2=\sin \theta \sin \varphi \end{array},\left\{\begin{array}{l} x_3=\cos \theta \cos \chi \\ x_4=\cos \theta \sin \chi \end{array}, \text { where } \theta \in[0, \pi / 2] ; \varphi, \chi \in[0,2 \pi]\right. \text {. }\right.$$
This can be described using two opposing conical surfaces for $\chi, \varphi$ and an axis $\theta$. At $\theta=0$ or $\theta=\pi/2$, one parameter becomes degenerate. It can also be described as a "doughnut" (solid torus) that scales with $\theta$, causing a parameter to degenerate at the endpoints. When $\theta=0$, the doughnut is a circle with zero width; only $\chi$ is valid along the circle, while $\varphi$ is invalid because the circle has no width. When $\theta=\pi/2$, the doughnut becomes a sphere with no hole, so $\chi$ becomes invalid and only $\varphi$ is effective.

The spherical coordinate system description is:
$$\text { For } \omega \in[0,2 \pi], \theta \in[0, \pi], \varphi \in[0,2 \pi] \text { we have }\left\{\begin{array}{l} x_1=\sin \frac{\omega}{2} \sin \theta \cos \varphi \\ x_2=\sin \frac{\omega}{2} \sin \theta \sin \varphi \\ x_3=\sin \frac{\omega}{2} \cos \theta \\ x_4=\cos \frac{\omega}{2} \end{array}\right.$$
SU(2) can also be expressed by Pauli matrices:
$$U=\left[\begin{array}{cc} x_4+i x_3 & x_2+i x_1 \\ -x_2+i x_1 & x_4-i x_3 \end{array}\right]=x_4 1_{2 \times 2}+i x_1 \sigma_1+i x_2 \sigma_2+i x_3 \sigma_3 .$$
Combining this further with spherical coordinates, we have:
$$\begin{aligned}U(\vec{n}, \omega)&=e^{i \frac{\omega}{2} \vec{n} \cdot \vec{\sigma}}=1_{2 \times 2} \cos \frac{\omega}{2}+i n^a \sigma_a \sin \frac{\omega}{2} \\ \vec{n}&=(\sin \theta \cos \varphi, \sin \theta \sin \varphi, \cos \theta) ; \omega \in[0,2 \pi], \theta \in[0, \pi], \varphi \in[0,2 \pi] . \end{aligned}$$
The basic definition of SO(3) is:
$$\begin{aligned}\mathrm{SO}(3)& \equiv\left\{\mathcal{R}\left|\mathcal{R} \in \mathrm{GL}(3, \mathbb{R}), \mathcal{R}^{\mathrm{T}} \mathcal{R}=1_{3 \times 3},|\mathcal{R}|=1\right\}\right.\\ &\equiv\left\{\begin{array}{l|l} \mathcal{R}(\vec{\omega}) & \begin{array}{l} \vec{\omega}=\omega \vec{n}, \vec{n}=(\cos \varphi \sin \theta, \sin \varphi \sin \theta, \cos \theta) \\ \omega \in[0, \pi], \theta \in[0, \pi], \varphi \in[0,2 \pi] \end{array} \end{array}\right\} . \end{aligned}$$
SO(3) is more intuitive; it represents the rotation operations we can see and touch. As a manifold, SO(3) can be viewed as a solid ball of radius $\pi$ formed by the endpoints of $\vec{\omega}$ with antipodal identification. Its abstraction lies in this antipodal identification. Although its origin is the simple fact that rotating $180^\circ$ counter-clockwise around a fixed axis is the same as rotating $180^\circ$ clockwise, this antipodal identification results in the solid ball being a connected manifold but _not_ a simply connected one (i.e., not every closed curve or loop in the space can be continuously shrunk to a point). The solid ball with antipodal identification has a name: Real Projective Space of 3 dimensions, denoted as $\mathbb{R}P^3$.

Mathematically, a **representation** of a group $G$ on a vector space $V$ is a **homomorphism** from the group $G$ to the general linear group $GL(V)$ (the group of all invertible transformations on $V$): $\forall g_1, g_2 \in G, \quad D(g_1 g_2) = D(g_1)D(g_2)$. For Lie groups, the map is also required to be continuous. **Projective representations** arise because, in quantum mechanics, physical states are described by **rays** in Hilbert space (i.e., $|\psi\rangle$ and $e^{i\alpha}|\psi\rangle$ represent the same physical state). Therefore, the group multiplication law only needs to hold up to a phase factor:
$$D(g_1)D(g_2) = \omega(g_1, g_2) D(g_1 g_2)$$
where $\omega(g_1, g_2)$ is a complex number with modulus 1, called the **group exponent**. Bargmann's Theorem (1954) provides a rigorous mathematical framework for projective representations: for a Lie group $G$ satisfying $H^2(\mathfrak{g}, \mathbb{R})=0$ (including SO(3) and the Lorentz group), all continuous projective unitary representations can be "lifted" to ordinary unitary representations of a central extension group $\tilde{G}$. For SO(3), where the "phase ambiguity" cannot be removed simply, we solve this by finding its **Universal Covering Group**, SU(2), and converting the projective representation of SO(3) into an ordinary representation of SU(2).

The concept of the universal covering group introduced here highlights the profound connection between SO(3) and SU(2). In topology, the universal covering space $\tilde{X}$ of a space $X$ is like an "upgraded version" of it, possessing two core features: **Simply Connectedness** (all loops in $\tilde{X}$ can be shrunk to a point; no topological holes) and **Local Isomorphism** (in local regions, $\tilde{X}$ looks exactly like $X$, but globally $\tilde{X}$ is often "larger" and covers $X$ in an $n:1$ manner).

Why do SU(2) matrices generate SO(3) rotations? Here is a classic construction method. We map a vector $\mathbf{x} = (x, y, z)$ in 3D space to a second-order **traceless Hermitian matrix** $X$:
$$X = x\sigma_1 + y\sigma_2 + z\sigma_3 = \begin{pmatrix} z & x-iy \\ x+iy & -z \end{pmatrix}$$
(where $\sigma_i$ are the Pauli matrices). Note that $\det(X) = -(x^2 + y^2 + z^2) = -\|\mathbf{x}\|^2$. Let a matrix $U$ in SU(2) act on $X$ via the following transformation: $X' = U X U^\dagger$. Since $U$ is unitary and has a determinant of 1, this transformation preserves the tracelessness and Hermiticity of $X$, and **preserves the determinant**: $\det(X') = \det(U X U^\dagger) = \det(X)$. This means $\|\mathbf{x}'\|^2 = \|\mathbf{x}\|^2$, i.e., the transformation preserves the length of the vector, so it describes a **3D rotation**. Observing the transformation formula $X' = U X U^\dagger$, if we replace $U$ with $-U$: $(-U) X (-U)^\dagger = (-1)^2 U X U^\dagger = U X U^\dagger$, we find that **$U$ and $-U$ produce exactly the same rotation effect**. This is the algebraic root of the 2:1 covering: every rotation in SO(3) corresponds to two points in SU(2). This explains why rotating by $2\pi$ does not return to the origin (in SU(2), it has only traveled half a circle), while rotating by $4\pi$ is required to return to the origin (completing a full circle in SU(2)). That is to say, SO(3) itself has a "hole" (its fundamental group is $\mathbb{Z}_2$), while SU(2) (i.e., $S^3$) is simply connected (fundamental group is 0) and has no topological holes.

The second condition of the universal cover, local consistency, leads to another major feature of SU(2) and SO(3): they are locally isomorphic near the identity element. This means that if you look only at "infinitesimal" rotations, or rotate only a tiny bit, the two groups are exactly the same. It is only when you rotate a large amount (e.g., $2\pi$) to explore the "full picture" of the group that you discover they are different (one returns to the start, the other goes to $-I$). Mathematically speaking, this is because they possess the exact same **Lie Algebra**, i.e., an isomorphism of the tangent spaces at the identity: $\mathfrak{su}(2) \cong \mathfrak{so}(3)$. From solving the Schrödinger equation, we know that the 3 generators of SO(3) are $J_x, J_y, J_z$ (corresponding to infinitesimal rotations about the x, y, z axes), and their commutation relations are: $[J_i, J_j] = i \epsilon_{ijk} J_k$. This formula defines the essence of 3D rotation; the so-called generators form a basis for the Lie algebra.

For the SU(2) group, let us now solve for its generators. Assume an infinitesimal transformation:
$$U(\epsilon) = I - i \epsilon S$$
For this to belong to SU(2), there is a unitarity constraint: $(I + i\epsilon S^\dagger)(I - i\epsilon S) = I \implies I - i\epsilon(S - S^\dagger) = I \implies S = S^\dagger$. Thus, $S$ must be a Hermitian matrix, which is physically observable. There is also a special constraint: using the formula $\det(e^A) = e^{\text{Tr}(A)}$, we have $\det(U) = \det(e^{-i\epsilon S}) = e^{-i\epsilon \text{Tr}(S)} = 1 \implies \text{Tr}(S) = 0$. So $S$ must be a traceless matrix. The matrices that fit these conditions are exactly the Pauli matrices $\sigma_x, \sigma_y, \sigma_z$, which form a complete **basis** for the Lie algebra $\mathfrak{su}(2)$. Thus, the generator $S$ must be proportional to $\sigma$. Since $[\sigma_i, \sigma_j] = 2i \epsilon_{ijk} \sigma_k$, we find this differs from $[L_i, L_j] = i \epsilon_{ijk} L_k$ by only a factor of $\frac{1}{2}$. This already demonstrates that the Lie algebras of SU(2) and SO(3) are isomorphic. If we take $S=\frac{1}{2}\sigma$, it becomes the standard $[S_i, S_j] = i \epsilon_{ijk} S_k$, exactly the same commutation relations as $J$. This gives us a self-consistent theory of angular momentum, where in the physical world, total angular momentum $L =J + S$ exists. If spin $S$ is to qualify as "angular momentum" and be additive with $J$ to form a conserved quantity, $S$ must follow the exact same algebraic rules as $J$. Since orbital angular momentum $J = \mathbf{r} \times \mathbf{p}$ is defined by spatial coordinates and its commutation relations are fixed (derived from the commutation of $x$ and $p$), we have no choice but to let $S=\frac{1}{2}\sigma$. Beyond theoretical consistency, real-world experimental results confirm this: when we perform the **Stern-Gerlach experiment**, measuring the deflection of electrons in a magnetic field, the measured physical values are **$\pm \frac{1}{2}\hbar$**. This directly proves that the operator $S$ representing the physical observable must have eigenvalues of $\pm 1/2$. Mathematically, only the matrix $\frac{1}{2}\sigma_z$ has eigenvalues of $\pm 1/2$ (since the eigenvalues of $\sigma_z$ are $\pm 1$).

Returning to representations: for Lie groups, a useful property of generators is that any finite transformation $D(\theta)$ can be obtained from the **generator** $J$ via the exponential map. If $J$ is an element of the Lie algebra $\mathfrak{g}$, then elements of the group can be written as:
$$D(\theta) = \exp(-i \theta \mathbf{n} \cdot \mathbf{J})$$
Here $\mathbf{J}$ is the angular momentum operator (matrix) we discussed. Note that this expression involves a common "abuse of notation" or shorthand in physics. Strictly speaking, the exponential map $\exp$ maps abstract Lie algebra elements to abstract Lie group elements. However, the physical formula $D(\theta) = \exp(-i \theta \mathbf{n} \cdot \mathbf{J})$ is actually an operation within the representation space (matrix space). Since $\mathbf{J}$ here is the matrix representation of the generator, the result $D(\theta)$ is naturally the matrix representation of the group element.

Whether we are dealing with SO(3) or SU(2), their **Lie algebras are isomorphic**. This means they share the same set of generator commutation relations: $[J_i, J_j] = i \epsilon_{ijk} J_k$ (taking $\hbar=1$). We want to find all finite-dimensional irreducible representations allowed by this set of algebraic rules. Define the ladder operators:
$$J_\pm = J_x \pm i J_y$$
Introduce the eigenstates $|j, m\rangle$ of $J_z$ such that:
$$J_z |j, m\rangle = m |j, m\rangle,\quad \mathbf{J}^2 |j, m\rangle = \lambda |j, m\rangle$$
Calculating the commutator:
$$[J_z, J_\pm] = [J_z, J_x] \pm i[J_z, J_y] = i J_y \pm i(-i J_x) = \pm (J_x \pm i J_y) = \pm J_\pm$$
This implies $J_\pm$ act as "ladders" for the eigenvalues:
$$J_z (J_\pm |j, m\rangle) = (J_\pm J_z + [J_z, J_\pm]) |j, m\rangle = (m \pm 1) (J_\pm |j, m\rangle)$$
If $m$ is an eigenvalue, then $m \pm 1$ are also eigenvalues. However, since we are looking for finite-dimensional representations, the spectrum of eigenvalues must have an upper bound $m_{max}$ and a lower bound $m_{min}$.
$$J_+ |j, m_{max}\rangle = 0,\quad J_- |j, m_{min}\rangle = 0$$
Using the operator identity $J_- J_+ = \mathbf{J}^2 - J_z^2 - J_z$ acting on the highest weight state $|j, m_{max}\rangle$:
$$0 = (\lambda - m_{max}^2 - m_{max}) |m_{max}\rangle \implies \lambda = m_{max}(m_{max} + 1)$$
For convenience, we label the maximum weight as $j$, i.e., $m_{max} \equiv j$. So the eigenvalue of the Casimir operator is $j(j+1)$. Similarly, using $J_+ J_- = \mathbf{J}^2 - J_z^2 + J_z$ acting on the lowest weight state $|j, m_{min}\rangle$:
$$0 = (j(j+1) - m_{min}^2 + m_{min}) |m_{min}\rangle$$
Solving the equation $m_{min}^2 - m_{min} - j(j+1) = 0$, we get two solutions:
$$m_{min} = -j \quad \text{or} \quad m_{min} = j+1$$
Since $m_{min} \le m_{max} = j$, we must have **$m_{min} = -j$**. Climbing from $m_{min} = -j$ to $m_{max} = j$ by adding 1 each step, we must reach the top in an integer number of steps $k$:
$$m_{max} - m_{min} = j - (-j) = 2j = k \quad (k \in \mathbb{Z})\quad\Longrightarrow\quad j=\frac{k}{2}$$
We arrive at the conclusion that, based solely on the Lie algebra structure, the allowed values for $j$ are **$0, 1/2, 1, 3/2, 2 \cdots$**. However, the Lie algebra structure is only a local property. We must now test these results against the **global group structure**. The core criterion for this test is **single-valuedness**: If we transform a group element along a closed path back to the starting point (the identity), its representation matrix must also return to the identity matrix (for an ordinary representation). SO(3) is the rotation group in 3D space. Rotating by $2\pi$ ($360^\circ$) around any axis (say, the $z$-axis) restores physical space completely: $R_z(2\pi) = R_z(0) = \mathbf{1}$, which is the group identity. For an ordinary representation $D$ of SO(3), it must satisfy: $D(R_z(2\pi)) = D(\mathbf{1}) = I$ (the identity matrix). Substituting the formula derived from the Lie algebra, where $J_z$ is diagonal in the $z$-basis with diagonal elements $m$: $D(2\pi) = \exp(-i 2\pi J_z) = \text{diag}(e^{-i 2\pi m}, \dots)$. To make this matrix equal to the identity $I$, every diagonal element must be 1: $e^{-i 2\pi m} = 1 \implies m \in \mathbb{Z}$. If $j$ is an integer ($0, 1, \dots$), then $m$ is an integer, and the condition is met. However, if $j$ is a half-integer ($1/2, 3/2, \dots$), then $m$ is a half-integer, and $e^{-i 2\pi m} = -1 \neq 1$. Therefore, half-integer spins are strictly forbidden in ordinary representations of SO(3).

However, the geometric structure of SU(2) is different from SO(3). It is the Universal Covering Group of SO(3) (a 2:1 cover). In SU(2), the parameter $\theta = 2\pi$ corresponds not to the identity element, but to $U(2\pi)=-I\neq I$; only a rotation of $4\pi$ corresponds to the identity element. We find that the behavior of $D(2\pi)$ perfectly matches the behavior of the SU(2) group itself. We have effectively obtained an instance of Bargmann's Theorem on SO(3) and SU(2): the projective representations of the non-simply connected Lie group SO(3) are equivalent to the ordinary representations of its universal covering group SU(2). The final mapping relationship is:

| **Spin j**                          | **In Lie Algebra** | **In SU(2)**                                                     | **In SO(3)**                       | **Physical Particle**      |
| ----------------------------------- | ------------------ | ---------------------------------------------------------------- | ---------------------------------- | -------------------------- |
| **Integer <br>($0, 1, \dots$)**     | Exists             | **Ordinary Rep.** (but not faithful, cannot distinguish $\pm I$) | **Ordinary Rep.**                  | Bosons (Photons, etc.)     |
| **Half-Integer <br>($1/2, \dots$)** | Exists             | **Ordinary Rep.** (Faithful Rep.)                                | **Projective Rep.** (Multi-valued) | Fermions (Electrons, etc.) |

"Spin" is able to "emerge" from this abstract mathematical structure because quantum mechanics defines "physical state" more leniently than classical mechanics, thereby releasing topological degrees of freedom that were masked by classical physics.
- **Symmetry (Root):** The universe possesses rotational symmetry, leading to the existence of the Lie algebra $\mathfrak{so}(3) \cong \mathfrak{su}(2)$.
- **Quantization (Opportunity):** The nature of probability waves allows for "projective representations," enabling the "half-integer parts" forbidden by classical physics in the Lie algebra to survive.
- **Intrinsic Nature (Formation):** These surviving half-integer representations cannot correspond to any spatial motion, and thus can only be interpreted as the particle's innate **intrinsic angular momentum**.

Now let us specifically calculate what the representations are for different $j$. We use the exponential map:
$$D^{(j)}(\hat{n}, \theta) = \sum_{k=0}^\infty \frac{(-i\theta)^k}{k!} (\hat{n} \cdot \mathbf{J}^{(j)})^k$$
where $\hat{n}$ is the rotation axis unit vector and $\theta$ is the rotation angle.

Simplest case: $j=0$ scalar representation. Dimension $d=2(0)+1=1$. The basis has only one state $|0,0\rangle$. Since $m$ can only be 0, the generator $J_z = [0]$. The ladder operators acting on the highest/lowest weight states are 0, so $J_+ = [0], J_- = [0]$, and thus $J_x = 0, J_y = 0, J_z = 0$. The exponential map gives the representation $D(\theta) = e^{-i\theta \mathbf{n} \cdot \mathbf{0}} = 1$, also known as the trivial representation. This is a scalar; no matter how you rotate, the value is always multiplied by 1, remaining unchanged.

When $j=\frac{1}{2}$, the dimension is $2j+1=2$. We already know the generator is $\mathbf{J}=\frac{1}{2} \sigma \Longrightarrow \hat{n} \cdot \mathbf{J}=\frac{1}{2}(\hat{n} \cdot \sigma)$. To calculate higher powers of $(\hat{n} \cdot \mathbf{J})$, recall the property of Pauli matrices: $(\hat{n} \cdot \vec{\sigma})^2 = I$ (Identity matrix). Thus, the power law for generators is:
$$(\hat{n} \cdot \mathbf{J})^2 = \left(\frac{1}{2} \hat{n} \cdot \vec{\sigma}\right)^2 = \frac{1}{4} (\hat{n} \cdot \vec{\sigma})^2 = \frac{1}{4} I,\quad (\hat{n} \cdot \mathbf{J})^3 = (\hat{n} \cdot \mathbf{J})^2 (\hat{n} \cdot \mathbf{J}) = \frac{1}{4} (\hat{n} \cdot \mathbf{J})$$
The general term formula is:
$$\begin{aligned}(\hat{n} \cdot \mathbf{J})^{2k} &= (\frac{1}{4})^k I = (\frac{1}{2})^{2k} I  \\  (\hat{n} \cdot \mathbf{J})^{2k+1} &= (\frac{1}{2})^{2k} (\hat{n} \cdot \mathbf{J}) = (\frac{1}{2})^{2k+1} (\hat{n} \cdot \vec{\sigma}) \end{aligned}$$
Summing the series by splitting the exponential series into even and odd parts:
$$\begin{aligned} D^{(1/2)} &= \sum_{k=0}^\infty \frac{(-i\theta)^k}{k!} (\hat{n} \cdot \mathbf{J})^k \\ &= \underbrace{\sum_{m=0}^\infty \frac{(-i\theta)^{2m}}{(2m)!} \left(\frac{1}{2}\right)^{2m} I}_{\text{Even terms}} + \underbrace{\sum_{m=0}^\infty \frac{(-i\theta)^{2m+1}}{(2m+1)!} \left(\frac{1}{2}\right)^{2m+1} (\hat{n} \cdot \vec{\sigma})}_{\text{Odd terms}} \end{aligned}$$
Even term coefficient: $\sum \frac{(-1)^m}{(2m)!} (\frac{\theta}{2})^{2m} = \cos(\frac{\theta}{2})$. Odd term coefficient: $-i \sum \frac{(-1)^m}{(2m+1)!} (\frac{\theta}{2})^{2m+1} = -i \sin(\frac{\theta}{2})$. Finally, we get:
$$\boxed{D^{(1/2)}(\hat{n}, \theta) = \cos\left(\frac{\theta}{2}\right) I - i \sin\left(\frac{\theta}{2}\right) (\hat{n} \cdot \vec{\sigma})}$$
This is the representation for $j=1/2$. It maps rotation operations to **$2 \times 2$ complex matrices**. **Checking $2\pi$:** Substitute $\theta=2\pi$, $\cos(\pi)=-1, \sin(\pi)=0$. The result is $-I$.

When $j=1$, the dimension is $2j+1=3$. We need $3 \times 3$ matrices. In the angular momentum basis defined in physics (Cartesian basis), the generators satisfy $(J_k)_{ab} = -i \epsilon_{kab}$. For example, the generator for rotation around the $z$-axis, $J_z$:
$$J_z = \begin{pmatrix} 0 & -i & 0 \\ i & 0 & 0 \\ 0 & 0 & 0 \end{pmatrix}$$
For an arbitrary axis $\hat{n}$, let matrix $K = \hat{n} \cdot \mathbf{J}$. Calculating powers of $J_z$ directly (other directions are similar):
$$J_z^2 = \begin{pmatrix} 0 & -i & 0 \\ i & 0 & 0 \\ 0 & 0 & 0 \end{pmatrix} \begin{pmatrix} 0 & -i & 0 \\ i & 0 & 0 \\ 0 & 0 & 0 \end{pmatrix} = \begin{pmatrix} 1 & 0 & 0 \\ 0 & 1 & 0 \\ 0 & 0 & 0 \end{pmatrix} \quad (\text{Note: This is not } I)$$
$$J_z^3 = J_z^2 \cdot J_z = \begin{pmatrix} 1 & 0 & 0 \\ 0 & 1 & 0 \\ 0 & 0 & 0 \end{pmatrix} \begin{pmatrix} 0 & -i & 0 \\ i & 0 & 0 \\ 0 & 0 & 0 \end{pmatrix} = \begin{pmatrix} 0 & -i & 0 \\ i & 0 & 0 \\ 0 & 0 & 0 \end{pmatrix} = J_z$$
We find a pattern: for $j=1$ generators, they satisfy the characteristic equation **$(\hat{n} \cdot \mathbf{J})^3 = (\hat{n} \cdot \mathbf{J})$**. This means: Odd terms ($k=1, 3, 5 \dots$): $(\hat{n} \cdot \mathbf{J})^k = (\hat{n} \cdot \mathbf{J})$; Even terms ($k=2, 4, 6 \dots$): $(\hat{n} \cdot \mathbf{J})^k = (\hat{n} \cdot \mathbf{J})^2$; $k=0$ term: $I$ (Identity matrix). Expanding the Taylor series again, but this time we must separate $I$ because $J^2 \neq I$.
$$D^{(1)} = I + \sum_{\text{odd } k} \frac{(-i\theta)^k}{k!} (\hat{n} \cdot \mathbf{J}) + \sum_{\text{even } k \ge 2} \frac{(-i\theta)^k}{k!} (\hat{n} \cdot \mathbf{J})^2$$
Odd term coefficient: $-i(\theta - \frac{\theta^3}{3!} + \dots) = -i \sin\theta$. Even term coefficient: $(\frac{-\theta^2}{2!} + \frac{\theta^4}{4!} - \dots) = \cos\theta - 1$. Result:
$$\boxed{D^{(1)}(\hat{n}, \theta) = I - i \sin\theta (\hat{n} \cdot \mathbf{J}) + (\cos\theta - 1) (\hat{n} \cdot \mathbf{J})^2}$$
This is the representation for $j=1$ (Rodrigues' rotation formula in physics form). It maps rotation operations to **$3 \times 3$ real matrices** (although $J$ contains $i$, $i \cdot J$ is a real matrix). **Checking $2\pi$:** Substitute $\theta=2\pi$, $\sin(2\pi)=0, \cos(2\pi)=1$, $D^{(1)} = I - 0 + (1-1)(\dots) = I$.

Generally, we can establish generators and representations for all $j$. The construction of generators for all $j$ relies on three core matrix element formulas for angular momentum operators in quantum mechanics. As long as we have these three formulas, we can write out matrices for $j=0, 3/2, 2$ or even $j=100$. First, $J_z$ is a diagonal matrix:
$$\langle j, m' | J_z | j, m \rangle = m \delta_{m'm}$$
Then $J_+$ (raising operator) is a superdiagonal matrix:
$$\langle j, m+1 | J_+ | j, m \rangle = \sqrt{j(j+1) - m(m+1)}$$
$J_-$ (lowering operator) is a subdiagonal matrix: It is the transpose of $J_+$ (in the real case). And $J_x$ and $J_y$ are composed of $J_\pm$:
$$J_x = \frac{1}{2}(J_+ + J_-), \quad J_y = \frac{1}{2i}(J_+ - J_-)$$
For example $j=3/2$: Spin-3/2 representation. This belongs to fermions, similar to electrons, but has 4 components. Commonly seen in $\Delta$ baryons or gravitinos in supergravity. Dimension: $d = 2(3/2) + 1 = 4$. Construct generator $J_z$ (diagonal):
$$J_z = \begin{pmatrix} 3/2 & 0 & 0 & 0 \\ 0 & 1/2 & 0 & 0 \\ 0 & 0 & -1/2 & 0 \\ 0 & 0 & 0 & -3/2 \end{pmatrix}$$
$J_+$ (raising operator coefficients) requires calculating $\sqrt{j(j+1) - m(m+1)}$, where $j=3/2$, which is $\sqrt{3.75 - m(m+1)}$. $m=1/2 \to 3/2$: $\sqrt{3.75 - 0.75} = \sqrt{3}$; $m=-1/2 \to 1/2$: $\sqrt{3.75 - (-0.25)} = \sqrt{4} = 2$; $m=-3/2 \to -1/2$: $\sqrt{3.75 - 0.75} = \sqrt{3}$. So:
$$J_+ = \begin{pmatrix} 0 & \sqrt{3} & 0 & 0 \\ 0 & 0 & 2 & 0 \\ 0 & 0 & 0 & \sqrt{3} \\ 0 & 0 & 0 & 0 \end{pmatrix}$$
Using $J_x = \frac{1}{2}(J_+ + J_+^\dagger)$:
$$J_x = \frac{1}{2} \begin{pmatrix} 0 & \sqrt{3} & 0 & 0 \\ \sqrt{3} & 0 & 2 & 0 \\ 0 & 2 & 0 & \sqrt{3} \\ 0 & 0 & \sqrt{3} & 0 \end{pmatrix}$$
Representation: This is a 4×4 unitary matrix. When rotating by 2π, since the diagonal elements are half-integers, it becomes **−I4×4​**. So j=3/2 is also a faithful representation of SU(2) and a projective representation of SO(3).

Thus far, we have completely narrated the essence of spin from the perspective of symmetry and group theory. However, it seems we did not need relativistic corrections as in the previous chapter. Unlike the previous chapter where we started from the Dirac equation and directly derived the 4-component wavefunction, here we started from spatial rotation (SU(2)/SO(3)) and only derived the 2-component spinor (Pauli spinor) for j=1/2. Where did the other two components go? The reason lies again in relativistic effects; the current symmetry analysis only considered spatial rotations and did not consider Lorentz boosts. Only by introducing the Lorentz Group can we explain why the electron must be the direct sum of "left-handed" and "right-handed" SU(2) representations (2+2=4), thereby forming a perfect closed loop back to the structure of the Dirac equation.

## 6. Lorentz Group

To achieve complete spin, we must begin considering the true symmetry group: the **Lorentz Group** $SO(1,3)$, which includes both rotations and boosts. When we attempt to find the "fundamental representation" of the Lorentz group, something extremely curious happens: the algebraic structure splits apart.

The definition of the Lorentz Group is:
$$\underbrace{\mathrm{O}(1,3) \equiv\left\{\Lambda \mid \Lambda \in \mathrm{GL}(4, \mathbb{R}), g_{\mu \nu} \Lambda^\mu{ }_\rho \Lambda^\nu{ }_\sigma=g_{\rho \sigma}\right\}}_{\operatorname{dim} \mathrm{O}(1,3)=6},\quad g=\operatorname{diag}(1,-1,-1,-1)$$
Fundamentally, it is the group of linear transformations that preserve the metric of Minkowski spacetime. From the metric-preserving condition $\Lambda^{\mathrm{T}} g \Lambda=g \rightarrow g_{\mu \nu} \Lambda^\mu{ }_\rho \Lambda^\nu{ }_\sigma=g_{\rho \sigma}$, we can derive a constraint on the component $\Lambda^0_0$:
$$1=g_{\mu \nu} \Lambda_0^\mu \Lambda_0^\nu=\left(\Lambda_0^0\right)^2-\sum_i\left(\Lambda_0^i\right)^2 \Rightarrow\left(\Lambda_0^0\right)^2=1+\sum_i\left(\Lambda_0^i\right)^2 \geq 1$$
This means that Lorentz transformations must have either $\Lambda^0_0 \geq 1$ or $\Lambda^0_0 \leq -1$, so the group is already disconnected. This allows us to divide the Lorentz group into two manifolds: $O^+(1,3)$ and $O^-(1,3)$. The former is called the **orthochronous** Lorentz group. The latter does not contain the identity element and thus does not form a group; it is called the **antichronous** branch of the Lorentz group.

From the metric-preserving condition, we can also determine the value of the determinant:
$$\left|\Lambda^{\mathrm{T}} g \Lambda\right|=|g| \Rightarrow|\Lambda|^2|g|=|g| \Rightarrow|\Lambda|^2=1 \text {, i.e., }|\Lambda|= \pm 1 \text {. }$$
Transformations with $|\Lambda|=1$ are denoted as $SO(1,3)$ and called the **proper** Lorentz group, while those with $|\Lambda|=-1$ are called the **improper** branch. Combining these two considerations, we can divide the Lorentz group $\mathrm{O}(1,3)$ into four connected manifolds. However, in practice, we only need to study the **proper orthochronous** branch $SO^+(1,3)$. This is because the other three branches can be obtained by acting on $SO^+(1,3)$ with two specific Lorentz transformations: time reversal $\mathcal{T}=\mathcal{T}^{-1}=\operatorname{diag}(-1,1,1,1)$ and parity inversion $\mathcal{P}=\mathcal{P}^{-1}=\operatorname{diag}(1,-1,-1,-1)$. Moreover, real-world reference frame transformations are strictly orthochronous and proper.

We focus on the **proper orthochronous Lorentz group** $SO^+(1,3)$. In this connected component, any transformation can be written as an exponential map from the identity. Just as $SO(3)$ has 3 rotation generators, $SO^+(1,3)$ has a total of 6 degrees of freedom (3 rotations + 3 boosts), corresponding to 6 generators. Considering an infinitesimal transformation $\Lambda \approx I - i\epsilon X$, similar to the process above, we can write out two sets of generators: **Rotation generators $\vec{J} = (J_1, J_2, J_3)$**, corresponding to spatial rotations (these are the familiar angular momentum operators); and **Boost generators $\vec{K} = (K_1, K_2, K_3)$**, corresponding to velocity transformations along the $x, y, z$ axes. These 6 generators satisfy the **Lorentz Lie algebra** $\mathfrak{so}(1,3)$ as follows:

**Pure rotations are closed** ($SO(3)$ subalgebra):
$$[J_i, J_j] = i \epsilon_{ijk} J_k$$
**Relation between rotations and boosts** (Boost operators themselves rotate like vectors):    $$[J_i, K_j] = i \epsilon_{ijk} K_k$$**Boosts are not closed among themselves** (The composition of two boosts in different directions is not just a boost but also produces a rotation, i.e., Thomas precession) (Note: the negative sign here is a characteristic manifestation of the spacetime metric $g=\text{diag}(1,-1,-1,-1)$, distinguishing it from the algebra of $SO(4)$):
$$[K_i, K_j] = -i \epsilon_{ijk} J_k$$
At this point, the algebraic structure still looks coupled ($J$ and $K$ are intertwined). To find irreducible representations, we introduce a **non-unitary basis change** (Complexification). Define two new sets of operators $\vec{N}^+$ and $\vec{N}^-$:
$$\vec{N}^+ = \frac{1}{2} (\vec{J} + i \vec{K}),\quad \vec{N}^- = \frac{1}{2} (\vec{J} - i \vec{K})$$
Let's calculate the commutation relations for these new operators. First, look within $\vec{N}^+$:
$$\begin{aligned} [N_i^+, N_j^+] &= \frac{1}{4} [J_i + iK_i, J_j + iK_j] \\ &= \frac{1}{4} \left( [J_i, J_j] + i[J_i, K_j] + i[K_i, J_j] - [K_i, K_j] \right) \\ &= \frac{1}{4} \left( i\epsilon_{ijk}J_k + i(i\epsilon_{ijk}K_k) + i(-i\epsilon_{ijk}K_k) - (-i\epsilon_{ijk}J_k) \right) \\ &= \frac{1}{4} \left( 2i\epsilon_{ijk}J_k - 2\epsilon_{ijk}K_k \right) \\ &= i\epsilon_{ijk} \frac{1}{2} (J_k + iK_k) = i\epsilon_{ijk} N_k^+ \end{aligned}$$
Similarly, we can verify that $[N_i^-, N_j^-] = i\epsilon_{ijk} N_k^-$. The most shocking result lies between $\vec{N}^+$ and $\vec{N}^-$:    
$$[N_i^+, N_j^-] = \frac{1}{4} [J_i + iK_i, J_j - iK_j] = \dots = 0$$
This means: upon complexification, the Lie algebra of the Lorentz group splits into the direct sum of two mutually independent $\mathfrak{su}(2)$ algebras.
$$\mathfrak{so}(1,3)_{\mathbb{C}} \cong \mathfrak{su}(2)_L \oplus \mathfrak{su}(2)_R$$
This is a massive simplification in group theory. Since we already know the representations of $\mathfrak{su}(2)$ inside out (labeled by spin $j$), irreducible representations of the Lorentz group can be uniquely labeled by a **pair** of half-integers or integers $(j_L, j_R)$. According to this decomposition, the most fundamental spinor representation is no longer unique; instead, there are two most basic choices (fundamental representations), corresponding to taking $j=1/2$ for one $\mathfrak{su}(2)$ and $j=0$ for the other. This introduces the concept of chirality.

**Left-handed Weyl Spinor** corresponds to the label **$(1/2, 0)$**. It behaves as spin $1/2$ under $\vec{N}^-$ and as a scalar under $\vec{N}^+$. This is a 2-component complex vector, denoted $\psi_L$. In this representation, $\vec{N}^- = \frac{1}{2}\vec{\sigma}$ and $\vec{N}^+ = 0$. Solving for the physical generators gives:
$$ \vec{J} = \vec{N}^+ + \vec{N}^- = \frac{1}{2}\vec{\sigma}, \quad \vec{K} = -i(\vec{N}^+ - \vec{N}^-) = i\frac{1}{2}\vec{\sigma}$$
**Right-handed Weyl Spinor** corresponds to the label **$(0, 1/2)$**. It behaves as a scalar under $\vec{N}^-$ and as spin $1/2$ under $\vec{N}^+$. This is also a 2-component complex vector, denoted $\psi_R$. In this representation, $\vec{N}^- = 0$ and $\vec{N}^+ = \frac{1}{2}\vec{\sigma}$. The physical generators are:
$$ \vec{J} = \frac{1}{2}\vec{\sigma}, \quad \vec{K} = -i\frac{1}{2}\vec{\sigma}$$
Note the difference in sign for $\vec{K}$! This demonstrates that while $\psi_L$ and $\psi_R$ behave identically under spatial rotation ($\vec{J}$) (both are spin $1/2$), their transformation properties under Lorentz Boosts ($\vec{K}$) are diametrically opposite.

Since $\psi_L$ and $\psi_R$ are both 2-component objects, why do we need 4 components? The reason lies in **Parity ($\mathcal{P}$)**. The parity transformation $\mathcal{P}$ inverts spatial coordinates $\vec{x} \to -\vec{x}$. $\vec{J}$ is an axial vector ($\vec{r} \times \vec{p}$), so it remains invariant under $\mathcal{P}$: $\vec{J} \to \vec{J}$. $\vec{K}$ is a polar vector ($\sim \vec{v}$), so it changes sign under $\mathcal{P}$: $\vec{K} \to -\vec{K}$. Substituting this into the definition of $\vec{N}^\pm$, we find that the parity transformation swaps these two algebras:
$$\mathcal{P}: \vec{N}^+ \longleftrightarrow \vec{N}^-$$
This means parity transforms the left-handed representation $(1/2, 0)$ into the right-handed representation $(0, 1/2)$. If we want to describe a particle like an electron that has both spin and mass, and obeys parity conservation (under electromagnetic forces), we cannot simply pick one. **We must take their "direct sum" together.** Thus, the **Dirac spinor** $\Psi$, as a representation of $SO^+(1,3)$ extended by the parity operator, is precisely the direct sum of these two fundamental representations:
$$\Psi = \begin{pmatrix} \psi_L \\ \psi_R \end{pmatrix} \in \left( \frac{1}{2}, 0 \right) \oplus \left( 0, \frac{1}{2} \right)$$
This explains why there are 4 components: **two components come from the left-handed sector, and two components come from the right-handed sector; they are tightly coupled together by the mass term and parity transformation.** The Pauli spinor we saw earlier with $SU(2)$ is merely a silhouette of this relativistic object in the rest frame (or non-relativistic limit).

Incidentally, the Weyl spinors here are deeply connected to the $\gamma^5$ matrix mentioned earlier in the context of gamma matrices. In fact, the Hermitian operator $\gamma^5 \equiv i \gamma^0 \gamma^1 \gamma^2 \gamma^3$ **is precisely the operator used to "identify" and "define" Weyl spinors**. Without $\gamma^5$, we could not mathematically distinguish what is "Left-handed" and what is "Right-handed". In Dirac theory, $\gamma^5$ is called the **Chirality Operator**. It has a crucial algebraic property: **it anti-commutes with all $\gamma^\mu$** ($\{\gamma^5, \gamma^\mu\} = 0$). However, it **commutes** with the generators of Lorentz transformations $S^{\mu\nu} = \frac{i}{4}[\gamma^\mu, \gamma^\nu]$ ($[\gamma^5, S^{\mu\nu}] = 0$), meaning $\gamma^5$ is a conserved quantity of the Lorentz group representation (for massless particles), and we can use its eigenvalues to classify spinors. A Right-handed Weyl spinor is a state with a $\gamma^5$ eigenvalue of **+1** ($\gamma^5 \psi_R = +\psi_R$), and a Left-handed Weyl spinor is a state with a $\gamma^5$ eigenvalue of **-1** ($\gamma^5 \psi_L = -\psi_L$). Thus, what is physically referred to as "left-handedness" and "right-handedness" mathematically refers to **whether the eigenvalue of $\gamma^5$ is -1 or +1**. Since the Dirac spinor $\Psi$ is a mixture (direct sum) of left and right, how do we "sift" the left-handed and right-handed parts out of a mixed $\Psi$ individually? This requires using **projection operators** based on $\gamma^5$:
$$P_L = \frac{1 - \gamma^5}{2}, \quad P_R = \frac{1 + \gamma^5}{2}$$
These two operators have the standard properties of projection operators ($P^2=P, P_L P_R = 0, P_L+P_R=1$). Their function is to kill off one handedness component and keep only the other:
$$P_L \Psi = \frac{1 - \gamma^5}{2} (\psi_L + \psi_R) = \frac{1 - (-1)}{2}\psi_L + \frac{1 - 1}{2}\psi_R = \psi_L,\quad P_R \Psi = \psi_R$$
In particle physics calculations (especially weak interactions), you will often see terms like $\frac{1-\gamma^5}{2}$; this is telling you: **"This interaction only plays with left-handed spinors; right-handed spinors, please step aside."** (This is precisely the mathematical expression of parity non-conservation). To make this relationship immediately clear, we can choose a special set of Gamma matrix forms called the **Weyl Representation (or Chiral Representation)**. Unlike the Dirac representation mentioned earlier, in the Weyl representation, the Gamma matrices are block diagonal, which makes the Dirac spinor explicitly split into upper and lower Weyl spinors $\Psi = (\psi_L, \psi_R)^T$. This is the most commonly used perspective in high-energy physics. In contrast, in low-energy condensed matter physics, we commonly use the Dirac (Standard) representation, where $\psi_L$ and $\psi_R$ are deeply mixed, better reflecting the non-relativistic approximation of "large components" and "small components".

## 7. Magnetic Gradient Force

We have completed a long mathematical journey. From the derivation of the Dirac equation to the representation of the Lorentz group, we have established that the electron must possess spin and is a 4-component relativistic object. Now, let us return to the original paradox: if the Lorentz force does no work, then who is doing the work? To answer this question, we need to link microscopic spin to macroscopic force.

By taking the non-relativistic approximation of the Dirac equation, we naturally obtained the Pauli equation. Let us revisit the "Zeeman term" that appeared seemingly out of nowhere:
$$H_{Zeeman} = - \frac{e\hbar}{2m} (\vec{\sigma} \cdot \vec{B})$$
In classical physics, we define the relationship between magnetic moment $\vec{\mu}$ and angular momentum $\vec{L}$ as the gyromagnetic ratio. For orbital angular momentum, this relationship is:
$$\vec{\mu}_L = \frac{e}{2m} \vec{L}$$
If we attempt to use the same logic to define the "spin magnetic moment," we need to relate the spin operator $\vec{S}$ to the magnetic moment. Recalling the definition of the spin operator in Section 5:
$$\vec{S} = \frac{\hbar}{2} \vec{\sigma} \quad \Longrightarrow \quad \vec{\sigma} = \frac{2}{\hbar} \vec{S}$$
Substituting $\vec{\sigma}$ back into the Zeeman term $H_{Zeeman}$, we get:
$$\begin{aligned} H_{Zeeman} &= - \frac{e\hbar}{2m} \left( \frac{2}{\hbar} \vec{S} \right) \cdot \vec{B}= - 2 \cdot \frac{e}{2m} \vec{S} \cdot \vec{B} \end{aligned}$$
We write the general form of magnetic potential energy as $U = -\vec{\mu}_S \cdot \vec{B}$. Comparing this with the equation above, we can read out the electron's **spin magnetic moment** $\vec{\mu}_S$:
$$\vec{\mu}_S = 2 \cdot \frac{e}{2m} \vec{S}$$
If we write this in the general Landé g-factor form $\vec{\mu} = g \frac{e}{2m} \vec{S}$, we immediately arrive at the conclusion:
$$\boxed{g = 2}$$
This **$g=2$** is not a parameter fudged to fit experiments; it is a **direct mathematical consequence of the spacetime symmetry of the Dirac equation**. It implies: **Electron spin generates a magnetic moment twice as efficiently as classical orbital motion.**

With the magnetic moment $\vec{\mu}$, we can finally explain "who is doing the work." The classical Lorentz force $\vec{F}_{Lorentz} = q(\vec{v} \times \vec{B})$ indeed does no work. However, for an object with an intrinsic magnetic moment, its dynamics are governed by the potential energy $U$. According to Hamiltonian mechanics, force is the negative gradient of potential energy:
$$\vec{F} = -\nabla U = -\nabla (-\vec{\mu} \cdot \vec{B}) = \nabla (\vec{\mu} \cdot \vec{B})$$
Since spin $\vec{\mu}$ is an intrinsic property and remains constant under spatial differentiation, we obtain:
$$\vec{F}_{Gradient} = (\vec{\mu} \cdot \nabla) \vec{B}$$
This is the force that does the work, known as the **Gradient Force**. If the magnetic field is uniform ($\nabla \vec{B} = 0$), the force is zero, and there is only torque. However, the magnetic field produced by a real magnet is **non-uniform** (the magnetic field lines diverge), so $\nabla \vec{B} \neq 0$. This is a conservative force that converts the **potential energy** of the magnetic field-moment coupling into the object's **kinetic energy**. Therefore, a magnet attracting iron is essentially the quantized spin magnetic moment being acted upon by the gradient force in a non-uniform magnetic field. The Lorentz force is responsible for deflection, while the gradient force is responsible for doing work.

So, there really are two types of magnetic forces. From the perspective of symmetry, they correspond to two completely different symmetry mechanisms, touching upon the edge of Quantum Field Theory. In QFT, interactions are prescribed by symmetry:

- **The Lorentz Force stems from Local Gauge Symmetry.** The electromagnetic interaction exists to maintain the $U(1)$ local phase invariance of the wavefunction: $\psi \to e^{i\alpha(x)}\psi$. To compensate for the variation of phase with position $\partial_\mu \alpha(x)$, we must introduce the gauge field $A_\mu$ and the covariant derivative $D_\mu = \partial_\mu - ieA_\mu$. The resulting equation of motion (the Lorentz force) essentially describes **how the gauge field couples to the Current**. This geometric constraint dictates that the force must be perpendicular to the four-velocity; projected into 3D space, this is $\vec{v} \times \vec{B}$. Its "no work" property is a direct manifestation of the geometric structure of gauge symmetry.
    
- **The Gradient Force stems from Broken Spatial Translational Symmetry.** According to **Noether's Theorem**, force and work are closely related to spacetime symmetry: **Momentum Conservation** $\longleftrightarrow$ **Spatial Translational Symmetry**. When an electron is in a **uniform magnetic field**, the Hamiltonian $H = -\vec{\mu} \cdot \vec{B}$ does not explicitly contain position $\vec{r}$. The system possesses spatial translational symmetry, momentum is conserved ($\dot{\vec{p}} = -\partial H / \partial \vec{r} = 0$), and there is no net force. However, when an electron is in a **non-uniform magnetic field** (near a magnet), the field $\vec{B}(\vec{r})$ depends on position: $\frac{\partial H}{\partial \vec{r}} = -\vec{\mu} \cdot \frac{\partial \vec{B}}{\partial \vec{r}} \neq 0$. The existence of the magnet breaks the spatial translational symmetry (Homogeneity is broken). It is precisely this **breaking of spacetime background symmetry** that forces the electron to change its momentum in response to the energy gradient. Thus, the Lorentz force is the price paid to maintain internal gauge symmetry, while the work-doing gradient force is the product of external spacetime symmetry breaking.

Since we are now adopting the perspective of Quantum Field Theory, we must point out that while Dirac's $g=2$ is glorious, it is not the ultimate truth. In the Dirac equation, we treat the electron as a classical field coupling to the electromagnetic field. But in full Quantum Electrodynamics (QED), the vacuum is not empty. As an electron propagates, it constantly emits and absorbs Virtual Photons, and even creates electron-positron pairs. This means the interaction Vertex between the electron and the magnetic field is no longer just a simple point (Tree level), but contains infinite Loop corrections. Julian Schwinger calculated the first-order correction (the one-loop diagram shown above) in 1948, giving the famous formula:
$$g = 2 \left( 1 + \frac{\alpha}{2\pi} + \mathcal{O}(\alpha^2) \right)$$
where $\alpha \approx 1/137$ is the fine-structure constant. This shifts the theoretical value of $g$ to $g \approx 2.002319...$, which is astonishingly consistent with experimental measurements (accurate to 12 decimal places). This tiny deviation (the Anomalous magnetic moment) not only confirms the relativistic origin of $g=2$ but also reveals the deep physics behind magnetism: when we feel the pull of a magnet, we are not only witnessing the geometric attributes of spacetime (spin) but also touching the seething ocean of virtual particles in the vacuum.


## 8. Heisenberg Model

We now know that every electron is a tiny magnetic needle ($g=2$). However, if you put a bunch of these tiny magnets together, thermal agitation at room temperature is sufficient to completely randomize their orientations, resulting in zero macroscopic magnetic moment (paramagnetism). To form ferromagnetism, there must be an extremely strong "coupling force" between spins that forces them to align. The classical magnetic dipole-dipole interaction is far too weak—only about one ten-thousandth of the thermal energy. The real power comes from the combination of the **identical particle statistics (Spin-Statistics)** we mentioned earlier and the **Coulomb interaction**. This is known as the **Exchange Interaction**.

To demonstrate the essence of this, let us consider the simplest model: a **two-electron system** (such as a Helium atom or electrons on two adjacent Iron atoms). Assume there are two electrons, 1 and 2, and two spatial orbitals $\psi_a(\vec{r})$ and $\psi_b(\vec{r})$, where $\psi_a(\vec{r})$ is localized near atom A and $\psi_b(\vec{r})$ is localized near atom B. We assume these two orbitals are orthonormal: $\langle \psi_a | \psi_b \rangle = 0$. Note that this orthogonality is a prerequisite assumption for the Heisenberg model we are about to derive. Even if they are not orthonormal, we can create two new orthonormal orbitals through a basis transformation. Assuming their overlap integral is small greatly simplifies the calculation of the two-electron system, but this does not mean there is no interaction between the two electrons, as the interaction involves exchange integrals which generally are not zero.

The total Hamiltonian of this system is $H = H_0 + H_{int}$, where $H_0$ is the single-electron part (kinetic energy + nuclear potential energy), and $H_{int}$ is the **Coulomb interaction** between the two electrons: $H_{int} = \frac{e^2}{|\vec{r}_1 - \vec{r}_2|}$. Note: there is absolutely no magnetic interaction term here, only pure electrostatic repulsion.

According to the Fermi statistics hypothesis for identical particles in quantum mechanics, the total wavefunction of the electrons $\Psi(1,2)$ must change sign (be antisymmetric) under the action of the particle exchange operator $P_{12}$:
$$P_{12} \Psi(1,2) = -\Psi(1,2)$$
Since the total wavefunction consists of a **spatial part** $\phi(\vec{r}_1, \vec{r}_2)$ and a **spin part** $\chi(s_1, s_2)$: $\Psi = \phi \otimes \chi$. We first derive the spin part, and then obtain the spatial part based on the overall antisymmetry. We have two spin-1/2 particles (e.g., two electrons), so there are a total of $2 \times 2 = 4$ possible product states (uncoupled basis). We want to add their spins together to see what the total spin $\vec{S}_{tot} = \vec{S}_1 + \vec{S}_2$ looks like, finding the common eigenstates $|S, M\rangle$ of the total spin operator $\hat{S}^2$ and total magnetic quantum number $\hat{S}_z$. According to angular momentum addition rules, the total spin $S$ formed by two spins of $1/2$ can be: $S = 1/2 + 1/2 = 1$ (Triplet, with 3 $M$ values: $+1, 0, -1$) and $S = 1/2 - 1/2 = 0$ (Singlet, with 1 $M$ value: $0$).

The Triplet corresponds to three components. The total magnetic quantum number $M$ is the sum of the magnetic quantum numbers of the two particles: $M = m_1 + m_2$. To get $M=1$, the only possibility is both electrons are spin-up: $1/2 + 1/2 = 1$. So, the first member of the Triplet is determined: $|1, 1\rangle = |\uparrow\uparrow\rangle$. Then, using the lowering operator ($S_-$), we get the intermediate state ($M=0$) from $|1, 1\rangle$ to derive $|1, 0\rangle$. Using the total lowering operator $\hat{S}_- = \hat{S}_{1-} + \hat{S}_{2-}$ acting on the state $|j, m\rangle$: $J_- |j, m\rangle = \hbar \sqrt{j(j+1) - m(m-1)} |j, m-1\rangle$, acting on the coupled state on the left gives:
$$\hat{S}_- |1, 1\rangle = \sqrt{1(1+1) - 1(1-1)} |1, 0\rangle = \sqrt{2} |1, 0\rangle$$
Acting on the product state on the right gives:
$$\begin{aligned} (\hat{S}_{1-} + \hat{S}_{2-}) |\uparrow\uparrow\rangle &= (\hat{S}_{1-} |\uparrow\rangle_1)|\uparrow\rangle_2 + |\uparrow\rangle_1 (\hat{S}_{2-} |\uparrow\rangle_2) \ = |\downarrow\rangle_1|\uparrow\rangle_2 + |\uparrow\rangle_1|\downarrow\rangle_2 \ = |\downarrow\uparrow\rangle + |\uparrow\downarrow\rangle \end{aligned}$$
Thus we obtain:
$$|1, 0\rangle = \frac{1}{\sqrt{2}} (|\uparrow\downarrow\rangle + |\downarrow\uparrow\rangle)$$
The lowest weight state ($M=-1$) is also simple; only both down can give $-1$: $|1, -1\rangle = |\downarrow\downarrow\rangle$. So the spin part of the Triplet is symmetric (does not change sign upon exchange), which means the spatial part must be antisymmetric.

The quantum numbers for the Singlet are $S=0, M=0$. It must be some linear combination of the product states $|\uparrow\downarrow\rangle$ and $|\downarrow\uparrow\rangle$ with $M=0$: $|0, 0\rangle = a |\uparrow\downarrow\rangle + b |\downarrow\uparrow\rangle$. Since eigenstates with different quantum numbers must be orthogonal, the Singlet $|0, 0\rangle$ must be orthogonal to $|1, 0\rangle$ in the Triplet. Solving this gives:
$$|0, 0\rangle = \frac{1}{\sqrt{2}} (|\uparrow\downarrow\rangle - |\downarrow\uparrow\rangle)$$
The spin part of the Singlet is antisymmetric, so the corresponding spatial part must be symmetric. Summarizing:
- Spatial Symmetric $\otimes$ Spin Antisymmetric (Singlet) Energy: $E_S$
    - **Spin Part (Antisymmetric):** $S=0$ Singlet $\chi_S = \frac{1}{\sqrt{2}}(\uparrow\downarrow - \downarrow\uparrow)$.
    - **Spatial Part (Symmetric):** $\phi_S(\vec{r}_1, \vec{r}_2) = \frac{1}{\sqrt{2}} [\psi_a(\vec{r}_1)\psi_b(\vec{r}_2) + \psi_a(\vec{r}_2)\psi_b(\vec{r}_1)]$.
- Spatial Antisymmetric $\otimes$ Spin Symmetric (Triplet) Energy: $E_T$
    - **Spin Part (Symmetric):** $S=1$ Triplet $\chi_T = \{\uparrow\uparrow, \frac{1}{\sqrt{2}}(\uparrow\downarrow + \downarrow\uparrow), \downarrow\downarrow\}$.
    - **Spatial Part (Antisymmetric):** $\phi_A(\vec{r}_1, \vec{r}_2) = \frac{1}{\sqrt{2}} [\psi_a(\vec{r}_1)\psi_b(\vec{r}_2) - \psi_a(\vec{r}_2)\psi_b(\vec{r}_1)]$.

Our goal is to find a mathematical expression $\hat{H}_{eff}$ containing only spin operators $\vec{S}_i$ and $\vec{S}_j$ such that when it acts on the Singlet and Triplet states, it automatically yields the corresponding energies $E_S$ and $E_T$. To construct this Hamiltonian, the most natural building block is the dot product of the two spins $\vec{S}_i \cdot \vec{S}_j$. We need to calculate the **eigenvalues** of this operator for the Singlet and Triplet states. Define the **total spin operator** for the two-electron system: $\vec{S}_{tot} = \vec{S}_i + \vec{S}_j$. Squaring the total spin operator allows us to solve for the dot product term: $\vec{S}_i \cdot \vec{S}_j = \frac{1}{2} \left( \vec{S}_{tot}^2 - \vec{S}_i^2 - \vec{S}_j^2 \right)$. Using the eigenvalue formula for the square of the angular momentum operator in quantum mechanics $\hat{S}^2 |s\rangle = s(s+1) |s\rangle$ (omitting $\hbar^2$ for brevity, or treating spin as dimensionless):
- **For a single electron** ($s=1/2$): $\vec{S}_i^2 = \vec{S}_j^2 = \frac{1}{2}\left(\frac{1}{2} + 1\right) = \frac{3}{4}$
- **For the Singlet** ($S_{tot}=0$): $\vec{S}_{tot}^2 |S\rangle = 0(0+1) |S\rangle = 0$
- **For the Triplet** ($S_{tot}=1$): $\vec{S}_{tot}^2 |T\rangle = 1(1+1) |T\rangle = 2 |T\rangle$. Now, substituting these values back into the dot product formula to calculate the eigenvalues:
- **Dot product value for Singlet**: $(\vec{S}_i \cdot \vec{S}_j) |S\rangle = \frac{1}{2} \left( 0 - \frac{3}{4} - \frac{3}{4} \right) |S\rangle = -\frac{3}{4} |S\rangle$
- **Dot product value for Triplet**: $(\vec{S}_i \cdot \vec{S}_j) |T\rangle = \frac{1}{2} \left( 2 - \frac{3}{4} - \frac{3}{4} \right) |T\rangle = \frac{1}{2} \left( \frac{1}{2} \right) |T\rangle = \frac{1}{4} |T\rangle$

We assume the effective Hamiltonian $\hat{H}_{ij}$ has the following linear form (this is the most general rotationally symmetric form): $\hat{H}_{ij} = C_0 + C_1 (\vec{S}_i \cdot \vec{S}_j)$, where $C_0$ is just a constant energy shift independent of spin configuration, which can be discarded (or the energy zero point redefined) when studying phase transitions and spin dynamics. Substituting the data for Singlet and Triplet, we have $E_S=C_1(-\frac{3}{4}), E_T=C_1(\frac{1}{4})$. Defining the constant $J \equiv E_S - E_T$, we obtain the two-particle Hamiltonian:
$$\hat{H}_{ij} = -J (\vec{S}_i \cdot \vec{S}_j)$$
- If $J>0$ ($E_S > E_T$): The coefficient is negative. The larger the dot product (parallel, +1/4), the lower the energy. **This is Ferromagnetism.**
- If $J<0$ ($E_S < E_T$): The coefficient is positive. The smaller the dot product (anti-parallel, -3/4), the lower the energy. **This is Antiferromagnetism.**

Now we generalize this two-particle interaction to the entire lattice. Assuming each electron $i$ only interacts with its nearest neighbors. We need to sum over all atoms in the lattice. To correct for double counting:
$$H_{exchange} = -\frac{J}{2} \sum_{i,j \text{ neighbor}} \vec{S}_i \cdot \vec{S}_j$$
Finally, we must consider the interaction of each electron spin with an external uniform magnetic field $\vec{B}$. This is a single-body interaction and does not involve neighbors. Recalling our conclusion from the Dirac equation, the electron has a spin magnetic moment:
$$\vec{\mu}_S = -g \frac{e}{2m} \vec{S}$$
To make the formula more concise and universal, physicists define a natural combination of constants called the **Bohr Magneton**. The Bohr Magneton is the natural unit of magnetic moment in atomic physics. It is defined as:
$$\mu_B \equiv \frac{e\hbar}{2m_e}$$
This physical quantity contains three fundamental constants: elementary charge $e$, Planck constant $\hbar$, and electron mass $m_e$. It represents the magnitude of the orbital magnetic moment generated by a classical electron moving in the ground state orbit of a hydrogen atom. This is in SI units; in Gaussian units, it also includes the speed of light: $\mu_B \equiv \frac{e\hbar}{2m_ec}$. If we treat the spin operator $\vec{S}$ as a **dimensionless** operator (i.e., eigenvalues are $1/2$ instead of $\hbar/2$), then the true physical angular momentum is $\hbar \vec{S}$. Extracting this $\hbar$ and combining it with the constants above:
$$\begin{aligned} \vec{\mu}_S &= -g \frac{e}{2m_e} (\hbar \vec{S}_{\text{dimensionless}}) = -g \left( \frac{e\hbar}{2m_e} \right) \vec{S}= -g \mu_B \vec{S} \end{aligned}$$
When an electron is in an external magnetic field $\vec{B}$, its potential energy (Zeeman Energy) is given by the classical electromagnetism formula $U = -\vec{\mu} \cdot \vec{B}$. Substituting the magnetic moment expression:
$$\begin{aligned} U_{Zeeman} &= - (-\vec{\mu}_S) \cdot \vec{B} \quad (\text{Note the sign: Potential energy is usually defined as } -\vec{\mu}\cdot\vec{B}) \\ &= - (-g \mu_B \vec{S}) \cdot \vec{B} \\ &= g \mu_B \vec{S} \cdot \vec{B} \end{aligned}$$
**Physical Convention on Signs:** In condensed matter physics, we usually want the Hamiltonian to reflect energy minima. Electrons are negatively charged, so the magnetic moment $\vec{\mu}$ is anti-parallel to the spin $\vec{S}$. The lowest energy state is when the magnetic moment $\vec{\mu}$ is **parallel** to the magnetic field $\vec{B}$. This means the spin $\vec{S}$ is **anti-parallel** to the magnetic field $\vec{B}$. To avoid dealing with cumbersome negative signs, or to make spin look like it aligns "with" the field (defining $\vec{S}$ to point in the direction of the magnetic moment rather than angular momentum), literature sometimes adjusts the definition. However, the standard derivation (keeping the electron's negative charge) gives the Zeeman term as $+ g\mu_B \vec{S} \cdot \vec{B}$ or $- \vec{\mu} \cdot \vec{B}$. Nevertheless, in the customary notation of the Heisenberg model, for mathematical symmetry and ease of discussion (e.g., assuming $g$ is negative or redefining the spin direction), the Zeeman term is typically written with a negative sign, indicating that spins tend to align along the field (this is a phenomenological treatment):
$$H_{Zeeman} = -g \mu_B \sum_i \vec{S}_i \cdot \vec{B}$$
(This implies that energy is minimized when $\vec{S}_i$ is in the same direction as $\vec{B}$. This implies we have redefined the spin direction, or taken $g$ to be negative. In phenomenological models, we only care about: **which direction does the magnetic field tend to pull the spins.**)

Now, we combine the two pieces of the puzzle: **Internal Interaction** (Exchange Energy generated by the Pauli principle and Coulomb force) and **External Interaction** (Coupling of magnetic moment with external field generated by relativistic quantum effects). Adding them together, we finally obtain the core Hamiltonian describing solid-state magnetism—the **Heisenberg Model**:
$$\boxed{H = -\frac{J}{2} \sum_{\langle i,j \rangle} \vec{S}_i \cdot \vec{S}_j - g \mu_B \sum_i \vec{S}_i \cdot \vec{B}}$$
This formula is the cornerstone of modern magnetism. The first term ($J$) explains **why magnets have magnetism** (spontaneous magnetization, ordered alignment of spins). The second term ($B$) explains **how magnets are controlled by the outside world** (magnetization process, hysteresis loop). $\mu_B$ and $g$ link microscopic quantum constants ($\hbar, e, m_e$) with macroscopic observable magnetic fields.

## 9. Ising Model

We have completed the construction of the microscopic mechanism (Dirac $\to$ Spin $\to$ Exchange Interaction $\to$ Heisenberg Hamiltonian). Now, we must move from the microscopic to the macroscopic. To do this, we need to handle the Heisenberg Model. However, solving the Heisenberg Model exactly in two or three dimensions is extremely difficult (because it contains non-commuting operators). Therefore, we need to introduce the **Ising Model** as an approximation and use **Mean-Field Theory** to demonstrate how symmetry is broken.

We first non-dimensionalize the Heisenberg model and analyze its structure. Assume the external magnetic field is along the $z$-direction: $\vec{B} = (0, 0, B)$. We expand the dot product of the spin operators $\vec{S}$ into longitudinal ($z$) and transverse ($x, y$) components:
$$\vec{S}_i \cdot \vec{S}_j = S_i^z S_j^z + (S_i^x S_j^x + S_i^y S_j^y)$$
To see the physical meaning of the transverse part more clearly, we introduce Ladder Operators:
$$S_i^+ = S_i^x + i S_i^y, \quad S_i^- = S_i^x - i S_i^y$$
Thus, the Heisenberg model can be rewritten in two parts:
$$H = \underbrace{\left[ -\frac{J}{2} \sum_{\langle i,j \rangle} S_i^z S_j^z - h \sum_i S_i^z \right]}_{\text{Ising Part}} + \underbrace{\left[ -\frac{J}{4} \sum_{\langle i,j \rangle} (S_i^+ S_j^- + S_i^- S_j^+) \right]}_{\text{Flip Part}}$$
(where $h = g\mu_B B$). These two parts have distinct physical meanings:

- **Ising Part (Longitudinal Term):** This term involves only $S^z$. Since $S_i^z$ on different lattice sites commute ($[S_i^z, S_j^z]=0$), they behave like classical scalar variables. This describes the static alignment of spins along the $z$-axis.
- **Flip Part (Transverse/Flip Term):** This term involves $S_i^+ S_j^-$. Its action is to flip the spin at site $j$ down ($S^-$) while simultaneously flipping the spin at site $i$ up ($S^+$): $S_i^+ S_j^- |\downarrow_i \uparrow_j\rangle = |\uparrow_i \downarrow_j\rangle$. Physically, this represents the **movement of spin excitations**. Just like a spin-flipped state hopping through the lattice, this corresponds to **Spin Waves** or **Magnons**. This is a form of **quantum fluctuation** that imparts "kinetic energy" to the system, tending to destroy ordered alignment.

In many real magnetic materials, due to the symmetry of the crystal structure, there exists **Magnetic Anisotropy**. This means the energy of spins along certain directions (e.g., the $z$-axis, the easy axis) is lower than in the $x,y$ plane. If the anisotropy is strong enough, or if we are only concerned with phase transition behavior in the classical limit, we can ignore the Flip Part (quantum fluctuations) and retain only the longitudinal term. This is the famous **Ising Model**.

At this point, we replace the operator $S_i^z$ with a classical variable $\sigma_i = \pm 1$ (absorbing the coefficients into $J$):
$$H_{Ising} = - \frac{J}{2} \sum_{\langle i,j \rangle} \sigma_i \sigma_j - h \sum_i \sigma_i$$
This is a massive simplification: we turn a non-commuting quantum matrix problem into a classical statistical combinatorial problem. The 2D Heisenberg model cannot be solved exactly to this day, though we can solve it using computational methods. However, the Ising model within it is relatively simpler. The solution to the 1D Ising model is very simple; there is no phase transition in 1D (Ising, 1924). But the 2D case is also very difficult to solve. It wasn't until the brilliant Lars Onsager published a very simple paper stating that he had solved it—without providing the solution details, but giving the critical temperature and pointing out that it is ferromagnetic at low temperatures and paramagnetic at high temperatures—that we had the first exactly solvable model exhibiting a ferromagnetic phase transition. He withheld the solution process until C.N. Yang saw the paper and provided a solution, which was still famously difficult. To understand the physical picture intuitively, we will adopt the **Mean-Field Approximation** here.

The problem we face is many-body coupling: the state of $\sigma_i$ depends on $\sigma_j$, and $\sigma_j$ depends on $\sigma_k$... This chain reaction makes the partition function difficult to calculate. The Mean-Field idea is: when we focus on atom $i$, we don't care whether neighbor $j$ is flipping between $+1$ or $-1$; we only care about the _average_ influence of the neighbors. We write $\sigma_j$ as an average value plus a fluctuation: $\sigma_j = \langle \sigma \rangle + \delta \sigma_j$. Ignoring the second-order fluctuation term $\delta \sigma_i \delta \sigma_j \approx 0$, the Hamiltonian can be linearized into a single-body form:
$$H_{MFA} = - \sum_i \sigma_i \underbrace{\left( J \sum_{j \in \text{neigh}} \langle \sigma \rangle + h \right)}_{h_{eff}}$$
This defines the **Effective Molecular Field** $h_{eff}$:
$$h_{eff} = J z \langle \sigma \rangle + h$$
where $z$ is the coordination number (number of neighbors for each atom). Now, the problem becomes the statistical distribution of a single spin in an "external field" $h_{eff}$. According to the Boltzmann distribution, the probability of this spin being up is proportional to $e^{\beta h_{eff}}$, and the probability of being down is proportional to $e^{-\beta h_{eff}}$ (where $\beta = 1/k_B T$). Thus, the thermodynamic average of this spin $\langle \sigma_i \rangle$ is:
$$\langle \sigma_i \rangle = \frac{(+1)e^{\beta h_{eff}} + (-1)e^{-\beta h_{eff}}}{e^{\beta h_{eff}} + e^{-\beta h_{eff}}} = \tanh(\beta h_{eff})$$
Since the lattice is uniform, $\langle \sigma_i \rangle$ must equal the average value of the field source itself, $m = \langle \sigma \rangle$. Substituting $h_{eff}$, we obtain the famous **Self-consistent Equation**:
$$m = \tanh\left( \frac{J z m + h}{k_B T} \right)$$
Let us consider the most critical case: **no external magnetic field (h=0)**. The equation simplifies to:
$$m = \tanh\left( \frac{T_c}{T} m \right)$$
where we package the constants into the definition of the **Curie Temperature** Tc​=Jz/kB​. This is a transcendental equation, and we can analyze the behavior of the solution graphically (by finding the intersection of y=m and y=tanh(TTc​​m)):
- **High-Temperature Phase (T>Tc​):** The slope of the tanh curve at the origin is Tc​/T<1. The line and the curve intersect at **only one point**, m=0. **Physical meaning:** Thermal agitation is intense; without an external field, there is no magnetism. This is the **Paramagnetic Phase**.
- **Low-Temperature Phase (T<Tc​):** The slope of the tanh curve at the origin is Tc​/T>1. The origin m=0 becomes an unstable solution, and **two new stable non-zero solutions** m=±m0​ appear. **Physical meaning:** Even if h=0, the system will spontaneously generate a non-zero magnetization m0​. This is the **Ferromagnetic Phase**.

**This is Spontaneous Symmetry Breaking:** The Hamiltonian has a flip symmetry σ→−σ when h=0. However, when the temperature drops below Tc​, nature is **forced** to choose between "all up" and "all down." This choice is not imposed by an external force but is a collective decision made **spontaneously** by the system to lower its energy (driven by the exchange interaction J). This is precisely the statistical mechanical essence behind the macroscopic phenomenon of a magnet attracting iron.

## 10. Magnetic Domains

Based on the Ising model and Mean-Field Theory, we concluded that when the temperature is below the Curie temperature $T_c$, electron spins spontaneously align, producing a massive macroscopic magnetization $M$. However, this immediately leads to a new paradox: if you go to a hardware store and buy an iron nail (room temperature is obviously far below Iron's Curie temperature of $1043K$), it is not magnetic. It does not pick up other objects. This is because we ignored one final energy competition.

Our previous Hamiltonian only considered Exchange Energy and Zeeman Energy. However, at the macroscopic scale, there is also the classical **Magnetostatic Energy**. If all $10^{23}$ atoms in a piece of iron were aligned upwards, this magnet would establish a huge magnetic field in the surrounding space. The magnetic field contains energy density $B^2/2\mu_0$. Spreading out all those magnetic field lines costs a tremendous amount of energy. To reduce this **Magnetostatic Energy**, the material spontaneously splits into many tiny regions called **Magnetic Domains**. Although **inside** a domain, the exchange interaction keeps spins aligned (satisfying microscopic ferromagnetism), **overall**, the vector sum of the magnetic moments of the various domains is zero ($\sum \vec{M}_i = 0$). There are no external magnetic field lines, thereby drastically reducing the magnetostatic energy.

The boundary between magnetic domains is called a **Domain Wall**. Inside the domain wall, spins do not flip abruptly but rotate gradually. This is another game of energy trade-offs: **Exchange Energy** wants spins to be parallel and resists their turning (preferring the wall to be as wide as possible); **Magnetic Anisotropy** wants spins to align along the easy axis and resists them pointing in intermediate directions (preferring the wall to be as narrow as possible). The balance between the two determines the thickness of the domain wall (typically hundreds of atomic layers). The formation of magnetic domains is not derived from "first principles" like spin, but belongs to the realm of **Micromagnetics**, involving energy minimization in continuum field theory, which we will not expand upon here.

Now, we can finally fully describe the macroscopic process of "a magnet attracting iron":
- **Initial State:** The interior of the iron nail is filled with chaotic magnetic domains; the macroscopic magnetic moment is zero.
- **External Field Intervention:** When you bring a magnet close to the nail, you provide an external magnetic field $\vec{B}_{ext}$.
- **Domain Wall Motion:** The equilibrium is broken. Domains whose direction **aligns** with $\vec{B}_{ext}$ have lower Zeeman energy ($E = -\vec{M} \cdot \vec{B}$). Consequently, these "compliant" domains begin to swallow the surrounding "non-compliant" domains. The domain walls move.
- **Macroscopic Magnetization:** The nail rapidly gains a huge net magnetic moment.
- **Gradient Force Work:** This induced macroscopic magnetic moment $\vec{m}_{total}$ is pulled by the **gradient force** $\vec{F} = \nabla(\vec{m}_{total} \cdot \vec{B})$ generated by the magnet's non-uniform field.
- **Click:** The nail flies towards the magnet.

## Conclusion: The Deep Symmetry of the Universe

When you play with two magnets in your hands, feeling the repulsion and attraction between them, you are feeling more than just a force. You are touching the **essence of quantum mechanics** and the **secrets of cosmic evolution** with your own hands. Let us review this journey and see how we rebuilt our physical intuition:

1. **The Classical Collapse:** We found that the Lorentz force does no work, and classical statistical physics forbids magnetism (Bohr-van Leeuwen Theorem).
2. **The Relativistic Correction:** The Dirac equation revealed that the electron must be a 4-component spinor carrying an intrinsic magnetic moment with g=2. Magnetism is the residue of relativistic effects in the low-speed world.
3. **The Power of Quantum Statistics:** The Pauli Exclusion Principle combined with Coulomb repulsion creates an equivalent "Exchange Interaction," forcing spins to align parallel.
4. **Symmetry Breaking:** The Ising model taught us that when the temperature drops, the system, in order to survive (lower its energy), is forced to break rotational symmetry and choose a direction.

Finally, it is worth mentioning that the **Spontaneous Symmetry Breaking (SSB)** we saw in the Ising model has significance far beyond solid-state physics. It is a core paradigm for understanding the universe in modern physics. At the beginning of the Big Bang (extremely high temperature), physical laws possessed extremely high symmetry. All fundamental particles were massless, just like the iron block at high temperatures has no magnetism (paramagnetic phase). As the universe cooled, when the temperature dropped below a certain critical value, the **Higgs Field** filling the universe underwent a phase transition. Just like electron spins suddenly choosing to point in one direction, the Higgs field acquired a non-zero **Vacuum Expectation Value** in empty space.

- In a ferromagnet, symmetry breaking endows the material with **magnetism**.
- In the Standard Model, symmetry breaking endows fundamental particles with **mass**.
    

So, the next time you see a magnet pick up a paperclip, realize this: you are witnessing a miniature moment of cosmic creation. The mechanism that gives the nail its magnetism is the very same mechanism that gives the quarks and electrons in your body their mass, allowing this universe to exist.

Magnetic force does no work; it is the geometry of spacetime doing the work. The attraction of a magnet is the dance of a quantum ghost in the macroscopic world.