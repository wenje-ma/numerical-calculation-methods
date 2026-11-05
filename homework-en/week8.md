# week8

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
> Let $A$ be a symmetric positive definite matrix. Then there exists a unique lower triangular matrix $L$ with positive diagonal entries such that $A=LL^{\mathrm{T}}$, known as the square root method. Comparing $A=LL^{\mathrm{T}}$ gives $l_{kk}=\left(a_{kk}-\sum_{j=1}^{k-1}l_{kj}^{2}\right)^{1/2}$ and $l_{ik}=\frac{a_{ik}-\sum_{j=1}^{k-1}l_{ij}l_{kj}}{l_{kk}}$. Solving $Ax=b$ reduces to solving $Ly=b$ and $L^{\mathrm{T}}x=y$ in sequence. Also $A$ can be decomposed as $A=LDL^{\mathrm{T}}$ (improved square root method, where $L$ is unit lower triangular and $D$ is diagonal), avoiding square roots.

> **Theorem 2.5 (Operator Norm of a Matrix)**
> 
> The matrix norm induced by a vector norm is $\left\|A\right\|=\max_{\left\|x\right\|=1}\left\|Ax\right\|$, satisfying the compatibility condition $\left\|Ax\right\|\le\left\|A\right\|\left\|x\right\|$. The commonly used 1-norm (column norm) and $\infty$-norm (row norm) are $\left\|A\right\|_1=\max_{1\le{j}\le{n}}\sum_{i=1}^{n}\left|a_{ij}\right|$ and $\left\|A\right\|_\infty=\max_{1\le{i}\le{n}}\sum_{j=1}^{n}\left|a_{ij}\right|$.

## 2-8

Solve the following system using the Thomas algorithm:

$$
\begin{bmatrix}2&-1&0&0\\-1&2&-1&0\\0&-1&2&-1\\0&0&-1&2\end{bmatrix}\begin{bmatrix}x_1\\x_2\\x_3\\x_4\end{bmatrix}=\begin{bmatrix}0\\1\\0\\2.5\end{bmatrix}.
$$

(Only part (1) is required.)

### Solution to 2-8

By **Definition 2.1 (Tridiagonal System)**, here the main diagonal is $b_i=2$, the subdiagonal is $a_i=-1$, the superdiagonal is $c_i=-1$, and the right-hand side is $d=\left(0,1,0,2.5\right)^{\mathrm{T}}$, satisfying row diagonal dominance. By **Theorem 2.3 (Thomas Algorithm)**.

Forward sweep ($Ly=d$): $u_1=b_1=2$, $y_1=d_1=0$; $l_2=a_2/u_1=-1/2=-0.5$, $u_2=2-\left(-1\right)\times\left(-0.5\right)=1.5$, $y_2=1-\left(-0.5\right)\times0=1$; $l_3=-1/1.5=-2/3$, $u_3=2-\left(-1\right)\times\left(-2/3\right)=4/3$, $y_3=0-\left(-2/3\right)\times1=2/3$; $l_4=-1/\left(4/3\right)=-3/4$, $u_4=2-\left(-1\right)\times\left(-3/4\right)=5/4$, $y_4=2.5-\left(-3/4\right)\times\left(2/3\right)=3$.

Backward sweep ($Ux=y$): $x_4=y_4/u_4=3/1.25=2.4$; $x_3=\left[y_3-c_3x_4\right]/u_3=\left[2/3-\left(-1\right)\times2.4\right]/\left(4/3\right)=2.3$; $x_2=\left[1-\left(-1\right)\times2.3\right]/1.5=2.2$; $x_1=\left[0-\left(-1\right)\times2.2\right]/2=1.1$.

Hence $x=\left(1.1,2.2,2.3,2.4\right)^{\mathrm{T}}$. $\blacksquare$
