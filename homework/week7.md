# week7

> **定义 5.10 (m 次样条函数)**
> 
> 设区间 $\left[a,b\right]$ 有分划 $\Delta:a=x_0<{}x_1<\cdots<{}x_n=b$. 若函数 $S\left(x\right)$ 在每个小区间 $\left[x_i,x_{i+1}\right]$ ($i=0,1,\ldots,n-1$) 上是 $m$ 次多项式, 且在整个 $\left[a,b\right]$ 上具有 $m-1$ 阶连续导数, 则称 $S\left(x\right)$ 为关于分划 $\Delta$ 的 $m$ 次样条函数. (教材 $\S5.5$, p148)

> **定义 5.11 (三次样条插值)**
> 
> 已知 $y=f\left(x\right)$ 在 $a=x_0<{}x_1<\cdots<{}x_n=b$ 上的值 $y_i=f\left(x_i\right)$, 若插值函数 $S\left(x\right)$ 满足: (1) $S\left(x_i\right)=y_i$; (2) 在每个 $\left[x_j,x_{j+1}\right]$ 上 $S\left(x\right)$ 是三次多项式, 记为 $S_j\left(x\right)$; (3) $S\left(x\right)$ 在 $\left[a,b\right]$ 上二阶连续可微, 则称 $S\left(x\right)$ 为 $f\left(x\right)$ 的三次样条插值函数. (教材 $\S5.5$, p148)

> **公式 (5.37) (三弯矩形式的分段表达式)**
> 
> 记 $M_j=S''\left(x_j\right)$, $h_j=x_{j+1}-x_j$, 则 $S_j\left(x\right)=\dfrac{M_{j+1}\left(x-x_j\right)^{3}}{6h_j}-\dfrac{M_j\left(x-x_{j+1}\right)^{3}}{6h_j}+\left(y_{j+1}-\dfrac{M_{j+1}h_j^{2}}{6}\right)\dfrac{x-x_j}{h_j}-\left(y_j-\dfrac{M_jh_j^{2}}{6}\right)\dfrac{x-x_{j+1}}{h_j}$, $x\in\left[x_j,x_{j+1}\right]$. (教材 $\S5.5$, p149)

> **公式 (5.41) (三弯矩方程)**
> 
> 记 $\alpha_j=\dfrac{h_{j-1}}{h_{j-1}+h_j}$, $\beta_j=1-\alpha_j=\dfrac{h_j}{h_{j-1}+h_j}$, $c_j=\dfrac{6}{h_{j-1}+h_j}\left(\dfrac{y_{j+1}-y_j}{h_j}-\dfrac{y_j-y_{j-1}}{h_{j-1}}\right)$, 则三次样条的参数 $M_j$ 满足 $\alpha_jM_{j-1}+2M_j+\beta_jM_{j+1}=c_j$ ($j=1,2,\ldots,n-1$). (教材 $\S5.5$, p150)

> **公式 (5.44) (三转角形式的分段表达式)**
> 
> 记 $m_j=S'\left(x_j\right)$, 则 $S_j\left(x\right)=\left(1+2\dfrac{x-x_j}{h_j}\right)\left(\dfrac{x-x_{j+1}}{h_j}\right)^{2}y_j+\left(1-2\dfrac{x-x_{j+1}}{h_j}\right)\left(\dfrac{x-x_j}{h_j}\right)^{2}y_{j+1}+\left(x-x_j\right)\left(\dfrac{x-x_{j+1}}{h_j}\right)^{2}m_j+\left(x-x_{j+1}\right)\left(\dfrac{x-x_j}{h_j}\right)^{2}m_{j+1}$, $x\in\left[x_j,x_{j+1}\right]$. (教材 $\S5.5$, p151)

> **公式 (5.45) (三转角方程)**
> 
> 以 $\alpha_j,\beta_j$ 如**公式 (5.41) (三弯矩方程)** 所记, $d_j=3\left[\beta_j\dfrac{y_j-y_{j-1}}{h_{j-1}}+\alpha_j\dfrac{y_{j+1}-y_j}{h_j}\right]$, 则三次样条的参数 $m_j$ 满足 $\beta_jm_{j-1}+2m_j+\alpha_jm_{j+1}=d_j$ ($j=1,2,\ldots,n-1$). (教材 $\S5.5$, p152)

> **定理 6.1 (正则方程组的解即最小二乘函数)**
> 
> 设 $\varphi_0\left(x\right),\ldots,\varphi_m\left(x\right)$ 线性无关, $a_0,a_1,\ldots,a_m$ 为正则方程组 $\sum_{k=0}^{m}\left(\varphi_k,\varphi_j\right)a_k=\left(y,\varphi_j\right)$ ($j=0,1,\ldots,m$) 的解, 其中 $\left(\varphi_k,\varphi_j\right)=\sum_{i=1}^{n}\omega_i\varphi_k\left(x_i\right)\varphi_j\left(x_i\right)$, $\left(y,\varphi_j\right)=\sum_{i=1}^{n}\omega_iy_i\varphi_j\left(x_i\right)$, 则 $\varphi\left(x\right)=\sum_{k=0}^{m}a_k\varphi_k\left(x\right)$ 满足 $\sum_{i=1}^{n}\omega_i\left[y_i-\varphi\left(x_i\right)\right]^{2}=\min_{\psi\in{}H}\sum_{i=1}^{n}\omega_i\left[y_i-\psi\left(x_i\right)\right]^{2}$. (教材 $\S6.1$, p175)

## 习题 5-17 (三次样条: 两种边界条件)

已知函数表

| $x_i$ | $0$ | $1$ | $2$ | $3$ |
|---|---|---|---|---|
| $y_i$ | $0$ | $0$ | $0$ | $0$ |

边界条件为 (1) $m_0=1$, $m_3=0$; (2) $M_0=1$, $M_3=0$, 分别求三次样条插值函数. 这里 $m_j=S'\left(x_j\right)$, $M_j=S''\left(x_j\right)$.

### 解答 5-17

两个边界条件都要用, 但按**定义 5.11 (三次样条插值)**, 参数取导数值或二阶导数值是同一族函数的两种坐标, 故 (1) 用三转角方程, (2) 用三弯矩方程, 各自求解再把参数代回分段表达式.

(1) **三转角方程**

由**公式 (5.45) (三转角方程)**, $h_0=h_1=h_2=1$, 故 $\alpha_j=\beta_j=\dfrac{1}{2}$ ($j=1,2$), 又 $y_0=y_1=y_2=y_3=0$, 故

$$
d_j=3\left[\frac{1}{2}\cdot\frac{0-0}{1}+\frac{1}{2}\cdot\frac{0-0}{1}\right]=0,\quad{}j=1,2.
$$

代入 $m_0=1$, $m_3=0$ 得两个方程

$$
\frac{1}{2}\cdot1+2m_1+\frac{1}{2}m_2=0,\quad\frac{1}{2}m_1+2m_2+\frac{1}{2}\cdot0=0.
$$

由第二式 $m_1=-4m_2$, 代入第一式得 $\dfrac{1}{2}-\dfrac{15}{2}m_2=0$, 即

$$
m_2=\frac{1}{15},\quad{}m_1=-\frac{4}{15}.
$$

$\blacksquare$

(2) **三弯矩方程**

由**公式 (5.41) (三弯矩方程)**, $h_j=1$ 且 $y_j$ 全为零, 故 $c_j=0$ ($j=1,2$). 代入 $M_0=1$, $M_3=0$ 得

$$
\frac{1}{2}\cdot1+2M_1+\frac{1}{2}M_2=0,\quad\frac{1}{2}M_1+2M_2+\frac{1}{2}\cdot0=0.
$$

与 (1) 的方程组逐项相同, 故

$$
M_2=\frac{1}{15},\quad{}M_1=-\frac{4}{15}.
$$

$\blacksquare$

(3) **分段表达式**

(1) 的资料为 $m=\left(1,-\dfrac{4}{15},\dfrac{1}{15},0\right)$, 由**公式 (5.44) (三转角形式的分段表达式)**, 因 $y_j$ 全为零, 只余两个导数项 (取 $h_j=1$):

$$
S_j\left(x\right)=\left(x-x_j\right)\left(x-x_{j+1}\right)^{2}m_j+\left(x-x_{j+1}\right)\left(x-x_j\right)^{2}m_{j+1}.
$$

逐段代入并整理:

$$
S_0\left(x\right)=x\left(x-1\right)^{2}-\frac{4}{15}x^{2}\left(x-1\right)=\frac{1}{15}x\left(x-1\right)\left(11x-15\right)=\frac{11}{15}x^{3}-\frac{26}{15}x^{2}+x,
$$

$$
S_1\left(x\right)=-\frac{4}{15}\left(x-1\right)\left(x-2\right)^{2}+\frac{1}{15}\left(x-2\right)\left(x-1\right)^{2}=\frac{1}{15}\left(x-1\right)\left(x-2\right)\left(7-3x\right)=-\frac{1}{5}x^{3}+\frac{16}{15}x^{2}-\frac{9}{5}x+\frac{14}{15},
$$

$$
S_2\left(x\right)=\frac{1}{15}\left(x-2\right)\left(x-3\right)^{2}+0=\frac{1}{15}\left(x-2\right)\left(x-3\right)^{2}=\frac{1}{15}x^{3}-\frac{8}{15}x^{2}+\frac{7}{5}x-\frac{6}{5}.
$$

(2) 的资料为 $M=\left(1,-\dfrac{4}{15},\dfrac{1}{15},0\right)$, 由**公式 (5.37) (三弯矩形式的分段表达式)**, 因 $y_j$ 全为零, 取 $h_j=1$ 得

$$
S_j\left(x\right)=\frac{M_{j+1}\left(x-x_j\right)^{3}}{6}-\frac{M_j\left(x-x_{j+1}\right)^{3}}{6}-\frac{M_{j+1}}{6}\left(x-x_j\right)+\frac{M_j}{6}\left(x-x_{j+1}\right).
$$

逐段代入并整理:

$$
S_0\left(x\right)=\frac{1}{6}\left[-\frac{4}{15}x^{3}-1\cdot\left(x-1\right)^{3}\right]-\frac{1}{6}\left[-\frac{4}{15}x-1\cdot\left(x-1\right)\right]=-\frac{19}{90}x^{3}+\frac{1}{2}x^{2}-\frac{13}{45}x,
$$

$$
S_1\left(x\right)=\frac{1}{6}\left[\frac{1}{15}\left(x-1\right)^{3}+\frac{4}{15}\left(x-2\right)^{3}\right]-\frac{1}{6}\left[\frac{1}{15}\left(x-1\right)+\frac{4}{15}\left(x-2\right)\right]=\frac{1}{18}x^{3}-\frac{3}{10}x^{2}+\frac{23}{45}x-\frac{4}{15},
$$

$$
S_2\left(x\right)=\frac{1}{6}\left[0-\frac{1}{15}\left(x-3\right)^{3}\right]-\frac{1}{6}\left[0-\frac{1}{15}\left(x-3\right)\right]=-\frac{1}{90}x^{3}+\frac{1}{10}x^{2}-\frac{13}{45}x+\frac{4}{15}.
$$

$\blacksquare$

(4) **校验**

按**定义 5.11 (三次样条插值)** 逐条核对 (1) 的结果. 插值条件: $S_0\left(0\right)=0$, $S_0\left(1\right)=0$, $S_1\left(2\right)=0$, $S_2\left(3\right)=0$. 内部节点 $x=1$: $S_0'\left(1\right)=\dfrac{33-52+15}{15}=-\dfrac{4}{15}$, $S_1'\left(1\right)=-\dfrac{9}{15}+\dfrac{32}{15}-\dfrac{27}{15}=-\dfrac{4}{15}$, 一阶导数连续; $S_0''\left(1\right)=\dfrac{66-52}{15}=\dfrac{14}{15}$, $S_1''\left(1\right)=-\dfrac{18}{15}+\dfrac{32}{15}=\dfrac{14}{15}$, 二阶导数连续. 内部节点 $x=2$: $S_1'\left(2\right)=-\dfrac{12}{5}+\dfrac{64}{15}-\dfrac{9}{5}=\dfrac{1}{15}$, $S_2'\left(2\right)=\dfrac{12}{15}-\dfrac{32}{15}+\dfrac{21}{15}=\dfrac{1}{15}$; $S_1''\left(2\right)=-\dfrac{12}{5}+\dfrac{32}{15}=-\dfrac{4}{15}$, $S_2''\left(2\right)=\dfrac{12}{15}-\dfrac{16}{15}=-\dfrac{4}{15}$, 均连续. 边界条件: $S_0'\left(0\right)=1=m_0$, $S_2'\left(3\right)=\dfrac{27}{15}-\dfrac{48}{15}+\dfrac{21}{15}=0=m_3$.

(2) 的结果同样: 插值条件成立; $S''\left(1\right)=-\dfrac{4}{15}=M_1$, $S''\left(2\right)=\dfrac{1}{15}=M_2$ (两侧一致), $S'\left(1\right)=\dfrac{7}{90}$ 与 $S'\left(2\right)=-\dfrac{1}{45}$ 两侧一致; 端点 $S_0''\left(0\right)=1=M_0$, $S_2''\left(3\right)=0=M_3$.

两点说明. 其一, 两组参数解数值相同 ($m_j=M_j$), 这只是因为 $y_j\equiv0$ 与两组边界值 $\left(1,0\right)$ 相同的巧合, 两条曲线并不相同: 第一组固定端点斜率, 其端点曲率为 $S''\left(0\right)=-\dfrac{52}{15}$, $S''\left(3\right)=\dfrac{2}{15}$; 第二组固定端点曲率, 其端点斜率为 $S'\left(0\right)=-\dfrac{13}{45}$, $S'\left(3\right)=\dfrac{1}{90}$. 其二, 因 $y_j\equiv0$, 两条样条都在 $\left[0,3\right]$ 上取零的函数值而中间起伏, 这正是边界斜率与曲率不匹配时的典型表现.

$\blacksquare$

## 习题 6-1 (一次最小二乘拟合)

已知数据表

| $x_i$ | $1.36$ | $1.49$ | $1.73$ | $1.81$ | $1.95$ | $2.16$ | $2.28$ | $2.48$ |
|---|---|---|---|---|---|---|---|---|
| $y_i$ | $14.094$ | $15.069$ | $16.844$ | $17.378$ | $18.435$ | $19.949$ | $20.963$ | $22.495$ |

试求其最小二乘一次拟合多项式.

### 解答 6-1

取 $\varphi_0\left(x\right)=1$, $\varphi_1\left(x\right)=x$, 权 $\omega_i=1$, 拟合函数 $\varphi\left(x\right)=a_0+a_1x$. 计算五个和:

$$
n=8,\quad\sum{}x_i=15.26,\quad\sum{}x_i^{2}=30.1556,\quad\sum{}y_i=145.227,\quad\sum{}x_iy_i=284.83628.
$$

由**定理 6.1 (正则方程组的解即最小二乘函数)**, 正则方程组为

$$
\begin{cases}8a_0+15.26a_1=145.227,\\15.26a_0+30.1556a_1=284.83628,\end{cases}
$$

系数行列式 $\Delta=8\times30.1556-15.26^{2}=241.2448-232.8676=8.3772$, 故

$$
a_1=\frac{8\times284.83628-15.26\times145.227}{8.3772}=\frac{2278.69024-2216.56402}{8.3772}=\frac{62.12622}{8.3772}\approx7.463857,
$$

$$
a_0=\frac{145.227-15.26\times7.463857}{8}=\frac{145.227-113.898457}{8}\approx3.916068.
$$

于是

$$
\varphi\left(x\right)=3.9161+7.4639x.
$$

$\blacksquare$

**残差校核**. 残差平方和 $Q=\sum\left(y_i-\varphi\left(x_i\right)\right)^{2}=0.019003$, 八点残差依次为 $0.0271$, $0.0318$, $0.0155$, $-0.0476$, $-0.0356$, $-0.0890$, $0.0293$, $0.0686$, 绝对值的最大者为 $0.089$, 与 $y$ 本身 $14$ 至 $22$ 的量级相比约为千分之四, 一次模型已足够. 又 $a_1\approx7.46>0$, 说明 $y$ 随 $x$ 单调上升, 数据基本落在一条直线上.

$\blacksquare$

## 习题 6-3 (钢液含碳量与冶炼时间的拟合)

某平炉的生产记录为

| $i$ | $1$ | $2$ | $3$ | $4$ | $5$ |
|---|---|---|---|---|---|
| $x_i$ | $165$ | $123$ | $150$ | $121$ | $141$ |
| $y_i$ | $187$ | $126$ | $172$ | $125$ | $148$ |

$i$ 为实验次数, $x_i$ 为全部炉料熔化完毕时钢液的含碳量, $y_i$ 为熔毕至出钢所需的冶炼时间, 求二者的函数关系.

### 解答 6-3

仍取 $\varphi_0\left(x\right)=1$, $\varphi_1\left(x\right)=x$, $\omega_i=1$, 计算

$$
n=5,\quad\sum{}x_i=700,\quad\sum{}x_i^{2}=99376,\quad\sum{}y_i=758,\quad\sum{}x_iy_i=108146.
$$

由**定理 6.1 (正则方程组的解即最小二乘函数)**, 正则方程组为

$$
\begin{cases}5a_0+700a_1=758,\\700a_0+99376a_1=108146,\end{cases}
$$

$\Delta=5\times99376-700^{2}=496880-490000=6880$, 故

$$
a_1=\frac{5\times108146-700\times758}{6880}=\frac{540730-530600}{6880}=\frac{10130}{6880}\approx1.472384,
$$

$$
a_0=\frac{758-700\times1.472384}{5}=\frac{758-1030.6688}{5}\approx-54.5337.
$$

即

$$
y\approx-54.534+1.4724x,
$$

即冶炼时间随含碳量增加而加长, 含碳量每增加 $1$ 个单位, 冶炼时间约延长 $1.47$ 个单位.

$\blacksquare$

**残差校核**. 五个点的残差依次为 $-1.41$, $-0.57$, $5.68$, $1.38$, $-5.07$, 平方和 $Q=62.15$, 均方根约 $3.53$. 残差在两头一负一正, 与随机误差的形态相符, 故一次式可用.

$\blacksquare$

**模型是否够用**. 若再加一项 $a_2x^{2}$, 正则方程组的解为 $a_0\approx-53.3148$, $a_1\approx1.4549$, $a_2\approx6.15\times10^{-5}$, 而 $Q$ 仍为 $62.15$, 二次项系数几乎为零, 可见这五个点几乎共线, 一次拟合不损失信息; 反之若硬用二次式, 只会引入一个数量级为 $10^{-5}$ 的无效系数. 故取一次式.

$\blacksquare$

## 习题 6-4 (形如 $y=a+bx^{2}$ 的经验公式)

用最小二乘法求形如 $y=a+bx^{2}$ 的经验公式拟合下列数据:

| $x_i$ | $19$ | $25$ | $31$ | $38$ | $44$ |
|---|---|---|---|---|---|
| $y_i$ | $19.0$ | $32.3$ | $49.0$ | $73.3$ | $97.8$ |

### 解答 6-4

模型对参数 $a,b$ 是线性的, 取 $\varphi_0\left(x\right)=1$, $\varphi_1\left(x\right)=x^{2}$, 记 $u_i=x_i^{2}$:

$$
u=\left(361,625,961,1444,1936\right).
$$

计算

$$
n=5,\quad\sum{}u_i=5327,\quad\sum{}u_i^{2}=7277699,\quad\sum{}y_i=271.4,\quad\sum{}u_iy_i=369321.5.
$$

由**定理 6.1 (正则方程组的解即最小二乘函数)**, 正则方程组为

$$
\begin{cases}5a+5327b=271.4,\\5327a+7277699b=369321.5,\end{cases}
$$

$\Delta=5\times7277699-5327^{2}=36388495-28376929=8011566$, 故

$$
b=\frac{5\times369321.5-5327\times271.4}{8011566}=\frac{1846607.5-1445749.8}{8011566}=\frac{400857.7}{8011566}\approx0.0500351,
$$

$$
a=\frac{271.4-5327\times0.0500351}{5}=\frac{271.4-266.5370}{5}\approx0.972579.
$$

于是经验公式为

$$
y=0.9726+0.050035x^{2}.
$$

$\blacksquare$

**残差校核**. $Q=\sum\left(y_i-a-bu_i\right)^{2}=0.015023$, 五个残差依次为 $-0.0353$, $0.0555$, $-0.0563$, $0.0767$, $-0.0405$, 绝对值最大者为 $0.077$ (在 $x=38$ 处), 相对 $y$ 本身不到千分之一, 拟合是好的. 又 $b>0$ 且 $b\approx0.05$, 说明 $y$ 随 $x^{2}$ 近似线性增长, 这就是该经验公式的实际含义.

$\blacksquare$

## 习题 6-6 (指数型经验公式 $y=ae^{bx}$)

用最小二乘法求形如 $y=ae^{bx}$ 的经验公式拟合下列数据:

| $x_i$ | $1$ | $2$ | $3$ | $4$ | $5$ | $6$ | $7$ | $8$ |
|---|---|---|---|---|---|---|---|---|
| $y_i$ | $15.3$ | $20.5$ | $27.4$ | $36.6$ | $49.1$ | $65.6$ | $87.87$ | $117.6$ |

### 解答 6-6

两边取对数化为线性模型: $\ln{}y=\ln{}a+bx$. 记 $v_i=\ln{}y_i$, 取 $\varphi_0\left(x\right)=1$, $\varphi_1\left(x\right)=x$, 待定系数为 $\ln{}a$ 与 $b$. 数据为

$$
v=\left(2.727853,3.020425,3.310543,3.600048,3.893859,4.183576,4.475858,4.767289\right).
$$

计算

$$
n=8,\quad\sum{}x_i=36,\quad\sum{}x_i^{2}=204,\quad\sum{}v_i=29.979451,\quad\sum{}x_iv_i=147.140593.
$$

由**定理 6.1 (正则方程组的解即最小二乘函数)**, 正则方程组为

$$
\begin{cases}8\ln{}a+36b=29.979451,\\36\ln{}a+204b=147.140593,\end{cases}
$$

$\Delta=8\times204-36^{2}=1632-1296=336$, 故

$$
b=\frac{8\times147.140593-36\times29.979451}{336}=\frac{1177.124744-1079.260236}{336}=\frac{97.864508}{336}\approx0.291263,
$$

$$
\ln{}a=\frac{29.979451-36\times0.291263}{8}=\frac{29.979451-10.485468}{8}\approx2.436748,
$$

$$
a\approx11.43577.
$$

于是

$$
y\approx11.4358e^{0.291263x}.
$$

$\blacksquare$

**残差校核**. 把拟合值代回原变量: $x=1,2,\ldots,8$ 处依次得 $15.302$, $20.476$, $27.400$, $36.664$, $49.061$, $65.649$, $87.846$, $117.549$, 与实测值的最大偏差为 $0.064$, 残差平方和 $\sum\left(y_i-ae^{bx_i}\right)^{2}=0.0118$, 八点残差均在 $0.06$ 以内且正负交替, 说明模型形式选对了.

$\blacksquare$

**方法说明**. 对数变换是拟合一类的标准化简, 它最小化的是 $\sum\left(\ln{}y_i-\ln{}a-bx_i\right)^{2}$, 而不是 $\sum\left(y_i-ae^{bx_i}\right)^{2}$, 二者只在残差很小时近似等价. 本题 $y$ 从 $15.3$ 单调增到 $117.6$, 相邻比值的对数平均即 $b$ 的估计 $0.291$, 而 $\ln{}y$ 关于 $x$ 的残差只有 $5.9\times10^{-6}$ 量级, 说明 $\ln{}y$ 几乎严格是 $x$ 的一次函数, 用对数最小二乘是恰当的.

$\blacksquare$
