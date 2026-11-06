# week5

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

## 2-1

Solve the following system using Gaussian elimination, column pivoting, and complete pivoting respectively, keeping 3 decimal places throughout:

$$
\begin{cases}2x_1+6x_2-4x_3=4,\\x_1+4x_2-5x_3=3,\\6x_1-x_2+18x_3=2.\end{cases}
$$

(Only part (1) is required.)

### Solution to 2-1

The augmented matrix of the system is

$$
\overline{A}=\begin{bmatrix}2&6&-4&4\\1&4&-5&3\\6&-1&18&2\end{bmatrix}.
$$

First eliminate by Gaussian Elimination. At step 1 take $a_{11}=2$ as pivot, with multipliers $l_{21}=1/2=0.500$, $l_{31}=6/2=3.000$; subtracting the corresponding multiples of row 1 from rows 2 and 3 gives

$$
\begin{bmatrix}2&6&-4&4\\0&1&-3&1\\0&-19&30&-10\end{bmatrix}.
$$

At step 2 take $a_{22}=1$ as pivot, with multiplier $l_{32}=-19/1=-19.000$; adding 19 times row 2 to row 3 gives the upper triangular matrix

$$
\begin{bmatrix}2&6&-4&4\\0&1&-3&1\\0&0&-27&9\end{bmatrix}.
$$

Back-substitute: $x_3=9/\left(-27\right)=-0.333$, $x_2=\left[1-\left(-3\right)\times\left(-0.333\right)\right]/1=0.000$, $x_1=\left[4-6\times0-\left(-4\right)\times\left(-0.333\right)\right]/2=1.333$.

Column pivoting selects $\left|6\right|$ in column 1 for row exchange, and complete pivoting selects the largest entry among all remaining entries for row and column exchange; in this problem the pivots $2,1,-27$ are all nonzero, so after pivoting the upper triangular system is the same and the back-substitution results agree. Hence

$$
x_1=1.333,\quad{x}_2=0.000,\quad{x}_3=-0.333.
$$

$\blacksquare$

## 2-2

Solve the system in Problem 1 using triangular decomposition.

### Solution to 2-2

By **Theorem 2.1 (Existence and Uniqueness of Direct Triangular Decomposition)** and Compact Formulas for Triangular Decomposition, perform the Doolittle decomposition $A=LU$ on the system of Problem 1, then solve $Ly=b$ and $Ux=y$ in sequence.

The system has $A=\begin{bmatrix}2&6&-4\\1&4&-5\\6&-1&18\end{bmatrix}$ and $b=\left(4,3,2\right)^\top$. The compact formulas give

$$
L=\begin{bmatrix}1&0&0\\0.5&1&0\\3&-19&1\end{bmatrix},\quad{U}=\begin{bmatrix}2&6&-4\\0&1&-3\\0&0&-27\end{bmatrix}.
$$

Forward substitution: $y_1=4$, $y_2=3-0.5\times4=1$, $y_3=2-3\times4-\left(-19\right)\times1=9$. Back substitution: $x_3=9/\left(-27\right)=-1/3$, $x_2=\left[1-\left(-3\right)\times\left(-1/3\right)\right]/1=0$, $x_1=\left[4-\left(-4\right)\times\left(-1/3\right)\right]/2=4/3$. Thus $x=\left(4/3,0,-1/3\right)^\top$. $\blacksquare$
