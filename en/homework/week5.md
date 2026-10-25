# Assignment 5

> **Definition 5.1** (The Interpolation Problem) <br>Given the values $y_i=f\left(x_i\right)$ of a function $f\left(x\right)$ at $n+1$ distinct nodes $x_0,x_1,\dots,x_n$ on an interval $\left[a,b\right]$, find a polynomial $P_n\left(x\right)$ of degree at most $n$ satisfying the interpolation conditions $P_n\left(x_i\right)=f\left(x_i\right)=y_i\ \left(i=0,1,\dots,n\right)$ at the given points; $P_n\left(x\right)$ is called the interpolation polynomial.

> **Theorem 5.1** (Interpolation Remainder) <br>Let $x_0,x_1,\dots,x_n$ be distinct nodes on $\left[a,b\right]$, and let $P_n\left(x\right)$ be the degree-$n$ interpolation polynomial through these nodes. If $f\left(x\right)$ is $n+1$ times continuously differentiable on $\left[a,b\right]$, then for any point $x$ in $\left[a,b\right]$, the interpolation remainder is $$R_n\left(x\right)=f\left(x\right)-P_n\left(x\right)=\frac{f^{\left(n+1\right)}\left(\xi\right)}{\left(n+1\right)!}\omega_{n+1}\left(x\right),\quad \xi\in\left(a,b\right),$$ where $\omega_{n+1}\left(x\right)=\prod_{j=0}^{n}\left(x-x_j\right)$.

> **Definition 5.3** (Lagrange Interpolation Polynomial) <br>The degree-$n$ polynomial satisfying $l_i\left(x_j\right)=\delta_{ij}$ (equal to $1$ when $i=j$ and $0$ otherwise) $$l_i\left(x\right)=\prod_{\substack{j=0\\j\ne i}}^{n}\frac{x-x_j}{x_i-x_j}\quad\left(i=0,1,\dots,n\right)$$ is called a Lagrange interpolation basis function, and $L_n\left(x\right)=\sum_{i=0}^{n}y_i l_i\left(x\right)$ is called the degree-$n$ Lagrange interpolation polynomial.

> **Definition 5.4** (Divided Differences and the Newton Interpolation Polynomial) <br>The quantity $f\left[x_i,x_j\right]=\frac{f\left(x_i\right)-f\left(x_j\right)}{x_i-x_j}$ is called the first divided difference of $f\left(x\right)$ with respect to the points $x_i,x_j$, and recursively $f\left[x_0,x_1,\dots,x_k\right]=\frac{f\left[x_1,\dots,x_k\right]-f\left[x_0,\dots,x_{k-1}\right]}{x_k-x_0}$ is called the $k$-th divided difference. This gives the Newton interpolation polynomial $$N_n\left(x\right)=f\left[x_0\right]+\left(x-x_0\right)f\left[x_0,x_1\right]+\left(x-x_0\right)\left(x-x_1\right)f\left[x_0,x_1,x_2\right]+\cdots+\left(x-x_0\right)\cdots\left(x-x_{n-1}\right)f\left[x_0,\dots,x_n\right].$$

> **Definition 5.6, Definition 5.7** (Forward Differences and Backward Differences) <br>For equally spaced nodes $x_k=x_0+kh$ ($h$ is the step size), $\Delta f_k=f_{k+1}-f_k$ is called the first forward difference and $\nabla f_k=f_k-f_{k-1}$ the first backward difference, with higher-order differences defined recursively. Setting $x=x_0+th$ gives the Newton forward-difference interpolation formula $$N_n\left(x_0+th\right)=f_0+t\Delta f_0+\frac{t\left(t-1\right)}{2!}\Delta^2f_0+\cdots+\frac{t\left(t-1\right)\cdots\left(t-n+1\right)}{n!}\Delta^nf_0;$$ setting $x=x_n+th$ gives the Newton backward-difference interpolation formula $$N_n\left(x_n+th\right)=f_n+t\nabla f_n+\frac{t\left(t+1\right)}{2!}\nabla^2f_n+\cdots+\frac{t\left(t+1\right)\cdots\left(t+n-1\right)}{n!}\nabla^nf_n.$$

> **Theorem 5.2** (Remainder of Piecewise Linear Interpolation) <br>If $f\left(x\right)$ is twice continuously differentiable on $\left[a,b\right]$, then the remainder of the piecewise linear interpolation function $p\left(x\right)$ satisfies the estimate $$\left|R\left(x\right)\right|=\left|f\left(x\right)-p\left(x\right)\right|\le\frac{h^2}{8}M,$$ where $h=\max\limits_{i}\left(x_{i+1}-x_i\right)$ and $M=\max\limits_{\left[a,b\right]}\left|f''\left(x\right)\right|$.

> **Definition 5.9** (Hermite Interpolation) <br>Given the values $y_i=f\left(x_i\right)$ of a function $f\left(x\right)$ at distinct nodes, and prescribed derivative values $y'_{i_k}=f'\left(x_{i_k}\right)$ at certain nodes $x_{i_k}$, a polynomial $H\left(x\right)$ satisfying both $H\left(x_i\right)=y_i$ and $H'\left(x_{i_k}\right)=y'_{i_k}$ is called a Hermite interpolation polynomial.

> **Theorem 5.5** (Remainder of Hermite Interpolation) <br>Suppose there are $n+1$ value nodes and $m+1$ derivative conditions (at the nodes $x_{i_0},\dots,x_{i_m}$). If $f\left(x\right)\in C^{n+m+2}\left[a,b\right]$, then for any $x\in\left[a,b\right]$, $$R\left(x\right)=f\left(x\right)-H\left(x\right)=\frac{f^{\left(n+m+2\right)}\left(\xi\right)}{\left(n+m+2\right)!}\omega_{n+1}\left(x\right)\prod_{k=0}^{m}\left(x-x_{i_k}\right),\quad \xi\in\left(a,b\right).$$

> **Definition 5.11** (Cubic Spline Interpolation) <br>Given the values $y_i=f\left(x_i\right)$ of $f\left(x\right)$ at nodes $a=x_0< x_1< \cdots< x_n=b$, if $S\left(x\right)$ satisfies $S\left(x_i\right)=y_i$, is a cubic polynomial on each subinterval $\left[x_i,x_{i+1}\right]$, and is twice continuously differentiable on $\left[a,b\right]$, then $S\left(x\right)$ is called a cubic spline interpolation function. Taking $M_i=S''\left(x_i\right)$ as parameters gives the three-moment equations $$\alpha_j M_{j-1}+2M_j+\beta_j M_{j+1}=C_j\quad\left(j=1,\dots,n-1\right),$$ where $\alpha_j=\frac{h_{j-1}}{h_{j-1}+h_j}$, $\beta_j=1-\alpha_j$, $C_j=\frac{1}{h_{j-1}+h_j}\left(\frac{y_{j+1}-y_j}{h_j}-\frac{y_j-y_{j-1}}{h_{j-1}}\right)$; the endpoint boundary conditions may be prescribed derivative values $S'\left(a\right)=m_0,\ S'\left(b\right)=m_n$ or prescribed second-derivative values $S''\left(a\right)=M_0,\ S''\left(b\right)=M_n$.

### Problem 1 (Problem 5-3)

Given the following function table: $x_i=1,\,3,\,4,\,6$; $f\left(x_i\right)=-7,\,5,\,8,\,14$. Find its degree-3 Lagrange interpolation polynomial and use it to compute an approximation to $f\left(2\right)$.

### Solution to Problem 1

By **Definition 5.3** (Lagrange Interpolation Polynomial), the four Lagrange interpolation basis functions at the nodes $x_0=1,\,x_1=3,\,x_2=4,\,x_3=6$ are respectively

$$
l_0\left(x\right)=\frac{\left(x-3\right)\left(x-4\right)\left(x-6\right)}{\left(1-3\right)\left(1-4\right)\left(1-6\right)}=-\frac{\left(x-3\right)\left(x-4\right)\left(x-6\right)}{30},
$$

$$
l_1\left(x\right)=\frac{\left(x-1\right)\left(x-4\right)\left(x-6\right)}{\left(3-1\right)\left(3-4\right)\left(3-6\right)}=\frac{\left(x-1\right)\left(x-4\right)\left(x-6\right)}{6},
$$

$$
l_2\left(x\right)=\frac{\left(x-1\right)\left(x-3\right)\left(x-6\right)}{\left(4-1\right)\left(4-3\right)\left(4-6\right)}=-\frac{\left(x-1\right)\left(x-3\right)\left(x-6\right)}{6},
$$

$$
l_3\left(x\right)=\frac{\left(x-1\right)\left(x-3\right)\left(x-4\right)}{\left(6-1\right)\left(6-3\right)\left(6-4\right)}=\frac{\left(x-1\right)\left(x-3\right)\left(x-4\right)}{30}.
$$

Therefore the desired degree-3 Lagrange interpolation polynomial is

$$
L_3\left(x\right)=-7l_0\left(x\right)+5l_1\left(x\right)+8l_2\left(x\right)+14l_3\left(x\right).
$$

Substituting $x=2$, the basis functions take the values

$$
l_0\left(2\right)=\frac{4}{15},\quad l_1\left(2\right)=\frac{4}{3},\quad l_2\left(2\right)=-\frac{2}{3},\quad l_3\left(2\right)=\frac{1}{15},
$$

and hence

$$
L_3\left(2\right)=-7\times\frac{4}{15}+5\times\frac{4}{3}+8\times\left(-\frac{2}{3}\right)+14\times\frac{1}{15}=\frac{2}{5}=0.4.
$$

Thus $f\left(2\right)\approx 0.4$. $\blacksquare$

### Problem 2 (Problem 5-7)

Let $x_0,x_1,\dots,x_n$ be $n+1$ distinct nodes, and let $l_j\left(x\right)\ \left(j=0,1,\dots,n\right)$ be the degree-$n$ Lagrange interpolation basis functions on these nodes. Prove: (1) $\sum\limits_{j=0}^{n}\left(x_j-x\right)^k l_j\left(x\right)\equiv 0\ \left(k=1,2,\dots,n\right)$; (2) let $P\left(x\right)$ be any polynomial of degree $n+1$ with leading coefficient $1$; then $P\left(x\right)-\sum\limits_{j=0}^{n}P\left(x_j\right)l_j\left(x\right)=\omega_{n+1}\left(x\right)=\prod\limits_{j=0}^{n}\left(x-x_j\right)$.

### Solution to Problem 2

First note a basic fact: for any polynomial $q\left(t\right)$ of degree at most $n$, its Lagrange interpolation polynomial at the nodes $x_0,\dots,x_n$ is itself, i.e. $q\left(t\right)=\sum_{j=0}^{n}q\left(x_j\right)l_j\left(t\right)$. This is because both sides are polynomials of degree at most $n$ and agree at the $n+1$ distinct nodes $t=x_i$; by the existence and uniqueness of the interpolation polynomial in **Definition 5.1** (The Interpolation Problem), the two are identically equal. (1) Regard $\left(t-x\right)^k$ as a polynomial in $t$ of degree $k$. When $k=1,2,\dots,n$ its degree is at most $n$, so by the above basic fact, $$
\left(t-x\right)^k=\sum_{j=0}^{n}\left(x_j-x\right)^k l_j\left(t\right).
$$

Setting $t=x$ on both sides, the left-hand side is $\left(x-x\right)^k=0$ ($k\ge1$), hence

$$
\sum_{j=0}^{n}\left(x_j-x\right)^k l_j\left(x\right)\equiv 0.
$$ (2) Let $L\left(x\right)=\sum_{j=0}^{n}P\left(x_j\right)l_j\left(x\right)$; it is a polynomial of degree at most $n$, and $L\left(x_i\right)=P\left(x_i\right)$ ($i=0,1,\dots,n$). Thus $P\left(x\right)-L\left(x\right)$ is a polynomial of degree $n+1$ (with leading coefficient $1$) having $x_0,x_1,\dots,x_n$ as all its roots, and therefore

$$
P\left(x\right)-L\left(x\right)=C\prod_{j=0}^{n}\left(x-x_j\right).
$$

Comparing the leading coefficients on both sides, the leading coefficient on the left is $1$, so $C=1$, i.e.

$$
P\left(x\right)-\sum_{j=0}^{n}P\left(x_j\right)l_j\left(x\right)=\prod_{j=0}^{n}\left(x-x_j\right)=\omega_{n+1}\left(x\right).\ \blacksquare
$$

### Problem 3 (Problem 5-8)

Given the following function table: $x_i=1.615,\,1.634,\,1.702,\,1.828$; $f\left(x_i\right)=2.414\,50,\,2.462\,59,\,2.652\,71,\,3.030\,35$. Find its degree-3 Newton interpolation polynomial and use it to compute an approximation to $f\left(1.682\right)$.

### Solution to Problem 3

By **Definition 5.4** (Divided Differences and the Newton Interpolation Polynomial), construct the divided-difference table recursively. First divided differences: $$
f\left[x_0,x_1\right]=\frac{2.462\,59-2.414\,50}{1.634-1.615}=2.531\,05,
$$

$$
f\left[x_1,x_2\right]=\frac{2.652\,71-2.462\,59}{1.702-1.634}=2.795\,88,\quad
f\left[x_2,x_3\right]=\frac{3.030\,35-2.652\,71}{1.828-1.702}=2.997\,14.
$$

Second divided differences: $$
f\left[x_0,x_1,x_2\right]=\frac{2.795\,88-2.531\,05}{1.702-1.615}=3.044\,02,
$$

$$
f\left[x_1,x_2,x_3\right]=\frac{2.997\,14-2.795\,88}{1.828-1.634}=1.037\,43.
$$

Third divided difference: $$
f\left[x_0,x_1,x_2,x_3\right]=\frac{1.037\,43-3.044\,02}{1.828-1.615}=-9.420\,63.
$$

Therefore the degree-3 Newton interpolation polynomial is

$$
N_3\left(x\right)=2.414\,50+2.531\,05\left(x-1.615\right)+3.044\,02\left(x-1.615\right)\left(x-1.634\right)-9.420\,63\left(x-1.615\right)\left(x-1.634\right)\left(x-1.702\right).
$$

Substituting $x=1.682$, where $x-1.615=0.067$, $x-1.634=0.048$, $x-1.702=-0.020$, gives

$$
\begin{aligned}
N_3\left(1.682\right)&=2.414\,50+2.531\,05\times0.067+3.044\,02\times0.067\times0.048-9.420\,63\times0.067\times0.048\times\left(-0.020\right)\\
&=2.414\,50+0.169\,58+0.009\,79+0.000\,61\\
&=2.594\,48.
\end{aligned}
$$

Thus $f\left(1.682\right)\approx 2.594\,48$. $\blacksquare$

### Problem 4 (Problem 5-10)

Given the following function table: $x_i=1,\,2,\,3,\,4$; $f\left(x_i\right)=3,\,5,\,9,\,15$. Use the Newton forward and backward interpolation formulas respectively to compute approximations to $f\left(1.5\right)$ and $f\left(3.7\right)$.

### Solution to Problem 4

The nodes are equally spaced with step size $h=1$. By **Definition 5.6, Definition 5.7** (Forward Differences and Backward Differences), construct the difference table: forward differences $\Delta f_0=5-3=2$, $\Delta f_1=9-5=4$, $\Delta f_2=15-9=6$, $\Delta^2f_0=4-2=2$, $\Delta^2f_1=6-4=2$, $\Delta^3f_0=0$; backward differences $\nabla f_3=6$, $\nabla^2f_3=2$, $\nabla^3f_3=0$.

For $f\left(1.5\right)$, which is near the head of the table $x_0=1$, use the Newton forward-difference formula. Let $x=1.5=x_0+th$; then $t=\frac{1.5-1}{1}=0.5$, so

$$
N_3\left(1.5\right)=f_0+t\Delta f_0+\frac{t\left(t-1\right)}{2!}\Delta^2f_0=3+0.5\times2+\frac{0.5\times\left(-0.5\right)}{2}\times2=3+1-0.25=3.75.
$$

For $f\left(3.7\right)$, which is near the tail of the table $x_3=4$, use the Newton backward-difference formula. Let $x=3.7=x_3+th$; then $t=\frac{3.7-4}{1}=-0.3$, so

$$
N_3\left(3.7\right)=f_3+t\nabla f_3+\frac{t\left(t+1\right)}{2!}\nabla^2f_3=15+\left(-0.3\right)\times6+\frac{\left(-0.3\right)\times0.7}{2}\times2=15-1.8-0.21=12.99.
$$

Thus $f\left(1.5\right)\approx 3.75$, $f\left(3.7\right)\approx 12.99$. $\blacksquare$

### Problem 5 (Problem 5-12)

On $\left[0,\pi/2\right]$, a table of equally spaced values of $f\left(x\right)=\sin x$ is given. To ensure that when piecewise linear interpolation is used to compute sine values at non-node points, the truncation error does not exceed $10^{-6}$, at least what step size should the table use? If piecewise quadratic interpolation is used instead, what step size should be used? ### Solution to Problem 5

For $f\left(x\right)=\sin x$, $f''\left(x\right)=-\sin x$, and on $\left[0,\pi/2\right]$, $\max\left|f''\left(x\right)\right|=1$.

First consider piecewise linear interpolation. By **Theorem 5.2** (Remainder of Piecewise Linear Interpolation), the truncation error satisfies

$$
\left|R\left(x\right)\right|\le\frac{h^2}{8}\max\left|f''\left(x\right)\right|=\frac{h^2}{8}.
$$

Requiring $\frac{h^2}{8}\le10^{-6}$ gives

$$
h\le\sqrt{8\times10^{-6}}=2\sqrt{2}\times10^{-3}\approx0.00283.
$$

Next consider piecewise quadratic interpolation. Here $f'''\left(x\right)=-\cos x$, and on $\left[0,\pi/2\right]$, $\max\left|f'''\left(x\right)\right|=1$. On three adjacent equally spaced nodes $x_{i-1},x_i,x_{i+1}$ (spacing $h$), do quadratic interpolation; by **Theorem 5.1** (Interpolation Remainder), $$
R\left(x\right)=\frac{f'''\left(\xi\right)}{3!}\left(x-x_{i-1}\right)\left(x-x_i\right)\left(x-x_{i+1}\right).
$$

Let $x=x_i+sh$ ($s\in\left[-1,1\right]$); then $\left(x-x_{i-1}\right)\left(x-x_i\right)\left(x-x_{i+1}\right)=h^3 s\left(s^2-1\right)$, whose maximum absolute value on $\left[-1,1\right]$ is $\frac{2}{3\sqrt{3}}$ (attained at $s=\pm\frac{1}{\sqrt{3}}$). Thus

$$
\left|R\left(x\right)\right|\le\frac{1}{6}\times\frac{2}{3\sqrt{3}}h^3=\frac{h^3}{9\sqrt{3}}.
$$

Requiring $\frac{h^3}{9\sqrt{3}}\le10^{-6}$ gives

$$
h\le\sqrt\left[3\right]{9\sqrt{3}\times10^{-6}}\approx0.0250.
$$

Therefore, for piecewise linear interpolation the step size should be $h\le0.00283$; for piecewise quadratic interpolation the step size should be $h\le0.0250$. $\blacksquare$

### Problem 6 (Problem 5-16)

Given the function table: $x_i=0,\,1,\,2$; $f\left(x_i\right)=1,\,2,\,1$; $f'\left(x_i\right)$ is not prescribed at $x=0$, and at $x=1,\,2$ it is respectively $0,\,-1$. It is also known that $f\left(x\right)$ is five times continuously differentiable on $\left[0,2\right]$. Find the degree-4 Hermite interpolation polynomial $H_4\left(x\right)$ of $f\left(x\right)$, and write out the expression for the remainder $f\left(x\right)-H_4\left(x\right)$.

### Solution to Problem 6

The interpolation conditions are $H\left(0\right)=1$, $H\left(1\right)=2$, $H\left(2\right)=1$, $H'\left(1\right)=0$, $H'\left(2\right)=-1$, totaling $5$ conditions, which uniquely determine a degree-4 polynomial. By **Definition 5.9** (Hermite Interpolation), first use Lagrange interpolation to find the degree-2 interpolation polynomial $P_2\left(x\right)$ satisfying the three value conditions: $$
P_2\left(x\right)=-x^2+2x+1.
$$

Let the desired degree-4 Hermite interpolation polynomial be

$$
H_4\left(x\right)=P_2\left(x\right)+\left(ax+b\right)\,x\left(x-1\right)\left(x-2\right),
$$

where the second term vanishes at the nodes $0,1,2$ and does not affect the value conditions. Differentiating gives

$$
H_4'\left(x\right)=-2x+2+a\left(x^3-3x^2+2x\right)+\left(ax+b\right)\left(3x^2-6x+2\right).
$$

Substituting $H_4'\left(1\right)=0$: here $x^3-3x^2+2x=0$, $3x^2-6x+2=-1$, so $H_4'\left(1\right)=-\left(a+b\right)=0$, i.e. $a+b=0$. Substituting $H_4'\left(2\right)=-1$: here $x^3-3x^2+2x=0$, $3x^2-6x+2=2$, so $H_4'\left(2\right)=-2+2\left(2a+b\right)=-1$, i.e. $2a+b=\frac12$. Solving jointly gives $a=\frac12$, $b=-\frac12$. Therefore

$$
H_4\left(x\right)=-x^2+2x+1+\frac12 x\left(x-1\right)^2\left(x-2\right).
$$

Here the value nodes are $0,1,2$ ($n=2$), and the derivative conditions are imposed at the nodes $1,2$ (totaling $m+1=2$, $m=1$). By **Theorem 5.5** (Remainder of Hermite Interpolation), and since $f\left(x\right)\in C^5\left[0,2\right]$, the remainder is

$$
f\left(x\right)-H_4\left(x\right)=\frac{f^{\left(5\right)}\left(\xi\right)}{5!}\,x\left(x-1\right)\left(x-2\right)\,\left(x-1\right)\left(x-2\right)=\frac{f^{\left(5\right)}\left(\xi\right)}{120}\,x\left(x-1\right)^2\left(x-2\right)^2,\quad \xi\in\left(0,2\right).\ \blacksquare
$$

### Problem 7 (Problem 5-17)

Given the following function table: $x_i=0,\,1,\,2,\,3$; $y_i=0,\,0,\,0,\,0$. The boundary conditions are (1) $m_0=1,\ m_3=0$; (2) $M_0=1,\ M_3=0$. Find the cubic spline interpolation function in each case.

### Solution to Problem 7

The nodes are equally spaced with $h=1$, and all $y_i=0$. By **Definition 5.11** (Cubic Spline Interpolation), in the three-moment equations

$$
\alpha_j=\beta_j=\frac{1}{2},\quad C_j=\frac{1}{h_{j-1}+h_j}\left(\frac{y_{j+1}-y_j}{h_j}-\frac{y_j-y_{j-1}}{h_{j-1}}\right)=0.
$$

**(1) Boundary condition $m_0=S'\left(0\right)=1$, $m_3=S'\left(3\right)=0$** (prescribed derivative values at both ends). The endpoint derivative conditions give the supplementary equations

$$
2M_0+M_1=6\left(\frac{y_1-y_0}{h_0}-m_0\right)=-6,\quad M_2+2M_3=6\left(m_3-\frac{y_3-y_2}{h_2}\right)=0.
$$

Together with the internal equations

$$
\frac12 M_0+2M_1+\frac12 M_2=0,\quad \frac12 M_1+2M_2+\frac12 M_3=0
$$

solving jointly gives $M_0=-\frac{52}{15}$, $M_1=\frac{14}{15}$, $M_2=-\frac{4}{15}$, $M_3=\frac{2}{15}$. From the piecewise expression of the cubic spline (taking $h=1$, $y_i=0$), $$
S_j\left(x\right)=\frac{M_j}{6}\left(x_{j+1}-x\right)^3+\frac{M_{j+1}}{6}\left(x-x_j\right)^3-\frac{M_j}{6}\left(x_{j+1}-x\right)-\frac{M_{j+1}}{6}\left(x-x_j\right),
$$

simplifying gives

$$
S_0\left(x\right)=\frac{x\left(1-x\right)\left(15-11x\right)}{15},\quad x\in\left[0,1\right],
$$

$$
S_1\left(x\right)=\frac{\left(x-1\right)\left(2-x\right)\left(3x-7\right)}{15},\quad x\in\left[1,2\right],
$$

$$
S_2\left(x\right)=\frac{\left(x-2\right)\left(3-x\right)^2}{15},\quad x\in\left[2,3\right].
$$

**(2) Boundary condition $M_0=S''\left(0\right)=1$, $M_3=S''\left(3\right)=0$** (prescribed second-derivative values at both ends). Substituting into the internal equations

$$
\frac12 M_0+2M_1+\frac12 M_2=0,\quad \frac12 M_1+2M_2+\frac12 M_3=0,
$$

gives $M_1=-\frac{4}{15}$, $M_2=\frac{1}{15}$. Similarly simplifying gives the piecewise expression

$$
S_0\left(x\right)=\frac{x\left(1-x\right)\left(19x-26\right)}{90},\quad x\in\left[0,1\right],
$$

$$
S_1\left(x\right)=\frac{\left(x-1\right)\left(2-x\right)\left(12-5x\right)}{90},\quad x\in\left[1,2\right],
$$

$$
S_2\left(x\right)=\frac{\left(x-2\right)\left(3-x\right)\left(x-4\right)}{90},\quad x\in\left[2,3\right].\ \blacksquare
$$
