# 作业 2

> **算法 2.1** (高斯消去法) <br>将方程组的增广矩阵逐列消元, 化为等价的上三角形方程组, 再按变量逆序回代求解. 第 $k$ 步以 $a_{kk}^{\left(k\right)}\ne0$ 为主元, 乘子 $l_{ik}=a_{ik}^{\left(k\right)}/a_{kk}^{\left(k\right)}$; 回代公式为 $$x_n=\frac{b_n^{\left(n\right)}}{a_{nn}^{\left(n\right)}},\qquad x_k=\frac{b_k^{\left(k\right)}-\sum_{j=k+1}^{n}a_{kj}^{\left(k\right)}x_j}{a_{kk}^{\left(k\right)}}\ \left(k=n-1,\dots,1\right).$$ 为抑制小主元引起的舍入误差增长, 可在第 $k$ 列 (列主元素法) 或全部剩余元素 (全主元素法) 中选绝对值最大者, 作相应行 (列) 交换后再消元.

> **定理 2.1** (直接三角分解的存在唯一性) <br>设 $A$ 为 $n$ 阶方阵, 若 $A$ 的各阶顺序主子式 $\det A_i\ \left(i=1,2,\dots,n-1\right)$ 均不为零, 则 $A$ 有唯一的杜利特尔分解 $A=LU$, 其中 $L$ 为单位下三角形矩阵, $U$ 为上三角形矩阵. 此时解 $Ax=b$ 等价于依次求解 $$Ly=b,\qquad Ux=y.$$

> **式(2.10)** (紧凑格式三角分解计算公式) <br>按"第 1 行, 第 1 列, 第 2 行, 第 2 列, ..."的顺序, 由比较 $A=LU$ 得 $$u_{1j}=a_{1j},\qquad l_{i1}=\frac{a_{i1}}{u_{11}},\qquad u_{rj}=a_{rj}-\sum_{k=1}^{r-1}l_{rk}u_{kj},\qquad l_{ir}=\frac{a_{ir}-\sum_{k=1}^{r-1}l_{ik}u_{kr}}{u_{rr}}.$$ 求解时把右端向量 $b$ 列在最后, 按同一紧凑格式先前代求 $y$, 再由 $x_k=\left(y_k-\sum_{j=k+1}^{n}u_{kj}x_j\right)/u_{kk}$ 回代求 $x$.

> **定理 2.4** (对称正定矩阵的乔列斯基分解) <br>设 $A$ 为对称正定矩阵, 则存在唯一的对角元皆为正数的下三角形矩阵 $L$, 使 $A=LL^{\mathrm T}$, 即平方根法. 由比较 $A=LL^{\mathrm T}$ 得 $$l_{kk}=\left(a_{kk}-\sum_{j=1}^{k-1}l_{kj}^{2}\right)^{1/2},\qquad l_{ik}=\frac{a_{ik}-\sum_{j=1}^{k-1}l_{ij}l_{kj}}{l_{kk}}.$$ 求解 $Ax=b$ 化为依次解 $Ly=b$ 与 $L^{\mathrm T}x=y$. 又 $A$ 可分解为 $A=LDL^{\mathrm T}$ (改进平方根法, $L$ 为单位下三角, $D$ 为对角阵) , 运算中无须开方.

> **定义 2.1** (三对角方程组) <br>系数矩阵 $A$ 的非零元素只分布在主对角线及相邻两条次对角线上: $$A=\begin{bmatrix}b_1&c_1&&\\a_2&b_2&c_2&\\&\ddots&\ddots&\ddots\\&&a_n&b_n\end{bmatrix}.$$ **定理 2.3** (追赶法) 当 $A$ 满足按行对角占优条件时, 可分解为 $A=LU$, 其中 $u_1=b_1$, $l_i=a_i/u_{i-1}$, $u_i=b_i-c_{i-1}l_i$; "追" (前代) 为 $y_1=d_1$, $y_k=d_k-l_k y_{k-1}$, "赶" (回代) 为 $$x_n=\frac{y_n}{u_n},\qquad x_k=\frac{y_k-c_k x_{k+1}}{u_k}\ \left(k=n-1,\dots,1\right).$$

> **定理 2.5** (矩阵的算子范数) <br>由向量范数诱导的矩阵范数为 $\left\|A\right\|=\max_{\left\|x\right\|=1}\left\|Ax\right\|$, 且满足相容性 $\left\|Ax\right\|\le\left\|A\right\|\left\|x\right\|$. 常用的 1-范数 (列范数) 与 $\infty$-范数 (行范数) 为 $$\left\|A\right\|_1=\max_{1\le j\le n}\sum_{i=1}^{n}\left|a_{ij}\right|,\qquad \left\|A\right\|_\infty=\max_{1\le i\le n}\sum_{j=1}^{n}\left|a_{ij}\right|.$$

> **定义 2.4** (矩阵的条件数) <br>对非奇异矩阵 $A$, 称 $\mathrm{cond}\left(A\right)=\left\|A\right\|\,\left\|A^{-1}\right\|$ 为 $A$ 的条件数, 特别地 $$\mathrm{cond}\left(A\right)_1=\left\|A\right\|_1\left\|A^{-1}\right\|_1,\qquad \mathrm{cond}\left(A\right)_\infty=\left\|A\right\|_\infty\left\|A^{-1}\right\|_\infty.$$ 条件数越大, 方程组 $Ax=b$ 关于右端项或系数矩阵扰动的"病态"越严重, 且恒有 $\mathrm{cond}\left(A\right)\ge1$.

### 习题一 (习题 2-1)

分别用高斯消去法, 列主元素法和全主元素法解下列方程组, 计算过程保留 3 位小数: $$
\begin{cases}2x_1+6x_2-4x_3=4,\\x_1+4x_2-5x_3=3,\\6x_1-x_2+18x_3=2.\end{cases}
$$ (仅做第 (1) 小题) ### 解答 习题一

方程组的增广矩阵为

$$
\overline A=\begin{bmatrix}2&6&-4&4\\1&4&-5&3\\6&-1&18&2\end{bmatrix}.
$$

先按**算法 2.1** (高斯消去法) 消元. 第 1 步取 $a_{11}=2$ 为主元, 乘子 $l_{21}=1/2=0.500$, $l_{31}=6/2=3.000$, 第 2, 3 行分别减去第 1 行的相应倍数, 得

$$
\begin{bmatrix}2&6&-4&4\\0&1&-3&1\\0&-19&30&-10\end{bmatrix}.
$$

第 2 步取 $a_{22}=1$ 为主元, 乘子 $l_{32}=-19/1=-19.000$, 第 3 行加上第 2 行的 $19$ 倍, 得上三角形矩阵

$$
\begin{bmatrix}2&6&-4&4\\0&1&-3&1\\0&0&-27&9\end{bmatrix}.
$$

回代: $x_3=9/\left(-27\right)=-0.333$, $x_2=\left[1-\left(-3\right)\times\left(-0.333\right)\right]/1=0.000$, $x_1=\left[4-6\times0-\left(-4\right)\times\left(-0.333\right)\right]/2=1.333$.

列主元素法在第 1 列中选绝对值最大者 $\left|6\right|$ 作行交换, 全主元素法在全部剩余元素中选最大者作行, 列交换; 本题主元 $2,1,-27$ 均非小量, 选主元交换后消元所得上三角形方程组与上相同, 回代结果一致. 故

$$
x_1=1.333,\qquad x_2=0.000,\qquad x_3=-0.333.
$$

$\blacksquare$

### 习题二 (习题 2-2)

用三角分解法求解题 1 中的方程组.

### 解答 习题二

由**定理 2.1** (直接三角分解的存在唯一性) 及**式(2.10)** (紧凑格式三角分解计算公式) , 对题 1 的两个方程组分别作杜利特尔分解 $A=LU$, 再依次解 $Ly=b$, $Ux=y$.

第 (1) 个方程组 $A=\begin{bmatrix}2&6&-4\\1&4&-5\\6&-1&18\end{bmatrix}$, $b=\left(4,3,2\right)^{\mathrm T}$. 紧凑格式算得

$$
L=\begin{bmatrix}1&0&0\\0.5&1&0\\3&-19&1\end{bmatrix},\qquad U=\begin{bmatrix}2&6&-4\\0&1&-3\\0&0&-27\end{bmatrix}.
$$

前代: $y_1=4$, $y_2=3-0.5\times4=1$, $y_3=2-3\times4-\left(-19\right)\times1=9$. 回代: $x_3=9/\left(-27\right)=-1/3$, $x_2=\left[1-\left(-3\right)\times\left(-1/3\right)\right]/1=0$, $x_1=\left[4-\left(-4\right)\times\left(-1/3\right)\right]/2=4/3$. 即 $x=\left(4/3,0,-1/3\right)^{\mathrm T}$.

第 (2) 个方程组 $A=\begin{bmatrix}2&1&2\\4&3&1\\6&1&5\end{bmatrix}$, $b=\left(6,11,13\right)^{\mathrm T}$, 分解得

$$
L=\begin{bmatrix}1&0&0\\2&1&0\\3&-2&1\end{bmatrix},\qquad U=\begin{bmatrix}2&1&2\\0&1&-3\\0&0&-7\end{bmatrix}.
$$

前代得 $y=\left(6,-1,-7\right)^{\mathrm T}$, 回代得 $x_3=\left(-7\right)/\left(-7\right)=1$, $x_2=\left[-1-\left(-3\right)\times1\right]/1=2$, $x_1=\left[6-1\times2-2\times1\right]/2=1$. 即 $x=\left(1,2,1\right)^{\mathrm T}$.
$\blacksquare$

### 习题三 (习题 2-3)

用紧凑格式解下列方程组, 并写出 $L,U$ 矩阵: $$
\begin{bmatrix}1&2&3&4\\1&4&9&16\\1&8&27&64\\1&16&81&256\end{bmatrix}\begin{bmatrix}x_1\\x_2\\x_3\\x_4\end{bmatrix}=\begin{bmatrix}2\\10\\44\\190\end{bmatrix}.
$$

### 解答 习题三

由**式(2.10)** (紧凑格式三角分解计算公式) , 按"第 1 行第 1 列, 第 2 行第 2 列, ..."的顺序分解 $A=LU$.

第 1 行, 第 1 列: $U$ 的第 1 行为 $\left(1,2,3,4\right)$, $l_{i1}=a_{i1}/u_{11}=1\ \left(i=2,3,4\right)$.

第 2 行, 第 2 列: $u_{22}=4-1\times2=2$, $u_{23}=9-1\times3=6$, $u_{24}=16-1\times4=12$; $l_{32}=\left(8-1\times2\right)/2=3$, $l_{42}=\left(16-1\times2\right)/2=7$.

第 3 行, 第 3 列: $u_{33}=27-1\times3-3\times6=6$, $u_{34}=64-1\times4-3\times12=24$; $l_{43}=\left(81-1\times3-7\times6\right)/6=6$.

第 4 行: $u_{44}=256-1\times4-7\times12-6\times24=24$.

故

$$
L=\begin{bmatrix}1&0&0&0\\1&1&0&0\\1&3&1&0\\1&7&6&1\end{bmatrix},\qquad U=\begin{bmatrix}1&2&3&4\\0&2&6&12\\0&0&6&24\\0&0&0&24\end{bmatrix}.
$$

把 $b=\left(2,10,44,190\right)^{\mathrm T}$ 作为最后一列, 前代得 $y_1=2$, $y_2=10-1\times2=8$, $y_3=44-1\times2-3\times8=18$, $y_4=190-1\times2-7\times8-6\times18=24$. 回代: $x_4=24/24=1$, $x_3=\left(18-24\times1\right)/6=-1$, $x_2=\left[8-6\times\left(-1\right)-12\times1\right]/2=1$, $x_1=2-2\times1-3\times\left(-1\right)-4\times1=-1$.

所以 $x=\left(-1,1,-1,1\right)^{\mathrm T}$. $\blacksquare$

### 习题四 (习题 2-6)

分别用平方根法和改进平方根法求解方程组: $$
\begin{bmatrix}1&2&1&-3\\2&5&0&-5\\1&0&14&1\\-3&-5&1&15\end{bmatrix}\begin{bmatrix}x_1\\x_2\\x_3\\x_4\end{bmatrix}=\begin{bmatrix}1\\2\\16\\8\end{bmatrix}.
$$

### 解答 习题四

系数矩阵对称, 且各阶顺序主子式均为正, 由**定理 2.4** (对称正定矩阵的乔列斯基分解) 可作 $A=LL^{\mathrm T}$.

平方根法: 按列计算 $L$ 的元素. $l_{11}=\sqrt{1}=1$, $l_{21}=2/1=2$, $l_{31}=1/1=1$, $l_{41}=-3/1=-3$; $l_{22}=\sqrt{5-2^{2}}=1$, $l_{32}=\left(0-1\times2\right)/1=-2$, $l_{42}=\left(-5-\left(-3\right)\times2\right)/1=1$; $l_{33}=\sqrt{14-1^{2}-\left(-2\right)^{2}}=3$, $l_{43}=\left[1-\left(-3\right)\times1-1\times\left(-2\right)\right]/3=2$; $l_{44}=\sqrt{15-\left(-3\right)^{2}-1^{2}-2^{2}}=1$. 故

$$
L=\begin{bmatrix}1&0&0&0\\2&1&0&0\\1&-2&3&0\\-3&1&2&1\end{bmatrix}.
$$

解 $Ly=b$: $y_1=1$, $y_2=\left(2-2\times1\right)/1=0$, $y_3=\left[16-1\times1-\left(-2\right)\times0\right]/3=5$, $y_4=\left[8-\left(-3\right)\times1-1\times0-2\times5\right]/1=1$. 再解 $L^{\mathrm T}x=y$: $x_4=1$, $x_3=\left(5-2\times1\right)/3=1$, $x_2=0-\left(-2\right)\times1-1\times1=1$, $x_1=1-2\times1-1\times1-\left(-3\right)\times1=1$.

改进平方根法: 作 $A=\widetilde L D\widetilde L^{\mathrm T}$, 其中 $D=\mathrm{diag}\left(1,1,9,1\right)$, 单位下三角阵 $\widetilde L$ 的非对角元为上述 $L$ 各列除以该列对角元 $\sqrt{d_k}$, 即 $l_{21}=2$, $l_{31}=1$, $l_{41}=-3$, $l_{32}=-2$, $l_{42}=1$, $l_{43}=2/3$. 前代 $Ly=b$ 得 $y=\left(1,0,15,1\right)^{\mathrm T}$, 再由 $x_k=y_k/d_k-\sum_{j=k+1}^{n}l_{jk}x_j$ 回代: $x_4=1$, $x_3=15/9-\left(2/3\right)\times1=1$, $x_2=0-\left(-2\right)\times1-1\times1=1$, $x_1=1-2\times1-1\times1-\left(-3\right)\times1=1$. 两种方法结果一致.

故 $x=\left(1,1,1,1\right)^{\mathrm T}$. $\blacksquare$

### 习题五 (习题 2-8)

用追赶法解下列方程组: $$
\begin{bmatrix}2&-1&0&0\\-1&2&-1&0\\0&-1&2&-1\\0&0&-1&2\end{bmatrix}\begin{bmatrix}x_1\\x_2\\x_3\\x_4\end{bmatrix}=\begin{bmatrix}0\\1\\0\\2.5\end{bmatrix}.
$$ (仅做第 (1) 小题) ### 解答 习题五

由**定义 2.1** (三对角方程组) , 本题主对角 $b_i=2$, 下次对角 $a_i=-1$, 上次对角 $c_i=-1$, 右端 $d=\left(0,1,0,2.5\right)^{\mathrm T}$, 且满足按行对角占优. 由**定理 2.3** (追赶法) .

追 (前代 $Ly=d$) : $u_1=b_1=2$, $y_1=d_1=0$; $l_2=a_2/u_1=-1/2=-0.5$, $u_2=2-\left(-1\right)\times\left(-0.5\right)=1.5$, $y_2=1-\left(-0.5\right)\times0=1$; $l_3=-1/1.5=-2/3$, $u_3=2-\left(-1\right)\times\left(-2/3\right)=4/3$, $y_3=0-\left(-2/3\right)\times1=2/3$; $l_4=-1/\left(4/3\right)=-3/4$, $u_4=2-\left(-1\right)\times\left(-3/4\right)=5/4$, $y_4=2.5-\left(-3/4\right)\times\left(2/3\right)=3$.

赶 (回代 $Ux=y$) : $x_4=y_4/u_4=3/1.25=2.4$; $x_3=\left[y_3-c_3 x_4\right]/u_3=\left[2/3-\left(-1\right)\times2.4\right]/\left(4/3\right)=2.3$; $x_2=\left[1-\left(-1\right)\times2.3\right]/1.5=2.2$; $x_1=\left[0-\left(-1\right)\times2.2\right]/2=1.1$.

故 $x=\left(1.1,2.2,2.3,2.4\right)^{\mathrm T}$. $\blacksquare$

### 习题六 (习题 2-10)

已知

$$
A=\begin{bmatrix}6&13&-17\\13&29&-38\\-17&-38&50\end{bmatrix},
$$

求 $\mathrm{cond}\left(A\right)_1$ 及 $\mathrm{cond}\left(A\right)_\infty$, 并说明方程组 $Ax=b$ 是否病态.

### 解答 习题六

由**定理 2.5** (矩阵的算子范数) . 对 $A$, 各列绝对值之和分别为 $6+13+17=36$, $13+29+38=80$, $17+38+50=105$, 故 $\left\|A\right\|_1=\max=105$; 各行绝对值之和分别为 $36$, $80$, $105$, 故 $\left\|A\right\|_\infty=105$.

又 $\det A=1$, 求得

$$
A^{-1}=\begin{bmatrix}6&-4&-1\\-4&11&7\\-1&7&5\end{bmatrix}.
$$

对 $A^{-1}$, 各列绝对值之和为 $11$, $22$, $13$, 故 $\left\|A^{-1}\right\|_1=22$; 各行绝对值之和为 $11$, $22$, $13$, 故 $\left\|A^{-1}\right\|_\infty=22$.

由**定义 2.4** (矩阵的条件数) , $$
\mathrm{cond}\left(A\right)_1=\left\|A\right\|_1\left\|A^{-1}\right\|_1=105\times22=2310,
$$

$$
\mathrm{cond}\left(A\right)_\infty=\left\|A\right\|_\infty\left\|A^{-1}\right\|_\infty=105\times22=2310.
$$

条件数约为 $2.3\times10^{3}$, 远大于 $1$, 故方程组 $Ax=b$ 是病态方程组, 右端项或系数矩阵的微小扰动会被放大约千倍. $\blacksquare$
