# 数值计算方法

## 绪论与有效数字

**定义 1.1** (绝对误差与误差限)

设 $x^{*}$ 为准确值 $x$ 的一个近似值, 称 $e\left(x^{*}\right)=x-x^{*}$ 为近似值 $x^{*}$ 的绝对误差, 简称误差. 一般情况下准确值难以求出, 从而也不能算出绝对误差 $e\left(x^{*}\right)$ 的准确值, 但可以根据测量工具或计算的情况估计出它的取值范围, 即估计出误差绝对值的一个上界 $\varepsilon$:

$$
\left|e\left(x^{*}\right)\right|=\left|x-x^{*}\right|\le\varepsilon.
$$

通常称 $\varepsilon$ 为近似值 $x^{*}$ 的绝对误差限, 简称误差限.

**定义 1.2** (相对误差与相对误差限)

设 $x^{*}$ 为准确值 $x$ 的近似值, 称绝对误差与准确值之比为近似值 $x^{*}$ 的相对误差, 记为 $e_r\left(x^{*}\right)$, 即

$$
e_r\left(x^{*}\right)=\frac{e\left(x^{*}\right)}{x}=\frac{x-x^{*}}{x}.
$$

由于在计算过程中准确值 $x$ 总是未知的, 故一般取相对误差为

$$
e_r\left(x^{*}\right)=\frac{e\left(x^{*}\right)}{x^{*}}.
$$

同样, 相对误差也只能估计其上限. 如果存在正数 $\varepsilon_r$, 使得

$$
\left|e_r\left(x^{*}\right)\right|=\left|\frac{e\left(x^{*}\right)}{x^{*}}\right|\le\varepsilon_r,
$$

则称 $\varepsilon_r$ 为 $x^{*}$ 的相对误差限.

**定义 1.3** (有效数字)

如果近似值 $x^{*}$ 的误差限是 $\frac{1}{2}\times10^{-n}$, 则称 $x^{*}$ 准确到小数点后第 $n$ 位, 并从第一个非零数字到这一位的所有数字均称为有效数字. 一般地, 如果近似值 $x^{*}$ 的规格化形式为

$$
x^{*}=\pm0.a_1a_2\cdots a_n\cdots\times10^{m},
$$

其中 $m$ 为整数, $a_1\ne0$, $a_i\left(i=1,2,\dots\right)$ 为 $0$ 到 $9$ 之间的整数, 且

$$
\left|x-x^{*}\right|\le\frac{1}{2}\times10^{m-n},
$$

则称近似值 $x^{*}$ 有 $n$ 位有效数字.

**定理 1.1** (相对误差限与有效数字的关系)

若 $x$ 的近似值 $x^{*}=\pm0.a_1a_2\cdots a_n\times10^{m}\left(a_1\ne0\right)$ 有 $n$ 位有效数字, 则 $\frac{1}{2a_1}\times10^{-n+1}$ 为其相对误差限. 反之, 若 $x^{*}$ 的相对误差限 $\varepsilon_r$ 满足 $\varepsilon_r\le\frac{1}{2}\times10^{-n}$, 则 $x^{*}$ 至少具有 $n$ 位有效数字.

**误差传播** (基本运算中的误差估计)

设数值计算中求得的解与参量 $x_1,x_2,\dots,x_n$ 有关, 记为 $y=f\left(x_1,x_2,\dots,x_n\right)$, 参量 $x_i$ 的近似值为 $x_i^{*}$. 假定 $f$ 在点 $\left(x_1^{*},x_2^{*},\dots,x_n^{*}\right)$ 处可微, 则当参量误差较小时, 解的绝对误差与相对误差分别为

$$
e\left(y^{*}\right)\approx\sum_{i=1}^n\frac{\partial f\left(x_1^{*},x_2^{*},\dots,x_n^{*}\right)}{\partial x_i}e\left(x_i^{*}\right),
$$

$$
e_r\left(y^{*}\right)\approx\sum_{i=1}^n\frac{\partial f\left(x_1^{*},x_2^{*},\dots,x_n^{*}\right)}{\partial x_i}\frac{x_i^{*}}{f\left(x_1^{*},x_2^{*},\dots,x_n^{*}\right)}e_r\left(x_i^{*}\right).
$$

特别地, 由上述公式可得和, 差, 积, 商之误差公式:

$$
\begin{cases}e\left(x_1\pm x_2\right)=e\left(x_1\right)\pm e\left(x_2\right),\\e_r\left(x_1\pm x_2\right)\approx\frac{x_1}{x_1\pm x_2}e_r\left(x_1\right)\pm\frac{x_2}{x_1\pm x_2}e_r\left(x_2\right),\end{cases}
$$

$$
\begin{cases}e\left(x_1x_2\right)\approx x_2e\left(x_1\right)+x_1e\left(x_2\right),\\e_r\left(x_1x_2\right)\approx e_r\left(x_1\right)+e_r\left(x_2\right),\end{cases}
$$

$$
\begin{cases}e\left(\frac{x_1}{x_2}\right)\approx\frac{1}{x_2}e\left(x_1\right)-\frac{x_1}{x_2^2}e\left(x_2\right),\\e_r\left(\frac{x_1}{x_2}\right)\approx e_r\left(x_1\right)-e_r\left(x_2\right).\end{cases}
$$

因此, 和, 差的误差限不超过各数的误差限之和, 积, 商的相对误差限不超过各数的相对误差限之和.

**1.4 数值计算中应注意的问题** (避免两个相近的数相减)

由**误差传播**, 两数之差 $u=x-y$ 的相对误差为

$$
e_r\left(u\right)\approx\frac{x}{x-y}e_r\left(x\right)-\frac{y}{x-y}e_r\left(y\right).
$$

当 $x$ 与 $y$ 很接近时, $\left|x-y\right|$ 很小, $u$ 的相对误差很大, 有效数字位数将严重丢失. 为避免这种情形出现, 常常改变计算公式.

## 解线性方程组的直接方法

**算法 2.1** (高斯消去法)

将方程组的增广矩阵逐列消元, 化为等价的上三角形方程组, 再按变量逆序回代求解. 第 $k$ 步以 $a_{kk}^{\left(k\right)}\ne0$ 为主元, 乘子 $l_{ik}=a_{ik}^{\left(k\right)}/a_{kk}^{\left(k\right)}$; 回代公式为

$$
x_n=\frac{b_n^{\left(n\right)}}{a_{nn}^{\left(n\right)}},\quad x_k=\frac{b_k^{\left(k\right)}-\sum_{j=k+1}^{n}a_{kj}^{\left(k\right)}x_j}{a_{kk}^{\left(k\right)}}\ \left(k=n-1,\dots,1\right).
$$

为抑制小主元引起的舍入误差增长, 可在第 $k$ 列 (列主元素法) 或全部剩余元素 (全主元素法) 中选绝对值最大者, 作相应行 (列) 交换后再消元.

**定理 2.1** (直接三角分解的存在唯一性)

设 $A$ 为 $n$ 阶方阵, 若 $A$ 的各阶顺序主子式 $\det A_i\ \left(i=1,2,\dots,n-1\right)$ 均不为零, 则 $A$ 有唯一的杜利特尔分解 $A=LU$, 其中 $L$ 为单位下三角形矩阵, $U$ 为上三角形矩阵. 此时解 $Ax=b$ 等价于依次求解

$$
Ly=b,\quad Ux=y.
$$

**式 (2.10)** (紧凑格式三角分解计算公式)

按"第 1 行, 第 1 列, 第 2 行, 第 2 列,..."的顺序, 由比较 $A=LU$ 得

$$
u_{1j}=a_{1j},\quad l_{i1}=\frac{a_{i1}}{u_{11}},\quad u_{rj}=a_{rj}-\sum_{k=1}^{r-1}l_{rk}u_{kj},\quad l_{ir}=\frac{a_{ir}-\sum_{k=1}^{r-1}l_{ik}u_{kr}}{u_{rr}}.
$$

求解时把右端向量 $b$ 列在最后, 按同一紧凑格式先前代求 $y$, 再由 $x_k=\left(y_k-\sum_{j=k+1}^{n}u_{kj}x_j\right)/u_{kk}$ 回代求 $x$.

**定理 2.4** (对称正定矩阵的楚列斯基分解)

设 $A$ 为对称正定矩阵, 则存在唯一的对角元皆为正数的下三角形矩阵 $L$, 使 $A=LL^{\mathrm T}$, 即平方根法. 由比较 $A=LL^{\mathrm T}$ 得

$$
l_{kk}=\left(a_{kk}-\sum_{j=1}^{k-1}l_{kj}^{2}\right)^{1/2},\quad l_{ik}=\frac{a_{ik}-\sum_{j=1}^{k-1}l_{ij}l_{kj}}{l_{kk}}.
$$

求解 $Ax=b$ 化为依次解 $Ly=b$ 与 $L^{\mathrm T}x=y$. 又 $A$ 可分解为 $A=LDL^{\mathrm T}$ (改进平方根法, $L$ 为单位下三角, $D$ 为对角阵), 运算中无须开方.

**定义 2.1** (三对角方程组)

系数矩阵 $A$ 的非零元素只分布在主对角线及相邻两条次对角线上:

$$
A=\begin{bmatrix}b_1&c_1&&\\a_2&b_2&c_2&\\&\ddots&\ddots&\ddots\\&&a_n&b_n\end{bmatrix}.
$$

**定理 2.3** (追赶法) 当 $A$ 满足按行对角占优条件时, 可分解为 $A=LU$, 其中 $u_1=b_1$, $l_i=a_i/u_{i-1}$, $u_i=b_i-c_{i-1}l_i$;"追" (前代) 为 $y_1=d_1$, $y_k=d_k-l_k y_{k-1}$,"赶" (回代) 为

$$
x_n=\frac{y_n}{u_n},\quad x_k=\frac{y_k-c_k x_{k+1}}{u_k}\ \left(k=n-1,\dots,1\right).
$$

**定理 2.5** (矩阵的算子范数)

由向量范数诱导的矩阵范数为 $\left\|A\right\|=\max_{\left\|x\right\|=1}\left\|Ax\right\|$, 且满足相容性 $\left\|Ax\right\|\le\left\|A\right\|\left\|x\right\|$. 常用的 1-范数 (列范数) 与 $\infty$-范数 (行范数) 为

$$
\left\|A\right\|_1=\max_{1\le j\le n}\sum_{i=1}^{n}\left|a_{ij}\right|,\quad \left\|A\right\|_\infty=\max_{1\le i\le n}\sum_{j=1}^{n}\left|a_{ij}\right|.
$$

**定义 2.4** (矩阵的条件数)

对非奇异矩阵 $A$, 称 $\mathrm{cond}\left(A\right)=\left\|A\right\|\,\left\|A^{-1}\right\|$ 为 $A$ 的条件数, 特别地

$$
\mathrm{cond}\left(A\right)_1=\left\|A\right\|_1\left\|A^{-1}\right\|_1,\quad \mathrm{cond}\left(A\right)_\infty=\left\|A\right\|_\infty\left\|A^{-1}\right\|_\infty.
$$

条件数越大, 方程组 $Ax=b$ 关于右端项或系数矩阵扰动的"病态"越严重, 且恒有 $\mathrm{cond}\left(A\right)\ge1$.

## 迭代法

**雅可比迭代法** (式 (3.12))

设方程组 $Ax=b$ 的系数矩阵 $A$ 分裂为 $A=D-L-U$, 其中

$$
D=\mathrm{diag}\left(a_{11},a_{22},\dots,a_{nn}\right).
$$

则雅可比迭代格式为

$$
x^{\left(k+1\right)}=Bx^{\left(k\right)}+g,\quad B=I-D^{-1}A,\quad g=D^{-1}b,
$$

分量形式为

$$
x_i^{\left(k+1\right)}=\frac{1}{a_{ii}}\left(b_i-\sum_{j\ne i}a_{ij}x_j^{\left(k\right)}\right),\ i=1,2,\dots,n.
$$

**高斯-赛德尔迭代法** (式 (3.15))

在雅可比迭代中, 一旦新分量 $x_i^{\left(k+1\right)}$ 算出即立即用于后续分量的计算, 便得高斯-赛德尔迭代法, 其矩阵形式为

$$
x^{\left(k+1\right)}=\left(D-L\right)^{-1}Ux^{\left(k\right)}+\left(D-L\right)^{-1}b,
$$

迭代矩阵为 $M=\left(D-L\right)^{-1}U$.

**松弛迭代法 (逐次超松弛法)** (式 (3.17))

在高斯-赛德尔迭代基础上引入松弛因子 $\omega$, 得

$$
x^{\left(k+1\right)}=\left(D-\omega L\right)^{-1}\left[\left(1-\omega\right)D+\omega U\right]x^{\left(k\right)}+\omega\left(D-\omega L\right)^{-1}b,
$$

迭代矩阵为

$$
M_{\omega}=\left(D-\omega L\right)^{-1}\left[\left(1-\omega\right)D+\omega U\right];
$$

当 $\omega=1$ 时即为高斯-赛德尔迭代法.

**定义 3.3** (谱半径)

设 $A$ 为 $n$ 阶方阵, $\lambda_i\left(i=1,2,\dots,n\right)$ 为 $A$ 的特征值, 称特征值绝对值的最大值为矩阵 $A$ 的谱半径, 记为

$$
\rho\left(A\right)=\max_{1\le i\le n}\left|\lambda_i\right|.
$$

**定理 3.6** (迭代法收敛的充要条件)

对任意初始向量 $x^{\left(0\right)}$ 和右端项 $g$, 由迭代格式 $x^{\left(k+1\right)}=Mx^{\left(k\right)}+g$ 产生的向量序列收敛的充要条件是

$$
\rho\left(M\right)< 1.
$$

**定义 3.4** (对角占优矩阵)

若 $n$ 阶方阵 $A=\left(a_{ij}\right)$ 满足

$$
\left|a_{ii}\right|\ge\sum_{j\ne i}\left|a_{ij}\right|\quad\left(i=1,2,\dots,n\right),
$$

且至少有一个 $i$ 使严格不等式成立, 则称 $A$ 为弱对角占优矩阵; 若对所有 $i$ 均严格成立, 则称 $A$ 为严格对角占优矩阵.

**几个常用的充分收敛条件** (判敛)

设方程组 $Ax=b$: (1) 若 $A$ 为严格对角占优矩阵 (或不可约弱对角占优矩阵), 则雅可比迭代法与高斯-赛德尔迭代法均收敛; (2) 若 $A$ 为对称正定矩阵且 $0< \omega< 2$, 则松弛法收敛 (此条件为充要条件).

## 特征值计算

**幂法** (求按模最大的特征值与特征向量)

设 $n\times n$ 实矩阵 $A$ 的特征值满足 $\left|\lambda_1\right|> \left|\lambda_2\right|\ge\cdots\ge\left|\lambda_n\right|$, 相应特征向量 $u_1,u_2,\dots,u_n$ 线性无关. 取初始向量 $\alpha^{\left(0\right)}\ne0$, 由迭代 $\alpha^{\left(k+1\right)}=A\alpha^{\left(k\right)}$ (式 (4.1)) 产生向量序列, 当 $k$ 充分大时 $\alpha^{\left(k+1\right)}$ 即可作为 $\lambda_1$ 相应特征向量的近似, 且

$$
\lambda_1\approx\frac{\alpha_i^{\left(k+1\right)}}{\alpha_i^{\left(k\right)}}
$$

(式 (4.3)). 为避免迭代中溢出或归零, 实际计算每次归一化:

$$
\alpha^{\left(k+1\right)}=Ay^{\left(k\right)},\quad y^{\left(k+1\right)}=\frac{\alpha^{\left(k+1\right)}}{\max_i\left|\alpha_i^{\left(k+1\right)}\right|},\quad\lambda_1\approx\max_i\left|\alpha_i^{\left(k+1\right)}\right|
$$

(式 (4.5)). 收敛速度由收敛因子 $\left|\lambda_2/\lambda_1\right|$ 决定, 其值越小收敛越快.

**幂法的艾特肯加速** (算法4.2)

若幂法产生的特征值近似序列 $\left\{a_k\right\}$ 线性收敛到 $a$, 即 $\lim_{k\to\infty}\frac{a_{k+1}-a}{a_k-a}=c\ne1$, 则当 $k$ 充分大时

$$
\widehat a_k=a_k-\frac{\left(a_{k+1}-a_k\right)^2}{a_{k+2}-2a_{k+1}+a_k}
$$

比 $\left\{a_k\right\}$ 更快地收敛到 $a$, 将其用于幂法所产生的序列即可加速收敛.

**反幂法** (式 (4.10), 算法4.3)

若 $\lambda,u$ 为 $A$ 的特征值与特征向量, 则 $A^{-1}u=\frac{1}{\lambda}u$, 即 $A^{-1}$ 的特征值为 $A$ 特征值的倒数而特征向量不变. 实际运算以解方程组

$$
A\alpha^{\left(k+1\right)}=\alpha^{\left(k\right)}
$$

(式 (4.10)) 代替 $\alpha^{\left(k+1\right)}=A^{-1}\alpha^{\left(k\right)}$. 若已知 $A$ 的某特征值 $\lambda$ 的近似值 $\lambda^*$, 对 $A-\lambda^*I$ 用反幂法, 因 $\lambda-\lambda^*$ 为 $A-\lambda^*I$ 的按模最小特征值, 收敛很快, 迭代归一化后得分量 $\beta\approx\frac{1}{\lambda-\lambda^*}$, 故 $\lambda\approx\lambda^*+\frac{1}{\beta}$, 且所得 $\alpha^{\left(k\right)}$ 即为相应特征向量.

**雅可比方法** (式 (4.12), 式 (4.13), 定理4.1)

任意 $n$ 阶实对称矩阵 $A$ 可经正交相似变换化为对角矩阵, 即存在正交矩阵 $Q$ 使

$$
Q^{\mathrm T}AQ=\mathrm{diag}\left(\lambda_1,\lambda_2,\dots,\lambda_n\right),
$$

对角元即 $A$ 的全部特征值, $Q$ 各列即为相应特征向量. 取平面旋转变换矩阵 $V_{ij}\left(\varphi\right)$ (式 (4.12), 在 $\left(i,j\right)$ 坐标平面旋转角 $\varphi$), 选

$$
\tan2\varphi=\frac{2a_{ij}}{a_{ii}-a_{jj}}
$$

可使变换后 $a_{ij}^{\left(1\right)}=0$ (式 (4.13)). 反复进行上述旋转, 由**定理 4.1**, 非对角元平方和趋于零, 矩阵趋于对角矩阵, 其对角元即 $A$ 的全部特征值.

## 插值法

**定义 5.1** (插值问题)

已知函数 $f\left(x\right)$ 在区间 $\left[a,b\right]$ 上 $n+1$ 个互异节点 $x_0,x_1,\dots,x_n$ 处的函数值 $y_i=f\left(x_i\right)$, 求一个至多 $n$ 次的多项式 $P_n\left(x\right)$, 使其在给定点处满足插值条件 $P_n\left(x_i\right)=f\left(x_i\right)=y_i\ \left(i=0,1,\dots,n\right)$, $P_n\left(x\right)$ 即称为插值多项式.

**定理 5.1** (插值余项)

设 $x_0,x_1,\dots,x_n$ 是 $\left[a,b\right]$ 上的互异节点, $P_n\left(x\right)$ 是过这组节点的 $n$ 次插值多项式. 如果 $f\left(x\right)$ 在 $\left[a,b\right]$ 上 $n+1$ 次连续可导, 则对 $\left[a,b\right]$ 内任意点 $x$, 插值余项为

$$
R_n\left(x\right)=f\left(x\right)-P_n\left(x\right)=\frac{f^{\left(n+1\right)}\left(\xi\right)}{\left(n+1\right)!}\omega_{n+1}\left(x\right),\quad \xi\in\left(a,b\right),
$$

其中 $\omega_{n+1}\left(x\right)=\prod_{j=0}^{n}\left(x-x_j\right)$.

**定义 5.3** (拉格朗日插值多项式)

称满足 $l_i\left(x_j\right)=\delta_{ij}$ ($i=j$ 时为 $1$, 否则为 $0$) 的 $n$ 次多项式

$$
l_i\left(x\right)=\prod_{\substack{j=0\\j\ne i}}^{n}\frac{x-x_j}{x_i-x_j}\quad\left(i=0,1,\dots,n\right)
$$

为拉格朗日插值基函数, 而 $L_n\left(x\right)=\sum_{i=0}^{n}y_i l_i\left(x\right)$ 称为 $n$ 次拉格朗日插值多项式.

**定义 5.4** (差商与牛顿插值多项式)

称 $f\left[x_i,x_j\right]=\frac{f\left(x_i\right)-f\left(x_j\right)}{x_i-x_j}$ 为 $f\left(x\right)$ 关于点 $x_i,x_j$ 的一阶差商, 并递推地称

$$
f\left[x_0,x_1,\dots,x_k\right]=\frac{f\left[x_1,\dots,x_k\right]-f\left[x_0,\dots,x_{k-1}\right]}{x_k-x_0}
$$

为 $k$ 阶差商. 由此得牛顿插值多项式

$$
N_n\left(x\right)=f\left[x_0\right]+\left(x-x_0\right)f\left[x_0,x_1\right]+\left(x-x_0\right)\left(x-x_1\right)f\left[x_0,x_1,x_2\right]+\cdots+\left(x-x_0\right)\cdots\left(x-x_{n-1}\right)f\left[x_0,\dots,x_n\right].
$$

**定义 5.6, 定义 5.7** (向前差分与向后差分)

对等距节点 $x_k=x_0+kh$ ($h$ 为步长), 称 $\Delta f_k=f_{k+1}-f_k$ 为一阶向前差分, 称 $\nabla f_k=f_k-f_{k-1}$ 为一阶向后差分, 高阶差分递推定义. 令 $x=x_0+th$ 得牛顿向前插值公式

$$
N_n\left(x_0+th\right)=f_0+t\Delta f_0+\frac{t\left(t-1\right)}{2!}\Delta^2f_0+\cdots+\frac{t\left(t-1\right)\cdots\left(t-n+1\right)}{n!}\Delta^nf_0;
$$

令 $x=x_n+th$ 得牛顿向后插值公式

$$
N_n\left(x_n+th\right)=f_n+t\nabla f_n+\frac{t\left(t+1\right)}{2!}\nabla^2f_n+\cdots+\frac{t\left(t+1\right)\cdots\left(t+n-1\right)}{n!}\nabla^nf_n.
$$

**定理 5.2** (分段线性插值余项)

如果 $f\left(x\right)$ 在 $\left[a,b\right]$ 上二阶连续可微, 则分段线性插值函数 $p\left(x\right)$ 的余项有估计

$$
\left|R\left(x\right)\right|=\left|f\left(x\right)-p\left(x\right)\right|\le\frac{h^2}{8}M,
$$

其中 $h=\max\limits_{i}\left(x_{i+1}-x_i\right)$, $M=\max\limits_{\left[a,b\right]}\left|f''\left(x\right)\right|$.

**定义 5.9** (埃尔米特插值)

给定函数 $f\left(x\right)$ 在互异节点上的函数值 $y_i=f\left(x_i\right)$, 并指定在若干节点 $x_{i_k}$ 上的导数值 $y'_{i_k}=f'\left(x_{i_k}\right)$, 要求一个多项式 $H\left(x\right)$ 同时满足 $H\left(x_i\right)=y_i$ 与 $H'\left(x_{i_k}\right)=y'_{i_k}$, 称为埃尔米特插值多项式.

**定理 5.5** (埃尔米特插值余项)

设共有 $n+1$ 个函数值节点与 $m+1$ 个导数条件 (在节点 $x_{i_0},\dots,x_{i_m}$ 上), 若 $f\left(x\right)\in C^{n+m+2}\left[a,b\right]$, 则对任意 $x\in\left[a,b\right]$, 有

$$
R\left(x\right)=f\left(x\right)-H\left(x\right)=\frac{f^{\left(n+m+2\right)}\left(\xi\right)}{\left(n+m+2\right)!}\omega_{n+1}\left(x\right)\prod_{k=0}^{m}\left(x-x_{i_k}\right),\quad \xi\in\left(a,b\right).
$$

**定义 5.11** (三次样条插值)

已知 $f\left(x\right)$ 在节点 $a=x_0< x_1< \cdots< x_n=b$ 上的值 $y_i=f\left(x_i\right)$, 若 $S\left(x\right)$ 满足 $S\left(x_i\right)=y_i$, 在每个小区间 $\left[x_i,x_{i+1}\right]$ 上是三次多项式, 在 $\left[a,b\right]$ 上二阶连续可微, 则称 $S\left(x\right)$ 为三次样条插值函数. 以 $M_i=S''\left(x_i\right)$ 为参数得三弯矩方程

$$
\alpha_j M_{j-1}+2M_j+\beta_j M_{j+1}=C_j\quad\left(j=1,\dots,n-1\right),
$$

其中 $\alpha_j=\frac{h_{j-1}}{h_{j-1}+h_j}$, $\beta_j=1-\alpha_j$, $C_j=\frac{1}{h_{j-1}+h_j}\left(\frac{y_{j+1}-y_j}{h_j}-\frac{y_j-y_{j-1}}{h_{j-1}}\right)$; 端点边界条件可取给定导数值 $S'\left(a\right)=m_0,\ S'\left(b\right)=m_n$ 或给定二阶导数值 $S''\left(a\right)=M_0,\ S''\left(b\right)=M_n$.

## 函数逼近

**线性最小二乘法的一般形式** (式 (6.7) – (6.9))

对数据组 $\left(x_i,y_i\right)\left(i=1,2,\dots,n\right)$, 取 $\left[a,b\right]$ 上一组线性无关的函数

$$
\varphi_k\left(x\right)\left(k=0,1,\dots,m\right),
$$

求 $p\left(x\right)=\sum_{k=0}^m a_k\varphi_k\left(x\right)$ 使残差加权平方和 $\sum_{i=1}^n w_i\left[y_i-p\left(x_i\right)\right]^2$ 最小. 系数满足正则方程组

$$
\sum_{k=0}^m a_k\left(\varphi_k,\varphi_j\right)=\left(y,\varphi_j\right)\quad\left(j=0,1,\dots,m\right),\quad\left(\varphi_k,\varphi_j\right)=\sum_{i=1}^n w_i\varphi_k\left(x_i\right)\varphi_j\left(x_i\right),\quad\left(y,\varphi_j\right)=\sum_{i=1}^n w_i y_i\varphi_j\left(x_i\right).
$$

特别地, 取 $\varphi_k\left(x\right)=x^k$ 即多项式拟合; 一次拟合 $y=a_0+a_1x$ ($w_i=1$) 的正则方程组为

$$
\begin{cases}n a_0+a_1\sum\limits_{i=1}^n x_i=\sum\limits_{i=1}^n y_i,\\a_0\sum\limits_{i=1}^n x_i+a_1\sum\limits_{i=1}^n x_i^2=\sum\limits_{i=1}^n x_i y_i.\end{cases}
$$

**非线性拟合的线性化** (6.1.2 指数拟合, 6.1.3 分式线性拟合)

对指数型 $y=ae^{bx}$, 两端取对数得 $\ln y=\ln a+bx$, 先对变换后的数据组 $\left(x_i,\ln y_i\right)$ 按**线性最小二乘法的一般形式**作一次线性拟合, 再取指数还原; 对可分离变量的分式型 $y=\frac{x}{ax+b}$, 两端取倒数得 $\frac{1}{y}=a+b\frac{1}{x}$, 先对数据组 $\left(\frac{1}{x_i},\frac{1}{y_i}\right)$ 作一次线性拟合, 再取倒数还原.

**定义 6.2** (正交函数系)

若函数系 $\left\{\varphi_k\left(x\right)\right\}$ 在区间 $\left[a,b\right]$ 上满足

$$
\left(\varphi_j,\varphi_k\right)=\int_a^b w\left(x\right)\varphi_j\left(x\right)\varphi_k\left(x\right)\,\mathrm dx=0\ \left(j\ne k\right)
$$

且 $\left(\varphi_k,\varphi_k\right)> 0$, 则称其为 $\left[a,b\right]$ 上关于权函数 $w\left(x\right)$ 的正交函数系, 其中 $\left(\varphi,\psi\right)=\int_a^b w\left(x\right)\varphi\left(x\right)\psi\left(x\right)\,\mathrm dx$ 称为函数的内积.

**定义 6.3** (最佳平方逼近函数)

设 $f\left(x\right)$ 在 $\left[a,b\right]$ 上连续,

$$
H=\operatorname{Span}\left\{\varphi_0,\varphi_1,\dots,\varphi_m\right\},
$$

若 $p\left(x\right)=\sum_{k=0}^m a_k\varphi_k\left(x\right)$ 使

$$
\int_a^b w\left(x\right)\left[f\left(x\right)-p\left(x\right)\right]^2\,\mathrm dx
$$

为最小, 则称 $p\left(x\right)$ 为 $f\left(x\right)$ 在 $H$ 中关于权函数 $w\left(x\right)$ 的最佳平方逼近函数.

**最佳平方逼近的正则方程组** (式 (6.32), (6.35), (6.36))

按**定义 6.3**, 系数 $a_k$ 满足正则方程组

$$
\sum_{k=0}^m a_k\left(\varphi_k,\varphi_j\right)=\left(f,\varphi_j\right)\ \left(j=0,1,\dots,m\right),
$$

其中 $\left(f,\varphi_j\right)=\int_a^b w\left(x\right)f\left(x\right)\varphi_j\left(x\right)\,\mathrm dx$. 若 $\left\{\varphi_k\right\}$ 为正交函数系, 则方程组对角化, 解为 $a_k=\frac{\left(f,\varphi_k\right)}{\left(\varphi_k,\varphi_k\right)}$, 最佳平方逼近函数为 $p\left(x\right)=\sum_{k=0}^m\frac{\left(f,\varphi_k\right)}{\left(\varphi_k,\varphi_k\right)}\varphi_k\left(x\right)$.

**勒让德多项式** (式 (6.18), (6.19))

前几项为 $P_0\left(x\right)=1$, $P_1\left(x\right)=x$, $P_2\left(x\right)=\frac{3x^2-1}{2}$, $P_3\left(x\right)=\frac{5x^3-3x}{2}$. 它是 $\left[-1,1\right]$ 上关于权 $w\left(x\right)\equiv1$ 的正交多项式系, 且 $\left(P_n,P_m\right)=0\ \left(n\ne m\right)$, $\left(P_n,P_n\right)=\frac{2}{2n+1}$. 在区间 $\left[a,b\right]$ 上使用时作变量替换 $t=\frac{2x-\left(b+a\right)}{b-a}$, 取 $\varphi_k\left(x\right)=P_k\left(t\right)$.

## 数值微分与数值积分

**定义 7.1** (代数精确度)

若当 $f\left(x\right)$ 为任意次数不高于 $m$ 的多项式时, 求积公式

$$
\int_a^b f\left(x\right)dx\approx\sum_{k=0}^n A_k f\left(x_k\right)
$$

均精确成立, 而对某个 $m+1$ 次多项式公式不精确成立, 则称该求积公式具有 $m$ 次代数精确度.

**定理 7.2** (梯形公式的误差)

若 $f\left(x\right)\in C^{\left(2\right)}\left[a,b\right]$, 则梯形公式的截断误差为

$$
R_1\left(f\right)=\int_a^b f\left(x\right)dx-\frac{b-a}{2}\left[f\left(a\right)+f\left(b\right)\right]=-\frac{\left(b-a\right)^3}{12}f''\left(\xi\right),\ \xi\in\left(a,b\right).
$$

**定理 7.3** (辛普森公式的误差)

若 $f\left(x\right)\in C^{\left(4\right)}\left[a,b\right]$, 则辛普森公式的截断误差为

$$
R_2\left(f\right)=\int_a^b f\left(x\right)dx-\frac{b-a}{6}\left[f\left(a\right)+4f\left(\frac{a+b}{2}\right)+f\left(b\right)\right]=-\frac{\left(b-a\right)^5}{2880}f^{\left(4\right)}\left(\xi\right)=-\frac{h^5}{90}f^{\left(4\right)}\left(\xi\right),\ \xi\in\left(a,b\right),
$$

其中 $h=b-a$.

**复化梯形公式** (式 (7.29), 式 (7.30))

将 $\left[a,b\right]$ 分成 $n$ 等份, $h=\frac{b-a}{n}$, 分点 $x_k=a+kh$, 则

$$
T_n=\frac{h}{2}\left[f\left(a\right)+f\left(b\right)+2\sum_{k=1}^{n-1}f\left(x_k\right)\right],
$$

截断误差为

$$
R_T\left(f\right)=\int_a^b f\left(x\right)dx-T_n=-\frac{b-a}{12}h^2 f''\left(\xi\right),\ \xi\in\left(a,b\right).
$$

**复化辛普森公式** (式 (7.31), 式 (7.32))

将 $\left[a,b\right]$ 分成 $n=2m$ 等份, 步长 $h=\frac{b-a}{n}$, 则

$$
S_n=\frac{h}{3}\left[f\left(a\right)+f\left(b\right)+2\sum_{k=1}^{m-1}f\left(x_{2k}\right)+4\sum_{k=1}^{m}f\left(x_{2k-1}\right)\right],
$$

截断误差为

$$
R_S\left(f\right)=\int_a^b f\left(x\right)dx-S_n=-\frac{b-a}{180}h^4 f^{\left(4\right)}\left(\xi\right),\ \xi\in\left(a,b\right).
$$

**二点与三点求导公式** (式 (7.9) 至式 (7.12))

对步长 $h$ 的等距节点 $x_0,x_1=x_0+h$, 二点公式 $f'\left(x_0\right)\approx\frac{f\left(x_1\right)-f\left(x_0\right)}{h}$, 截断误差 $R_1\left(x_0\right)=-\frac{h}{2}f''\left(\xi\right)$; 对节点 $x_0,x_1,x_2=x_0+2h$, 三点中心公式

$$
f'\left(x_1\right)\approx\frac{f\left(x_2\right)-f\left(x_0\right)}{2h},
$$

截断误差 $R_2\left(x_1\right)=-\frac{h^2}{6}f^{\left(3\right)}\left(\xi\right)$.

**梯形公式的逐次分半算法** (式 (7.34))

记 $2^m$ 等分区间的梯形值为 $T_{2^m}$, 则逐次分半递推为

$$
T_{2^m}=\frac{1}{2}T_{2^{m-1}}+\frac{b-a}{2^m}\sum_{k=1}^{2^{m-1}}f\left(a+\left(2k-1\right)\frac{b-a}{2^m}\right),
$$

且事后误差估计为

$$
\left|R\left(f,T_{2^m}\right)\right|\approx\frac{1}{3}\left|T_{2^m}-T_{2^{m-1}}\right|,
$$

当 $\left|T_{2^m}-T_{2^{m-1}}\right|< 3\varepsilon$ 时停止计算.

**龙贝格求积公式** (式 (7.41))

由理查森外推法,

$$
T_m^{\left(k\right)}=\frac{4^m T_{m-1}^{\left(k+1\right)}-T_{m-1}^{\left(k\right)}}{4^m-1},\ m=1,2,\dots,
$$

第一列 $T_0^{\left(k\right)}$ 为复化梯形值序列, 以后各列依次为辛普森, 科茨, 龙贝格值, 精度逐列提高.

**定义 7.2** (高斯点与高斯型求积公式)

若 $n$ 个节点 $x_1,\dots,x_n\in\left[a,b\right]$ 使带权求积公式

$$
\int_a^b \rho\left(x\right)f\left(x\right)dx\approx\sum_{k=1}^n A_k f\left(x_k\right)
$$

具有 $2n-1$ 次代数精确度, 则称这组节点为高斯点, 公式称为带权 $\rho\left(x\right)$ 的高斯型求积公式.

**定理 7.4** (高斯点与正交多项式的关系)

求积公式的节点是高斯点的充要条件是函数 $w_n\left(x\right)=\prod_{k=1}^n\left(x-x_k\right)$ 与任意次数不超过 $n-1$ 的多项式 $p\left(x\right)$ 在 $\left[a,b\right]$ 上关于权函数 $\rho\left(x\right)$ 正交, 即

$$
\int_a^b \rho\left(x\right)p\left(x\right)w_n\left(x\right)dx=0.
$$

**高斯-勒让德求积公式** (式 (7.57))

区间 $\left[-1,1\right]$ 上以勒让德多项式零点为节点, 权函数 $\rho\left(x\right)=1$ 的高斯型求积公式. 对任意有限区间 $\left[a,b\right]$, 作变换 $x=\frac{b-a}{2}t+\frac{a+b}{2}$, 则

$$
\int_a^b f\left(x\right)dx=\frac{b-a}{2}\int_{-1}^1 f\left(\frac{b-a}{2}t+\frac{a+b}{2}\right)dt.
$$

**二重积分的复化求积公式** (式 (7.82), 式 (7.83))

矩形区域 $D=\left[a,b\right]\times\left[c,d\right]$ 上的二重积分, $x$ 方向 $n$ 等分, $y$ 方向 $m$ 等分, 步长 $h=\frac{b-a}{n}$, $k=\frac{d-c}{m}$, 其复化求积公式为两个方向一维公式的张量乘积. 梯形权重为 $\omega^{\left(t\right)}=\left[\frac12,1,\dots,1,\frac12\right]$, 辛普森权重为 $\omega^{\left(s\right)}=\left[1,4,2,\dots,2,4,1\right]$.

## 非线性方程解法

**定义 8.1** (迭代法与不动点迭代法)

将方程 $f\left(x\right)=0$ 改写为等价形式 $x=\varphi\left(x\right)$, 取定初值 $x_0$, 由迭代公式

$$
x_{n+1}=\varphi\left(x_n\right)\ \left(n=0,1,2,\dots\right)
$$

产生序列 $\left\{x_n\right\}$; 若 $x_n\to x^{*}$, 则 $x^{*}=\varphi\left(x^{*}\right)$ 称为 $\varphi\left(x\right)$ 的不动点, 上述方法称为迭代法 (不动点迭代法).

**定理 8.2** (不动点迭代法的收敛条件)

设函数 $\varphi\left(x\right)$ 在区间 $\left[a,b\right]$ 上满足条件: (1) 对任意 $x\in\left[a,b\right]$, 有 $\varphi\left(x\right)\in\left[a,b\right]$; (2) 存在常数 $0< L< 1$, 使得对任意 $x\in\left[a,b\right]$, 都有 $\left|\varphi'\left(x\right)\right|\le L$. 则方程 $x=\varphi\left(x\right)$ 在 $\left[a,b\right]$ 上有唯一的根 $x^{*}$, 对任意初值 $x_0\in\left[a,b\right]$, 迭代序列 $x_{n+1}=\varphi\left(x_n\right)$ 收敛于 $x^{*}$, 并有事后误差估计

$$
\left|x^{*}-x_n\right|\le\frac{L}{1-L}\left|x_n-x_{n-1}\right|.
$$

**定义 8.2** (迭代法的收敛阶)

设序列 $\left\{x_n\right\}$ 收敛于 $x^{*}$, 如果存在正数 $r$ 和 $a$, 使得

$$
\lim_{n\to\infty}\frac{\left|x_{n+1}-x^{*}\right|}{\left|x_n-x^{*}\right|^{r}}=a
$$

成立 (当 $r=1$ 时要求 $a< 1$), 则称序列 $\left\{x_n\right\}$ 是 $r$ 阶收敛的; $r=1$ 称线性收敛, $r=2$ 称平方收敛.

**定理 8.4** (迭代法收敛阶与迭代函数导数的关系)

设迭代函数 $\varphi\left(x\right)$ 在 $x^{*}$ 邻近有 $r$ 阶连续导数 $\left(r\ge2\right)$, 且

$$
x^{*}=\varphi\left(x^{*}\right),\quad\varphi'\left(x^{*}\right)=\varphi''\left(x^{*}\right)=\dots=\varphi^{\left(r-1\right)}\left(x^{*}\right)=0,
$$

而 $\varphi^{\left(r\right)}\left(x^{*}\right)\ne0$, 则迭代序列 $\left\{x_n\right\}$ 是 $r$ 阶收敛的; 若 $x^{*}=\varphi\left(x^{*}\right)$ 而 $0< \left|\varphi'\left(x^{*}\right)\right|< 1$, 则 $\left\{x_n\right\}$ 是线性收敛的.

**牛顿迭代法** (切线法, 式 (8.16))

将非线性方程在根邻近线性化, 得迭代公式

$$
x_{n+1}=x_n-\frac{f\left(x_n\right)}{f'\left(x_n\right)}.
$$

**定理 8.5** (牛顿法的局部收敛性) 指出: 当 $f'\left(x^{*}\right)\ne0$ (即 $x^{*}$ 为单根) 时, 牛顿法在 $x^{*}$ 邻近至少二阶收敛; 当 $x^{*}$ 为 $r$ 重根时牛顿法退化为线性收敛, 其改进格式为

$$
x_{n+1}=x_n-r\frac{f\left(x_n\right)}{f'\left(x_n\right)}\quad\left(n=0,1,2,\dots\right)
$$

(式 (8.17)), 至少二阶收敛.

**弦截法** (割线法, 式 (8.19))

用差商代替导数, 得两步迭代公式

$$
x_{n+1}=x_n-\frac{f\left(x_n\right)\left(x_n-x_{n-1}\right)}{f\left(x_n\right)-f\left(x_{n-1}\right)}\quad\left(n=1,2,\dots\right).
$$
