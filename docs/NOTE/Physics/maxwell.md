# Maxwell Equation
>改变人类文明进程的伟大方程

## 对称性原则

我们首先回忆学过的方程

在真空中，我们有

- 电场高斯定理

\[
    \oiint \vec{E} \cdot \vec{dS} = \frac{Q}{\varepsilon_0}
\]

- 磁场高斯定理

\[
    \oiint \vec{B} \cdot \vec{dS} = 0
\]

- 法拉第电磁感应定律

\[
    \oint \vec{E} \cdot \vec{dl} = -\frac{d\Phi_B}{dt} = -\oiint \frac{\partial \vec{B}}{\partial t} \cdot \vec{dS}
\]

- 安培环路定理

\[
    \oint \vec{B} \cdot \vec{dl} = \mu_0 I_{enc}
\]


在电介质或者磁芯材料中，我们有

- 电场高斯定理推广

\[
    \oiint \vec{D} \cdot \vec{dS} = Q_{free}
\]

- 磁场环路定理推广
  
\[
    \oint \vec{H} \cdot \vec{dl} = I_{free} = \oiint \vec{J} \cdot \vec{dS}
\]

我们还有欧姆定律微分形式

\[
    \vec{J} = \sigma \vec{E}
\]


{==对称性原则==}：物理学家们希望方程是对称美观的，观察电场和磁场的高斯定律，于是自然不想看到磁场高斯定律的等号右边空空如也，也希望电场环路定律出现电流的形式，所以引入了磁荷$q_m$对方程进行修正

\[
    \begin{cases}
    \oiint \vec{B} \cdot \vec{dS} = q_m \\
    \oint \vec{E} \cdot \vec{dl} = \dfrac{dq_m}{dt}= -\oiint \dfrac{\partial \vec{B}}{\partial t} \cdot \vec{dS}
    \end{cases} 
\]


## Stokez公式与麦克斯韦方程
> 我宣佈現在我也是麥克斯韋了

<div align=center>
    <img src="../img/looplaw.png" width="50%">
</div>

使用电场的环路定理，再用斯托克斯公式变成面积分

\[
\oint \mathbf{H} \cdot d\mathbf{l} = i_0 = \iint_{S_2} \mathbf{J}_0 \cdot d\mathbf{A}
\]

\[
-\iint_{S_1} \mathbf{J}_0 \cdot d\mathbf{A} = \iint_{S_2} \mathbf{J}_0 \cdot d\mathbf{A} = i_0
\]

\[
\iint_{S} \mathbf{J}_0 \cdot d\mathbf{A} = \iint_{S_1} \mathbf{J}_0 \cdot d\mathbf{A} + \iint_{S_2} \mathbf{J}_0 \cdot d\mathbf{A} = 0
\]

这启发我们，以一个封闭的曲面包裹着电流，其面积分为0；

但是这样的结论在给电容器充电时出现了诡异的情况

<div align=center>
    <img src="../img/chargec.png" width="50%">
</div>

对于(1,2)曲面，面积分为0，(1,4)曲面，面积分为0，但是(1,3)曲面，面积分不为0，此时电流从1面进入，但是没有从3面出去；这太不自然了

所以我们自然引入位移电流$I_D$

\[
   \oint \vec{H} \cdot \vec{dl} = I_{free} + I_D
\]

但是$I_D$是什么呢？我们可以从面积分的形式出发

考虑(1,3)曲面$S$，只进不出

\[
    \oiint_S \vec{J} \cdot \vec{dS} = -\dfrac{dq}{dt}
\]

\[
    \oiint_S \vec{D} \cdot \vec{dS} = q
\]

\[
    \oiint_s \dfrac{\partial \vec{D}}{\partial t} \cdot \vec{dS} = \dfrac{dq}{dt}
\]

所以在(1,3)曲面上，我们有

\[
    \oiint_S \left( \vec{J} + \dfrac{\partial \vec{D}}{\partial t} \right) \cdot \vec{dS} = 0
\]

此时在1曲面进的等于3曲面出的

\[
    - \oiint_{S_1} \vec{J} \cdot \vec{dS} = \oiint_{S_3} \vec{J} \cdot \vec{dS} 
\]

!!!key-point "位移电流"
    1曲面没有位移电流，3曲面没有自由电流，位移电流$I_D=I_0$

最后，更加完整的定义为


$$
\Phi_D = \iint \mathbf{D} \cdot d\mathbf{A} \quad \text{electric displacement flux}
$$

$$
i_D = \frac{d\Phi_D}{dt} = \iint \frac{\partial \mathbf{D}}{\partial t} \cdot d\mathbf{A} \quad \text{displacement current}
$$

$$
\mathbf{j}_D = \frac{\partial \mathbf{D}}{\partial t} \quad \text{displacement current density}
$$

分别是电位移通量，位移电流，位移电流密度

!!!proof "i_D=i_0"
    $$
    E = \frac{\sigma_e}{\epsilon_0} = \frac{q}{\epsilon_0 A} \quad \therefore \quad q = \epsilon_0 A E = \epsilon_0 \Phi_E = AD
    $$

    $$
    \therefore \quad i_0 = \frac{dq}{dt} = \epsilon_0 \frac{d\Phi_E}{dt} = \frac{d\Phi_D}{dt} = i_D, \quad \mathbf{D} = \epsilon_0 \mathbf{E}
    $$


电容充满电之后$i_D=i_0=0$;

这个电流也会产生磁场


![](./img/maxwell1.png){ align=left } 

![](./img/maxwell2.png){ align=right }


\[
\oint \vec{H} \cdot d\vec{l} = \int \int \frac{\partial \vec{D}}{\partial t} \cdot d\vec{A}  \enspace  (I_D)
\]

\[
\oint \frac{\vec{B}}{\mu_0} \cdot d\vec{l} = \epsilon_0 \int \int \frac{\partial \vec{E}}{\partial t} \cdot dA
\]

\[
\oint \vec{B} \cdot d\vec{l} = \mu_0 \epsilon_0 \int \int \frac{\partial \vec{E}}{\partial t} \cdot dA
\]

变化的电场产生磁场，变化的磁场产生电场，这就是麦克斯韦方程

最后，我们得到

\[
    \oint \vec{H} \cdot \vec{dl} = \iint \vec{J} \cdot \vec{dS} + \iint \frac{\partial \vec{D}}{\partial t} \cdot \vec{dS}
\]

以及

\[
    \nabla \times \vec{H} = \vec{J} + \frac{\partial \vec{D}}{\partial t}
\]


