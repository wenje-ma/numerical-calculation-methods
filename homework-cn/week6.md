# week6

> **定义 2.1 (三对角方程组)**
> 
> 系数矩阵 $A$ 的非零元素只分布在主对角线及相邻两条次对角线上: $A=\begin{bmatrix}b_1&c_1&&\\a_2&b_2&c_2&\\&\ddots&\ddots&\ddots\\&&a_n&b_n\end{bmatrix}$.

> **定理 2.1 (直接三角分解的存在唯一性)**
> 
> 设 $A$ 为 $n$ 阶方阵, 若 $A$ 的各阶顺序主子式 $\det A_i$ ($i=1,2,\dots,n-1$) 均不为零, 则 $A$ 有唯一的杜利特尔分解 $A=LU$, 其中 $L$ 为单位下三角形矩阵, $U$ 为上三角形矩阵. 此时解 $Ax=b$ 等价于依次求解 $Ly=b$, $Ux=y$.

> **定理 2.3 (追赶法)**
> 
> 当三对角矩阵 $A$ 满足按行对角占优条件时, 可分解为 $A=LU$, 其中 $u_1=b_1$, $l_i=a_i/u_{i-1}$, $u_i=b_i-c_{i-1}l_i$; 追 (前代) 为 $y_1=d_1$, $y_k=d_k-l_k y_{k-1}$, 赶 (回代) 为 $x_n=\frac{y_n}{u_n}$, $x_k=\frac{y_k-c_k x_{k+1}}{u_k}$ ($k=n-1,\dots,1$).

> **定义 2.4 (矩阵的条件数)**
> 
> 对非奇异矩阵 $A$, 称 $\mathrm{cond}\left(A\right)=\left\|A\right\|\,\left\|A^{-1}\right\|$ 为 $A$ 的条件数. 条件数越大, 方程组 $Ax=b$ 关于右端项或系数矩阵扰动的病态越严重, 且恒有 $\mathrm{cond}\left(A\right)\ge1$.

> **定理 2.4 (对称正定矩阵的乔列斯基分解)**
> 
> 设 $A$ 为对称正定矩阵, 则存在唯一的对角元皆为正数的下三角形矩阵 $L$, 使 $A=LL^{\mathrm T}$, 即平方根法. 由比较 $A=LL^{\mathrm T}$ 得 $l_{kk}=\left(a_{kk}-\sum_{j=1}^{k-1}l_{kj}^{2}\right)^{1/2}$, $l_{ik}=\frac{a_{ik}-\sum_{j=1}^{k-1}l_{ij}l_{kj}}{l_{kk}}$. 求解 $Ax=b$ 化为依次解 $Ly=b$ 与 $L^{\mathrm T}x=y$. 又 $A$ 可分解为 $A=LDL^{\mathrm T}$ (改进平方根法, $L$ 为单位下三角, $D$ 为对角阵), 运算中无须开方.

> **定理 2.5 (矩阵的算子范数)**
> 
> 由向量范数诱导的矩阵范数为 $\left\|A\right\|=\max_{\left\|x\right\|=1}\left\|Ax\right\|$, 且满足相容性 $\left\|Ax\right\|\le\left\|A\right\|\left\|x\right\|$. 常用的 1-范数 (列范数) 与 $\infty$-范数 (行范数) 为 $\left\|A\right\|_1=\max_{1\le j\le n}\sum_{i=1}^{n}\left|a_{ij}\right|$, $\left\|A\right\|_\infty=\max_{1\le i\le n}\sum_{j=1}^{n}\left|a_{ij}\right|$.

## 2-3

用紧凑格式解下列方程组, 并写出 $L,U$ 矩阵:

$$
\begin{bmatrix}1&2&3&4\\1&4&9&16\\1&8&27&64\\1&16&81&256\end{bmatrix}\begin{bmatrix}x_1\\x_2\\x_3\\x_4\end{bmatrix}=\begin{bmatrix}2\\10\\44\\190\end{bmatrix}.
$$

### 解答 2-3

由紧凑格式三角分解计算公式, 按第 1 行第 1 列, 第 2 行第 2 列, ... 的顺序分解 $A=LU$.

第 1 行第 1 列: $U$ 的第 1 行为 $\left(1,2,3,4\right)$, $l_{i1}=a_{i1}/u_{11}=1$ ($i=2,3,4$).

第 2 行第 2 列: $u_{22}=4-1\times2=2$, $u_{23}=9-1\times3=6$, $u_{24}=16-1\times4=12$; $l_{32}=\left(8-1\times2\right)/2=3$, $l_{42}=\left(16-1\times2\right)/2=7$.

第 3 行第 3 列: $u_{33}=27-1\times3-3\times6=6$, $u_{34}=64-1\times4-3\times12=24$; $l_{43}=\left(81-1\times3-7\times6\right)/6=6$.

第 4 行: $u_{44}=256-1\times4-7\times12-6\times24=24$.

故

$$
L=\begin{bmatrix}1&0&0&0\\1&1&0&0\\1&3&1&0\\1&7&6&1\end{bmatrix},\quad U=\begin{bmatrix}1&2&3&4\\0&2&6&12\\0&0&6&24\\0&0&0&24\end{bmatrix}.
$$

把 $b=\left(2,10,44,190\right)^{\mathrm T}$ 作为最后一列, 前代得 $y_1=2$, $y_2=10-1\times2=8$, $y_3=44-1\times2-3\times8=18$, $y_4=190-1\times2-7\times8-6\times18=24$. 回代: $x_4=24/24=1$, $x_3=\left(18-24\times1\right)/6=-1$, $x_2=\left[8-6\times\left(-1\right)-12\times1\right]/2=1$, $x_1=2-2\times1-3\times\left(-1\right)-4\times1=-1$.

所以 $x=\left(-1,1,-1,1\right)^{\mathrm T}$. $\blacksquare$
