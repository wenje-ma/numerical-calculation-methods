# week8

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

## 2-8

用追赶法解下列方程组:

$$
\begin{bmatrix}2&-1&0&0\\-1&2&-1&0\\0&-1&2&-1\\0&0&-1&2\end{bmatrix}\begin{bmatrix}x_1\\x_2\\x_3\\x_4\end{bmatrix}=\begin{bmatrix}0\\1\\0\\2.5\end{bmatrix}.
$$

(仅做第 (1) 小题)

### 解答 2-8

由**定义 2.1 (三对角方程组)**, 本题主对角 $b_i=2$, 下次对角 $a_i=-1$, 上次对角 $c_i=-1$, 右端 $d=\left(0,1,0,2.5\right)^{\mathrm T}$, 且满足按行对角占优. 由**定理 2.3 (追赶法)**.

追 (前代 $Ly=d$): $u_1=b_1=2$, $y_1=d_1=0$; $l_2=a_2/u_1=-1/2=-0.5$, $u_2=2-\left(-1\right)\times\left(-0.5\right)=1.5$, $y_2=1-\left(-0.5\right)\times0=1$; $l_3=-1/1.5=-2/3$, $u_3=2-\left(-1\right)\times\left(-2/3\right)=4/3$, $y_3=0-\left(-2/3\right)\times1=2/3$; $l_4=-1/\left(4/3\right)=-3/4$, $u_4=2-\left(-1\right)\times\left(-3/4\right)=5/4$, $y_4=2.5-\left(-3/4\right)\times\left(2/3\right)=3$.

赶 (回代 $Ux=y$): $x_4=y_4/u_4=3/1.25=2.4$; $x_3=\left[y_3-c_3 x_4\right]/u_3=\left[2/3-\left(-1\right)\times2.4\right]/\left(4/3\right)=2.3$; $x_2=\left[1-\left(-1\right)\times2.3\right]/1.5=2.2$; $x_1=\left[0-\left(-1\right)\times2.2\right]/2=1.1$.

故 $x=\left(1.1,2.2,2.3,2.4\right)^{\mathrm T}$. $\blacksquare$
