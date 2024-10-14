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
        - 右连续性：$\lim_{x\to x_0+0}F(x)=F(x_0)$
        - 在有些教材中  
        
        $$F(x)=P(\xi \leq x)$$
        
        此时 $F(x)$要求左连续

