# week2

> **Basic Knowledge: Gaussian Elimination**<br>Eliminate the augmented matrix of the system column by column into an equivalent upper triangular system, then back-substitute in reverse variable order. At step $k$, take $a_{kk}^{\left(k\right)}\ne0$ as the pivot, with multipliers $l_{ik}=a_{ik}^{\left(k\right)}/a_{kk}^{\left(k\right)}$; the back-substitution formulas are $x_n=\frac{b_n^{\left(n\right)}}{a_{nn}^{\left(n\right)}}$ and $x_k=\frac{b_k^{\left(k\right)}-\sum_{j=k+1}^{n}a_{kj}^{\left(k\right)}x_j}{a_{kk}^{\left(k\right)}}$ ($k=n-1,\dots,1$). To suppress the growth of roundoff errors caused by small pivots, one may select the entry of largest absolute value in column $k$ (column pivoting) or among all remaining entries (complete pivoting), perform the corresponding row (column) exchange, and then eliminate.

> **Basic Knowledge: Compact Formulas for Triangular Decomposition**<br>In the order of row 1 column 1, row 2 column 2, ..., comparing $A=LU$ gives $u_{1j}=a_{1j}$, $l_{i1}=\frac{a_{i1}}{u_{11}}$, $u_{rj}=a_{rj}-\sum_{k=1}^{r-1}l_{rk}u_{kj}$, $l_{ir}=\frac{a_{ir}-\sum_{k=1}^{r-1}l_{ik}u_{kr}}{u_{rr}}$. In solving, append the right-hand side vector $b$ as the last column, first forward-substitute to find $y$ in the same compact form, then back-substitute by $x_k=\left(y_k-\sum_{j=k+1}^{n}u_{kj}x_j\right)/u_{kk}$.

> **Definition 2.1 (Tridiagonal System)**<br>The nonzero entries of the coefficient matrix $A$ lie only on the main diagonal and the two adjacent subdiagonals: $A=\begin{bmatrix}b_1&c_1&&\\a_2&b_2&c_2&\\&\ddots&\ddots&\ddots\\&&a_n&b_n\end{bmatrix}$.

> **Theorem 2.1 (Existence and Uniqueness of Direct Triangular Decomposition)**<br>Let $A$ be an $n\times n$ matrix. If all leading principal minors $\det A_i$ ($i=1,2,\dots,n-1$) of $A$ are nonzero, then $A$ has a unique Doolittle decomposition $A=LU$, where $L$ is a unit lower triangular matrix and $U$ is an upper triangular matrix. Solving $Ax=b$ is then equivalent to solving $Ly=b$ and $Ux=y$ in sequence.

> **Theorem 2.3 (Thomas Algorithm)**<br>When the tridiagonal matrix $A$ satisfies the row diagonal dominance condition, it can be decomposed as $A=LU$, where $u_1=b_1$, $l_i=a_i/u_{i-1}$, $u_i=b_i-c_{i-1}l_i$; the forward sweep is $y_1=d_1$, $y_k=d_k-l_k y_{k-1}$, and the backward sweep is $x_n=\frac{y_n}{u_n}$, $x_k=\frac{y_k-c_k x_{k+1}}{u_k}$ ($k=n-1,\dots,1$).

> **Definition 2.4 (Condition Number of a Matrix)**<br>For a nonsingular matrix $A$, the quantity $\mathrm{cond}\left(A\right)=\left\|A\right\|\,\left\|A^{-1}\right\|$ is called the condition number of $A$. The larger the condition number, the more ill-conditioned the system $Ax=b$ is with respect to perturbations in the right-hand side or the coefficient matrix, and always $\mathrm{cond}\left(A\right)\ge1$.

> **Theorem 2.4 (Cholesky Decomposition of a Symmetric Positive Definite Matrix)**<br>Let $A$ be a symmetric positive definite matrix. Then there exists a unique lower triangular matrix $L$ with positive diagonal entries such that $A=LL^{\mathrm T}$, known as the square root method. Comparing $A=LL^{\mathrm T}$ gives $l_{kk}=\left(a_{kk}-\sum_{j=1}^{k-1}l_{kj}^{2}\right)^{1/2}$ and $l_{ik}=\frac{a_{ik}-\sum_{j=1}^{k-1}l_{ij}l_{kj}}{l_{kk}}$. Solving $Ax=b$ reduces to solving $Ly=b$ and $L^{\mathrm T}x=y$ in sequence. Also $A$ can be decomposed as $A=LDL^{\mathrm T}$ (improved square root method, where $L$ is unit lower triangular and $D$ is diagonal), avoiding square roots.

> **Theorem 2.5 (Operator Norm of a Matrix)**<br>The matrix norm induced by a vector norm is $\left\|A\right\|=\max_{\left\|x\right\|=1}\left\|Ax\right\|$, satisfying the compatibility condition $\left\|Ax\right\|\le\left\|A\right\|\left\|x\right\|$. The commonly used 1-norm (column norm) and $\infty$-norm (row norm) are $\left\|A\right\|_1=\max_{1\le j\le n}\sum_{i=1}^{n}\left|a_{ij}\right|$ and $\left\|A\right\|_\infty=\max_{1\le i\le n}\sum_{j=1}^{n}\left|a_{ij}\right|$.

---

## 2-1

Solve the following system using Gaussian elimination, column pivoting, and complete pivoting respectively, keeping 3 decimal places throughout:

$$
\begin{cases}2x_1+6x_2-4x_3=4,\\x_1+4x_2-5x_3=3,\\6x_1-x_2+18x_3=2.\end{cases}
$$

(Only part (1) is required.)

### Solution 2-1

The augmented matrix of the system is

$$
\overline A=\begin{bmatrix}2&6&-4&4\\1&4&-5&3\\6&-1&18&2\end{bmatrix}.
$$

First eliminate by **Basic Knowledge: Gaussian Elimination**. At step 1 take $a_{11}=2$ as pivot, with multipliers $l_{21}=1/2=0.500$, $l_{31}=6/2=3.000$; subtracting the corresponding multiples of row 1 from rows 2 and 3 gives

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
x_1=1.333,\quad x_2=0.000,\quad x_3=-0.333.
$$

$\blacksquare$

---

## 2-2

Solve the system in Problem 1 using triangular decomposition.

### Solution 2-2

By **Theorem 2.1 (Existence and Uniqueness of Direct Triangular Decomposition)** and **Basic Knowledge: Compact Formulas for Triangular Decomposition**, perform the Doolittle decomposition $A=LU$ on the system of Problem 1, then solve $Ly=b$ and $Ux=y$ in sequence.

The system has $A=\begin{bmatrix}2&6&-4\\1&4&-5\\6&-1&18\end{bmatrix}$ and $b=\left(4,3,2\right)^{\mathrm T}$. The compact formulas give

$$
L=\begin{bmatrix}1&0&0\\0.5&1&0\\3&-19&1\end{bmatrix},\quad U=\begin{bmatrix}2&6&-4\\0&1&-3\\0&0&-27\end{bmatrix}.
$$

Forward substitution: $y_1=4$, $y_2=3-0.5\times4=1$, $y_3=2-3\times4-\left(-19\right)\times1=9$. Back substitution: $x_3=9/\left(-27\right)=-1/3$, $x_2=\left[1-\left(-3\right)\times\left(-1/3\right)\right]/1=0$, $x_1=\left[4-\left(-4\right)\times\left(-1/3\right)\right]/2=4/3$. Thus $x=\left(4/3,0,-1/3\right)^{\mathrm T}$. $\blacksquare$

---

## 2-3

Solve the following system using the compact form, and write out the $L,U$ matrices:

$$
\begin{bmatrix}1&2&3&4\\1&4&9&16\\1&8&27&64\\1&16&81&256\end{bmatrix}\begin{bmatrix}x_1\\x_2\\x_3\\x_4\end{bmatrix}=\begin{bmatrix}2\\10\\44\\190\end{bmatrix}.
$$

### Solution 2-3

By **Basic Knowledge: Compact Formulas for Triangular Decomposition**, decompose $A=LU$ in the order row 1 column 1, row 2 column 2, ...

Row 1 column 1: row 1 of $U$ is $\left(1,2,3,4\right)$, and $l_{i1}=a_{i1}/u_{11}=1$ ($i=2,3,4$).

Row 2 column 2: $u_{22}=4-1\times2=2$, $u_{23}=9-1\times3=6$, $u_{24}=16-1\times4=12$; $l_{32}=\left(8-1\times2\right)/2=3$, $l_{42}=\left(16-1\times2\right)/2=7$.

Row 3 column 3: $u_{33}=27-1\times3-3\times6=6$, $u_{34}=64-1\times4-3\times12=24$; $l_{43}=\left(81-1\times3-7\times6\right)/6=6$.

Row 4: $u_{44}=256-1\times4-7\times12-6\times24=24$.

Thus

$$
L=\begin{bmatrix}1&0&0&0\\1&1&0&0\\1&3&1&0\\1&7&6&1\end{bmatrix},\quad U=\begin{bmatrix}1&2&3&4\\0&2&6&12\\0&0&6&24\\0&0&0&24\end{bmatrix}.
$$

Appending $b=\left(2,10,44,190\right)^{\mathrm T}$ as the last column, forward substitution gives $y_1=2$, $y_2=10-1\times2=8$, $y_3=44-1\times2-3\times8=18$, $y_4=190-1\times2-7\times8-6\times18=24$. Back substitution: $x_4=24/24=1$, $x_3=\left(18-24\times1\right)/6=-1$, $x_2=\left[8-6\times\left(-1\right)-12\times1\right]/2=1$, $x_1=2-2\times1-3\times\left(-1\right)-4\times1=-1$.

Therefore $x=\left(-1,1,-1,1\right)^{\mathrm T}$. $\blacksquare$

---

## 2-6

Solve the following system using both the square root method and the improved square root method:

$$
\begin{bmatrix}1&2&1&-3\\2&5&0&-5\\1&0&14&1\\-3&-5&1&15\end{bmatrix}\begin{bmatrix}x_1\\x_2\\x_3\\x_4\end{bmatrix}=\begin{bmatrix}1\\2\\16\\8\end{bmatrix}.
$$

### Solution 2-6

The coefficient matrix is symmetric and all leading principal minors are positive; by **Theorem 2.4 (Cholesky Decomposition of a Symmetric Positive Definite Matrix)**, the decomposition $A=LL^{\mathrm T}$ is possible.

Square root method: compute the entries of $L$ column by column. $l_{11}=\sqrt{1}=1$, $l_{21}=2/1=2$, $l_{31}=1/1=1$, $l_{41}=-3/1=-3$; $l_{22}=\sqrt{5-2^{2}}=1$, $l_{32}=\left(0-1\times2\right)/1=-2$, $l_{42}=\left(-5-\left(-3\right)\times2\right)/1=1$; $l_{33}=\sqrt{14-1^{2}-\left(-2\right)^{2}}=3$, $l_{43}=\left[1-\left(-3\right)\times1-1\times\left(-2\right)\right]/3=2$; $l_{44}=\sqrt{15-\left(-3\right)^{2}-1^{2}-2^{2}}=1$. Thus

$$
L=\begin{bmatrix}1&0&0&0\\2&1&0&0\\1&-2&3&0\\-3&1&2&1\end{bmatrix}.
$$

Solving $Ly=b$: $y_1=1$, $y_2=\left(2-2\times1\right)/1=0$, $y_3=\left[16-1\times1-\left(-2\right)\times0\right]/3=5$, $y_4=\left[8-\left(-3\right)\times1-1\times0-2\times5\right]/1=1$. Then solving $L^{\mathrm T}x=y$: $x_4=1$, $x_3=\left(5-2\times1\right)/3=1$, $x_2=0-\left(-2\right)\times1-1\times1=1$, $x_1=1-2\times1-1\times1-\left(-3\right)\times1=1$.

Improved square root method: form $A=\widetilde L D\widetilde L^{\mathrm T}$, where $D=\mathrm{diag}\left(1,1,9,1\right)$, and the off-diagonal entries of the unit lower triangular matrix $\widetilde L$ are the columns of $L$ divided by $\sqrt{d_k}$, i.e. $l_{21}=2$, $l_{31}=1$, $l_{41}=-3$, $l_{32}=-2$, $l_{42}=1$, $l_{43}=2/3$. Forward substitution $Ly=b$ gives $y=\left(1,0,15,1\right)^{\mathrm T}$, and back substitution by $x_k=y_k/d_k-\sum_{j=k+1}^{n}l_{jk}x_j$ gives: $x_4=1$, $x_3=15/9-\left(2/3\right)\times1=1$, $x_2=0-\left(-2\right)\times1-1\times1=1$, $x_1=1-2\times1-1\times1-\left(-3\right)\times1=1$. Both methods agree.

Hence $x=\left(1,1,1,1\right)^{\mathrm T}$. $\blacksquare$

---

## 2-8

Solve the following system using the Thomas algorithm:

$$
\begin{bmatrix}2&-1&0&0\\-1&2&-1&0\\0&-1&2&-1\\0&0&-1&2\end{bmatrix}\begin{bmatrix}x_1\\x_2\\x_3\\x_4\end{bmatrix}=\begin{bmatrix}0\\1\\0\\2.5\end{bmatrix}.
$$

(Only part (1) is required.)

### Solution 2-8

By **Definition 2.1 (Tridiagonal System)**, here the main diagonal is $b_i=2$, the subdiagonal is $a_i=-1$, the superdiagonal is $c_i=-1$, and the right-hand side is $d=\left(0,1,0,2.5\right)^{\mathrm T}$, satisfying row diagonal dominance. By **Theorem 2.3 (Thomas Algorithm)**.

Forward sweep ($Ly=d$): $u_1=b_1=2$, $y_1=d_1=0$; $l_2=a_2/u_1=-1/2=-0.5$, $u_2=2-\left(-1\right)\times\left(-0.5\right)=1.5$, $y_2=1-\left(-0.5\right)\times0=1$; $l_3=-1/1.5=-2/3$, $u_3=2-\left(-1\right)\times\left(-2/3\right)=4/3$, $y_3=0-\left(-2/3\right)\times1=2/3$; $l_4=-1/\left(4/3\right)=-3/4$, $u_4=2-\left(-1\right)\times\left(-3/4\right)=5/4$, $y_4=2.5-\left(-3/4\right)\times\left(2/3\right)=3$.

Backward sweep ($Ux=y$): $x_4=y_4/u_4=3/1.25=2.4$; $x_3=\left[y_3-c_3 x_4\right]/u_3=\left[2/3-\left(-1\right)\times2.4\right]/\left(4/3\right)=2.3$; $x_2=\left[1-\left(-1\right)\times2.3\right]/1.5=2.2$; $x_1=\left[0-\left(-1\right)\times2.2\right]/2=1.1$.

Hence $x=\left(1.1,2.2,2.3,2.4\right)^{\mathrm T}$. $\blacksquare$

---

## 2-10

Given

$$
A=\begin{bmatrix}6&13&-17\\13&29&-38\\-17&-38&50\end{bmatrix},
$$

find $\mathrm{cond}\left(A\right)_1$ and $\mathrm{cond}\left(A\right)_\infty$, and determine whether the system $Ax=b$ is ill-conditioned.

### Solution 2-10

By **Theorem 2.5 (Operator Norm of a Matrix)**. For $A$, the column sums of absolute values are $6+13+17=36$, $13+29+38=80$, $17+38+50=105$, so $\left\|A\right\|_1=\max=105$; the row sums are $36$, $80$, $105$, so $\left\|A\right\|_\infty=105$.

Moreover $\det A=1$, and

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
