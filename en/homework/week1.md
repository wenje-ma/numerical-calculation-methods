# week1

> **Basic Knowledge: Error Propagation in Basic Operations**<br>Suppose the solution obtained in numerical computation depends on the parameters $x_1,x_2,\dots,x_n$, denoted $y=f\left(x_1,x_2,\dots,x_n\right)$, and let the approximation of $x_i$ be $x_i^{*}$. Assuming $f$ is differentiable at $\left(x_1^{*},x_2^{*},\dots,x_n^{*}\right)$, when the parameter errors are small, the absolute error and relative error of the solution are $e\left(y^{*}\right)\approx\sum_{i=1}^n\frac{\partial f}{\partial x_i}e\left(x_i^{*}\right)$ and $e_r\left(y^{*}\right)\approx\sum_{i=1}^n\frac{\partial f}{\partial x_i}\frac{x_i^{*}}{f}e_r\left(x_i^{*}\right)$. In particular, the error bound of a sum or difference does not exceed the sum of the error bounds of the individual numbers, and the relative error bound of a product or quotient does not exceed the sum of the relative error bounds of the individual numbers.

> **Basic Knowledge: Avoid Subtracting Two Nearly Equal Numbers**<br>By error propagation in basic operations, the relative error of the difference $u=x-y$ of two numbers is $e_r\left(u\right)\approx\frac{x}{x-y}e_r\left(x\right)-\frac{y}{x-y}e_r\left(y\right)$. When $x$ and $y$ are very close, $\left|x-y\right|$ is very small and the relative error of $u$ is very large, causing a serious loss of significant digits; hence the computational formula should be changed to avoid subtracting two nearly equal numbers.

> **Definition 1.1 (Absolute Error and Error Bound)**<br>Let $x^{*}$ be an approximation to the exact value $x$. The quantity $e\left(x^{*}\right)=x-x^{*}$ is called the absolute error of $x^{*}$, or error for short. If there exists a positive number $\varepsilon$ such that $\left|e\left(x^{*}\right)\right|=\left|x-x^{*}\right|\le\varepsilon$, then $\varepsilon$ is called the absolute error bound of $x^{*}$, or error bound for short.

> **Theorem 1.1 (Relation Between the Relative Error Bound and Significant Digits)**<br>If the approximation $x^{*}=\pm0.a_1a_2\cdots a_n\times10^{m}\left(a_1\ne0\right)$ of $x$ has $n$ significant digits, then $\frac{1}{2a_1}\times10^{-n+1}$ is its relative error bound. Conversely, if the relative error bound $\varepsilon_r$ of $x^{*}$ satisfies $\varepsilon_r\le\frac{1}{2}\times10^{-n}$, then $x^{*}$ has at least $n$ significant digits.

> **Definition 1.2 (Relative Error and Relative Error Bound)**<br>Let $x^{*}$ be an approximation to the exact value $x$. The quantity $e_r\left(x^{*}\right)=\frac{e\left(x^{*}\right)}{x^{*}}$ is called the relative error of $x^{*}$. If there exists a positive number $\varepsilon_r$ such that $\left|e_r\left(x^{*}\right)\right|\le\varepsilon_r$, then $\varepsilon_r$ is called the relative error bound of $x^{*}$.

> **Definition 1.3 (Significant Digits)**<br>If the normalized form of the approximation $x^{*}$ is $x^{*}=\pm0.a_1a_2\cdots a_n\cdots\times10^{m}$, where $m$ is an integer, $a_1\ne0$, and $\left|x-x^{*}\right|\le\frac{1}{2}\times10^{m-n}$, then $x^{*}$ is said to have $n$ significant digits.

---

## 1-3

Given that $a=1.2031$ and $b=0.978$ are approximations obtained after rounding, how many significant digits do $a+b$ and $a\times b$ have?

### Solution 1-3

By **Definition 1.1 (Absolute Error and Error Bound)** and the meaning of rounding, $a=1.2031$ has 5 significant digits, with error bound $\frac{1}{2}\times10^{-4}$; $b=0.978$ has 3 significant digits, with error bound $\frac{1}{2}\times10^{-3}$.

First consider the sum $a+b=1.2031+0.978=2.1811$. By **Basic Knowledge: Error Propagation in Basic Operations**, the error bound of a sum does not exceed the sum of the error bounds of the individual numbers, so

$$
\left|e\left(a+b\right)\right|\le\left|e\left(a\right)\right|+\left|e\left(b\right)\right|\le\frac{1}{2}\times10^{-4}+\frac{1}{2}\times10^{-3}=0.00055.
$$

Moreover, $2.1811=0.21811\times10^{1}$ ($m=1$), and $\frac{1}{2}\times10^{1-4}=\frac{1}{2}\times10^{-3}=0.0005< 0.00055\le\frac{1}{2}\times10^{1-3}=\frac{1}{2}\times10^{-2}=0.005$, so by **Definition 1.3 (Significant Digits)**, $a+b$ has 3 significant digits.

Next consider the product $a\times b=1.2031\times0.978=1.17663$. By **Definition 1.2 (Relative Error and Relative Error Bound)** and **Basic Knowledge: Error Propagation in Basic Operations**, the relative error bound of a product does not exceed the sum of the relative error bounds of the individual numbers, so

$$
\left|e_r\left(a\right)\right|\le\frac{\frac{1}{2}\times10^{-4}}{1.2031}\approx4.156\times10^{-5},\quad\left|e_r\left(b\right)\right|\le\frac{\frac{1}{2}\times10^{-3}}{0.978}\approx5.113\times10^{-4},
$$

$$
\left|e_r\left(a\times b\right)\right|\le\left|e_r\left(a\right)\right|+\left|e_r\left(b\right)\right|\approx5.528\times10^{-4},
$$

$$
\left|e\left(a\times b\right)\right|\approx\left|a\times b\right|\cdot\left|e_r\left(a\times b\right)\right|\approx1.17663\times5.528\times10^{-4}\approx6.505\times10^{-4}.
$$

Moreover, $1.17663=0.117663\times10^{1}$ ($m=1$), and $\frac{1}{2}\times10^{-3}=0.0005< 6.505\times10^{-4}\le\frac{1}{2}\times10^{-2}=0.005$, so by **Definition 1.3 (Significant Digits)**, $a\times b$ has 3 significant digits. $\blacksquare$

---

## 1-7

The side length of a square is about $100$ centimeters. How large must the error in measuring the side length be to ensure that the error in the area does not exceed $1$ centimeter$^{2}$?

### Solution 1-7

Let the side length of the square be $a\approx100$ centimeters and the area be $S=a^{2}$. By **Basic Knowledge: Error Propagation in Basic Operations**, the absolute error of the area satisfies

$$
\left|e\left(S\right)\right|\approx\left|S'\left(a\right)\right|\cdot\left|e\left(a\right)\right|=2a\left|e\left(a\right)\right|=200\left|e\left(a\right)\right|.
$$

To ensure the error in the area does not exceed $1$ centimeter$^{2}$, i.e. $\left|e\left(S\right)\right|\le1$, it suffices that

$$
200\left|e\left(a\right)\right|\le1\ \Rightarrow\ \left|e\left(a\right)\right|\le\frac{1}{200}=0.005.
$$

Therefore, when measuring the side length, the error bound in the side length should not exceed $0.005$ centimeters. $\blacksquare$

---

## 1-9

Let $s=\frac{1}{2}gt^{2}$. Suppose $g$ is exact, while the measurement of $t$ has an error of $\pm0.1$ seconds. Show that as $t$ increases, the absolute error of $s$ increases while its relative error decreases.

### Solution 1-9

By **Basic Knowledge: Error Propagation in Basic Operations**, $s=\frac{1}{2}gt^{2}$; since $g$ is exact, i.e. $e\left(g\right)=0$, the absolute error of $s$ is approximately

$$
\left|e\left(s\right)\right|\approx\left|\frac{\partial s}{\partial t}\right|\left|e\left(t\right)\right|=gt\left|e\left(t\right)\right|=0.1gt.
$$

As $t$ increases, $0.1gt$ increases, so the absolute error of $s$ increases.

Also by **Basic Knowledge: Error Propagation in Basic Operations**, for $\ln s=\ln\frac{g}{2}+2\ln t$, we have

$$
\left|e_r\left(s\right)\right|\approx\left|2\frac{e\left(t\right)}{t}\right|=\frac{2\times0.1}{t}=\frac{0.2}{t}.
$$

As $t$ increases, $\frac{0.2}{t}$ decreases, so the relative error of $s$ decreases. In summary, as $t$ increases, the absolute error of $s$ increases while its relative error decreases. $\blacksquare$

---

## 1-10

Given that $\sqrt{783}\approx27.983$ has 5 significant digits, find the two roots of the equation $x^{2}-56x+1=0$ so that they each have at least 4 significant digits.

### Solution 1-10

The discriminant of the equation $x^{2}-56x+1=0$ is

$$
\Delta=56^{2}-4=3136-4=3132=4\times783,
$$

so $\sqrt{\Delta}=2\sqrt{783}\approx2\times27.983=55.966$. By the quadratic formula, the two roots can be written as

$$
x_1=\frac{56+\sqrt{\Delta}}{2}=28+\sqrt{783}\approx28+27.983=55.983,
$$

$$
x_2=\frac{56-\sqrt{\Delta}}{2}=28-\sqrt{783}\approx28-27.983=0.017.
$$

If $x_2$ is computed directly as $28-\sqrt{783}$, this is the subtraction of two nearly equal numbers; by **Basic Knowledge: Avoid Subtracting Two Nearly Equal Numbers**, significant digits would be seriously lost, so this direct computation cannot be used.

By Vieta's formulas, the product of the two roots is $x_1x_2=1$, so $x_2=\frac{1}{x_1}$ (note $x_1\ne0$). First compute $x_1$: by **Definition 1.3 (Significant Digits)**, $\sqrt{783}\approx27.983=0.27983\times10^{2}$ has 5 significant digits with error bound $\frac{1}{2}\times10^{2-5}=\frac{1}{2}\times10^{-3}=0.0005$, so

$$
\left|e\left(x_1\right)\right|=\left|e\left(\sqrt{783}\right)\right|\le0.0005\le\frac{1}{2}\times10^{2-4}=0.005,
$$

i.e. $x_1\approx55.983$ has at least 4 significant digits.

Then by **Basic Knowledge: Error Propagation in Basic Operations**, for $x_2=\frac{1}{x_1}$, the relative error of a quotient is approximately the difference of the relative errors of numerator and denominator, so

$$
\left|e_r\left(x_2\right)\right|\approx\left|e_r\left(x_1\right)\right|\le\frac{0.0005}{55.983}\approx8.93\times10^{-6},
$$

while $x_2=\frac{1}{55.983}\approx0.017862=0.17862\times10^{-1}$, so

$$
\left|e\left(x_2\right)\right|\approx x_2\left|e_r\left(x_2\right)\right|\approx0.017862\times8.93\times10^{-6}\approx1.595\times10^{-7}\le\frac{1}{2}\times10^{-1-4}=\frac{1}{2}\times10^{-5},
$$

by **Definition 1.3 (Significant Digits)**, $x_2\approx0.017862$ has at least 4 significant digits.

Therefore the two roots are $x_1\approx55.983$ and $x_2\approx0.017862$, each having at least 4 significant digits. $\blacksquare$

---

## 1-12

Rewrite the following expressions so that the computation is more accurate: (1) $\frac{1}{1+2x}-\frac{1-x}{1+x}$, $\left|x\right|\ll1$; (2) $\sqrt{x+\frac{1}{x}}-\sqrt{x-\frac{1}{x}}$, $\left|x\right|\gg1$; (3) $\frac{\tan x-\sin x}{x^{2}}$, $\left|x\right|\ll1$ and $x\ne0$. (Only part (1) is required.)

### Solution 1-12

By **Basic Knowledge: Avoid Subtracting Two Nearly Equal Numbers**, when $\left|x\right|\ll1$, both $\frac{1}{1+2x}$ and $\frac{1-x}{1+x}$ are close to $1$, and subtracting them directly would cause a serious loss of significant digits. Combine the expression over a common denominator:

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
