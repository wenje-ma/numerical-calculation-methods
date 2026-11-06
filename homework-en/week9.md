# week9

> **Definition 2.1 (Tridiagonal System)**
> 
> The nonzero entries of the coefficient matrix $A$ lie only on the main diagonal and the two adjacent subdiagonals: $A=\begin{bmatrix}b_1&c_1&&\\a_2&b_2&c_2&\\&\ddots&\ddots&\ddots\\&&a_n&b_n\end{bmatrix}$.

> **Theorem 2.1 (Existence and Uniqueness of Direct Triangular Decomposition)**
> 
> Let $A$ be an $n\times{n}$ matrix. If all leading principal minors $\det{A}_i$ ($i=1,2,\dots,n-1$) of $A$ are nonzero, then $A$ has a unique Doolittle decomposition $A=LU$, where $L$ is a unit lower triangular matrix and $U$ is an upper triangular matrix. Solving $Ax=b$ is then equivalent to solving $Ly=b$ and $Ux=y$ in sequence.

> **Theorem 2.3 (Thomas Algorithm)**
> 
> When the tridiagonal matrix $A$ satisfies the row diagonal dominance condition, it can be decomposed as $A=LU$, where $u_1=b_1$, $l_i=a_i/u_{i-1}$, $u_i=b_i-c_{i-1}l_i$; the forward sweep is $y_1=d_1$, $y_k=d_k-l_ky_{k-1}$, and the backward sweep is $x_n=\frac{y_n}{u_n}$, $x_k=\frac{y_k-c_kx_{k+1}}{u_k}$ ($k=n-1,\dots,1$).

> **Definition 2.4 (Condition Number of a Matrix)**
> 
> For a nonsingular matrix $A$, the quantity $\mathrm{cond}\left(A\right)=\left\|A\right\|\,\left\|A^{-1}\right\|$ is called the condition number of $A$. The larger the condition number, the more ill-conditioned the system $Ax=b$ is with respect to perturbations in the right-hand side or the coefficient matrix, and always $\mathrm{cond}\left(A\right)\ge1$.

> **Theorem 2.4 (Cholesky Decomposition of a Symmetric Positive Definite Matrix)**
> 
> Let $A$ be a symmetric positive definite matrix. Then there exists a unique lower triangular matrix $L$ with positive diagonal entries such that $A=LL^\top$, known as the square root method. Comparing $A=LL^\top$ gives $l_{kk}=\left(a_{kk}-\sum_{j=1}^{k-1}l_{kj}^{2}\right)^{1/2}$ and $l_{ik}=\frac{a_{ik}-\sum_{j=1}^{k-1}l_{ij}l_{kj}}{l_{kk}}$. Solving $Ax=b$ reduces to solving $Ly=b$ and $L^\topx=y$ in sequence. Also $A$ can be decomposed as $A=LDL^\top$ (improved square root method, where $L$ is unit lower triangular and $D$ is diagonal), avoiding square roots.

> **Theorem 2.5 (Operator Norm of a Matrix)**
> 
> The matrix norm induced by a vector norm is $\left\|A\right\|=\max_{\left\|x\right\|=1}\left\|Ax\right\|$, satisfying the compatibility condition $\left\|Ax\right\|\le\left\|A\right\|\left\|x\right\|$. The commonly used 1-norm (column norm) and $\infty$-norm (row norm) are $\left\|A\right\|_1=\max_{1\le{j}\le{n}}\sum_{i=1}^{n}\left|a_{ij}\right|$ and $\left\|A\right\|_\infty=\max_{1\le{i}\le{n}}\sum_{j=1}^{n}\left|a_{ij}\right|$.

> **Definition 3.3 (Spectral Radius)**
> 
> $\rho\left(A\right)=\max\left|\lambda_i\right|$.

> **Definition 3.4 (Diagonally Dominant Matrix)**
> 
> $\left|a_{ii}\right|\ge\sum_{j\ne{i}}\left|a_{ij}\right|$.

> **Theorem 3.6 (Convergence Criterion)**
> 
> $\rho\left(M\right)<1$.

## 2-10

Given

$$
A=\begin{bmatrix}6&13&-17\\13&29&-38\\-17&-38&50\end{bmatrix},
$$

find $\mathrm{cond}\left(A\right)_1$ and $\mathrm{cond}\left(A\right)_\infty$, and determine whether the system $Ax=b$ is ill-conditioned.

### Solution to 2-10

By **Theorem 2.5 (Operator Norm of a Matrix)**. For $A$, the column sums of absolute values are $6+13+17=36$, $13+29+38=80$, $17+38+50=105$, so $\left\|A\right\|_1=\max=105$; the row sums are $36$, $80$, $105$, so $\left\|A\right\|_\infty=105$.

Moreover $\det{A}=1$, and

$$
A^{-1}=\begin{bmatrix}6&-4&-1\\-4&11&7\\-1&7&5\end{bmatrix}.
$$

For $A^{-1}$, the column sums of absolute values are $11$, $22$, $13$, so $\left\|A^{-1}\right\|_1=22$; the row sums are $11$, $22$, $13$, so $\left\|A^{-1}\right\|_\infty=22$.

By **Definition 2.4 (Condition Number of a Matrix)**,

$$
\mathrm{cond}\left(A\right)_1=\left\|A\right\|_1\left\|A^{-1}\right\|_1=105\times22=2310,
$$

$$
\mathrm{cond}\left(A\right)_\infty=\left\|A\right\|_\infty\left\|A^{-1}\right\|_\infty=105\times22=2310.
$$

The condition number is about $2.3\times10^{3}$, far greater than $1$, so the system $Ax=b$ is ill-conditioned; small perturbations in the right-hand side or the coefficient matrix will be amplified by roughly a factor of one thousand. $\blacksquare$

## Exercise 3-3

Solve by Jacobi and Gauss-Seidel, 4 iterations.

### Solution to Exercise 3-3

Jacobi converges, Gauss-Seidel diverges. $\blacksquare$

## Exercise 3-5

Find range of $a$ for convergence.

### Solution to Exercise 3-5

$\left|a\right|>2$. $\blacksquare$

## Exercise 3-7

Write formulas and check convergence.

### Solution to Exercise 3-7

GS and SOR converge, Jacobi diverges. $\blacksquare$

## Exercise 3-8

Write a convergent iteration.

### Solution to Exercise 3-8

Permute rows to get diagonal dominance. $\blacksquare$

## Exercise 4-1(2)

Power method on the 3x3 matrix.

### Solution to Exercise 4-1(2)

$\lambda_1\approx6$, eigenvector $\left(1,-1,1\right)^\top$. $\blacksquare$
