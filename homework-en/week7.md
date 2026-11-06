# week7

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

## 2-6

Solve the following system using both the square root method and the improved square root method:

$$
\begin{bmatrix}1&2&1&-3\\2&5&0&-5\\1&0&14&1\\-3&-5&1&15\end{bmatrix}\begin{bmatrix}x_1\\x_2\\x_3\\x_4\end{bmatrix}=\begin{bmatrix}1\\2\\16\\8\end{bmatrix}.
$$

### Solution to 2-6

The coefficient matrix is symmetric and all leading principal minors are positive; by **Theorem 2.4 (Cholesky Decomposition of a Symmetric Positive Definite Matrix)**, the decomposition $A=LL^\top$ is possible.

Square root method: compute the entries of $L$ column by column. $l_{11}=\sqrt{1}=1$, $l_{21}=2/1=2$, $l_{31}=1/1=1$, $l_{41}=-3/1=-3$; $l_{22}=\sqrt{5-2^{2}}=1$, $l_{32}=\left(0-1\times2\right)/1=-2$, $l_{42}=\left(-5-\left(-3\right)\times2\right)/1=1$; $l_{33}=\sqrt{14-1^{2}-\left(-2\right)^{2}}=3$, $l_{43}=\left[1-\left(-3\right)\times1-1\times\left(-2\right)\right]/3=2$; $l_{44}=\sqrt{15-\left(-3\right)^{2}-1^{2}-2^{2}}=1$. Thus

$$
L=\begin{bmatrix}1&0&0&0\\2&1&0&0\\1&-2&3&0\\-3&1&2&1\end{bmatrix}.
$$

Solving $Ly=b$: $y_1=1$, $y_2=\left(2-2\times1\right)/1=0$, $y_3=\left[16-1\times1-\left(-2\right)\times0\right]/3=5$, $y_4=\left[8-\left(-3\right)\times1-1\times0-2\times5\right]/1=1$. Then solving $L^\topx=y$: $x_4=1$, $x_3=\left(5-2\times1\right)/3=1$, $x_2=0-\left(-2\right)\times1-1\times1=1$, $x_1=1-2\times1-1\times1-\left(-3\right)\times1=1$.

Improved square root method: form $A=\widetilde{L}D\widetilde{L}^\top$, where $D=\mathrm{diag}\left(1,1,9,1\right)$, and the off-diagonal entries of the unit lower triangular matrix $\widetilde{L}$ are the columns of $L$ divided by $\sqrt{d_k}$, i.e. $l_{21}=2$, $l_{31}=1$, $l_{41}=-3$, $l_{32}=-2$, $l_{42}=1$, $l_{43}=2/3$. Forward substitution $Ly=b$ gives $y=\left(1,0,15,1\right)^\top$, and back substitution by $x_k=y_k/d_k-\sum_{j=k+1}^{n}l_{jk}x_j$ gives: $x_4=1$, $x_3=15/9-\left(2/3\right)\times1=1$, $x_2=0-\left(-2\right)\times1-1\times1=1$, $x_1=1-2\times1-1\times1-\left(-3\right)\times1=1$. Both methods agree.

Hence $x=\left(1,1,1,1\right)^\top$. $\blacksquare$
