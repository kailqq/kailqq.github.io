---
comments: true
---

# 数字特征

## 数学期望

!!!Definition "数学期望的定义"
    设$X$是一个离散型随机变量，$X$的数学期望（或称为期望值）是$X$所有可能取值的加权平均，记为$E(X)$或$\mu$，即
    
    \[
        E(X)=\sum_{i=1}^{n}x_iP(X=x_i)
    \]
    
    其中，$x_i$是$X$的可能取值，$P(X=x_i)$是$X$取值为$x_i$的概率。

    若$X$是一个连续型随机变量，其概率密度函数为$p(x)$，则$X$的数学期望为

    \[
        E(X)=\int_{-\infty}^{+\infty}xp(x)dx
    \]

    


数学期望的意义在于，当随机变量$X$独立重复地进行大量实验时，$X$的平均值将趋于$E(X)$。

数学期望跟参数有关，有几个参数就跟几个参数有关。

!!!Property "常见分布的数学期望"
    === "二项分布"
        若$X\sim B(n,p)$，则
        
        $$E(X)=np$$
    
    === "泊松分布"
        若$X\sim P(\lambda)$，则
        
        $$E(X)=\lambda$$

    === "几何分布"
        若$X\sim G(p)$，则
        
        $$E(X)=\dfrac{1}{p}$$
    
    === "均匀分布"
        若$X\sim U(a,b)$，则
        
        $$E(X)=\dfrac{a+b}{2}$$

    === "指数分布"
        若$X\sim E(\lambda)$，则
        
        $$E(X)=\dfrac{1}{\lambda}$$

    === "正态分布"
        若$X\sim N(\mu,\sigma^2)$，则
        
        $$E(X)=\mu$$
    
    === "超几何分布"
        若$X\sim H(N,M,n)$，则
        
        $$E(X)=n\dfrac{M}{N}$$


在计算数学期望的时候需要用到级数的知识，需要考虑到函数列是否一致收敛来运用逐项求导或者求积分，级数是否绝对收敛来判断是否可以用级数的重排；

!!!Note
    为了避免同一个随机变量因为排序不同造成的数学期望不同，我们要求

    \[
        \sum_{i=1}^{\infty}x_ip_i
    \]

    是绝对收敛的($\sum_{i=1}^{\infty}\lvert x_ip_i \rvert$收敛)，即该级数的任意一个重排都收敛于同一个值。
    如果是连续型随机变量，则要求
    
    \[
        \int_{-\infty}^{+\infty}\lvert xp(x) \rvert dx
    \] 

    可积。

### 数学期望的性质

- {==有界==}: 
    
\[
    a \leqslant X \leqslant b \Rightarrow a \leqslant E(X) \leqslant b
\]

即数学期望不会超过随机变量的取值范围。

- {==线性运算==}

\[
    E(a+bY)=a+bE(Y)
\]

从求和和积分的性质可以得到。

- {==加法定理==}

由[随机变量加法的分布](http://www.kailqq.cc/NOTE/Probability/second/#_19-etaxi_1xi_2)

假设 \((X, Y) \sim p(x, y)\)，那么 \(Z = X + Y\) 具有密度

\[
p_Z(z) = \int_{-\infty}^{\infty} p(x, z - x) dx
\]

所以

\[
E(X + Y) = \int_{-\infty}^{\infty} z p_Z(z) dz
\]

\begin{align*}
E(X + Y) &= \int_{-\infty}^{\infty} z p_Z(z) dz \\
&= \int_{-\infty}^{\infty} z \int_{-\infty}^{\infty} p(x, z - x) dx dz\\
&= \int_{-\infty}^{\infty} \int_{-\infty}^{\infty} (x + y) p(x, y) dx dy\\
&= \int_{-\infty}^{\infty} \int_{-\infty}^{\infty} x p(x, y) dx dy + \int_{-\infty}^{\infty} \int_{-\infty}^{\infty} y p(x, y) dx dy\\
&= \int_{-\infty}^{\infty} x p_X(x) dx + \int_{-\infty}^{\infty} y p_Y(y) dy\\
&= E X + E Y
\end{align*}

推广：

\[
E(a_1 X_1 + a_2 X_2 + \cdots + a_m X_m) = a_1 E X_1 + a_2 E X_2 + \cdots + a_m E X_m
\]

!!!Example "应用"
    假设 \(X_1, X_2, \dots, X_m\) 是非负、独立同分布的随机变量，求

    \[
    E \frac{X_1 + \cdots + X_k}{X_1 + \cdots + X_m}
    \]


    \[
    E \frac{X_1}{X_1 + \cdots + X_m} = \cdots = E \frac{X_m}{X_1 + \cdots + X_m}
    \]

    存在，有限。另外，

    \begin{align*}
    1 &= E \frac{X_1 + \cdots + X_m}{X_1 + \cdots + X_m}\\
    &= E \frac{X_1}{X_1 + \cdots + X_m} + \cdots + E \frac{X_m}{X_1 + \cdots + X_m}\\
    &= m \cdot E \frac{X_1}{X_1 + \cdots + X_m}\\
    \end{align*}

    所以，

    \[
    E \frac{X_1}{X_1 + \cdots + X_m} = \frac{1}{m}
    \Rightarrow E \frac{X_1 + \cdots + X_k}{X_1 + \cdots + X_m} = \frac{k}{m}
    \]

    **加法定理计算期望**
    
    令 \( N \) 是产品总数，\( M \) 是次品数，现抽取 \( n \) 件产品检查，其中 \( n \leq M \)。  
    令 \( S_n \) 表示 \( n \) 件抽查产品中次品的个数。那么
    
    \[
    P(S_n = k) = \frac{\binom{M}{k} \binom{N - M}{n - k}}{\binom{N}{n}}
    \]

    下面给出 \( X \) 的另一种表示：令 \( \xi_i \) 表示第 \( i \)-次抽检时次品个数，
    
    \[
    X_i = 
    \begin{cases}
    1, & p \\
    0, & 1 - p
    \end{cases}
    \quad i = 1, 2, \dots, n，\text{同分布，但是不独立}
    \]

    那么
    
    \[
    S_n = \sum_{i=1}^n X_i 
    \]

    \[
    E S_n = \sum_{i=1}^n E X_i = n \frac{M}{N}
    \]

    !!!key-point
        $X_i$指第$i$次抽到的是不是次品，这相当于抽奖，无论抽奖顺序是什么，每个人抽到的概率都是一样的，所以$X_i$是同分布的，但是不独立。


如果随机变量$X$和$Y$独立，那么$E(XY)=E(X)E(Y)$，如果$E(XY)=E(X)E(Y)$，并不一定有$X$和$Y$独立。

###  随机变量函数的数学期望

随机变量函数的数学期望可以用以下公式来定义：

$(\Omega,\mathcal{F},P)$是一个概率空间, $X:\Omega \to \mathbf{R}$是一个随机变量，\( g(X) \) 是 \( X \) 的一个实值可测函数，那么 \( g(X) \) 的数学期望 \( E[g(X)] \) 定义为：

=== "离散型随机变量"
     期望 \( E[g(X)] \) 为：
     
    \[
     E[g(X)] = \sum_{x} g(x) P(X = x)
    \]
     
     其中 \( P(X = x) \) 是 \( X \) 取值为 \( x \) 的概率。

=== "连续型随机变量"
     期望 \( E[g(X)] \) 为：
     
    \[
     E[g(X)] = \int_{-\infty}^{\infty} g(x) f_X(x) \, dx
    \]
     
     其中 \( f_X(x) \) 是 \( X \) 的概率密度函数。

     如果$X$有分布函数，那么
     
      
    \[
     E[g(X)] = \int_{-\infty}^{\infty} g(x) f_X(x) \, dx= \int_{-\infty}^{\infty} g(x) dF_X(x)
    \]


## 方差

!!!Definition
    方差是用来衡量随机变量偏离其均值的程度的指标。设 \( X \) 是一个随机变量，其数学期望为 \( E(X) \)，则 \( X \) 的方差记作 \( \operatorname{Var}(X) \) 或 \( \sigma^2 \)，定义如下：

    \[
    \operatorname{Var}(X) = E[(X - E(X))^2]
    \]


方差定义的是随机变量 \( X \) 与其均值 \( E(X) \) 偏差的平方的期望。它反映了 \( X \) 取值的分散程度。方差越大，说明 \( X \) 的取值离均值越远，分散性越大；方差越小，说明 \( X \) 的取值集中在均值附近，分散性较小。

$\sqrt{\operatorname{Var}(X)}$ 称为随机变量 \( X \) 的标准差，记作$\sigma$




!!!property "常见分布的方差"
    === "二项分布"
        若$X\sim B(n,p)$，则
        
        $$\operatorname{Var}(X)=np(1-p)$$
    
    === "泊松分布"
        若$X\sim P(\lambda)$，则
        
        $$\operatorname{Var}(X)=\lambda$$

        对于泊松分布，方差等于数学期望，这是泊松分布的一个特性。

    === "几何分布"
        若$X\sim G(p)$，则
        
        $$\operatorname{Var}(X)=\dfrac{1-p}{p^2}$$
    
    === "均匀分布"
        若$X\sim U(a,b)$，则
        
        $$\operatorname{Var}(X)=\dfrac{(b-a)^2}{12}$$

    === "指数分布"
        若$X\sim E(\lambda)$，则
        
        $$\operatorname{Var}(X)=\dfrac{1}{\lambda^2}$$

    === "正态分布"
        若$X\sim N(\mu,\sigma^2)$，则
        
        $$\operatorname{Var}(X)=\sigma^2$$
    
    === "超几何分布"
        若$X\sim H(N,M,n)$，则
        
        $$\operatorname{Var}(X)=n\dfrac{M}{N}\dfrac{N-M}{N}\dfrac{N-n}{N-1}$$


### 计算公式
可以通过以下公式计算方差：

\[
\operatorname{Var}(X) = E(X^2) - [E(X)]^2
\]

!!!proof
    方差的定义是：
    
    \[
    \operatorname{Var}(X) = E[(X - E(X))^2]
    \]
    
    展开括号，得到：
    
    \[
    \operatorname{Var}(X) = E[X^2 - 2X \cdot E(X) + (E(X))^2]
    \]
    
    利用期望的线性性质，得到：
    
    \[
    \operatorname{Var}(X) = E(X^2) - 2 E(X) \cdot E(X) + (E(X))^2
    \]
    
    由于 \( E(X) \) 是一个常数，所以 \( E(X) \cdot E(X) = [E(X)]^2 \)，因此可以简化为：
    
    \[
    \operatorname{Var}(X) = E(X^2) - [E(X)]^2
    \]


该公式表明，计算方差时可以通过求 \( X \) 的平方的期望 \( E(X^2) \) 减去 \( X \) 的期望的平方 \( [E(X)]^2 \) 来得到。这种形式通常更方便，尤其是在 \( E(X) \) 和 \( E(X^2) \) 容易求得的情况下，可以简化计算。

其中：

- \( E(X^2) \) 是 \( X \) 的平方的期望，即二阶矩。

- \( [E(X)]^2 \) 是 \( X \) 的期望的平方。



### 方差的性质

- {==非负性==}：

方差总是非负的，即 \( \operatorname{Var}(X) \geq 0 \)。



- {==平移不变性==}

若 \( c \) 为常数，则 \( \operatorname{Var}(X + c) = \operatorname{Var}(X) \)。


- {==方差的线性变换==}

对于独立随机变量 \( Y \) ，以及常数 \( a \) 和 \( b \)，有
   
\[
   \operatorname{Var}(a + bY) = b^2 \operatorname{Var}(Y)
\]


- {==方差的加法==}

对于独立随机变量 \( X \) 和 \( Y \)，有

\[
   \operatorname{Var}(X + Y) = \operatorname{Var}(X) + \operatorname{Var}(Y)+2\operatorname{Cov}(X,Y)
\]

其中，\( \operatorname{Cov}(X,Y) \) 是 \( X \) 和 \( Y \) 的协方差，即

\[
   \operatorname{Cov}(X,Y) = E[(X - E(X))(Y - E(Y))]=E(XY)-E(X)E(Y)
\]

如果$X,Y$相互独立，则$\operatorname{Cov}(X,Y)=0$，所以

\[
   \operatorname{Var}(X + Y) = \operatorname{Var}(X) + \operatorname{Var}(Y)
\]

可推广到多个独立随机变量的情况。


### 选择平均值的原因

在计算方差时，我们通常使用平均值作为中心点，而不是其他值。这是因为平均值是使方差最小的点。也就是说，对于任何实数 \( c \)，有

\[
   \operatorname{Var'}(X) = E[(X - c)^2] \geqslant E[(X - E(X))^2] = \operatorname{Var}(X)
\]

!!!proof 
    \begin{align*}
     \operatorname{Var}(X)&=E(X-EX)^2\\
        &=E(X-c-(EX-c))^2\\
        &=E(X-c)^2-2E(X-c)(EX-c)+E(EX-c)^2\\
        &=E(X-c)^2-(EX-c)^2 \leqslant E(X-c)^2
    \end{align*}

### 切比雪夫不等式(Chebyschev)


设 \((\Omega, \mathcal{A}, P)\) 是概率空间， \(X : \Omega \rightarrow \mathbb{R}\) 是随机变量，那么对任意 \(\varepsilon > 0\)，

\[
P(|X - EX| > \varepsilon) \leqslant \frac{\operatorname{Var}(X)}{\varepsilon^2}
\]

!!!Note
    切比雪夫不等式给出了随机变量偏离其均值大于某个精度的概率的上界。

仅取 \(X \sim p(x)\) 加以证明。

\[
P(|X - EX| > \varepsilon) = \int_{x: |x - EX| > \varepsilon} p(x) \, dx
\]

\[
\leqslant \int_{x: |x - EX| > \varepsilon} \frac{|x - EX|^2}{\varepsilon^2} p(x) \, dx
\]

\[
\leqslant \frac{1}{\varepsilon^2} \int_{-\infty}^{\infty} |x - EX|^2 p(x) \, dx
\]

\[
= \frac{\operatorname{Var}(X)}{\varepsilon^2}
\]

!!!Summary "推广"
    若 \(f\) 是单调不减严格正函数，那么

    \[
    P(X > \varepsilon) \leqslant \frac{E f(X)}{f(\varepsilon)}
    \]

    事实上，使用了Markov不等式:
    
    \[
    P(X > \varepsilon) \leqslant P(f(X) \geqslant f(\varepsilon)) \leqslant \frac{E f(X)}{f(\varepsilon)}
    \]
