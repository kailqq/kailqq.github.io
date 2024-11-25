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
    \quad i = 1, 2, \dots, n，\operatorname{同分布，但是不独立}
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


## 协方差矩阵

### 均值向量

对于一个随机向量 \( X = (X_1, X_2, \dots, X_n) \)，如果$X_i$的数学期望存在；其均值向量 \( \mu \) 定义为：

\[
\mu = E(X) = (E(X_1), E(X_2), \dots, E(X_n))
\]

### 协方差

假设$X$和$Y$是两个随机变量，且两者的数学期望和方差都存在，那么$X$和$Y$的协方差定义为：

\[
\operatorname{Cov}(X, Y) = E[(X - E(X))(Y - E(Y))]
\]

协方差也可以表示为：

\[
\operatorname{Cov}(X, Y) = E(XY) - E(X)E(Y)
\]

!!!Note "Cauchy-Schwarz不等式"

    对于任意两个随机变量$X$和$Y$，有

    \[
        \operatorname{Cov}(X, Y)^2 \leq \operatorname{Var}(X) \operatorname{Var}(Y)
    \]
    
    \[
        E[(X - E(X))(Y - E(Y))] \leqslant \sqrt{E[(X - E(X))^2]E[(Y - E(Y))^2]}
    \]

    运用任意实数$t$,满足

    \[
        E[(|X|+t|Y|)^2] \geqslant 0
    \]

    展开利用二次函数的性质即可；


协方差矩阵为

\[
\Sigma = \begin{bmatrix}
\operatorname{Var}(X_1) & \operatorname{Cov}(X_1, X_2) & \cdots & \operatorname{Cov}(X_1, X_n) \\
\operatorname{Cov}(X_2, X_1) & \operatorname{Var}(X_2) & \cdots & \operatorname{Cov}(X_2, X_n) \\
\vdots & \vdots & \ddots & \vdots \\
\operatorname{Cov}(X_n, X_1) & \operatorname{Cov}(X_n, X_2) & \cdots & \operatorname{Var}(X_n)
\end{bmatrix}
\]

对于二元随机变量 \( X = (X_1, X_2) \)，协方差矩阵为

\[
\Sigma = \begin{bmatrix}
\operatorname{Var}(X_1) & \operatorname{Cov}(X_1, X_2) \\
\operatorname{Cov}(X_2, X_1) & \operatorname{Var}(X_2)
\end{bmatrix}
\]

!!!key-point
    协方差矩阵是一个非负定矩阵，即对于任意非零列向量 \( a \)，有 \( a^T \Sigma a \geq 0 \)。


如果$X$, $Y$相互独立，此时 $E(XY)=E(X)E(Y)$ 那么$\operatorname{Cov}(X, Y) = 0$，反之，如果$\operatorname{Cov}(X, Y) = 0$，并不一定有$X$和$Y$相互独立，但是可以定义为{==不相关==}。


!!!Example
    二元联合正态分布的协方差为$\pho$

### 相关系数

!!!Definition
    二元函数的相关系数（Correlation Coefficient）用来衡量两个随机变量 \( X \) 和 \( Y \) 之间的线性关系，其定义基于协方差和标准差，计算公式如下：

    \[
    \rho(X, Y) = \frac{\operatorname{Cov}(X, Y)}{\sigma_X \cdot \sigma_Y}
    \]

    其中：

    - \(\operatorname{Cov}(X, Y)\) 是 \( X \) 和 \( Y \) 的协方差，定义为：
      
    \[
      \operatorname{Cov}(X, Y) = \mathbb{E}[(X - \mathbb{E}[X])(Y - \mathbb{E}[Y])] = \mathbb{E}[XY] - \mathbb{E}[X] \cdot \mathbb{E}[Y]
    \]

    - \(\sigma_X\) 和 \(\sigma_Y\) 分别是 \( X \) 和 \( Y \) 的标准差，定义为：
      
    \[
      \sigma_X = \sqrt{\operatorname{Var}(X)}, \quad \sigma_Y = \sqrt{\operatorname{Var}(Y)}
    \]
      
      其中方差为：
     
    \[
      \operatorname{Var}(X) = \mathbb{E}[(X - \mathbb{E}[X])^2]
    \]

    1. **取值范围：**
       
    \[
       -1 \leq \rho(X, Y) \leq 1
    \]
       
       - 当 \(\rho(X, Y) = 1\) 时，\( X \) 和 \( Y \) 完全正线性相关。
       - 当 \(\rho(X, Y) = -1\) 时，\( X \) 和 \( Y \) 完全负线性相关。
       - 当 \(\rho(X, Y) = 0\) 时，\( X \) 和 \( Y \) 没有线性关系，但不一定独立。

    2. **无量纲性：**
       \(\rho(X, Y)\) 是一个无量纲量，反映的是两变量线性关系的强弱，与变量的量纲无关。

    3. **对称性：**
    
    \[
       \rho(X, Y) = \rho(Y, X)
    \]

    一般也用$\gamma$来表示相关系数

## 条件期望

对于两个随机变量X，Y，其条件期望定义为：

=== "离散型"
    给定$Y=y_i$,$X$的条件期望定义为

    \[
        E(X|Y=y_i)=\sum_{i=1}^\infty x_i P(X=x_i|Y=y_i)
    \]

    要求该级数绝对收敛

    若给定$X$,$Y$的条件期望也是类似

=== "连续型"
    
    \[
        P(X=x|Y=y)=\dfrac{p(x,y)}{p_Y(y)}
    \]

    所以

    \[
        E(X=x|Y=y)=\int_{-\infty}^{+infty} x  P(X=x|Y=y) dx
    \]
    
    要求该积分绝对可积

    若给定$X$,$Y$的条件期望也是类似


### 全期望公式

$$
P(X = x_i, Y = y_j) = p_{ij}, \quad i, j = 1, 2, \ldots
$$

每一个 $y_j$，对应一个条件期望 $E(X|Y = y_j)$，即

$$
y_j \rightarrow E(X|Y = y_j)
$$

定义

$$
g(y_j) = E(X|Y = y_j)
$$

即

$$
g(Y) = E(X|Y)
$$

它是 $Y$ 的函数，所以是随机变量。求 $Eg(Y)$；

$$
Eg(Y) = \sum_{j=1}^{\infty} g(y_j) P(Y = y_j)
$$

$$
= \sum_{j=1}^{\infty} \sum_{i=1}^{\infty} x_i P(X = x_i | Y = y_j) P(Y = y_j)
$$

$$
= \sum_{i=1}^{\infty} x_i \sum_{j=1}^{\infty} P(X = x_i | Y = y_j) P(Y = y_j)
$$

$$
= \sum_{i=1}^{\infty} x_i P(X = x_i)
$$

$$
= E X
$$

!!!key-point
    $E(E(X|Y))=EX$,$E(E(Y|X))=EY$