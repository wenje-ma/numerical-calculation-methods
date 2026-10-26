# Numerical Calculation Methods

## Introduction and Significant Digits

**Definition 1.1** (Absolute Error and Error Bound)

Let $x^{*}$ be an approximation to the exact value $x$. The quantity $e\left(x^{*}\right)=x-x^{*}$ is called the absolute error of the approximation $x^{*}$, or error for short. In general the exact value is hard to obtain, and hence the exact value of the absolute error $e\left(x^{*}\right)$ cannot be computed; however, from the measuring instrument or the computation one can estimate the range of its possible values, namely an upper bound $\varepsilon$ on the absolute value of the error:

$$
\left|e\left(x^{*}\right)\right|=\left|x-x^{*}\right|\le\varepsilon.
$$

Then $\varepsilon$ is called the absolute error bound of the approximation $x^{*}$, or error bound for short.

**Definition 1.2** (Relative Error and Relative Error Bound)

Let $x^{*}$ be an approximation to the exact value $x$. The ratio of the absolute error to the exact value is called the relative error of the approximation $x^{*}$, denoted $e_r\left(x^{*}\right)$, that is

$$
e_r\left(x^{*}\right)=\frac{e\left(x^{*}\right)}{x}=\frac{x-x^{*}}{x}.
$$

Since the exact value $x$ is always unknown in the computation, the relative error is generally taken to be

$$
e_r\left(x^{*}\right)=\frac{e\left(x^{*}\right)}{x^{*}}.
$$

Similarly, only an upper bound on the relative error can be estimated. If there exists a positive number $\varepsilon_r$ such that

$$
\left|e_r\left(x^{*}\right)\right|=\left|\frac{e\left(x^{*}\right)}{x^{*}}\right|\le\varepsilon_r,
$$

then $\varepsilon_r$ is called the relative error bound of $x^{*}$.

**Definition 1.3** (Significant Digits)

If the error bound of the approximation $x^{*}$ is $\frac{1}{2}\times10^{-n}$, then $x^{*}$ is said to be accurate to the $n$-th decimal place, and all digits from the first nonzero digit up to this place are called significant digits. In general, if the normalized form of the approximation $x^{*}$ is

$$
x^{*}=\pm0.a_1a_2\cdots a_n\cdots\times10^{m},
$$

where $m$ is an integer, $a_1\ne0$, and each $a_i\left(i=1,2,\dots\right)$ is an integer between $0$ and $9$, and

$$
\left|x-x^{*}\right|\le\frac{1}{2}\times10^{m-n},
$$

then the approximation $x^{*}$ is said to have $n$ significant digits.

**Theorem 1.1** (Relation Between the Relative Error Bound and Significant Digits)

If the approximation $x^{*}=\pm0.a_1a_2\cdots a_n\times10^{m}\left(a_1\ne0\right)$ of $x$ has $n$ significant digits, then $\frac{1}{2a_1}\times10^{-n+1}$ is its relative error bound. Conversely, if the relative error bound $\varepsilon_r$ of $x^{*}$ satisfies $\varepsilon_r\le\frac{1}{2}\times10^{-n}$, then $x^{*}$ has at least $n$ significant digits.

**Error Propagation** (Error Estimation in Basic Operations)

Suppose the solution obtained in numerical computation depends on the parameters $x_1,x_2,\dots,x_n$, denoted $y=f\left(x_1,x_2,\dots,x_n\right)$, and let the approximation of the parameter $x_i$ be $x_i^{*}$. Assuming $f$ is differentiable at $\left(x_1^{*},x_2^{*},\dots,x_n^{*}\right)$, then when the parameter errors are small, the absolute error and relative error of the solution are respectively

$$
e\left(y^{*}\right)\approx\sum_{i=1}^n\frac{\partial f\left(x_1^{*},x_2^{*},\dots,x_n^{*}\right)}{\partial x_i}e\left(x_i^{*}\right),
$$

$$
e_r\left(y^{*}\right)\approx\sum_{i=1}^n\frac{\partial f\left(x_1^{*},x_2^{*},\dots,x_n^{*}\right)}{\partial x_i}\frac{x_i^{*}}{f\left(x_1^{*},x_2^{*},\dots,x_n^{*}\right)}e_r\left(x_i^{*}\right).
$$

In particular, the above formulas give the error formulas for sums, differences, products and quotients:

$$
\begin{cases}e\left(x_1\pm x_2\right)=e\left(x_1\right)\pm e\left(x_2\right),\\e_r\left(x_1\pm x_2\right)\approx\frac{x_1}{x_1\pm x_2}e_r\left(x_1\right)\pm\frac{x_2}{x_1\pm x_2}e_r\left(x_2\right),\end{cases}
$$

$$
\begin{cases}e\left(x_1x_2\right)\approx x_2e\left(x_1\right)+x_1e\left(x_2\right),\\e_r\left(x_1x_2\right)\approx e_r\left(x_1\right)+e_r\left(x_2\right),\end{cases}
$$

$$
\begin{cases}e\left(\frac{x_1}{x_2}\right)\approx\frac{1}{x_2}e\left(x_1\right)-\frac{x_1}{x_2^2}e\left(x_2\right),\\e_r\left(\frac{x_1}{x_2}\right)\approx e_r\left(x_1\right)-e_r\left(x_2\right).\end{cases}
$$

Therefore, the error bound of a sum or difference does not exceed the sum of the error bounds of the individual numbers, and the relative error bound of a product or quotient does not exceed the sum of the relative error bounds of the individual numbers.

**1.4 Issues to Note in Numerical Computation** (Avoid Subtracting Two Nearly Equal Numbers)

By **Error Propagation**, the relative error of the difference $u=x-y$ of two numbers is

$$
e_r\left(u\right)\approx\frac{x}{x-y}e_r\left(x\right)-\frac{y}{x-y}e_r\left(y\right).
$$

When $x$ and $y$ are very close, $\left|x-y\right|$ is very small and the relative error of $u$ is very large, causing a serious loss of significant digits. To avoid this situation, the computational formula is often changed.

## Direct Methods for Solving Systems of Linear Equations

**Algorithm 2.1** (Gaussian Elimination)

The augmented matrix of the system is eliminated column by column into an equivalent upper-triangular system, which is then solved by back substitution in reverse order of the variables. At the $k$-th step take $a_{kk}^{\left(k\right)}\ne0$ as the pivot, with multipliers $l_{ik}=a_{ik}^{\left(k\right)}/a_{kk}^{\left(k\right)}$; the back-substitution formula is

$$
x_n=\frac{b_n^{\left(n\right)}}{a_{nn}^{\left(n\right)}},\quad x_k=\frac{b_k^{\left(k\right)}-\sum_{j=k+1}^{n}a_{kj}^{\left(k\right)}x_j}{a_{kk}^{\left(k\right)}}\ \left(k=n-1,\dots,1\right).
$$

To suppress the growth of round-off errors caused by small pivots, one may choose the element of largest absolute value in the $k$-th column (column pivoting) or among all remaining elements (complete pivoting), perform the corresponding row (column) swap, and then eliminate.

**Theorem 2.1** (Existence and Uniqueness of Direct Triangular Decomposition)

Let $A$ be a square matrix of order $n$. If all leading principal minors $\det A_i\ \left(i=1,2,\dots,n-1\right)$ of $A$ are nonzero, then $A$ has a unique Doolittle decomposition $A=LU$, where $L$ is a unit lower-triangular matrix and $U$ is an upper-triangular matrix. Then solving $Ax=b$ is equivalent to successively solving

$$
Ly=b,\quad Ux=y.
$$

**Formula (2.10)** (Compact-Format Triangular Decomposition Formulas)

In the order "1st row, 1st column, 2nd row, 2nd column, ...", comparing $A=LU$ gives

$$
u_{1j}=a_{1j},\quad l_{i1}=\frac{a_{i1}}{u_{11}},\quad u_{rj}=a_{rj}-\sum_{k=1}^{r-1}l_{rk}u_{kj},\quad l_{ir}=\frac{a_{ir}-\sum_{k=1}^{r-1}l_{ik}u_{kr}}{u_{rr}}.
$$

When solving, append the right-hand side vector $b$ at the end; following the same compact format, first do forward substitution to find $y$, then back substitute via $x_k=\left(y_k-\sum_{j=k+1}^{n}u_{kj}x_j\right)/u_{kk}$ to find $x$.

**Theorem 2.4** (Cholesky Decomposition of Symmetric Positive-Definite Matrices)

Let $A$ be a symmetric positive-definite matrix. Then there exists a unique lower-triangular matrix $L$ with positive diagonal entries such that $A=LL^{\mathrm T}$, namely the square-root method. Comparing $A=LL^{\mathrm T}$ gives

$$
l_{kk}=\left(a_{kk}-\sum_{j=1}^{k-1}l_{kj}^{2}\right)^{1/2},\quad l_{ik}=\frac{a_{ik}-\sum_{j=1}^{k-1}l_{ij}l_{kj}}{l_{kk}}.
$$

Solving $Ax=b$ reduces to successively solving $Ly=b$ and $L^{\mathrm T}x=y$. Alternatively, $A$ can be decomposed as $A=LDL^{\mathrm T}$ (the improved square-root method, where $L$ is unit lower-triangular and $D$ is diagonal), so that no square roots are needed in the computation.

**Definition 2.1** (Tridiagonal Systems)

The nonzero entries of the coefficient matrix $A$ lie only on the main diagonal and the two adjacent sub-diagonals:

$$
A=\begin{bmatrix}b_1&c_1&&\\a_2&b_2&c_2&\\&\ddots&\ddots&\ddots\\&&a_n&b_n\end{bmatrix}.
$$

**Theorem 2.3** (Thomas Algorithm) When $A$ satisfies the row diagonal dominance condition, it can be decomposed as $A=LU$, where $u_1=b_1$, $l_i=a_i/u_{i-1}$, $u_i=b_i-c_{i-1}l_i$; the "forward sweep" (forward substitution) is $y_1=d_1$, $y_k=d_k-l_k y_{k-1}$, and the "backward sweep" (back substitution) is

$$
x_n=\frac{y_n}{u_n},\quad x_k=\frac{y_k-c_k x_{k+1}}{u_k}\ \left(k=n-1,\dots,1\right).
$$

**Theorem 2.5** (Operator Norm of a Matrix)

The matrix norm induced by a vector norm is $\left\|A\right\|=\max_{\left\|x\right\|=1}\left\|Ax\right\|$, and it satisfies the compatibility condition $\left\|Ax\right\|\le\left\|A\right\|\left\|x\right\|$. The commonly used 1-norm (column norm) and $\infty$-norm (row norm) are

$$
\left\|A\right\|_1=\max_{1\le j\le n}\sum_{i=1}^{n}\left|a_{ij}\right|,\quad \left\|A\right\|_\infty=\max_{1\le i\le n}\sum_{j=1}^{n}\left|a_{ij}\right|.
$$

**Definition 2.4** (Condition Number of a Matrix)

For a nonsingular matrix $A$, the quantity $\mathrm{cond}\left(A\right)=\left\|A\right\|\,\left\|A^{-1}\right\|$ is called the condition number of $A$; in particular

$$
\mathrm{cond}\left(A\right)_1=\left\|A\right\|_1\left\|A^{-1}\right\|_1,\quad \mathrm{cond}\left(A\right)_\infty=\left\|A\right\|_\infty\left\|A^{-1}\right\|_\infty.
$$

The larger the condition number, the more "ill-conditioned" the system $Ax=b$ is with respect to perturbations of the right-hand side or the coefficient matrix, and always $\mathrm{cond}\left(A\right)\ge1$.

## Iterative Methods

**Jacobi Iteration** (Formula (3.12))

Let the coefficient matrix $A$ of the system $Ax=b$ be split as $A=D-L-U$, where

$$
D=\mathrm{diag}\left(a_{11},a_{22},\dots,a_{nn}\right).
$$

Then the Jacobi iteration scheme is

$$
x^{\left(k+1\right)}=Bx^{\left(k\right)}+g,\quad B=I-D^{-1}A,\quad g=D^{-1}b,
$$

whose component form is

$$
x_i^{\left(k+1\right)}=\frac{1}{a_{ii}}\left(b_i-\sum_{j\ne i}a_{ij}x_j^{\left(k\right)}\right),\ i=1,2,\dots,n.
$$

**Gauss–Seidel Iteration** (Formula (3.15))

In Jacobi iteration, as soon as a new component $x_i^{\left(k+1\right)}$ is computed it is immediately used in the computation of the subsequent components; this gives the Gauss–Seidel iteration, whose matrix form is

$$
x^{\left(k+1\right)}=\left(D-L\right)^{-1}Ux^{\left(k\right)}+\left(D-L\right)^{-1}b,
$$

with iteration matrix $M=\left(D-L\right)^{-1}U$.

**Relaxation Iteration (Successive Over-Relaxation)** (Formula (3.17))

Introducing a relaxation factor $\omega$ into the Gauss–Seidel iteration gives

$$
x^{\left(k+1\right)}=\left(D-\omega L\right)^{-1}\left[\left(1-\omega\right)D+\omega U\right]x^{\left(k\right)}+\omega\left(D-\omega L\right)^{-1}b,
$$

the iteration matrix is

$$
M_{\omega}=\left(D-\omega L\right)^{-1}\left[\left(1-\omega\right)D+\omega U\right];
$$

when $\omega=1$, this is exactly the Gauss–Seidel iteration.

**Definition 3.3** (Spectral Radius)

Let $A$ be a square matrix of order $n$ and let $\lambda_i\left(i=1,2,\dots,n\right)$ be the eigenvalues of $A$. The maximum of the absolute values of the eigenvalues is called the spectral radius of the matrix $A$, denoted

$$
\rho\left(A\right)=\max_{1\le i\le n}\left|\lambda_i\right|.
$$

**Theorem 3.6** (Necessary and Sufficient Condition for Convergence of Iterative Methods)

For any initial vector $x^{\left(0\right)}$ and right-hand side $g$, the vector sequence generated by the iteration $x^{\left(k+1\right)}=Mx^{\left(k\right)}+g$ converges if and only if

$$
\rho\left(M\right)< 1.
$$

**Definition 3.4** (Diagonally Dominant Matrix)

If a square matrix $A=\left(a_{ij}\right)$ of order $n$ satisfies

$$
\left|a_{ii}\right|\ge\sum_{j\ne i}\left|a_{ij}\right|\quad\left(i=1,2,\dots,n\right),
$$

and at least one $i$ satisfies the strict inequality, then $A$ is called a weakly diagonally dominant matrix; if the strict inequality holds for all $i$, then $A$ is called a strictly diagonally dominant matrix.

**Some Commonly Used Sufficient Convergence Conditions** (Convergence Criteria)

For the system $Ax=b$: (1) if $A$ is strictly diagonally dominant (or irreducibly and weakly diagonally dominant), then both Jacobi and Gauss–Seidel iteration converge; (2) if $A$ is symmetric positive-definite and $0< \omega< 2$, then the relaxation method converges (this condition is necessary and sufficient).

## Eigenvalue Computation

**Power Method** (Finding the Dominant Eigenvalue and Eigenvector)

Let the eigenvalues of the $n\times n$ real matrix $A$ satisfy $\left|\lambda_1\right|> \left|\lambda_2\right|\ge\cdots\ge\left|\lambda_n\right|$, with corresponding linearly independent eigenvectors $u_1,u_2,\dots,u_n$. Take an initial vector $\alpha^{\left(0\right)}\ne0$ and generate a vector sequence by the iteration $\alpha^{\left(k+1\right)}=A\alpha^{\left(k\right)}$ (Formula (4.1)); when $k$ is sufficiently large, $\alpha^{\left(k+1\right)}$ serves as an approximation to the eigenvector corresponding to $\lambda_1$, and

$$
\lambda_1\approx\frac{\alpha_i^{\left(k+1\right)}}{\alpha_i^{\left(k\right)}}
$$

(Formula (4.3)). To avoid overflow or underflow during iteration, each step is normalized in practice:

$$
\alpha^{\left(k+1\right)}=Ay^{\left(k\right)},\quad y^{\left(k+1\right)}=\frac{\alpha^{\left(k+1\right)}}{\max_i\left|\alpha_i^{\left(k+1\right)}\right|},\quad\lambda_1\approx\max_i\left|\alpha_i^{\left(k+1\right)}\right|
$$

(Formula (4.5)). The convergence rate is determined by the convergence factor $\left|\lambda_2/\lambda_1\right|$; the smaller its value, the faster the convergence.

**Aitken Acceleration of the Power Method** (Algorithm 4.2)

If the sequence $\left\{a_k\right\}$ of eigenvalue approximations produced by the power method converges linearly to $a$, i.e. $\lim_{k\to\infty}\frac{a_{k+1}-a}{a_k-a}=c\ne1$, then for $k$ sufficiently large

$$
\widehat a_k=a_k-\frac{\left(a_{k+1}-a_k\right)^2}{a_{k+2}-2a_{k+1}+a_k}
$$

converges to $a$ faster than $\left\{a_k\right\}$; applying it to the sequence produced by the power method accelerates convergence.

**Inverse Power Method** (Formula (4.10), Algorithm 4.3)

If $\lambda,u$ are an eigenvalue and eigenvector of $A$, then $A^{-1}u=\frac{1}{\lambda}u$; that is, the eigenvalues of $A^{-1}$ are the reciprocals of those of $A$, while the eigenvectors remain unchanged. In practice one solves the system

$$
A\alpha^{\left(k+1\right)}=\alpha^{\left(k\right)}
$$

(Formula (4.10)) in place of $\alpha^{\left(k+1\right)}=A^{-1}\alpha^{\left(k\right)}$. If an approximation $\lambda^*$ to an eigenvalue $\lambda$ of $A$ is known, applying the inverse power method to $A-\lambda^*I$ converges rapidly, since $\lambda-\lambda^*$ is the eigenvalue of smallest modulus of $A-\lambda^*I$; after normalization one obtains a component $\beta\approx\frac{1}{\lambda-\lambda^*}$, so that $\lambda\approx\lambda^*+\frac{1}{\beta}$, and the resulting $\alpha^{\left(k\right)}$ is the corresponding eigenvector.

**Jacobi Method** (Formula (4.12), Formula (4.13), Theorem 4.1)

Any real symmetric matrix $A$ of order $n$ can be reduced to a diagonal matrix by an orthogonal similarity transformation; that is, there exists an orthogonal matrix $Q$ such that

$$
Q^{\mathrm T}AQ=\mathrm{diag}\left(\lambda_1,\lambda_2,\dots,\lambda_n\right),
$$

the diagonal entries are all the eigenvalues of $A$, and the columns of $Q$ are the corresponding eigenvectors. Take a plane-rotation matrix $V_{ij}\left(\varphi\right)$ (Formula (4.12), rotating by angle $\varphi$ in the $\left(i,j\right)$ coordinate plane), and choose

$$
\tan2\varphi=\frac{2a_{ij}}{a_{ii}-a_{jj}}
$$

so that after the transformation $a_{ij}^{\left(1\right)}=0$ (Formula (4.13)). Repeating these rotations, by **Theorem 4.1** the sum of squares of the off-diagonal entries tends to zero and the matrix tends to a diagonal matrix whose diagonal entries are all the eigenvalues of $A$.

## Interpolation

**Definition 5.1** (The Interpolation Problem)

Given the values $y_i=f\left(x_i\right)$ of a function $f\left(x\right)$ at $n+1$ distinct nodes $x_0,x_1,\dots,x_n$ on an interval $\left[a,b\right]$, find a polynomial $P_n\left(x\right)$ of degree at most $n$ satisfying the interpolation conditions $P_n\left(x_i\right)=f\left(x_i\right)=y_i\ \left(i=0,1,\dots,n\right)$ at the given points; $P_n\left(x\right)$ is called the interpolation polynomial.

**Theorem 5.1** (Interpolation Remainder)

Let $x_0,x_1,\dots,x_n$ be distinct nodes on $\left[a,b\right]$, and let $P_n\left(x\right)$ be the degree-$n$ interpolation polynomial through these nodes. If $f\left(x\right)$ is $n+1$ times continuously differentiable on $\left[a,b\right]$, then for any point $x$ in $\left[a,b\right]$, the interpolation remainder is

$$
R_n\left(x\right)=f\left(x\right)-P_n\left(x\right)=\frac{f^{\left(n+1\right)}\left(\xi\right)}{\left(n+1\right)!}\omega_{n+1}\left(x\right),\quad \xi\in\left(a,b\right),
$$

where $\omega_{n+1}\left(x\right)=\prod_{j=0}^{n}\left(x-x_j\right)$.

**Definition 5.3** (Lagrange Interpolation Polynomial)

The degree-$n$ polynomial satisfying $l_i\left(x_j\right)=\delta_{ij}$ (equal to $1$ when $i=j$ and $0$ otherwise)

$$
l_i\left(x\right)=\prod_{\substack{j=0\\j\ne i}}^{n}\frac{x-x_j}{x_i-x_j}\quad\left(i=0,1,\dots,n\right)
$$

is called a Lagrange interpolation basis function, and $L_n\left(x\right)=\sum_{i=0}^{n}y_i l_i\left(x\right)$ is called the degree-$n$ Lagrange interpolation polynomial.

**Definition 5.4** (Divided Differences and the Newton Interpolation Polynomial)

The quantity $f\left[x_i,x_j\right]=\frac{f\left(x_i\right)-f\left(x_j\right)}{x_i-x_j}$ is called the first divided difference of $f\left(x\right)$ with respect to the points $x_i,x_j$, and recursively

$$
f\left[x_0,x_1,\dots,x_k\right]=\frac{f\left[x_1,\dots,x_k\right]-f\left[x_0,\dots,x_{k-1}\right]}{x_k-x_0}
$$

is called the $k$-th divided difference. This gives the Newton interpolation polynomial

$$
N_n\left(x\right)=f\left[x_0\right]+\left(x-x_0\right)f\left[x_0,x_1\right]+\left(x-x_0\right)\left(x-x_1\right)f\left[x_0,x_1,x_2\right]+\cdots+\left(x-x_0\right)\cdots\left(x-x_{n-1}\right)f\left[x_0,\dots,x_n\right].
$$

**Definition 5.6, Definition 5.7** (Forward Differences and Backward Differences)

For equally spaced nodes $x_k=x_0+kh$ ($h$ is the step size), $\Delta f_k=f_{k+1}-f_k$ is called the first forward difference and $\nabla f_k=f_k-f_{k-1}$ the first backward difference, with higher-order differences defined recursively. Setting $x=x_0+th$ gives the Newton forward-difference interpolation formula

$$
N_n\left(x_0+th\right)=f_0+t\Delta f_0+\frac{t\left(t-1\right)}{2!}\Delta^2f_0+\cdots+\frac{t\left(t-1\right)\cdots\left(t-n+1\right)}{n!}\Delta^nf_0;
$$

Setting $x=x_n+th$ gives the Newton backward-difference interpolation formula

$$
N_n\left(x_n+th\right)=f_n+t\nabla f_n+\frac{t\left(t+1\right)}{2!}\nabla^2f_n+\cdots+\frac{t\left(t+1\right)\cdots\left(t+n-1\right)}{n!}\nabla^nf_n.
$$

**Theorem 5.2** (Remainder of Piecewise Linear Interpolation)

If $f\left(x\right)$ is twice continuously differentiable on $\left[a,b\right]$, then the remainder of the piecewise linear interpolation function $p\left(x\right)$ satisfies the estimate

$$
\left|R\left(x\right)\right|=\left|f\left(x\right)-p\left(x\right)\right|\le\frac{h^2}{8}M,
$$

where $h=\max\limits_{i}\left(x_{i+1}-x_i\right)$ and $M=\max\limits_{\left[a,b\right]}\left|f''\left(x\right)\right|$.

**Definition 5.9** (Hermite Interpolation)

Given the values $y_i=f\left(x_i\right)$ of a function $f\left(x\right)$ at distinct nodes, and prescribed derivative values $y'_{i_k}=f'\left(x_{i_k}\right)$ at certain nodes $x_{i_k}$, a polynomial $H\left(x\right)$ satisfying both $H\left(x_i\right)=y_i$ and $H'\left(x_{i_k}\right)=y'_{i_k}$ is called a Hermite interpolation polynomial.

**Theorem 5.5** (Remainder of Hermite Interpolation)

Suppose there are $n+1$ value nodes and $m+1$ derivative conditions (at the nodes $x_{i_0},\dots,x_{i_m}$). If $f\left(x\right)\in C^{n+m+2}\left[a,b\right]$, then for any $x\in\left[a,b\right]$,

$$
R\left(x\right)=f\left(x\right)-H\left(x\right)=\frac{f^{\left(n+m+2\right)}\left(\xi\right)}{\left(n+m+2\right)!}\omega_{n+1}\left(x\right)\prod_{k=0}^{m}\left(x-x_{i_k}\right),\quad \xi\in\left(a,b\right).
$$

**Definition 5.11** (Cubic Spline Interpolation)

Given the values $y_i=f\left(x_i\right)$ of $f\left(x\right)$ at nodes $a=x_0< x_1< \cdots< x_n=b$, if $S\left(x\right)$ satisfies $S\left(x_i\right)=y_i$, is a cubic polynomial on each subinterval $\left[x_i,x_{i+1}\right]$, and is twice continuously differentiable on $\left[a,b\right]$, then $S\left(x\right)$ is called a cubic spline interpolation function. Taking $M_i=S''\left(x_i\right)$ as parameters gives the three-moment equations

$$
\alpha_j M_{j-1}+2M_j+\beta_j M_{j+1}=C_j\quad\left(j=1,\dots,n-1\right),
$$

where $\alpha_j=\frac{h_{j-1}}{h_{j-1}+h_j}$, $\beta_j=1-\alpha_j$, $C_j=\frac{1}{h_{j-1}+h_j}\left(\frac{y_{j+1}-y_j}{h_j}-\frac{y_j-y_{j-1}}{h_{j-1}}\right)$; the endpoint boundary conditions may be prescribed derivative values $S'\left(a\right)=m_0,\ S'\left(b\right)=m_n$ or prescribed second-derivative values $S''\left(a\right)=M_0,\ S''\left(b\right)=M_n$.

## Function Approximation

**General Form of the Linear Least-Squares Method** (Formulas (6.7)–(6.9))

For a data set $\left(x_i,y_i\right)\left(i=1,2,\dots,n\right)$, take a set of linearly independent functions on $\left[a,b\right]$

$$
\varphi_k\left(x\right)\left(k=0,1,\dots,m\right),
$$

and find $p\left(x\right)=\sum_{k=0}^m a_k\varphi_k\left(x\right)$ that minimizes the weighted sum of squared residuals $\sum_{i=1}^n w_i\left[y_i-p\left(x_i\right)\right]^2$. The coefficients satisfy the normal equations

$$
\sum_{k=0}^m a_k\left(\varphi_k,\varphi_j\right)=\left(y,\varphi_j\right)\quad\left(j=0,1,\dots,m\right),\quad\left(\varphi_k,\varphi_j\right)=\sum_{i=1}^n w_i\varphi_k\left(x_i\right)\varphi_j\left(x_i\right),\quad\left(y,\varphi_j\right)=\sum_{i=1}^n w_i y_i\varphi_j\left(x_i\right).
$$

In particular, taking $\varphi_k\left(x\right)=x^k$ gives polynomial fitting; for a linear fit $y=a_0+a_1x$ ($w_i=1$), the normal equations are

$$
\begin{cases}n a_0+a_1\sum\limits_{i=1}^n x_i=\sum\limits_{i=1}^n y_i,\\a_0\sum\limits_{i=1}^n x_i+a_1\sum\limits_{i=1}^n x_i^2=\sum\limits_{i=1}^n x_i y_i.\end{cases}
$$

**Linearization of Nonlinear Fitting** (6.1.2 Exponential Fitting, 6.1.3 Fractional Linear Fitting)

For the exponential form $y=ae^{bx}$, taking logarithms on both sides gives $\ln y=\ln a+bx$; first perform a linear fit on the transformed data set $\left(x_i,\ln y_i\right)$ according to the **General Form of the Linear Least-Squares Method**, then take exponentials to recover. For the separable fractional form $y=\frac{x}{ax+b}$, taking reciprocals on both sides gives $\frac{1}{y}=a+b\frac{1}{x}$; first perform a linear fit on the data set $\left(\frac{1}{x_i},\frac{1}{y_i}\right)$, then take reciprocals to recover.

**Definition 6.2** (Orthogonal Function System)

If a function system $\left\{\varphi_k\left(x\right)\right\}$ on $\left[a,b\right]$ satisfies

$$
\left(\varphi_j,\varphi_k\right)=\int_a^b w\left(x\right)\varphi_j\left(x\right)\varphi_k\left(x\right)\,\mathrm dx=0\ \left(j\ne k\right)
$$

and $\left(\varphi_k,\varphi_k\right)> 0$, then it is called an orthogonal function system on $\left[a,b\right]$ with respect to the weight function $w\left(x\right)$, where $\left(\varphi,\psi\right)=\int_a^b w\left(x\right)\varphi\left(x\right)\psi\left(x\right)\,\mathrm dx$ is called the inner product of the functions.

**Definition 6.3** (Best Least-Squares Approximation Function)

Let $f\left(x\right)$ be continuous on $\left[a,b\right]$, and let

$$
H=\operatorname{Span}\left\{\varphi_0,\varphi_1,\dots,\varphi_m\right\},
$$

If $p\left(x\right)=\sum_{k=0}^m a_k\varphi_k\left(x\right)$ makes

$$
\int_a^b w\left(x\right)\left[f\left(x\right)-p\left(x\right)\right]^2\,\mathrm dx
$$

minimal, then $p\left(x\right)$ is called the best least-squares approximation function to $f\left(x\right)$ in $H$ with respect to the weight function $w\left(x\right)$.

**Normal Equations for Best Least-Squares Approximation** (Formulas (6.32), (6.35), (6.36))

By **Definition 6.3**, the coefficients $a_k$ satisfy the normal equations

$$
\sum_{k=0}^m a_k\left(\varphi_k,\varphi_j\right)=\left(f,\varphi_j\right)\ \left(j=0,1,\dots,m\right),
$$

where $\left(f,\varphi_j\right)=\int_a^b w\left(x\right)f\left(x\right)\varphi_j\left(x\right)\,\mathrm dx$. If $\left\{\varphi_k\right\}$ is an orthogonal function system, the equations are diagonalized and the solution is $a_k=\frac{\left(f,\varphi_k\right)}{\left(\varphi_k,\varphi_k\right)}$, so that the best least-squares approximation function is $p\left(x\right)=\sum_{k=0}^m\frac{\left(f,\varphi_k\right)}{\left(\varphi_k,\varphi_k\right)}\varphi_k\left(x\right)$.

**Legendre Polynomials** (Formulas (6.18), (6.19))

The first few are $P_0\left(x\right)=1$, $P_1\left(x\right)=x$, $P_2\left(x\right)=\frac{3x^2-1}{2}$, $P_3\left(x\right)=\frac{5x^3-3x}{2}$. They form an orthogonal polynomial system on $\left[-1,1\right]$ with weight $w\left(x\right)\equiv1$, with $\left(P_n,P_m\right)=0\ \left(n\ne m\right)$ and $\left(P_n,P_n\right)=\frac{2}{2n+1}$. When used on an interval $\left[a,b\right]$, make the change of variable $t=\frac{2x-\left(b+a\right)}{b-a}$ and take $\varphi_k\left(x\right)=P_k\left(t\right)$.

## Numerical Differentiation and Numerical Integration

**Definition 7.1** (Algebraic Degree of Precision)

If, whenever $f\left(x\right)$ is any polynomial of degree at most $m$, the quadrature formula

$$
\int_a^b f\left(x\right)dx\approx\sum_{k=0}^n A_k f\left(x_k\right)
$$

holds exactly, but does not hold exactly for some polynomial of degree $m+1$, then the quadrature formula is said to have algebraic degree of precision $m$.

**Theorem 7.2** (Error of the Trapezoidal Rule)

If $f\left(x\right)\in C^{\left(2\right)}\left[a,b\right]$, then the truncation error of the trapezoidal rule is

$$
R_1\left(f\right)=\int_a^b f\left(x\right)dx-\frac{b-a}{2}\left[f\left(a\right)+f\left(b\right)\right]=-\frac{\left(b-a\right)^3}{12}f''\left(\xi\right),\ \xi\in\left(a,b\right).
$$

**Theorem 7.3** (Error of Simpson's Rule)

If $f\left(x\right)\in C^{\left(4\right)}\left[a,b\right]$, then the truncation error of Simpson's rule is

$$
R_2\left(f\right)=\int_a^b f\left(x\right)dx-\frac{b-a}{6}\left[f\left(a\right)+4f\left(\frac{a+b}{2}\right)+f\left(b\right)\right]=-\frac{\left(b-a\right)^5}{2880}f^{\left(4\right)}\left(\xi\right)=-\frac{h^5}{90}f^{\left(4\right)}\left(\xi\right),\ \xi\in\left(a,b\right),
$$

where $h=b-a$.

**Composite Trapezoidal Rule** (Formulas (7.29), (7.30))

Divide $\left[a,b\right]$ into $n$ equal parts, with $h=\frac{b-a}{n}$ and nodes $x_k=a+kh$; then

$$
T_n=\frac{h}{2}\left[f\left(a\right)+f\left(b\right)+2\sum_{k=1}^{n-1}f\left(x_k\right)\right],
$$

the truncation error is

$$
R_T\left(f\right)=\int_a^b f\left(x\right)dx-T_n=-\frac{b-a}{12}h^2 f''\left(\xi\right),\ \xi\in\left(a,b\right).
$$

**Composite Simpson's Rule** (Formulas (7.31), (7.32))

Divide $\left[a,b\right]$ into $n=2m$ equal parts, with step size $h=\frac{b-a}{n}$; then

$$
S_n=\frac{h}{3}\left[f\left(a\right)+f\left(b\right)+2\sum_{k=1}^{m-1}f\left(x_{2k}\right)+4\sum_{k=1}^{m}f\left(x_{2k-1}\right)\right],
$$

the truncation error is

$$
R_S\left(f\right)=\int_a^b f\left(x\right)dx-S_n=-\frac{b-a}{180}h^4 f^{\left(4\right)}\left(\xi\right),\ \xi\in\left(a,b\right).
$$

**Two-Point and Three-Point Derivative Formulas** (Formulas (7.9) through (7.12))

For equally spaced nodes $x_0,x_1=x_0+h$ of step size $h$, the two-point formula is $f'\left(x_0\right)\approx\frac{f\left(x_1\right)-f\left(x_0\right)}{h}$ with truncation error $R_1\left(x_0\right)=-\frac{h}{2}f''\left(\xi\right)$; for nodes $x_0,x_1,x_2=x_0+2h$, the three-point central formula is

$$
f'\left(x_1\right)\approx\frac{f\left(x_2\right)-f\left(x_0\right)}{2h},
$$

with truncation error $R_2\left(x_1\right)=-\frac{h^2}{6}f^{\left(3\right)}\left(\xi\right)$.

**Successive Halving Algorithm for the Trapezoidal Rule** (Formula (7.34))

Denote the trapezoidal value for a subdivision into $2^m$ equal parts by $T_{2^m}$; then the successive-halving recurrence is

$$
T_{2^m}=\frac{1}{2}T_{2^{m-1}}+\frac{b-a}{2^m}\sum_{k=1}^{2^{m-1}}f\left(a+\left(2k-1\right)\frac{b-a}{2^m}\right),
$$

and the a posteriori error estimate is

$$
\left|R\left(f,T_{2^m}\right)\right|\approx\frac{1}{3}\left|T_{2^m}-T_{2^{m-1}}\right|,
$$

Stop the computation when $\left|T_{2^m}-T_{2^{m-1}}\right|< 3\varepsilon$.

**Romberg Quadrature Formula** (Formula (7.41))

By Richardson extrapolation,

$$
T_m^{\left(k\right)}=\frac{4^m T_{m-1}^{\left(k+1\right)}-T_{m-1}^{\left(k\right)}}{4^m-1},\ m=1,2,\dots,
$$

the first column $T_0^{\left(k\right)}$ is the sequence of composite trapezoidal values, and the subsequent columns are successively Simpson, Cotes, and Romberg values, with the precision improving column by column.

**Definition 7.2** (Gaussian Nodes and Gaussian Quadrature Formulas)

If $n$ nodes $x_1,\dots,x_n\in\left[a,b\right]$ make the weighted quadrature formula

$$
\int_a^b \rho\left(x\right)f\left(x\right)dx\approx\sum_{k=1}^n A_k f\left(x_k\right)
$$

have algebraic degree of precision $2n-1$, then these nodes are called Gaussian nodes, and the formula is called a Gaussian quadrature formula with weight $\rho\left(x\right)$.

**Theorem 7.4** (Relation Between Gaussian Nodes and Orthogonal Polynomials)

The nodes of a quadrature formula are Gaussian if and only if the function $w_n\left(x\right)=\prod_{k=1}^n\left(x-x_k\right)$ is orthogonal on $\left[a,b\right]$ with respect to the weight function $\rho\left(x\right)$ to every polynomial $p\left(x\right)$ of degree at most $n-1$, i.e.

$$
\int_a^b \rho\left(x\right)p\left(x\right)w_n\left(x\right)dx=0.
$$

**Gauss–Legendre Quadrature Formula** (Formula (7.57))

The Gaussian quadrature formula on $\left[-1,1\right]$ using the zeros of the Legendre polynomials as nodes and weight function $\rho\left(x\right)=1$. For any finite interval $\left[a,b\right]$, make the change $x=\frac{b-a}{2}t+\frac{a+b}{2}$, so that

$$
\int_a^b f\left(x\right)dx=\frac{b-a}{2}\int_{-1}^1 f\left(\frac{b-a}{2}t+\frac{a+b}{2}\right)dt.
$$

**Composite Quadrature Formulas for Double Integrals** (Formulas (7.82), (7.83))

For a double integral over a rectangular region $D=\left[a,b\right]\times\left[c,d\right]$, subdivide into $n$ equal parts in the $x$ direction and $m$ equal parts in the $y$ direction, with step sizes $h=\frac{b-a}{n}$ and $k=\frac{d-c}{m}$; the composite quadrature formula is the tensor product of the one-dimensional formulas in the two directions. The trapezoidal weights are $\omega^{\left(t\right)}=\left[\frac12,1,\dots,1,\frac12\right]$, and the Simpson weights are $\omega^{\left(s\right)}=\left[1,4,2,\dots,2,4,1\right]$.

## Methods for Nonlinear Equations

**Definition 8.1** (Iterative Methods and Fixed-Point Iteration)

Rewrite the equation $f\left(x\right)=0$ in the equivalent form $x=\varphi\left(x\right)$, choose an initial value $x_0$, and use the iteration formula

$$
x_{n+1}=\varphi\left(x_n\right)\ \left(n=0,1,2,\dots\right)
$$

to generate the sequence $\left\{x_n\right\}$; if $x_n\to x^{*}$, then $x^{*}=\varphi\left(x^{*}\right)$ is called a fixed point of $\varphi\left(x\right)$, and the above method is called an iterative method (fixed-point iteration).

**Theorem 8.2** (Convergence Conditions for Fixed-Point Iteration)

Suppose the function $\varphi\left(x\right)$ satisfies on $\left[a,b\right]$: (1) for any $x\in\left[a,b\right]$, $\varphi\left(x\right)\in\left[a,b\right]$; (2) there exists a constant $0< L< 1$ such that for any $x\in\left[a,b\right]$, $\left|\varphi'\left(x\right)\right|\le L$. Then the equation $x=\varphi\left(x\right)$ has a unique root $x^{*}$ on $\left[a,b\right]$, and for any initial value $x_0\in\left[a,b\right]$, the iteration sequence $x_{n+1}=\varphi\left(x_n\right)$ converges to $x^{*}$, with the a posteriori error estimate

$$
\left|x^{*}-x_n\right|\le\frac{L}{1-L}\left|x_n-x_{n-1}\right|.
$$

**Definition 8.2** (Order of Convergence of an Iterative Method)

Let the sequence $\left\{x_n\right\}$ converge to $x^{*}$. If there exist positive numbers $r$ and $a$ such that

$$
\lim_{n\to\infty}\frac{\left|x_{n+1}-x^{*}\right|}{\left|x_n-x^{*}\right|^{r}}=a
$$

holds (when $r=1$ it is required that $a< 1$), then the sequence $\left\{x_n\right\}$ is said to converge with order $r$; $r=1$ is called linear convergence and $r=2$ quadratic convergence.

**Theorem 8.4** (Relation Between the Order of Convergence and the Derivatives of the Iteration Function)

Suppose the iteration function $\varphi\left(x\right)$ has $r$ continuous derivatives near $x^{*}$ $\left(r\ge2\right)$, and

$$
x^{*}=\varphi\left(x^{*}\right),\quad\varphi'\left(x^{*}\right)=\varphi''\left(x^{*}\right)=\dots=\varphi^{\left(r-1\right)}\left(x^{*}\right)=0,
$$

but $\varphi^{\left(r\right)}\left(x^{*}\right)\ne0$, then the iteration sequence $\left\{x_n\right\}$ converges with order $r$; if $x^{*}=\varphi\left(x^{*}\right)$ and $0< \left|\varphi'\left(x^{*}\right)\right|< 1$, then $\left\{x_n\right\}$ converges linearly.

**Newton Iteration** (Tangent Method, Formula (8.16))

Linearizing the nonlinear equation near the root gives the iteration formula

$$
x_{n+1}=x_n-\frac{f\left(x_n\right)}{f'\left(x_n\right)}.
$$

**Theorem 8.5** (Local Convergence of Newton's Method) states: when $f'\left(x^{*}\right)\ne0$ (i.e. $x^{*}$ is a simple root), Newton's method converges at least quadratically near $x^{*}$; when $x^{*}$ is an $r$-fold root, Newton's method degenerates to linear convergence, and its improved scheme is

$$
x_{n+1}=x_n-r\frac{f\left(x_n\right)}{f'\left(x_n\right)}\quad\left(n=0,1,2,\dots\right)
$$

(Formula (8.17)), which converges at least quadratically.

**Secant Method** (Chord Method, Formula (8.19))

Replacing the derivative by a divided difference gives the two-step iteration formula

$$
x_{n+1}=x_n-\frac{f\left(x_n\right)\left(x_n-x_{n-1}\right)}{f\left(x_n\right)-f\left(x_{n-1}\right)}\quad\left(n=1,2,\dots\right).
$$
