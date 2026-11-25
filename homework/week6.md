# week6

> **定义 5.2 (截断误差, 即插值余项)**
> 
> 插值多项式 $P\left(x\right)$ 与被插函数 $f\left(x\right)$ 之间的差 $R_n\left(x\right)=f\left(x\right)-P\left(x\right)$ 称为截断误差, 又称插值余项. (教材 $\S5.2$, p132)

> **定理 5.1 (插值多项式的存在唯一性)**
> 
> 设 $x_0,x_1,\ldots,x_n$ 是区间 $\left[a,b\right]$ 上的互异节点, 则满足插值条件 $P_n\left(x_i\right)=y_i$ ($i=0,1,\ldots,n$) 的次数不超过 $n$ 的多项式 $P_n\left(x\right)$ 存在且唯一. (教材 $\S5.2$, p132)

> **定义 5.4 (差商)**
> 
> 设 $f\left(x\right)$ 在互异点 $x_0,x_1,\ldots$ 上有值, 称 $\dfrac{f\left(x_i\right)-f\left(x_j\right)}{x_i-x_j}$ ($i\ne{}j$) 为 $f$ 关于 $x_i,x_j$ 的一阶差商; 一般地 $k$ 阶差商由 $k-1$ 阶差商递归定义 $f\left[x_0,x_1,\ldots,x_k\right]=\dfrac{f\left[x_1,\ldots,x_k\right]-f\left[x_0,\ldots,x_{k-1}\right]}{x_k-x_0}$. (教材 $\S5.3$, p138)

> **定义 5.7 (差分)**
> 
> 设等距节点 $x_k=x_0+kh$ ($k=0,1,\ldots,n$), 步长 $h$, $f_k=f\left(x_k\right)$, 称 $f\left(x_k\right)$ 与其前面点 $f\left(x_{k-1}\right)$ 的差为 $f$ 在 $x_k$ 处以 $h$ 为步长的向后差分. (教材 $\S5.3$, p143)

> **定理 5.2 (分段线性插值的余项)**
> 
> 如果 $f\left(x\right)$ 在 $\left[a,b\right]$ 上二阶连续可微, 则分段线性插值函数 $\varphi\left(x\right)$ 的余项有估计 $\left|f\left(x\right)-\varphi\left(x\right)\right|\le\dfrac{h^{2}}{8}\max_{a\le{}x\le{}b}\left|f''\left(x\right)\right|$, 其中 $h$ 为步长. (教材 $\S5.4$, p150)

> **定义 5.9 (Hermite 插值)**
> 
> 设已知 $y=f\left(x\right)$ 在 $n+1$ 个互异节点上的函数值, 并在某些节点上还给出导数值, 要求一个次数不高于给定条件个数的多项式, 使它在这些节点上与 $f$ 的函数值 与 导数值都相同, 这类插值称为 Hermite 插值. (教材 $\S5.4$, p151)

## 习题 5-7 (插值基函数的两条恒等式)

设 $x_0,x_1,\ldots,x_n$ 为 $n+1$ 个互异节点, $l_j\left(x\right)$ ($j=0,1,\ldots,n$) 为这组节点上的 $n$ 次 Lagrange 插值基函数, 试证:

(1) $\sum_{j=0}^{n}\left(x_j-x\right)^{k}l_j\left(x\right)\equiv0$ ($k=1,2,\ldots,n$);

(2) 设 $P\left(x\right)$ 是任意一个最高次项系数为 $1$ 的 $n+1$ 次多项式, 则

$$
P\left(x\right)-\sum_{j=0}^{n}P\left(x_j\right)l_j\left(x\right)=\omega_{n+1}\left(x\right)=\prod_{j=0}^{n}\left(x-x_j\right).
$$

### 解答 5-7

(1) 固定 $x$, 把 $g\left(t\right)=\left(t-x\right)^{k}$ 看作 $t$ 的多项式. 因 $k\le{}n$, $g$ 的次数不超过 $n$. 而 $\sum_{j=0}^{n}g\left(x_j\right)l_j\left(x\right)$ 是一个关于 $x$ 的次数不超过 $n$ 与 在节点 $x_0,\ldots,x_n$ 上取值为 $g\left(x_j\right)$ 的多项式, 即 $g$ 在这组节点上的 $n$ 次插值多项式. 由**定理 5.1 (插值多项式的存在唯一性)**, 它只能是 $g$ 本身, 即

$$
\sum_{j=0}^{n}\left(x_j-x\right)^{k}l_j\left(x\right)=g\left(x\right)=\left(x-x\right)^{k}=0,\quad{}k=1,2,\ldots,n.
$$

若 $k=0$, 同样的论证给出 $\sum_jl_j\left(x\right)\equiv1$, 这正是基函数的单位分解性质, 也解释了 $k\ge1$ 时必须为零.

$\blacksquare$

(2) 记

$$
Q\left(x\right)=P\left(x\right)-\sum_{j=0}^{n}P\left(x_j\right)l_j\left(x\right).
$$

右端第二项的次数不超过 $n$, 故 $Q$ 的次数不超过 $n+1$, 且 $Q$ 的最高次项系数就是 $P$ 的最高次项系数 $1$ ($Q$ 是首一多项式). 又在每个节点处

$$
Q\left(x_i\right)=P\left(x_i\right)-\sum_{j=0}^{n}P\left(x_j\right)l_j\left(x_i\right)=P\left(x_i\right)-P\left(x_i\right)=0,\quad{}i=0,1,\ldots,n,
$$

这里用到 $l_j\left(x_i\right)=\delta_{ij}$. 于是 $Q$ 是次数不超过 $n+1$ 与 以 $x_0,\ldots,x_n$ 为根的首一多项式, 而这类多项式只有 $\prod_j\left(x-x_j\right)$ (次数 $n+1$ 且首一, 根已给定唯一确定), 故

$$
P\left(x\right)-\sum_{j=0}^{n}P\left(x_j\right)l_j\left(x\right)=\omega_{n+1}\left(x\right).
$$

$\blacksquare$

## 习题 5-8 (三阶 Newton 插值多项式)

已知函数表

| $x_i$ | $1.615$ | $1.634$ | $1.702$ | $1.828$ |
|---|---|---|---|---|
| $f\left(x_i\right)$ | $2.41450$ | $2.46259$ | $2.65271$ | $3.03035$ |

试求其三阶 Newton 插值多项式, 并以此计算 $f\left(1.682\right)$ 的近似值.

### 解答 5-8

按**定义 5.4 (差商)** 造差商表 (保留 $8$ 位小数):

| $x_i$ | $f\left(x_i\right)$ | 一阶 | 二阶 | 三阶 |
|---|---|---|---|---|
| $1.615$ | $2.41450$ | | | |
| $1.634$ | $2.46259$ | $2.53105263$ | | |
| $1.702$ | $2.65271$ | $2.79588235$ | $3.04401979$ | |
| $1.828$ | $3.03035$ | $2.99714286$ | $1.03742528$ | $-9.42063149$ |

逐个核对第一列:

$$
f\left[x_0,x_1\right]=\frac{2.46259-2.41450}{1.634-1.615}=\frac{0.04809}{0.019}=2.53105263,
$$

$$
f\left[x_1,x_2\right]=\frac{2.65271-2.46259}{1.702-1.634}=\frac{0.19012}{0.068}=2.79588235,\quad{}f\left[x_2,x_3\right]=\frac{0.37764}{0.126}=2.99714286;
$$

$$
f\left[x_0,x_1,x_2\right]=\frac{2.79588235-2.53105263}{1.702-1.615}=\frac{0.26482972}{0.087}=3.04401979,
$$

$$
f\left[x_1,x_2,x_3\right]=\frac{2.99714286-2.79588235}{1.828-1.634}=\frac{0.20126051}{0.194}=1.03742528,
$$

$$
f\left[x_0,x_1,x_2,x_3\right]=\frac{1.03742528-3.04401979}{1.828-1.615}=\frac{-2.00659451}{0.213}=-9.42063149.
$$

三阶 Newton 插值多项式取差商表对角线上第一行:

$$
N_3\left(x\right)=2.41450+2.53105263\left(x-1.615\right)+3.04401979\left(x-1.615\right)\left(x-1.634\right)-9.42063149\left(x-1.615\right)\left(x-1.634\right)\left(x-1.702\right).
$$

代入 $x=1.682$: 记 $t_1=1.682-1.615=0.067$, $t_2=1.682-1.634=0.048$, $t_3=1.682-1.702=-0.020$, 则

$$
N_3\left(1.682\right)=2.41450+2.53105263\times0.067+3.04401979\times0.067\times0.048-9.42063149\times0.067\times0.048\times\left(-0.020\right)
$$

$$
=2.41450+0.169580+0.009790+0.000606=2.594476.
$$

故 $f\left(1.682\right)\approx2.5945$. 校验: $N_3$ 在四个节点处应当精确取到表中值, 例如 $N_3\left(1.615\right)=2.41450$ (后三项为零), $N_3\left(1.634\right)=2.41450+2.53105263\times0.019=2.46259$ (高次项含因子 $x-1.634$ 而为零), 与表相符.

$\blacksquare$

## 习题 5-10 (Newton 向前 与 向后插值公式)

已知函数表

| $x_i$ | $1$ | $2$ | $3$ | $4$ |
|---|---|---|---|---|
| $f\left(x_i\right)$ | $3$ | $5$ | $9$ | $15$ |

分别用 Newton 向前 与 向后插值公式计算 $f\left(1.5\right)$, $f\left(3.7\right)$ 的近似值.

### 解答 5-10

节点等距, $h=1$. 先造差分表, 按**定义 5.7 (差分)** 记 $\Delta$ 为向前差分 与 $\nabla$ 为向后差分:

| $x_i$ | $f_i$ | $\Delta$ | $\Delta^{2}$ | $\Delta^{3}$ |
|---|---|---|---|---|
| $1$ | $3$ | $2$ | $2$ | $0$ |
| $2$ | $5$ | $4$ | $2$ | |
| $3$ | $9$ | $6$ | | |
| $4$ | $15$ | | | |

(1) Newton 向前插值公式 (以 $x_0=1$ 为基点, $t=x-1$):

$$
N\left(x\right)=f_0+t\Delta{}f_0+\frac{t\left(t-1\right)}{2!}\Delta^{2}f_0+\frac{t\left(t-1\right)\left(t-2\right)}{3!}\Delta^{3}f_0
=3+2t+\frac{t\left(t-1\right)}{2}\times2+0.
$$

代入 $x=1.5$, $t=0.5$:

$$
f\left(1.5\right)\approx3+2\times0.5+0.5\times\left(-0.5\right)=3+1-0.25=3.75.
$$

(2) Newton 向后插值公式 (以 $x_3=4$ 为基点, $t=x-4$, 用 $\nabla$ 差分):

$$
N\left(x\right)=f_3+t\nabla{}f_3+\frac{t\left(t+1\right)}{2!}\nabla^{2}f_3+\frac{t\left(t+1\right)\left(t+2\right)}{3!}\nabla^{3}f_3
=15+6t+\frac{t\left(t+1\right)}{2}\times2+0,
$$

其中 $\nabla{}f_3=f_3-f_2=6$, $\nabla^{2}f_3=\nabla{}f_3-\nabla{}f_2=6-4=2$. 代入 $x=3.7$, $t=-0.3$:

$$
f\left(3.7\right)\approx15+6\times\left(-0.3\right)+\left(-0.3\right)\times0.7=15-1.8-0.21=12.99.
$$

(3) 校验. 表中数据满足 $f\left(x\right)=x^{2}-x+3$ ($1-1+3=3$, $4-2+3=5$, $9-3+3=9$, $16-4+3=15$), 而三阶差分已为零, 说明插值多项式恰为该二次式, 因此两个公式给出的值都是精确值: $1.5^{2}-1.5+3=3.75$, $3.7^{2}-3.7+3=12.99$. 两个公式的差别只在所用基点和差分方向, 对同一张表给出的多项式相同.

$\blacksquare$

## 习题 5-12 (插值步长的选取)

在 $\left[0,\pi/2\right]$ 上给出 $f\left(x\right)=\sin{}x$ 的等距节点函数表, 为保证用分段线性插值求非节点处的正弦值时截断误差不超过 $10^{-6}$, 函数表的步长至多应取多大? 若改用分段二次插值, 步长至多应取多大?

### 解答 5-12

(1) 分段线性插值. 由**定理 5.2 (分段线性插值的余项)**, 在每个小区间 $\left[x_i,x_{i+1}\right]$ 上

$$
\left|f\left(x\right)-\varphi\left(x\right)\right|\le\frac{h^{2}}{8}\max_{x_i\le{}x\le{}x_{i+1}}\left|f''\left(x\right)\right|.
$$

$f\left(x\right)=\sin{}x$ 满足 $\left|f''\left(x\right)\right|=\left|\sin{}x\right|\le1$, 故

$$
\frac{h^{2}}{8}\times1\le10^{-6}\quad\Longrightarrow\quad{}h\le\sqrt{8\times10^{-6}}=2\sqrt{2}\times10^{-3}\approx2.828\times10^{-3}.
$$

即步长不得超过 $0.0028$ (取 $\pi/2$ 均分时, 分段数 $n$ 需满足 $\left(\pi/2\right)/n\le0.00283$, 即 $n\ge556$).

$\blacksquare$

(2) 分段二次插值. 在每个长度为 $h$ 的小区间上取三个等距节点作二次插值, 由**定义 5.2 (截断误差, 即插值余项)**, 余项为

$$
\frac{f'''\left(\xi\right)}{3!}\left(x-x_i\right)\left(x-x_{i+\frac{1}{2}}\right)\left(x-x_{i+1}\right).
$$

令 $u=\left(x-x_i\right)/h\in\left[0,1\right]$, 三次因子化为 $h^{3}u\left(u-\dfrac{1}{2}\right)\left(u-1\right)$. 记 $\varphi\left(u\right)=u\left(u-\dfrac{1}{2}\right)\left(u-1\right)=u^{3}-\dfrac{3}{2}u^{2}+\dfrac{1}{2}u$, 则 $\varphi'\left(u\right)=3u^{2}-3u+\dfrac{1}{2}$, 令其为零得 $u=\dfrac{1}{2}\pm\dfrac{\sqrt{3}}{6}$, 此时

$$
\left|\varphi\left(u\right)\right|=\left|\left(\frac{1}{2}\pm\frac{\sqrt{3}}{6}\right)\left(\pm\frac{\sqrt{3}}{6}\right)\left(-\frac{1}{2}\pm\frac{\sqrt{3}}{6}\right)\right|=\frac{\sqrt{3}}{36}\approx0.04811,
$$

(计算: $\dfrac{\sqrt{3}}{6}\left(\dfrac{3}{36}-\dfrac{1}{4}\right)=-\dfrac{\sqrt{3}}{36}$, 故绝对值恰为 $\dfrac{\sqrt{3}}{36}$). 又 $\left|f'''\left(x\right)\right|\le1$, 于是

$$
\left|f\left(x\right)-\varphi_2\left(x\right)\right|\le\frac{1}{6}h^{3}\cdot\frac{\sqrt{3}}{36}=\frac{\sqrt{3}}{216}h^{3}\le10^{-6}
$$

$$
\Longrightarrow\quad{}h\le\left(\frac{216}{\sqrt{3}}\times10^{-6}\right)^{1/3}=\left(1.24708\times10^{-4}\right)^{1/3}\approx0.04996.
$$

即步长不得超过 $0.0500$ (校验: $h=0.05$ 时误差界为 $\sqrt{3}\times0.05^{3}/216=1.00\times10^{-6}$, 恰在临界; 取 $\pi/2$ 均分时 $n\ge32$).

$\blacksquare$

(3) 比较. 同为 $10^{-6}$ 的要求, 分段线性允许的步长是 $2.8\times10^{-3}$, 分段二次是 $5.0\times10^{-2}$, 相差约 $18$ 倍. 粗略地说, 误差阶由 $O\left(h^{2}\right)$ 升到 $O\left(h^{3}\right)$ 会让步长放宽约 $10^{-6}$ 的六次根 (即 $10$ 倍), 余下的倍数来自两个估计式中常数的差别 ($1/8$ 与 $\sqrt{3}/216\approx0.00801$); 实际含义是同一精度下节点数可减少到约 $1/18$.

$\blacksquare$

## 习题 5-16 (四次 Hermite 插值与余项)

给定函数表

| $x_i$ | $0$ | $1$ | $2$ |
|---|---|---|---|
| $f\left(x_i\right)$ | $1$ | $2$ | $1$ |
| $f'\left(x_i\right)$ | $0$ | | $-1$ |

且已知 $f\left(x\right)$ 在 $\left[0,2\right]$ 上五阶连续可导, 求 $f\left(x\right)$ 的四次 Hermite 插值多项式 $H_4\left(x\right)$, 并写出余项 $f\left(x\right)-H_4\left(x\right)$ 的表示式.

### 解答 5-16

按**定义 5.9 (Hermite 插值)**, 共有 $5$ 个条件 (三个函数值加两个导数值), 故取次数不超过 $4$ 的插值多项式. 用重节点差商: 节点序列取 $z=\left(0,0,1,2,2\right)$, 在重节点处一阶差商改用导数值.

| $z$ | $f\left(z\right)$ | 一阶 | 二阶 | 三阶 | 四阶 |
|---|---|---|---|---|---|
| $0$ | $1$ | | | | |
| $0$ | $1$ | $f'\left(0\right)=0$ | | | |
| $1$ | $2$ | $1$ | $1$ | | |
| $2$ | $1$ | $-1$ | $-1$ | $-1$ | |
| $2$ | $1$ | $f'\left(2\right)=-1$ | $0$ | $0.5$ | $0.75$ |

逐格核对: $f\left[0,1\right]=\left(2-1\right)/1=1$; $f\left[1,2\right]=\left(1-2\right)/1=-1$; $f\left[2,2\right]=f'\left(2\right)=-1$; 

$$
f\left[0,0,1\right]=\frac{1-0}{1-0}=1,\quad{}f\left[0,1,2\right]=\frac{-1-1}{2-0}=-1,\quad{}f\left[1,2,2\right]=\frac{-1-\left(-1\right)}{2-1}=0;
$$

$$
f\left[0,0,1,2\right]=\frac{-1-1}{2-0}=-1,\quad{}f\left[0,1,2,2\right]=\frac{0-\left(-1\right)}{2-0}=0.5;
$$

$$
f\left[0,0,1,2,2\right]=\frac{0.5-\left(-1\right)}{2-0}=0.75.
$$

取对角线上元素构造:

$$
H_4\left(x\right)=1+0\cdot{}x+1\cdot{}x\left(x-0\right)+\left(-1\right)x\left(x-0\right)\left(x-1\right)+0.75\,x\left(x-0\right)\left(x-1\right)\left(x-2\right)
$$

$$
=1+x^{2}-x^{2}\left(x-1\right)+0.75x^{2}\left(x-1\right)\left(x-2\right)=\frac{3}{4}x^{4}-\frac{13}{4}x^{3}+\frac{7}{2}x^{2}+1.
$$

校验五个条件:

$$
H_4\left(0\right)=1,\quad{}H_4\left(1\right)=0.75-3.25+3.5+1=2,\quad{}H_4\left(2\right)=12-26+14+1=1,
$$

$$
H_4'\left(x\right)=3x^{3}-9.75x^{2}+7x,\quad{}H_4'\left(0\right)=0,\quad{}H_4'\left(2\right)=24-39+14=-1,
$$

与表中数据及 $f'\left(0\right)=0$ 与 $f'\left(2\right)=-1$ 完全一致.

余项. 由**定义 5.2 (截断误差, 即插值余项)**, 插值余项由 $H_4$ 与被插函数之差给出. 因插值条件共 $5$ 个 (相当于 $5$ 个重节点), 余项形式为

$$
f\left(x\right)-H_4\left(x\right)=\frac{f^{\left(5\right)}\left(\xi\right)}{5!}\,x^{2}\left(x-1\right)\left(x-2\right)^{2},\quad\xi\in\left(0,2\right)\;\text{依赖于}\;x,
$$

其中 $x^{2}\left(x-1\right)\left(x-2\right)^{2}$ 是重节点的节点多项式 (节点 $0$ 与 $2$ 各二重, 节点 $1$ 一重). 特别地在节点处该式为零, 与插值条件相符.

$\blacksquare$
