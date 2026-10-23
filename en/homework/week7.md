# Assignment 7

> **Definition 7.1** (Algebraic Degree of Precision) <br>If, whenever $f\left(x\right)$ is any polynomial of degree at most $m$, the quadrature formula $\int_a^b f\left(x\right)dx\approx\sum_{k=0}^n A_k f\left(x_k\right)$ holds exactly, but does not hold exactly for some polynomial of degree $m+1$, then the quadrature formula is said to have algebraic degree of precision $m$.

> **Theorem 7.2** (Error of the Trapezoidal Rule) <br>If $f\left(x\right)\in C^{\left(2\right)}\left[a,b\right]$, then the truncation error of the trapezoidal rule is $$R_1\left(f\right)=\int_a^b f\left(x\right)dx-\frac{b-a}{2}\left[f\left(a\right)+f\left(b\right)\right]=-\frac{\left(b-a\right)^3}{12}f''\left(\xi\right),\ \xi\in\left(a,b\right).$$

> **Theorem 7.3** (Error of Simpson's Rule) <br>If $f\left(x\right)\in C^{\left(4\right)}\left[a,b\right]$, then the truncation error of Simpson's rule is $$R_2\left(f\right)=\int_a^b f\left(x\right)dx-\frac{b-a}{6}\left[f\left(a\right)+4f\left(\frac{a+b}{2}\right)+f\left(b\right)\right]=-\frac{\left(b-a\right)^5}{2880}f^{\left(4\right)}\left(\xi\right)=-\frac{h^5}{90}f^{\left(4\right)}\left(\xi\right),\ \xi\in\left(a,b\right),$$ where $h=b-a$.

> **Composite Trapezoidal Rule** (Formulas (7.29), (7.30)) <br>Divide $\left[a,b\right]$ into $n$ equal parts, with $h=\frac{b-a}{n}$ and nodes $x_k=a+kh$; then $$T_n=\frac{h}{2}\left[f\left(a\right)+f\left(b\right)+2\sum_{k=1}^{n-1}f\left(x_k\right)\right],$$ and the truncation error is $$R_T\left(f\right)=\int_a^b f\left(x\right)dx-T_n=-\frac{b-a}{12}h^2 f''\left(\xi\right),\ \xi\in\left(a,b\right).$$

> **Composite Simpson's Rule** (Formulas (7.31), (7.32)) <br>Divide $\left[a,b\right]$ into $n=2m$ equal parts, with step size $h=\frac{b-a}{n}$; then $$S_n=\frac{h}{3}\left[f\left(a\right)+f\left(b\right)+2\sum_{k=1}^{m-1}f\left(x_{2k}\right)+4\sum_{k=1}^{m}f\left(x_{2k-1}\right)\right],$$ and the truncation error is $$R_S\left(f\right)=\int_a^b f\left(x\right)dx-S_n=-\frac{b-a}{180}h^4 f^{\left(4\right)}\left(\xi\right),\ \xi\in\left(a,b\right).$$

> **Two-Point and Three-Point Derivative Formulas** (Formulas (7.9) through (7.12)) <br>For equally spaced nodes $x_0,x_1=x_0+h$ of step size $h$, the two-point formula is $f'\left(x_0\right)\approx\frac{f\left(x_1\right)-f\left(x_0\right)}{h}$ with truncation error $R_1\left(x_0\right)=-\frac{h}{2}f''\left(\xi\right)$; for nodes $x_0,x_1,x_2=x_0+2h$, the three-point central formula is $$f'\left(x_1\right)\approx\frac{f\left(x_2\right)-f\left(x_0\right)}{2h},$$ with truncation error $R_2\left(x_1\right)=-\frac{h^2}{6}f^{\left(3\right)}\left(\xi\right)$.

> **Successive Halving Algorithm for the Trapezoidal Rule** (Formula (7.34)) <br>Denote the trapezoidal value for a subdivision into $2^m$ equal parts by $T_{2^m}$; then the successive-halving recurrence is $$T_{2^m}=\frac{1}{2}T_{2^{m-1}}+\frac{b-a}{2^m}\sum_{k=1}^{2^{m-1}}f\left(a+\left(2k-1\right)\frac{b-a}{2^m}\right),$$ and the a posteriori error estimate is $\left|R\left(f,T_{2^m}\right)\right|\approx\frac{1}{3}\left|T_{2^m}-T_{2^{m-1}}\right|$; stop the computation when $\left|T_{2^m}-T_{2^{m-1}}\right|<3\varepsilon$.

> **Romberg Quadrature Formula** (Formula (7.41)) <br>By Richardson extrapolation, $$T_m^{\left(k\right)}=\frac{4^m T_{m-1}^{\left(k+1\right)}-T_{m-1}^{\left(k\right)}}{4^m-1},\ m=1,2,\dots,$$ the first column $T_0^{\left(k\right)}$ is the sequence of composite trapezoidal values, and the subsequent columns are successively Simpson, Cotes, and Romberg values, with the precision improving column by column.

> **Definition 7.2** (Gaussian Nodes and Gaussian Quadrature Formulas) <br>If $n$ nodes $x_1,\dots,x_n\in\left[a,b\right]$ make the weighted quadrature formula $\int_a^b \rho\left(x\right)f\left(x\right)dx\approx\sum_{k=1}^n A_k f\left(x_k\right)$ have algebraic degree of precision $2n-1$, then these nodes are called Gaussian nodes, and the formula is called a Gaussian quadrature formula with weight $\rho\left(x\right)$.

> **Theorem 7.4** (Relation Between Gaussian Nodes and Orthogonal Polynomials) <br>The nodes of a quadrature formula are Gaussian if and only if the function $w_n\left(x\right)=\prod_{k=1}^n\left(x-x_k\right)$ is orthogonal on $\left[a,b\right]$ with respect to the weight function $\rho\left(x\right)$ to every polynomial $p\left(x\right)$ of degree at most $n-1$, i.e. $$\int_a^b \rho\left(x\right)p\left(x\right)w_n\left(x\right)dx=0.$$

> **Gauss–Legendre Quadrature Formula** (Formula (7.57)) <br>The Gaussian quadrature formula on $\left[-1,1\right]$ using the zeros of the Legendre polynomials as nodes and weight function $\rho\left(x\right)=1$. For any finite interval $\left[a,b\right]$, make the change $x=\frac{b-a}{2}t+\frac{a+b}{2}$, so that $$\int_a^b f\left(x\right)dx=\frac{b-a}{2}\int_{-1}^1 f\left(\frac{b-a}{2}t+\frac{a+b}{2}\right)dt.$$

> **Composite Quadrature Formulas for Double Integrals** (Formulas (7.82), (7.83)) <br>For a double integral over a rectangular region $D=\left[a,b\right]\times\left[c,d\right]$, subdivide into $n$ equal parts in the $x$ direction and $m$ equal parts in the $y$ direction, with step sizes $h=\frac{b-a}{n}$ and $k=\frac{d-c}{m}$; the composite quadrature formula is the tensor product of the one-dimensional formulas in the two directions. The trapezoidal weights are $\omega^{\left(t\right)}=\left[\frac12,1,\dots,1,\frac12\right]$, and the Simpson weights are $\omega^{\left(s\right)}=\left[1,4,2,\dots,2,4,1\right]$.

### Problem 1 (Problem 7-3)

Let $f\left(x\right)=\frac{1}{\left(1+x\right)^2}$, take step size $h=0.1$, and use the two-point and three-point formulas respectively to compute $f'\left(0.5\right)$ and estimate the error.

### Solution to Problem 1

By **Two-Point and Three-Point Derivative Formulas** (Formulas (7.9) through (7.12)), take the nodes $x_0=0.5$, $x_1=0.6$, and first use the two-point formula to find $f'\left(0.5\right)$: $$
f'\left(0.5\right)\approx\frac{f\left(0.6\right)-f\left(0.5\right)}{0.1}=\frac{\frac{1}{1.6^2}-\frac{1}{1.5^2}}{0.1}=\frac{0.390625-0.444444}{0.1}=-0.538194.
$$

Its truncation error is $R_1\left(x_0\right)=-\frac{h}{2}f''\left(\xi\right)$. Since $f''\left(x\right)=\frac{6}{\left(1+x\right)^4}$, on $\left[0.5,0.6\right]$, $\max\left|f''\left(x\right)\right|=\frac{6}{1.5^4}=1.1852$, so

$$
\left|R_1\left(0.5\right)\right|\le\frac{0.1}{2}\times1.1852=0.0593.
$$

Next take the nodes $x_0=0.4$, $x_1=0.5$, $x_2=0.6$, and use the three-point central formula: $$
f'\left(0.5\right)\approx\frac{f\left(0.6\right)-f\left(0.4\right)}{2h}=\frac{0.390625-\frac{1}{1.4^2}}{0.2}=\frac{0.390625-0.510204}{0.2}=-0.597895.
$$

Its truncation error is $R_2\left(x_1\right)=-\frac{h^2}{6}f^{\left(3\right)}\left(\xi\right)$. Since $f^{\left(3\right)}\left(x\right)=-\frac{24}{\left(1+x\right)^5}$, on $\left[0.4,0.6\right]$, $\max\left|f^{\left(3\right)}\left(x\right)\right|=\frac{24}{1.4^5}=4.4631$, so

$$
\left|R_2\left(0.5\right)\right|\le\frac{0.1^2}{6}\times4.4631=0.00744.
$$

The exact value is $f'\left(0.5\right)=-\frac{2}{1.5^3}=-0.592593$; the two-point formula error is about $0.0544$ and the three-point formula error is about $0.0053$, consistent with the truncation error estimates; the three-point formula is clearly more accurate than the two-point formula. $\blacksquare$

### Problem 2 (Problem 7-4)

Use the trapezoidal rule and Simpson's rule respectively to compute approximations to the following integrals and estimate the errors: (1) $\int_0^1 e^{-x}dx$; (2) $\int_{0.1}^{0.5} e^{\frac{1}{x}}dx$. (Only part (2) is required.) ### Solution to Problem 2

Here $a=0.1$, $b=0.5$, $f\left(x\right)=e^{1/x}$. By **Theorem 7.2** (Error of the Trapezoidal Rule), the trapezoidal rule gives

$$
\int_{0.1}^{0.5} e^{1/x}dx\approx\frac{0.5-0.1}{2}\left[e^{10}+e^2\right]=0.2\left[22026.4658+7.3891\right]=4406.77.
$$

By **Theorem 7.3** (Error of Simpson's Rule), the midpoint is $\frac{0.1+0.5}{2}=0.3$, $e^{1/0.3}=28.0317$, so

$$
\int_{0.1}^{0.5} e^{1/x}dx\approx\frac{0.4}{6}\left[e^{10}+4e^{1/0.3}+e^2\right]=\frac{0.4}{6}\left[22026.4658+112.1268+7.3891\right]=1476.40.
$$

Estimate the truncation error. For $f\left(x\right)=e^{1/x}$, one computes

$$
f''\left(x\right)=e^{1/x}\left(\frac{1}{x^4}+\frac{2}{x^3}\right),\quad f^{\left(4\right)}\left(x\right)=e^{1/x}\left(\frac{1}{x^8}+\frac{12}{x^7}+\frac{36}{x^6}+\frac{24}{x^5}\right).
$$

Both attain their maximum on $\left[0.1,0.5\right]$ at $x=0.1$: $\max\left|f''\left(x\right)\right|=2.643\times10^8$, $\max\left|f^{\left(4\right)}\left(x\right)\right|=5.692\times10^{12}$. By **Theorem 7.2** and **Theorem 7.3**, $$
\left|R_T\right|\le\frac{\left(0.4\right)^3}{12}\times2.643\times10^8=1.41\times10^6,
$$

$$
\left|R_S\right|\le\frac{\left(0.4\right)^5}{2880}\times5.692\times10^{12}=2.02\times10^7.
$$

Since the integrand varies extremely rapidly near $x=0.1$, the truncation errors of the low-order trapezoidal and Simpson rules are both very large, and the approximations are far from the exact integral value (about $288.3$); this shows that low-order quadrature formulas should not be used directly for functions that vary rapidly. $\blacksquare$

### Problem 3 (Problem 7-8)

Find the approximate formula

$$
\int_0^1 f\left(x\right)dx\approx\frac{1}{3}\left[2f\left(\frac14\right)-f\left(\frac12\right)+2f\left(\frac34\right)\right]
$$

for its algebraic degree of precision.

### Solution to Problem 3

By **Definition 7.1** (Algebraic Degree of Precision), test successively with $f\left(x\right)=1,x,x^2,x^3,x^4$.

When $f\left(x\right)=1$, left side $=1$, right side $=\frac13\left(2-1+2\right)=1$, holds exactly; when $f\left(x\right)=x$, left side $=\frac12$, right side $=\frac13\left(2\cdot\frac14-\frac12+2\cdot\frac34\right)=\frac13\cdot\frac32=\frac12$, holds exactly; when $f\left(x\right)=x^2$, left side $=\frac13$, right side $=\frac13\left(2\cdot\frac1{16}-\frac14+2\cdot\frac9{16}\right)=\frac13\cdot1=\frac13$, holds exactly; when $f\left(x\right)=x^3$, left side $=\frac14$, right side $=\frac13\left(2\cdot\frac1{64}-\frac18+2\cdot\frac{27}{64}\right)=\frac13\cdot\frac34=\frac14$, holds exactly; when $f\left(x\right)=x^4$, left side $=\frac15=0.2$, right side $=\frac13\left(2\cdot\frac1{256}-\frac1{16}+2\cdot\frac{81}{256}\right)=\frac{37}{192}\approx0.19271$, does not hold exactly.

Thus the quadrature formula holds exactly for $f\left(x\right)=1,x,x^2,x^3$ but not for $x^4$; by **Definition 7.1**, it has algebraic degree of precision $3$. $\blacksquare$

### Problem 4 (Problem 7-10)

Use the composite trapezoidal rule and composite Simpson's rule respectively to compute approximations to the following integrals: (1) $\int_0^1 \frac{x}{1+x^2}dx,\ n=8$; (2) $\int_0^1 \frac{\ln\left(1+x\right)}{\left(1+x\right)^2}dx,\ n=4$. (Only part (1) is required.) ### Solution to Problem 4

Here $a=0$, $b=1$, $n=8$, step size $h=\frac18=0.125$, nodes $x_k=0.125k\ \left(k=0,1,\dots,8\right)$, integrand $f\left(x\right)=\frac{x}{1+x^2}$.

By **Composite Trapezoidal Rule** (Formula (7.29)), $$
T_8=\frac{0.125}{2}\left[f\left(0\right)+f\left(1\right)+2\sum_{k=1}^{7}f\left(0.125k\right)\right]=0.34527.
$$

By **Composite Simpson's Rule** (Formula (7.31)), $$
S_8=\frac{0.125}{3}\left[f\left(0\right)+f\left(1\right)+2\sum_{k=1}^{3}f\left(0.25k\right)+4\sum_{k=1}^{4}f\left(0.125\left(2k-1\right)\right)\right]=0.34658.
$$

The exact integral value is $\int_0^1\frac{x}{1+x^2}dx=\frac12\ln 2=0.34657$; the composite Simpson value $S_8=0.34658$ is closer to the exact value than the composite trapezoidal value $T_8=0.34527$. $\blacksquare$

### Problem 5 (Problem 7-11)

If the composite trapezoidal rule is used to compute the integral $\int_0^1 e^{-x^2}dx$, into how many equal parts must the interval be subdivided to ensure that the result has four significant digits (assuming no round-off error in the computation)? If the composite Simpson's rule is used, into how many equal parts should the interval be subdivided? ### Solution to Problem 5

The integral value is $I=\int_0^1 e^{-x^2}dx\approx0.7468$, $0<I<1$, and four significant digits requires the truncation error not to exceed $\frac12\times10^{-4}$.

First find bounds on the derivatives. $f\left(x\right)=e^{-x^2}$, $$
f''\left(x\right)=\left(4x^2-2\right)e^{-x^2},\quad f^{\left(4\right)}\left(x\right)=\left(12-48x^2+16x^4\right)e^{-x^2}.
$$

On $\left[0,1\right]$, $\max\left|f''\left(x\right)\right|=2$ (at $x=0$), $\max\left|f^{\left(4\right)}\left(x\right)\right|=12$ (at $x=0$).

With the composite trapezoidal rule, by the error in the **Composite Trapezoidal Rule** (Formula (7.30)), $$
\left|R_T\right|=\frac{1}{12}h^2\cdot2=\frac{h^2}{6}\le\frac12\times10^{-4},
$$

which gives $h^2\le3\times10^{-4}$, $h\le0.01732$, and hence $n=\frac{1}{h}\ge57.7$, i.e. one should subdivide into $n=58$ parts.

With the composite Simpson's rule, by the error in the **Composite Simpson's Rule** (Formula (7.32)), $$
\left|R_S\right|=\frac{1}{180}h^4\cdot12=\frac{h^4}{15}\le\frac12\times10^{-4},
$$

which gives $h^4\le7.5\times10^{-4}$, $h\le0.1655$, and hence $n=\frac{1}{h}\ge6.04$. Since Simpson's rule requires $n$ to be even, take $n=8$.

One sees that to attain the same precision, the composite Simpson's rule requires far fewer subdivisions than the composite trapezoidal rule. $\blacksquare$

### Problem 6 (Problem 7-12)

Given the function table

| $i$ | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 |
|---|---|---|---|---|---|---|---|---|---|
| $x_i$ | 0 | 0.125 | 0.25 | 0.375 | 0.5 | 0.625 | 0.75 | 0.875 | 1 |
| $f\left(x_i\right)$ | 1 | 0.997398 | 0.989616 | 0.976727 | 0.958851 | 0.936156 | 0.908852 | 0.877193 | 0.841471 |

compute an approximation to the integral $I=\int_0^1 f\left(x\right)dx$ and estimate the error.

### Solution to Problem 6

Here $n=8$, step size $h=0.125$. By **Composite Trapezoidal Rule** (Formula (7.29)), $$
T_8=\frac{0.125}{2}\left[f\left(x_0\right)+f\left(x_8\right)+2\sum_{k=1}^{7}f\left(x_k\right)\right]=0.945691.
$$

By **Composite Simpson's Rule** (Formula (7.31)), $$
S_8=\frac{0.125}{3}\left[f\left(x_0\right)+f\left(x_8\right)+2\sum_{k=1}^{3}f\left(x_{2k}\right)+4\sum_{k=1}^{4}f\left(x_{2k-1}\right)\right]=0.946084.
$$

This table corresponds to $f\left(x\right)=\frac{\sin x}{x}$, and the exact integral value is $I=0.9460831$. Comparison shows that $S_8=0.946084$ already has about $6$ significant digits, while $T_8=0.945691$ has an error of about $4\times10^{-4}$. By the **Composite Trapezoidal Rule** (Formula (7.30)) and **Composite Simpson's Rule** (Formula (7.32)), the composite Simpson error is $O\left(h^4\right)$ and the composite trapezoidal error is $O\left(h^2\right)$, so Simpson's rule is more accurate. $\blacksquare$

### Problem 7 (Problem 7-13)

Use the successive halving algorithm for the trapezoidal rule to compute the following integrals: (1) $\int_0^\pi \frac{dx}{x+\cos x}$; (2) $\int_0^1 \frac{dx}{1+x^3}$.

Require the error not to exceed $\varepsilon=3\times10^{-4}$. (Only part (1) is required.) ### Solution to Problem 7

Here $a=0$, $b=\pi$, $f\left(x\right)=\frac{1}{x+\cos x}$. By the **Successive Halving Algorithm for the Trapezoidal Rule** (Formula (7.34)), the initial value is $T_1=\frac{\pi}{2}\left[f\left(0\right)+f\left(\pi\right)\right]=2.3043$; successively halve to compute the trapezoidal value sequence, using the a posteriori error estimate $\left|R\right|\approx\frac13\left|T_{2^m}-T_{2^{m-1}}\right|$ to control precision, with the results: | $2^m$ | $T_{2^m}$ | $\lvert T_{2^m}-T_{2^{m-1}}\rvert$ |
|---|---|---|
| 1 | 2.3043 | -- |
| 2 | 2.1521 | 0.1521 |
| 4 | 2.0786 | 0.0736 |
| 8 | 2.0527 | 0.0258 |
| 16 | 2.0456 | 0.00720 |
| 32 | 2.0437 | 0.00186 |
| 64 | 2.0432 | 0.000470 |

When $2^m=64$, $\lvert T_{64}-T_{32}\rvert=0.000470<3\varepsilon=9\times10^{-4}$; by the stopping criterion of the **Successive Halving Algorithm for the Trapezoidal Rule**, at this point $\left|R\right|\approx\frac13\times0.000470=1.6\times10^{-4}<3\times10^{-4}$, meeting the precision requirement. Therefore

$$
\int_0^\pi \frac{dx}{x+\cos x}\approx T_{64}=2.0432.
$$

$\blacksquare$

### Problem 8 (Problem 7-15)

Use the Romberg method to compute an approximation to the integral $I=\int_0^1 e^{-x^2}dx$, requiring the error not to exceed $10^{-4}$.

### Solution to Problem 8

Here $a=0$, $b=1$, $f\left(x\right)=e^{-x^2}$. By the **Romberg Quadrature Formula** (Formula (7.41)), the first-column trapezoidal values are $T_1=\frac12\left[f\left(0\right)+f\left(1\right)\right]=0.683940$; successively halve and extrapolate by $T_m^{\left(k\right)}=\frac{4^m T_{m-1}^{\left(k+1\right)}-T_{m-1}^{\left(k\right)}}{4^m-1}$, giving the computation table: | $k$ | Trapezoidal $T_0^{\left(k\right)}$ | Simpson $T_1^{\left(k\right)}$ | Cotes $T_2^{\left(k\right)}$ | Romberg $T_3^{\left(k\right)}$ |
|---|---|---|---|---|
| 0 | 0.683940 | | | |
| 1 | 0.731370 | 0.747180 | | |
| 2 | 0.742984 | 0.746855 | 0.746834 | |
| 3 | 0.745866 | 0.746826 | 0.746824 | 0.746824 |

When extrapolating to $k=3$, the difference between the Romberg value $T_3^{\left(3\right)}=0.746824$ and the corresponding value in the previous row is already less than $10^{-4}$; by the stopping criterion of the **Romberg Quadrature Formula**, the precision requirement is met. Therefore

$$
\int_0^1 e^{-x^2}dx\approx0.7468,
$$

whose exact value is $0.7468241\cdots$. $\blacksquare$

### Problem 9 (Problem 7-16)

Determine the nodes and quadrature weights in the following formulas so that they have the highest possible algebraic degree of precision: (1) $\int_{-h}^{h}f\left(x\right)dx\approx A_1 f\left(-\frac h2\right)+A_2 f\left(0\right)+A_3 f\left(\frac h2\right)$; (2) $\int_0^2 f\left(x\right)dx\approx f\left(x_1\right)+f\left(x_2\right)$; (3) $\int_{-1}^{1}f\left(x\right)dx\approx A_1 f\left(x_1\right)+A_2 f\left(0\right)+f\left(1\right)$. (Only part (2) is required.) ### Solution to Problem 9

The formula is $\int_0^2 f\left(x\right)dx\approx f\left(x_1\right)+f\left(x_2\right)$, with the two quadrature weights already fixed at $1$ and the nodes $x_1,x_2$ to be determined. By **Definition 7.1** (Algebraic Degree of Precision), require the formula to hold exactly for $f\left(x\right)=1,x,x^2$.

When $f\left(x\right)=1$, left side $\int_0^2 1dx=2$, right side $=1+1=2$, automatically satisfied; when $f\left(x\right)=x$, left side $\int_0^2 xdx=2$, right side $=x_1+x_2$, so

$$
x_1+x_2=2.
$$

When $f\left(x\right)=x^2$, left side $\int_0^2 x^2dx=\frac83$, right side $=x_1^2+x_2^2$; using $x_1^2+x_2^2=\left(x_1+x_2\right)^2-2x_1x_2$,

$$
4-2x_1x_2=\frac83\ \Rightarrow\ x_1x_2=\frac23.
$$

Thus $x_1,x_2$ are the two roots of $t^2-2t+\frac23=0$, and solving gives

$$
x_{1,2}=1\pm\frac{1}{\sqrt3}.
$$

Check $f\left(x\right)=x^3$: left side $\int_0^2 x^3dx=4$, right side $=x_1^3+x_2^3=\left(x_1+x_2\right)^3-3x_1x_2\left(x_1+x_2\right)=8-3\cdot\frac23\cdot2=4$, holds exactly; then check $f\left(x\right)=x^4$: left side $\int_0^2 x^4dx=\frac{32}{5}=6.4$, right side $=x_1^4+x_2^4=\frac{56}{9}\approx6.222$, does not hold exactly.

Thus taking $x_1=1-\frac{1}{\sqrt3}$, $x_2=1+\frac{1}{\sqrt3}$, the formula has algebraic degree of precision $3$, attaining the highest precision for a two-node formula, $2n-1=3$. $\blacksquare$

### Problem 10 (Problem 7-16, continued)

(Only part (3) is required.) $$
\int_{-1}^{1}f\left(x\right)dx\approx A_1 f\left(x_1\right)+A_2 f\left(0\right)+f\left(1\right).
$$

### Solution to Problem 10

The three unknowns are $x_1,A_1,A_2$. By **Definition 7.1** (Algebraic Degree of Precision), require the formula to hold exactly for $f\left(x\right)=1,x,x^2$.

When $f\left(x\right)=1$, left side $\int_{-1}^1 1dx=2$, so

$$
A_1+A_2+1=2\ \Rightarrow\ A_1+A_2=1.
$$

When $f\left(x\right)=x$, left side $\int_{-1}^1 xdx=0$, so

$$
A_1 x_1+A_2\cdot0+1\cdot1=0\ \Rightarrow\ A_1 x_1=-1.
$$

When $f\left(x\right)=x^2$, left side $\int_{-1}^1 x^2dx=\frac23$, so

$$
A_1 x_1^2+A_2\cdot0+1\cdot1=\frac23\ \Rightarrow\ A_1 x_1^2=-\frac13.
$$

Dividing $A_1 x_1=-1$ by $A_1 x_1^2=-\frac13$ gives $x_1=\frac13$; substituting back gives $A_1=-3$, and then from $A_1+A_2=1$ gives $A_2=4$.

Check $f\left(x\right)=x^3$: left side $\int_{-1}^1 x^3dx=0$, right side $=A_1 x_1^3+A_2\cdot0+1=\left(-3\right)\cdot\frac1{27}+1=\frac89\ne0$, does not hold exactly.

Thus taking $x_1=\frac13$, $A_1=-3$, $A_2=4$, the formula has algebraic degree of precision $2$. $\blacksquare$

### Problem 11 (Problem 7-18)

Determine $x_1,x_2,A_1,A_2$ so that the quadrature formula

$$
\int_0^1 \sqrt{x}\,f\left(x\right)dx\approx A_1 f\left(x_1\right)+A_2 f\left(x_2\right)
$$

is a Gaussian quadrature formula.

### Solution to Problem 11

By **Definition 7.2** (Gaussian Nodes and Gaussian Quadrature Formulas), a two-node Gaussian formula should have algebraic degree of precision $2n-1=3$. By **Theorem 7.4** (Relation Between Gaussian Nodes and Orthogonal Polynomials), the node polynomial $w_2\left(x\right)=\left(x-x_1\right)\left(x-x_2\right)=x^2+px+q$ should be orthogonal to $1,x$ on $\left[0,1\right]$ with respect to the weight function $\rho\left(x\right)=\sqrt{x}$, i.e.

$$
\int_0^1 \sqrt{x}\left(x^2+px+q\right)dx=0,\quad \int_0^1 x\sqrt{x}\left(x^2+px+q\right)dx=0.
$$

Computing gives

$$
\frac{2}{7}+\frac{2p}{5}+\frac{2q}{3}=0,\quad \frac{2}{9}+\frac{2p}{7}+\frac{2q}{5}=0.
$$

Simplifying to

$$
\frac17+\frac p5+\frac q3=0,\quad \frac19+\frac p7+\frac q5=0,
$$

solves to $p=-\frac{10}{9}$, $q=\frac{5}{21}$. Thus

$$
w_2\left(x\right)=x^2-\frac{10}{9}x+\frac{5}{21},
$$

whose two roots are

$$
x_1=\frac{\frac{10}{9}-\sqrt{\left(\frac{10}{9}\right)^2-\frac{20}{21}}}{2}\approx0.28995,\quad x_2\approx0.82116.
$$

Then by **Definition 7.1**, require the formula to hold exactly for $f\left(x\right)=1,x$ to determine the weights: $$
A_1+A_2=\int_0^1\sqrt{x}dx=\frac23,\quad A_1 x_1+A_2 x_2=\int_0^1 x\sqrt{x}dx=\frac25,
$$

which solves to $A_1\approx0.27756$, $A_2\approx0.38911$. The formula now also holds exactly for $f\left(x\right)=x^2$, has algebraic degree of precision $3$, and is indeed a Gaussian quadrature formula. $\blacksquare$

### Problem 12 (Problem 7-21)

Use the three-point Gauss–Legendre quadrature formula to compute the integral

$$
I=\int_0^1 \frac{2\sin\left(2x-1\right)}{3-2x}dx.
$$

### Solution to Problem 12

By the **Gauss–Legendre Quadrature Formula** (Formula (7.57)), first make the interval change $x=\frac{t+1}{2}$; then $dx=\frac12 dt$, $2x-1=t$, $3-2x=2-t$, and hence

$$
I=\int_{-1}^1 \frac{2\sin t}{2-t}\cdot\frac12 dt=\int_{-1}^1 \frac{\sin t}{2-t}dt.
$$

The three-point Gauss–Legendre nodes are $t=0,\ \pm\sqrt{\frac35}=\pm0.77459667$, with corresponding weights $\frac89,\ \frac59,\ \frac59$. Substituting gives

$$
I\approx\frac59\cdot\frac{\sin\left(-0.7746\right)}{2+0.7746}+\frac89\cdot\frac{\sin0}{2}+\frac59\cdot\frac{\sin\left(0.7746\right)}{2-0.7746}.
$$

Computing each term: $\sin\left(\pm0.7746\right)=\pm0.6993$, so

$$
I\approx\frac59\left[-\frac{0.6993}{2.7746}+\frac{0.6993}{1.2254}\right]=\frac59\left[-0.2520+0.5707\right]=0.17705.
$$

The exact integral value is about $0.17758$, and the three-point Gauss–Legendre formula error is about $5\times10^{-4}$. $\blacksquare$

### Problem 13 (Problem 7-26)

Let $n=m=4$. Use the composite trapezoidal rule and composite Simpson's rule respectively to compute the double integral, and compare the results with the exact value: (1) $I=\int_{1.0}^{1.5}dx\int_{1.2}^{1.6}\ln\left(x+2y\right)dy$; (2) $I=\int_0^{0.5}dx\int_1^{1.6}\frac{1}{1+xy}dy$. (Only part (1) is required.) ### Solution to Problem 13

The integration region is the rectangle $D=\left[1.0,1.5\right]\times\left[1.2,1.6\right]$, with $x$-direction step size $h_x=\frac{0.5}{4}=0.125$ and nodes $x_i=1.0+0.125i$; $y$-direction step size $h_y=\frac{0.4}{4}=0.1$ and nodes $y_j=1.2+0.1j$; integrand $f\left(x,y\right)=\ln\left(x+2y\right)$.

By **Composite Quadrature Formulas for Double Integrals** (Formula (7.82)), the composite trapezoidal rule is the tensor product of the one-dimensional trapezoidal rules in the two directions: $$
T_{4,4}=h_xh_y\sum_{i=0}^4\sum_{j=0}^4\omega_i^{\left(t\right)}\omega_j^{\left(t\right)}f\left(x_i,y_j\right)=0.27923,
$$

where $\omega^{\left(t\right)}=\left[\frac12,1,1,1,\frac12\right]$.

By **Composite Quadrature Formulas for Double Integrals** (Formula (7.83)), the composite Simpson's rule is

$$
S_{4,4}=\frac{h_xh_y}{9}\sum_{i=0}^4\sum_{j=0}^4\omega_i^{\left(s\right)}\omega_j^{\left(s\right)}f\left(x_i,y_j\right)=0.27929,
$$

where $\omega^{\left(s\right)}=\left[1,4,2,4,1\right]$.

For the exact integral value, first integrate the inner integral: $\int_{1.2}^{1.6}\ln\left(x+2y\right)dy=\frac12\left.\left(u\ln u-u\right)\right|_{u=x+2.4}^{u=x+3.2}$, then integrate with respect to $x$, giving $I=0.27929$. One sees that the composite Simpson result $S_{4,4}=0.27929$ almost coincides with the exact value, while the composite trapezoidal result $T_{4,4}=0.27923$ has an error of about $6\times10^{-5}$. $\blacksquare$

### Problem 14 (Problem 7-27)

Let $n=m=4$. Derive an approximate quadrature formula for double integrals over a rectangular region using the composite trapezoidal rule in the $x$ direction and the composite Simpson's rule in the $y$ direction, and compute the integral in Problem 26.

### Solution to Problem 14

Let the rectangular region be $D=\left[a,b\right]\times\left[c,d\right]$, with the $x$ direction subdivided into $n$ equal parts (step size $h_x=\frac{b-a}{n}$, nodes $x_i=a+ih_x$) and the $y$ direction into $m$ equal parts (step size $h_y=\frac{d-c}{m}$, nodes $y_j=c+jh_y$). By **Composite Quadrature Formulas for Double Integrals** (Formulas (7.82), (7.83)), the double integral is the tensor product of the one-dimensional quadrature formulas in the two directions. If the composite trapezoidal rule is used in the $x$ direction (weights $\omega^{\left(t\right)}=\left[\frac12,1,\dots,1,\frac12\right]$) and the composite Simpson's rule in the $y$ direction (weights $\omega^{\left(s\right)}=\left[1,4,2,\dots,2,4,1\right]$), then the mixed quadrature formula is

$$
M_{n,m}=\frac{h_xh_y}{2\cdot3}\sum_{i=0}^n\sum_{j=0}^m\omega_i^{\left(t\right)}\omega_j^{\left(s\right)}f\left(x_i,y_j\right)
=\frac{h_xh_y}{6}\sum_{i=0}^n\sum_{j=0}^m\omega_i^{\left(t\right)}\omega_j^{\left(s\right)}f\left(x_i,y_j\right).
$$

Now compute the integral in Problem 26 (1), $I=\int_{1.0}^{1.5}dx\int_{1.2}^{1.6}\ln\left(x+2y\right)dy$, with $n=m=4$, $h_x=0.125$, $h_y=0.1$, $\omega^{\left(t\right)}=\left[\frac12,1,1,1,\frac12\right]$, $\omega^{\left(s\right)}=\left[1,4,2,4,1\right]$; substituting gives

$$
M_{4,4}=\frac{0.125\times0.1}{6}\sum_{i=0}^4\sum_{j=0}^4\omega_i^{\left(t\right)}\omega_j^{\left(s\right)}\ln\left(x_i+2y_j\right)=0.27927.
$$

This result lies between the composite trapezoidal $T_{4,4}=0.27923$ and the composite Simpson $S_{4,4}=0.27929$, with an error of about $2\times10^{-5}$ from the exact value $0.27929$. $\blacksquare$
