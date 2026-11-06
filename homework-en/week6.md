# week6

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
> Let $A$ be a symmetric positive definite matrix. Then there exists a unique lower triangular matrix $L$ with positive diagonal entries such that $A=LL^{\top}$, known as the square root method. Comparing $A=LL^{\top}$ gives $l_{kk}=\left(a_{kk}-\sum_{j=1}^{k-1}l_{kj}^{2}\right)^{1/2}$ and $l_{ik}=\frac{a_{ik}-\sum_{j=1}^{k-1}l_{ij}l_{kj}}{l_{kk}}$. Solving $Ax=b$ reduces to solving $Ly=b$ and $L^{\top}x=y$ in sequence. Also $A$ can be decomposed as $A=LDL^{\top}$ (improved square root method, where $L$ is unit lower triangular and $D$ is diagonal), avoiding square roots.

> **Theorem 2.5 (Operator Norm of a Matrix)**
> 
> The matrix norm induced by a vector norm is $\left\|A\right\|=\max_{\left\|x\right\|=1}\left\|Ax\right\|$, satisfying the compatibility condition $\left\|Ax\right\|\le\left\|A\right\|\left\|x\right\|$. The commonly used 1-norm (column norm) and $\infty$-norm (row norm) are $\left\|A\right\|_1=\max_{1\le{j}\le{n}}\sum_{i=1}^{n}\left|a_{ij}\right|$ and $\left\|A\right\|_\infty=\max_{1\le{i}\le{n}}\sum_{j=1}^{n}\left|a_{ij}\right|$.

## 2-3

Solve the following system using the compact form, and write out the $L,U$ matrices:

$$
\begin{bmatrix}1&2&3&4\\1&4&9&16\\1&8&27&64\\1&16&81&256\end{bmatrix}\begin{bmatrix}x_1\\x_2\\x_3\\x_4\end{bmatrix}=\begin{bmatrix}2\\10\\44\\190\end{bmatrix}.
$$

### Solution to 2-3

By Compact Formulas for Triangular Decomposition, decompose $A=LU$ in the order row 1 column 1, row 2 column 2, ...

Row 1 column 1: row 1 of $U$ is $\left(1,2,3,4\right)$, and $l_{i1}=a_{i1}/u_{11}=1$ ($i=2,3,4$).

Row 2 column 2: $u_{22}=4-1\times2=2$, $u_{23}=9-1\times3=6$, $u_{24}=16-1\times4=12$; $l_{32}=\left(8-1\times2\right)/2=3$, $l_{42}=\left(16-1\times2\right)/2=7$.

Row 3 column 3: $u_{33}=27-1\times3-3\times6=6$, $u_{34}=64-1\times4-3\times12=24$; $l_{43}=\left(81-1\times3-7\times6\right)/6=6$.

Row 4: $u_{44}=256-1\times4-7\times12-6\times24=24$.

Thus

$$
L=\begin{bmatrix}1&0&0&0\\1&1&0&0\\1&3&1&0\\1&7&6&1\end{bmatrix},\quad{U}=\begin{bmatrix}1&2&3&4\\0&2&6&12\\0&0&6&24\\0&0&0&24\end{bmatrix}.
$$

Appending $b=\left(2,10,44,190\right)^{\top}$ as the last column, forward substitution gives $y_1=2$, $y_2=10-1\times2=8$, $y_3=44-1\times2-3\times8=18$, $y_4=190-1\times2-7\times8-6\times18=24$. Back substitution: $x_4=24/24=1$, $x_3=\left(18-24\times1\right)/6=-1$, $x_2=\left[8-6\times\left(-1\right)-12\times1\right]/2=1$, $x_1=2-2\times1-3\times\left(-1\right)-4\times1=-1$.

Therefore $x=\left(-1,1,-1,1\right)^{\top}$. $\blacksquare$
