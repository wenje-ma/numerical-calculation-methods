# week2

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

## 1-7

The side length of a square is about $100$ centimeters. How large must the error in measuring the side length be to ensure that the error in the area does not exceed $1$ centimeter$^{2}$?

### Solution to 1-7

Let the side length of the square be $a\approx100$ centimeters and the area be $S=a^{2}$. By Error Propagation in Basic Operations, the absolute error of the area satisfies

$$
\left|e\left(S\right)\right|\approx\left|S'\left(a\right)\right|\cdot\left|e\left(a\right)\right|=2a\left|e\left(a\right)\right|=200\left|e\left(a\right)\right|.
$$

To ensure the error in the area does not exceed $1$ centimeter$^{2}$, i.e. $\left|e\left(S\right)\right|\le1$, it suffices that

$$
200\left|e\left(a\right)\right|\le1\ \Rightarrow\ \left|e\left(a\right)\right|\le\frac{1}{200}=0.005.
$$

Therefore, when measuring the side length, the error bound in the side length should not exceed $0.005$ centimeters. $\blacksquare$

## 1-9

Let $s=\frac{1}{2}gt^{2}$. Suppose $g$ is exact, while the measurement of $t$ has an error of $\pm0.1$ seconds. Show that as $t$ increases, the absolute error of $s$ increases while its relative error decreases.

### Solution to 1-9

By Error Propagation in Basic Operations, $s=\frac{1}{2}gt^{2}$; since $g$ is exact, i.e. $e\left(g\right)=0$, the absolute error of $s$ is approximately

$$
\left|e\left(s\right)\right|\approx\left|\frac{\partial s}{\partial t}\right|\left|e\left(t\right)\right|=gt\left|e\left(t\right)\right|=0.1gt.
$$

As $t$ increases, $0.1gt$ increases, so the absolute error of $s$ increases.

Also by Error Propagation in Basic Operations, for $\ln s=\ln\frac{g}{2}+2\ln t$, we have

$$
\left|e_r\left(s\right)\right|\approx\left|2\frac{e\left(t\right)}{t}\right|=\frac{2\times0.1}{t}=\frac{0.2}{t}.
$$

As $t$ increases, $\frac{0.2}{t}$ decreases, so the relative error of $s$ decreases. In summary, as $t$ increases, the absolute error of $s$ increases while its relative error decreases. $\blacksquare$
