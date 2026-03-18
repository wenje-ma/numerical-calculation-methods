# week3

> **定理 2.4 (Cholesky 分解)**
> 
> 设 $A$ 是对称正定矩阵, 则存在唯一的非奇异下三角形矩阵 $L$, 使得 $A=LL^{\mathrm{T}}$, 且 $L$ 的对角元全为正. (教材 $\S2.4$, p45)

> **定义 2.4 (条件数)**
> 
> 对非奇异矩阵 $A$, 称数 $\left\|A\right\|\left\|A^{-1}\right\|$ 为矩阵 $A$ 的条件数, 记为 $\operatorname{cond}\left(A\right)$. (教材 $\S2.5$, p55)

> **定义 3.3 (谱半径)**
> 
> 设 $A$ 为 $n$ 阶方阵, $\lambda_i$ ($i=1,2,\ldots,n$) 为 $A$ 的特征值, 称特征值绝对值的最大值 $\rho\left(A\right)=\max_i\left|\lambda_i\right|$ 为 $A$ 的谱半径. (教材 $\S3.2$, p81)

> **定理 3.6 (迭代法收敛的充要条件)**
> 
> 对任意初始向量 $x^{\left(0\right)}$ 和右端项 $g$, 由迭代格式 $x^{\left(k+1\right)}=Mx^{\left(k\right)}+g$ 产生的向量序列 $\left\{x^{\left(k\right)}\right\}$ 收敛的充要条件是 $\rho\left(M\right)<1$. (教材 $\S3.2$, p82)

## 习题 2-6 (平方根法与改进平方根法)

分别用平方根法和改进平方根法求解方程组

$$
\begin{pmatrix}1&2&1&-3\\2&5&0&-5\\1&0&14&1\\-3&-5&1&15\end{pmatrix}\begin{pmatrix}x_1\\x_2\\x_3\\x_4\end{pmatrix}=\begin{pmatrix}1\\2\\16\\8\end{pmatrix}.
$$

### 解答 2-6

先证 $A$ 对称正定: $A$ 显然对称, 顺序主子式

$$
D_1=1>0,\quad D_2=\begin{vmatrix}1&2\\2&5\end{vmatrix}=1>0,\quad D_3=\begin{vmatrix}1&2&1\\2&5&0\\1&0&14\end{vmatrix}=9>0,
$$

$D_4=\det A=9>0$, 故 $A$ 正定, 由**定理 2.4 (Cholesky 分解)**, $A=LL^{\mathrm{T}}$ 且 $L$ 唯一, 对角元为正.

(1) 平方根法. 按 $l_{jk}=\left(a_{jk}-\sum_{s<k}l_{js}l_{ks}\right)/l_{kk}$, $l_{kk}=\sqrt{a_{kk}-\sum_{s<k}l_{ks}^{2}}$ 逐列计算:

$$
l_{11}=1,\quad l_{21}=2,\quad l_{31}=1,\quad l_{41}=-3;
$$

$$
l_{22}=\sqrt{5-4}=1,\quad l_{32}=\frac{0-2\times1}{1}=-2,\quad l_{42}=\frac{-5-2\times\left(-3\right)}{1}=1;
$$

$$
l_{33}=\sqrt{14-1-4}=3,\quad l_{43}=\frac{1-1\times\left(-3\right)-\left(-2\right)\times1}{3}=2;
$$

$$
l_{44}=\sqrt{15-9-1-4}=1.
$$

即

$$
L=\begin{pmatrix}1&0&0&0\\2&1&0&0\\1&-2&3&0\\-3&1&2&1\end{pmatrix}.
$$

解 $Ly=b$:

$$
y_1=1,\quad y_2=2-2\times1=0,\quad y_3=\frac{16-1\times1-\left(-2\right)\times0}{3}=5,\quad y_4=8+3\times1-1\times0-2\times5=1.
$$

解 $L^{\mathrm{T}}x=y$:

$$
x_4=\frac{1}{1}=1,\quad x_3=\frac{5-2\times1}{3}=1,\quad x_2=\frac{0-\left(-2\right)\times1-1\times1}{1}=1,\quad x_1=1-2\times1-1\times1+3\times1=1.
$$

$\blacksquare$

(2) 改进平方根法. 把 $A=LL^{\mathrm{T}}$ 改写成 $A=MDM^{\mathrm{T}}$, 其中 $M$ 为单位下三角阵 ($m_{ij}=l_{ij}/l_{jj}$), $D=\operatorname{diag}\left(l_{11}^{2},\ldots,l_{nn}^{2}\right)$:

$$
M=\begin{pmatrix}1&0&0&0\\2&1&0&0\\1&-2&1&0\\-3&1&\frac{2}{3}&1\end{pmatrix},\qquad D=\operatorname{diag}\left(1,1,9,1\right).
$$

解 $Mz=b$:

$$
z_1=1,\quad z_2=2-2\times1=0,\quad z_3=16-1\times1+\frac{2}{3}\times0=15,\quad z_4=8+3\times1-1\times0-\frac{2}{3}\times15=1.
$$

解 $Dw=z$: $w=\left(1,0,\frac{15}{9},1\right)^{\mathrm{T}}=\left(1,0,\frac{5}{3},1\right)^{\mathrm{T}}$. 解 $M^{\mathrm{T}}x=w$:

$$
x_4=1,\quad x_3=\frac{5}{3}-\frac{2}{3}\times1=1,\quad x_2=0-\left(-2\right)\times1-1\times1=1,\quad x_1=1-2\times1-1\times1+3\times1=1.
$$

两种方法给出同一解 $x=\left(1,1,1,1\right)^{\mathrm{T}}$. 代回原方程校验: $1+2+1-3=1$, $2+5-5=2$, $1+14+1=16$, $-3-5+1+15=8$, 全部吻合. 改进平方根法不需要开方, 与平方根法只差一次对角缩放.

$\blacksquare$

## 习题 2-8 (追赶法)

用追赶法解下列方程组:

(1) $\begin{pmatrix}2&-1&0&0\\-1&2&-1&0\\0&-1&2&-1\\0&0&-1&2\end{pmatrix}\begin{pmatrix}x_1\\x_2\\x_3\\x_4\end{pmatrix}=\begin{pmatrix}0\\1\\0\\2.5\end{pmatrix}$;

(2) $\begin{pmatrix}136.01&90.860&0&0\\90.860&98.810&-67.590&0\\0&-67.590&132.01&46.260\\0&0&46.260&177.17\end{pmatrix}\begin{pmatrix}x_1\\x_2\\x_3\\x_4\end{pmatrix}=\begin{pmatrix}-33.254\\49.709\\28.067\\-7.3244\end{pmatrix}$.

### 解答 2-8

追赶法的"追" (消元)为 $u_1=b_1$, $l_i=a_i/u_{i-1}$, $u_i=b_i-l_ic_{i-1}$, $y_1=d_1$, $y_i=d_i-l_iy_{i-1}$; "赶" (回代)为 $x_n=y_n/u_n$, $x_i=\left(y_i-c_ix_{i+1}\right)/u_i$. 两题的系数矩阵都是三对角且严格对角占优 $\left(\left|b_i\right|>\left|a_i\right|+\left|c_i\right|\right)$, 故消元过程不会出现零主元.

(1) $a_i=-1$, $b_i=2$, $c_i=-1$, $d=\left(0,1,0,2.5\right)^{\mathrm{T}}$.

$$
u_1=2,\quad l_2=-\frac{1}{2},\ u_2=2-\left(-\frac{1}{2}\right)\left(-1\right)=\frac{3}{2},\quad l_3=-\frac{2}{3},\ u_3=2-\left(-\frac{2}{3}\right)\left(-1\right)=\frac{4}{3},\quad l_4=-\frac{3}{4},\ u_4=2-\left(-\frac{3}{4}\right)\left(-1\right)=\frac{5}{4};
$$

$$
y_1=0,\quad y_2=1-\left(-\frac{1}{2}\right)\times0=1,\quad y_3=0-\left(-\frac{2}{3}\right)\times1=\frac{2}{3},\quad y_4=2.5-\left(-\frac{3}{4}\right)\times\frac{2}{3}=3.
$$

回代:

$$
x_4=\frac{3}{5/4}=2.4,\quad x_3=\frac{\frac{2}{3}+2.4}{4/3}=2.3,\quad x_2=\frac{1+2.3}{3/2}=2.2,\quad x_1=\frac{0+2.2}{2}=1.1.
$$

即 $x=\left(1.1,2.2,2.3,2.4\right)^{\mathrm{T}}$. 校验: $2\times1.1-2.2=0$, $-1.1+4.4-2.3=1$, $-2.2+4.6-2.4=0$, $-2.3+4.8=2.5$.

$\blacksquare$

(2) $a=\left(90.860,-67.590,46.260\right)^{\mathrm{T}}$, $b=\left(136.01,98.810,132.01,177.17\right)^{\mathrm{T}}$, $c=\left(90.860,-67.590,46.260\right)^{\mathrm{T}}$, 计算保留 $4$ 位小数.

$$
u_1=136.01,\quad l_2=\frac{90.860}{136.01}=0.6680,\quad u_2=98.810-0.6680\times90.860=38.1120;
$$

$$
l_3=\frac{-67.590}{38.1120}=-1.7735,\quad u_3=132.01-\left(-1.7735\right)\times\left(-67.590\right)=12.1419;
$$

$$
l_4=\frac{46.260}{12.1419}=3.8099,\quad u_4=177.17-3.8099\times46.260=0.9222.
$$

$$
y_1=-33.254,\quad y_2=49.709-0.6680\times\left(-33.254\right)=71.9240,
$$

$$
y_3=28.067-\left(-1.7735\right)\times71.9240=155.6212,\quad y_4=-7.3244-3.8099\times155.6212=-600.2319.
$$

回代:

$$
x_4=\frac{-600.2319}{0.9222}=-650.8975,\quad x_3=\frac{155.6212+46.260\times650.8975}{12.1419}=2492.6974,
$$

$$
x_2=\frac{71.9240+67.590\times2492.6974}{38.1120}=4422.5833,\quad x_1=\frac{-33.254-90.860\times4422.5833}{136.01}=-2954.7031.
$$

即 $x\approx\left(-2954.7031,\ 4422.5833,\ 2492.6974,\ -650.8975\right)^{\mathrm{T}}$. 代回校验, 四个方程的残量都在 $10^{-4}$ 以内. 解的量级远大于右端, 原因是 $u_4=0.9222$ 与右端 $177.17$ 相比很小, 说明该矩阵虽严格对角占优却接近奇异, 追赶法在这里仍稳定, 但解的敏感性很高.

$\blacksquare$

## 习题 2-10 (求 $\operatorname{cond}_1$ 与 $\operatorname{cond}_\infty$)

已知

$$
A=\begin{pmatrix}6&13&-17\\13&29&-38\\-17&-38&50\end{pmatrix},
$$

求 $\operatorname{cond}\left(A\right)_1$ 及 $\operatorname{cond}\left(A\right)_\infty$, 并说明方程组 $Ax=b$ 是否病态.

### 解答 2-10

由**定义 2.4 (条件数)**, $\operatorname{cond}\left(A\right)_1=\left\|A\right\|_1\left\|A^{-1}\right\|_1$, $\operatorname{cond}\left(A\right)_\infty=\left\|A\right\|_\infty\left\|A^{-1}\right\|_\infty$.

先算 $\det A$:

$$
\det A=6\left(29\times50-38^{2}\right)-13\left(13\times50-38\times17\right)+\left(-17\right)\left(13\times\left(-38\right)-29\times\left(-17\right)\right)=6\times54-13\times4-17\times1=1.
$$

按伴随矩阵求 $A^{-1}$: 各代数余子式为 $A_{11}=54$, $A_{12}=-4$, $A_{13}=1$, $A_{21}=-4$, $A_{22}=11$, $A_{23}=-7$, $A_{31}=1$, $A_{32}=7$, $A_{33}=5$, 转置后除以 $\det A=1$ 得

$$
A^{-1}=\begin{pmatrix}6&-4&-1\\-4&11&7\\-1&7&5\end{pmatrix}.
$$

校验 $AA^{-1}=I$ 的第一行: $\left(6,13,-17\right)\cdot\left(6,-4,-1\right)=36-52+17=1$; $\left(6,13,-17\right)\cdot\left(-4,11,7\right)=-24+143-119=0$; $\left(6,13,-17\right)\cdot\left(-1,7,5\right)=-6+91-85=0$, 其余两行同样逐个校验均合, 故 $A^{-1}$ 无误.

列和与行和:

$$
\left\|A\right\|_1=\max\left\{6+13+17,\ 13+29+38,\ 17+38+50\right\}=\max\left\{36,80,105\right\}=105,
$$

$$
\left\|A^{-1}\right\|_1=\max\left\{6+4+1,\ 4+11+7,\ 1+7+5\right\}=\max\left\{11,22,13\right\}=22.
$$

由对称性 $\left\|A\right\|_\infty=\left\|A\right\|_1=105$, 而

$$
\left\|A^{-1}\right\|_\infty=\max\left\{11,22,13\right\}=22,
$$

故

$$
\operatorname{cond}\left(A\right)_1=\operatorname{cond}\left(A\right)_\infty=105\times22=2310.
$$

$2310$ 属中等偏大的条件数 (量级 $10^{3}$), 按经验 $\operatorname{cond}\left(A\right)\gg1$ 时方程组病态, 本题的 $2310$ 意味着右端 $b$ 的相对扰动可被放大约 $2.3\times10^{3}$ 倍, 已属病态范畴, 只是还不算极端.

$\blacksquare$

## 习题 3-3 (Jacobi 与 Gauss-Seidel 迭代四次比较)

用 Jacobi 迭代法和 Gauss-Seidel 迭代法求解方程组

$$
\begin{cases}x_1+2x_2-2x_3=1,\\ x_1+x_2+x_3=1,\\ 2x_1+2x_2+x_3=1,\end{cases}
$$

取初值 $x^{\left(0\right)}=\left(0,0,0\right)^{\mathrm{T}}$, 迭代 $4$ 次, 并比较它们的计算结果.

### 解答 3-3

系数矩阵 $A=\begin{pmatrix}1&2&-2\\1&1&1\\2&2&1\end{pmatrix}$, 对角元全为 $1$, 但 $A$ 不按行严格对角占优 ($\left|a_{11}\right|=1<2+2$), 收敛性须直接由谱半径判定.

(1) Jacobi 迭代. 迭代格式 $x_i^{\left(k+1\right)}=b_i-\sum_{j\ne i}a_{ij}x_j^{\left(k\right)}$, 即

$$
x_1^{\left(k+1\right)}=1-2x_2^{\left(k\right)}+2x_3^{\left(k\right)},\quad x_2^{\left(k+1\right)}=1-x_1^{\left(k\right)}-x_3^{\left(k\right)},\quad x_3^{\left(k+1\right)}=1-2x_1^{\left(k\right)}-2x_2^{\left(k\right)}.
$$

逐次计算:

$$
x^{\left(1\right)}=\left(1,1,1\right)^{\mathrm{T}},\quad x^{\left(2\right)}=\left(1,-1,-3\right)^{\mathrm{T}},\quad x^{\left(3\right)}=\left(-3,3,1\right)^{\mathrm{T}},\quad x^{\left(4\right)}=\left(-3,3,1\right)^{\mathrm{T}}.
$$

第 $4$ 次与前一次完全相同. 而 $\left(-3,3,1\right)$ 满足

$$
-3+6-2=1,\quad -3+3+1=1,\quad -6+6+1=1,
$$

即它就是精确解, 故 Jacobi 迭代在第 $3$ 次已到精确解, 第 $4$ 次只是重复.

$\blacksquare$

(2) Gauss-Seidel 迭代. 迭代格式按分量即时更新:

$$
x_1^{\left(k+1\right)}=1-2x_2^{\left(k\right)}+2x_3^{\left(k\right)},\quad x_2^{\left(k+1\right)}=1-x_1^{\left(k+1\right)}-x_3^{\left(k\right)},\quad x_3^{\left(k+1\right)}=1-2x_1^{\left(k+1\right)}-2x_2^{\left(k+1\right)}.
$$

逐次计算:

$$
x^{\left(1\right)}=\left(1,0,-1\right)^{\mathrm{T}},\quad x^{\left(2\right)}=\left(-1,3,-3\right)^{\mathrm{T}},\quad x^{\left(3\right)}=\left(-11,15,-7\right)^{\mathrm{T}},\quad x^{\left(4\right)}=\left(-43,51,-15\right)^{\mathrm{T}}.
$$

分量绝对值逐次增大, 序列发散.

$\blacksquare$

(3) 比较与收敛性判定. 由**定义 3.3 (谱半径)**, 只需看迭代矩阵的谱半径.

Jacobi 迭代矩阵

$$
B_J=D^{-1}\left(L+U\right)=\begin{pmatrix}0&-2&2\\-1&0&-1\\-2&-2&0\end{pmatrix},\qquad B_J^{2}=\begin{pmatrix}-2&-4&2\\2&4&-2\\2&4&-2\end{pmatrix},\qquad B_J^{3}=O,
$$

$B_J$ 是幂零矩阵, $\rho\left(B_J\right)=0<1$, 由**定理 3.6 (迭代法收敛的充要条件)**, Jacobi 迭代对任意初值收敛, 且因 $B_J^{3}=O$ 必在 $3$ 步内到精确解 (本题恰好第 $3$ 步到达).

Gauss-Seidel 迭代矩阵

$$
B_{GS}=\left(D+L\right)^{-1}\left(-U\right)=\begin{pmatrix}0&-2&2\\0&2&-3\\0&0&2\end{pmatrix},
$$

其特征多项式为 $\lambda\left(\lambda-2\right)^{2}$, 故 $\rho\left(B_{GS}\right)=2>1$, 由**定理 3.6 (迭代法收敛的充要条件)**, Gauss-Seidel 迭代对任意初值发散, 与第 (2) 步算出的发散序列一致.

结论: 同一个方程组上 Jacobi 收敛而 Gauss-Seidel 发散, 说明"Gauss-Seidel 一定不慢于 Jacobi"只在特定矩阵类 (如对称正定, 严格对角占优) 才成立; 本题 $A$ 不属于这些类, 比较结果与直觉相反.

$\blacksquare$
