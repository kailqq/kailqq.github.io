# 光学


## 可见光

在电磁波中，可见光只占了很小一部分

<div align=center>
<img src="../img/light/light1.png" width="70%">
</div>

!!!property
    - 可见光波长范围：$400nm-700nm$
    - 可见光频率范围：$4.3\times10^{14}Hz-7.5\times10^{14}Hz$
    - 可见光波长与频率的关系：$\lambda f=c$
    - 人眼最敏感的波长$550nm$左右为黄绿光
    - 波长越长，频率越低，能量越低,所以红光能量最低，紫光能量最高
    - 

### 波的多普勒效应

\[
f'=\dfrac{v\pm v_0}{v\pm v_s}f
\]

其中，$v$为波在介质中的传播速度，波源速度为$v_s$，接收者速度为$v_0$，$f$为波的频率

对于光波，有红移和蓝移

- 红移：波源远离接收者，波长变长，频率变小，光谱向红色移动

\[
    f=f_0 \sqrt{\dfrac{1-\frac{u}{c}}{1+\frac{u}{c}}}
\]

- 蓝移：波源靠近接收者，波长变短，频率变大，光谱向蓝色移动
  
\[
    f=f_0 \sqrt{\dfrac{1+\frac{u}{c}}{1-\frac{u}{c}}}
\]

!!!key-point 
    通式为
    
    \[
        f = f_0 \dfrac{\sqrt{1-\frac{u^2}{c^2}}}{1-\frac{u}{c}\cos \theta}
    \]

    其中$\theta$为速度与光波运动的夹角


## 几何光学

### 全反射

全反射是光波在传播过程中发生的一种物理现象。当光从光密介质（如玻璃或水）进入光疏介质（如空气）时，如果入射角大于某个临界角（称为临界角），光就不会发生折射，而是全部被反射回光密介质，这种现象称为全反射

<div align=center>
<img src="../img/light/light2.png" width="70%">
</div>

例如，在玻璃中，$n=1.5$，在空气中，$n_0=1$;又有

\[
   \dfrac{\sin \theta_2}{\sin \theta_1}=\dfrac{n_1}{n_2}
\]

临界角为$\theta_2 = 90^\circ$，所以此时

\[
    \sin \theta_c = \dfrac{n_2}{n_1}
\]

如果入射角大于临界角，光就会发生全反射，被束缚在光密介质中,在这个例子中，临界角为$\theta_c = \arcsin \dfrac{1}{1.5} = 41.8^\circ$

!!!Note
    求折射率,可以通过以下公式求解
    
    \[
        n = \dfrac{\sin \theta_1}{\sin \theta_2}
    \]

    其中$\theta_1$为空气中入射角，$\theta_2$为折射角

### 色散

**色散现象**是指当白光或复色光通过介质（如棱镜、光栅）时，不同波长的光由于折射率不同而发生不同程度的偏折，从而使光被分解成各种单色光的现象。它是光的波动特性的一种表现，主要由介质的**折射率随波长的变化**引起。


\[
n = \frac{c}{v}
\]

由于 \( v \) 与波长 \( \lambda \) 相关，介质对不同波长的光折射率不同，导致折射角不同。通常情况下：

- 短波长光（如紫光）折射率较大，偏折角较大。
- 长波长光（如红光）折射率较小，偏折角较小。

这种波长依赖性导致了色散。

<div align=center>
<img src="../img/light/light3.png" width="70%">
</div>



### 惠更斯原理

!!!Summary "定理内容"
    波前上的每一个点都可以看作是新的球面波（次波）源，这些次波相干叠加后形成了波的传播方向和波前。

<div align=center>
<img src="../img/light/light4.png" width="30%">
</div>


!!!Example "惠更斯原理证明光的反射与折射"
    <div align=center>
    <img src="../img/light/light5.png" width="50%">
    </div>


    **反射**

    证明三角形全等，运用等角互余

    $$
    A_1 C_1 = A_n B_n = v_1 t_n
    $$

    $$
    \Delta A_1 C_1 B_n \cong \Delta B_n A_n A_1
    $$

    $$
    \therefore \angle A_n A_1 B_n = \angle C_1 B_n A_1
    $$

    $$
    \Rightarrow i_1' = i_1 
    $$

    **折射**

    \[
    \angle D_1B_nA_1 = i_2
    \]

    \[
    \sin i_2 = \frac{A_1D_1}{A_1B_n}
    \]

    \[
    \sin i_1 = \frac{A_nB_n}{A_1B_n}
    \]

    \[
    \therefore \frac{\sin i_1}{\sin i_2} = \frac{A_nB_n}{A_1D_1} = \frac{v_1 t}{v_2 t} = \frac{v_1}{v_2}
    \]

    再运用

    \[
        v=\dfrac{c}{n}
    \]

    带入即可


### 费马原理

光程定义为

\[
    L = n_1 s_1 + n_2 s_2
\]

其中$n_1$和$n_2$分别为两个介质的折射率，$s_1$和$s_2$分别为两个介质中光线的实际路径长度

积分形式为

\[
    L = \int n ds
\]

费马原理是指光线在传播过程中，若可以成像，则光程的变分为零(对某一个变量求偏导为零)

即

\[
    \delta \int n ds = 0
\]


!!!Example "费马原理证明反射和折射"
    <div align=center>
    <img src="../img/light/light6.png" width="50%">
    </div>

    \[
    L = \sqrt{a^2 + x^2} + \sqrt{b^2 + (d - x)^2}
    \]

    \[
    \frac{dL}{dx} = \frac{1}{2} \cdot \frac{2x}{\sqrt{a^2 + x^2}} - \frac{1}{2} \cdot \frac{2(d - x)}{\sqrt{b^2 + (d - x)^2}} = 0
    \]

    \[
    \frac{x}{\sqrt{a^2 + x^2}} = \frac{(d - x)}{\sqrt{b^2 + (d - x)^2}}
    \]

    \[
    \sin \theta_1 = \sin \theta_1' \quad \theta_1 = \theta_1'
    \]


    <div align=center>
    <img src="../img/light/light7.png" width="50%">
    </div>

    $$
    L = n_1 \sqrt{a^2 + x^2} + n_2 \sqrt{b^2 + (d - x)^2}
    $$

    $$
    \frac{dL}{dx} = \frac{1}{2} n_1 \frac{2x}{\sqrt{a^2 + x^2}} - \frac{1}{2} n_2 \frac{2(d - x)}{\sqrt{b^2 + (d - x)^2}} = 0
    $$

    $$
    n_1 \frac{x}{\sqrt{a^2 + x^2}} = n_2 \frac{(d - x)}{\sqrt{b^2 + (d - x)^2}}, \quad n_1 \sin \theta_1 = n_2 \sin \theta_2
    $$

## 成像(Image Formation)

<div align=center>
<img src="../img/light/light8.png" width="50%">
</div>

成像的基本原则是等光程

左边称为物方，右边称为像方

### 球面镜成像

C为球心;r为球半径;

<div align=center>
<img src="../img/light/light9.png" width="50%">
</div>

首先，使用正弦定理

\[
\begin{cases}
\dfrac{p}{\sin \phi} = \dfrac{o + r}{\sin \theta} = \dfrac{r}{\sin u} \\
\dfrac{p'}{\sin \phi} = \dfrac{i - r}{\sin \theta'} = \dfrac{r}{\sin u'}
\end{cases}
\]


\[
\begin{align*}
n \sin \theta &= n' \sin \theta' \\
\theta - u &= \theta' + u' = \phi
\end{align*}
\]

\[
\begin{cases}
\dfrac{p}{o + r} = \dfrac{\sin \phi}{\sin \theta} \\
\dfrac{p'}{i - r} = \dfrac{\sin \phi}{\sin \theta'}
\end{cases}
\]

\[
\therefore \frac{p}{n(o + r)} = \frac{p'}{n'(i - r)}
\]

使用余弦定理

\[
\begin{cases}
p^2 = (o + r)^2 + r^2 - 2r(o + r) \cos \phi = o^2 + 4r(o + r) \sin^2 \frac{\phi}{2} \\
p'^2 = (i - r)^2 + r^2 + 2r(i - r) \cos \phi = i^2 - 4r(i - r) \sin^2 \frac{\phi}{2}
\end{cases}
\]

\[
\cos \phi = 1 - 2 \sin^2 \frac{\phi}{2}
\]

\[
\Rightarrow \frac{o^2}{n^2(o + r)^2} - \frac{i^2}{n'^2(i - r)^2} = -4r \sin^2 \frac{\phi}{2} \left[ \frac{1}{n^2(o + r)} + \frac{1}{n'^2(i - r)} \right]
\]


不同的$\phi$对应不同的成像位置,球面不能成像；

唯一可能的位置为两边为0；


\[
\begin{cases}
\dfrac{o^2}{n^2(o + r)^2} - \dfrac{i^2}{n'^2(i - r)^2} = 0 \\
\dfrac{1}{n^2(o + r)} + \dfrac{1}{n'^2(i - r)} = 0
\end{cases}
\]


或者使用旁轴近似,即$\phi$很小,右边为0；

\[
\frac{o^2}{n^2(o + r)^2} = \frac{i^2}{n'^2(i - r)^2}
\]

\[
\frac{n(o + r)}{o} = \frac{n'(i - r)}{i}
\]

{==

\[
\frac{n'}{i} + \frac{n}{o} = \frac{n' - n}{r}
\]

==}


又有

\[
\begin{cases}
i \to \infty, \quad o = f = \dfrac{n}{n' - n} r \\
o \to \infty, \quad i = f' = \dfrac{n'}{n' - n} r
\end{cases}
\]


\[
\dfrac{f}{f'} = \dfrac{n}{n'}, \quad \dfrac{f}{o} + \dfrac{f'}{i} = 1
\]

!!!Note "符号的约定"
    - $o$,实为+，虚为-(Q，在左为+，右为-)
    - $i$,实为+，虚为-(Q'，在左为-，右为+)
    - $r$,凸为+，凹为-(C,在左为-，右为+)
    
    <div align=center>
    <img src="../img/light/light10.png" width="50%">
    </div>

    <div align=center>
    <img src="../img/light/light11.png" width="50%">
    </div>


### 球面镜反射

<div align=center>
<img src="../img/light/light12.png" width="50%">
</div>


\[
n \sin \theta = n' \sin \theta' \quad \text{if } \theta > 0, \text{ then } \theta' < 0
\]


\[
n = -n'
\]


\[
f = \frac{n}{n' - n} r = -\frac{r}{2}
\]

\[
f' = \frac{n'}{n' - n} r = \frac{1}{2} r
\]


带入折射公式

\[
\Rightarrow \frac{1}{o} + \frac{1}{i} = -\frac{2}{r}
\]

如果是平面镜，那么$r \to \infty$，成虚像；

### 放大倍数(TODO)
<div align=center>
<img src="../img/light/light13.png" width="50%">
</div>

### 薄透镜成像(TODO)

