# 普通物理学二(H)
> 授课:方明虎

## Electric Charge and Coulomb's Law(电荷和库仑定律)

**A ring of charge**

对于一个均匀带电的圆环，距离其中心 $z$ 的带电量为 $q_0$ 所受的沿 $Z$ 方向的力 $F_z$ 

<div align=center><img src="https://raw.githubusercontent.com/kailqq/cdn_img/master/img/image.png" width=55%/></div>

先计算电荷密度

\[
\lambda = \frac{q}{2 \pi R}
\]

\[
dF = \frac{1}{4 \pi \epsilon_0} \frac{q_0 dq}{r^2} = \frac{1}{4 \pi \epsilon_0} \frac{q_0 \lambda Rd\phi}{(z^2 + R^2)}
\]

\[
F_z = \int dF_z = \int dF \cos \theta = \int \frac{q_0 \lambda Rd\phi}{4 \pi \epsilon_0 (z^2 + R^2)} \frac{z}{\sqrt{z^2 + R^2}}
\]

\[
= \frac{1}{4 \pi \epsilon_0} \int_0^{2\pi} \frac{q_0 \lambda Rz}{(z^2 + R^2)^{3/2}} d\phi
\]

\[
= \frac{1}{4 \pi \epsilon_0} \cdot \frac{q_0 q z}{(z^2 + R^2)^{3/2}} \bigg|_0^{2\pi}
\]

\[
= \frac{1}{4 \pi \epsilon_0} \cdot \frac{q_0 q z}{(z^2 + R^2)^{3/2}}
\]


!!!Note
    当 $z$ 非常大,原式子就退化成了两个点电荷之间的相互作用
    
    \[
      z \to +\infty, F_z \to \frac{1}{4 \pi \epsilon_0} \dfrac{q_0q}{z^2}
    \]

**A disk of charge**

如果是一个圆盘，$F_z$ 可以用圆环来逼近

<div align=center><img src="https://raw.githubusercontent.com/kailqq/cdn_img/master/img/image-1.png" width=55%/></div>

\[
\sigma = \frac{q}{\pi R^2}
\]

\[
dq = \sigma dA = \sigma(2 \pi \omega d\omega) = 2 \pi \sigma \omega d\omega
\]

\[
dF_z = \frac{1}{4 \pi \epsilon_0} \frac{q_0 (2 \pi \sigma \omega d\omega) z}{(z^2 + \omega^2)^{3/2}}
\]

\[
F_z = \frac{1}{4 \pi \epsilon_0} q_0 2 \pi \sigma z \int_0^{R} \frac{\omega d\omega}{(z^2 + \omega^2)^{3/2}}
\]

\[
= \frac{1}{4 \pi \epsilon_0} \cdot \frac{2 q_0 q}{R^2} \left( 1 - \frac{z}{\sqrt{z^2 + R^2}} \right)
\]

当 $z$ 非常大,原式子就退化成了两个点电荷之间的相互作用(用Taylor展开分析)


$$ z \to +\infty, F_z \to \frac{1}{4 \pi \epsilon_0} \dfrac{q_0q}{z^2} $$

\[
  \left( 1 - \frac{z}{\sqrt{z^2 + R^2}} \right) \to \left( 1- (1+\frac{R^{2}}{z^{2}})^{-\frac{1}{2}} \right) = \frac{R^{2}}{2z^{2}}
\]

**A infinite stick of charge**

<div align=center><img src="https://raw.githubusercontent.com/kailqq/cdn_img/master/img/20240917150153.png" width=55%/></div>

由于对称性，在$x$方向上没有电场

$$
\begin{align*}
  dq &= \lambda dx = \lambda d(r \tan \theta) = \lambda r \sec^2 \theta d\theta \\
  dE_y &= dE \cos \theta= \frac{1}{4 \pi \varepsilon_0} \frac{dq}{r'^2} \cos \theta \\
  &= \frac{1}{4 \pi \varepsilon_0} \frac{\lambda r\cos^2 \theta \sec^2 \theta d\theta}{r^2} \cos \theta \\
  &= \frac{1}{4 \pi \varepsilon_0} \frac{\lambda \cos \theta d\theta}{r}\\
  E_y &= \int_{-\frac{\pi}{2}}^{\frac{\pi}{2}} dE_y = \int_{-\frac{\pi}{2}}^{\frac{\pi}{2}} \frac{1}{4 \pi \varepsilon_0} \frac{\lambda \cos \theta d\theta}{r} \\
  &= \dfrac{\lambda}{2 \pi \varepsilon_0 r} \
\end{align*}
$$

### Dipole(电偶极矩)

!!!Definition 
    电偶极矩是描述带电粒子系统中电荷分布的物理量，通常用于量化两个相反电荷之间的分离程度和方向。在经典电磁学中，电偶极矩通常表示为一个矢量，其大小等于电荷量乘以电荷间的距离。
    定义为：

    \[
    \boldsymbol{p} = q \cdot \boldsymbol{d}
    \]

    其中：

    - \( q \) 是两个相反电荷的电荷量，
    - \( \mathbf{d} \) 是从负电荷指向正电荷的矢量，表示两个电荷之间的距离。

    电偶极矩的方向从负电荷指向正电荷，因此在分子或原子系统中，它反映了电荷不对称分布的程度。对于分子，电偶极矩的大小和方向对分子的化学性质和反应性有重要影响。

    电偶极矩的单位通常是德拜（Debye，符号为 D），1 德拜大约等于 \( 3.33564 \times 10^{-30} \) 库仑·米。
    
根据电偶极矩可以将分子间作用力分为几种类型

<div align=center><img src="https://raw.githubusercontent.com/kailqq/cdn_img/master/img/20240917121336.png" width=55%/></div>


- **离子-偶极相互作用（Ion-Dipole Interaction）**

离子-偶极相互作用发生在带电的离子和极性分子之间。当离子（如 \( \text{Na}^+ \) 或 \( \text{Cl}^- \)）靠近一个有电偶极矩的分子（如水分子，H\(_2\)O）时，离子会与极性分子的部分正电荷或负电荷产生吸引力。

!!!eg
    在盐溶解于水的过程中，水分子的极性部分（氧的负电部分或氢的正电部分）与钠离子或氯离子之间产生的吸引力是离子-偶极相互作用。这种相互作用有助于溶解过程。

- **偶极-偶极相互作用（Dipole-Dipole Interaction）**

偶极-偶极相互作用发生在两个极性分子之间，这些分子都有永久的偶极矩。当一个分子的正电部分接近另一个分子的负电部分时，它们之间会产生吸引力。

!!!eg
    像氯化氢 (HCl) 这样的极性分子之间的相互作用就属于偶极-偶极相互作用。HCl 分子的氯原子带负电，而氢原子带正电，这两种相反的电荷相互吸引，从而形成偶极-偶极相互作用。

-  **伦敦色散力（London Dispersion Force）**

伦敦色散力，又称为**瞬时偶极-诱导偶极力**，是一种在所有原子和分子之间都存在的弱相互作用力，特别是对于非极性分子。它是由瞬时的电子运动引起的，即在某个瞬间，分子或原子周围的电子云分布不均匀，形成瞬时偶极，这个瞬时偶极会诱导临近分子或原子产生相似的瞬时偶极，从而产生吸引力。

!!!eg
      即使是像氮气 (N\(_2\)) 和氧气 (O\(_2\)) 这样的非极性分子，也存在伦敦色散力。这种相互作用虽然很弱，但对大多数非极性物质的凝聚力和熔沸点有重要影响。



#### 电偶极矩产生的电场

<div align=center><img src="https://raw.githubusercontent.com/kailqq/cdn_img/master/img/20240917122502.png" width=45%/></div>



\[
  E_x(x,0)=0(symmetry)
\]

\[
E_y(x,0) = -2 \cdot \frac{1}{4 \pi \varepsilon_0} \cdot \frac{Q}{r^2} \sin \theta
\]

\[
\sin \theta = \frac{a}{r}, \quad r^2 = x^2 + a^2
\]

\[
E_y(x,0) = -2 \cdot \frac{1}{4 \pi \varepsilon_0} \cdot \frac{Qa}{(x^2 + a^2)^{3/2}}
\]

!!!Note
    \[
    for \ r>>a  \\
    E_y(r,0) = -2 \cdot \frac{1}{4 \pi \varepsilon_0} \cdot \frac{Qa}{r^3}
    \]

如果考虑 $(0,y)$ 上的电场，则其在 $x$ 方向上没有分量


\[
  E_x(0,y)=0
\]

\[
\begin{align*}
E_y(0,y) &= \frac{Q}{4 \pi \varepsilon_0} \cdot \left(\frac{1}{(y-a)^2}-\frac{1}{(y+a)^2}\right)\\
         &= \frac{Q}{4 \pi \varepsilon_0} \cdot \dfrac{4ay}{y^4(1-\frac{a^2}{y^2})^2}
\end{align*}
\]

!!!Note
    \[
    for \ r>>a  \\
    E_y(0,r) = 4 \cdot \frac{1}{4 \pi \varepsilon_0} \cdot \frac{Qa}{r^3}
    \]

!!!eg
    北高峰上的天线和紫金港的分子

    $E$ 和 $r^3$ 成反比 

!!!Key-point
    电偶极矩的电场与距离$r^3$成反比，而点电荷的电场与距离$r^2$成反比，无穷长导线的电场与距离$r$成反比

#### 电偶极矩在电场中

<div align=center><img src="https://raw.githubusercontent.com/kailqq/cdn_img/master/img/20240918084819.png" width=55%/></div>

$$
   \tau = F \cdot \frac{d}{2} \sin \theta + F \cdot \frac{d}{2} \sin \theta = Fd \sin \theta = qEd \sin \theta
   = pE \sin \theta
$$

$$
    \boldsymbol{p}=q\boldsymbol{d} \\
    \boldsymbol{\tau}= \boldsymbol{p} \times \boldsymbol{E}
$$

!!!Key-point
     电偶极矩在电场中受到的力矩会驱使电偶极矩旋转上与电场方向对齐

对于电偶极矩在电场中的势能

$$
\begin{align*}
  W &=\int dw = \int_{\theta_0}^{\theta} \tau \cdot d\theta = - \int_{\theta_0}^{\theta} pE \sin \theta d\theta \\ 
  &= pE(\cos \theta - \cos \theta_0) \\
  \Delta U &= U(\theta) - U(\theta_0)=-W\\
           &= pE(\cos \theta_0 - \cos \theta)\\
  \theta_0 &= \frac{\pi}{2}, U(\theta_0) = 0\\
 U(\theta) &= -pE\cos \theta= -\boldsymbol{p} \cdot \boldsymbol{E}
\end{align*}
$$

第一个式子的负号是因为力矩与角度的变化方向相反

