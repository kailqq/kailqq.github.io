# 电动力学

## 法拉第电磁感应定律

\[
    \Phi = \int_S \boldsymbol{B} \cdot d\boldsymbol{S}
\]

\[
    \varepsilon = -\frac{d\Phi}{dt}
\]

!!!Key-Point
    楞次定律已经蕴含在"-"号中,楞次定律是能量守恒定律在电磁感应中的体现


## 动生电动势

电荷受到的非静电力

\[
    \boldsymbol{f} = q(\boldsymbol{v} \times \boldsymbol{B})
\]

实际上这个是洛伦兹力的分量

!!!Proof
    <div align=center>
        <img src="https://raw.githubusercontent.com/kailqq/cdn_img/master/img/202411062107903.png" width="50%">
    </div>
    克服洛伦兹力的分量做功转化为非静电力做功,洛伦兹力总的不做功
     
    \[
        V=v+v_d \enspace F=N+f
    \]

    \[
        F=qVB
    \]

    \[
        dW_N=N (vdt)=F\sin\theta vdt=Fvdt\dfrac{v_d}{V}=F\dfrac{v}{V}(v_d dt)=F\cos\theta v_d dt=fv_d dt=dW_f
    \]


!!!Key-Point "动生电动势"


    \[
        \varepsilon =\oint \boldsymbol{E} \cdot d\boldsymbol{l}=\oint \dfrac{\boldsymbol{f}}{q}d\boldsymbol{l}= \oint (\boldsymbol{v} \times \boldsymbol{B}) \cdot d\boldsymbol{l}
    \]


发电机

<div align=center>
    <img src="https://raw.githubusercontent.com/kailqq/cdn_img/master/img/202411062102050.png" width="50%">
</div>

\[
    \Phi = \boldsymbol{B} \cdot \boldsymbol{S} =BS\cos\theta=BA\cos\omega t
\]

\[
    \varepsilon = -\dfrac{d\Phi}{dt} = BA\omega\sin\omega t
\]

## 感生电动势

涡旋电流

\[
    \varepsilon = \oint \boldsymbol{E} \cdot d\boldsymbol{l}
\]

!!!Proof
    做功相等

    \[
        \varepsilon q_0=q_0 E_{induce} l
    \]

    \[
        \varepsilon = E_{induce} l
    \]

    \[
        \varepsilon = \oint \boldsymbol{E} \cdot d\boldsymbol{l}
    \]

    这提供了一种求出感生电场的方法

    !!!Example
        <div align=center>
        <img src="https://raw.githubusercontent.com/kailqq/cdn_img/master/img/202411062107903.png" width="50%">
        </div>
        
        磁场静止，动生电动势$\varepsilon=BDv$

        磁场运动，感生电动势

        \[
            \varepsilon=\oint E dl=ED=BDv
        \]

        \[
            E=v \times B
        \]

变化的磁场

\[
    \varepsilon = -\frac{d\Phi}{dt}=-A \frac{dB}{dt}
\]


!!!info "推广电场环路定律"
    \[
        \oint (\boldsymbol{E_{sta}+E_{ind}}) \cdot d\boldsymbol{l} =0+( -\frac{d\Phi}{dt})
    \]

    \[
        \Phi = \iint \boldsymbol{B} \cdot d\boldsymbol{S}
    \]

    \[
        \oint \boldsymbol{E} \cdot d\boldsymbol{l} = -\frac{d\Phi}{dt}= - \iint \frac{\partial \boldsymbol{B}}{\partial t} \cdot d\boldsymbol{S}
    \]

    运用stokes公式

    \[
      \nabla \times \boldsymbol{E} = -\frac{\partial \boldsymbol{B}}{\partial t}
    \]


!!!danger
    在涡旋电场中，环路积分并不是0，所以在涡旋电场中不能使用电势的概念


## 电感与材料的磁性质