# 磁学部分

## Ampere's Law

对于电学，我们有库仑定律

\[
    d \boldsymbol{F} = \frac{1}{4 \pi \epsilon_0} \frac{dq_1 dq_2}{r^2}
\]

!!!definition "Ampere's Law"      
    \[
    dF_{12} = \frac{\mu_0}{4 \pi} \frac{i_2 ds_2 \times (i_1ds_1 \times r_{12})}{r_{12}^2}
    \]

    其中，$\mu_0$ 是真空磁导率，$i_1, i_2$ 是电流，$ds_1, ds_2$ 是电流元长度，$r_{12}$ 是电流元之间的距离。


!!!idea "Newton's Third Law"
    Case 1: 两电流元平行
    <div align="center">
        <img src="https://raw.githubusercontent.com/kailqq/cdn_img/master/img/202410232204374.png" width="30%"/>
    </div>

    \[
        F_{12} = \frac{\mu_0}{4 \pi} \frac{i_2 ds_2 \times (i_1ds_1 \times r_{12})}{r_{12}^2}
    \]

    \[
        F_{21} = \frac{\mu_0}{4 \pi} \frac{i_1 ds_1 \times (i_2ds_2 \times r_{21})}{r_{21}^2}
    \]
     
    \[
        F_{12} = -F_{21}
    \]

    Case 2: 两电流元垂直
    <div align="center">
        <img src="https://raw.githubusercontent.com/kailqq/cdn_img/master/img/202410232204374.png" width="30%"/>
    </div>

    \[
        F_{12} = 0
    \]
    
    \[
        F_{21} = \frac{\mu_0}{4 \pi} \frac{i_1 ds_1 \times (i_2ds_2 \times r_{21})}{r_{21}^2} \neq 0
    \]

    ???info "Why?"
        这只是一小段的电流元，当考虑一整段电流时，得到的结果并不违背牛顿第三定律，当年安培就是利用相互垂直时的这一特性，巧妙的设计了实验来证明了安培定律。



## Biot-Savart Law

<div align="center">
    <img src="https://raw.githubusercontent.com/kailqq/cdn_img/master/img/202410232218692.png" width="30%"/>
</div>

继续根据电场中的思想，引入试探电流源并定义 **磁感应强度**

如果固定一个电流元，积分另一电流元，我们有

\[ 
    d\boldsymbol{F}_2 = i_2 d\boldsymbol{s}_2 \times \frac{\mu_0}{4\pi} \int_{L_1} \frac{i_1 d\boldsymbol{s}_1 \times \hat{r}_{12}}{r_{12}^2} 
\]

定义：

\[ 
    \boldsymbol{B}_1 = \frac{\mu_0}{4\pi} \int_{L_1} \frac{i_1 d\boldsymbol{s}_1 \times \hat{r}_{12}}{r_{12}^2} 
\]

因此：

\[ 
    d\boldsymbol{F}_2 = i_2 d\boldsymbol{s}_2 \times \boldsymbol{B}_1 
\]

!!!Definition "磁感应强度"
    \[
        \boldsymbol{B} = \frac{\mu_0}{4\pi} \int_{L} \frac{i d\boldsymbol{s} \times \hat{r}}{r^2}
    \]

    单位为 $T$，特斯拉。

    ???info "为什么不是磁场强度？"
        如果要完全跟电场对应，应该使用磁场强度，但是却叫磁感应强度，这是因为大家都这么叫:point_up_2:
        

###  长直导线周围的电场

<div align="center">
    <img src="https://raw.githubusercontent.com/kailqq/cdn_img/master/img/202410232229307.png" width="30%"/>
</div>

\begin{align*}
    d\boldsymbol{B} &= \frac{\mu_0}{4\pi} \frac{i d\boldsymbol{s} \times \hat{r}}{r^2} \\
    d B &= \frac{\mu_0}{4\pi} \frac{i ds \sin \theta}{r^2}\\
    B &= \frac{\mu_0}{4\pi} \int_{A_1}^{A_2} \frac{i ds \sin \theta}{r^2}\\
    r &= \frac{r_0}{\sin \theta}\\
    s &= r_0 \cot (\pi - \theta) = -r_0 \cot \theta\\
    ds &= r_0 \csc^2 \theta d\theta= r_0 \frac{d \theta}{\sin^2 \theta} \\
    B &= \frac{\mu_0 i}{4\pi r_0} \int_{\theta_1}^{\theta_2} \sin \theta d\theta\\
      &= \frac{\mu_0 i}{4\pi r_0} (\cos \theta_1 - \cos \theta_2)
\end{align*}

如果是无限长，则

\[
    B = \frac{\mu_0 i}{2\pi r_0}
\]


也就是说，无限长直导线周围的磁感应强度与距离成反比。

!!!Note 
    回忆电场中的无限长直导线，其电场强度与距离成反比。
    
    \[
        E = \frac{\lambda}{2\pi \epsilon_0 r}
    \]


### 圆电流轴线上的磁场

<div align="center">
    <img src="https://raw.githubusercontent.com/kailqq/cdn_img/master/img/202410232305141.png" width="30%"/>
</div>


<div align="center">
    <img src="https://raw.githubusercontent.com/kailqq/cdn_img/master/img/202410232255157.png" width="30%"/>
</div>

其中由于对称性在与圆环平行的方向上，磁感应强度为零。

\[
    dB = \frac{\mu_0}{4\pi} \frac{i ds \sin \theta}{r^2} = \frac{\mu_0}{4\pi} \frac{i ds}{r^2}(\theta = \frac{\pi}{2})
\]

\[
    dB_x= dB \cos \alpha= \frac{\mu_0}{4 \pi} \frac{i ds}{r^2} \cos \alpha
\]

\[
    r=\frac{r_0}{\sin \alpha}
\]

\[
    B= \frac{\mu_0 i}{4\pi r_0^2} \int_{s} \sin^2 \alpha \cos \alpha ds =\frac{\mu_0 i}{4\pi r_0} \sin^2 \alpha \cos \alpha 2 \pi R
\]

\[
    \sin \alpha = \frac{r_0}{\sqrt{r_0^2 + R^2}} \enspace \cos \alpha = \frac{R}{\sqrt{r_0^2 + R^2}}
\]

\[
    B = \frac{\mu_0}{2} \frac{iR^2}{(r_0^2 + R^2)^{3/2}}
\]

!!!Note
    当 $r_0 \to 0$ 时，$B \to \frac{\mu_0 i}{2R}$

    当 $r_0 \to \infty$ 时，$B \to \frac{\mu_0 i}{2r_0^3}R^2$ 与 $r_0^3$ 成反比。在磁场中，电偶极矩在无穷远处产生的电场也与 $r^3$ 成反比。

定义磁偶极矩

\[
    \boldsymbol{m} = i \pi R^2
\]

则

\[
    B =  \frac{\mu_0 i}{2r_0^3}R^2 = \frac{\mu_0 m}{2 \pi r_0^3}
\]

如果有N匝线圈，则

\[
    B =  \frac{\mu_0 N i}{2r_0^3}R^2 = \frac{\mu_0 N m}{2 \pi r_0^3}
\]

或者令 $m' = N i \pi R^2$,

\[
    B = \frac{\mu_0 m'}{2 \pi r_0^3}
\]
    

### 电流平面产生的磁场

<div align="center">
    <img src ="https://raw.githubusercontent.com/kailqq/cdn_img/master/img/202410241258154.png" width="30%"/>
</div>

由于对称性，在只会在$x$方向上产生磁场

\[ 
dB = \frac{\mu_0 di}{2\pi d} = \frac{\mu_0 \frac{i}{a} dx}{2\pi d} 
\]

\[ 
dB_x = dB \cdot \cos \theta 
\]

\[ 
d = \frac{R}{\cos \theta} 
\]

\[ 
B_x = \int dB_x = \int \frac{\mu_0 i \cos^2 \theta dx}{2\pi Ra} = \frac{\mu_0 i}{2\pi aR} \int \cos^2 \theta dx 
\]

\[ 
x = R \tan \theta, \quad dx = \frac{R \, d\theta}{\cos^2 \theta} 
\]

\[ 
B_x = \frac{\mu_0 i}{2\pi aR} \int \cos^2 \theta dx = \frac{\mu_0 i}{2\pi a} \int_{-\alpha}^{\alpha} d\theta = \frac{\mu_0 i}{\pi a} \alpha = \frac{\mu_0 i}{\pi a} \tan^{-1} \frac{a}{2R} 
\]

!!!Note 
    当 $a \to 0,\alpha \to \tan\alpha =  \dfrac{a}{2R} $ 时，$B_x \to \dfrac{\mu_0 i}{2\pi R}$

    当 $a \to \infty, \alpha \to \dfrac{\pi}{2}$ 时, $B_x \to \dfrac{\mu_0 i}{2 a}$


### 单层通电螺旋管产生的磁场

在通电螺旋管内部，会产生匀强磁场

<div align="center">
    <img src="https://raw.githubusercontent.com/kailqq/cdn_img/master/img/202410241320154.png" width="30%"/>
</div>


设$x$为点P据中心轴线的水平距离；螺线管长度为$L$,单位长度匝数为$n$，每匝电流为$i$。

根据磁偶极矩产生的磁场公式

\[
    dB = \dfrac{\mu_0 m}{2\pi r^3}=\dfrac{\mu_0 n i dl \pi R^2}{2\pi (\sqrt{R^2+(x-l)^2})^3}
\]

\[
   r=\dfrac{R}{\sin \beta} \quad \dfrac{x-l}{R} =\cot \beta \quad dl = \dfrac{R d\beta}{\sin^2 \beta}
\]

\[
    B =\frac{\mu_0}{2} n i \int_{\beta_1}^{\beta_2} \sin \beta d\beta = \frac{\mu_0}{2} n i (\cos \beta_1 - \cos \beta_2)  
\]

!!!Note
    $L \to \infty$ 时，$B = \mu_0 n i$


### 多层通电螺线管产生的磁场

<div align="center">
    <img src="https://raw.githubusercontent.com/kailqq/cdn_img/master/img/202410242125937.png" width="30%"/>
</div>


从下往上，逐层积分

\[
    dB=\frac{\mu_0}{2} n i (\cos \beta_1 - \cos \beta_2)  
\]

$ni$ 为每一层单位长度的电流，

\[
    ni = \frac{N'i}{L} =\frac{jLdr}{L}=jdr=\frac{Ni}{L(R_2-R_1)}dr
\]

其中$N'$为每一层的匝数，$j$电流密度，$R_1,R_2$为内外半径，$N$为总匝数。

\[
    \cos \beta_1 - \cos \beta_2 =2\cos \beta_1 =\dfrac{2l}{\sqrt{l^2+r^2}}
\]

\[
    dB=\frac{\mu_0}{2} jdr \frac{2l}{\sqrt{l^2+r^2}} \quad B =\mu_0 j l \int_{R_1}^{R_2} \frac{dr}{\sqrt{r^2+l^2}}
\]

\[
    B = \mu_0 j l \ln \dfrac{R_2+\sqrt{R_2^2+l^2}}{R_1+\sqrt{R_1^2+l^2}}
\]

???Note "详细过程"
    毁了啊，secx的原函数都记不住:cry:

    <div align="center">
        <img src="https://raw.githubusercontent.com/kailqq/cdn_img/master/img/202410242152695.png" width="70%"/>
    </div>