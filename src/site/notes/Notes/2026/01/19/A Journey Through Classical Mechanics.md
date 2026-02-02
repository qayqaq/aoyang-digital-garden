---
{"dg-publish":true,"permalink":"/notes/2026/01/19/a-journey-through-classical-mechanics/"}
---

(待完善)
## 1. Basic Mathematics and Physics

Outline: 
- Hamiltonian Canonical Equation
- Concept and Definition of Force
- Relationships between Force and Potential
- Potential Energy Curve
- Derivative Form
- Stokes Formula

### 1.1 Potential Energy and Force

从势能出发, 我们可以给出力的定义, 即势能对位置的偏导, 结合牛二定律有 $\frac{d \vec{p}}{d t}=\vec{F}=-\frac{\partial V}{\partial \vec{x}}$, 同时还知道动量的表达式 $\frac{\vec{p}}{m}=\frac{d \vec{x}}{d t}$. 

现在把这两个式子作为已知, 我们就可以定义一个量 $H(\vec{x}, \vec{p})=\frac{\vec{p}^2}{2 m}+V(\vec{x})$ 目前我们可以简单地认为这是总能量, 其中我们认为 x 和 p 是独立自变量, 上面两个式子可以改写成 $\frac{d \vec{p}}{d t}=-\frac{\partial H}{\partial \vec{x}}, \frac{d \vec{x}}{d t}=\frac{\partial H}{\partial \vec{p}}$. 这进一步可以导出 $\frac{d H}{d t}=0$. 所以这是一个守恒量, 也就是说我们现在可以通过这个量守恒来等价推导出原来的两个最初的式子.

拓展到多粒子情形: $H=\sum_i \frac{\overrightarrow{p}_i^2}{2 m_i}+V\left(\vec{x}_1, \vec{x}_2, \cdots, \vec{x}_N\right)$ 可以得到对每个粒子有 $\frac{d \vec{p}_i}{d t}=-\frac{\partial H}{\partial \vec{x}_i}, \frac{d \overrightarrow{x_i}}{d t}=\frac{\partial H}{\partial \vec{p}_i}$.

于是我们现在有一个处理经典物理系统的基本方法:
- 找到基本力学变量.
- 写下哈密顿量.
- 写下哈密顿正则方程.

过去我们比较习惯的是画出 $V(x)$ 的势能图, 并在其中画一条横线代表总能量, 那么因为动能是非负的, 所以可以导出粒子所能运动的区域, 只能在 $V(x)$ 在这条横线一下有值的区域. 比如一个 $V(x)$ 洼地, 粒子就会在这个洼地里面来回运动, 这称为束缚运动, 束缚轨道, 否则我们称为散射.

现在既然我们把 x 和 p 认为是独立自变量, 那么我们可以在 (x,p) space 中画出系统的轨道图, 这个 space 也称为 phase space, 显然针对不同的总能量值, phase space 中的轨道 orbital 是不同的, 我们可以考虑粒子在某一个特定能量值下运动的周期: $T(E)=\oint_E d t=\oint_E \frac{m}{p} d x=\oint_E \frac{m}{\sqrt{2 m\left(E-V(x)\right)}} d x$, 通过引入相空间区域的面积: $2 \pi I(E)=\oint_E p d x=\oint_E \sqrt{2 m(E-V(x))} d x$. 那么就有: $\frac{\partial I(E)}{\partial E}=\frac{1}{2 \pi} \oint_E \frac{\partial}{\partial E} \sqrt{2 m(E-V(x))} d x=\frac{T(E)}{2 \pi}$. 写成角频率的话: $\frac{\partial E}{\partial I}=\omega(I)$ 这是一个可以拓展到可积系统的结果.

进一步, 我们可以联系到Bohr 的定态假设, 如果我们认为 $E_n-E_{n-1}=\hbar \omega$ 当 n 趋于无穷时有 $\frac{\partial E_n}{\partial n}=\hbar \omega$ 结合刚才的结果我们实际上得到了旧量子论的 Bohr-Sommerfeld quantization condition $I=n\hbar$. 

> [!Example]
> 一维线性谐振子 $V(x)=\frac{1}{2} k x^2=\frac{1}{2} m \omega^2 x^2$, 那么轨道为 $\frac{p^2}{2 m}+\frac{1}{2} m w^2 x^2=E$, 面积为 $2 \pi E / \omega=2 \pi I$ 于是有 $E=I\omega=n\hbar\omega$.

### 1.2 Derivative Form, Exterior Derivative and Stokes Formula

势能对位置的偏导定义出的力抓住了自然界中基本相互作用力的本质, 满足这一定义的力学系统自动是一个哈密顿系统, 即满足哈密顿正则方程. 然而这样定义的力却不能包括日常生活中的所有力, 比如摩擦力. 事实上这样定义的力常称为保守力, 而摩擦力就是非保守力. 本节我们将要引入一个数学方法:微分形式, 来研究保守力的特性.

首先我们拔高对多变量函数变量带换的理解, 定义 wedge product $d x \wedge d y=-d y \wedge d x, d x \wedge d x=0$ 此时有 $d x \wedge d y=\left(\frac{\partial x}{\partial x^{\prime}} d x^{\prime}+\frac{\partial x}{\partial y^{\prime}} d y^{\prime}\right) \wedge\left(\frac{\partial y}{\partial x^{\prime}} d x^{\prime}+\frac{\partial y}{\partial y^{\prime}} d y^{\prime}\right)=\left(\frac{\partial x}{\partial x^{\prime}} \frac{\partial y}{\partial y^{\prime}}-\frac{\partial x}{\partial y^{\prime}} \frac{\partial y}{\partial x^{\prime}}\right) d x^{\prime} \wedge d y^{\prime}=\left|\frac{\partial(x, y)}{\partial\left(x^{\prime}, y^{\prime}\right)}\right| d x^{\prime} \wedge d y^{\prime}$. 这正啊好哦就是变量带换的形式. 

基于此, 我们定义 n-form: $\omega=f\left(x^{\prime}, x^2, \ldots x^n\right) d x^{\prime} \wedge d x^2 \wedge \ldots \wedge d x^n$, 很自然, 一个n元函数的n重积分实际上就等价于 integral of n-form $\iint\cdots\int f\left(x^1 \cdots x^n\right) d x^1 \cdots d x^n:=\int d \omega$. 我们进一步可以做出拓展, 定义 n 元变量的 k-form: $\alpha = \frac{1}{k!} \alpha_{i_1, i_2 \dots i_k} dx^{i_1} \wedge dx^{i_2} \wedge \dots \wedge dx^{i_k}$, 注意这里使用了爱因斯坦求和记号, 一个 k-form 实际上是一个线性组合, 而 $\alpha_{i_1, i_2 \dots i_k}$ 称为分量, 那既然是求和, 考虑到 wedge product 的交换顺序取负号, 我们可以认为 k-form 的分量对任意两个维度都是反对称的, 也称全反称, 这是因为任何一个 $\alpha_{ij}$ 都可以拆分为两部分之和：**对称部分 (Symmetric part)**: $S_{ij} = \frac{1}{2}(\alpha_{ij} + \alpha_{ji})$，满足 $S_{ij} = S_{ji}$ 和**反对称部分 (Anti-symmetric part)**: $A_{ij} = \frac{1}{2}(\alpha_{ij} - \alpha_{ji})$，满足 $A_{ij} = -A_{ji}$。当计算 $\alpha = \frac{1}{2} \alpha_{ij} dx^i \wedge dx^j$ 时，实际上是在做如下运算：
$$\alpha = \frac{1}{2} (S_{ij} + A_{ij}) dx^i \wedge dx^j = \underbrace{\frac{1}{2} S_{ij} dx^i \wedge dx^j}_{\text{对称} \times \text{反对称}} + \underbrace{\frac{1}{2} A_{ij} dx^i \wedge dx^j}_{\text{反对称} \times \text{反对称}}$$
第一项在求和中就正负抵消了, 只有后者会保留下来, 也就是说只有反称部分对 k-form 是有贡献的, 所以我们不妨认为分量 $\alpha_{i_1 \dots i_k}$ 就是**全反对称**的. 而当 k>n 时必然指标有重复, 所以 k-from 就是 0. 而 1/n! 的系数则是因为求和中有重复计算, 比如 k=n 时, 因为全反称的性质, 所有的分量一半相等一半为相反数, 但是正好 wedge product 交换顺序取负号, 所以正好重复计算 n! 次.

3-dim 的例子:
- 0-form: $f(x,y,z)$.
- 3-form: $f(x, y, z) d x \wedge d y \wedge d z$.
- 1-form: $a_1 d x+a_2 d y+a_3 d z=\vec{a}(\vec{x}) \cdot d \vec{x}$.
- 2-form: $a_{12} d x \wedge d y+a_{23} d y \wedge d z+a_{21} d z \wedge d x=\frac{1}{2} a_{i j}(\vec{x}) d x^i \wedge d x^j \rightarrow b_1 d x+b_2 d y+b_3 d z$. 这个变换中我们认为 $b_1=a_{23}, b_2=a_{31} . b_3=a_{12} . d x \wedge d y \rightarrow d z . d y \wedge d z \rightarrow d x . d z \wedge d x \rightarrow d y$. 如果再令 $d \vec{S}=(d y \wedge d z, d z \wedge d x, d x \wedge d y)$ 那么就有 $a=\vec{b} \cdot d \vec{S}$.
我们会发现 0,3-form 与 1,2-form 之间的对应关系可以推广到高维空间, 建立 k-form 与 n-k-form 的一一对应, 这称为 Hodge Duality.

对 2-d-1-form $a=a_x d x+a_y d y$ 定义外微分 $d a=d a_x \wedge d x+d a_y \wedge d y$. 展开有 $da=\left(\partial_x a_x d x+\partial_y a_x d y\right) \wedge d x+\left(\partial_x a_y d x+\partial_y a_y d y\right) \wedge d y=\left(\partial_x a_y-\partial_y a_x\right) d x \wedge d y$. 而根据 2-d Green Formula 我们知道 $\oint_{\partial D}\left(a_x d x+a_y d y\right)=\int_D\left(\partial_x a_y-\partial_y a_x\right) d x d y$. 于是有 $\int_{\partial D} a=\int_D d a$.

对 3-d-1-form $a=\vec{a} \cdot d \vec{x}=a_x d x+a_y d y+a_z d z$ 有外微分 $d a=d a_x \wedge d x+d a_y \wedge d y+d a_z \wedge d z$. 展开有 $d a=\left(\partial_x a_y-\partial_y a_x\right) d x \wedge d y+\left(\partial_y a_z-\partial_z a_y\right) d y \wedge d z+\left(\partial_z a_x-\partial_x a_z\right) d z \wedge d x=(\nabla \times \mathbf{a}) \cdot d \mathbf{S}$. 而根据 3-d Stokes Formula $\oint_{\partial D} \mathbf{a} \cdot d \mathbf{x}=\int_D(\nabla \times \mathbf{a}) \cdot d \mathbf{S}$. 我们发现了一样的式子 $\int_{\partial D} a=\int_D d a$ 成立.

对 3-d-2-form $a=a_{12} d x \wedge d y+a_{23} d y \wedge d z+a_{31} d z \wedge d x$ 有外微分 $d a=d a_{12} \wedge d x \wedge d y+d a_{23} \wedge d y \wedge d z+d a_{31} \wedge d z \wedge d x$ 展开有 $d a=\left(\partial_3 a_{12}+\partial_1 a_{23}+\partial_2 a_{31}\right) d x \wedge d y \wedge d z=(\nabla \cdot \mathbf{b}) d x \wedge d y \wedge d z$. 而根据 3-d Gauss Theorem 有 $\oint_{\partial V} \mathbf{b} \cdot d \mathbf{S}=\int_V(\nabla \cdot \mathbf{b}) d V$ 我们又得到了 $\int_{\partial D} a=\int_D d a$ 成立.

综上, 我们可可以得到一个 Generalized Stokes Formula: $\int_{\partial D} \alpha=\int_D d \alpha$. 其中 $\alpha$ 是 3-d-k-1-form, D 是 3-d 中的 k-dim 曲面. 而外微分 $d\alpha$ 就是一个 k-form. 我们发现利用外微分, 上述结果统一了.

更进一步, 对 n-d-k-1-form $\alpha=\frac{1}{(k-1)!} \alpha_{i_1 i_2 \ldots i_{k-1}} d x^{i_1} \wedge d x^{i_2} \wedge \ldots \wedge d x^{i_{k-1}}$ 可以定义其外微分: 
$$
d \alpha=\frac{1}{(k-1)!}\left(\partial_j \alpha_{i_1 i_2 \ldots i_{k-1}}\right) d x^j \wedge d x^{i_1} \wedge d x^{i_2} \wedge \ldots \wedge d x^{i_{k-1}}
$$
外微分的性质: $d^2\alpha=0$. 因为两个偏导可以交换位置结果不变, 形成了对称分量, 最终求和后为 0.

如果 $d\alpha=0$ 称 $\alpha$ 为闭形式.

如果 $\alpha=d\beta$ 称 $\alpha$ 为恰当形式. 所以任何恰当形式都是闭形式.

保守力的定义为 $\sum_i \mathbf{F}_i \cdot d \mathbf{x}_i=-d V$. 我们可以写成形式: $F_\mu d x^\mu=-d V\left(x^1, \ldots, x^{3 N}\right)$ 称为力1形式, 简记为 $F=-dV$ 显然这是一个恰当形式, 也是闭形式 $dF=0$, 而 V 就是势能0形式. 具体地, $d F=\left(\partial_\mu F_\nu\right) d x^\mu \wedge d x^\nu=\left[\frac{1}{2}\left(\partial_\mu F_\nu-\partial_\nu F_\mu\right)+\frac{1}{2}\left(\partial_\mu F_\nu+\partial_\nu F_\mu\right)\right] d x^\mu \wedge d x^\nu=\frac{1}{2}\left(\partial_\mu F_\nu - \partial_\nu F_\mu\right) d x^\mu \wedge d x^\nu=0$. 于是有 $\partial_\mu F_\nu-\partial_\nu F_\mu=0, \nabla \times \vec{F}=0$ 即保守力无旋, 而 $\int_{\partial D} F=\int_D d F=0$ 代表保守力闭合曲线做功为零.

## 2. Minimal Action Principle

Outline: 
- Principle of Least Action in Phase Space $\Longleftrightarrow$ Hamiltonian Canonical Equation
- $\Longrightarrow$ Principle of Least Action in Coordinate Space $\Longrightarrow$ Lagrangian
- Generalized Coordinates & Generalized Momentum $\Longrightarrow$ Application to Constrained System
- Mathematically
	- Fermat's Principle
	- Functional and Variation
	- Variational Method and Functional Derivative
	- Euler-Lagrange Equation

### 2.1 Local and Global Perspective Physics

哈密顿正则方程 $\frac{d \vec{p}}{d t}=-\frac{\partial H}{\partial \vec{x}}, \frac{d \vec{x}}{d t}=\frac{\partial H}{\partial \vec{p}}$ 属于一种蚂蚁视角. 另一个视角则是全局来看, 一条路径有一个 action 作用量: $S[\mathbf{x}(t), \mathbf{p}(t)]=\int[\mathbf{p} \cdot \dot{\mathbf{x}}-H(\mathbf{x}, \mathbf{p})] d t$, 注意这个相空间路径是任意的不一定要满足哈密顿正则方程. 类比到量子力学, 也有类似的两种视角, 算符描述和路径积分描述.

### 2.2 From Fermat's Principle to Variational Method

最小作用量原理源自费马原理的推广. 给定起点终点, 光走的路经一定是最短时间 $t=\int \frac{d l}{v}=\frac{1}{c} \int n(\vec{x})|d \vec{x}|$. 定义 optical path: $S=\int n(\vec{x})|d \vec{x}|$ 如果只考虑二维平面, 那么有 $S=\int n(y) \sqrt{(d x)^2+(d y)^2}=\int n(y) \sqrt{1+y^{\prime}(x)^2} d x$ 且固定端点 $y_a=y(a),y_b=y(b)$. 我们可以把这个问题做出抽象: 令 $L(y,y')=n(y) \sqrt{1+y^{\prime}(x)^2}$ 有 $S[y(x)]=\int dx L(y,y')$. 这是一个泛函.

我们现在要求泛函极值, 可以先简单地认为一个泛函就是有无穷多离散的自变量: $d S=S\left(y_1+d y_1, y_2+d y_2, \cdots\right)-S\left(y_1, y_2, \cdots\right)=\sum_i \frac{\partial S}{\partial y_i} d y_i=0$, 我们可以重写为: $d S\left[y_x\right]=S\left[y_x+d y_x\right]-S\left[y_x\right]=\sum_x \frac{\partial S}{\partial y_x} d y_x$, 进一步重写为: $\delta S[y(x)]=S[y(x)+\delta y(x)]-S[y(x)]=\int dx \frac{\delta S}{\delta y(x)}\delta y(x)$. 我们称中间这个量为泛函导数 Functional Derivative $\frac{\delta S}{\delta y(x)}$. 一个简单的例子: $\delta y(x)=\int d x^{\prime} \delta\left(x-x^{\prime}\right) \delta y\left(x^{\prime}\right)$ 那么 $\frac{d y(x)}{\delta y\left(x^{\prime}\right)}=\delta\left(x-x^{\prime}\right)$.

现在计算泛函极值 $S[y(x)]=\int dx L(y,y'), \delta y(a)=\delta y(b)=0$. 首先有
$$\begin{aligned} \delta L\left(y, y^{\prime}\right) & =L\left(y+\delta y, y^{\prime}+\delta y^{\prime}\right)-L\left(y, y^{\prime}\right) \\ & =\frac{\partial L}{\partial y} \delta y+\frac{\partial L}{\partial y^{\prime}} \delta y^{\prime}=\frac{\partial L}{\partial y} \delta y+\frac{\partial L}{\partial y^{\prime}}(\delta y)^{\prime}\end{aligned}$$
利用 $\delta d x=d \delta x=\delta x=0$ 和 $\delta L(x, \dot{x})=\frac{\partial L}{\partial x} \delta x+\frac{\partial L}{\partial \dot{x}} \delta \dot{x}$ 和分部积分:
$$
\begin{aligned}
\delta S[y(x)] & = \int_a^b d x \delta L\left(y, y^{\prime}\right) \\
& =\int_a^b d x\left[\frac{\partial L}{\partial y} d y+\frac{\partial L}{\partial y^{\prime}}(\partial y)^{\prime}\right] \\
& =\int_a^b d x\left[\frac{\partial L}{\partial y} \delta y+\frac{d}{d x}\left(\frac{\partial L}{\partial y^{\prime}} d y\right)-\delta y \frac{d}{d x}\left(\frac{\partial L}{\partial y^{\prime}}\right)\right] \\
& =\int_a^b d x \frac{d}{d x}\left(\frac{\partial L}{\partial y^{\prime}} \delta y\right)+\int_a^b d x\left[\frac{\partial L}{\partial y} \delta y-\delta y \frac{d}{d x}\left(\frac{\partial L}{\partial y^{\prime}}\right)\right] \\
& =\left.\frac{\partial L}{\partial y^{\prime}} \delta y\right|_a
{ #b}
+\int_a^b d x\left(\frac{\partial L}{\partial y}-\frac{d}{d x}\left(\frac{\partial L}{\partial y^{\prime}}\right)\right) \delta y \\
& =\int_a^b d x\left(\frac{\partial L}{\partial y}-\frac{d}{d x}\left(\frac{\partial L}{\partial y^{\prime}}\right)\right) \delta y=0 .
\end{aligned}
$$
所以泛函导数为: 
$$
\frac{d S}{\delta y(x)}=\frac{\partial L}{\partial y}-\frac{d}{d x}\left(\frac{\partial L}{\partial y^{\prime}}\right)=0
$$
这就是 Euler-Lagrange Equation.

> [!Example]
> 
如果回到光路的例子: $\mathcal{L}\left(y \cdot y^{\prime}\right)=n(y) \sqrt{1+\left(y^{\prime}\right)^2}$. 可以计算出$$\begin{aligned}
\frac{d n}{d y} \sqrt{1+\left(y^{\prime}\right)^2}-\frac{d}{d x}\left(n(y) \frac{y^{\prime}}{\sqrt{1+\left(y^{\prime}\right)^2}}\right)=0 \\
\left(1+\left(y^{\prime}\right)^2\right) \frac{d n}{d y}-n(y) y^{\prime \prime}=0 \\
\frac{d}{d x}\left(\frac{n(y)}{\sqrt{1+(y')^2}}\right)=0 \Leftrightarrow \frac{n(y)}{\sqrt{1+(y')^2}}=C
\end{aligned}$$

### 2.3 Principle of Least Action in Phase Space

现在考虑相空间作用量: $S[\mathbf{x}(t), \mathbf{p}(t)]=\int[\mathbf{p} \cdot \dot{\mathbf{x}}-H(\mathbf{x}, \mathbf{p})] d t$. 这同样是一个泛函极值问题: $S[\vec{x}(t), \vec{p}(t)]=\int_{t_i}^{t_f} d t L(\vec{x}, \vec{p}, \dot{\vec{x}})$. 不过此时我们不能直接使用 Euler-Lagrange Equation. 因为我们不能同时固定住 $(\vec{x}(t), \vec{p}(t))$ 的起点和终点. 正确的做法是让 $\delta \vec{x}\left(t_i\right)=\delta \vec{x}\left(t_f\right)=0$ 让动量自由.
$$\begin{aligned} \delta S[\vec{x}(t), \vec{p}(t)] & =\int_{t_i}^{t_f}[\delta \vec{p} \cdot \dot{\vec{x}}+\vec{p} \cdot \delta \dot{\vec{x}}-\delta H(\vec{x}, \vec{p})] d t . \\ & =\int_{t_i}^{t_f}\left[\delta \vec{p} \cdot \dot{\vec{x}}+\frac{d}{d t}(\vec{p} \cdot \delta \vec{x})-\delta \vec{x} \cdot \dot{\vec{p}}-\delta H(\vec{x} \cdot \vec{p})\right] d t \\ & =\left.\vec{p} \cdot \delta \vec{x}\right|_{t_i} ^{t_f}+\int_{t_i}^{t_f}[\delta \vec{p}\cdot \dot{\vec{x}}-\delta \vec{x} \cdot \dot{\vec{p}}-\delta H(\vec{x} \cdot \vec{p})] d t \\ & =\int_{t_i}^{t_f}\left[\delta \vec{p} \cdot \vec{x}-\delta \vec{x} \cdot \dot{\vec{p}}-\frac{\partial H}{\partial \vec{x}} \cdot \delta \vec{x}-\frac{\partial H}{\partial \vec{p}} \cdot \delta \vec{p}\right] d t \\ & =\int_{t_i}^{t_f}\left[\left(\dot{\vec{x}}-\frac{\partial H}{\partial \vec{p}}\right) \cdot \delta \vec{p}-\left(\dot{\vec{p}}+\frac{\partial H}{\partial \vec{x}}\right) \cdot \delta \vec{x}\right] d t=0 .\end{aligned}$$
我们实际上推导出了 Hamiltonian Canonical Equation, 二者是等价的.
$$\frac{\delta S}{\delta \vec{p}(t)}=\dot{\vec{x}}-\frac{\partial H}{\partial \vec{p}}=0 . \quad \frac{\delta S}{\delta \vec{x}(t)}=-\left(\dot{\vec{p}}+\frac{\partial H}{\partial \vec{x}}\right)=0$$
对于 general Hemilton system, 我们实际上没有必要要求 $p=m\dot{x}$, 真正的关系式为: $\dot{x}=\frac{\partial H}{\partial p}$.

多粒子情形同理: $S[x(t),p(t)]=\int_{t_i}^{t_f} \operatorname{dt}\left[p_\mu \dot{x}^\mu-H(x, p)\right]$. 正则方程为: $\dot{x}^\mu=\frac{\partial H}{\partial p_\mu}, \dot{p}_\mu=-\frac{\partial H}{\partial x^\mu}$.

作用量依赖于哈密顿量, 有时是很难写出来的, 而下面我们会将 phase space 转换为 coordinate space, 在 coordinate space 下我们往往可以根据对称性来写出 action. 也就是说 symmetry 会约束 action.

### 2.4 Principle of Least Action in Coordinate Space

实际上我们通常说的最小作用两都是在坐标空间的 coordinate space, 这可以由 phase space 导出. 其动机可以考虑一个二元函数求极值, 通常我们直接求解 $\frac{\partial S}{\partial x}=0, \frac{\partial S}{\partial y}=0$. 但是等价地, 我们可以从从 $\frac{\partial S}{\partial y}=0$ 中求解出 $y=\phi(x)$ 并得到 $S(x,\phi(x))$ 然后在求导 $\frac{d S}{d x}=\frac{\partial S}{\partial x}+\frac{\partial S}{\partial y} \frac{\partial \phi}{\partial x}=0$.

那么对于作用量 $S[\mathbf{x}(t), \mathbf{p}(t)]$ 的极值, 正常思路是求解 $\frac{\delta S}{\delta x(t)}=0, \frac{\partial S}{\delta p(t)}=0$ 这也符合上面的推导, 等价地, 我们可以先求解 $\frac{\delta S}{\delta \vec{p}(t)}=\dot{x}-\frac{\partial H}{\partial \vec{p}}=0$ 得到 $\vec{p}(t)=\phi(\vec{x}(t)) \Rightarrow S[\vec{x}(t), \phi(\vec{x}(t))]$. 我们可以记为 $S[\vec{x}(t)]$. 回忆一下 action in phase space 的被积函数: $L(\mathbf{x}, \mathbf{p}, \dot{\mathbf{x}})=\mathbf{p} \cdot \dot{\mathbf{x}}-H(\mathbf{x}, \mathbf{p})$, 我们会发现, 第一步求解 $\frac{\delta S}{\delta \vec{p}(t)}=\dot{x}-\frac{\partial H}{\partial \vec{p}}=0$ 就是在对 $L(\mathbf{x}, \mathbf{p}, \dot{\mathbf{x}})$ 求关于 $p$ 的极值, 所以我们定义一个新函数 $L(\mathbf{x}, \dot{\mathbf{x}})=\operatorname{extrem}_{\mathbf{p}} L(\mathbf{x}, \mathbf{p}, \dot{\mathbf{x}})=\operatorname{extrem}_{\mathbf{p}}[\mathbf{p} \cdot \dot{\mathbf{x}}-H(\mathbf{x}, \mathbf{p})]$, 那么很显然新的坐标空间作用量泛函就是 $S[\mathbf{x}(t)]=\int_{t_i}^{t_f} L(\mathbf{x}, \dot{\mathbf{x}}) d t$ 而此时的 $L(\mathbf{x}, \dot{\mathbf{x}})$ 就称为 Lagrangian. 这就是 least action in coordinate space 和 least action in phase space 是等价的.

很显然, 坐标空间的最小作用量原理完全可以用前面导出来的欧拉-拉格朗日方程来处理了:
$$
\frac{\partial L}{\partial \mathbf{x}}-\frac{d}{d t}\left(\frac{\partial L}{\partial \dot{\mathbf{x}}}\right)=0
$$
这个方程也常称为拉格朗日方程.

Lagrangian $L(\mathbf{x}, \dot{\mathbf{x}})$ 和 Hamiltonian $H(\mathbf{x}, \mathbf{p})$ 实际上是由 Legendre Transformation 关联起来的:
$$\begin{aligned}\operatorname{extrem}_{\dot{\mathbf{x}}}[\mathbf{p} \cdot \dot{\mathbf{x}}-L(\mathbf{x}, \dot{\mathbf{x}})]=H(\mathbf{x}, \mathbf{p}) \\ \operatorname{extrem}_{\mathbf{p}}[\mathbf{p} \cdot \dot{\mathbf{x}}-H(\mathbf{x}, \mathbf{p})] = L(\mathbf{x}, \dot{\mathbf{x}}) \end{aligned}$$
证明为:
$$\begin{aligned} & \operatorname{extrem}_{\dot{\mathbf{x}}}[\mathbf{p} \cdot \dot{\mathbf{x}}-L(\mathbf{x}, \dot{\mathbf{x}})] \\ = & \operatorname{extrem}_{\dot{\mathbf{x}}}\left[\mathbf{p} \cdot \dot{\mathbf{x}}-\operatorname{extrem}_{\mathbf{p}^{\prime}}\left[\mathbf{p}^{\prime} \cdot \dot{\mathbf{x}}-H\left(\mathbf{x}, \mathbf{p}^{\prime}\right)\right]\right] \\ = & \operatorname{extrem}_{\dot{\mathbf{x}}} \operatorname{extrem}_{\mathbf{p}^{\prime}}\left[\left(\mathbf{p}-\mathbf{p}^{\prime}\right) \cdot \dot{\mathbf{x}}+H\left(\mathbf{x}, \mathbf{p}^{\prime}\right)\right] \\ = & \operatorname{extrem}_{\mathbf{p}^{\prime}, \dot{\mathbf{x}}}\left[\left(\mathbf{p}-\mathbf{p}^{\prime}\right) \cdot \dot{\mathbf{x}}+H\left(\mathbf{x}, \mathbf{p}^{\prime}\right)\right] \\ = & H(\mathbf{x}, \mathbf{p}) .\end{aligned}$$

> [!Example]
> 单粒子: $H(\mathbf{x}, \mathbf{p})=\frac{\mathbf{p}^2}{2 m}+V(\mathbf{x})$ 由哈密顿正则方程能得到 $\mathbf{p}=m \dot{\mathbf{x}}$, 根据勒让得变换能得到拉格朗日量 $L(\mathbf{x}, \dot{\mathbf{x}})=\operatorname{extrem}_{\mathbf{p}}\left[\mathbf{p} \cdot \dot{\mathbf{x}}-\frac{\mathbf{p}^2}{2 m}-V(\mathbf{x})\right]=\frac{1}{2} m \dot{\mathbf{x}}^2-V(\mathbf{x})$ 正好为动能减去势能, 这个结论也可以推广到多粒子情形. 于是坐标空间作用量为: $S[\mathbf{x}(t)]=\int_{t_i}^{t_f} d t\left[\frac{1}{2} m \dot{\mathbf{x}}^2-V(\mathbf{x})\right]$. 拉格朗日方程为: $m \frac{d^2 \mathbf{x}}{d t^2}=-\frac{\partial V}{\partial \mathbf{x}}$. 正好给出了牛顿定律.

> [! Example]
> Lorentz Force: 单粒子的 Lagrangian 是一个速度的二次型, 如果引入一个速度的一阶项 $\vec{A} \cdot \dot{\vec{x}}$ 会怎么样. 如果 $\vec{A}$ 是常数, 那么实际上积分后对作用量的贡献为 $\vec{A} \cdot\left(\vec{x}\left(t_f\right)-\vec{x}\left(t_i\right)\right)$ 但是因为端点是固定的, 所以变分时直接归零了, 对系统运动没有影响. 所以最少也要让 $\vec{A}$ 是依赖 $\vec{x}$ 的:
> $$L=\frac{1}{2} m \dot{\mathbf{x}}^2+\mathbf{A}(\mathbf{x}) \cdot \dot{\mathbf{x}}-V(\mathbf{x}).$$
于是作用量为:$$\begin{aligned}
S[\mathbf{x}(t)] & =\int_{t_i}^{t_f} d t\left[\frac{1}{2} m \dot{\mathbf{x}}^2+\mathbf{A}(\mathbf{x}) \cdot \dot{\mathbf{x}}-V(\mathbf{x})\right] \\
& =\int_{t_i}^{t_f} d t\left[\frac{1}{2} m \dot{\mathbf{x}}^2-V(\mathbf{x})\right]+\int A_j(\mathbf{x}) \cdot d x^j
\end{aligned}$$
利用 $\delta t=\delta d t=d \delta t=0 .$ 对作用量求变分:$$\begin{aligned} \delta S[\vec{x}(t)] & =\int_{i_i}^{t_f} d t \cdot \delta\left[\frac{1}{2} m \dot{\vec{x}}-V(\vec{x})\right]+\delta \int A_j(\vec{x}) \cdot d x^j \\ & =\int_{t_i}^{t_f} d t\left[-\frac{\partial V}{\partial \vec{x}} \delta \vec{x}+m \dot{\vec{x}} \delta \dot{\vec{x}}\right]+\delta \int A_j(\vec{x}) \cdot d x^j \\
& =\int_{t_i}^{t_f} d t\left[-\frac{\partial V}{\partial \vec{x}} \delta \vec{x}+m \dot{\vec{x}}(\delta \vec{x})^{\prime}\right]+\delta \int A_j(\vec{x}) \cdot d x^j \\
& =\int_{t_i}^{t_f} d t\left[-\frac{\partial V}{\partial \vec{x}} \delta \vec{x}+\frac{d}{d t}(m \dot{\vec{x}} \cdot \delta \vec{x})-\delta \vec{x} \cdot \frac{d}{d t}(m \dot{\vec{x}})\right]+\delta \int A_j(\vec{x}) \cdot d x^j \\
& =\left.m\dot{\vec{x}} \cdot \delta \vec{x}\right|_{t_i} ^{t_f}-\int_{t_i}^{t_f} d t\left[\frac{\partial V}{\partial \vec{x}}+m \ddot{\vec{x}}\right] \cdot \delta \vec{x}+\delta \int A_j(\vec{x}) \cdot d x^j \\
& =-\int_{t_i}^{t_f} d t\left[m \ddot{\vec{x}}_i+\partial_i V(\vec{x})\right] \delta x^i+\delta \int A_j(\vec{x}) d x^j \\
& =-\int_{t_i}^{t_j} d t\left[m \ddot{\vec{x}}_i+\partial_i V(\vec{x})\right] \delta x^i+\int A_i d \delta x^i+\partial_i A_j \delta x^i d x^j \\
& =-\int_{t_i}^{t_j} d t\left[m \ddot{\vec{x}_i}+\partial_i V(\vec{x})\right] \delta x^i+\int d\left(A_i \delta x^i\right)+\int \partial_i A_j \delta x^i d x^j-\delta x^i d A_i \\
& =-\int_{t_i}^{t_j} d t\left[m \ddot{\overrightarrow{x_i}}+\partial_i V(\vec{x})\right] \delta x^i+\int \partial_i A_j \delta x^i d x^j-\partial_j A_i d x^j \delta x^i \\
& =-\int_{t_i}^{t_j} d t\left[m \ddot{\overrightarrow{x_i}}+\partial_i V(\vec{x})\right] \delta x^i+\int\left(\partial_i A_j-\partial_j A_i\right) d x^j \delta x^i . \\
& =-\int_{t_i}^{t_j} d t\left[m \ddot{\overrightarrow{x_i}}+\partial_i V(\vec{x})-F_{i j} \dot{x}^j\right] \delta x^i=0 .
\end{aligned}$$最后一行引入了 $F_{ij}=\partial_i A_j-\partial_j A_i$. 于是有了结果:
$$\begin{aligned}\frac{\partial S}{\partial x^{(i)}(t)} & = -\left[m \ddot{\vec{x}_i}+\partial_i V(\vec{x})-F_{i j} \dot{x}^j\right]=0 \\ \Rightarrow m \ddot{x}_i & = -\partial_i V(\vec{x})+F_{i j} \dot{x}^j \end{aligned}$$
事实上, $F_{x y}=\partial_x A_y-\partial_y A_x=(\nabla \times \vec{A})_z$, 这实际上是磁场 $\vec{B}$ 的分量. 借用 Levi-Silveta symbol $F_{ij}=\varepsilon_{ijk}B_k$ 有:$$m \ddot{x}_i=-\partial_i V(\vec{x})+\varepsilon_{i j k} \dot{x}^j B^k$$这就是: $m \ddot{x}=-\nabla V+\dot{\vec{x}} \times \vec{B}$. 这已经很像洛伦兹力了, 为了能精确得到洛伦兹力, 我们只需要把 $\vec{A}$ 替换为 $q\vec{A}$ 就可以了,  $\vec{A}$ 被称为 vector potential $\vec{B}=\nabla \times \vec{A}$. 所以只需要在作用量中添加一个速度一阶项且系数依赖 x 那么就可以自然获得洛伦兹力了. 正确地描述洛伦兹力的 Lagrangian 为: $$L(\mathbf{x}, \dot{\mathbf{x}})=\frac{1}{2} m \dot{\mathbf{x}}^2+q \mathbf{A}(\mathbf{x}) \cdot \dot{\mathbf{x}}-V(\mathbf{x})$$
使用勒让得变换, 先求极值: $$
\frac{\partial}{\partial \dot{\mathbf{x}}}[\mathbf{p} \cdot \dot{\mathbf{x}}-L(\mathbf{x}, \dot{\mathbf{x}})]=0 \Leftrightarrow \mathbf{p}=\frac{\partial L}{\partial \dot{\mathbf{x}}}=m\dot{\mathbf{x}}+q\mathbf{A}$$
这就是一个 $\mathbf{p}\neq m\mathbf{\dot{x}}$ 的例子, 而是有 $\dot{\mathbf{x}}=(\mathbf{p}-q \mathbf{A}) / m$, 进而有哈密顿量:$$H(\mathbf{x}, \mathbf{p})=\operatorname{extrem}_{\dot{\mathbf{x}}}[\mathbf{p} \cdot \dot{\mathbf{x}}-L(\mathbf{x}, \dot{\mathbf{x}})]=\frac{(\mathbf{p}-q \mathbf{A})^2}{2 m}+V(\mathbf{x})$$
可见, 相比 Lagrangian, 这个 Hamiltonian 难猜得多.

而最小作用量原理并不是万能的, 他恰好只能描述经典物理系统的运动微分方程, 但无法描述诸如非保守系统或耗散系统等更复杂的系统, 因为变分原理或作用量是具有高度对称性的, 数学上体现为泛函二阶导的对称性, 比如交换两个时间变量之后应该保持不变, 但是如果运动方程中出现了速度的一阶项, 那往往系统演化会出现明确的时间指向性, 这类方程通常需要引入额外的“瑞利耗散函数 (Rayleigh Dissipation Function)”才能强行纳入拉格朗日框架，但那已经不是纯粹的作用量原理了。

> [!Example]
> 对于 $\frac{\delta S}{\delta x(t)}=\dot{x}(t)$, 我们可以计算得到 $\frac{\delta^2 S}{\delta x\left(t^{\prime}\right) \delta x(t)}=\frac{\delta \dot{x}(t)}{\delta x\left(t^{\prime}\right)}=\frac{d}{d t}\left(\frac{\delta x(t)}{\delta x\left(t^{\prime}\right)}\right)=\frac{d}{d t} \delta\left(t-t^{\prime}\right)$. 但是交换时间变量发现, 二阶导变负了, 所以并不存在这样的作用量满足这个一维运动. 热扩散同理.

进一步, 经典物理系统中发生的真实路径也并不一定是作用量的极小值, 而通常只是作用量泛函的稳定值，或者说驻定值，Saddle point value。这是因为确定极大或极小值需要对泛函求二阶导来判定, 也就是说会和 $\delta x$ 如何使泛函变化有关, 因为 $\delta x$ 在 $t_1$ 和 $t_2$ 都是 0, 所以可以对 $\delta x$ 做正弦展开 $\delta x(t)=\varepsilon \sum_n a_n \sin \left(\omega_n\left(t-t_1\right)\right)$ 其中 $\omega_n=\frac{n \pi}{t_2-t_1}$, 真实路径可以认为是无穷维向量 $(a_1,a_2,\cdots)$ 取原点的结果. 那么可以想见, 对于不同的 $S$ 随着 $a_n$ 取不同值, 会得到不同性质的 saddle point.

> [!Example]
> 考虑一维谐振子: $S=\int_{t_1}^{t_2} \frac{m}{2}\left(\dot{x}^2-\omega^2 x^2\right) d t$. 一阶变分为零, 二阶变分为:  $\delta^2 S=\int_{t_1}^{t_2} \frac{m}{2}\left[(\delta \dot{x})^2-\omega^2(\delta x)^2\right] d t$. 那么根据 $\delta \dot{x}(t)=\varepsilon \sum_n a_n \omega_n \cos \left(\omega_n\left(t-t_1\right)\right)$ 就可以得到 $\delta^2 S=\varepsilon^2 \frac{m}{4}\left(t_2-t_1\right) \sum_n a_n^2\left(\omega_n^2-\omega^2\right)$. 所以当 $\omega_1>\omega$ 即 $t_2-t_1<\frac{T}{2}$ 时作用量取极小值, 否则就是鞍点了.

### 2.5 Generalized Coordinates and Generalized Momentum

之前的描述只涉及到单粒子和多粒子情形的直角坐标, 作用量描述实际上可以拓展到任何坐标, 这对于求解一大类约束系统很有帮助.

理想约束系统: 约束力对系统所有可能的满足约束条件的运动 (不管它是否真实发生) 均不做功。从而只要不破坏约束条件，那约束力对这一系统的能量就没有贡献，也就是对哈密顿量没有贡献，从而我们就可以根本不去管约束力。这时候就可以使用这两章所发展起来的力学处理框架。

广义坐标：描述理想约束系统的独立变量。自由度：独立变量数目。

这些彼此独立的广义坐标的变分也是彼此独立的， 所以我们仍然可以通过最小作用量原理推导出哈密顿正则方程或拉格朗日方程。

接下来我们希望找到广义动量。在相空间作用量 $S=\int d t\left[p_\mu \dot{x}^\mu-H(x, p)\right]=\int p_\mu d x^\mu-\int H d t$ 推导微分运动方程是，我们应该能感受到最终微分方程的形态主要是由作用量的第一项决定的，毕竟第二项就是哈密顿量，第一项有一个专门的术语叫做 symplectic potential 辛势 $\Theta=p_\mu dx^\mu,\mu=1,2,\cdots,3N$，我们希望变换为广义坐标后辛势形式不变：$\Theta=p_\mu dx^\mu=p_adq^a,a=1,2,\cdots,s$，区别在于坐标 $\mu$ 彼此可能不独立，但是坐标 $a$ 彼此独立，满足这个形式的 $p_a$ 就是广义动量：$p_a=p_\mu \frac{\partial x^\mu}{\partial q^a}$，于是相空间作用量可以改写为：$S=\int d t\left[p_a \dot{q}^a-H(q, p)\right]$，自然地得到同样形式的哈密顿正则方程：$\frac{d q^a}{d t}=\frac{\partial H}{\partial p_a}, \frac{d p_a}{d t}=-\frac{\partial H}{\partial q^a}$。

> [!example]
> 单粒子约束在 $x^2+y^2=R^2$ 上，广义坐标 $\theta$，有 $x=R\cos\theta,y=R\sin\theta,\Theta=p_xdx+p_ydy=p_\theta d\theta$ 于是有 $p_\theta=\left[-p_x \sin (\theta)+p_y \cos (\theta)\right] R$。再利用约束 $p_x \cos (\theta)+p_y \sin (\theta)=0$ 可以得到 $\mathbf{p}^2=p_\theta^2 / R^2$。于是哈密顿量为 $H=\frac{\mathbf{p}^2}{2 m}+V=\frac{p_\theta^2}{2 m R^2}+V(\theta)$，进而正则方程为 $\dot{\theta}=\frac{\partial H}{\partial p_\theta}=\frac{p_\theta}{m R^2},\dot{p}_\theta=-\frac{\partial H}{\partial \theta}=-\frac{\partial V}{\partial \theta}$。

上面是从作用量出发，我们也可以从拉格朗日量出发，我们可以可以直接做坐标变换获得 $L(q,\dot{q})$，相应的作用量为 $S[q(t)]=\int d t L(q, \dot{q})$，拉格朗日方程为：$\frac{\partial L}{\partial q^a}-\frac{d}{d t}\left(\frac{\partial L}{\partial \dot{q}^a}\right)=0$，然后经过勒让得变换得到哈密顿量 $H(q, p)=\operatorname{extrem}_{\left\{\dot{q}^a\right\}}\left[p_b \dot{q}^b-L(q, \dot{q})\right]$，为了求解勒让得变换，我们需要计算 $\frac{\partial}{\partial \dot{q}^a}\left[p_b \dot{q}^b-L(q, \dot{q})\right]=0 \Rightarrow p_a=\frac{\partial L}{\partial \dot{q}^a}$ 这就可以作为从拉格朗日量出发的广义动量的定义。

> [!example]
> 双摆，两个广义坐标$\theta_1,\theta_2$。这是一个相当复杂的系统，当能量大到一定程度时，系统会变成混沌。 $$\begin{aligned}
T_1 & = \frac{1}{2} m_1 l_1^2 \dot{\theta}_1^2, \quad V_1=-m_1 g l_1 \cos \left(\theta_1\right) \\ x_2 & = l_1 \sin \left(\theta_1\right)+l_2 \sin \left(\theta_2\right), \quad y_2=l_1 \cos \left(\theta_1\right)+l_2 \cos \left(\theta_2\right) \\ T_2 & = \frac{1}{2} m_2\left(\dot{x}_2^2+\dot{y}_2^2\right)=\frac{1}{2} m_2\left(l_1^2 \dot{\theta}_1^2+l_2^2 \dot{\theta}_2^2+2 l_1 l_2 \cos \left(\theta_1-\theta_2\right) \dot{\theta}_1 \dot{\theta}_2\right) \\ V_2 & = -m_2 g y_2=-m_2 g\left(l_1 \cos \left(\theta_1\right)+l_2 \cos \left(\theta_2\right)\right) \\ L & = \frac{1}{2}\left(m_1+m_2\right) l_1^2 \dot{\theta}_1^2+\frac{1}{2} m_2 l_2^2 \dot{\theta}_2^2+m_2 l_1 l_2 \cos \left(\theta_1-\theta_2\right) \dot{\theta}_1 \dot{\theta}_2 \\ & +\left(m_1+m_2\right) g l_1 \cos \left(\theta_1\right)+m_2 g l_2 \cos \left(\theta_2\right) \\ \frac{\partial L}{\partial \theta_1} & -\frac{d}{d t}\left(\frac{\partial L}{\partial \dot{\theta}_1}\right)=0, \quad \frac{\partial L}{\partial \theta_2}-\frac{d}{d t}\left(\frac{\partial L}{\partial \dot{\theta}_2}\right)=0 \end{aligned}
$$

### 2.6 Geometric Understanding

进入下一章前，我们可以从几何的角度重新审视 $q$ 和 $p$ 的本质。在初级力学中，我们往往把它们视为普通的实数变量，但在现代物理框架下，它们生活在完全不同的几何空间中。
- **构型流形 (Configuration Manifold, $\mathcal{M}$)**： 系统的所有可能位置构成的集合不仅仅是一个平直的欧几里得空间 $\mathbb{R}^n$，而是一个 $n$ 维**微分流形** $\mathcal{M}$。一个被限制在球面上运动的质点，其构型空间是一个球面 $S^2$；一个刚体的构型空间包含了转动，是 $SO(3)$ 流形。广义坐标 $q^a$ 实际上是这个流形上的**局部坐标卡 (Local Chart)**。就像我们用经纬度标记地球表面一样，$q^a$ 只是流形局部的数学标签。
- **切丛 (Tangent Bundle, $T\mathcal{M}$) —— 拉格朗日力学的舞台**： 在拉格朗日力学中，系统的状态由位置和速度 $(q, \dot{q})$ 描述。几何上，速度矢量 $\dot{q}$ 并不生活在流形 $\mathcal{M}$ 上，而是生活在流形上某一点 $q$ 的**切空间 (Tangent Space)** $T_q\mathcal{M}$ 中（想象一个紧贴球面的切平面，速度矢量就在这个平面上）。将流形上所有点 $q$ 的所有可能的切空间 $T_q\mathcal{M}$ 集合起来，就形成了**切丛** $T\mathcal{M}=\bigcup_{q \in \mathcal{M}} T_q \mathcal{M}$。因此，拉格朗日量 $L(q, \dot{q})$ 本质上是一个定义在切丛上的标量函数：$L: T\mathcal{M} \rightarrow \mathbb{R}$。
- **余切丛 (Cotangent Bundle, $T^*\mathcal{M}$) —— 哈密顿力学的舞台**： 广义动量的定义是 $p_a = \frac{\partial L}{\partial \dot{q}^a}$。这里有一个微妙但至关重要的几何跳跃：当你对一个矢量（这里是速度 $\dot{q}^a$）求导时，结果在几何变换性质上不再是一个矢量，而是一个**对偶矢量 (Dual Vector)**，也称为**余切矢量**或 **1-形式 (1-form)**。动量 $p$ 生活在切空间 $T_q\mathcal{M}$ 的对偶空间——**余切空间** $T^*_q\mathcal{M}$ 中。将流形上所有点的余切空间集合起来，就形成了**余切丛** $T^*\mathcal{M}$。这也是为什么 $p_a$ 带有下指标（协变指标），而 $q^a$ 带有上指标（逆变指标）。
- **自然配对 (Natural Pairing)**： 这完美解释了作用量中 $p_a \dot{q}^a$ 这一项的物理意义。这**不是**两个矢量之间的点积（点积通常需要度规 $g_{ij}$ 参与），而是余切矢量 $p$ 和切矢量 $\dot{q}$ 之间的**自然配对**（收缩）：$\langle p, \dot{q} \rangle = p_a \dot{q}^a$。这种配对不需要引入度规结构，在任何坐标变换下都是标量。这说明哈密顿力学的相空间结构（辛结构）比拉格朗日力学更底层，因为它不依赖于度规。
- 从拉格朗日力学到哈密顿力学的勒让得变换 (Legendre Transformation)，在几何上是从**切丛** $T\mathcal{M}$ 到**余切丛** $T^*\mathcal{M}$ 的映射。

## 3. Symmetry

- 物理定律的对称性就是某些物理性质的不可分辨性。
- 这种不可分辨性实际上就是我们可以在物理系统中做某些操作， 但是操作前后物理定律保持了完全一致的数学形式。
- 因此物理定律的对称性实际上就是操作前后物理定律的不变性。

### 3.1 Noether Theorem: Symmetry and Conservation Laws

延续上一章，我们可以认为物理定律是由变分作用量为零 $\delta S[q(t)]=0$ 得来的，也就是说变换前后同样需要有 $\delta S[q(t)]=\delta S[\tilde{q}(t)]=0,\tilde{q}(t)=F(q(t))$。为了满足这一点，最简单直接的方式就是变换前后作用量相等 $S[q(t)]= S[\tilde{q}(t)]$。即是说，在对称操作的作用下，作用量泛函保持不变，对称性就是作用量的不变性。

操作可以分为离散性操作和连续性操作，相对应的，对称性也就分为了离散与连续两种。而大名鼎鼎的 Noether Theorem 就是说：每一个连续对称性都会对应一个物理的守恒律。

证明：这里的证明假设操作不会改变时间，不过是可以推广的。假设系统有一个连续的对称性 $G(\theta)$ 其中 $\theta$ 是参数，$\theta=0$ 是恒等变换，$\theta=\varepsilon$ 是无穷小变换，可以有 $q(t) \rightarrow \widetilde{q}(t)=q(t)+\varepsilon F(q(t))$，仍然保持：$\delta S=S[\tilde{q}(t)]-S[q(t)]=\int d t L(\tilde{q}, \dot{\tilde{q}})-\int d t L(q, \dot{q})=0$。想象常数 $\varepsilon$ 变成了一个任意函数 $\varepsilon(t)$ 但有 $\varepsilon(t_i)=\varepsilon(t_f)=0$，于是有 $\delta q=\tilde{q}(t)-q(t)=\varepsilon(t) F(q(t))$，当然，这样的 $\varepsilon(t)$ 就不再是对称变换参数了，因为对称变换参数不能依赖于 $t$，所以这个变换并不是一个对称性，因此不能保持作用量不变，但是如果 $\varepsilon(t)$ 变回常数函数，那作用量将是不变的。为了确定下来 $\delta S$ 考虑以下三点：
- 作用量是某个函数 (拉格朗日量) 对时间的积分，所以作用量的改变量必然具有时间积分的形式。
- 拉格朗日量中只含有 $q(t)$ 的一阶导数，因此作用量的改变量中最多只含有 $ε(t)$ 的一阶导数。
- 将作用量的改变量计算到一阶无穷小项，那这个改变量必然不能含 $ε(t)$，因为这样的项在 $ε(t)$ 变回常数函数时不能变成零。所以这个改变量的一阶小量只能含 $\dot{\varepsilon}$，因此当 $ε(t)$ 变回常数函数时自动得到零。
综合这三点，必有：
$$
\delta S=\int_{t_i}^{t_f} d t\delta L=\int_{t_i}^{t_f} d t(L(\widetilde{q}, \dot{\widetilde{q}})-L(q, \dot{q}))=\int_{t_i}^{t_f} d t Q(q, \dot{q}) \dot{\varepsilon}(t)
$$
而对于真实物理路径 $\delta S=0$ 再利用分部积分就有：$\delta S=-\int_{t_i}^{t_f} d t \dot{Q}(q, \dot{q}) \varepsilon(t)=0,\frac{dQ}{dt}=0$。即 $Q(q,\dot{q})$ 是一个守恒量。这实际上也给了我们一个寻找守恒量的方式。

> [!example]
> 空间平移不变性与动量守恒。坐标平移：$\mathbf{x}_i \rightarrow \widetilde{\mathbf{x}}_i=\mathbf{x}_i+\mathbf{a}$. 取 $\mathbf{a}=\varepsilon$ 有 $$0=\delta L=L\left(\mathbf{x}_i+\varepsilon, \dot{\mathbf{x}}_i\right)-L\left(\mathbf{x}_i, \dot{\mathbf{x}}_i\right)=\varepsilon \cdot \sum_j \frac{\partial L}{\partial \mathbf{x}_j}$$取 $\varepsilon$ 为 $\varepsilon(t)$ 有$$
\begin{aligned}
\delta S & =\int d t \delta L=\int d t\left[\sum_j \frac{\partial L}{\partial \mathbf{x}_j} \cdot \delta \mathbf{x}_j+\sum_j \frac{\partial L}{\partial \dot{\mathbf{x}}_j} \delta \dot{\mathbf{x}}_j\right] \\
& =\int d t\left[\sum_j \frac{\partial L}{\partial \mathbf{x}_j} \cdot \varepsilon+\sum_j \frac{\partial L}{\partial \dot{\mathbf{x}}_j} \cdot \dot{\varepsilon}\right]=\int d t\left(\sum_j \frac{\partial L}{\partial \dot{\mathbf{x}}_j}\right) \cdot \dot{\varepsilon}
\end{aligned}
$$于是有动量守恒为：$$\sum_j \frac{\partial L}{\partial \dot{\mathbf{x}}_j}=\sum_j \mathbf{p}_j=\mathbf{p}$$

> [!example]
> 空间旋转不变性与角动量守恒。假设 $d$ 维空间 $\vec{x}=\left(x^1, x^2, \cdots x^d\right)=x^\alpha ,\alpha=1,2, \cdots d .$ 对无穷小旋转有$$
\delta x_\alpha=\varepsilon_{\alpha \beta} x^\beta . \delta \vec{x}^2=0=\vec{x} \delta \vec{x}=\varepsilon_{\alpha \beta} x^\alpha x^\beta \Rightarrow \varepsilon_{\alpha \beta}=-\varepsilon_{\beta \alpha} .
$$所以独立变量数目是 $\frac{d(d-1)}{2}$。若 $\varepsilon_{\alpha \beta}$ 是常数，有 $\delta \dot{x}_\alpha=\varepsilon_{\alpha \beta} \dot{x}^\beta$。如果变成 $\varepsilon_{\alpha \beta}(t)$ 则有 $\delta \dot{x}_\alpha=\varepsilon_{\alpha \beta} \dot{x}^\beta+\dot{\varepsilon}_{\alpha \beta} x^\beta$ 进而有：$$\begin{aligned}\delta L & =\frac{\partial L}{\partial \dot{x}^\beta} \dot{\varepsilon}^{\beta \alpha} x_\alpha=p_\beta x_\alpha \dot{\varepsilon}^{\beta \alpha}=-\frac{1}{2}\left(x_\alpha p_\beta-x_\beta p_\alpha\right) \dot{\varepsilon}^{\alpha \beta} . \\ \delta S & = -\frac{1}{2} \int d t\left(x_\alpha p_\beta-x_\beta p_\alpha\right) \dot{\varepsilon}^{\alpha \beta} \end{aligned}$$ 于是有角动量守恒为：$$
J_{\alpha \beta}=x_\alpha p_\beta-x_\beta p_\alpha,\quad J^i=\frac{1}{2} \varepsilon^{i j k} J_{j k}
$$

> [!example]
> 时间平移对称性与能量守恒。对封闭系统，因为 Lagrangian 是不显式包含时间 $t$ 的，此时如果对时间做变换 $t \rightarrow \tilde{t}=t+a, q(t) \rightarrow \tilde{q}(t)=q(\tilde{t})$，作用量是不会变化的：$$
\begin{aligned}
S[q(t)]=\int_{t_i}^{t_f} d t L(q(t), \dot{q}(t)) & \rightarrow \\
\left.S[q(\widetilde{t})]=\int_{t_i-a}^{t_f-a} d t L(q \widetilde{t}), \frac{d}{d t} q(\widetilde{t})\right) & \left.=\int_{t_i}^{t_f} d \widetilde{t} L(q \widetilde{t}), \dot{q}(\widetilde{t})\right) \\
& =\int_{t_i}^{t_f} d t L(q(t), \dot{q}(t))=S[q(t)]
\end{aligned}
$$但是对于开放系统，Lagrangian 显式依赖 $L(q,\dot{q},t)$ 就没有时间平移不变性了。现在考虑变换为 $t \rightarrow \widetilde{t}(t)=t+\varepsilon(t)$ 此时有：$$
\begin{aligned}
S[q(\widetilde{t})] & =\int d t L\left(q(\widetilde{t}), \frac{d}{d t} q(\widetilde{t})\right)=\int d \widetilde{t}\left(\frac{d t}{d \widetilde{t}}\right) L\left(q(\widetilde{t}),\left(\frac{d \widetilde{t}}{d t}\right) \dot{q}(\widetilde{t})\right) \\
& =\int d \widetilde{t}\left(\frac{1}{1+\dot{\varepsilon}}\right) L(q(\widetilde{t}),(1+\dot{\varepsilon}) \dot{q}(\widetilde{t})) \\
& =\int d \widetilde{t} L(q (\widetilde{t}), \dot{q}(\widetilde{t}))-\int d \widetilde{t}(\dot{\varepsilon}) L(q (\widetilde{t}), \dot{q}(\widetilde{t}))+\int d \widetilde{t} \frac{\partial L}{\partial(\dot{q}(\widetilde{t}))} \dot{q}(\widetilde{t})(\dot{\varepsilon}) \\
& =\int d t L(q(t), \dot{q}(t))+\int d t\left[\frac{\partial L}{\partial(\dot{q}(t))} \dot{q}(t)-L(q(t), \dot{q}(t))\right] \dot{\varepsilon}, \\ 0= \delta S & = S[q(\widetilde{t})]-S[q(t)]=\int d t\left[\frac{\partial L}{\partial \dot{q}} \dot{q}-L(q, \dot{q})\right] \dot{\varepsilon}=\int d t\left[p \dot{q}-L(q, \dot{q})\right] \dot{\varepsilon}=\int d tH(q,p) \dot{\varepsilon}
\end{aligned}
$$正好代表了哈密顿量即能量守恒，这个推导也正好就是 time-varying Noether Theorem 的证明。

> [!example]
> 伽利略不变性。变换为：$\mathbf{x} \rightarrow \mathbf{x}+\mathbf{v} t$。考察多粒子作用量为：$S[\mathbf{x}(t)]=\int d t\left[\frac{1}{2} \sum_i m_i \dot{\mathbf{x}}_i^2-\sum_{i<j} V\left(\mathbf{x}_i-\mathbf{x}_j\right)\right]$。我们实际上可以算出变换后的作用量为：$S[\tilde{\mathbf{x}}(t)]=S[\mathbf{x}(t)]+\sum_i m_i\left[\mathbf{x}_i\left(t_f\right)-\mathbf{x}_i\left(t_i\right)\right] \cdot \mathbf{v}+\frac{1}{2} m \mathbf{v}^2\left(t_f-t_i\right)$ 这与原始作用量不同，但是多出来的是端点项，不影响 $\delta S=0$ 所以伽利略变换仍然是这个力学系统的对称性。进一步如果考虑 $\mathbf{x}_i \rightarrow \widetilde{\mathbf{x}}_i=\mathbf{x}_i+\varepsilon(t) t$ 那么可以算出 $\delta S=\int_{t_i}^{t_f} d t\left[\left(\sum_i m_i \dot{\mathbf{x}}_i\right) t-\sum_i m_i \mathbf{x}_i\right] \cdot \dot{\varepsilon}$，所以伽利略变换对称性的守恒量其实为 $\mathbf{K}=\mathbf{p} t-m \mathbf{x}_c=\mathbf{p} t-\sum_i m_i \mathbf{x}_i$，这是显然的。

### 3.2 Symmetry Determines Action

- 作用量可以推导出运动微分方程。
- 作用量可以导出拉格朗日量可以进一步通过勒让得变换导出哈密顿量。
- 作用量的不变性可以导出物理定律的不变性。
那么如何获得一个物理系统的作用量的，基本靠猜，但是以对称性为约束。
- 我们接下来重点讨论通过相对论不变性给出狭义相对论情况下的自由粒子作用量。
- 并重点讨论进一步通过规范不变性再给出电磁场耦合时的带电粒子的作用量。
- 后来，电磁场的规范对称性被杨振宁和米尔斯推广成所谓的非阿贝尔规范对称性。
- 再后来人们发现强相互作用和弱相互作用也分别由一种非阿贝尔规范对称性决定。
- 爱因斯坦又发现引力定律遵循一种广义协变性，更现代的说法为微分同胚不变性，这种对称性既决定了处于引力场中的粒子的作用量，也决定了引力场本身的作用量，从而也就决定了引力场本身的爱因斯坦方程。至此四大基本作用都是由对称性决定的。

### 3.3 Relativistic Invariance and Lorentz Transformation

这里我们不再赘述狭义相对论的基本设置了，我们直接给出两个临近事件在两个线性变换的参考系中的时空坐标的关系：$d t^{\prime 2}-d x^{\prime 2}-d y^{\prime 2}-d z^{\prime 2}=d\tau^{\prime 2}=d\tau^2=d t^2-d x^2-d y^2-d z^2$，这称为 space-time interval invariance 间隔不变性。对于给定的两个时空事件，虽然不同的观测者测到的时间和空间坐标各不相同，但时空间隔 $d\tau$ 是一个绝对的、客观存在的‘物理量’，不随参考系的改变而改变。假如有一个粒子从 $(t, x, y,z)$ 运动到 $(t + dt, x + dx, y + dy,z + dz)$，那么其间隔 $dτ^2$ 就等于一个固定在粒子上的钟在这个过程中所走过的时间的平方（因为在粒子本身的参考系中这个钟的空间坐标改变量为零），所以这时候 $dτ$ 就是这个钟走过的时间，称为粒子的固有时 proper time。间隔的定义和是否有粒子运动无关，而固有时的定义却依赖于一个运动的粒子。因此，这是两个不同的概念，人们常常用不同的记号表示它们。

约定 $x^\mu,\mu=0,1,2,3,t=x^0, x=x^1, y=x^2, z=x^3$，间隔为 $-d \tau^2=\eta_{\mu v} d x^\mu d x^v,-\eta_{00}=\eta_{11}=\eta_{22}=\eta_{33}=1$，$\eta_{\mu\nu}$ 为四维闵可夫斯基时空的度规张量，所谓的闵可夫斯基时空指的就是狭义相对论中的平直时空，内积为 $A \cdot B=A^\mu B_\mu=A_\mu B^\mu=\eta_{\mu v} A^\mu B^v$。狭义相对论中，两个参考系之间的时空坐标变换称作洛伦兹变换，是一个保持间隔不变性的线性变换 $x^{\prime \mu}=\Lambda_v^\mu x^v$，若认为 $y=y',z=z'$ 则有 $-d \tau^2=-d t^2+d x^2=d x^{+} d x^{-},x^+=x+t,x^-=x-t$ 于是必有 $d x^{+^{\prime}} d x^{-^{\prime}}=d x^{+} d x^{-}$ 即存在 $\omega$ 使得 $x^{+^{\prime}}=e^{-\omega} x^{+},x^{-^{\prime}}=e^{\omega} x^{-}$，即：
$$
\begin{aligned}
x^{\prime} & =\cosh (\omega) x-\sinh (\omega) t \\
t^{\prime} & =-\sinh (\omega) x+\cosh (\omega) t
\end{aligned}
$$
考虑物理含义，我们知道 $S'$ 系坐标原点 $x'=0$ 在 $S$ 系中运动速度为 $v$，于是有 $\tanh (\omega)=v$ 进而 $\cosh (\omega)=1 / \sqrt{1-v^2}, \sinh (\omega)=v / \sqrt{1-v^2}$，于是：
$$
\begin{aligned}
t^{\prime} & =\frac{t-v x}{\sqrt{1-v^2}}, \\
x^{\prime} & =\frac{x-v t}{\sqrt{1-v^2}}
\end{aligned}
$$
相对论不变性就是说，相对论粒子的作用量得是洛伦兹变换不变的，唯一的和粒子坐标有关的这种不变量就是粒子的固有时 $dτ$。又由量纲分析，我们可以知道最直接的相对论粒子的作用量为：
$$
S[x(s)]=-m \int d \tau=-m \int d s \sqrt{-\eta_{\mu v} \frac{d x^\mu}{d s} \frac{d x^v}{d s}}
$$
其中 $s$ 是粒子运动轨迹的参数，其中的负号是因为可以正确退化到非相对论极限，显然这个作用量有重参数不变性。比如可以取 $s=\tau$，
$$
S[x(\tau)]=-m \int d \tau=-m \int d \tau \sqrt{-\eta_{\mu v} \frac{d x^\mu}{d \tau} \frac{d x^v}{d \tau}} .
$$
或者取 $s=x^0=t$，有 $d \tau^2=d t^2-d \mathbf{x}^2=d t^2\left(1-\mathbf{v}^2\right)$，此时可以计算和四矢量相对应的四动量 $p^0=\frac{m}{\sqrt{1-\mathbf{v}^2}}, \mathbf{p}=\frac{m \mathbf{v}}{\sqrt{1-\mathbf{v}^2}}, -p^\mu p_\mu=\left(p^0\right)^2-\mathbf{p}^2=m^2$，作用量为：
$$S[\mathbf{x}(t)]=-m \int d t \sqrt{1-\mathbf{v}^2}=-m \int d t+\int d t \frac{1}{2} m \mathbf{v}^2+\ldots$$
于是在低速时，退化到了非相对论的自由粒子的作用量，因为第一项是常数对变分没有影响。

我们可以进一步引入一个辅助变量 $e(s)$ 把作用量写成一个没有根号的形式：
$$
S[e(s), x(s)]=\frac{1}{2} \int d s\left(e^{-1} \eta_{\mu v} \frac{d x^\mu}{d s} \frac{d x^v}{d s}-e m^2\right) .
$$
只需要利用 $\frac{\delta S}{\delta e(s)}=0$ 消去 $e(s)$ 就能得到原来的作用量了，这和从相空间最小作用量原理推导坐标空间最小作用量原理类似。

### 3.4 Coupling with Electromagnetic Fields

现在自由粒子基础上让其与场交互。在 [[Notes/2026/01/19/A Journey Through Classical Mechanics#2.4 Principle of Least Action in Coordinate Space\|最小作用量导出Lorentz Force]] 的例子中我们引入了矢量势 $\mathbf{A}$，和四矢量四动量一样，配合标量电势我们构造四矢量 $A^\mu,\mu=0,1,2,3,A^0=\phi,A^i=A_i,i=1,2,3$，注意 $A^\mu$ 不是物理的，真正物理可测的是电场强度 $\mathbf{E}$ 和磁场强度 $\mathbf{B}$，可以合写成 $F_{i 0}=E_i, F_{i j}=\varepsilon_{i j k} B^k,i, j=1,2,3$，有关系 
$$F_{\mu v}=\partial_\mu A_v-\partial_v A_\mu, \partial_\mu=\frac{\partial}{\partial x^\mu}$$
显然 $F_{\mu\nu}$ 在变换 $A_\mu \rightarrow A_\mu+\partial_\mu \varepsilon$ 下保持不变，其中 $\varepsilon(x)$ 为时空坐标 $x^\mu$ 的任意函数，这个变换称为电磁场的规范变换，用微分形式的语言，则是：$A=A_\mu d x^\mu,A\rightarrow A+d\varepsilon$，因为电磁场都不变，粒子因与电磁场的交互作用下的运动也不会变，所以其作用量也要保持不变，这就是规范对称性。

我们接下来要在 $-m\int d\tau$ 的基础上寻找一个既规范不变又洛伦兹不变的项加上去。那无非是利用 $F$ 或 $A$，如果使用 $F$ 那为了形成洛伦兹标量，最直接的要么是 $F_{\mu \nu} \frac{d x^\mu}{d s} \frac{d x^v}{d s}$ 要么是 $F_{\mu v} F^{\mu v}$，但是前者因为反对称为零，后者则是二阶项，当电磁场较小时可忽略，我们最终发现使用 $A$ 的项 $q\int^b_aA$ 是更合理的，虽然规范变换下 $q \int_a^b A \rightarrow q \int_a^b A+q \int_a^b d \varepsilon=q \int_a^b A+q(\varepsilon(b)-\varepsilon(a))$ 作用量本身是变化的，但是变分之后端点项消失，所以是合理的。相对论性带电粒子完整的作用量为：
$$
\begin{aligned}
S[x(s)] & =-m \int d \tau+q \int A \\
& =-m \int d s \sqrt{-\eta_{\mu v} \frac{d x^\mu}{d s} \frac{d x^v}{d s}}+q \int d s A_\mu \frac{d x^\mu}{d s}  \\
& \approx -m \int d t+\int d t\left[\frac{1}{2} m \mathbf{v}^2-q \phi+q \mathbf{A} \cdot \mathbf{v}\right]+\ldots
\end{aligned}
$$
低速极限下的拉格朗日量：$L \approx \frac{1}{2} m \mathbf{v}^2-q \phi+q \mathbf{A} \cdot \mathbf{v}$，广义动量为 $\mathbf{p}=\frac{\partial L}{\partial \dot{\mathbf{x}}}=m \dot{\mathbf{x}}+q \mathbf{A}$，所以哈密顿量为：
$$
H=\mathbf{p} \cdot \mathbf{v}-L=\mathbf{p} \cdot \frac{\mathbf{p}-q \mathbf{A}}{m}-\left[\frac{1}{2} m\left(\frac{\mathbf{p}-q \mathbf{A}}{m}\right)^2-q \phi+q \mathbf{A} \cdot \frac{\mathbf{p}-q \mathbf{A}}{m}\right]=\frac{(\mathbf{p}-q \mathbf{A})^2}{2 m}+q \phi
$$
我们此时可以借助上一章结尾的几何视角，来深化地理解为什么正则动量不再是 $m\mathbf{v}$，实际上，$\mathbf{p}$ 是**正则动量 (Canonical Momentum)**，它是广义坐标的共轭变量；而 $m\mathbf{v}$ 是**机械动量 (Mechanical/Kinematic Momentum)**。$p \neq mv$ 这一事实是电磁耦合系统的基本特征。分解式 $\mathbf{p} = m\mathbf{v} + q\mathbf{A}$ 并非随意的数学组合，它代表了流形上两种截然不同的几何结构的融合。利用张量记号，正则动量可以写为：
$$
\begin{aligned}
p_i=\frac{\partial L}{\partial v^i} & =\frac{\partial}{\partial v^i}\left(\frac{1}{2} m g_{j k} v^j v^k+q A_j v^j-q \phi\right) \\
& =\frac{1}{2} m g_{j k}\left(\delta_i^j v^k+v^j \delta_i^k\right)+q A_j \delta_i^j \\
& =\frac{1}{2} m\left(g_{i k} v^k+g_{j i} v^j\right)+q A_i \\
& =m g_{i j} v^j+q A_i
\end{aligned}
$$

- **动能项 ($m\mathbf{v}$)**：这一项源于动能 $T = \frac{1}{2} m g_{ij} v^i v^j$。它的存在显式地依赖于 **度规张量 (Metric Tensor)** $g_{ij}$（即测量距离的“尺子”）。如果没有度规，我们无法定义速度的大小 $v^2$，也就无法定义这一部分的动量。这一项代表了粒子的 **惯性 (Inertial)** 属性。
- **相互作用项 ($q\mathbf{A}$)**： 这一项源于耦合项 $q A_i v^i$。在几何上，$A_i$ 是一个 1-形式 (1-form) 场。注意，缩并 $A_i v^i$ **不需要** 度规参与；它是切矢量 ($v$) 与余切矢量 ($A$) 之间的自然配对 (Natural Pairing)。 在纤维丛 (Fiber Bundles) 的语言中，$\mathbf{A}$ 代表了一个 **联络 (Connection)**。它规定了粒子的内部状态（相位）在空间移动时如何进行平移输运。这一项是纯粹 **拓扑/几何** 的，独立于我们如何测量距离。

正则动量 $\mathbf{p}$ 将依赖于度规的惯性信息 ($mv$) 与依赖于联络的几何信息 ($qA$) 结合在了一起。由于 $\mathbf{p}$ 定义为 $L$ 的梯度 ($\partial L / \partial \dot{q}$)，它天然是一个生活在余切丛 $T^*\mathcal{M}$ 上的协变矢量 (1-form)，这使得它成为相空间动力学中最基本的几何对象。

### 3.5 Quantum Extension

透过正则动量，规范不变性，我们得以联系到量子力学，也能更好地理解为什么规范代表的联络为什么携带了粒子的内部相位状态信息。我们接下来考虑，为什么在量子力学中，对应于梯度算符 $-i\hbar\nabla$ 的基本变量是正则动量 $\mathbf{p}$（而非机械动量 $m\mathbf{v}$）。这一结论可以通过考察作用量 $S$ 对 **规范变换 (Gauge Transformations)** 的响应来推导。将对任意标量函数 $\chi(\mathbf{x},t)$ 的规范变换
$$\mathbf{A}^{\prime}=\mathbf{A}+\nabla \chi, \quad \phi^{\prime}=\phi-\frac{\partial \chi}{\partial t}$$
代入拉格朗日量有：
$$
\begin{aligned}
L^{\prime} & =\frac{1}{2} m \mathbf{v}^2-q\left(\phi-\partial_t \chi\right)+q(\mathbf{A}+\nabla \chi) \cdot \mathbf{v} \\
& =\left(\frac{1}{2} m \mathbf{v}^2-q \phi+q \mathbf{A} \cdot \mathbf{v}\right)+q\left(\partial_t \chi+\mathbf{v} \cdot \nabla \chi\right)=L+q \frac{d \chi}{d t}
\end{aligned}
$$
拉格朗日量改变了一个全时间导数项。因此，作用量 $S = \int_{t_1}^{t_2} L dt$ 改变了一个边界项：
$$
S^{\prime}=S+q\left[\chi\left(t_2\right)-\chi\left(t_1\right)\right]
$$
在半经典路径积分表述（或 WKB 近似）中，量子波函数与经典作用量的关系为 $\psi \sim e^{iS/\hbar}$。 应用作用量的改变量 $\Delta S = q\chi$，变换后的波函数 $\psi'$ 与原波函数 $\psi$ 的关系必然为：
$$
\psi^{\prime}(\mathbf{x}, t)=e^{i \frac{q}{\hbar} \chi(\mathbf{x}, t)} \psi(\mathbf{x}, t)
$$
这揭示了规范变换的物理本质：**它是波函数相位的局部旋转。** 场 $\mathbf{A}$ 正是管理这一相位的“联络”。

而在量子力学中，动量同样是空间平移的生成元，由梯度 $\nabla$ 表示。然而，如果我们对变换后的波函数应用普通梯度算符 $\nabla \psi^{\prime}=\nabla\left(e^{i \frac{q}{\hbar} \chi} \psi\right)=e^{i \frac{q}{\hbar} \chi}\left(\nabla \psi+i \frac{q}{\hbar}(\nabla \chi) \psi\right)$ 会发现结果**不是**协变的。由于 $\nabla \chi$（来自 $\mathbf{A}$ 的规范变换）项的出现，破坏了简单的变换规律。这意味着普通导数 $\nabla$（对应机械动量）在规范变换下不是一个定义良好的物理量。为了修复这一点，我们需要引入 **协变导数 (Covariant Derivative)** $\mathbf{D} = \nabla - i \frac{q}{\hbar} \mathbf{A}$。让我们检查它在 $\mathbf{A}' = \mathbf{A} + \nabla \chi$ 下的变换属性：
$$
\begin{aligned}
\mathbf{D}^{\prime} \psi^{\prime} & =\left(\nabla-i \frac{q}{\hbar} \mathbf{A}^{\prime}\right)\left(e^{i \frac{q}{\hbar} \chi} \psi\right) \\
& =\nabla\left(e^{i \frac{q}{\hbar} \chi} \psi\right)-i \frac{q}{\hbar}(\mathbf{A}+\nabla \chi)\left(e^{i \frac{q}{\hbar} \chi} \psi\right) \\
& =e^{i \frac{q}{\hbar} \chi}\left[\left(\nabla \psi+i \frac{q}{\hbar}(\nabla \chi) \psi\right)-i \frac{q}{\hbar} \mathbf{A} \psi-i \frac{q}{\hbar}(\nabla \chi) \psi\right] \\
& =e^{i \frac{q}{\hbar} \chi}\left(\nabla-i \frac{q}{\hbar} \mathbf{A}\right) \psi \\
& =e^{i \frac{q}{\hbar} \chi} \mathbf{D} \psi
\end{aligned}
$$
多余的 $\nabla \chi$ 项完美抵消！算符 $\mathbf{D}$ 保持了物理对称性。 将此与动量算符进行对比，**物理（机械）动量** 对应于规范不变的算符：$\frac{\hat{\mathbf{p}}_{mech}}{i\hbar} \leftrightarrow \mathbf{D} = \nabla - i\frac{q}{\hbar}\mathbf{A}$。两边乘以 $-i\hbar$：$\hat{\mathbf{p}}_{mech} = -i\hbar\nabla - q\mathbf{A}$。由于经典关系为 $\mathbf{p}_{mech} = \mathbf{p}_{can} - q\mathbf{A}$，我们可以识别出 **正则动量** 算符为：
$$
\hat{\mathbf{p}}_{c a n}=-i \hbar \nabla
$$
正则动量 $\mathbf{p}$ 对应于纯微分算符 $-i\hbar\nabla$（平移生成元）。尽管 $\nabla$ 本身不是规范不变的，但它充当了余切丛中的坐标基底。矢量势 $\mathbf{A}$ 作为 **联络**，修正了相空间的几何结构，使得物理量（如速度）变得有意义。这确立了 $\mathbf{p} = m\mathbf{v} + q\mathbf{A}$ 是连接经典几何与量子相位动力学的必然桥梁。

如果再拓展一下，我们会发现规范变换对应于波函数的相位旋转 $\psi' = e^{i\theta(\mathbf{x})} \psi$，其中 $\theta(\mathbf{x}) = \frac{q}{\hbar}\chi(\mathbf{x})$。 所有可能的相位因子 $e^{i\theta}$ 构成了一个数学群，称为 **$U(1)$ 群**（一维酉群）。所以从**李群视角**，电磁相互作用的本质，就是物理系统具有 **局域 $U(1)$ 规范对称性**。而从**李代数视角**，$U(1)$ 是一个**阿贝尔群 (Abelian Group)**，意味着变换是可以交换顺序的（$e^{i\theta_1} e^{i\theta_2} = e^{i\theta_2} e^{i\theta_1}$）。其李代数结构非常简单，生成元只有一个（即虚数单位 $i$），结构常数为零。这一视角的威力在于推广。如果我们把 $U(1)$ 换成更复杂的、不可交换的矩阵群（如 $SU(2)$ 或 $SU(3)$），我们就进入了**杨-米尔斯理论 (Yang-Mills Theory)** 的领域，那是描述弱相互作用和强相互作用的基础。在那时，矢量势 $\mathbf{A}$ 将变成矩阵（非阿贝尔规范场），规范变换将不再是对易的，物理图像将变得更加丰富，但其几何核心仍然是我们在电磁学中建立的“联络”与“协变导数”。


## 4. Hamiltonian Mechanics

Outline:
- 哈密顿力学的系统理论，包括泊松括号，正则变换，哈密顿雅可比方程。
- 几个和正则变换有关的定理：诺特定理，刘维尔定理，庞加莱回归定理。
### 4.1 Symplectic Structure

回忆广义坐标动量（也称为正则坐标动量）相空间哈密顿正则方程：$\dot{q}^a=\frac{\partial H}{\partial p_a}, \dot{p}_a=-\frac{\partial H}{\partial q^a},a=1,\dots,n$，坐标动量地位非常平等，但是有一个负号，从之前的推导中我们知道这来自于 symplectic potential $\Theta=p_adq^a$，但是显然在辛势中，正则坐标与动量是地位不平等的，为使二者地位平等，取外微分 $\omega=d\Theta=dp_a\wedge dq^a$ 称为 symplectic form 辛形式，这是一个 2-form 是 exact from 是 closed form，方程中的负号来源就是因为 wedge product 交换顺序出负号。Symplectic form 是相空间的一个基本结构，非常重要。有了 symplectic form $\omega$ 的相空间称为 phase space defined with symplectic structure。

我们进而可以更平等地写出变量：$\mathbf{x}=\left(x^1, x^2, \ldots x^{2 n}\right)^T=\left(q^1, \ldots, q^n, p_1, \ldots, p_n\right)^T$ 记为 $x^i$，于是有 $$\begin{aligned}\omega=d p_a \wedge d q^a \equiv \frac{1}{2} \omega_{i j} d x^i \wedge d x^j,\quad J^{-1}=\left(\omega_{i j}\right)=\left(\begin{array}{cc}
0_{n \times n} & -1_{n \times n} \\
1_{n \times n} & 0_{n \times n}
\end{array}\right), \\ J=-J^{-1}=(\omega^{ij})=\left(\begin{array}{cc}
0_{n \times n} & 1_{n \times n} \\
-1_{n \times n} & 0_{n \times n}
\end{array}\right),\quad  \omega_{i j} \omega^{j k}=\delta_i^k, \quad \omega^{i j} \omega_{j k}=\delta_k^i \end{aligned}$$
按照这种写法，哈密顿正则方程为：
$$\dot{x}^i=\omega^{i j} \partial_j H\quad \text{ or }\quad \dot{\mathbf{x}}=J \frac{\partial H}{\partial \mathbf{x}} .$$
我们在这里稍微深入叙述下“辛”，Symplectic 希腊语意为“编织”，描述了 $p$ 与 $q$ 之间一种特殊的纠缠关系：它们必须成对出现，且 $\omega$ 测量的是它们在相空间构成的**有向面积**，而非长度。我们同时需要区分两个层面的概念：“余切丛上的辛几何”（物理学常用的）和“一般辛流形”（数学定义的）。在经典力学中讨论的相空间，几乎总是有 **余切丛 (Cotangent Bundle, $T^*\mathcal{M}$)** 的。**底空间**是构型空间 $\mathcal{M}$（位置 $q^a$），**纤维**则是余切空间（动量 $p_a$）。在这种情况下，矢量（$q$）和对偶矢量（$p$）的区别是预定义好的，这种几何结构被称为 **“典范辛结构” (Canonical Symplectic Structure)**，所谓的辛形式 $p_idq^i$ 其实来源于**重言 1-形式 (Tautological 1-form)**，记为 $\theta$。

重言形式的不依赖于坐标的几何定义为，相空间的一个点 $\alpha$ 本身由两部分组成：$\alpha = (q, p)$。$q$ 为在底流形（位置空间）上的位置。$p$ 则这个位置上的动量（一个 1-form，余切矢量）。现在我们要在这个点 $\alpha$ 定义一个 1-form $\theta_\alpha$。这个 1-form 需要“吃”一个切矢量 $X$。 定义如下：
$$\theta_\alpha(X) = p(d\pi(X))$$
其中 $\pi$ 是投影（把相空间的矢量 $X$ 投影到底空间上去变成 $v$）。在这个点 $(q,p)$ 上， $\theta$ 的作用规则就是：直接使用该点自带的那个 $p$，去作用在投影下来的矢量上。$X$ 有两个变化方向：位置变了多少 ($\delta q$)，动量变了多少 ($\delta p$)：$X = \delta q^i \frac{\partial}{\partial q^i} + \delta p_i \frac{\partial}{\partial p_i}$。$\pi$ 是投影映射：它把相空间点 $(q,p)$ 投射回底空间点 $q$。$d\pi$ 是投影的微分（推前 push forward 映射）：它把相空间矢量 $X$ 投射成底空间矢量。因为投影只看位置，所以它把 $X$ 中的 $\delta p$ 部分直接扔掉了：$d\pi(X) = \delta q^i \frac{\partial}{\partial q^i}$。又因为 $p$ 是一个余切矢量（1-form），它的坐标形式是 $p = p_j dq^j$。所以最终结果为 
$$
\begin{aligned}
\left(p_j d q^j\right)\left(\delta q^i \frac{\partial}{\partial q^i}\right) =p_j \cdot \delta q^i \cdot \underbrace{d q^j\left(\frac{\partial}{\partial q^i}\right)}_{\delta_i^j} =p_i \delta q^i
\end{aligned}
$$
显然 $dq^i(X) = \delta q^i$。 所以：$\theta(X)=p_i d q^i(X)$ 即 $\theta=p_idq^i$。重言形式定义里没有出现任何指标 $i, j, k$。这意味着不管你用什么坐标系（笛卡尔、球坐标、椭圆坐标），这个 $\theta$ 的定义方式是一模一样的。它是相空间**内禀**的几何结构，而不是人为凑出来的公式。在几何上，如果你想在一个流形上定义一个结构，通常需要引入外部客体（比如引入一个度规 $g$，或者引入一个电磁场 $A$）。 但是，在余切丛（相空间）上，**你不需要引入任何外部东西**。因为相空间里的每个点 $(q, p)$，天生就携带了一个 1-form（那就是 $p$ 自己）。所以，$\theta$ 是相空间**土生土长**的、唯一且自然的 1-form。它除了利用点本身的信息外，没用到任何别的东西。在数学上，这叫做 **Canonical（典范的）**，意思就是“它是上帝钦定的，不是人为选择的”。正因为 $\theta = p_i dq^i$ 是“重言”的（即天然存在的），所以由它导出的辛形式：$\omega = -d\theta = dp_i \wedge dq^i$  也是天然存在的。所以相空间天生就是辛流形，只要你有位置 $q$，自然就有动量 $p$，自然就有辛形式 $\omega$，不再需要引入度规来测量距离。

同时，我们也可以再次回顾正则动量和机械动量的差别，因为正则动量才是重言结构的基石，如果使用**机械动量** $\boldsymbol{\pi} = m\mathbf{v}$ 当作基本变量，那么标准的辛形式会变成：
$$
\begin{aligned}
\omega & =d\left(\pi_i+q A_i\right) \wedge d q^i=d \pi_i \wedge d q^i+q d A_i \wedge d q^i = \underbrace{d\pi_i \wedge dq^i}_{\text{标准项}} + \underbrace{\frac{q}{2} F_{ij} dq^i \wedge dq^j}_{\text{磁场项 (曲率)}}
\end{aligned}
$$
代价出现了，如果用正则动量 $\mathbf{p}$：相空间的几何结构是平坦、标准的 $dp \wedge dq$。哈密顿方程形式完美对称。但如果用机械动量 $m\mathbf{v}$：相空间的几何结构扭曲了，辛形式里多出了一个电磁场张量 $F_{ij}$（磁场），这意味着，哈密顿方程里会显式地出现洛伦兹力项（磁场项），破坏了方程的正则对偶性（Canonical Duality）。$\mathbf{p}$ 之所以基本，是因为它吸收了 $q\mathbf{A}$ 的几何影响，把相空间的辛结构“对角化”成了最简单的形式。

从上面的叙述，我们能够感受到，在更广泛的数学定义中，辛流形只是一个偶数维流形，上面有一个闭的、非退化的 2-形式 $\omega$。此时，我们并不一定要把坐标预先分成“位置”和“动量”，是辛形式 $\omega$ 本身定义了谁是谁的对偶。$\omega$ 是一个映射机器，把矢量变成对偶矢量（和度规一样降指标）。这意味着在辛几何中，切空间 $T\mathcal{M}$ 和余切空间 $T^*\mathcal{M}$ 是 **同构 (Isomorphic)** 的。辛形式 $\omega$ 让相空间中任意一个方向，都能找到一个跟它配对的“共轭方向”。

这里引出一个更深刻的几何问题：相空间可以是弯曲的流形（例如球面的余切丛），那么这种弯曲是否会阻碍我们建立标准的哈密顿力学？在黎曼几何中，曲率的存在使得我们无法在局部找到一组坐标让度规变回平直的欧几里得度规（$g_{ij} = \delta_{ij}$）。然而，辛几何展现了截然不同的柔性。**达布定理 (Darboux's Theorem)** 指出：对于任意 $2n$ 维辛流形 $(\mathcal{M}, \omega)$ 上的任意一点，都存在一个局部坐标系 $(q^1, \dots, q^n, p_1, \dots, p_n)$，使得在该邻域内辛形式可以写为标准形式：$\omega = \sum_{a=1}^n d p_a \wedge d q^a$。这在物理上具有重大的意义：
- **相空间的局部平坦性**：辛流形没有局部几何不变量（即没有“辛曲率”）。无论物理系统多么复杂，其相空间在局部永远看起来像标准的 $\mathbb{R}^{2n}$ 空间。
- **正则形式的普适性**：它保证了**正则坐标**总是存在的。我们总是可以通过适当的坐标变换，消除相空间的任何“扭曲”，使得哈密顿正则方程 $\dot{\mathbf{x}} = J \nabla H$ 在局部严格成立。这是哈密顿力学能够成为普适理论的几何基石。

### 4.2 Poisson Bracket

在哈密顿力学中，对物理量的描述是一个相空间的函数，$A(p,q)$ 或 $A(x)$，考察物理量随时间演化：
$$
\frac{d A}{d t}=\frac{\partial A}{\partial q^a} \dot{q}^a+\frac{\partial A}{\partial p_a} \dot{p}_a=\frac{\partial A}{\partial q^a} \frac{\partial H}{\partial p_a}-\frac{\partial A}{\partial p_a} \frac{\partial H}{\partial q^a}\equiv [A,H]=\frac{\partial A}{\partial x^i} \omega^{i j} \frac{\partial H}{\partial x^j}=\left(\partial_i A\right) \omega^{i j}\left(\partial_j H\right).
$$
称为泊松括号。所以物理量守恒则代表 $[A,H]=0$ 称为泊松对易。哈密顿正则方程可以写为：
$$
\dot{q}^a=\left[q^a, H\right], \quad \dot{p}_a=\left[p_a, H\right] \quad \text{ or }\quad\dot{\mathbf{x}}=[\mathbf{x}, H] .
$$
如果推广到含时物理量，那么其烟花则为：$\frac{d A}{d t}=\frac{\partial A}{\partial t}+[A, H]$。

泊松括号的基本性质：
$$\begin{aligned}
\left[q^a, q^b\right] & =\left[p_a, p_b\right]=0, \quad\left[q^a, p_b\right]=\delta_b^a \quad \text{ or }\quad \left[x^i, x^j\right]=\omega^{i j} . \\
[A, B] & =-[B, A] \\
\left[A, c_1 B_1+c_2 B_2\right] & = c_1\left[A, B_1\right]+c_2\left[A, B_2\right] \\
[A,[B, C]]&+[B,[C, A]]+[C,[A, B]]=0 \\
\frac{d}{d t}([A, B])&=\left[\frac{d}{d t} A, B\right]+\left[A, \frac{d}{d t} B\right] .
\end{aligned}$$
> [!example]
> 角动量 $J_1=y p_z-z p_y, \quad J_2=z p_x-x p_z, \quad J_3=x p_y-y p_x$ 的泊松括号$$
\begin{aligned}
{\left[J_1, J_2\right] } & =\left[y p_z-z p_y, z p_x-x p_z\right] \\
& =\left[y p_z, z p_x\right]+\left[z p_y, x p_z\right]-\left[y p_z, x p_z\right]-\left[z p_y, z p_x\right] \\
& =y\left[p_z, z\right] p_x+x\left[z, p_z\right] p_y=x p_y-y p_x=J_3
\end{aligned}
$$一般地，$\left[J_i, J_j\right]=\varepsilon_{i j k} J_k$。同时还有 $\left[\mathbf{J}^2, J_i\right]=0$。

定义泊松括号 $\{f, g\}$ 之后，我们要揭示它背后真正的数学身份：它是相空间物理量构成的**李代数**的运算规则。为了理解这一点，我们需要从头梳理**李群**与**李代数**的关系。

李群 $G$ 是一个群，同时也是一个光滑的**微分流形**。而物理学中的对称性（如旋转、平移）通常是**连续**的，正好适合李群来描述，群的乘法 $g_1 \cdot g_2$ 对应于在流形上的移动：先做 $g_2$ 操作，再做 $g_1$ 操作，结果等效于到了一个新的点。但是困难在于李群（流形）往往是弯曲的、复杂的（比如 $SO(3)$ 的拓扑结构很复杂），直接研究它很难。数学家发现，要了解这个地形图的性质，只需要研究原点（单位元，即不做任何操作）附近的性质就足够了，于是给出了李代数 $\mathfrak{g}$ 的定义是：李群在单位元 $e$ 处的**切空间 (Tangent Space)**，切空间里的矢量 $X$ 被称为生成元。如果“李群上的点”代表一个**有限**的变换（转了 $\theta$ 角），那么“李代数里的矢量”代表一个**无穷小**的变换趋势（转动的速度/方向）。李代数是一个**矢量空间**（线性的，平直的）。你可以在这里自由地做加减法（线性叠加），比在弯曲的群上处理容易得多。

切平面（李代数）上的一个矢量 $X$，如何变回李群上的一个操作？ 答案是：**沿着这个切线方向一直走下去。** 数学上这叫做**指数映射**：$g(\theta) = e^{\theta X}$，其中 $X$ 是生成元（比如“绕Z轴旋转”的指令），$\theta$ 是参数（比如“转多少度”），$e^{\theta X}$ 就是最终生成的有限变换（群元素）。比如平移生成元是 $\nabla$（动量）。有限平移是 $e^{\mathbf{a} \cdot \nabla} f(x) = f(x+\mathbf{a})$（这就是泰勒展开的本质）。旋转生成元是角动量矩阵 $J$。有限旋转是 $R(\theta) = e^{i\theta J}$。

现在，李代数（切平面）是平的，李群（地形）是弯的。我们怎么在平坦的地图上，记录下地球是弯曲的这一事实？答案在于“不对易性” (Non-commutativity)。在弯曲空间做变换，顺序很重要：先绕X轴转再绕Y轴转 $\neq$ 先绕Y轴转再绕X轴转，即 $g_1 g_2 \neq g_2 g_1$。在李代数（无穷小层面）上，这种“顺序的差异”被定义为 **李括号 (Lie Bracket)**，记为 $[X, Y]$。它的定义源自于群的交换子（Commutator）：
$$e^{\epsilon X} e^{\epsilon Y} - e^{\epsilon Y} e^{\epsilon X} \approx \epsilon^2 [X, Y]$$
**李括号 $[X, Y]$ 测量了两个无穷小变换交换顺序后的差异。** 如果 $[X, Y] = 0$，说明这两个变换可以完美交换（群是平坦的/阿贝尔的）；如果不为 0，说明群结构是弯曲的。

现在回到哈密顿力学，我们有物理量 $A, B, C...$（比如角动量 $L_x, L_y, L_z$），我们已经知道的是，诺特定理告诉我们这些物理量对应于某种对称性（生成元）；以及这些物理量的**泊松括号** $\{A, B\}$ 满足雅可比恒等式。我们接下来想要更深入地说明，相空间中的物理量（守恒量），就是某个对称李群的**李代数生成元**；泊松括号 $\{A, B\}$ 正是这个李代数上的李括号 $[A, B]$。这意味着我们不需要画出复杂的李群流形，只需要计算物理量的泊松括号，就能完全掌握系统的对称性结构。

我们首先从上节引入的辛形式开始引出一个哈密顿矢量场的概念。给你任意一个相空间上的函数 $f$（比如能量 $H$、动量 $p$、或者任意一个乱写的函数），在几何上，函数 $f$ 的变化率由它的**外微分** $df$ 描述，它是一个 **1-form (余切矢量)**，其物理意义是在每一点，函数 $f$ 沿哪个方向变化最快（梯度的对偶描述）。辛形式 $\omega$ 是一个**双线性映射**，它吃两个矢量，吐出一个数，我们同样可以视为吃一个矢量，吐出一个1-form (余切矢量)，而辛形式 $\omega$ 的非退化性给出了映射 $\tilde{\omega}: X \to \omega(X, \cdot)$ 是可逆的 (Invertible)，给定任何一个矢量 $X$，你能唯一找到一个对应的 1-form，反之亦然，给定任何一个 1-form $\alpha$，你都能唯一找到一个对应的矢量 $X$，使得 $\omega(X, \cdot) = \alpha$。那么一定**存在且唯一**存在一个矢量场 $X_f$，满足(注：负号是物理上的习惯约定，为了配合哈密顿方程的符号)：
$$\omega(X_f, \cdot) = -df(\cdot)$$
类比一下，在黎曼几何（欧氏空间）中，我们用度规 $g$ 来做这个映射。
$$g(\nabla f, \cdot) = df$$
得到的 $\nabla f$ 是**梯度**。而梯度的方向垂直于等高线，指向 $f$ **增加最快**的方向（爬坡）。在辛几何中，我们用 $\omega$ 来做映射，得到的 $X_f$ 是**辛梯度 (Symplectic Gradient)**。由于 $\omega$ 是**反对称**的 ($\omega(X, Y) = -\omega(Y, X),\omega(X, X)=0$)，这导致 $X_f$ 的方向被**旋转了 90 度**，即**沿着**等高线跑，指向 $f$ **保持不变**的方向，这点可以看 $f$ 沿着 $X_f$ 怎么变：
$$X_f(f) = df(X_f) = -\omega(X_f, X_f)=0$$
也就是哈密顿流 $X_f$ 永远守恒它自己的生成元 $f$。如果 $f=H$（能量），那么哈密顿流 $X_H$（时间演化）就会让系统沿着等能面运动（能量守恒）。这就是为什么行星绕太阳转圈（哈密顿流，沿着等能线），而不是掉进太阳里（梯度流，沿着势能下降方向）。

回顾最上面的哈密顿力学中的泊松括号的定义：$[A,H]=\frac{\partial A}{\partial x^i} \omega^{i j} \frac{\partial H}{\partial x^j}$，如果推广到任意辛形式，我们会发现 $[g, f] \equiv \omega(X_f, X_g)$，也就是说，对任何函数 $f$ 生成的一个**哈密顿矢量场** $X_f$ 对任意测试函数 $g$ 有 $X_f(g) = \{g, f\}$，这个哈密顿矢量场就是我们要找的“李代数生成元” $X_f$。

在微分几何中，两个矢量场 $X$ 和 $Y$ 的 **李括号 (Lie Bracket)** $[X, Y]$ 定义为它们的交换子：
$$[X, Y](g) = X(Y(g)) - Y(X(g))$$
它测量了“先做 $Y$ 变换再做 $X$ 变换”与“反过来做”之间的差异。现在的核心任务是： 计算两个哈密顿矢量场 $X_f$ 和 $X_g$ 的李括号 $[X_f, X_g]$，看看它是否等于“泊松括号 $\{f, g\}$ 生成的矢量场” $X_{\{f, g\}}$。我们把 $[X_f, X_g]$ 作用在一个任意测试函数 $h$ 上：
$$ [X_f, X_g](h) = X_f(X_g(h)) - X_g(X_f(h))= X_f(\{h, g\}) - X_g(\{h, f\}) = \{ \{h, g\}, f \} - \{ \{h, f\}, g \}$$
这里出现了双重泊松括号。为了化简它，我们必须使用**雅可比恒等式 (Jacobi Identity)**：
$$\{ \{h, g\}, f \} + \{ \{g, f\}, h \} + \{ \{f, h\}, g \} = 0$$
稍微移项整理一下：
$$\{ \{h, g\}, f \} - \{ \{h, f\}, g \} = -\{ \{g, f\}, h \} = \{ \{f, g\}, h \}$$
最终得到：
$$[X_f, X_g](h) = \{ \{f, g\}, h \}=X_{\{f, g\}}(h) = \{h, \{f, g\}\} = - \{ \{f, g\}, h \}$$
(注：这里通常差一个负号，取决于哈密顿矢量场定义是 $\{g,f\}$ 还是 $\{f,g\}$，这在数学上称为“李代数反同态”，但在物理结构上视为等价)_。

于是我们得到了结论：
$$[X_f, X_g] \longleftrightarrow X_{\{f, g\}}$$
相空间中的物理量（守恒量），就是某个对称李群的李代数生成元，因为每一个物理量 $A$，都通过映射 $A \to X_A$ 变成了一个几何上的矢量场（生成元）。而泊松括号就是李括号，因为上面的推导证明了：“物理量的代数运算（泊松括号）”直接反映了“几何变换的不对易性（李括号）。泊松括号并不是凭空定义的一套规则，它是**李群及其李代数结构在相空间函数上的“投影”**，这是一种李代数同态，如果 $\{J_x, J_y\} = J_z$（角动量代数），那么必然有 $[X_{J_x}, X_{J_y}] \approx -X_{J_z}$（几何旋转的不对易性）。 这意味着我们不需要去画复杂的相流图，只需要在代数层面上计算泊松括号，就能完全掌握系统对称变换的群结构。这就是为什么在量子力学中，我们只关注算符的对易关系，因为那已经包含了所有几何变换的信息。

如果没有李群的几何结构做支撑，泊松括号的雅可比恒等式就成了无源之水；反之，正是因为泊松括号满足雅可比恒等式，它才有资格成为量子力学中对易子 $[\hat{A}, \hat{B}]$ 的经典父亲。泊松括号在量子力学中对应算符的对易子 $[\widehat{A}, \widehat{B}]=\widehat{A} \widehat{B}-\widehat{B} \widehat{A}$，算符对易子满足泊松括号的所有性质。它说明，经典物理和量子物理是有联系的，经典物理可以看成量子物理在普朗克常数 $\hbar → 0$ 时的极限。的确，可以证明，在 $\hbar → 0$ 时算符对易子自动就会给出经典物理的泊松括号。

### 4.3 Canonical Transformation

正则变换是哈密顿力学中的核心概念，它保相空间中的辛结构。有两个视角：
- 可以看成是一个相空间中的坐标变换。
- 可以看成是一个从相空间到自身的一一映射，这个映射将相空间中的一个点映射到另一个点。
数学上二者是等价的，详情可以参考梁灿彬老师的微分几何与广义相对论教材。而其中的一种重要的无穷小变换会与之前讲过的 Noether Theorem 有深刻关联。

#### 4.3.1 As Coordinate Transformation in Phase Space

我们希望坐标变换 $\vec{x}=(q, p) \rightarrow \vec{x}^{\prime}=\left(q^{\prime}, p^{\prime}\right)$ 这个变换保 symplectic structure。具体地，symplectic form $\omega$ 作为一个 differential form 是独立于坐标的。所以在任意新的坐标系 $x'$，我们有 $\omega=\frac{1}{2} \omega_{i j} d x^i \wedge d x^j=\frac{1}{2} \omega_{m n}^{\prime} d x^{\prime m} \wedge d x^{\prime n}$，利用 $\omega_{i j} d x^i \wedge d x^j=\omega_{i j} \frac{\partial x^i}{\partial x^{\prime m}} \frac{\partial x^j}{\partial x^{\prime n}} d x^{\prime m} \wedge d x^{\prime n}$ 有新的坐标分量为：$\omega_{m n}^{\prime}=\omega_{i j} \frac{\partial x^i}{\partial x^{\prime m}} \frac{\partial x^j}{\partial x^{\prime n}}$。但是为了正则坐标和动量的正则方程仍然成立，$J^{-1}$ 是固定不能变的，所以必须有：
$$
\omega_{m n}^{\prime}=\omega_{m n}=\omega_{i j} \frac{\partial x^i}{\partial x^{\prime m}} \frac{\partial x^j}{\partial x^{\prime n}}
$$
这就是保持相空间的辛结构。如果记 $D^i{ }_m=\frac{\partial x^i}{\partial x^{\prime m}}$，则有：$D^T J^{-1} D=J^{-1},\left(D^{-1}\right) J\left(D^{-1}\right)^T=J$，再展开则有：
$$
\frac{\partial x^{\prime m}}{\partial x^i} \omega^{i j} \frac{\partial x^{\prime n}}{\partial x^j}=\omega^{m n} \Leftrightarrow \partial_i x^{\prime m} \omega^{i j} \partial_j x^{\prime n}=\omega^{m n}=\left[x^{\prime m}, x^{\prime n}\right]_{\mathbf{x}}=\left[x^{\prime m}, x^{\prime n}\right]_{\mathbf{x}'}
$$
于是我们得到，相空间坐标变换保持辛结构的要求其实就等价于保持基本泊松括号不变，那么计算任何两个物理量的泊松括号时，是用新坐标来计算还是用老坐标来计算就是一样的了 $[A, B]_{\mathbf{x}}=[A, B]_{\mathbf{x}^{\prime}}$，也就是说物理量的泊松括号在正则变换下是不变的，于是哈密顿正则方程的数学结构在正则变换下将保持不变：
$$
\dot{\mathbf{x}}^{\prime}=\left[\mathbf{x}^{\prime}, H\right]_{\mathbf{x}}=\left[\mathbf{x}^{\prime}, H\right]_{\mathbf{x}^{\prime}}=J \frac{\partial H}{\partial \mathbf{x}^{\prime}}
$$
注意，虽然哈密顿正则方程的数学结构在正则变换下将保持不变，但是哈密顿量在正则变换前后是两个函数，严格来讲是 $H'(x')=H(x)$，只不过在新老坐标下描述的是同一物理量，一般就只写 $H$ 了，但是哈密顿量的函数形式变了，动力学方程也变了，因此，正则变换一般来说并不是一种对称性。

#### 4.3.2 As Diffeomorphism of Phase Space

这种观点下，实际上相当于直接映射 $\omega$ 到自身来保辛结构，将会的到一样的结果：
$$
\omega \rightarrow \omega^{\prime}=\frac{1}{2} \omega_{i j} d x^i \wedge d x^{\prime j}=\omega\quad \Longrightarrow\quad \omega_{m n}=\omega_{i j} \frac{\partial x^i}{\partial x^{\prime m}} \frac{\partial x^j}{\partial x^{\prime n}} . 
$$
或者等价地写为保持辛势：$d p_a^{\prime} \wedge d q^{\prime a}=d p_a \wedge d q^a \Leftrightarrow d \Theta^{\prime}=d \Theta$，于是变换前后辛势之差为一个 closed form $d\left(\Theta-\Theta^{\prime}\right)=0$。闭形式不一定是恰当形式，但是如果只关心空间的局部区域，而不关心空间整体，有庞加莱引理：闭形式局部上也必定是恰当形式。甚至在理论力学的应用中，这一庞加莱引理成立的相空间局部常常能延展为整个相空间，于是有：
$$
\Theta-\Theta^{\prime}=d F \Leftrightarrow p_a d q^a-p_a^{\prime} d q^{\prime a}=d F .
$$
于是满足上式的相空间的微分同胚映射必定是正则变换，并且反过来常常也对。有了之前对于辛几何与李群的介绍，我们现在可以补充从辛几何的观点来看，正则变换 $\Phi: \mathcal{M} \to \mathcal{M}$ 本质上是保持辛形式 $\omega$ 不变的微分同胚映射，即 $\Phi^* \omega = \omega$。在现代几何力学中，这种映射被称为 **辛同胚 (Symplectomorphism)**。 所有辛同胚的集合构成了一个群，称为 **辛群 (Symplectic Group, $Symp(\mathcal{M}, \omega)$)**。这是一个无穷维的李群。相比于有限维的旋转群 $SO(3)$，辛群包含的对称性要丰富得多。物理系统的演化历史，本质上就是相空间中一条落在辛群里的轨迹。

#### 4.3.3 Infinitestimal Transformation

如果某个正则变换将一个相空间点映射到一个非常接近的另一个点，距离小到无穷小，我们就成为 infinitestimal canonical transformation：
$$
q^a \rightarrow q^{\prime a}=q^a+\delta q^a=q^a+\varepsilon Q^a(q, p), \quad p_a \rightarrow p_a^{\prime}=p_a+\delta p_a=p_a+\varepsilon P_a(q, p) .
$$
当 $\varepsilon$ 无穷小时，变换点前后距离一定是无穷小的，那如何使之正则呢？即保辛结构 $d p_a^{\prime} \wedge d q^{\prime a}-d p_a \wedge d q^a=0$，代入展开到一阶无穷小有 $\left(d P_a \wedge d q^a+d p_a \wedge d Q^a\right) \varepsilon=0$，于是，
$$
\begin{aligned}
0 & =d P_b \wedge d q^b+d p_a \wedge d Q^a \\
& =\frac{\partial P_b}{\partial q^a} d q^a \wedge d q^b+\frac{\partial P_b}{\partial p_a} d p_a \wedge d q^b+\frac{\partial Q^a}{\partial q^b} d p_a \wedge d q^b+\frac{\partial Q^a}{\partial p_b} d p_a \wedge d p_b \\
& =\frac{1}{2}\left(\frac{\partial P_b}{\partial q^a}-\frac{\partial P_a}{\partial q^b}\right) d q^a \wedge d q^b+\frac{1}{2}\left(\frac{\partial Q^a}{\partial p_b}-\frac{\partial Q^b}{\partial p_a}\right) d p_a \wedge d p_b \\
& +\left(\frac{\partial P_b}{\partial p_a}+\frac{\partial Q^a}{\partial q^b}\right) d p_a \wedge d q^b .
\end{aligned}
$$
从而，
$$
\begin{aligned}
\frac{\partial P_b}{\partial q^a}-\frac{\partial P_a}{\partial q^b}=0,\quad
\frac{\partial Q^a}{\partial p_b}-\frac{\partial Q^b}{\partial p_a}=0,\quad \frac{\partial P_b}{\partial p_a}+\frac{\partial Q^a}{\partial q^b}=0 .
\end{aligned}
$$
容易知道
$$
\delta q^a=\varepsilon Q^a=\varepsilon \frac{\partial G}{\partial p_a}, \quad \delta p_a=-\varepsilon  P_a=-\frac{\partial G}{\partial q^a}
$$
是一个通解，其中 $G$ 为某个任意的相空间函数。也就是说如果变换具有这种形式，那个就是一个无穷小正则变换，称之为由物理量 $G(q, p)$ 生成的无穷小正则变换。其函数形式的无穷小改变为：
$$
\delta A=A\left(q^{\prime}, p^{\prime}\right)-A^{\prime}\left(q^{\prime}, p^{\prime}\right)=A\left(q^{\prime}, p^{\prime}\right)-A(q, p)=\frac{\partial A}{\partial q^a} \delta q^a+\frac{\partial A}{\partial p_a} \delta p_a=\varepsilon[A,G]
$$

> [!example]
> 取 $G=p_c$ 那么 $Q^a=\delta_c^a, P_a=0$，从而 $q^a \rightarrow q^a+\varepsilon \delta_c^a, \quad p_a \rightarrow p_a$，即正则动量 $p_c$ 可以生成正则坐标 $q^c$ 的无穷小平移。

现在推广一下变换的形式，考察一个正则变换的单参簇 $q^a \rightarrow q^{\prime a}(q, p, \lambda), p_a \rightarrow p_a^{\prime}(q, p, \lambda)$，$\lambda=0$ 时无变化。随着参数 $λ$ 的连续变动，这簇正则变换会在相空间中画出一条以 $λ$ 为参数的路径，路径上任何 两个相差无穷小量 $dλ$ 的点都是用无穷小正则变换连接起来的。因此容易得到：
$$
\frac{d q^{\prime a}}{d \lambda}=\frac{\partial G}{\partial p_a^{\prime}}, \quad \frac{d p_a^{\prime}}{d \lambda}=-\frac{\partial G}{\partial q^{\prime a}},
$$
其中 $G(q',p',\lambda)$ 称为这个正则变换单参簇的生成元，习惯上省略 $'$，$\left(\frac{d q^a}{d \lambda}, \frac{d p_a}{d \lambda}\right)$ 就可以视为一个相流，表达在相空间中由 $G$ 诱导的流动。更紧凑地，
$$
v_G^i=\frac{d x^i}{d \lambda}=\omega^{i j} \partial_j G,\quad \mathbf{x}=(q,p)
$$
特别的，取 $\lambda=t,G=H$ 那么相流方程就变成哈密顿正则方程了，因此哈密顿量为时间演化的生成元，由于哈密顿量描述的就是系统能量，因此这就给出了物理系统能量的一般定义，即，时间演化的生成元描述系统的能量。同时系统在相空间的时间演化过程实际上是一个持续进行的正则变换，是以时间为参数的正则变换单参簇。因此，时间演化过程保持相空间的辛结构。

进一步，假设我们有两个正则变换的单参簇，分别由 $G_1$ 和 $G_2$ 生成，相应的参数分别记为 $λ_1,λ_2$, 则利用相流方程以及 $ω_{ij}ω^{jm} = δ^m_n$, 可以算得辛形式在速度场 $v_{G_1}^i,v_{G_2}^j$ 上的值就是两个生成元的泊松括号：
$$
\omega(v_{G_1},v_{G_2})\equiv\omega_{i j} v_{G_1}^i v_{G_2}^j=\omega_{i j} \frac{d x^i}{d \lambda_1} \frac{d x^j}{d \lambda_2}=\left(\partial_m G_2\right) \omega^{m n}\left(\partial_n G_1\right)=\left[G_2, G_1\right]
$$
从几何上看，无穷小正则变换正是由 **哈密顿矢量场 $X_G$** 生成的流。回忆我们在 4.2 节引入的几何定义 $\omega(X_G, \cdot) = -dG$。无穷小变换 $\mathbf{x} \to \mathbf{x} + \epsilon X_G$ 实际上就是李导数 $\mathcal{L}_{X_G}$ 的作用。而这一变换之所以是“正则”的（即保辛结构），是因为 Cartan 同伦公式保证了：
$$\mathcal{L}_{X_G} \omega = d(\iota_{X_G} \omega) + \iota_{X_G} (d\omega) = d(-dG) + 0 = 0$$
这简洁地证明了：**任何由哈密顿矢量场生成的流，天然就是辛同胚（正则变换）。**

#### 4.3.4 Noether Theorem

原则上正则变换可以是任何保持辛结构的数学变换。不过，对一个物理系统进行的物理操作（比如将系统旋转一个角度）常常在相空间诱导出一个正则变换。这是因为，对系统的物理操作会将一个物理状态变到另一个物理状态，从而在相空间诱导出一个微分同胚映射，而且由于物理操作之后系统依然是一个哈密顿正则系统，满足同样的哈密顿正则方程，所以这一诱导出来的微分同胚映射必定是一个正则变换。特别的，如果物理操作本身依赖于一个连续参数（比如旋转操作中的旋转角度），那它就会在相空间诱导出一个正则变换的单参簇，这时候我们就称这个单参簇的生成元为相应物理操作的生成元。正则动量就是对相应正则坐标的平移操作的生成元，角动量是旋转操作的生成元。

以上所谈是任意的连续物理操作。但是，如果这一连续操作本身是一个对称操作，即在操作前后系统的运动微分方程保持形式不变。那就会有更进一步的结论，也就是诺特定理，它说，这时候这一对称操作的生成元必定是守恒量。证明非常简单，对称操作由于要保持运动微分方程（由哈密顿正则方程给出）的形式不变，因此必定要保持哈密顿量的函数表达式 $H(q, p)$ 不变 $\delta H=0$，设对称操作的生成元为 $G$，从而即有
$$
0=\delta H=\varepsilon[H, G] \Leftrightarrow 0=[H, G]=\frac{dG}{dt}.
$$
Noether 定理的逆命题在局部也是成立的：**任何一个守恒量 $G$（即 $\{G, H\}=0$），都对应着系统的一个连续对称性。** 这意味着，只要你能找到一个积分常数，你就一定能找到一个让哈密顿量保持不变的几何变换。这使得哈密顿力学成为寻找和分析对称性的最强有力的框架。
### 4.4 Liouville's Theorem and Poincare Recurrence Theorem

我们已经知道了物理系统在相空间的时序演化可以被视为一个相流，且相流速度由哈密顿正则方程给出 $\dot{\mathbf{x}}=[\mathbf{x}, H]$。刘维尔定理则是说这个流体是不可压缩的。具体地，在 $t=0$ 时取相空间中一个区域 $D_0$ 演化到 $D_t$，体积不变 $\text{Vol}(D_t)=\text{Vol}(D_0)$。

为证明，引入 volume element 的概念 $\Omega=d p_1 d q^1 d p_2 d q^2$ 或 $\Omega=d p_1 \wedge d q^1 \wedge d p_2 \wedge d q^2$，易知：
$$\begin{aligned} \Omega =\frac{1}{2}\left(d p_1 \wedge d q^1+d p_2 \wedge d q^2\right) \wedge\left(d p_1 \wedge d q^1+d p_2 \wedge d q^2\right)= \frac{1}{2!} \omega\wedge\omega=\frac{1}{2!} \omega^{\wedge 2}\end{aligned}$$
容易推广得到 $\Omega=d p_1 d q^1 d p_2 d q^2 \ldots . d p_n d q^n=\frac{1}{n!} \omega^{\wedge n}$，这意味着 volume element 仅仅依赖于 symplectic form $\omega$。又因为正则变换的微分同胚是保辛形式的，那么 volume 在时间演化中也是不变的。同样的论证也可以用于相空间的任何 $2k(k ≤ n)$ 维曲面 $S_{2k}$, 其“面积元”定义为 $\frac{1}{k!} ω^{∧k}$。我们同样有：随时间演化的 $S_{2k}$，其“面积”将保持不变。特别的，在相空间任取一条闭合回路 $C$，让 $C$ 随着时间演化，考察辛势 $Θ$ 沿着这条闭合回路的积分 $I_C=\frac{1}{2 \pi} \oint_C \Theta$，由于 $\oint_C \Theta=\int_{S_2} d \Theta=\int_{S_2} \omega$，式中 $S_2$ 为回路 $C$ 所包围的区域。从上面的推导易知，$I_C$ 将在时间演化下保持不变。很显然，以上的所有结果不仅对时间演化生成的相流成立，而且对任何正则变换单参簇的相流都成立。

刘维尔定理告诉我们相流保持体积不变，这让人联想到不可压缩流体。然而，辛几何比流体力学拥有更强的“刚性”。直到 1985 年，Gromov 发现了一个惊人的定理，彻底区分了辛同胚和普通的保体积微分同胚。**格罗莫夫非被挤压定理 (Gromov's Non-Squeezing Theorem)**，又称**辛骆驼定理 (Symplectic Camel)**：考虑相空间中的一个球体 $B(R)$（半径为 $R$），和一个圆柱体 $Z(r) = B^2(r) \times \mathbb{R}^{2n-2}$（底面半径为 $r$）。定理指出：我们无法通过任何正则变换（辛同胚）$\Phi$，将球体 $B(R)$ 嵌入到圆柱体 $Z(r)$ 中，除非 $r \ge R$。
$$\text{If } \Phi(B(R)) \subset Z(r), \text{ then } r \ge R.$$
即使圆柱体的体积是无限大的（因为它在其他方向上无限延伸），只要它的“腰围”（共轭变量平面的面积）太小，球体就塞不进去。其**物理意义在于经典的量子测不准原理** 圆柱体的截面 $B^2(r)$ 对应于一对共轭变量 $(q_1, p_1)$ 的相面积 $\pi r^2$。这个定理告诉我们：**你不能在保持辛结构的前提下，无限压缩共轭变量对的不确定度面积。** 这在经典力学中预示了量子力学的必然出现：相空间不仅仅是体积守恒的，它在共轭平面上有一个最小的“硬核”尺寸限制。辛几何的这种拓扑刚性，正是量子测不准原理 $\Delta x \Delta p \ge \hbar$ 的经典几何投影。

刘维尔定理会引出一个结论：只要等的足够久，会有庞加莱回归，这似乎违背热力学第二定律，然而第二定律需要取热力学极限即 $N\to\infty$，而庞加莱回归的时间为 $t\propto t_c^N$ 其中 $t_c>1$ 是某个特征量，所以我们是看不到庞加莱回归的。庞加莱回归定理：对于一个相空间有限的哈密顿正则系统，任意取定一个相空间初始点 $x_0$，则对于它的任意邻域 $D_0$, 必定存在一个点 $x_0' ∈ D_0$, 它将在有限时间内回归 $D_0$。简单地说就是，只要等待的时间足够长，那么系统总可以回归到和初态任意接近的状态。证明：取有限时间步 $\tau$，直到时间趋于无穷，有 $\text{Vol}(D_k)=\text{Vol}(D_0),\forall k$，那么因为相空间有限，就一定会存在 $k'>k,D_k\cap D_{k'}\neq0$。于是因为微分同胚的可逆性，有 $D_0\cap D_{k'-k}\neq0$ 回归就出现了。

现在我们考虑很多系统。想象我们在相空间里撒了一把“沙子”（或者滴了一滴墨水），每一粒沙子代表一个**系统复本 (Replica)**，它们处于不同的初始状态 $(q, p)$（这被称为**系综 Ensemble**），大量沙子的分布密度记为 $\rho(q, p, t)$，随着时间 $t$ 演化，每粒沙子都遵循哈密顿正则方程运动，这就形成了一股**相流 (Phase Flow)**。因为系统（沙子）既不会凭空消失，也不会凭空产生，所以概率密度必须满足**连续性方程 (Continuity Equation)**（就像流体力学里的质量守恒）：
$$\frac{\partial \rho}{\partial t} + \nabla \cdot (\rho \mathbf{v}) = 0$$
这里 $\mathbf{v} = (\dot{q}, \dot{p})$ 是相空间中的速度矢量，$\nabla = (\frac{\partial}{\partial q}, \frac{\partial}{\partial p})$ 是相空间梯度。我们将 $\nabla \cdot (\rho \mathbf{v})$ 展开：
$$\nabla \cdot (\rho \mathbf{v}) = (\mathbf{v} \cdot \nabla) \rho + \rho (\nabla \cdot \mathbf{v})$$
这里 **$\nabla \cdot \mathbf{v}$** 是相流的散度（速度场的源/汇）。让我们计算它：
$$\nabla \cdot \mathbf{v} = \frac{\partial \dot{q}}{\partial q} + \frac{\partial \dot{p}}{\partial p}$$
代入哈密顿方程 $\dot{q} = \frac{\partial H}{\partial p}, \dot{p} = -\frac{\partial H}{\partial q}$：
$$\nabla \cdot \mathbf{v} = \frac{\partial}{\partial q}\left(\frac{\partial H}{\partial p}\right) + \frac{\partial}{\partial p}\left(-\frac{\partial H}{\partial q}\right) = \frac{\partial^2 H}{\partial q \partial p} - \frac{\partial^2 H}{\partial p \partial q} = 0$$
结论：相流的散度为零（$\nabla \cdot \mathbf{v} = 0$）。这意味着相空间的“流体”是**不可压缩**的。把 $\nabla \cdot \mathbf{v} = 0$ 代回连续性方程便得到：
$$
\frac{d\rho}{d t}=\frac{\partial \rho}{\partial t}+(\mathbf{v} \cdot \nabla) \rho=0
$$
这实际上就是**刘维尔定理的微分形式**。其物理意义非常深刻：
- **$\frac{\partial \rho}{\partial t}$ (欧拉视角)**：你站在相空间某个固定位置不动，看流过去的流体密度变化。
- **$\frac{d \rho}{dt}$ (拉格朗日视角)**：你骑在一粒沙子（随流运动）上，看你周围的密度变化。结论就是，如果你跟着相流走，你周围的概率密度**永远不变**。这就像一块不可压缩的云，它在风中飘动变形，但云的浓密程度（密度）始终保持原样，不会被压实或稀释。

接下来我们可以关联到统计力学了。什么是“统计平衡态”？平衡态意味着宏观性质不随时间变化。在统计上，这意味着概率分布函数在**固定位置**不随时间变化：
$$\text{Equilibrium} \quad \Longleftrightarrow \quad \frac{\partial \rho}{\partial t} = 0$$
结合刘维尔方程，有方程 $\frac{\partial \rho}{\partial t} + (\mathbf{v} \cdot \nabla) \rho = 0$。既然 $\frac{\partial \rho}{\partial t} = 0$，那么必须满足：
$$(\mathbf{v} \cdot \nabla) \rho = 0$$

再引入泊松括号，展开 $(\mathbf{v} \cdot \nabla) \rho$：
$$
(\mathbf{v} \cdot \nabla) \rho=\dot{q} \frac{\partial \rho}{\partial q}+\dot{p} \frac{\partial \rho}{\partial p}=\frac{\partial H}{\partial p} \frac{\partial \rho}{\partial q}-\frac{\partial H}{\partial q} \frac{\partial \rho}{\partial p}
$$
于是我们发现，平衡态条件等价于：
$$
\{\rho, H\}=0
$$
方程 $\{\rho, H\} = 0$ 告诉我们：**分布函数 $\rho$ 必须与哈密顿量 $H$ 泊松对易。** 在数学上，如果一个函数 $\rho(q, p)$ 要使得它和 $H(q, p)$ 的泊松括号处处为零，最自然、最通用的解是：**$\rho$ 仅仅通过 $H$ 来依赖于 $(q, p)$**。 即：
$$\rho(q, p) = f(H(q, p))$$
其中 $f$ 是任意函数。现在我们知道 $\rho$ 必须是能量 $H$ 的函数了。

对于一个**孤立系统**（能量守恒，且没有与其他热库交换）：系统能量被严格限制在 $H(q, p) = E$ 这个能面上。在能面之外（$H \neq E$），概率密度必须为 0。在能面之上（$H = E$），$\rho$ 是常数（因为 $H$ 是常数，$f(H)$ 自然也是常数）。这就直接导致了**微正则分布 (Microcanonical Distribution)**：
$$\rho(q, p) \propto \delta(H(q, p) - E)$$
- **$\delta$ 函数**：保证了只有 $H=E$ 的地方有值。
- **$\propto$ 常数**：说明在能面上，所有点的概率密度**相等**。

**这就是“等概率原理”的由来。** 它不是物理学家拍脑袋瞎猜的，而是：
1. **Liouville 定理** 保证了密度不会随流变化（不会这就没法谈稳态）。
2. **平衡态假设** 保证了密度不显含时间。
3. **泊松对易关系** 锁死了密度只能依赖于守恒量（主要是能量）。
4. **能量守恒** 将分布限制在能面上。

四者结合，唯一的逻辑结果就是：在能量面上均匀分布。但是要注意等概率原理（Fundamental Assumption）至今仍然是一个“假设”（Postulate），并不能完全单纯地从哈密顿动力学（Liouville定理）中“推导”出来。刚才的推导展示的是它的“动力学相容性”（即：如果你假设它是均匀的，这与动力学不矛盾），但我们确实跳过了一个巨大的逻辑鸿沟。这个鸿沟就是：**各态历经性 (Ergodicity)**。我们将在近可积系统和混沌章节中讲述。

### 4.5 Generating Function and Hamiltonian Canonical Equation

现在我们考虑如何建立正则变换。我们已经知道了一个变换是正则的的充分（通常也是必要的）条件：$p_adq^a-p_a'dq'^a=dF$ 其中 $F$ 是相空间的一个函数。

假设我们取 $F$ 为某种形式 $F_1(q,q')$ 那么有
$$p_a d q^a-p_a^{\prime} d q^{\prime a}=d F_1\quad \Rightarrow \quad p_a d q^a-p_a^{\prime} d q^{\prime a}=\frac{\partial F_1}{\partial q^a} d q^a+\frac{\partial F_1}{\partial q^{\prime a}} d q^{\prime a} .$$
那么只需要取：
$$
p_a=\frac{\partial F_1}{\partial q^a}\left(q, q^{\prime}\right) \quad-p_a^{\prime}=\frac{\partial F_1}{\partial q^{\prime a}}\left(q, q^{\prime}\right)
$$
于是只要取不同的 $F_1(q,q')$ 就可以生成不同的正则变换，函数 $F_1(q,q')$ 因此称为正则变换的第一类生成函数。如果把最早的条件改写为 $p_a d q^a+q^{\prime a} d p_a^{\prime}=d\left(F+p_a^{\prime} q^{\prime a}\right)=d F_2$，那么只需要取：
$$
p_a=\frac{\partial F_2}{\partial q^a}\left(q, p^{\prime}\right) \quad q^{\prime a}=\frac{\partial F_2}{\partial p_a^{\prime}}\left(q, p^{\prime}\right) .
$$
易知第三、第四类生成函数：
$$
\begin{array}{lll}
F_3\left(p, q^{\prime}\right): \text { 取 } & q^a=-\frac{\partial F_3}{\partial p_a}\left(p, q^{\prime}\right), & p_a^{\prime}=-\frac{\partial F_3}{\partial q^{\prime a}}\left(p, q^{\prime}\right) \\
F_4\left(p, p^{\prime}\right): \text { 取 } & q^a=-\frac{\partial F_4}{\partial p_a}\left(p, p^{\prime}\right), & q^{\prime a}=\frac{\partial F_4}{\partial p_a^{\prime}}\left(p, p^{\prime}\right) .
\end{array}
$$
注意这 4 类并没有穷尽所有正则变换，比如对于 2x2=4 维的正则变换 $q^{\prime 1}=q^1, q^{\prime 2}=p_2, p_1^{\prime}=p_1, p_2^{\prime}=-q^2$ 实际上是由一种混合型（第一类和第二类混合）生成函数生成，具体的生成函数为 $q^1p_1'+q^2q'^2$。

最后，当正则变换的函数关系显含时间 $\mathbf{x}^{\prime}(\mathbf{x}, t)$，则需要引入一个 $K$ 使得 $p_a d q^a-H d t=p_a^{\prime} d q^{\prime a}-K d t+d F$ 成立，即刚好抵消关于 $t$ 的偏微分。如果将式中的 $F$ 取成第一类生成函数 $F_1(q,q',t)$，那 $K$ 即是 $K=H+\frac{\partial F_1}{\partial t}$，和原来类似地可以证明 $K$ 就是变换后的哈密顿量：$\dot{q}^{\prime a}=\frac{\partial K}{\partial p_a^{\prime}}, \quad \dot{p}_a^{\prime}=-\frac{\partial K}{\partial q^{\prime a}}$。

### 4.6 Hamiltonian-Jacobian Equation and Integrable System

给定坐标在相空间的起点 $q_0$ 和终点 $q$，并不指定起终点的 $p$，给定连接两点的一条相空间路径 $\left(q\left(t^{\prime}\right), p\left(t^{\prime}\right)\right)$，我们可以计算 action：
$$
S\left[q\left(t^{\prime}\right), p\left(t^{\prime}\right)\right]=\int_0^t\left[p_a\left(t^{\prime}\right) d q^a\left(t^{\prime}\right)-H\left(q\left(t^{\prime}\right), p\left(t^{\prime}\right)\right) d t^{\prime}\right] .
$$
进一步，假设路径是满足哈密顿正则方程的，即作用量取极值的，有了这个条件，这个作用量就只依赖于 $q_0,q,t$ 了：
$$S\left(q_0, q, t\right)=\operatorname{extrem}_{\left[q\left(t^{\prime}\right), p\left(t^{\prime}\right)\right]} S\left[q\left(t^{\prime}\right), p\left(t^{\prime}\right)\right]$$
我们要研究这个函数，假设末端有无穷小变动 $\delta q$：
$$
\begin{aligned}
& \delta S\left(q_0, q, t\right)=\operatorname{extrem} \delta S\left[q\left(t^{\prime}\right), p\left(t^{\prime}\right)\right] \\
= & \int_0^t d\left(p_a \delta q^a\right)+\operatorname{extrem} \int_0^t d t^{\prime}\left[\left(\dot{q}^a-\frac{\partial H}{\partial p_a}\right) \delta p_a-\left(\dot{p}_a+\frac{\partial H}{\partial q^a}\right) \delta q^a\right] . \\
= & p_a(t) \delta q^a(t)=p_a(t) \delta q^a  \quad\Longrightarrow \quad p_a(t)=\frac{\partial S}{\partial q^a}\left(q_0, q, t\right)
\end{aligned}
$$
又因为：
$$S=\int pdq-Hdt,dS=pdq-Hdt\quad\Longrightarrow\quad \frac{\partial S}{\partial t}\left(q_0, q, t\right)=-H(q, p) .$$
所以可以得到哈密顿-雅可比方程：
$$
\frac{\partial S}{\partial t}+H\left(q, \frac{\partial S}{\partial q}, t\right)=0 .
$$
下面反过来，假设我们从哈密顿-雅可比方程出发，我们想求解这个偏微分方程。那上面的推理过程就告诉我们，如何通过考虑一条起于 $q_0$，$t$ 时刻到达 $q$ 的极值路径，并计算这条路径的作用量泛函，来构造出哈密顿-雅可比方程方程的解。在这种构造方式中，起始点 $q_0$ 可以看成是积分常数。这一构造过程也告诉我们，如果极值路径（也称作物理路径，或经典路径）可以解析求解（允许用积分来表达），那就能得到哈密顿-雅可比方程的形如 $S(q_0,q,t)$ 的解析解。

但是，$S(q_0,q,t)$ 只是哈密顿-雅可比方程的一类解。而且实际上，我们通常无法求出其解析形式。进一步，对一个 $n$ 自由度的系统，如果能找到哈密顿-雅可比方程的一类形如 $S(α,q,t)$ 的解析解（允许用积分来表达），其中 $α$ 代表 $α^a (a = 1,2,...,n)$，为积分常数（类比于前面的 $q_0$），那这样的系统就称作可积系统 Integrable System，可积系统之所以称作可积系统，是因为可以进一步得出粒子运动路径的解析解（用积分和隐函数表达出来），下面我们来证明这个结论。

假设找到了哈密顿-雅可比方程的一类含 $n$ 个积分常数的解析解，记为 $S(α,q,t)$ 或 $S\left(\alpha^1, \ldots, \alpha^n, q^1, \ldots, q^n, t\right)$，我们可以将 $α^a ,a = 1,2,..,n$ 看作是正则变换以后新的 $q$ 坐标，进而考虑 $(q, p)$ 到 $(α,β)$ 的正则变换，将哈密顿-雅可比方程的解 $S(α,q,t)$ 取作正则变换的第一类生成函数。很明显，这是一种显含时间的正则变换，变换以后的哈密顿量 $K$ 为 $K=H+\frac{\partial S}{\partial t}$，根据哈密顿雅可比方程，我们有 $K=0$，进而由变换以后的哈密顿正则方程，可以知道 $\dot{\alpha}^a=0, \dot{\beta}_a=0$，于是变换后的正则坐标都为守恒量，所以彼此泊松对易。反过来，如果一个哈密顿力学系统有 $n$ 个泊松对易的独立守恒量，那我们就能用这些守恒量构造出哈密顿-雅可比方程的一类形如 $S(α,q,t)$ 的解析解。所以，存在 $n$ 个泊松对易的独立守恒量是一个哈密顿力学系统成为一个可积系统的充要条件。而虽然正则动量 $β_a$ 也是守恒量，不过，由于正则动量和正则坐标的泊松括号不是零，所以它们与 $α^a$ 并不泊松对易，实际上，对它们的更好解释是，将之看成初始条件。因为 $S(α,q,t)$ 取作正则变换的第一类生成函数，于是有 $\beta_a=-\frac{\partial S}{\partial \alpha^a}$，解这组式子就能得到位形空间的运动路径 $q^a (t)$（作为 $α,β$ 的函数）。进一步，通过 $p_a=\frac{\partial S}{\partial q^a}$ 这一组方程就进一步决定了函数 $p_a(t)$。可见，可积系统粒子运动路径的解析解是可以得到的。

一般地，假设找到了哈密顿-雅可比方程的一个解 $S(q,t)$，就能得到粒子正则动量与正则坐标的函数关系 $p_a(t)=\frac{\partial S}{\partial q^a}\left(q_0, q, t\right)$，代入哈密顿正则方程的第一个方程就能解出粒子在位形空间的运动路径，
$$
\dot{q}^a=\left.\frac{\partial H}{\partial p_a}\right|_{p=\frac{\partial S}{\partial q}}
$$
显然，这种求解运动路径的方法最后只需求解 $n$ 个一阶常微分方程，而不是求解 $n$ 个二阶常微分方程，大大简化了问题，但是，我们需要进一步验证哈密顿正则方程的第二个方程也是满足的：
$$
\begin{aligned}
\dot{p}_a & =\frac{d}{d t}\left(\frac{\partial S}{\partial q^a}\right)=\frac{\partial^2 S}{\partial t \partial q^a}+\frac{\partial^2 S}{\partial q^b \partial q^a} \dot{q}^b \\
& \frac{\partial^2 S}{\partial t \partial q^a}+\left.\frac{\partial H}{\partial q^a}\right|_{p=\frac{\partial S}{\partial q}}+\left.\frac{\partial H}{\partial p_b}\right|_{p=\frac{\partial S}{\partial q}} \frac{\partial^2 S}{\partial q^b \partial q^a}=0 \\
\Rightarrow & \frac{\partial^2 S}{\partial t \partial q^a}+\left.\frac{\partial H}{\partial q^a}\right|_{p=\frac{\partial S}{\partial q}}+\dot{q}^b \frac{\partial^2 S}{\partial q^b \partial q^a}=0 . \\
\Rightarrow & \frac{\partial^2 S}{\partial t \partial q^a}+\dot{q}^b \frac{\partial^2 S}{\partial q^b \partial q^a}=-\left.\frac{\partial H}{\partial q^a}\right|_{p=\frac{\partial S}{\partial q}} .
\end{aligned}
$$
假设哈密顿量不显含时间，则有能量守恒，记这个守恒量为 $E$, 哈密顿-雅可比方程当然有依赖于这个守恒量的解，定义
$$
S(E, q, t)=W(E, q)-E t .
$$
将这个定义代入哈密顿雅可比方程，就可以得到
$$
H\left(q, \frac{\partial W}{\partial q}\right)=E .
$$
我们只需求解这个偏微分方程，就能得到原来的哈密顿-雅可比方程的一类解，这类解的特点是，利用它反过来求解出的粒子运动路径都有同样的能量 $E$。$W(E,q)$ 也常常简记为 $W(q)$，人们有时候称之为哈密顿主函数，也叫约化作用量，它是去掉了时间演化项之后的纯空间部分，本质上就是**Maupertuis 最小作用量原理**（Least Action Principle of Maupertuis）中的那个“作用量”。它的定义式是 $W = \int \mathbf{p} \cdot d\mathbf{q}$，在不考虑时间流逝，只考虑空间路径形状时，$W$ 就是那个起决定性作用的“作用量”，有：
$$
p_i=\frac{\partial S}{\partial q^i}=\frac{\partial W}{\partial q^i} \quad \Longrightarrow \mathbf{p}=\nabla W
$$
如果代入具体的哈密顿量，对于一个在势场 $V(q)$ 中运动的经典粒子，哈密顿量通常是 $H = \frac{p^2}{2m} + V(q)$。 把 $p = \nabla W$ 代进去：$\frac{1}{2 m}|\nabla W|^2+V(q)=E$ 整理过后有：
$$
|\nabla W|^2=2 m(E-V(q))
$$
这个式子左边是梯度的平方，右边是一个只依赖于位置 $q$ 的函数。这个形式与几何光学中，如果光在折射率不均匀的介质 $n(q)$ 中传播，描述光波相位（光程）$\mathcal{S}(q)$ 的程函方程 Eikonal Equation 是一样的：
$$
|\nabla \mathcal{S}|^2=n^2(q)
$$
**粒子的动量 $p$** 扮演了 **折射率 $n$** 的角色：在光学里，光线总是向折射率 $n$ 大的地方弯曲（斯涅尔定律）；在力学里，粒子总是向动量 $p$ 大的地方（也就是势能 $V$ 低、动能大的地方）弯曲。所以粒子在势场中的轨迹，完全等同于光线在变折射率介质中的轨迹。而**作用量 $W$** 扮演了 **相位 $\mathcal{S}$** 的角色：$W$ 为常数的曲面，就是“力学波”的**波面**；粒子轨迹（射线），就是垂直于这些波面的线。这个相似性实际上直接导致了量子力学的发现，因为**几何光学**是**波动光学**的近似（当波长 $\lambda \to 0$ 时），而**经典力学**（H-J 方程）长得像几何光学，薛定谔当时就想，如果经典力学相当于“几何光学”，那是不是说明，在经典力学背后，也藏着一个更本质的“波动力学”？于是他反推，通过把 $W$ 视为波动的相位，成功猜出了波函数 $\psi$ 满足的方程——薛定谔方程。

## 5. Rule and Chaos

### 5.1 Invariant Torus

我们已经知道了对称性可以导出守恒律，也看到了对称性决定系统作用量，最后一章我们会看到对称性还强烈限制着哈密顿力学系统的动力学行为：对称性越高，守恒量越多，动力学行为越规则，对称性降低，守恒量越少，则可能导致混沌。

动力学行为最规则的哈密顿系统就是所谓的可积系统，也称作刘维尔可积系统。可以证明刘维尔-阿诺德定理 (Liouville-Arnold Theorem)，如果 $2n$ 维相空间 $\mathcal{M_g}$ 连通且有限（用数学术语来说即紧致），那它一定可以参数化为 $n$ 维环面 $T_n = S^1 ×S^1 ×...×S^1$，即 $\mathcal{M_g} = T^n$，称作相空间的不变环面，不变的意思是，系统始终在这个环面上运动。

$T^n$ 由 $n$ 个圆周作笛卡尔积而成，每一个圆周对应一个拓扑独立的非平凡回路，即不可以通过连续形变相互过渡也不可以连续收缩为一点的回路，因此 $T^n$ 上有 $n$ 个拓扑独立的非平凡回路，不妨记为 $C_a,a = 1,2,...,n$。假设 $\mathcal{M_g} = T^n$ , 则系统就在这个 $n$ 维环面上运动，它在每一个独立回路 $C_a$ 方向都是周期性的，但是整个完整的相轨道却不一定是闭合轨道，因为这里有两种不同的可能性。为了弄清楚问题，我们记系统在 $C_a$ 方向的运动周期为 $T_a$，从而它在这个方向的角频率为 $ω_a = 2π/T_a$ 。仔细考虑一下不难明白，如果任何两个方向的角频率之比 $ω_a/ω_b$ 都是整数比，则各个方向的运动一定有公共的周期，从而整个系统一定作周期性的运动，从而一定是闭合轨道。但是，如果这些角频率之比都是无理数，那就没有公共的周期，也没有闭合轨道，实际上，这时候系统的相轨道最终将密密布满整个 $T^n$ , 称作相轨道遍历整个不变环面。一般来说，对于具有角频率 $\vec{ω}=(ω_1,ω_2,...,ω_n)$ 的不变环面，它不能被相应相轨道遍历的充要条件是，存在一组整数 $\vec{m}=\left(m_1, m_2, \ldots, m_n\right) \neq 0$，使得 $\vec{\omega} \cdot \vec{m}=m_1 \omega_1+m_2 \omega_2+\ldots+m_n \omega_n=0$。这个条件称之为共振条件，满足共振条件的不变环面就是所谓的共振环面。对于可积系统，有另一个刘维尔定理，即可积系统的相空间运动可以通过积分法求解，这里不展开。

总结下来，**可积性意味着相空间被层层叠叠的环面填满。** 系统的动力学行为被完全限制在这些面包圈表面，永远无法逃离，这就是“规则”的几何本质。

### 5.2 Action-Angular Variable

而对于这样规则的系统，可以选择一组非常有用的正则变量，称之为作用-角变量。其中作用变量通常记为 $I_a,a = 1,2,..,n$，是一组互相泊松对易的守恒量，它和原来的守恒量 $G$ 互为函数关系。$I_a$ 常常作为正则动量，与之对应的正则坐标记为 $θ^a$，称作角变量。可积系统的哈密顿量只是作用变量 $I$ 的函数，记为 $H(I)$。作用变量的定义相应于不变环面 $T^n$ 上的非平凡回路，对于每一个独立非平凡回路 $C_a$，可以定义相应的 $I_a$ 如下$I_a=\oint_{C_a} \frac{\Theta}{2 \pi}=\oint_{C_a} \frac{p_b d q^b}{2 \pi}$，而最终的作用变量和角变量满足的哈密顿正则方程为 $\dot{I}_a=0, \dot{\theta}^a=\frac{\partial H}{\partial I_a}=\omega_a(I)$。我们最早谈到的 Bohr-Sommerfeld quantization condition 可以推广为 $I_a=n_a\hbar$ 式中 $n_a$ 为非负整数，是一个标记量子状态的量子数。假设我们以作用变量和角变量为相空间的坐标，那玻尔-索末菲量子化条件将带来一个直观的相空间图像，对于一维运动情 形，它意味着相空间沿着 $θ$ 轴可以划分成一个个长为 $2π$ 的区间，而沿着 $I$ 轴可以划分成一个个长为 $\hbar$ 的区间，这样就可以将整个相空间分成一些宽为 $2π$，高为 $\hbar$, 从而面积为 $2π\hbar$，的小格子，称之为相格。玻尔-索末菲量子化条件告诉我们，每一个相格对应一个量子状态。推广到 $n$ 自由度情形即是，相空间可以划分成一些体积为 $(2π\hbar) n$ 的相格，每一 个相格对应一个量子状态。

作用变量还有一重身份，就是作为所谓的绝热不变量。考虑一个一维系统，假设其势能曲线将系统约束在一个有限的区间上作周期运动，从而其相空间的不变环面就是一条相空间闭合回路 $C$，拓扑上等价于 $S^1$。进一步，再假设势能函数依赖于某个控制参数 $λ$，记为 $V(q,λ)$，因此系统的哈密顿量 $H=\frac{p^2}{2 m}+V(q, \lambda)$。现在，假设我们以几乎恒定的速率缓慢地调节参数 $λ$，即让 $λ$ 以几乎恒定的速率随时间缓慢变化, 记为 $λ(t)$，那这就变成了一个显含时间 $t$ 的系统，能量 $E$ 因此不再守恒，而是也依赖于时间，记为 $E(t)$。很显然，如果参数 $λ$ 相对于系统的运动周期来说变化得足够缓慢，那系统将依然近似作周期运动，但是它的各个物理量 (比如能量) 都将同时随时间缓慢变化。所谓的绝热不变量，指的就是这样一个特殊物理量，它在参数的缓慢调节下保持不变。

作用变量 $I=\frac{1}{2 \pi} \oint p d q$ 就是一个绝热不变量。这是因为 $p=\sqrt{2 m[E-V(q, \lambda)]}=p(q, E, \lambda)$ 从而作用变量也是 $E,\lambda$ 的函数，随着参数的缓慢调节，$E$ 和 $λ$ 都将随时间缓慢变化，但是，这两者的变化并不相互独立，而是满足 $\dot{E}=\frac{\partial H}{\partial t}=\frac{\partial H}{\partial \lambda} \dot{\lambda}$，这两种变化对作用变量 $I$ 的贡献正好相互抵消，从而使 $I$ 绝热不变。一方面，从最早关于势能曲线的讨论知道 $\frac{\partial I}{\partial E}=\frac{T}{2 \pi}$，而另一方面
$$
\frac{\partial I}{\partial \lambda}=\frac{1}{2 \pi} \frac{\partial}{\partial \lambda} \oint p d q=\frac{1}{2 \pi} \oint \frac{\partial p}{\partial \lambda} d q=\frac{1}{2 \pi} \int_0^T \frac{\partial p}{\partial \lambda} \frac{d q}{d t} d t=\frac{1}{2 \pi} \int_0^T \frac{\partial p}{\partial \lambda} \frac{\partial H}{\partial p} d t=-\frac{1}{2 \pi} \int_0^T \frac{\partial H}{\partial \lambda} d t 
$$
综合起来，有
$$
\dot{I}=\frac{\partial I}{\partial E} \dot{E}+\frac{\partial I}{\partial \lambda} \dot{\lambda}=\left(\frac{\partial I}{\partial E} \frac{\partial H}{\partial \lambda}+\frac{\partial I}{\partial \lambda}\right) \dot{\lambda}=\left(T \frac{\partial H}{\partial \lambda}-\int_0^T \frac{\partial H}{\partial \lambda} d t\right) \frac{\dot{\lambda}}{2 \pi}
$$
接下来对一个运动周期求平均 $\bar{A}=\frac{1}{T} \int_0^T d t A(t, \lambda)$ 会发现两项就正好抵消了，即 
$$
\overline{\dot{I}}=0,\quad I(t+T)=I(t)
$$
也即是说，对于足够缓慢的参数调节来说，作用变量最多是以运动周期为周期的函数，或者说作用变量在一个周期之内的平均变化率为零，这才是前面我们说作用变量是绝热不变量的精确含义。注意到相对于参数变化的时间尺度而言，运动周期 $T$ 是非常短的，因此这其实是说，作用变量在参数变化的时间尺度上近似不变。以一维运动的谐振子为例，其哈密顿量为 $H = Iω$，因此即使谐振子的频率 $ω$ 随时间缓慢变化，谐振子能量 $E$ 与 $ω$ 的比值 $E/ω$ 也近似保持不变。

实际上，历史上在从经典力学到量子力学的过渡过程中，人们首先注意到了作用变量的绝热不变性，即注意到作用变量在参数的缓慢变化下保持不变的性质，这使得人们自然假设它是一个量子化的量 (因为量子化的量不能连续变化，从而自然在参数的连续变化下保持不变)，由此人们才提出作用变量的玻尔-索末菲量子化条件。

### 5.3 Nearly Integrable System and Chaos

如果对可积系统 $H_0(I)$ 加微扰 $H(I, \theta)=H_0(I)+\varepsilon H_1(I, \theta)$，这个扰动以后的系统就是一个近可积系统。KAM 定理是说，非退化的可积系统在上述扰动之后，虽然某些不变环面会被扰动破坏掉（称为共振环面），但所谓满足强非共振条件的不变环面（这种不变环面占大多数）仍然会被保存下来。也就是说近可积系统整个相空间中大部分的相轨道依然是非常规则的！在那些不变环面被扰动破坏的相空间区域，随着不变环面的破坏可能发生两件事情：第一，系统的相空间轨迹可能会与邻近轨迹发生剧烈的甚至随时间指数增长的偏离，从而导致对初始条件的极端敏感性和混沌行为。第二，它可能使得系统演化缺乏可预测性。即使我们处理的是严格的确定性系统，它也可能产生有效的随机输出，从而使得系统丧失可预测性。

由于哈密顿系统通常维数较高（$2n \ge 4$），直接画出相轨迹很难看清结构。庞加莱引入了降维打击的方法：**庞加莱截面 (Poincaré Section)**。 我们在相空间中取一个横截面 $\Sigma$（维数为 $2n-1$），记录轨迹每次穿过该截面的点。这就把连续时间的流 $\phi_t$ 转化为了离散时间的映射 $P: \Sigma \to \Sigma$，称为**庞加莱映射**。
- **规则运动 (可积)**：轨迹在环面上缠绕。如果频率比是有理数，截面上出现有限个离散点（周期轨道）；如果是无理数，点会密密麻麻地描绘出一条**闭合曲线**（环面的截面）。
- **混沌运动 (不可积)**：当扰动增强，KAM 环面破裂。截面上的点不再落在闭合曲线上，而是像灰尘一样随机散布在一个区域内，形成所谓的 **“混沌海” (Chaos Sea)**。
这种从“闭合曲线”到“弥散点集”的几何相变，是识别混沌最直观的指纹。

假设我们考察的既不是可积系统，又不是近可积系统，而是一个一般性的哈密顿系统，其泊松对易的守恒量的数目少于自由度数目 $n$，甚至当自由度数目 $n$ 很大时大大少于 $n$，比方说只有一个守恒量，即能量。那这时候系统的动力学行为往往不再规则，而是常常会表现出混沌。双摆系统是一个两自由度的系统，但是它只有一个守恒量，即能量，当能量足够大时这个系统会表现出混沌行为；庞加莱在研究受限三体问题时发现了混沌；两维平面上的涡旋系统，只找到 3 个相互泊松对易的守恒量，所以对于 3 个涡旋的情形，那是一个可积系统，但是 4 个和 4 个以上涡旋的运动则通常是混沌的。

为什么微扰会导致混沌？几何上的罪魁祸首是**共振 (Resonance)** 附近的结构不稳定性。 在可积系统中，共振区域通常存在一种特殊的轨道——**分界线 (Separatrix)**（例如单摆从摆动到旋转的临界轨道）。分界线连接了不稳定的平衡点。 当微扰 $\epsilon H_1$ 加入时，KAM 定理告诉我们，远离共振的环面因频率极度无理而难以被破坏。但是，在共振附近，微扰虽然微小，却足以打破分界线的重合结构。 原本重合的“稳定流形”和“不稳定流形”不再平滑连接，而是发生横截相交。根据斯梅尔 (Smale) 的理论，一旦发生一次相交，它们就会发生无数次相交，形成极其复杂的折叠和纠缠结构，称为 **同宿纠缠 (Homoclinic Tangle)**。 这种纠缠迫使相体积在极小的区域内反复拉伸和折叠（Smale Horseshoe Map），从而导致了对初值的指数敏感性。因此，**混沌总是最先在共振产生的分界线附近萌芽，随着扰动增大，逐渐吞噬周围的规则环面。**

我们已经看到，随着扰动的增强，KAM 环面破裂，同宿纠缠导致了混沌海的形成。这在动力学上不仅意味着“乱”，更意味着一种全新的守恒律的破坏与重构。对于**可积系统**，相点被限制在 $T^n$ 环面上，它永远无法访问具有相同能量的其他相空间区域。这种系统是**非各态历经 (Non-Ergodic)** 的。对于这样的系统，时间平均 $\neq$ 空间（能面）平均。然而，对于**充分混沌**的系统（或者说在混沌海区域），同宿纠缠引发了强烈的**混合 (Mixing)** 效应。原本聚在一起的相体积元会被无限拉伸、折叠，像墨水滴入水中一样均匀散布到整个可及的相空间区域。这引出了统计物理最核心的概念：**各态历经性 (Ergodicity)**。

**各态历经假设 (Ergodic Hypothesis)** 断言：对于一个混沌系统，一条典型的相轨迹在经过足够长的时间后，会无限逼近能量曲面上的每一点。
$$\lim_{T \to \infty} \frac{1}{T} \int_0^T f(\mathbf{x}(t)) dt = \frac{1}{\text{Vol}(\Omega)} \int_{\Omega} f(\mathbf{x}) d\Omega$$
即：**时间平均 = 相空间（系综）平均**。其几何定义是，在能量为 $E$ 的曲面（能面）上，**几乎所有的点都落在同一条无限长的轨迹上**。其物理意义首先在于微观信息的耗散：由于混沌的混合特性，系统彻底“遗忘”了具体的初始条件，只记住了唯一的守恒量——能量 $H$。

更重要的是，各态历经性 (Ergodicity) 使我们刚才从哈密顿动力学（Liouville定理）中“推导”出来统计力学中的基本假设等概率原理的一个漏洞。回顾一下之前的逻辑链：**Liouville** $\implies$ $\frac{d\rho}{dt} = 0$；**平衡态** $\implies$ $\frac{\partial \rho}{\partial t} = 0$；**结论** $\implies$ $\{\rho, H\} = 0$，即 $\rho$ 是运动常数的函数。**漏洞就在这最后一步：** 如果 $\rho$ 是运动常数的函数，它**一定**只依赖于哈密顿量 $H$ 吗？即 $\rho = f(H)$？不一定。如果系统除了能量 $H$ 之外，还有其他的守恒量（比如角动量 $L$，或者像可积系统里的作用量 $I_2, I_3 \dots$），那么分布函数完全可以是：
$$\rho = f(H, L, I_2, \dots)$$
这就出问题了。在同一个能面（$H=E$）上，可能有 $L=0$ 的区域，也有 $L=100$ 的区域。如果 $\rho$ 依赖于 $L$，那么 $\rho$ 在 $H=E$ 的能面上就**不是均匀的**！它可能在 $L=0$ 的地方很密，在 $L=100$ 的地方很稀。这直接否定了“等概率原理”的普适性证明。只要系统有多余的守恒量（可积系统），微正则分布（均匀分布）就不是唯一的平衡分布，等概率原理就不成立。

为了让“等概率原理”成立，物理学家（最早是玻尔兹曼）引入了**各态历经假设**。因为刘维尔定理 $\rho$ 在一条轨迹上必须是守恒量，那么再加上各态历经假设，就有 $\rho$ 在整个能面上必须是一个**常数**。而如果有除了能量守恒即 $H$ 以外的守恒量，那么就又有了运动的限制，也违反了各态历经假设。在这种情况下，$\rho$ **只能**是 $H$ 的函数，在 $H=E$ 面上没有其他区分标志了，$\rho$ 必须是常数。**所以，真相是：**
$$\text{Liouville定理} + \text{各态历经假设} \Longrightarrow \text{等概率原理}$$
最尴尬的地方在于，数学上，证明各态历经性极其困难，甚至在很多情况下是错的。比如刚刚讲过的 KAM 定理，对于绝大多数经典系统（近可积系统），相空间里充满了**不变环面**。粒子被锁在环面上，根本跑不到能面的其他地方去。严格来说，这些系统**不是**各态历经的。只有在强混沌系统中（如阿诺德猫映射，或者硬球气体模型），各态历经性才被严格证明。那么，既然大多数系统（如KAM系统）不是严格各态历经的，为什么统计力学还能用？这有两派解释：

**物理派（“实际上够用了”）** 虽然数学上存在 KAM 环面，但在宏观系统（$N \sim 10^{23}$）中，这些非各态历经的区域（环面）虽然存在，但在相空间中所占的体积比例极小，或者微小的外界扰动就足以打破它们。对于实际的宏观时间尺度，我们可以“实际上”认为系统跑遍了大部分能面。

**信息论派（Jaynes 的最大熵原理）** 这是更现代、更深刻的观点（E.T. Jaynes）。 它认为“等概率原理”根本不需要动力学去“证明”。它不是关于自然的定律，而是关于我们“知识匮乏”的定律。如果你只知道系统的能量是 $E$，除此之外一无所知（不知道是否有其他隐藏守恒量，也不知道具体的初始位置）。**推论**：那么，对你来说，**最诚实、最不偏不倚**的猜测是什么？当然是假设所有可能状态概率相等！**结论**：如果你假设 $\rho$ 不均匀，你就引入了你并不拥有的“额外信息”（Bias）。所以，等概率原理实际上是**信息熵最大化（Max Entropy）**的结果。

最后我们补充一下混沌是对初值的“敏感依赖性”的定量描述，我们通过 **李雅普诺夫指数 (Lyapunov Exponent, $\lambda$)** 来衡量两条邻近轨道在相空间中分离的速率。假设 $t=0$ 时两条轨道的初始距离为 $|\delta \mathbf{x}(0)|$，随着时间演化，它们的距离大约按指数规律变化：
$$|\delta \mathbf{x}(t)| \approx e^{\lambda t} |\delta \mathbf{x}(0)|$$
- 如果 $\lambda \le 0$，轨道保持靠近或仅仅是多项式分离（规则运动）。
- 如果 $\lambda > 0$，轨道呈指数分离。
一个 $2n$ 维的哈密顿系统有 $2n$ 个李雅普诺夫指数（成对出现，$\pm \lambda_i$），只要其中**最大的那个指数 $\lambda_{max} > 0$**，我们就判定系统处于混沌状态。$\lambda_{max}$ 的倒数 $1/\lambda_{max}$ 定义了**“李雅普诺夫时间”**，也就是系统可预测性的时间视界（Event Horizon of Predictability）。

## 6. From Dynamics to Statistics

我们这趟经典力学之旅，从最简单的单粒子运动方程 $F=ma$ 开始，经过了拉格朗日与哈密顿形式的几何化，最终在相空间中看到了规则的环面与纠缠的混沌。

当我们面对宏观系统（粒子数 $N \sim 10^{23}$）时，追踪每一个自由度的正则方程 $\dot{\mathbf{x}} = J \nabla H$ 既不可能也无必要。我们需要一种新的语言。这不仅是计算上的妥协，更是物理本质的升华。在本章，我们将综述经典力学是如何为统计力学铺平道路的，揭示热力学定律并非凭空产生，而是哈密顿动力学在混沌与大数定律下的自然涌现。

### 6.1 The Necessity of Ignorance

我们已经知道，对于一般的三体或更多体系统，混沌是普遍存在的，无论我们的测量多么精确，只要有无穷小的误差，在有限的“李雅普诺夫时间”后，我们对系统微观状态的预测将完全失效。对于宏观系统，这个时间尺度极短。因此，**微观信息的丢失是不可避免的**。这种“无知”迫使我们将描述对象从精确的“点（轨迹）”转变为相空间中的“体积（概率分布）”，从追踪 $\mathbf{x}(t)$ 转变为研究分布函数 $\rho(\mathbf{x}, t)$ 的演化。这便是 **系综 (Ensemble)** 概念的起源。

### 6.2 The Geometric Foundation: Liouville's Theorem & Ergodicity

既然我们必须研究概率密度 $\rho$，那么动力学定律（哈密顿方程）对 $\rho$ 施加了什么约束？答案在于刘维尔定理，从它出发我们可以得知：
$$\frac{d\rho}{dt} = \frac{\partial \rho}{\partial t} + \{\rho, H\} = 0$$
即沿着相流运动，概率密度是守恒的。这是统计力学成立的基石——相体积（即微观状态数）在动力学演化下具有刚性，不会凭空消失或产生。

如果我们寻找系统的 **统计平衡态**（即宏观性质不随时间变化，$\frac{\partial \rho}{\partial t} = 0$），刘维尔方程立即给出一个强约束：$\{\rho, H\} = 0$。这意味着 $\rho$ 必须是运动常数的函数。

如果再加上 **各态历经性 (Ergodicity)**（通常由 Sec 5.3 中讨论的混沌机制导致），情况将发生质变。由于同宿纠缠带来的混合效应，除了能量 $H$ 以外的所有几何约束（“墙”）都被打破，轨迹能够跑遍整个能面。在这种情况下，$\rho$ 只能依赖于 $H$。对于固定能量 $E$ 的孤立系统，$\rho$ 在能面上只能是一个常数。这就在动力学上证明了统计力学的 **等概率原理 (Fundamental Assumption)**：

> 对于各态历经的孤立系统，所有满足 $H(\mathbf{q}, \mathbf{p})=E$ 的微观状态出现的概率相等。

### 6.3 Emergence of Thermodynamics

一旦建立了微正则分布，经典力学的几何量就直接转化为了热力学的宏观量。通过这种方式，温度、压力、化学势等概念，不再是人为的定义，而是哈密顿系统在混沌与大数定律下，从辛几何结构中自然涌现的统计规律。

**熵与相体积 (Entropy and Phase Volume)** 我们在 5.2 节中引入了相格的概念，相空间被量子化为体积 $h^{3N}$ 的单元。微观状态数 $g(E)$ 本质上就是能量曲面所围成的辛体积：$g(E) \sim \frac{1}{h^{3N}} \int \delta(H(\mathbf{q}, \mathbf{p}) - E) \, d\Omega$。**熵** 被定义为 $S = k_B \ln g$。这解释了熵的广延性，因为它直接对应于高维相空间体积的对数。绝热过程 (Adiabatic Process) 在 5.2 节，我们证明了当参数缓慢变化时，作用量变量 $I = \oint p dq$ 是绝热不变量。 在统计力学中，缓慢改变体积而不交换热量的过程被称为绝热过程，其特征是熵 $S$ 不变。 这揭示了深刻的对应关系：**宏观的熵 $S$ 守恒，微观上对应于系统被限制在特定的相体积（或量子态）内演化，即作用量 $I$ 的守恒。

温度的几何起源：高维球体体积 (Geometric Origin of Temperature)。在纯粹的哈密顿力学方程 $F=ma$ 中，并不存在“温度”这个变量，只有动能。温度的涌现，源于我们将统计力学的定义应用于相空间特定的几何结构。几何设定为，考虑由 $N$ 个无相互作用粒子组成的理想气体。其哈密顿量为纯动能：
$$H(\mathbf{q}, \mathbf{p}) = \sum_{i=1}^{3N} \frac{p_i^2}{2m} = E$$
在 $3N$ 维的动量空间中，方程 $\sum p_i^2 = 2mE$ 定义了一个半径为 $R = \sqrt{2mE}$ 的**超球面**。微观状态数 $g(E)$ 正比于能量 $E$ 以下的相体积 $\Omega$。根据 $d$ 维球体的体积公式 $V_d(R) \propto R^d$，这里的维度 $d=3N$：
$$g(E) \sim \Omega(E) = \int_{H<E} d^{3N}q \, d^{3N}p = V^N \cdot C_{3N} ( \sqrt{2mE} )^{3N}$$
略去常数因子，我们得到相体积随能量的依赖关系：$g(E) \propto E^{\frac{3N}{2}}$。此时根据熵的统计定义 $S = k_B \ln g(E)$ 以及温度的统计定义 $1/T = \partial S / \partial E$：
$$ \frac{1}{T} \equiv \frac{\partial S}{\partial E} = k_B \frac{\partial}{\partial E} \ln \left( E^{\frac{3N}{2}} \right) = k_B \frac{3N}{2} \frac{1}{E}$$
整理该式，既然总能量 $E$ 等于总动能 $\langle K_{total} \rangle$，我们得到：
$$ \langle K_{total} \rangle = \frac{3}{2} N k_B T$$
**结论（均分定理）**：这是热力学与力学的第一座桥梁。它揭示了：**温度本质上是 $3N$ 维相空间体积随能量膨胀的“相对速率” (Logarithmic expansion rate)。** 维度 $N$ 越高，体积随能量增长越快，对应的能量-温度比例系数就越确定。

压强的动力学起源：维里定理 (Virial Theorem)。既然温度对应动能，那么 **压强 (Pressure)** 是什么？我们不需要借助热力学公式，而是可以直接从哈密顿动力学推导出一个 **纯力学的状态方程**。这依赖于 **维里定理**。**维里量的演化**： 定义一个标量函数，称为“维里” (Virial)：$G = \sum_i \mathbf{p}_i \cdot \mathbf{x}_i$。 计算其随时间的变化率：
$$ \frac{dG}{dt} = \sum_i \dot{\mathbf{p}}_i \cdot \mathbf{x}_i + \sum_i \mathbf{p}_i \cdot \dot{\mathbf{x}}_i$$
利用哈密顿方程（或牛顿定律）$\dot{\mathbf{x}}_i = \mathbf{v}_i$ 和 $\dot{\mathbf{p}}_i = \mathbf{F}_i$，代入得：
$$ \frac{dG}{dt} = \sum_i \mathbf{F}_i \cdot \mathbf{x}_i + \sum_i m \mathbf{v}_i^2$$
即：$\frac{dG}{dt} = \sum \mathbf{F}_i \cdot \mathbf{x}_i + 2K$，其中 $K$ 是总动能。做时间平均： 对于被束缚在容器内的气体，系统处于稳态，坐标和动量都是有界的。因此，$G(t)$ 也是有界的。对上式取长时间平均 $\langle \cdot \rangle = \lim_{\tau \to \infty} \frac{1}{\tau} \int_0^\tau dt$：
$$ \left\langle \frac{dG}{dt} \right\rangle = \lim_{\tau \to \infty} \frac{G(\tau) - G(0)}{\tau} = 0$$
于是我们得到了著名的 **维里定理**：
$$ 2 \langle K \rangle = - \left\langle \sum_i \mathbf{F}_i \cdot \mathbf{x}_i \right\rangle$$
**压强的涌现**： 右边的力 $\mathbf{F}_i$ 是粒子受到的合力，对于理想气体，粒子间无相互作用，力仅来源于**容器壁的约束力** $\mathbf{F}_{wall}$。 这个求和可以转化为对容器表面的积分。设容器壁对粒子施加的压强为 $P$，则面元 $d\mathbf{A}$ 上的力为 $d\mathbf{F} = -P \hat{n} dA$（指向容器内）。
$$ \sum_i \mathbf{F}_i \cdot \mathbf{x}_i \approx \oint_{\partial V} (-P \hat{n} dA) \cdot \mathbf{x} = -P \oint_{\partial V} \mathbf{x} \cdot \hat{n} dA$$
利用高斯散度定理 $\oint \mathbf{x} \cdot \hat{n} dA = \int_V (\nabla \cdot \mathbf{x}) dV$。由于 $\nabla \cdot \mathbf{x} = \frac{\partial x}{\partial x} + \frac{\partial y}{\partial y} + \frac{\partial z}{\partial z} = 3$，所以：
$$ -P \int_V 3 dV = -3PV$$
将此结果代回维里定理：
$$ 2 \langle K \rangle = - (-3PV) = 3PV$$
**结论（力学状态方程）**：
$$PV = \frac{2}{3} \langle K \rangle$$
请注意，这是一个 **纯力学推导的结果**。它完全不依赖于温度、熵或热力学，它仅仅联系了压强（约束力）、体积（约束空间）和动能（微观运动）。

现在，我们将上述两个独立推导的结果结合起来：**来自几何与统计的**：$\langle K \rangle = \frac{3}{2} N k_B T$，**来自哈密顿动力学的**：$\langle K \rangle = \frac{3}{2} PV$，我们直接得出了：
$$\frac{3}{2} PV = \frac{3}{2} N k_B T \quad \Longrightarrow \quad PV = N k_B T$$
这展示了完整的逻辑链条：**维里定理提供了宏观状态方程的动力学骨架（$P$ 与 $E$ 的关系），而相空间几何（熵）赋予了能量以温度的灵魂（$E$ 与 $T$ 的关系）。** 理想气体定律并非仅仅是实验规律的总结，它是哈密顿力学在大数统计下的必然几何投影。

## 7. Summary: The Geometric Unity of Physics

最后，我们将经典力学的几何结构与我们窥探到的量子力学特性进行对比。我们发现，物理学并非是由互不相关的理论拼凑而成，而是共享着同一套深层的数学骨架。经典力学并非是被量子力学“推翻”的旧理论，而是量子力学在 $\hbar \to 0$ 极限下的几何投影。

| **概念**    | **拉格朗日力学 (流形 $TM$)** | **哈密顿力学 (辛流形 $T^∗M$)**      | **量子力学 (希尔伯特空间 $H$)**                             |
| --------- | -------------------- | --------------------------- | ------------------------------------------------- |
| **状态描述**  | 位置与速度 $(q, \dot{q})$ | 相空间点 $(q, p)$               | 态矢量 $                                             |
| **动力学变量** | 标量函数 $L(q, \dot{q})$ | 相空间函数 $f(q, p)$             | 线性算符 $\hat{f}$                                    |
| **基本结构**  | 变分原理 $\delta S = 0$  | 辛形式 $\omega$ / 泊松括号 $\{,\}$ | 对易子 $[\hat{A}, \hat{B}]$                          |
| **代数关系**  | (隐含)                 | $\{q, p\} = 1$              | $[\hat{q}, \hat{p}] = i\hbar$                     |
| **对称性生成** | 诺特定理 (流)             | 哈密顿矢量场 $X_G$                | 酉算符 $\hat{U} = e^{-i\hat{G}\theta}$               |
| **时间演化**  | E-L 方程               | $\dot{f} = \{f, H\}$        | $i\hbar \frac{d}{dt}\hat{f} = [\hat{f}, \hat{H}]$ |
| **几何图像**  | 切丛上的测地线              | 辛流形上的哈密顿流                   | 酉群在希尔伯特空间的作用                                      |
| **波粒二象性** | 最小作用量原理              | H-J 方程 (射线/法线)              | 薛定谔方程 (波动)                                        |
| **规则与混沌** | 耗散/驱动                | KAM 环面 vs 同宿纠缠              | 量子混沌 (能级统计/随机矩阵)                                  |
| **统计基础**  | (隐含)                 | 相体积 (辛体积)                   | 希尔伯特子空间维数 (Trace)                                 |


**References & Further Reading:** 这份笔记的几何化视角深受以下经典著作的启发，推荐进一步阅读：

1. **V.I. Arnold**, _Mathematical Methods of Classical Mechanics_ (经典力学的几何圣经)
2. **L.D. Landau & E.M. Lifshitz**, _Mechanics_ (物理直觉的巅峰)
3. **Herbert Goldstein**, _Classical Mechanics_ (标准教材)
4. **Baez & Muniain**, _Gauge Fields, Knots and Gravity_ (关于几何与规范场的极佳读物)

