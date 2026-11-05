# week1

> **Definition 1.1 (Absolute Error and Error Bound)**
> 
> Let $x^{*}$ be an approximation to the exact value $x$. The quantity $e\left(x^{*}\right)=x-x^{*}$ is called the absolute error of $x^{*}$, or error for short. If there exists a positive number $\varepsilon$ such that $\left|e\left(x^{*}\right)\right|=\left|x-x^{*}\right|\le\varepsilon$, then $\varepsilon$ is called the absolute error bound of $x^{*}$, or error bound for short.

> **Theorem 1.1 (Relation Between the Relative Error Bound and Significant Digits)**
> 
> If the approximation $x^{*}=\pm0.a_1a_2\cdots{a}_n\times10^{m}\left(a_1\ne0\right)$ of $x$ has $n$ significant digits, then $\frac{1}{2a_1}\times10^{-n+1}$ is its relative error bound. Conversely, if the relative error bound $\varepsilon_r$ of $x^{*}$ satisfies $\varepsilon_r\le\frac{1}{2}\times10^{-n}$, then $x^{*}$ has at least $n$ significant digits.

> **Definition 1.2 (Relative Error and Relative Error Bound)**
> 
> Let $x^{*}$ be an approximation to the exact value $x$. The quantity $e_r\left(x^{*}\right)=\frac{e\left(x^{*}\right)}{x^{*}}$ is called the relative error of $x^{*}$. If there exists a positive number $\varepsilon_r$ such that $\left|e_r\left(x^{*}\right)\right|\le\varepsilon_r$, then $\varepsilon_r$ is called the relative error bound of $x^{*}$.

> **Definition 1.3 (Significant Digits)**
> 
> If the normalized form of the approximation $x^{*}$ is $x^{*}=\pm0.a_1a_2\cdots{a}_n\cdots\times10^{m}$, where $m$ is an integer, $a_1\ne0$, and $\left|x-x^{*}\right|\le\frac{1}{2}\times10^{m-n}$, then $x^{*}$ is said to have $n$ significant digits.

## 1-3

Given that $a=1.2031$ and $b=0.978$ are approximations obtained after rounding, how many significant digits do $a+b$ and $a\times{b}$ have?

### Solution to 1-3

By **Definition 1.1 (Absolute Error and Error Bound)** and the meaning of rounding, $a=1.2031$ has 5 significant digits, with error bound $\frac{1}{2}\times10^{-4}$; $b=0.978$ has 3 significant digits, with error bound $\frac{1}{2}\times10^{-3}$.

First consider the sum $a+b=1.2031+0.978=2.1811$. By Error Propagation in Basic Operations, the error bound of a sum does not exceed the sum of the error bounds of the individual numbers, so

$$
\left|e\left(a+b\right)\right|\le\left|e\left(a\right)\right|+\left|e\left(b\right)\right|\le\frac{1}{2}\times10^{-4}+\frac{1}{2}\times10^{-3}=0.00055.
$$

Moreover, $2.1811=0.21811\times10^{1}$ ($m=1$), and $\frac{1}{2}\times10^{1-4}=\frac{1}{2}\times10^{-3}=0.0005<0.00055\le\frac{1}{2}\times10^{1-3}=\frac{1}{2}\times10^{-2}=0.005$, so by **Definition 1.3 (Significant Digits)**, $a+b$ has 3 significant digits.

Next consider the product $a\times{b}=1.2031\times0.978=1.17663$. By **Definition 1.2 (Relative Error and Relative Error Bound)** and Error Propagation in Basic Operations, the relative error bound of a product does not exceed the sum of the relative error bounds of the individual numbers, so

$$
\left|e_r\left(a\right)\right|\le\frac{\frac{1}{2}\times10^{-4}}{1.2031}\approx4.156\times10^{-5},\quad\left|e_r\left(b\right)\right|\le\frac{\frac{1}{2}\times10^{-3}}{0.978}\approx5.113\times10^{-4},
$$

$$
\left|e_r\left(a\times{b}\right)\right|\le\left|e_r\left(a\right)\right|+\left|e_r\left(b\right)\right|\approx5.528\times10^{-4},
$$

$$
\left|e\left(a\times{b}\right)\right|\approx\left|a\times{b}\right|\cdot\left|e_r\left(a\times{b}\right)\right|\approx1.17663\times5.528\times10^{-4}\approx6.505\times10^{-4}.
$$

Moreover, $1.17663=0.117663\times10^{1}$ ($m=1$), and $\frac{1}{2}\times10^{-3}=0.0005<6.505\times10^{-4}\le\frac{1}{2}\times10^{-2}=0.005$, so by **Definition 1.3 (Significant Digits)**, $a\times{b}$ has 3 significant digits. $\blacksquare$
