# week4

> **Definition 1.1 (Absolute Error and Error Bound)**
> 
> Let $x^{*}$ be an approximation to the exact value $x$. The quantity $e\left(x^{*}\right)=x-x^{*}$ is called the absolute error of $x^{*}$, or error for short. If there exists a positive number $\varepsilon$ such that $\left|e\left(x^{*}\right)\right|=\left|x-x^{*}\right|\le\varepsilon$, then $\varepsilon$ is called the absolute error bound of $x^{*}$, or error bound for short.

> **Theorem 1.1 (Relation Between the Relative Error Bound and Significant Digits)**
> 
> If the approximation $x^{*}=\pm0.a_1a_2\cdots a_n\times10^{m}\left(a_1\ne0\right)$ of $x$ has $n$ significant digits, then $\frac{1}{2a_1}\times10^{-n+1}$ is its relative error bound. Conversely, if the relative error bound $\varepsilon_r$ of $x^{*}$ satisfies $\varepsilon_r\le\frac{1}{2}\times10^{-n}$, then $x^{*}$ has at least $n$ significant digits.

> **Definition 1.2 (Relative Error and Relative Error Bound)**
> 
> Let $x^{*}$ be an approximation to the exact value $x$. The quantity $e_r\left(x^{*}\right)=\frac{e\left(x^{*}\right)}{x^{*}}$ is called the relative error of $x^{*}$. If there exists a positive number $\varepsilon_r$ such that $\left|e_r\left(x^{*}\right)\right|\le\varepsilon_r$, then $\varepsilon_r$ is called the relative error bound of $x^{*}$.

> **Definition 1.3 (Significant Digits)**
> 
> If the normalized form of the approximation $x^{*}$ is $x^{*}=\pm0.a_1a_2\cdots a_n\cdots\times10^{m}$, where $m$ is an integer, $a_1\ne0$, and $\left|x-x^{*}\right|\le\frac{1}{2}\times10^{m-n}$, then $x^{*}$ is said to have $n$ significant digits.

## 1-12

Rewrite the following expressions so that the computation is more accurate: (1) $\frac{1}{1+2x}-\frac{1-x}{1+x}$, $\left|x\right|\ll1$; (2) $\sqrt{x+\frac{1}{x}}-\sqrt{x-\frac{1}{x}}$, $\left|x\right|\gg1$; (3) $\frac{\tan x-\sin x}{x^{2}}$, $\left|x\right|\ll1$ and $x\ne0$. (Only part (1) is required.)

### Solution to 1-12

By Avoid Subtracting Two Nearly Equal Numbers, when $\left|x\right|\ll1$, both $\frac{1}{1+2x}$ and $\frac{1-x}{1+x}$ are close to $1$, and subtracting them directly would cause a serious loss of significant digits. Combine the expression over a common denominator:

$$
\frac{1}{1+2x}-\frac{1-x}{1+x}=\frac{\left(1+x\right)-\left(1-x\right)\left(1+2x\right)}{\left(1+2x\right)\left(1+x\right)}.
$$

While

$$
\left(1-x\right)\left(1+2x\right)=1+2x-x-2x^{2}=1+x-2x^{2},
$$

$$
\left(1+x\right)-\left(1-x\right)\left(1+2x\right)=\left(1+x\right)-\left(1+x-2x^{2}\right)=2x^{2},
$$

Therefore

$$
\frac{1}{1+2x}-\frac{1-x}{1+x}=\frac{2x^{2}}{\left(1+2x\right)\left(1+x\right)}.
$$

When $\left|x\right|\ll1$, $\left(1+2x\right)\left(1+x\right)$ is close to $1$; the rewritten denominator no longer involves subtracting nearly equal numbers, and the numerator $2x^{2}$ is very small, thus avoiding the loss of significant digits. Hence one should use $\frac{2x^{2}}{\left(1+2x\right)\left(1+x\right)}$ for the computation. $\blacksquare$
