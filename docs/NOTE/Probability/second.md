---
comments: true
---

# 随机变量与随机向量

## 随机变量

### 随机变量的概念

!!! info "随机变量"
    定义概率空间 $(\Omega, \mathcal{F}, P)$ 上的单值实函数 $\xi(\omega)$，即

    $$
    \xi: \Omega\to \mathbb R
    $$

    还要求 $\xi(\omega)$ 的任意取值组合对应的样本点集合构成的事件在事件域 $\mathcal{F}$ 中，这样就可以称 $\xi(\omega)$ 为 **随机变量 (random variable)**


### 离散型随机变量

离散型随机变量：随机变量 $\xi$ 可取的值至多可列个。

!!! info "分布列 (distribution sequence)"
    $$
    \left[
    \begin{matrix}
    x_1&x_2&\cdots&x_n&\cdots\\
    p(x_1)&p(x_2)&\cdots&p(x_n)&\cdots
    \end{matrix}
    \right]
    $$

第一行是 $\xi$ 可能取的值，第二行是 $\xi$ 取这些值的概率。

!!! abstract "分布列的性质"
    - 正性，即

    $$
    p(x_i)>0,i=1,2\cdots
    $$

    - 规范性，即

    $$
    \sum_{i=1}^\infty p(x_i)=1
    $$

!!! example "Examples"
    对一些常见离散型随机变量举例如下：

    === "退化分布"
        即 degenerate distribution

        $$
        \left[
        \begin{matrix}
        c\\
        1
        \end{matrix}
        \right]
        $$

    === "两点分布"
        即 **伯努利分布** ，Bernoulli distribution

        $$
        \left[
        \begin{matrix}
        1&0\\
        p&1-p
        \end{matrix}
        \right],p\in (0,1)
        $$

    === "二项分布"
        即 binomial distribution

        $$
        P(\xi=k)=\begin{pmatrix}
            n\\k
        \end{pmatrix}
        p^k(1-p)^{n-k},p\in (0,1),k=0,1,\cdots,n
        $$

        记为 $\xi\sim B(n,p)$

    === "泊松分布"
        即 Poisson distribution
       
        $$
        P(\xi=k)=\frac{\lambda^k}{k!}e^{-\lambda}
        ,\lambda>0,k\in \mathbb N
        $$

        记为 $\xi\sim\mathcal{P}(\lambda)$
        
        对于二项分布，当 $n\to\infty,np=\lambda$ 时，二项分布趋近于泊松分布。
        
        \begin{align*}
        \lim_{n\to\infty}\begin{pmatrix}
            n\\k
        \end{pmatrix}p^k(1-p)^{n-k}&=\frac{1}{k!}n(n-1)\cdots(n-k+1)\frac{1}{n^k}(np)^k(1-\frac{np}{n})^{n-k}\\
        &=\frac{\lambda^k}{k!}(1-\frac{1}{n})\cdots(1-\frac{k-1}{n})e^{-\lambda}\\
        &=\frac{\lambda^k}{k!}e^{-\lambda}\\
        \end{align*}
        
        !!!Note
            其中 $\lambda=np$ 是泊松分布的参数，也是它的数学期望；
            因为
            
            \begin{align*}
                E_{\xi\sim P(\lambda)}(\xi)&=\sum_{k=0}^\infty k\frac{\lambda^k}{k!}e^{-\lambda}\\
                &=\lambda\sum_{k=1}^\infty\frac{\lambda^{k-1}}{(k-1)!}e^{-\lambda}\\
                &=\lambda e^{\lambda}e^{-\lambda}\\
                &=\lambda
            \end{align*}

    === "几何分布"
        即 geometry distribution,一般用于解决第一次成功的问题

        $$
        P(\xi=k)=p(1-p)^{k-1},p\in (0,1),k\in \mathbb{N}_+
        $$

    === "超几何分布"
        即 hypergeometry distribution，一般用于解决次品抽样问题 

        $$
        P(\xi=k)=\frac{\displaystyle
        \begin{pmatrix}
            M\\k
        \end{pmatrix}
        \begin{pmatrix}
            N-M\\n-k
        \end{pmatrix}
            }{\displaystyle
        \begin{pmatrix}
            N\\n
        \end{pmatrix}}
        ,n\leqslant N,M\leqslant N,k=0,1,\cdots, \min\{n,M\}
        $$

## 分布函数与连续型随机变量

离散型随机变量是用分布列来描述的，而对于某些情况，例如随机变量可以在某一个区间内取任意值，这个时候就不存在分布列，需要引入新的描述方法来描述概率分布，并且我们希望这个描述方法能够对一切的随机变量都适用。

!!!Definition "分布函数"
    设 $\xi$ 是一个随机变量，对任意实数 $x$，定义函数 $F(x)$ 为

    $$
    F(x)=P(\xi \leqslant x)
    $$

    这个函数称为 $\xi$ 的 **分布函数 (distribution function)**
    对于给定的随机变量 $\xi$，其分布函数是唯一的，它是实变量 $x$ 的函数，且满足：
    !!!Property "性质"
        - 有界性：作为事件的概率自然有 $0\leqslant F(x)\leqslant 1$
        - 单调不减性：$x_1<x_2\Rightarrow F(x_1)\leqslant F(x_2)$
       
        - 作为一个有界的单调不减函数 $F(-\infty)=0$, $F(+\infty)=1$
        - 右连续性：$\lim_{x\to x_0+0}F(x)=F(x_0)$，左极限存在$\lim_{x\to x_0-0}F(x)=F(x_0)$
        - 在有些教材中  
        
        $$F(x)=P(\xi < x)$$
        
        此时 $F(x)$要求左连续,右极限存在
    
    ???Note 各种随机变量的分布函数
        - 对于离散型随机变量，其分布函数是阶梯函数
        - 对于连续型随机变量，其分布函数是连续函数，采用密度函数积分来计算
        - 只要函数值大于0，且整个定义域积分为1，就可以叫做密度函数
        

### 正态分布

!!!Definition
    若随机变量 $\xi$ 的分布函数为

    $$
    F(x)=\frac{1}{\sqrt{2\pi}\sigma}\int_{-\infty}^x e^{-\frac{(t-\mu)^2}{2\sigma^2}}dt
    $$

    其中 $\mu$ 和 $\sigma$ 是常数，且 $\sigma>0$，则称 $\xi$ 服从参数为 $\mu$ 和 $\sigma$ 的 **正态分布 (normal distribution)**，记为 $\xi\sim N(\mu,\sigma^2)$

    正态分布的密度函数为

    $$
    f(x)=\frac{1}{\sqrt{2\pi}\sigma}e^{-\frac{(x-\mu)^2}{2\sigma^2}}
    $$

    正态分布是最重要的分布之一，它的密度函数是一个钟形曲线，且具有以下性质：
    !!!Property
        - 期望值：$E(\xi)=\mu$
        - 方差：$D(\xi)=\sigma^2$
        - 正态分布的密度函数是关于 $\mu$ 对称的，即 $f(x)=f(2\mu-x)$
    
    !!!section "标准正态分布"
        若 $\xi\sim N(0,1)$，则称 $\xi$ 服从 **标准正态分布 (standard normal distribution)**，记为 $\xi\sim N(0,1)$

        此时 $\mu=0$，$\sigma=1$，其密度函数为

        $$
        f(x)=\frac{1}{\sqrt{2\pi}}e^{-\frac{x^2}{2}}
        $$

        如果$x$不是标准正态分布，则可以通过

        \[
            \eta = \dfrac{x - \mu}{ \sigma} 
        \]

        将其变为 $\eta$ ,标准分布


虽然标准正态分布的显式分布函数求不出来，但是可以通过查表得到其值

!!!Note "3 $\sigma$ 原则"
    \[
    0.6827 \quad 0.9545 \quad 0.99.73
    \]


### 随机变量的映射

对于常见的函数$f$,$Y=f(X)$ 也是一个随机变量


!!!section "计算Y的分布"
    === "离散型随机变量"
        此时$Y$也是离散型随机变量;根据 $X$ 的取值，可以得到 $Y$ 的取值，然后根据 $X$ 的分布列，可以得到 $Y$ 的分布列,
        
        $$P(Y=y_i)=P(X=x_i,j\dots,k),f(X=x_i,j\dots,k)=y_i$$

    
    === "连续型随机变量"
        此时$Y$不一定是连续型随机变量，没有统一的计算公式，但是 **一般可以先求出$Y$的分布函数，然后求导得到密度函数**



### 离散型随机向量



给定概率空间 \((\Omega, A, P)\)，\((X, Y)\) 是 2-随机向量。

假设 \(X\) 取值为 \(x_1, x_2, \dots\)，\(Y\) 取值为 \(y_1, y_2, \dots\)。那么称 \((X, Y)\) 为离散型随机向量。

记

\[
p_{ij} = P(X = x_i, Y = y_j), \quad i, j = 1, 2, \dots
\]

满足

\[
p_{ij} \geq 0, \quad \sum_{i,j} p_{ij} = 1
\]

称

\[
\left( (x_i, y_j), p_{ij} \right)_{i,j=1}^{\infty}
\]

为随机向量 \((X, Y)\) 的联合分布。




对于任意 Borel 集合 \( A, B \),

\[
P(X \in A, Y \in B) = \sum_{i: x_i \in A, j: y_j \in B} p_{ij}
\]

特别地，

\[
P(X \leq x, Y \leq y) = \sum_{i: x_i \leq x, j: y_j \leq y} p_{ij}
\]

#### 边际分布

\( X, Y \) 的分布可以由 \( p_{ij} \) 计算得到

\[
X \sim \begin{pmatrix} x_1 & x_2 & \dots & x_i & \dots \\ p_1. & p_2. & \dots & p_i. & \dots \end{pmatrix}
\]

其中

\[
p_i = \sum_{j=1}^{\infty} p_{ij}, \quad p_i \geq 0, \quad \sum_{i=1}^{\infty} p_i = 1
\]

类似地，

\[
Y \sim \begin{pmatrix} y_1 & y_2 & \dots & y_j & \dots \\ p_{.1} & p_{.2} & \dots & p_{.j} & \dots \end{pmatrix}
\]

其中

\[
p_{.j} = \sum_{i=1}^{\infty} p_{ij}, \quad p_{.j} \geq 0, \quad \sum_{j=1}^{\infty} p_{.j} = 1
\]


!!!Warning
    边际分布由联合分布唯一确定，但是反过来不一定成立。因为加起来等于一个值并不能确定分开的每一个值



### 条件概率与条件分布

对于固定的 \( x_i, y_j \)，我们得到

\[
P(Y = y_j | X = x_i) = \frac{P(X = x_i, Y = y_j)}{P(X = x_i)} = \frac{p_{ij}}{p_i}
\]

如果 \( x_i, y_j \) 变化，那么我们可以得到条件分布：

给定 \( X = x_i \) 的条件下，\( Y \) 可取值 \( y_1, y_2, \dots, y_j, \dots \) 时，概率分别为

\[
P(Y = y_j | X = x_i) = \frac{p_{ij}}{p_i}
\]

#### 条件分布列

\[
Y | X = x_i \sim \begin{pmatrix} y_1 & y_2 & \dots & y_j & \dots \\ \frac{p_{i1}}{p_i} & \frac{p_{i2}}{p_i} & \dots & \frac{p_{ij}}{p_i} & \dots \end{pmatrix}
\]

同理也可以得到 $X|Y$ 的条件分布

!!!Note
    方便起见，这里把 $P_{i.}$ 记为 $P_i$

### 连续性随机向量



给定概率空间 \((\Omega, A, P)\)，\((X, Y)\) 是其上的随机向量。如果存在 \(p(x, y)\) 使得

\[ 
p(x, y) \geq 0, \quad \int_{-\infty}^{\infty} \int_{-\infty}^{\infty} p(x, y) dx dy = 1 
\]

并且对任意 Borel 集 \(A, B \subset \mathbb{R}\),

\[ 
P(X \in A, Y \in B) = \int_A \int_B p(u, v) du dv 
\]

那么称 \((X, Y)\) 是连续型随机向量，具有密度函数 \(p(x, y)\)。

特别，对任意 \(x, y \in \mathbb{R}\)

\[ 
P(X \leq x, Y \leq y) = \int_{-\infty}^x \int_{-\infty}^y p(u, v) du dv 
\]

#### 连续型的边际分布

显然，如果 \((X, Y)\) 是连续型随机向量，那么 \(X, Y\) 都是连续型随机变量。并且，

\[ 
X \sim p_X(x), \quad Y \sim p_Y(y) 
\]

其中

\[ 
p_X(x) = \int_{-\infty}^{\infty} p(x, y) dy, \quad p_Y(y) = \int_{-\infty}^{\infty} p(x, y) dx 
\]

同样，联合分布惟一决定边际分布，边际分布不能决定联合分布。

#### 连续型的条件分布

与离散型的类似；连续型的条件分布的密度函数就是在原来的基础上分母变为对应确定变量的边际函数某点的值；更详细地说:


假设 \((X, Y)\) 是连续型随机向量，具有联合密度函数 \(p(x, y)\)，下面讨论条件分布

给定 \(X = x\)，求 \(Y\) 的分布？

即 \(P(Y \leq y | X = x)\)

注意 \(P(X = x) = 0\)，我们采用

\[ 
P(Y \leq y | X = x) = \lim_{\varepsilon \to 0} P(Y \leq y | x - \varepsilon < X \leq x + \varepsilon) 
\]

\[
P(Y \leq y | X = x) = \lim_{\varepsilon \to 0} \frac{P(Y \leq y, x - \varepsilon < X \leq x + \varepsilon)}{P(x - \varepsilon < X \leq x + \varepsilon)}
\]

\[
= \lim_{\varepsilon \to 0} \frac{\int_{x-\varepsilon}^{x+\varepsilon} \int_{-\infty}^{y} p(u, v) \, dv \, du / (2 \varepsilon)}{\int_{x-\varepsilon}^{x+\varepsilon} p_X(u) \, du / (2\varepsilon)}
\]

\[
= \frac{\int_{-\infty}^{y} p(x, v) \, dv}{p_X(x)}
\]

给定 \(X = x\) 下，\(Y\) 具有密度函数

\[
p_{Y|X}(y|x) = \frac{p(x, y)}{p_X(x)}
\]

!!!key-point
    推导过程中上下同时除以 $2\varepsilon$ 是为了使用拉格朗日中值定理
    即

    \[
        F(x+\varepsilon)-F(x-\varepsilon) = F'(\xi)2\varepsilon
    \]



!!!example "联合正态分布"
    如果随机向量 \((X, Y)\) 具有密度函数：\(\forall x, y \in \mathbb{R}\)

    \[
    p(x, y) = \frac{1}{2\pi\sigma_1\sigma_2\sqrt{1-\rho^2}} e^{-\frac{1}{2(1-\rho^2)}\left(\frac{(x-\mu_1)^2}{\sigma_1^2} - \frac{2\rho(x-\mu_1)(y-\mu_2)}{\sigma_1\sigma_2} + \frac{(y-\mu_2)^2}{\sigma_2^2}\right)}
    \]

    那么称 \((X, Y)\) 服从二维联合正态分布，\(\mu_1, \mu_2, \sigma_1^2, \sigma_2^2, \rho\) 为参数。简记

    \[
    (X, Y) \sim \mathcal{N}(\mu_1, \sigma_1^2, \mu_2, \sigma_2^2; \rho)
    \]

    验证 \(p(x, y)\) 确实是密度函数

    \[
    \int_{-\infty}^{\infty} \int_{-\infty}^{\infty} \frac{1}{2\pi\sigma_1\sigma_2\sqrt{1-\rho^2}} e^{-\frac{1}{2(1-\rho^2)}\left[\frac{x^2}{\sigma_1^2} - \frac{2\rho xy}{\sigma_1\sigma_2} + \frac{y^2}{\sigma_2^2}\right]} dxdy = 1
    \]

    经过变换：\(u = \frac{x-\mu_1}{\sigma_1}, v = \frac{y-\mu_2}{\sigma_2}\)，等价于

    \[
    \int_{-\infty}^{\infty} \int_{-\infty}^{\infty} \frac{1}{2\pi\sqrt{1-\rho^2}} e^{-\frac{1}{2(1-\rho^2)}[u^2 - 2\rho uv + v^2]} dudv = 1
    \]

    左边进行配方，得

    \[
    = \int_{-\infty}^{\infty} \frac{1}{\sqrt{2\pi}} e^{-v^2/2} \left( \int_{-\infty}^{\infty} \frac{1}{\sqrt{2\pi(1-\rho^2)}} e^{-\frac{1}{2(1-\rho^2)}(u-\rho v)^2} du \right) dv
    \]

    \[
    = \int_{-\infty}^{\infty} \frac{1}{\sqrt{2\pi}} e^{-v^2/2} dv = 1
    \]
    
    !!!idea 
        这里利用了标准正态分布的性质，即

        \[
        \int_{-\infty}^{\infty} \frac{1}{\sqrt{2\pi}} e^{-v^2/2} dv = 1
        \]


    !!!property "联合正态分布的边际分布"
        $p_X(x)$ 和 $p_Y(y)$ 都是正态分布

        假设 \((X, Y) \sim \mathcal{N}(\mu_1, \sigma_1^2, \mu_2, \sigma_2^2; \rho)\)，求 \(X, Y\) 的边际分布？

        \[ 
        X \sim p_X(x) 
        \]

        \[
        p_X(x) = \int_{-\infty}^{\infty} p(x, y) \, dy
        \]

        \[
        = \int_{-\infty}^{\infty} \frac{1}{2\pi\sigma_1\sigma_2\sqrt{1-\rho^2}} e^{-\frac{1}{2(1-\rho^2)}\left[\frac{(x-\mu_1)^2}{\sigma_1^2} - \frac{2\rho(x-\mu_1)(y-\mu_2)}{\sigma_1\sigma_2} + \frac{(y-\mu_2)^2}{\sigma_2^2}\right]} \, dy
        \]

        进行配方，得

        令 \(z = y - \mu_2\)，则

        \[
        p_X(x) = \int_{-\infty}^{\infty} \frac{1}{2\pi\sigma_1\sigma_2\sqrt{1-\rho^2}} e^{-\frac{1}{2(1-\rho^2)}\left[\frac{(x-\mu_1)^2}{\sigma_1^2} - \frac{2\rho(x-\mu_1)z}{\sigma_1\sigma_2} + \frac{z^2}{\sigma_2^2}\right]} \, dz
        \]

        将指数部分进行配方，得

        \[
        -\frac{1}{2(1-\rho^2)}\left[\frac{(x-\mu_1)^2}{\sigma_1^2} - \frac{2\rho(x-\mu_1)z}{\sigma_1\sigma_2} + \frac{z^2}{\sigma_2^2}\right] = -\frac{(x-\mu_1)^2}{2\sigma_1^2} - \frac{z^2 - 2\rho(x-\mu_1)z\sigma_2/\sigma_1 + \rho^2(x-\mu_1)^2\sigma_2^2/\sigma_1^2}{2\sigma_2^2(1-\rho^2)}
        \]

        \[
        = -\frac{(x-\mu_1)^2}{2\sigma_1^2} - \frac{(z - \rho(x-\mu_1)\sigma_2/\sigma_1)^2}{2\sigma_2^2(1-\rho^2)}
        \]

        因此，

        \[
        p_X(x) = \frac{1}{2\pi\sigma_1\sigma_2\sqrt{1-\rho^2}} e^{-\frac{(x-\mu_1)^2}{2\sigma_1^2}} \int_{-\infty}^{\infty} e^{-\frac{(z - \rho(x-\mu_1)\sigma_2/\sigma_1)^2}{2\sigma_2^2(1-\rho^2)}} \, dz
        \]

        由于

        \[
        \int_{-\infty}^{\infty} e^{-\frac{(z - \rho(x-\mu_1)\sigma_2/\sigma_1)^2}{2\sigma_2^2(1-\rho^2)}} \, dz = \sqrt{2\pi\sigma_2^2(1-\rho^2)}
        \]

        所以

        \[
        p_X(x) = \frac{1}{2\pi\sigma_1\sigma_2\sqrt{1-\rho^2}} e^{-\frac{(x-\mu_1)^2}{2\sigma_1^2}} \cdot \sqrt{2\pi\sigma_2^2(1-\rho^2)}
        \]

        \[
        = \frac{1}{\sqrt{2\pi}\sigma_1} e^{-\frac{(x-\mu_1)^2}{2\sigma_1^2}}
        \]

        因此，

        \[
        X \sim \mathcal{N}(\mu_1, \sigma_1^2)
        \]

    当 $\rho = 0$ 时，$X, Y$ 独立



对于一般的随机向量，有可能其既没有分布列，也没有密度函数，此时主要用其分布函数来描述。
    

### 独立性

对于联合分布，如果 $p(x,y)=p_X(x)p_Y(y)$，则称 $X$ 和 $Y$ 独立。

或者 $F(x,y)=F_X(x)F_Y(y)$

或者对于任意波雷尔集$A,B$

\[
    P( X \in A,Y \in B)=P(X \in A)P(Y \in B)
\]

一般最后一个是很好用的，可以用来证明$f(X),g(Y)$是独立的，(运用原像集也是博雷尔集的性质)


### 二元分布函数的性质

!!!property "二元分布函数的性质"
    - \(F(-\infty, y) = 0\), \(F(x, -\infty) = 0\), \(F(\infty, \infty) = 1\)
    - \(F(x, y)\) 关于 \(x\) 和 \(y\) 非减
    - \(F(x, y)\) 关于 \(x\) 和 \(y\) 右连续，左极限存在

    \[
        P(a < X \leqslant b, c < Y \leqslant d) = F(a,c)+F(b,d)-F(a,d)-F(b,c)
    \]

    可以从积分区域的角度理解


$F_X(x) = F(x, \infty)$

$F_Y(y) = F(\infty, y)$


#### 条件分布

假设 \((X, Y)\) 具有分布函数 \(F(x, y)\)，那么给定 \(X = x\)，\(Y\) 的条件分布函数为

\[
P(Y \leqslant y | X = x) = \lim_{\varepsilon \to 0} P(Y \leqslant y | x - \varepsilon < X \leqslant x + \varepsilon)
\]

\[
= \lim_{\varepsilon \to 0} \frac{F(x + \varepsilon, y) - F(x - \varepsilon, y)}{F_X(x + \varepsilon) - F_X(x - \varepsilon)}
\]

类似地，

\[
P(X \leqslant x | Y = y) = \lim_{\varepsilon \to 0} P(X \leqslant x | y - \varepsilon < Y \leqslant y + \varepsilon)
\]

\[
= \lim_{\varepsilon \to 0} \frac{F(x, y + \varepsilon) - F(x, y - \varepsilon)}{F_Y(y + \varepsilon) - F_Y(y - \varepsilon)}
\]


#### 多维随机向量

- 多维随机向量

假设 \((\Omega, \mathcal{A}, P)\) 是给定的概率空间，

\[
\mathbf{X} = (X_1, X_2, \cdots, X_m) : \Omega \mapsto \mathbb{R}^m
\]

如果对任意 Borel 集 \(B \subset \mathbb{R}^m\),

\[
\{\omega : \mathbf{X}(\omega) \in B\} \in \mathcal{A}
\]

!!!Note
    这里指的是经过随机向量的映射后仍属于博雷尔集的样本点的集合仍在事件域中

那么称 \(\mathbf{X}\) 为 \(m\)-维随机向量

- \(m\)-元联合分布函数

假设 \(\mathbf{X} = (X_1, X_2, \cdots, X_m)\) 是 \(m\)-维随机向量，其联合分布函数为

\[
F_{\mathbf{X}}(\mathbf{x}) = P(X_1 \leq x_1, \cdots, X_m \leq x_m)
\]

其中 \(\mathbf{x} = (x_1, \cdots, x_m)\).

- 边际分布

\(X_i\) 的边际分布为

\[
F_{X_i}(x_i) = P(X_i \leq x_i)
\]

- 独立随机变量

假设 \(\mathbf{X} = (X_1, X_2, \cdots, X_m)\) 是 \(m\)-维随机向量，其联合分布函数为 \(F_{\mathbf{X}}(x)\)，边际分布为 \(F_{X_i}(x_i), i = 1, \cdots, m\)。如果

\[
F_{\mathbf{X}}(\mathbf{x}) = \prod_{i=1}^{m} F_{X_i}(x_i), \quad \forall \mathbf{x} = (x_1, \cdots, x_m)
\]

那么称 \(X_1, X_2, \cdots, X_m\) 相互独立。

- 注：如果 \(X_1, X_2, \cdots, X_m\) 相互独立，那么

1. \((X_{i_1}, X_{i_2}, \cdots, X_{i_k}), k \leq m\) 相互独立
2. \(f_1(X_1), f_2(X_2), \cdots, f_m(X_m)\) 相互独立
3. \(f(X_{i_1}, X_{i_2}, \cdots, X_{i_k}), g(X_{j_1}, X_{j_2}, \cdots, X_{j_l})\) 分别是 \(k\) 元和 \(l\) 元 Borel 可测函数，且 \(A \cap B = \emptyset\)。如果 \(A, B \subset \{1, 2, \cdots, m\}, |A| = k, |B| = l\)，并且 \(A \cap B = \emptyset\)，那么 \(f(X_i, i \in A)\) 和 \(g(X_i, i \in B)\) 相互独立。