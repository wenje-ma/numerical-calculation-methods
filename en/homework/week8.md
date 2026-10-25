# Assignment 8

> **Definition 8.1** (Iteration and Fixed-Point Iteration) <br>Rewrite the equation $f\left(x\right)=0$ in the equivalent form $x=\varphi\left(x\right)$; choose an initial value $x_0$ and use the iteration formula $$x_{n+1}=\varphi\left(x_n\right)\ \left(n=0,1,2,\dots\right)$$ to generate a sequence $\left\{x_n\right\}$; if $x_n\to x^{*}$, then $x^{*}=\varphi\left(x^{*}\right)$ is called a fixed point of $\varphi\left(x\right)$, and the above method is called an iteration method (fixed-point iteration).

> **Theorem 8.2** (Convergence Conditions for Fixed-Point Iteration) <br>Let the function $\varphi\left(x\right)$ satisfy on $\left[a,b\right]$: (1) for any $x\in\left[a,b\right]$, $\varphi\left(x\right)\in\left[a,b\right]$; (2) there exists a constant $0< L< 1$ such that for any $x\in\left[a,b\right]$, $\left|\varphi'\left(x\right)\right|\le L$. Then the equation $x=\varphi\left(x\right)$ has a unique root $x^{*}$ on $\left[a,b\right]$; for any initial value $x_0\in\left[a,b\right]$, the iteration sequence $x_{n+1}=\varphi\left(x_n\right)$ converges to $x^{*}$, with the a posteriori error estimate $$\left|x^{*}-x_n\right|\le\frac{L}{1-L}\left|x_n-x_{n-1}\right|.$$

> **Definition 8.2** (Order of Convergence of an Iteration Method) <br>Let the sequence $\left\{x_n\right\}$ converge to $x^{*}$; if there exist positive numbers $r$ and $a$ such that $$\lim_{n\to\infty}\frac{\left|x_{n+1}-x^{*}\right|}{\left|x_n-x^{*}\right|^{r}}=a$$ holds (when $r=1$, require $a< 1$), then the sequence $\left\{x_n\right\}$ is said to converge with order $r$; $r=1$ is called linear convergence, and $r=2$ quadratic convergence.

> **Theorem 8.4** (Relation Between the Convergence Order and the Derivative of the Iteration Function) <br>Let the iteration function $\varphi\left(x\right)$ have continuous derivatives of order $r$ in a neighborhood of $x^{*}$ $\left(r\ge2\right)$, with $x^{*}=\varphi\left(x^{*}\right)$, $\varphi'\left(x^{*}\right)=\varphi''\left(x^{*}\right)=\dots=\varphi^{\left(r-1\right)}\left(x^{*}\right)=0$, and $\varphi^{\left(r\right)}\left(x^{*}\right)\ne0$; then the iteration sequence $\left\{x_n\right\}$ converges with order $r$. If $x^{*}=\varphi\left(x^{*}\right)$ but $0< \left|\varphi'\left(x^{*}\right)\right|< 1$, then $\left\{x_n\right\}$ converges linearly.

> **Newton's Iteration** (Tangent Method, Formula (8.16)) <br>Linearizing the nonlinear equation near the root gives the iteration formula $$x_{n+1}=x_n-\frac{f\left(x_n\right)}{f'\left(x_n\right)}.$$ **Theorem 8.5** (Local Convergence of Newton's Method) states: when $f'\left(x^{*}\right)\ne0$ (i.e. $x^{*}$ is a simple root), Newton's method converges at least quadratically near $x^{*}$; when $x^{*}$ is a root of multiplicity $r$, Newton's method degenerates to linear convergence, and its improved scheme $$x_{n+1}=x_n-r\frac{f\left(x_n\right)}{f'\left(x_n\right)}\quad\left(n=0,1,2,\dots\right)$$ (Formula (8.17)) converges at least quadratically.

> **Secant Method** (Formula (8.19)) <br>Replacing the derivative by a divided difference gives the two-step iteration formula $$x_{n+1}=x_n-\frac{f\left(x_n\right)\left(x_n-x_{n-1}\right)}{f\left(x_n\right)-f\left(x_{n-1}\right)}\quad\left(n=1,2,\dots\right).$$

### Problem 1 (Problem 8-3)

Use the simple iteration method to find the roots of the following equations, requiring $\left|x_{n+1}-x_n\right|< 10^{-5}$: (1) $x-\cos x=0$; (2) $4x-e^{-x}=0$; (3) $x^{3}-2x-5=0$.

### Solution to Problem 1 (1) Rewrite the equation in the equivalent form $x=\cos x$, taking the iteration function $\varphi\left(x\right)=\cos x$. When $x\in\left[0,1\right]$, $\varphi\left(x\right)=\cos x\in\left[\cos1,1\right]\subset\left[0,1\right]$, and $\left|\varphi'\left(x\right)\right|=\left|-\sin x\right|\le\sin1\approx0.841< 1$. By **Theorem 8.2** (Convergence Conditions for Fixed-Point Iteration), the iteration $x_{n+1}=\cos x_n$ converges. Taking $x_0=0.5$, the iteration gives

$$
x_1=0.87758,\ x_2=0.63901,\ x_3=0.80269,\ \dots,\ x_{27}=0.73909,\ x_{28}=0.73908,
$$

at which point $\left|x_{28}-x_{27}\right|=8.25\times10^{-6}< 10^{-5}$, so $x^{*}\approx0.73908$. (2) Rewrite the equation as $x=\frac{1}{4}e^{-x}$, taking the iteration function $\varphi\left(x\right)=\frac{1}{4}e^{-x}$. On $\left[0,1\right]$, $\varphi\left(x\right)\in\left[\frac{e^{-1}}{4},\frac{1}{4}\right]\subset\left[0,1\right]$, and $\left|\varphi'\left(x\right)\right|=\frac{1}{4}e^{-x}\le\frac{1}{4}=0.25< 1$. By **Theorem 8.2**, the iteration converges. Taking $x_0=0.25$, the iteration gives

$$
x_1=0.19470,\ x_2=0.20577,\ x_3=0.20350,\ x_4=0.20397,\ x_5=0.20387,\ x_6=0.20389,\ x_7=0.20389,
$$

at which point $\left|x_7-x_6\right|=3.91\times10^{-6}< 10^{-5}$, so $x^{*}\approx0.20389$. (3) Rewrite the equation as $x=\sqrt\left[3\right]{2x+5}$, taking the iteration function $\varphi\left(x\right)=\left(2x+5\right)^{1/3}$. Since $f\left(2\right)=-1< 0$, $f\left(2.5\right)> 0$, take the root-containing interval $\left[2,2.5\right]$; on it, $\varphi\left(x\right)\in\left[\sqrt\left[3\right]{9},\sqrt\left[3\right]{10}\right]\subset\left[2,2.5\right]$, and

$$
\left|\varphi'\left(x\right)\right|=\frac{2}{3\left(2x+5\right)^{2/3}}\le\frac{2}{3\cdot9^{2/3}}\approx0.154< 1.
$$

By **Theorem 8.2**, the iteration converges. Taking $x_0=2$, the iteration gives

$$
x_1=2.08008,\ x_2=2.09235,\ x_3=2.09422,\ x_4=2.09450,\ x_5=2.09454,\ x_6=2.09455,
$$

at which point $\left|x_6-x_5\right|=6.55\times10^{-6}< 10^{-5}$, so $x^{*}\approx2.09455$. $\blacksquare$

### Problem 2 (Problem 8-7)

Consider the iteration method for solving the equation $12-3x+2\cos x=0$

$$
x_{n+1}=4+\frac{2}{3}\cos x_n.
$$ (1) Prove that for $\forall x_0\in\mathbf{R}$, this iteration converges to the root of the equation; (2) take $x_0=4$ and use this iteration to find an approximation to the root, with error not exceeding $\frac{1}{2}\times10^{-5}$; (3) what is the order of convergence of this iteration? Explain why.

### Solution to Problem 2

The iteration function is $\varphi\left(x\right)=4+\frac{2}{3}\cos x$. (1) For any $x\in\mathbf{R}$, $\cos x\in\left[-1,1\right]$, so $\varphi\left(x\right)\in\left[4-\frac{2}{3},4+\frac{2}{3}\right]=\left[\frac{10}{3},\frac{14}{3}\right]$, i.e. $\varphi$ maps $\mathbf{R}$ into the closed interval $\left[\frac{10}{3},\frac{14}{3}\right]$, and $\varphi\left(\left[\frac{10}{3},\frac{14}{3}\right]\right)\subset\left[\frac{10}{3},\frac{14}{3}\right]$. Also $\varphi'\left(x\right)=-\frac{2}{3}\sin x$, so for all $x$, $\left|\varphi'\left(x\right)\right|\le\frac{2}{3}< 1$. By **Theorem 8.2** (Convergence Conditions for Fixed-Point Iteration), the iteration $x_{n+1}=\varphi\left(x_n\right)$ has a unique fixed point $x^{*}$ on $\left[\frac{10}{3},\frac{14}{3}\right]$ and converges to it. For any $x_0\in\mathbf{R}$, $x_1=\varphi\left(x_0\right)\in\left[\frac{10}{3},\frac{14}{3}\right]$, and all subsequent terms converge to $x^{*}$. Moreover $x^{*}=\varphi\left(x^{*}\right)$ means $x^{*}=4+\frac{2}{3}\cos x^{*}$, i.e. $12-3x^{*}+2\cos x^{*}=0$, so $x^{*}$ is precisely the root of the original equation. (2) By the a posteriori error estimate in **Theorem 8.2**, $\left|x^{*}-x_n\right|\le\frac{L}{1-L}\left|x_n-x_{n-1}\right|$. Here the contraction factor is $L=\frac{2}{3}$, so

$$
\left|x^{*}-x_n\right|\le\frac{2/3}{1-2/3}\left|x_n-x_{n-1}\right|=2\left|x_n-x_{n-1}\right|.
$$

To make the error not exceed $\frac{1}{2}\times10^{-5}$, it suffices that $2\left|x_n-x_{n-1}\right|\le\frac{1}{2}\times10^{-5}$, i.e. $\left|x_n-x_{n-1}\right|\le\frac{1}{4}\times10^{-5}$. Taking $x_0=4$, the iteration gives

$$
x_1=3.56424,\ x_2=3.39200,\ x_3=3.35412,\ x_4=3.34833,\ x_5=3.34753,\ x_6=3.34742,\ x_7=3.34741,\ x_8=3.34740,
$$

at which point $\left|x_8-x_7\right|=2.04\times10^{-6}$ and $2\left|x_8-x_7\right|=4.08\times10^{-6}\le\frac{1}{2}\times10^{-5}$, so $x^{*}\approx3.34740$. (3) $\varphi'\left(x\right)=-\frac{2}{3}\sin x$. From (2), the fixed point is $x^{*}\approx3.3474$, at which $\sin x^{*}\approx-0.2044$, so

$$
\varphi'\left(x^{*}\right)=-\frac{2}{3}\sin x^{*}\approx0.136\ne0,\quad 0< \left|\varphi'\left(x^{*}\right)\right|< 1.
$$

By **Theorem 8.4** (Relation Between the Convergence Order and the Derivative of the Iteration Function), when $x^{*}=\varphi\left(x^{*}\right)$ and $0< \left|\varphi'\left(x^{*}\right)\right|< 1$, the iteration sequence converges linearly. Thus this iteration converges linearly (first order). $\blacksquare$

### Problem 3 (Problem 8-8)

Prove that the iteration sequence $\left\{x_n\right\}$ generated by

$$
x_{n+1}=\frac{x_n}{2}+\frac{1}{x_n}\quad\left(n=0,1,2,\dots\right)
$$

converges to $\sqrt{2}$ for any $x_0> 1$, and converges quadratically.

### Solution to Problem 3

The iteration function is $\varphi\left(x\right)=\frac{x}{2}+\frac{1}{x}\ \left(x> 0\right)$.

First find the fixed point. Set $x=\varphi\left(x\right)$, i.e. $x=\frac{x}{2}+\frac{1}{x}$, which simplifies to $\frac{x}{2}=\frac{1}{x}$, i.e. $x^{2}=2$; the positive fixed point is $x^{*}=\sqrt{2}$.

Next prove convergence. For any $x> 0$, by the AM–GM inequality

$$
\varphi\left(x\right)=\frac{x}{2}+\frac{1}{x}\ge2\sqrt{\frac{x}{2}\cdot\frac{1}{x}}=\sqrt{2},
$$

with equality if and only if $\frac{x}{2}=\frac{1}{x}$, i.e. $x=\sqrt{2}$. Thus starting from any $x_0> 1$, $x_1=\varphi\left(x_0\right)\ge\sqrt{2}$. When $x_n\ge\sqrt{2}$, $$
\varphi\left(x\right)-x=\frac{x}{2}+\frac{1}{x}-x=\frac{2-x^{2}}{2x}\le0\quad\left(x\ge\sqrt{2}\right),
$$

i.e. $x_{n+1}=\varphi\left(x_n\right)\le x_n$. Thus from $x_1$ onward, $\left\{x_n\right\}$ is monotonically decreasing and bounded below by $\sqrt{2}$; by the monotone convergence theorem, $\left\{x_n\right\}$ converges to some limit $L\ge\sqrt{2}$. Taking limits on both sides of $x_{n+1}=\varphi\left(x_n\right)$ ($\varphi$ is continuous) gives $L=\frac{L}{2}+\frac{1}{L}$, i.e. $L^{2}=2$; together with $L\ge\sqrt{2}$, $L=\sqrt{2}$. Hence for any $x_0> 1$, $x_n\to\sqrt{2}$.

Finally examine the convergence order. $\varphi'\left(x\right)=\frac{1}{2}-\frac{1}{x^{2}}$, $\varphi''\left(x\right)=\frac{2}{x^{3}}$, and hence

$$
\varphi'\left(\sqrt{2}\right)=\frac{1}{2}-\frac{1}{2}=0,\quad \varphi''\left(\sqrt{2}\right)=\frac{2}{\left(\sqrt{2}\right)^{3}}=\frac{1}{\sqrt{2}}\ne0.
$$

By **Theorem 8.4** (Relation Between the Convergence Order and the Derivative of the Iteration Function), since $\varphi\left(\sqrt{2}\right)=\sqrt{2}$, $\varphi'\left(\sqrt{2}\right)=0$ and $\varphi''\left(\sqrt{2}\right)\ne0$, the iteration sequence $\left\{x_n\right\}$ converges quadratically near $\sqrt{2}$. $\blacksquare$

### Problem 4 (Problem 8-10)

Use Newton's method to solve the following equations, requiring $\left|x_{n+1}-x_n\right|< 10^{-6}$: (1) $x-\ln x=2$; (2) $xe^{x}-1=0$; (3) $x+\sin x=1$.

### Solution to Problem 4

By **Newton's Iteration** (Formula (8.16)), $x_{n+1}=x_n-\frac{f\left(x_n\right)}{f'\left(x_n\right)}$. (1) $f\left(x\right)=x-\ln x-2$, $f'\left(x\right)=1-\frac{1}{x}=\frac{x-1}{x}$. The root-containing interval is $\left[2,4\right]$ ($f\left(3\right)< 0$, $f\left(4\right)> 0$). The Newton scheme is

$$
x_{n+1}=x_n-\frac{x_n-\ln x_n-2}{1-\frac{1}{x_n}}.
$$

Taking $x_0=3$, the iteration gives $x_1=3.14792$, $x_2=3.14619$, $x_3=3.14619$, at which point $\left|x_3-x_2\right|\approx2.2\times10^{-7}< 10^{-6}$, so $x^{*}\approx3.14619$. (2) $f\left(x\right)=xe^{x}-1$, $f'\left(x\right)=e^{x}\left(1+x\right)$. The Newton scheme is

$$
x_{n+1}=x_n-\frac{x_ne^{x_n}-1}{e^{x_n}\left(1+x_n\right)}.
$$

Taking $x_0=0.5$, the iteration gives $x_1=0.57102$, $x_2=0.56716$, $x_3=0.56714$, $x_4=0.56714$, at which point $\left|x_4-x_3\right|\approx1.2\times10^{-10}< 10^{-6}$, so $x^{*}\approx0.56714$. (3) $f\left(x\right)=x+\sin x-1$, $f'\left(x\right)=1+\cos x$. The Newton scheme is

$$
x_{n+1}=x_n-\frac{x_n+\sin x_n-1}{1+\cos x_n}.
$$

Taking $x_0=0.5$, the iteration gives $x_1=0.51096$, $x_2=0.51097$, $x_3=0.51097$, at which point $\left|x_3-x_2\right|\approx3.1\times10^{-11}< 10^{-6}$, so $x^{*}\approx0.51097$. $\blacksquare$

### Problem 5 (Problem 8-12)

Prove that the equation $f\left(x\right)=x^{3}-x-1=0$ has exactly one root in $\left[1,2\right]$. Take $x_0=1.5$ and use Newton's method to find this root, accurate to 5 significant digits, and show that its order of convergence is 2.

### Solution to Problem 5

First prove existence and uniqueness. $f\left(1\right)=1-1-1=-1< 0$, $f\left(2\right)=8-2-1=5> 0$; by the intermediate value theorem, $f\left(x\right)=0$ has a root in $\left(1,2\right)$. Also $f'\left(x\right)=3x^{2}-1$, and on $\left[1,2\right]$, $f'\left(x\right)\ge3\cdot1^{2}-1=2> 0$, so $f\left(x\right)$ is strictly increasing on $\left[1,2\right]$ and hence has exactly one root in $\left[1,2\right]$.

By **Newton's Iteration** (Formula (8.16)), $$
x_{n+1}=x_n-\frac{x_n^{3}-x_n-1}{3x_n^{2}-1}.
$$

Taking $x_0=1.5$, the iteration gives $x_1=1.34783$, $x_2=1.32520$, $x_3=1.32472$, $x_4=1.32472$, at which point $\left|x_4-x_3\right|\approx2.2\times10^{-7}$, so the root is $x^{*}\approx1.3247$ (5 significant digits).

Then explain the convergence order. At the root, $f'\left(x^{*}\right)=3\left(1.3247\right)^{2}-1\approx4.265\ne0$, so $x^{*}$ is a simple root. By **Theorem 8.5** (Local Convergence of Newton's Method), when $f'\left(x^{*}\right)\ne0$, the sequence generated by Newton's method converges to $x^{*}$ at least quadratically, so the order of convergence of this Newton iteration is 2. $\blacksquare$

### Problem 6 (Problem 8-13)

If $x^{*}$ is a root of multiplicity $r$ of $f\left(x\right)=0$, i.e. $f\left(x\right)=\left(x-x^{*}\right)^{r}\varphi\left(x\right)$ with $\varphi\left(x^{*}\right)\ne0$, prove: (1) Newton's method converges linearly near $x^{*}$; (2) the modified Newton method

$$
x_{n+1}=x_n-r\frac{f\left(x_n\right)}{f'\left(x_n\right)}\quad\left(n=0,1,2,\dots\right)
$$

converges quadratically.

### Solution to Problem 6

From $f\left(x\right)=\left(x-x^{*}\right)^{r}\varphi\left(x\right)$ with $\varphi\left(x^{*}\right)\ne0$, differentiating gives

$$
f'\left(x\right)=r\left(x-x^{*}\right)^{r-1}\varphi\left(x\right)+\left(x-x^{*}\right)^{r}\varphi'\left(x\right)
=\left(x-x^{*}\right)^{r-1}\left[r\varphi\left(x\right)+\left(x-x^{*}\right)\varphi'\left(x\right)\right].
$$ (1) The iteration function of Newton's method is $g\left(x\right)=x-\frac{f\left(x\right)}{f'\left(x\right)}$. Substituting the above, $$
g\left(x\right)-x^{*}=\left(x-x^{*}\right)-\frac{\left(x-x^{*}\right)\varphi\left(x\right)}{r\varphi\left(x\right)+\left(x-x^{*}\right)\varphi'\left(x\right)}
=\left(x-x^{*}\right)\cdot\frac{\left(r-1\right)\varphi\left(x\right)+\left(x-x^{*}\right)\varphi'\left(x\right)}{r\varphi\left(x\right)+\left(x-x^{*}\right)\varphi'\left(x\right)}.
$$

Hence

$$
\lim_{x\to x^{*}}\frac{g\left(x\right)-x^{*}}{x-x^{*}}
=\frac{\left(r-1\right)\varphi\left(x^{*}\right)}{r\varphi\left(x^{*}\right)}=\frac{r-1}{r}.
$$

For a root of multiplicity $r$ $\left(r\ge2\right)$, $0< \frac{r-1}{r}< 1$. By **Definition 8.2** (Order of Convergence of an Iteration Method) and **Theorem 8.4** (Relation Between the Convergence Order and the Derivative of the Iteration Function), the sequence generated by Newton's method converges linearly to $x^{*}$ near $x^{*}$ with ratio $\frac{r-1}{r}$, i.e. Newton's method converges linearly for multiple roots. (2) The iteration function of the modified Newton method is $g\left(x\right)=x-r\frac{f\left(x\right)}{f'\left(x\right)}$, and hence

$$
g\left(x\right)-x^{*}=\left(x-x^{*}\right)-\frac{r\left(x-x^{*}\right)\varphi\left(x\right)}{r\varphi\left(x\right)+\left(x-x^{*}\right)\varphi'\left(x\right)}
=\frac{\left(x-x^{*}\right)^{2}\varphi'\left(x\right)}{r\varphi\left(x\right)+\left(x-x^{*}\right)\varphi'\left(x\right)}.
$$

Therefore

$$
\lim_{x\to x^{*}}\frac{g\left(x\right)-x^{*}}{\left(x-x^{*}\right)^{2}}
=\frac{\varphi'\left(x^{*}\right)}{r\varphi\left(x^{*}\right)}.
$$

This limit is a finite constant (a nonzero constant when $\varphi'\left(x^{*}\right)\ne0$). By **Definition 8.2** (Order of Convergence of an Iteration Method), the sequence generated by the modified Newton method converges to $x^{*}$ at least quadratically near $x^{*}$. $\blacksquare$

### Problem 7 (Problem 8-16)

Use the secant method to solve the following equations, requiring $\left|x_{n+1}-x_n\right|< 10^{-5}$: (1) $x-\ln x=2$; (2) $5x-\cos x-1=0$; (3) $x=3-2^{x}$. (Only part (1) is required.) ### Solution to Problem 7

By the **Secant Method** (Formula (8.19)), the iteration scheme is

$$
x_{n+1}=x_n-\frac{f\left(x_n\right)\left(x_n-x_{n-1}\right)}{f\left(x_n\right)-f\left(x_{n-1}\right)}.
$$ (Only part (1).) Take $f\left(x\right)=x-\ln x-2$. On the root-containing interval $\left[3,4\right]$, take the initial values $x_0=3$, $x_1=4$ ($f\left(3\right)< 0$, $f\left(4\right)> 0$); the iteration gives

$$
x_2=3.13844,\ x_3=3.14580,\ x_4=3.14619,\ x_5=3.14619,
$$

at which point $\left|x_5-x_4\right|\approx2.3\times10^{-7}< 10^{-5}$, so $x^{*}\approx3.14619$. $\blacksquare$
