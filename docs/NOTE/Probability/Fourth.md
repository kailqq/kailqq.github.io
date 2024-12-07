# 概率极限理论

## 大数定律

大数定律是概率论中的一个重要定理，它描述了在大量重复试验中，事件的频率会接近其概率。大数定律有两种形式：弱大数定律和强大数定律。

### 弱大数定律
弱大数定律指出，对于一组独立同分布的随机变量，其样本均值会以概率收敛到期望值。具体来说，如果 \(X_1, X_2, \ldots, X_n\) 是一组独立同分布的随机变量，且期望值为 \(E(X_i) = \mu\)，则对于任意的 \(\epsilon > 0\)，有：

\[
\lim_{n \to \infty} P\left( \left| \frac{1}{n} \sum_{i=1}^n X_i - \mu \right| < \epsilon \right) = 1
\]

### 强大数定律
强大数定律则更为严格，它指出样本均值几乎必然收敛到期望值。具体来说，如果 \(X_1, X_2, \ldots, X_n\) 是一组独立同分布的随机变量，且期望值为 \(E(X_i) = \mu\)，则有：

\[
P\left( \lim_{n \to \infty} \frac{1}{n} \sum_{i=1}^n X_i = \mu \right) = 1
\]

这意味着随着样本数量的增加，样本均值会几乎肯定地趋近于期望值。

### 伯努利大数定律

给定$p \in (0, 1)$，记$S_n \sim \text{Binomial}(n, p)$，则

\[
    P(w: \lvert \frac{S_n(w)}{n} - p \rvert \geqslant \epsilon) \to 0 \quad (n \to \infty)
\]

即频率与概率的偏差的概率随着试验次数的增加而趋近于0



### 依概率收敛


\((\Omega, \mathcal{S}, P)\) 是一个概率空间，\(X, X_n, n \geq 1\) 是一列随机变量，如果对任意 \(\epsilon > 0\),

\[
P(\omega : |X_n(\omega) - X(\omega)| > \epsilon) \to 0, \quad n \to \infty
\]

称 \(X_n\) 依概率收敛到 \(X\)，记做 \(X_n \xrightarrow{P} X\)。

按此概念，Bernoulli 大数律可写成

\[
\frac{S_n}{n} \xrightarrow{P} p
\]

## De Moivre-Laplace 中心极限定理

!!!quote "De Moivre公式"
    \[
        (\cos \theta + i \sin \theta)^n = \cos n\theta + i \sin n\theta
    \]

假设 \(S_n \sim B(n, p)\)，那么

\[ 
P\left( \frac{S_n - np}{\sqrt{np(1-p)}} \leqslant x \right) \approx \int_{-\infty}^{x} \frac{1}{\sqrt{2\pi}} e^{-\frac{t^2}{2}} \, dt 
\]

- 左边：规范化 \(\frac{S_n - np}{\sqrt{np(1-p)}}\) 随机变量的分布函数

- 右边：正态分布函数

\[
\Phi(x) = \int_{-\infty}^{x} \frac{1}{\sqrt{2\pi}} e^{-\frac{t^2}{2}} \, dt
\]

- 

\[
P(a \leqslant S_n \leqslant b) = P\left( \frac{a - np}{\sqrt{np(1-p)}} \leqslant \frac{S_n - np}{\sqrt{np(1-p)}} \leqslant \frac{b - np}{\sqrt{np(1-p)}} \right) 
\approx \Phi\left( \frac{b - np}{\sqrt{np(1-p)}} \right) - \Phi\left( \frac{a - np}{\sqrt{np(1-p)}} \right)
\]

\[
\bullet \text{ de Moivre - Laplace 中心极限定理的意义}
\]

- 给出近似计算公式

### 依分布收敛

假设 \((\Omega, \Sigma, P)\) 是概率空间，\(X, X_n, n \geq 1\) 是一列随机变量，\(F, F_n, n \geq 1\) 是一列相应的分布函数，如果对于 \(F\) 的任意连续点 \(x\),

\[
F_n(x) \to F(x), \quad n \to \infty
\]

称 \(F_n\) 依分布收敛于 \(F\)，记 \(F_n \xrightarrow{d} F\) 或者 \(X_n \xrightarrow{d} X\)。

按此概念，中心极限定理可写成

\[
\frac{S_n - np}{\sqrt{np(1-p)}} \xrightarrow{d} N(0, 1)
\]

## Possion 极限定理

令 \(0 < p_n < 1\)，假设 \(S_n \sim B(n, p_n)\)，如果 \(np_n \to \lambda\)，并且 \(0 < \lambda < 1\) 那么对任何 \(k = 0, 1, 2, \ldots\)

\[
P(S_n = k) \to \frac{\lambda^k e^{-\lambda}}{k!}, \quad n \to \infty
\]

证明：由于 \(S_n \sim B(n, p_n)\)

\[
P(S_n = k) = \frac{n!}{k!(n-k)!} p_n^k (1-p_n)^{n-k}
\]

\[
= \frac{1}{k!} \cdot \frac{n(n-1)\cdots(n-k+1)}{n^k} \cdot (np_n)^k \cdot \left(1 - \frac{\lambda}{n} + o\left(\frac{1}{n}\right)\right)^{n-k}
\]

\[
\to \frac{\lambda^k e^{-\lambda}}{k!}, \quad n \to \infty
\]

## Chebyshev 大数律


**Chebyshev 不等式**: 对任意随机变量 \(X\), \(EX\) 和 \(EX^2\) 存在有限, 那么对任意 \(\varepsilon > 0\)

\[
P(|X - EX| > \varepsilon) \leq \frac{Var(X)}{\varepsilon^2}
\]


!!!example "应用 Chebyshev 不等式证明 Bernoulli 大数律"
    \[
    P\left(\left|\frac{S_n}{n} - p\right| > \varepsilon\right) = P(|S_n - np| > n\varepsilon)
    \]

    \[
    \leqslant \frac{Var(S_n - np)}{n^2 \varepsilon^2}
    \]

    \[
    = \frac{np(1-p)}{n^2 \varepsilon^2} \to 0, \quad n \to \infty
    \]


假设 \(\xi_k, k \geq 1\) 是一列随机变量，\(E\xi_k = \mu\)。记 \(S_n = \sum_{k=1}^{n} \xi_k\)，如果

\[
\frac{Var(S_n)}{n^2} \to 0, \quad n \to \infty
\]

那么

\[
\frac{S_n}{n} \to \mu, \quad n \to \infty
\]

更一般地，假设 \(\xi_k, k \geq 1\) 是一列随机变量，\(E\xi_k = \mu_k\)。如果

\[
\frac{Var(S_n)}{n^2} \to 0, \quad n \to \infty
\]

那么

\[
\frac{S_n}{n} - \frac{\sum_{k=1}^{n} \mu_k}{n} \to 0, \quad n \to \infty
\]


!!!Proof "Chebyshev 大数律的证明"
    对任意 \(\varepsilon > 0\),

    \[
    P\left(\left|\frac{S_n}{n} - \frac{\sum_{k=1}^{n} \mu_k}{n}\right| > \varepsilon\right) \leqslant \frac{Var(S_n)}{n^2 \varepsilon^2} \to 0
    \]
    
    这里$S_n$ 对应Chebyshev不等式中的$X$，$\sum_{k=1}^{n} \mu_k$ 对应Chebyshev不等式中的$\mu$

    $n\varepsilon$ 对应Chebyshev不等式中的$\varepsilon$

    Chebyshev 大数律的意义:
    1. 样本均值渐近逼近均值
    2. 没有独立性要求
    3. Chebyshev 大数律的不足之处: {==要求方差存在==}


## Khinchin 大数律

假设 \(\xi_k, k \geq 1\) 是一列独立同分布的随机变量，且 \(E\xi_k = \mu\)，如果

记 \(S_n = \sum_{k=1}^{n} \xi_k\)，那么

\[
\frac{S_n}{n} \to \mu, \quad n \to \infty
\]



