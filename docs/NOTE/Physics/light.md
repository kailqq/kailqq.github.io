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

### 放大倍数
<div align=center>
<img src="../img/light/light13.png" width="50%">
</div>

首先，由旁轴近似

\[
    n \sin \theta = n' \sin \theta' \Rightarrow  n \theta = n' \theta'
\]

$y'<0$

\[
y \approx o \cdot \theta, \, -y' = i \cdot \theta'
\]

\[
\therefore m = \frac{y'}{y} = -\frac{i\theta'}{o\theta} = -\frac{n \cdot i}{n' \cdot o}
\]

如果$n=n'$，则$m=-\dfrac{i}{o}$ 负号表示倒像



### 薄透镜成像

<div align=center>
<img src="../img/light/light24.png" width="50%">
</div>

首先，对于$n$和$n_L$,$n_L$和$n'$，分别使用球面镜成像公式

\[
\begin{cases} 
\frac{f_1'}{i_1} + \frac{f_1}{o_1} = 1 \tag{1} \\ 
\frac{f_2'}{i_2} + \frac{f_2}{o_2} = 1 \tag{2}
\end{cases}
\]

其中

\[
\begin{aligned}
f_1 &= \frac{n}{n_L - n} r_1, \quad f_1' = \frac{n_L}{n_L - n} r_1 \\
f_2 &= \frac{n_L}{n' - n_L} r_2, \quad f_2' = \frac{n'}{n' - n_L} r_2
\end{aligned}
\]

$o_2$是Q经过第一个球面镜的虚像像距,所以

\[
-o_2 = i_1 - d, \quad o_2 = d - i_1
\]

对于(1)式两边同时乘以$f_2$，对于(2)式两边同时乘以$f_1'$

\[
\begin{cases} 
\frac{f_1' f_2}{i_1} + \frac{f_1 f_2}{o_1} = f_2 \\ 
\frac{f_1' f_2'}{i_2} + \frac{f_1' f_2}{-i_1} = f_1'
\end{cases}
\]

相加

\[
\frac{f_1' f_2'}{i_2} + \frac{f_1 f_2}{o_1} = f_1' + f_2
\]

\[
\frac{f_1' f_2'}{i} + \frac{f_1 f_2}{o} = f_1' + f_2
\]

除过去,得到


\[
\frac{f'}{i} + \frac{f}{o} = 1
\]

其中，令

\[
    f' = \frac{f_1' f_2'}{f_1' + f_2}
\]

\[
    f = \frac{f_1 f_2}{f_1 + f_2}
\]

####  磨镜者公式(Lens Maker's Equation)

\[
f' = \frac{f_1' f_2'}{f_1' + f_2} = \frac{\frac{n_L}{n_L - n} \cdot \frac{n'}{n' - n_L} r_1 r_2}{\frac{n_L}{n_L - n} r_1 + \frac{n'}{n' - n_L} r_2} = \frac{n'}{\frac{n_L - n}{r_1} + \frac{n' - n_L}{r_2}}
\]

\[
f = \frac{f_1 f_2}{f_1 + f_2} = \frac{\frac{n}{n_L - n} \cdot \frac{n_L}{n' - n_L} r_1 r_2}{\frac{n}{n_L - n} r_1 + \frac{n_L}{n' - n_L} r_2} = \frac{n}{\frac{n_L - n}{r_1} + \frac{n' - n_L}{r_2}}
\]



所以

\[
    \dfrac{f'}{f} = \dfrac{n'}{n}
\]

如果$n=n'=1$，则$f' = f$

\[
f = f' = \frac{1}{(n_L - 1) \left( \frac{1}{r_1} - \frac{1}{r_2} \right)}
\]


如果$f'和f$都为正，则透镜为凸透镜，反之$f，f'$为负，则透镜为凹透镜

#### 符号约定

<div align=center>
<img src="../img/light/light25.png" width="70%">
</div>

- 如果 $Q$ 在 $F$ 点的左侧，$x > 0$
- 如果 $Q$ 在 $F$ 点的右侧，$x < 0$
- 如果 $Q'$ 在 $F'$ 点的左侧，$x' < 0$
- 如果 $Q'$ 在 $F'$ 点的右侧，$x' > 0$

\[
o = f + x
\]

\[
i = f' + x'
\]

\[
\frac{1}{f + x} + \frac{1}{f' + x'} = \frac{1}{f}
\]

可以化简为

\[
xx' = ff'
\]

#### 横向放大倍数与屈光度

<div align=center>
<img src="../img/light/light13.png" width="70%">
</div>


对于单个镜面，放大倍数为

\[
m_1 = -\dfrac{ni_1}{n_L o_1}, \quad m_2 = -\dfrac{n i_2}{n' o_2}
\]

其中$o_2$是Q经过第一个球面镜的虚像像距,是负的；

\[
m = m_1 m_2 = \dfrac{n i_1}{n_L o_1} \cdot \dfrac{n_L i_2}{n' o_2} = \dfrac{n i_1}{n_L o_1} \cdot \dfrac{n_L i}{n' (-i_1)} = -\dfrac{n i}{n' o} = -\dfrac{fi}{f' o}
\]

定义屈光度

\[
D = \dfrac{1}{f}
\]



### 人眼成像

人眼最近可以看清的距离为25cm，最远可以看清的距离为无穷远；

<div align=center>
<img src="../img/light/light26.png" width="70%">
</div>

\[
\frac{1}{250 \, \text{mm}} + \frac{1}{25 \, \text{mm}} = \frac{1}{f}
\]

此时$f = 22.7mm$

看无穷远时,$d_o = \infty, d_i = 25mm$,此时$f = 25mm$

!!!idea "近视眼和远视眼可以抵消吗？"
    近视眼和远视眼不能抵消，近视眼是看不清无穷远，成像在视网膜前方，远视眼是看不清25cm，成像在视网膜后方；两者都是因为人的晶状体变化跟不上，如果同时有近视眼和远视眼，可能只能看到特定距离的物体；


#### 放大镜

对于很小的物体，我们可以把它凑得离眼睛很近，但是这样对晶状体的压力很大，所以我们使用放大镜，凑得很近的时候，利用放大镜成一个放大的虚像

例如，原本在$N$的地方有一个小物体，高度为$d_0$

<div align=center>
<img src="../img/light/light27.png" width="60%">
</div>

\[
    \tan \theta = \frac{d_0}{N} \sim \theta = \frac{d_0}{N}
\]


利用放大镜

<div align=center>
<img src="../img/light/light28.png" width="60%">
</div>

\[
\text{Compare to unaided eye:} \quad \theta = \frac{h_0}{N}, \quad \theta' = \frac{h_i}{d_i} = \frac{h_o}{d_o}
\]

放大倍数

\[
M = \frac{\theta'}{\theta} = \frac{h_o/d_o}{h_o/N} = \frac{N}{d_o}
\]


对于该放大镜

\[
\frac{1}{d_o} + \frac{1}{d_i} = \frac{1}{f} \quad \Rightarrow \quad \frac{1}{d_o} = \frac{1}{f} - \frac{1}{d_i}
\]

我们要把像成在N处，$d_i$是虚像，所以$-d_i = N$

也就是说

\[
\frac{1}{d_o} = \frac{1}{f} + \frac{1}{N}
\]

得到放大倍数为

\[
M = \frac{N}{d_o} = N(\frac{1}{f} + \frac{1}{N}) = \frac{N}{f}+1
\]




## 波动光学

### 光的干涉(Interference)

#### 光的叠加

电场强度 $E$ 的振动在空间的传播可以表示为：

\[
E = E_0 \cos(\omega t + \varphi_1 - 2\pi \frac{x}{\lambda})
\]

对于两列光波的叠加：

- $\omega_1 = \omega_2 = \omega$
- $E_1 = E_{10} \cos(\omega t + \varphi_{10})$
- $E_2 = E_{20} \cos(\omega t + \varphi_{20})$

叠加电场：

\[
E = E_1 + E_2
\]

<div align=center>
<img src="../img/light/light14.png" width="70%">
</div>
<div align=center>
<img src="../img/light/light15.png" width="70%">
</div>

- 同相位：$\Delta \varphi = 0$,相干，in phase
- 反相位：$\Delta 


!!!Note "复平面矢量推导"
    对于两列光波的叠加：

    - $\omega_1 = \omega_2 = \omega$
    - $E_1 = E_{10} \cos(\omega t + \varphi_{10})$
    - $E_2 = E_{20} \cos(\omega t + \varphi_{20})$

    叠加电场：

    \[
    E = E_1 + E_2 = E_0 \cos(\omega t + \varphi_0)
    \]

    光强：

    \[
    I_0 = E_0^2 = E_{10}^2 + E_{20}^2 + 2E_{10}E_{20}\cos\Delta\varphi
    \]

    其中，$\Delta\varphi = \varphi_{20} - \varphi_{10}$

    <div align=center>
    <img src="../img/light/light16.png" width="60%"/>
    </div>


!!!info "干涉的光强分布"
    干涉现象的光强分布可以表示为：

    \[
    I = I_1 + I_2 + 2\sqrt{I_1 I_2} \cos \Delta \varphi
    \]

    其中，$I_1$ 和 $I_2$ 是两列光波的强度，$\Delta \varphi$ 是相位差。

    当 $I_1 = I_2$ 时，光强分布为：

    \[
    I = 4I_1 \cos^2 \frac{\Delta \varphi}{2}
    \]

    这表明光强的最大值为 $I_{\text{max}} = 4I_1$，最小值为 $I_{\text{min}} = 0$。

    <div align=center>
    <img src="../img/light/light17.png" width="60%"/>
        </div>

#### 媒质中的光程

相位差在分析光的干涉时十分重要，为便于计算光通过不同媒质时的相位差，引入“光程差”的概念。(光程是 $\int n ds$)

\[
    \Delta \varphi = \dfrac{2\pi}{\lambda} \Delta L
\]

如果在介质中

\[
\lambda_n = \dfrac{v}{f} = \dfrac{c/n}{f} = \dfrac{c/f}{n} = \dfrac{\lambda_0}{n}
\]

此时

\[
     \Delta \varphi = \dfrac{2\pi}{\lambda} n \Delta  L
\]


!!!Summary "结论"
    - 相干条件：振动方向相同，相位差恒定,频率相同

    干涉判断：

    \[
    \Delta \varphi = 
    \begin{cases} 
    \pm 2k\pi, & k = 0,1,2,\ldots \quad (\text{干涉加强}) \\
    \pm (2k + 1)\pi, & k = 0,1,2,\ldots \quad (\text{干涉减弱})
    \end{cases}
    \]

    \[
    \delta = 
    \begin{cases} 
    \pm k\lambda_0, & k = 0,1,2,\ldots \quad (\text{干涉加强}) \\
    \pm \left(2k + 1\right)\dfrac{\lambda_0}{2}, & k = 0,1,2,\ldots \quad (\text{干涉减弱})
    \end{cases}
    \]

#### 杨氏双缝干涉实验

<div align=center>
    <img src="../img/light/light18.png" width="60%"/>
</div>

<div align=center>
    <img src="../img/light/light19.png" width="60%"/>
</div>


- 干涉相长，明纹：$\delta = d \cdot \frac{x}{D} = \pm k\lambda$
- 干涉相消，暗纹：$\delta = d \cdot \frac{x}{D} = \pm (2k - 1)\frac{\lambda}{2}$
- 暗纹中心：$x_{\pm(2k+1)} = \pm (2k - 1)\frac{D}{2d}\lambda, \, k = 1,2,3\ldots$
- 明纹中心：$x_{\pm k} = \pm k\frac{D}{d}\lambda, \, k = 0,1,2,3\ldots$
- 两相邻明纹（或暗纹）间距：$\Delta x = \frac{D}{d}\lambda$

???question
    - 若S1、S2两条缝的宽度不等，条纹有何变化？ 
    两条缝的宽度不等，使两光束的强度不等；虽然干涉条纹中心距不变，但原极小处的强度不再为零，条纹的可见度变差。

    - 若使用白光进行干涉实验，条纹有何变化？
    若使用白光光源，则在中央零级出现白色亮纹，两侧对称排列若干彩色条纹。

    - 用白光 作双缝干涉实验时，能观察 到几级清晰可辨的彩色光谱？
    在中央白色明纹两侧， 只有第一级彩色光谱是清晰可辨的。


#### 洛埃德镜实验

<div align=center>
    <img src="../img/light/light20.png" width="60%"/>
</div>

当屏移到A'B'位置时，在屏上的P点出现暗条纹。这一结论证实，光在镜子表面反射时有相位$\pi$突变。

{==Reflection Phase Shifts==}半波损失

如果光是从光 疏媒质传向光密媒质，在其分界面上反射时将发生半波损失，折射波无半波损失。在上述实验中，光从空气传向玻璃，因此在反射时发生半波损失。产生$\pi$的相位差，因此为暗纹。



#### 等厚干涉

当一束平行光入射到厚度不均匀的透明介质薄膜上，如图所示，两光线 $a$ 和 $b$ 的光程差：

\[
\delta = 2n_2e + \delta'
\]

其中，$\delta'$ 为因为半波损失而产生的附加光程差。

- 当 $e$ 保持不变时，光程差仅与膜的厚度有关，凡厚度相同的地方光程差相同，从而对应同一条干涉条纹 —— 等厚干涉条纹。

<div align=center>
    <img src="../img/light/light21.png" width="60%"/>
</div>

**劈尖膜**

<div align=center>
    <img src="../img/light/light22.png" width="60%"/>
</div>

从空气到玻璃存在半波损失

\[
    \delta = 2ne + \frac{\lambda}{2}
\]

发生干涉时

\[
    \delta = \begin{cases}
    2ne + \frac{\lambda}{2} = k\lambda, & \text{明纹} \\
    2ne + \frac{\lambda}{2} = (2k - 1)\frac{\lambda}{2}, & \text{暗纹}
    \end{cases}
\]

相邻明纹（或暗纹）间距

\[
    \Delta e = \frac{\lambda}{2n}
\]

???Example "利用劈尖测量工件凹凸"
    <div align=center>
        <img src="../img/light/light23.png" width="60%"/>
    </div>
    如果工件表面是精确的平面,等厚干涉条纹应该是等距离的平行直条纹，现在观察到的干涉条纹弯向空气膜的左端。因此，可判断工件表面是下凹的

    利用相似三角形关系，我们可以得到：

    \[
    \frac{a}{b} = \frac{\Delta h}{(e_k - e_{k-1})} = \frac{\Delta h}{\frac{\lambda}{2}}
    \]

    所以：

    \[
    \Delta h = \frac{a \lambda}{b \cdot 2}
    \]

    

### 光的衍射(Diffraction)

### 光的偏振(Polarization)