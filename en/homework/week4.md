# Assignment 4

> **Power Method** (Finding the Dominant Eigenvalue and Eigenvector) <br>Let the eigenvalues of the $n\times n$ real matrix $A$ satisfy $\left|\lambda_1\right|> \left|\lambda_2\right|\ge\cdots\ge\left|\lambda_n\right|$, with corresponding linearly independent eigenvectors $u_1,u_2,\dots,u_n$. Take an initial vector $\alpha^{\left(0\right)}\ne0$ and generate a vector sequence by the iteration $\alpha^{\left(k+1\right)}=A\alpha^{\left(k\right)}$ (Formula (4.1)); when $k$ is sufficiently large, $\alpha^{\left(k+1\right)}$ serves as an approximation to the eigenvector corresponding to $\lambda_1$, and $$\lambda_1\approx\frac{\alpha_i^{\left(k+1\right)}}{\alpha_i^{\left(k\right)}}$$ (Formula (4.3)). To avoid overflow or underflow during iteration, each step is normalized in practice: $$\alpha^{\left(k+1\right)}=Ay^{\left(k\right)},\quad y^{\left(k+1\right)}=\frac{\alpha^{\left(k+1\right)}}{\max_i\left|\alpha_i^{\left(k+1\right)}\right|},\quad\lambda_1\approx\max_i\left|\alpha_i^{\left(k+1\right)}\right|$$ (Formula (4.5)). The convergence rate is determined by the convergence factor $\left|\lambda_2/\lambda_1\right|$; the smaller its value, the faster the convergence.

> **Aitken Acceleration of the Power Method** (Algorithm 4.2) <br>If the sequence $\left\{a_k\right\}$ of eigenvalue approximations produced by the power method converges linearly to $a$, i.e. $\lim_{k\to\infty}\frac{a_{k+1}-a}{a_k-a}=c\ne1$, then for $k$ sufficiently large $$\hat a_k=a_k-\frac{\left(a_{k+1}-a_k\right)^2}{a_{k+2}-2a_{k+1}+a_k}$$ converges to $a$ faster than $\left\{a_k\right\}$; applying it to the sequence produced by the power method accelerates convergence.

> **Inverse Power Method** (Formula (4.10), Algorithm 4.3) <br>If $\lambda,u$ are an eigenvalue and eigenvector of $A$, then $A^{-1}u=\frac{1}{\lambda}u$; that is, the eigenvalues of $A^{-1}$ are the reciprocals of those of $A$, while the eigenvectors remain unchanged. In practice one solves the system $$A\alpha^{\left(k+1\right)}=\alpha^{\left(k\right)}$$ (Formula (4.10)) in place of $\alpha^{\left(k+1\right)}=A^{-1}\alpha^{\left(k\right)}$. If an approximation $\lambda^*$ to an eigenvalue $\lambda$ of $A$ is known, applying the inverse power method to $A-\lambda^*I$ converges rapidly, since $\lambda-\lambda^*$ is the eigenvalue of smallest modulus of $A-\lambda^*I$; after normalization one obtains a component $\beta\approx\frac{1}{\lambda-\lambda^*}$, so that $\lambda\approx\lambda^*+\frac{1}{\beta}$, and the resulting $\alpha^{\left(k\right)}$ is the corresponding eigenvector.

> **Jacobi Method** (Formula (4.12), Formula (4.13), Theorem 4.1) <br>Any real symmetric matrix $A$ of order $n$ can be reduced to a diagonal matrix by an orthogonal similarity transformation; that is, there exists an orthogonal matrix $Q$ such that $$Q^{\mathrm T}AQ=\mathrm{diag}\left(\lambda_1,\lambda_2,\dots,\lambda_n\right),$$ the diagonal entries are all the eigenvalues of $A$, and the columns of $Q$ are the corresponding eigenvectors. Take a plane-rotation matrix $V_{ij}\left(\varphi\right)$ (Formula (4.12), rotating by angle $\varphi$ in the $\left(i,j\right)$ coordinate plane), and choose $$\tan2\varphi=\frac{2a_{ij}}{a_{ii}-a_{jj}}$$ so that after the transformation $a_{ij}^{\left(1\right)}=0$ (Formula (4.13)). Repeating these rotations, by **Theorem 4.1** the sum of squares of the off-diagonal entries tends to zero and the matrix tends to a diagonal matrix whose diagonal entries are all the eigenvalues of $A$.

### Problem 1 (Problem 4-1)

Use the power method to compute the dominant eigenvalue and corresponding eigenvector of the following matrices, taking $x^{\left(0\right)}=\left(1,0,0\right)^{\mathrm T}$: (1) $A=\begin{bmatrix}-4&14&0\\-5&13&0\\-1&0&2\end{bmatrix}$; (2) $A=\begin{bmatrix}4&-1&1\\-1&3&-2\\1&-2&3\end{bmatrix}$. (Only part (2) is required.) ### Solution to Problem 1

For the matrix in (2), $A=\begin{bmatrix}4&-1&1\\-1&3&-2\\1&-2&3\end{bmatrix}$, by **Power Method** (Formula (4.5)), take $y^{\left(0\right)}=x^{\left(0\right)}=\left(1,0,0\right)^{\mathrm T}$, and normalize by the largest absolute-value component after each iteration. The computation is as follows: $$
\alpha^{\left(1\right)}=Ay^{\left(0\right)}=\left(4,-1,1\right)^{\mathrm T},\quad\lambda_1\approx4,\quad y^{\left(1\right)}=\left(1,-0.25,0.25\right)^{\mathrm T},
$$

$$
\alpha^{\left(2\right)}=Ay^{\left(1\right)}=\left(4.5,-2.25,2.25\right)^{\mathrm T},\quad\lambda_2\approx4.5,\quad y^{\left(2\right)}=\left(1,-0.5,0.5\right)^{\mathrm T},
$$

$$
\alpha^{\left(3\right)}=Ay^{\left(2\right)}=\left(5,-3.5,3.5\right)^{\mathrm T},\quad\lambda_3\approx5,\quad y^{\left(3\right)}=\left(1,-0.7,0.7\right)^{\mathrm T},
$$

$$
\alpha^{\left(4\right)}=Ay^{\left(3\right)}=\left(5.4,-4.5,4.5\right)^{\mathrm T},\quad\lambda_4\approx5.4,\quad y^{\left(4\right)}=\left(1,-0.8333,0.8333\right)^{\mathrm T},
$$

$$
\alpha^{\left(5\right)}=Ay^{\left(4\right)}=\left(5.6667,-5.1667,5.1667\right)^{\mathrm T},\quad\lambda_5\approx5.6667,\quad y^{\left(5\right)}=\left(1,-0.9118,0.9118\right)^{\mathrm T},
$$

$$
\alpha^{\left(6\right)}=Ay^{\left(5\right)}=\left(5.8235,-5.5588,5.5588\right)^{\mathrm T},\quad\lambda_6\approx5.8235,\quad y^{\left(6\right)}=\left(1,-0.9545,0.9545\right)^{\mathrm T}.
$$

One sees that the eigenvalue approximations $\lambda_k$ increase monotonically and tend to $6$, while the last two components of the normalized vector $y^{\left(k\right)}$ tend to equal magnitude with opposite signs. Continuing the iteration gives the dominant eigenvalue $\lambda_1\approx6$ and the corresponding eigenvector $x\approx\left(1,-1,1\right)^{\mathrm T}$. Check: $A\left(1,-1,1\right)^{\mathrm T}=\left(6,-6,6\right)^{\mathrm T}=6\left(1,-1,1\right)^{\mathrm T}$. $\blacksquare$

### Problem 2 (Problem 4-2)

Use the power method with Aitken acceleration to compute the dominant eigenvalue and corresponding eigenvector of the matrix in Problem 1, requiring 4 significant digits in the result. (i.e. the matrix in Problem 1 (2).) ### Solution to Problem 2

By **Power Method** (Formula (4.5)), the sequence of eigenvalue approximations already obtained is

$$
\lambda_1\approx4,\ \lambda_2\approx4.5,\ \lambda_3\approx5,\ \lambda_4\approx5.4,\ \lambda_5\approx5.6667,\ \lambda_6\approx5.8235,\ \lambda_7\approx5.9091,\ \lambda_8\approx5.9538,\ \lambda_9\approx5.9767.
$$

Applying **Aitken Acceleration of the Power Method** (Algorithm 4.2) to this sequence. First take $a=\lambda_6=5.8235$, $b=\lambda_7=5.9091$, $c=\lambda_8=5.9538$: $$
\hat a=a-\frac{\left(b-a\right)^2}{c-2b+a}=5.8235-\frac{\left(0.0856\right)^2}{5.9538-2\times5.9091+5.8235}\approx5.8235+0.1794\approx6.003.
$$

Then take $a=\lambda_7=5.9091$, $b=\lambda_8=5.9538$, $c=\lambda_9=5.9767$: $$
\hat a=5.9091-\frac{\left(0.0447\right)^2}{5.9767-2\times5.9538+5.9091}\approx5.9091+0.0916\approx6.001.
$$

Both accelerations give $\lambda_1\approx6.000$, attaining 4 significant digits. The corresponding eigenvector is the same as in Problem 1, namely $x\approx\left(1,-1,1\right)^{\mathrm T}$. $\blacksquare$

### Problem 3 (Problem 4-4)

Use the inverse power method to compute the eigenvector of the matrix $A=\begin{bmatrix}2&1&0\\1&3&1\\0&1&4\end{bmatrix}$ corresponding to the eigenvalue $1.2679$.

### Solution to Problem 3

By **Inverse Power Method** (Formula (4.10), Algorithm 4.3), take the shift $\lambda^*=1.2679$ and set

$$
B=A-\lambda^*I=\begin{bmatrix}0.7321&1&0\\1&1.7321&1\\0&1&2.7321\end{bmatrix}.
$$

Take an arbitrary initial vector $y^{\left(0\right)}=\left(1,1,1\right)^{\mathrm T}$, repeatedly solve the system $Bz=y^{\left(k\right)}$ and normalize by the largest component. The first solve $Bz=\left(1,1,1\right)^{\mathrm T}$ gives $z\approx\left(6776.4,-4960.0,1815.8\right)^{\mathrm T}$, and normalization gives $y^{\left(1\right)}\approx\left(1,-0.7320,0.2680\right)^{\mathrm T}$; the second solve $Bz=y^{\left(1\right)}$ gives $z\approx\left(20327.5,-14880.7,5446.7\right)^{\mathrm T}$, and normalization gives $y^{\left(2\right)}\approx\left(1,-0.7321,0.2679\right)^{\mathrm T}$; one more iteration leaves the result unchanged.

Therefore the eigenvector corresponding to the eigenvalue $1.2679$ is $x\approx\left(1,-0.732,0.268\right)^{\mathrm T}$ (up to a nonzero constant factor and sign). Here the largest component is $m\approx20327.5$, $\beta=\frac{1}{m}\approx4.9\times10^{-5}$, $\lambda\approx1.2679+\beta\approx1.26795$, in agreement with the given eigenvalue. $\blacksquare$

### Problem 4 (Problem 4-7)

Let $A$ be a real symmetric matrix of order $n$. For any nonzero vector $x\in\mathbb R^n$, the quantity $\frac{\left\langle Ax,x\right\rangle}{\left\langle x,x\right\rangle}=\frac{x^{\mathrm T}Ax}{x^{\mathrm T}x}$ is called the Rayleigh quotient of $A$. Prove that: $$
\min_{x\ne0}\frac{\left\langle Ax,x\right\rangle}{\left\langle x,x\right\rangle}=\min\lambda\left(A\right),\quad\max_{x\ne0}\frac{\left\langle Ax,x\right\rangle}{\left\langle x,x\right\rangle}=\max\lambda\left(A\right).
$$

### Solution to Problem 4

By the result underlying the **Jacobi Method**, a real symmetric matrix $A$ can be orthogonally diagonalized; that is, there exists an orthogonal matrix $U=\left(u_1,u_2,\dots,u_n\right)$ such that $U^{\mathrm T}AU=\Lambda=\mathrm{diag}\left(\lambda_1,\lambda_2,\dots,\lambda_n\right)$, where $\lambda_1\le\lambda_2\le\cdots\le\lambda_n$ are all the eigenvalues of $A$, and $u_1,u_2,\dots,u_n$ are the corresponding orthonormal eigenvectors.

For any nonzero vector $x\in\mathbb R^n$, expand $x=\sum_{j=1}^n c_ju_j$ in the orthonormal basis $\left\{u_j\right\}$; then

$$
\left\langle Ax,x\right\rangle=x^{\mathrm T}Ax=\sum_{j=1}^n\lambda_jc_j^2,\quad\left\langle x,x\right\rangle=x^{\mathrm T}x=\sum_{j=1}^nc_j^2.
$$

Thus the Rayleigh quotient is

$$
R\left(x\right)=\frac{\left\langle Ax,x\right\rangle}{\left\langle x,x\right\rangle}=\frac{\sum_{j=1}^n\lambda_jc_j^2}{\sum_{j=1}^nc_j^2}.
$$

Since $\lambda_1\le\lambda_j\le\lambda_n\left(j=1,2,\dots,n\right)$,

$$
\lambda_1\sum_{j=1}^nc_j^2\le\sum_{j=1}^n\lambda_jc_j^2\le\lambda_n\sum_{j=1}^nc_j^2,
$$

dividing both sides by the positive number $\sum_{j=1}^nc_j^2$ gives $\lambda_1\le R\left(x\right)\le\lambda_n$.

Taking $x=u_1$ (i.e. $c_1=1$ and all other $c_j=0$), we have $R\left(u_1\right)=\lambda_1=\min\lambda\left(A\right)$; taking $x=u_n$, we have $R\left(u_n\right)=\lambda_n=\max\lambda\left(A\right)$. Therefore

$$
\min_{x\ne0}\frac{\left\langle Ax,x\right\rangle}{\left\langle x,x\right\rangle}=\min\lambda\left(A\right),\quad\max_{x\ne0}\frac{\left\langle Ax,x\right\rangle}{\left\langle x,x\right\rangle}=\max\lambda\left(A\right).
$$

$\blacksquare$

### Problem 5 (Problem 4-8)

Use the Jacobi method to find all eigenvalues of the following matrices: (1) $A=\begin{bmatrix}4&2&2\\2&5&1\\2&1&6\end{bmatrix}$; (2) $A=\begin{bmatrix}2&-1&0\\-1&-2&-1\\0&-1&2\end{bmatrix}$. (Only part (2) is required.) ### Solution to Problem 5

For the real symmetric matrix in (2), $A=\begin{bmatrix}2&-1&0\\-1&-2&-1\\0&-1&2\end{bmatrix}$, by **Jacobi Method** (Formula (4.12), Formula (4.13), Theorem 4.1), at each step take the off-diagonal entry of largest absolute value and perform a rotation.

First take $i=1,j=2$: $a_{12}=-1$, $a_{11}=2$, $a_{22}=-2$, and from $\tan2\varphi=\frac{2a_{12}}{a_{11}-a_{22}}=\frac{-2}{4}=-0.5$ one gets $\varphi=-0.2318$, $\cos\varphi=0.9733$, $\sin\varphi=-0.2298$. After the $V_{12}\left(\varphi\right)$ transformation

$$
A^{\left(1\right)}\approx\begin{bmatrix}2.2361&0&0.2298\\0&-2.2361&-0.9733\\0.2298&-0.9733&2\end{bmatrix}.
$$

Next take $i=2,j=3$; after rotation

$$
A^{\left(2\right)}\approx\begin{bmatrix}2.2361&-0.2245&0.0491\\-0.2245&2.2129&0\\0.0491&0&-2.4490\end{bmatrix}.
$$

Next take $i=1,j=2$; after rotation

$$
A^{\left(3\right)}\approx\begin{bmatrix}2.4492&0&0.0356\\0&1.9997&0.0338\\0.0356&0.0338&-2.4490\end{bmatrix}.
$$

Continuing the rotations by **Theorem 4.1**, the sum of squares of the off-diagonal entries tends to zero and the matrix tends to a diagonal matrix, with diagonal entries converging to $2.449$, $2.000$, $-2.449$. Therefore all the eigenvalues of $A$ are

$$
\lambda_1\approx2.449,\quad\lambda_2\approx2.000,\quad\lambda_3\approx-2.449
$$ (the exact values are $\sqrt6,\ 2,\ -\sqrt6$). $\blacksquare$
