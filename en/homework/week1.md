# Assignment 1

> **Definition 1.1** (Absolute Error and Error Bound) <br>Let $x^{*}$ be an approximation to the exact value $x$. The quantity $e\left(x^{*}\right)=x-x^{*}$ is called the absolute error of the approximation $x^{*}$, or error for short. In general the exact value is hard to obtain, and hence the exact value of the absolute error $e\left(x^{*}\right)$ cannot be computed; however, from the measuring instrument or the computation one can estimate the range of its possible values, namely an upper bound $\varepsilon$ on the absolute value of the error: $$\left|e\left(x^{*}\right)\right|=\left|x-x^{*}\right|\le\varepsilon.$$ Then $\varepsilon$ is called the absolute error bound of the approximation $x^{*}$, or error bound for short.

> **Definition 1.2** (Relative Error and Relative Error Bound) <br>Let $x^{*}$ be an approximation to the exact value $x$. The ratio of the absolute error to the exact value is called the relative error of the approximation $x^{*}$, denoted $e_r\left(x^{*}\right)$, that is $$e_r\left(x^{*}\right)=\frac{e\left(x^{*}\right)}{x}=\frac{x-x^{*}}{x}.$$ Since the exact value $x$ is always unknown in the computation, the relative error is generally taken to be $$e_r\left(x^{*}\right)=\frac{e\left(x^{*}\right)}{x^{*}}.$$ Similarly, only an upper bound on the relative error can be estimated. If there exists a positive number $\varepsilon_r$ such that $$\left|e_r\left(x^{*}\right)\right|=\left|\frac{e\left(x^{*}\right)}{x^{*}}\right|\le\varepsilon_r,$$ then $\varepsilon_r$ is called the relative error bound of $x^{*}$.

> **Definition 1.3** (Significant Digits) <br>If the error bound of the approximation $x^{*}$ is $\frac{1}{2}\times10^{-n}$, then $x^{*}$ is said to be accurate to the $n$-th decimal place, and all digits from the first nonzero digit up to this place are called significant digits. In general, if the normalized form of the approximation $x^{*}$ is $$x^{*}=\pm0.a_1a_2\cdots a_n\cdots\times10^{m},$$ where $m$ is an integer, $a_1\ne0$, and each $a_i\left(i=1,2,\dots\right)$ is an integer between $0$ and $9$, and $$\left|x-x^{*}\right|\le\frac{1}{2}\times10^{m-n},$$ then the approximation $x^{*}$ is said to have $n$ significant digits.

> **Theorem 1.1** (Relation Between the Relative Error Bound and Significant Digits) <br>If the approximation $x^{*}=\pm0.a_1a_2\cdots a_n\times10^{m}\left(a_1\ne0\right)$ of $x$ has $n$ significant digits, then $\frac{1}{2a_1}\times10^{-n+1}$ is its relative error bound. Conversely, if the relative error bound $\varepsilon_r$ of $x^{*}$ satisfies $\varepsilon_r\le\frac{1}{2}\times10^{-n}$, then $x^{*}$ has at least $n$ significant digits.

> **Error Propagation** (Error Estimation in Basic Operations) <br>Suppose the solution obtained in numerical computation depends on the parameters $x_1,x_2,\dots,x_n$, denoted $y=f\left(x_1,x_2,\dots,x_n\right)$, and let the approximation of the parameter $x_i$ be $x_i^{*}$. Assuming $f$ is differentiable at $\left(x_1^{*},x_2^{*},\dots,x_n^{*}\right)$, then when the parameter errors are small, the absolute error and relative error of the solution are respectively $$e\left(y^{*}\right)\approx\sum_{i=1}^n\frac{\partial f\left(x_1^{*},x_2^{*},\dots,x_n^{*}\right)}{\partial x_i}e\left(x_i^{*}\right),$$ $$e_r\left(y^{*}\right)\approx\sum_{i=1}^n\frac{\partial f\left(x_1^{*},x_2^{*},\dots,x_n^{*}\right)}{\partial x_i}\frac{x_i^{*}}{f\left(x_1^{*},x_2^{*},\dots,x_n^{*}\right)}e_r\left(x_i^{*}\right).$$ In particular, the above formulas give the error formulas for sums, differences, products and quotients: $$\begin{cases}e\left(x_1\pm x_2\right)=e\left(x_1\right)\pm e\left(x_2\right),\\e_r\left(x_1\pm x_2\right)\approx\frac{x_1}{x_1\pm x_2}e_r\left(x_1\right)\pm\frac{x_2}{x_1\pm x_2}e_r\left(x_2\right),\end{cases}$$ $$\begin{cases}e\left(x_1x_2\right)\approx x_2e\left(x_1\right)+x_1e\left(x_2\right),\\e_r\left(x_1x_2\right)\approx e_r\left(x_1\right)+e_r\left(x_2\right),\end{cases}$$ $$\begin{cases}e\left(\frac{x_1}{x_2}\right)\approx\frac{1}{x_2}e\left(x_1\right)-\frac{x_1}{x_2^2}e\left(x_2\right),\\e_r\left(\frac{x_1}{x_2}\right)\approx e_r\left(x_1\right)-e_r\left(x_2\right).\end{cases}$$ Therefore, the error bound of a sum or difference does not exceed the sum of the error bounds of the individual numbers, and the relative error bound of a product or quotient does not exceed the sum of the relative error bounds of the individual numbers.

> **1.4 Issues to Note in Numerical Computation** (Avoid Subtracting Two Nearly Equal Numbers) <br>By **Error Propagation**, the relative error of the difference $u=x-y$ of two numbers is $$e_r\left(u\right)\approx\frac{x}{x-y}e_r\left(x\right)-\frac{y}{x-y}e_r\left(y\right).$$ When $x$ and $y$ are very close, $\left|x-y\right|$ is very small and the relative error of $u$ is very large, causing a serious loss of significant digits. To avoid this situation, the computational formula is often changed.

### Problem 1 (Problem 1-3)

Given that $a=1.2031$ and $b=0.978$ are approximations obtained after rounding, how many significant digits do $a+b$ and $a\times b$ have? ### Solution to Problem 1

By **Definition 1.1** (Absolute Error and Error Bound), $a=1.2031$ has 5 significant digits, with error bound $\frac{1}{2}\times10^{-4}$; $b=0.978$ has 3 significant digits, with error bound $\frac{1}{2}\times10^{-3}$.

First consider the sum $a+b=1.2031+0.978=2.1811$. By **Error Propagation** (the error bound of a sum or difference does not exceed the sum of the error bounds of the individual numbers), $$
\left|e\left(a+b\right)\right|\le\left|e\left(a\right)\right|+\left|e\left(b\right)\right|\le\frac{1}{2}\times10^{-4}+\frac{1}{2}\times10^{-3}=0.00055.
$$

Moreover, $2.1811=0.21811\times10^{1}$ ($m=1$), and $\frac{1}{2}\times10^{1-4}=\frac{1}{2}\times10^{-3}=0.0005<0.00055\le\frac{1}{2}\times10^{1-3}=\frac{1}{2}\times10^{-2}=0.005$, so by **Definition 1.3** (Significant Digits), $a+b$ has 3 significant digits.

Next consider the product $a\times b=1.2031\times0.978=1.17663$. By **Definition 1.2** (Relative Error and Relative Error Bound) and **Error Propagation** (the relative error bound of a product does not exceed the sum of the relative error bounds of the individual numbers), $$
\left|e_r\left(a\right)\right|\le\frac{\frac{1}{2}\times10^{-4}}{1.2031}\approx4.156\times10^{-5},\quad\left|e_r\left(b\right)\right|\le\frac{\frac{1}{2}\times10^{-3}}{0.978}\approx5.113\times10^{-4},
$$

therefore

$$
\left|e_r\left(a\times b\right)\right|\le\left|e_r\left(a\right)\right|+\left|e_r\left(b\right)\right|\approx5.528\times10^{-4},
$$

$$
\left|e\left(a\times b\right)\right|\approx\left|a\times b\right|\cdot\left|e_r\left(a\times b\right)\right|\approx1.17663\times5.528\times10^{-4}\approx6.505\times10^{-4}.
$$

Moreover, $1.17663=0.117663\times10^{1}$ ($m=1$), and $\frac{1}{2}\times10^{-3}=0.0005<6.505\times10^{-4}\le\frac{1}{2}\times10^{-2}=0.005$, so by **Definition 1.3**, $a\times b$ has 3 significant digits. $\blacksquare$

### Problem 2 (Problem 1-7)

The side length of a square is about $100$ centimeters. How large must the error in measuring the side length be to ensure that the error in the area does not exceed $1$ centimeter$^{2}$? ### Solution to Problem 2

Let the side length of the square be $a\approx100$ centimeters and the area be $S=a^{2}$. By **Error Propagation** (absolute error estimation), the absolute error of the area satisfies

$$
\left|e\left(S\right)\right|\approx\left|S'\left(a\right)\right|\cdot\left|e\left(a\right)\right|=2a\left|e\left(a\right)\right|=200\left|e\left(a\right)\right|.
$$

To ensure the error in the area does not exceed $1$ centimeter$^{2}$, i.e. $\left|e\left(S\right)\right|\le1$, it suffices that

$$
200\left|e\left(a\right)\right|\le1\ \Rightarrow\ \left|e\left(a\right)\right|\le\frac{1}{200}=0.005.
$$

Therefore, when measuring the side length, the error (error bound) in the side length should not exceed $0.005$ centimeters. $\blacksquare$

### Problem 3 (Problem 1-9)

Let $s=\frac{1}{2}gt^{2}$. Suppose $g$ is exact, while the measurement of $t$ has an error of $\pm0.1$ seconds. Show that as $t$ increases, the absolute error of $s$ increases while its relative error decreases.

### Solution to Problem 3

By **Error Propagation** (absolute error estimation), $s=\frac{1}{2}gt^{2}$; since $g$ is exact, i.e. $e\left(g\right)=0$, the absolute error of $s$ is approximately

$$
\left|e\left(s\right)\right|\approx\left|\frac{\partial s}{\partial t}\right|\left|e\left(t\right)\right|=gt\left|e\left(t\right)\right|=0.1gt.
$$

As $t$ increases, $0.1gt$ increases, so the absolute error of $s$ increases.

Also, by **Error Propagation** (relative error $e_r\left(y^{*}\right)\approx d\left(\ln f\right)$), for $\ln s=\ln\frac{g}{2}+2\ln t$, we have

$$
\left|e_r\left(s\right)\right|\approx\left|2\frac{e\left(t\right)}{t}\right|=\frac{2\times0.1}{t}=\frac{0.2}{t}.
$$

As $t$ increases, $\frac{0.2}{t}$ decreases, so the relative error of $s$ decreases. In summary, as $t$ increases, the absolute error of $s$ increases while its relative error decreases. $\blacksquare$

### Problem 4 (Problem 1-10)

Given that $\sqrt{783}\approx27.983$ has 5 significant digits, find the two roots of the equation $x^{2}-56x+1=0$ so that they each have at least 4 significant digits.

### Solution to Problem 4

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

If $x_2$ is computed directly as $28-\sqrt{783}$, this is the subtraction of two nearly equal numbers; by **1.4 Issues to Note in Numerical Computation** (Avoid Subtracting Two Nearly Equal Numbers), significant digits would be seriously lost, so this direct computation cannot be used.

By Vieta's formulas, the product of the two roots is $x_1x_2=1$, so $x_2=\frac{1}{x_1}$ (note $x_1\ne0$). First compute $x_1$: by **Definition 1.3** (Significant Digits), $\sqrt{783}\approx27.983=0.27983\times10^{2}$ has 5 significant digits with error bound $\frac{1}{2}\times10^{2-5}=\frac{1}{2}\times10^{-3}=0.0005$, so

$$
\left|e\left(x_1\right)\right|=\left|e\left(\sqrt{783}\right)\right|\le0.0005\le\frac{1}{2}\times10^{2-4}=0.005,
$$

i.e. $x_1\approx55.983$ has at least 4 significant digits.

Then, by **Error Propagation** (relative error of a quotient), for $x_2=\frac{1}{x_1}$, we have

$$
\left|e_r\left(x_2\right)\right|\approx\left|e_r\left(x_1\right)\right|\le\frac{0.0005}{55.983}\approx8.93\times10^{-6},
$$

while $x_2=\frac{1}{55.983}\approx0.017862=0.17862\times10^{-1}$, so

$$
\left|e\left(x_2\right)\right|\approx x_2\left|e_r\left(x_2\right)\right|\approx0.017862\times8.93\times10^{-6}\approx1.595\times10^{-7}\le\frac{1}{2}\times10^{-1-4}=\frac{1}{2}\times10^{-5},
$$

by **Definition 1.3**, $x_2\approx0.017862$ has at least 4 significant digits.

Therefore the two roots are $x_1\approx55.983$ and $x_2\approx0.017862$, each having at least 4 significant digits. $\blacksquare$

### Problem 5 (Problem 1-12)

Rewrite the following expressions so that the computation is more accurate: (1) $\frac{1}{1+2x}-\frac{1-x}{1+x}$, $\left|x\right|\ll1$; (2) $\sqrt{x+\frac{1}{x}}-\sqrt{x-\frac{1}{x}}$, $\left|x\right|\gg1$; (3) $\frac{\tan x-\sin x}{x^{2}}$, $\left|x\right|\ll1$ and $x\ne0$. (Only part (1) is required.) ### Solution to Problem 5

By **1.4 Issues to Note in Numerical Computation** (Avoid Subtracting Two Nearly Equal Numbers), when $\left|x\right|\ll1$, both $\frac{1}{1+2x}$ and $\frac{1-x}{1+x}$ are close to $1$, and subtracting them directly would cause a serious loss of significant digits. Combine the expression over a common denominator: $$
\frac{1}{1+2x}-\frac{1-x}{1+x}=\frac{\left(1+x\right)-\left(1-x\right)\left(1+2x\right)}{\left(1+2x\right)\left(1+x\right)}.
$$

while

$$
\left(1-x\right)\left(1+2x\right)=1+2x-x-2x^{2}=1+x-2x^{2},
$$

$$
\left(1+x\right)-\left(1-x\right)\left(1+2x\right)=\left(1+x\right)-\left(1+x-2x^{2}\right)=2x^{2},
$$

therefore

$$
\frac{1}{1+2x}-\frac{1-x}{1+x}=\frac{2x^{2}}{\left(1+2x\right)\left(1+x\right)}.
$$

When $\left|x\right|\ll1$, $\left(1+2x\right)\left(1+x\right)$ is close to $1$; the rewritten denominator no longer involves subtracting nearly equal numbers, and the numerator $2x^{2}$ is very small, thus avoiding the loss of significant digits. Hence one should use $\frac{2x^{2}}{\left(1+2x\right)\left(1+x\right)}$ for the computation. $\blacksquare$
