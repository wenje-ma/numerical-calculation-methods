# week11

> **定义 7.2 (Gauss 点与 Gauss 型求积公式)**
> 
> 若节点 $x_1,x_2,\ldots,x_n\in\left[a,b\right]$ 使带权求积公式 $\int_a^b\rho\left(x\right)f\left(x\right)\mathrm{d}x\approx\sum_{k=1}^{n}A_kf\left(x_k\right)$ 具有 $2n-1$ 次代数精确度, 则称 $\left\{x_k\right\}$ 为 Gauss 点, 该公式称为带权函数 $\rho\left(x\right)$ 的 Gauss 型求积公式. (教材 $\S7.5.1$, p218)

> **公式 (7.29) (复化梯形公式)**
> 
> 将 $\left[a,b\right]$ 等分为 $n$ 份, $h=\dfrac{b-a}{n}$, $x_k=a+kh$, 则 $\int_a^bf\left(x\right)\mathrm{d}x\approx h\left[\dfrac{1}{2}f\left(a\right)+\sum_{k=1}^{n-1}f\left(x_k\right)+\dfrac{1}{2}f\left(b\right)\right]$. (教材 $\S7.3$, p206)

> **公式 (7.31) (复化 Simpson 公式)**
> 
> 将 $\left[a,b\right]$ 分成 $n=2m$ 等份, $h=\dfrac{b-a}{n}$, 则 $\int_a^bf\left(x\right)\mathrm{d}x\approx\dfrac{h}{3}\left[f\left(a\right)+f\left(b\right)+2\sum_{k=1}^{m-1}f\left(x_{2k}\right)+4\sum_{k=1}^{m}f\left(x_{2k-1}\right)\right]$. (教材 $\S7.3$, p207)

> **定义 8.2 (收敛阶)**
> 
> 设序列 $\left\{x_n\right\}$ 收敛于 $x^{*}$, 若存在正数 $r$ 和 $a$, 使 $\lim_{n\to\infty}\dfrac{\left|x_{n+1}-x^{*}\right|}{\left|x_n-x^{*}\right|^{r}}=a$ 成立, 则称 $\left\{x_n\right\}$ 是 $r$ 阶收敛的 ($r=1$ 时要求 $a<1$). $r=1$ 称线性收敛, $r>1$ 称超线性收敛, $r=2$ 称平方收敛. (教材 $\S8.2.3$, p256)

> **定理 8.1 (压缩映射原理)**
> 
> 若 $\varphi\left(x\right)$ 在 $\left[a,b\right]$ 上满足 (1) 对任意 $x\in\left[a,b\right]$ 有 $\varphi\left(x\right)\in\left[a,b\right]$; (2) 存在 $0<L<1$ 使对一切 $x,y\in\left[a,b\right]$ 有 $\left|\varphi\left(x\right)-\varphi\left(y\right)\right|\le L\left|x-y\right|$, 则 $x=\varphi\left(x\right)$ 在 $\left[a,b\right]$ 内有唯一根 $x^{*}$, 且对任意 $x_0\in\left[a,b\right]$ 迭代序列 $x_{n+1}=\varphi\left(x_n\right)$ 收敛于 $x^{*}$, 并有 $\left|x^{*}-x_n\right|\le\dfrac{L^{n}}{1-L}\left|x_1-x_0\right|$ 与 $\left|x^{*}-x_n\right|\le\dfrac{L}{1-L}\left|x_n-x_{n-1}\right|$. (教材 $\S8.2.2$, p253)

> **定理 8.2 (用导数界判别不动点迭代的收敛性)**
> 
> 若 $\varphi\left(x\right)$ 在 $\left[a,b\right]$ 上满足 (1) 对任意 $x\in\left[a,b\right]$ 有 $\varphi\left(x\right)\in\left[a,b\right]$; (2) 存在 $0<L<1$ 使对任意 $x\in\left[a,b\right]$ 有 $\left|\varphi'\left(x\right)\right|\le L$, 则方程 $x=\varphi\left(x\right)$ 在 $\left[a,b\right]$ 上有唯一根 $x^{*}$, 且对任意初值 $x_0\in\left[a,b\right]$ 迭代序列收敛于 $x^{*}$, 并有 $\left|x^{*}-x_n\right|\le\dfrac{L}{1-L}\left|x_n-x_{n-1}\right|$. (教材 $\S8.2.2$, p255)

> **定理 8.4 (迭代序列收敛阶的判别)**
> 
> 若 $\varphi\left(x\right)$ 在 $x^{*}$ 邻近有 $r$ 阶连续导数 ($r\ge2$), $x^{*}=\varphi\left(x^{*}\right)$, $\varphi^{\left(k\right)}\left(x^{*}\right)=0$ ($k=1,2,\ldots,r-1$), $\varphi^{\left(r\right)}\left(x^{*}\right)\ne0$, 则迭代序列 $\left\{x_n\right\}$ 是 $r$ 阶收敛的; 若 $0<\left|\varphi'\left(x^{*}\right)\right|<1$, 则 $\left\{x_n\right\}$ 是线性收敛的. (教材 $\S8.2.3$, p257)

## 习题 7-21 (三点与五点 Gauss-Legendre 公式)

用三点及五点 Gauss-Legendre 求积公式计算积分

$$
I=\int_0^1\frac{2\sin\left(2x-1\right)}{3-2x}\,\mathrm{d}x.
$$

### 解答 7-21

**化到标准区间**. 令 $t=2x-1$, 则 $x=\dfrac{t+1}{2}$, $\mathrm{d}x=\dfrac{1}{2}\mathrm{d}t$, $x\in\left[0,1\right]$ 对应 $t\in\left[-1,1\right]$, 且 $3-2x=3-\left(t+1\right)=2-t$, 故

$$
I=\int_{-1}^{1}\frac{2\sin t}{2-t}\cdot\frac{1}{2}\mathrm{d}t=\int_{-1}^{1}\frac{\sin t}{2-t}\,\mathrm{d}t.
$$

记 $g\left(t\right)=\dfrac{\sin t}{2-t}$. 在 $\left[-1,1\right]$ 上 $2-t\ge1>0$, $g$ 光滑且无奇点, 只是 $g$ 本身的奇点在 $t=2$ (公式预分式零点), 它离积分区间只有 $1$ 的距离, 这一点后文会用到.

$\blacksquare$

**三点公式**. 由教材表 7.4 (Gauss-Legendre 求积公式的节点与系数), 三点节点与权为 $t=\mp0.77459667,0$ 与 $A=0.55555556,0.88888889,0.55555556$. 由**定义 7.2 (Gauss 点与 Gauss 型求积公式)**, 它精确到 $2n-1=5$ 次. 节点处函数值为

$$
g\left(-0.77459667\right)=-0.25208272,\qquad g\left(0\right)=0,\qquad g\left(0.77459667\right)=0.57077360,
$$

于是

$$
I\approx0.55555556\times\left(-0.25208272\right)+0.88888889\times0+0.55555556\times0.57077360
$$

$$
=0.55555556\times0.31869088=0.17705049.
$$

**五点公式**. 五点节点与权为 $t=0,\mp0.53846931,\mp0.90617985$ 与 $A=0.56888889,0.47862867,0.23692689$, 精确到 $2n-1=9$ 次. 函数值为

$$
g\left(0\right)=0,\quad g\left(\pm0.53846931\right)=0.35088042,\ -0.20202037,
$$

$$
g\left(\pm0.90617985\right)=0.71963693,\ -0.27085501.
$$

$$
I\approx0.56888889\times0+0.47862867\times\left(0.35088042-0.20202037\right)+0.23692689\times\left(0.71963693-0.27085501\right)
$$

$$
=0.47862867\times0.14886005+0.23692689\times0.44878192=0.07124304+0.10633417=0.17757719.
$$

$\blacksquare$

**误差**. 该积分的值为 $I=0.1775799623$ (由高精度复化 Simpson 与 Romberg 校核), 故

$$
I_{3}-I=0.17705049-0.17757996=-5.294\times10^{-4},\qquad I_{5}-I=0.17757719-0.17757996=-2.77\times10^{-6}.
$$

$\blacksquare$

**讨论**. 五点公式的误差是三点公式的 $1/191$, 相当于多用了 $2$ 个节点就换来两位以上有效数字. 原因是 $g$ 在 $\left[-1,1\right]$ 上除 $t=2$ 外处处解析, 而 $t=2$ 到区间中心 $0$ 的距离为 $2$, 故 $g$ 的 Taylor 级数在 $\left[-1,1\right]$ 上收敛且系数按 $2^{-k}$ 衰减; 这使高精度插值型公式的误差衰减得很快, 与低阶求积在"端点奇性"下精度停滞的典型表现形成对照. 若被积函数在区间端点有奇性 (如 $\sqrt{x}$, $1/\sqrt{x}$), Gauss-Legendre 公式则退化, 此时必须换用带相应权函数的 Gauss 型公式, 这也是下一题的做法.

$\blacksquare$

## 习题 7-26(1) (二重积分的复化梯形与复化 Simpson)

设 $n=m=4$, 分别用复化梯形公式和复化 Simpson 公式计算二重积分

$$
Y=\int_{1.0}^{1.5}\mathrm{d}x\int_{1.2}^{1.6}\ln\left(x+2y\right)\mathrm{d}y,
$$

并将计算结果与精确值作比较.

### 解答 7-26(1)

**剖分与权重**. $x$ 方向 $\left[1.0,1.5\right]$ 四等分, $h_x=0.125$, 节点 $x_i=1.0+0.125i$; $y$ 方向 $\left[1.2,1.6\right]$ 四等分, $h_y=0.1$, 节点 $y_j=1.2+0.1j$. 由**公式 (7.29) (复化梯形公式)** 与**公式 (7.31) (复化 Simpson 公式)** 可直接张量积成二维权重:

$$
w^{T}=\left(\frac{1}{2},1,1,1,\frac{1}{2}\right),\qquad w^{S}=\left(1,4,2,4,1\right),
$$

二维复化梯形取 $I\approx h_xh_y\sum_{i,j}w_i^{T}w_j^{T}f\left(x_i,y_j\right)$, 二维复化 Simpson 取 $I\approx\dfrac{h_xh_y}{9}\sum_{i,j}w_i^{S}w_j^{S}f\left(x_i,y_j\right)$.

$\blacksquare$

**先积 $y$**. 对每个 $x_i$, 用 $y$ 方向的一维公式算内层 $\displaystyle\int_{1.2}^{1.6}\ln\left(x_i+2y\right)\mathrm{d}y$:

| $x_i$ | 内层梯形 | 内层 Simpson |
|---|---|---|
| $1.000$ | $0.533165925$ | $0.533259164$ |
| $1.125$ | $0.546164551$ | $0.546251892$ |
| $1.250$ | $0.558752464$ | $0.558834452$ |
| $1.375$ | $0.570954917$ | $0.571032029$ |
| $1.500$ | $0.582794892$ | $0.582867553$ |

$\blacksquare$

**再积 $x$**. 梯形外层: $h_x\left[\dfrac{1}{2}\left(0.533165925+0.582794892\right)+0.546164551+0.558752464+0.570954917\right]$

$$
=0.125\times\left(0.557980409+1.675871932\right)=0.125\times2.233852341=0.27923154.
$$

Simpson 外层: $\dfrac{h_x}{3}\left[0.533259164+0.582867553+2\times0.558834452+4\times\left(0.546251892+0.571032029\right)\right]$

$$
=0.04166667\times\left(1.116126717+1.117668904+4.469135684\right)=0.04166667\times6.702931305=0.27928880.
$$

$\blacksquare$

**与精确值比较**. 精确值为

$$
Y=0.2792888519
$$

(先对 $y$ 用原函数 $\dfrac{\left(x+2y\right)\ln\left(x+2y\right)-\left(x+2y\right)}{2}$ 精确积分, 再对 $x$ 作高精度积分, 两种算法一致到十位). 于是

$$
Y_T-Y=-5.73\times10^{-5},\qquad Y_S-Y=-4.75\times10^{-8}.
$$

$\blacksquare$

**误差结构**. 二维张量积的截断误差是两方向误差之和, 梯形为 $O\left(h_x^{2}\right)+O\left(h_y^{2}\right)$, Simpson 为 $O\left(h_x^{4}\right)+O\left(h_y^{4}\right)$. 对梯形可算出主项

$$
R_T\approx-\frac{h_x^{2}}{12}\iint f_{xx}\,\mathrm{d}x\mathrm{d}y-\frac{h_y^{2}}{12}\iint f_{yy}\,\mathrm{d}x\mathrm{d}y,
$$

其中 $\displaystyle\iint f_{xx}\,\mathrm{d}x\mathrm{d}y=0.010127$, $\displaystyle\iint f_{yy}\,\mathrm{d}x\mathrm{d}y=0.049540$, 故

$$
R_T\approx-\frac{0.015625}{12}\times0.010127-\frac{0.01}{12}\times0.049540=-1.32\times10^{-5}-4.13\times10^{-5}=-5.45\times10^{-5},
$$

与实测 $-5.73\times10^{-5}$ 吻合. 这说明本题梯形误差的 $87\%$ 来自 $y$ 方向: $\ln\left(x+2y\right)$ 关于 $y$ 的二阶导数是 $-\dfrac{4}{\left(x+2y\right)^{2}}$, 关于 $x$ 的二阶导数只有 $-\dfrac{1}{\left(x+2y\right)^{2}}$, 相差 $4$ 倍, 再叠加 $h_y$ 与 $h_x$ 的比例关系.

$\blacksquare$

## 习题 7-27 (x 方向梯形与 y 方向 Simpson 的混合公式)

设 $n=m=4$, 试推导在 $x$ 方向用复化梯形公式, 在 $y$ 方向用复化 Simpson 公式的矩形区域上二重积分的近似求积公式, 并计算 7-26 题中的积分.

### 解答 7-27

**推导**. 设矩形 $D=\left[a,b\right]\times\left[c,d\right]$, $x$ 方向 $n$ 等分 ($h_x=\dfrac{b-a}{n}$), $y$ 方向 $m$ 等分 ($m$ 为偶数, $h_y=\dfrac{d-c}{m}$). 先对每个固定的 $x$ 用 $y$ 方向的复化 Simpson 公式积分:

$$
\int_c^df\left(x,y\right)\mathrm{d}y\approx\frac{h_y}{3}\sum_{j=0}^{m}w_j^{S}f\left(x,y_j\right)=:S\left(x\right),
$$

其中 $w^{S}=\left(1,4,2,4,\ldots,2,4,1\right)$, $y_j=c+jh_y$. 再对 $S\left(x\right)$ 用**公式 (7.29) (复化梯形公式)**:

$$
I\approx h_x\left[\frac{1}{2}S\left(a\right)+\sum_{i=1}^{n-1}S\left(x_i\right)+\frac{1}{2}S\left(b\right)\right]=\frac{h_xh_y}{3}\sum_{i=0}^{n}\sum_{j=0}^{m}w_i^{T}w_j^{S}f\left(x_i,y_j\right),
$$

$w^{T}=\left(\dfrac{1}{2},1,\ldots,1,\dfrac{1}{2}\right)$. 这就是所求的混合求积公式, 其截断误差为 $O\left(h_x^{2}\right)+O\left(h_y^{4}\right)$, 即被"最弱"的那个方向卡住.

$\blacksquare$

**计算 7-26(1)**. 沿用上题的 $h_x=0.125$, $h_y=0.1$ 与内层 Simpson 值:

$$
I_{1}\approx h_x\left[\frac{1}{2}\left(0.533259164+0.582867553\right)+0.546251892+0.558834452+0.571032029\right]
$$

$$
=0.125\times\left(0.558063359+1.676118373\right)=0.125\times2.234181732=0.27927272.
$$

**计算 7-26(2)**. 对 $I=\displaystyle\int_0^{0.5}\mathrm{d}x\int_1^{1.5}\frac{\mathrm{d}y}{1+xy}$, 同样 $h_x=0.125$ (节点 $0,0.125,\ldots,0.5$), $h_y=0.125$ (节点 $1,1.125,\ldots,1.5$), 内层 Simpson 值为 $0.500000000$, $0.432537772$, $0.381240736$, $0.340889039$, $0.308301452$, 于是

$$
I_{2}\approx0.125\left[\frac{1}{2}\left(0.500000000+0.308301452\right)+0.432537772+0.381240736+0.340889039\right]
$$

$$
=0.125\times\left(0.404150726+1.154667547\right)=0.125\times1.558818273=0.19485228.
$$

$\blacksquare$

**与精确值及全 Simpson 结果比较**. 两个积分的精确值为 $Y=0.2792888519$ 与 $I=0.1943470619$, 四种组合的结果汇总如下.

| 组合 ($x$ 方向 / $y$ 方向) | 7-26(1) | 误差 | 7-26(2) | 误差 |
|---|---|---|---|---|
| 梯形 / 梯形 | $0.27923154$ | $-5.73\times10^{-5}$ | $0.19487051$ | $+5.23\times10^{-4}$ |
| 梯形 / Simpson | $0.27927272$ | $-1.61\times10^{-5}$ | $0.19485228$ | $+5.05\times10^{-4}$ |
| Simpson / 梯形 | $0.27924765$ | $-4.12\times10^{-5}$ | $0.19437186$ | $+2.48\times10^{-5}$ |
| Simpson / Simpson | $0.27928880$ | $-4.75\times10^{-8}$ | $0.19435376$ | $+6.70\times10^{-6}$ |

$\blacksquare$

**讨论**. 对 (1), 混合公式把误差从 $5.73\times10^{-5}$ 降到 $1.61\times10^{-5}$, 改善 $3.6$ 倍, 但远不如把 $x$ 方向也升阶 (Simpson/梯形为 $4.12\times10^{-5}$, 全 Simpson 为 $4.75\times10^{-8}$). 这与误差主项的结构一致: 上题已算出本题梯形误差 $87\%$ 出自 $y$ 方向, 故升 $y$ 方向的阶只吃掉那一部分, 剩下的 $x$ 方向 $O\left(h_x^{2}\right)$ 依旧存在, 仍大于全 Simpson 的 $O\left(h_y^{4}\right)$ 修正量的一半以上. 对 (2) 更明显: 混合公式只把误差从 $5.23\times10^{-4}$ 改到 $5.05\times10^{-4}$ ($3.4\%$), 因为 $1/\left(1+xy\right)$ 在 $x=0$ 处关于 $y$ 是常数, 内层梯形在该列已经精确, $y$ 方向的误差本来就集中在右端几列, 升阶收效甚微; 而把 $x$ 方向换成 Simpson 后误差立刻降到 $2.48\times10^{-5}$. 结论: 混合阶公式的实际精度由低阶方向决定, 若要真正提高精度, 应升级误差贡献大的那个方向, 而不是任意一个方向.

$\blacksquare$

## 习题 8-3 (简单迭代法求三个方程的根)

用简单迭代法求下列方程的根, 要求 $\left|x_{n+1}-x_n\right|<10^{-5}$:

(1) $x-\cos x=0$; (2) $4x-e^{-x}=0$; (3) $x^{3}-2x-5=0$.

### 解答 8-3

**(1) $x=\cos x$**. 取迭代函数 $\varphi\left(x\right)=\cos x$, 初值 $x_0=0.5$. 在区间 $\left[0.5,0.9\right]$ 上 $\cos x$ 单调递减, 取值从 $0.877583$ 降到 $0.621610$, 故 $\varphi\left(\left[0.5,0.9\right]\right)\subset\left[0.5,0.9\right]$; 又 $\left|\varphi'\left(x\right)\right|=\left|\sin x\right|\le\sin0.9=0.783327=L<1$, 由**定理 8.2 (用导数界判别不动点迭代的收敛性)** 迭代必收敛. 计算得

| $n$ | $0$ | $1$ | $2$ | $3$ | $4$ | $5$ |
|---|---|---|---|---|---|---|
| $x_n$ | $0.500000$ | $0.877583$ | $0.639012$ | $0.802685$ | $0.694778$ | $0.768196$ |

| $n$ | $10$ | $15$ | $20$ | $25$ | $26$ | $27$ | $28$ |
|---|---|---|---|---|---|---|---|
| $x_n$ | $0.735006$ | $0.739650$ | $0.739007$ | $0.739096$ | $0.739078$ | $0.739090$ | $0.739082$ |

$\left|x_{28}-x_{27}\right|=\left|0.73908181-0.73909006\right|=8.25\times10^{-6}<10^{-5}$, 故 $x^{*}\approx0.7390818$, 而真值为 $0.7390851$, 误差 $3.3\times10^{-6}$. 迭代在根两侧来回跳跃, 收敛率约为 $0.6736=\left|\sin x^{*}\right|$, 每步只减少 $1/3$ 的误差, 因此走了 $28$ 步.

$\blacksquare$

**(2) $4x=e^{-x}$, 即 $x=\dfrac{e^{-x}}{4}$**. 取 $\varphi\left(x\right)=\dfrac{e^{-x}}{4}$, $x_0=0.5$. 在 $\left[0,0.5\right]$ 上 $\varphi$ 递减, $\varphi\left(\left[0,0.5\right]\right)=\left[0.151633,0.25\right]\subset\left[0,0.5\right]$, 且 $\left|\varphi'\left(x\right)\right|=\dfrac{e^{-x}}{4}\le\dfrac{1}{4}=L$, 由**定理 8.2 (用导数界判别不动点迭代的收敛性)** 收敛, 且理论误差界 $\left|x^{*}-x_n\right|\le\dfrac{1}{3}\left|x_n-x_{n-1}\right|$.

| $n$ | $0$ | $1$ | $2$ | $3$ | $4$ | $5$ | $6$ | $7$ | $8$ |
|---|---|---|---|---|---|---|---|---|---|
| $x_n$ | $0.500000$ | $0.151633$ | $0.214826$ | $0.201670$ | $0.204341$ | $0.203796$ | $0.203907$ | $0.203885$ | $0.203889$ |

$\left|x_8-x_7\right|=\left|0.20388914-0.20388452\right|=4.62\times10^{-6}<10^{-5}$, 故 $x^{*}\approx0.2038891$; 真值为 $0.2038884$, 误差 $1.9\times10^{-6}$. 压缩率 $L=1/4$ 使每步误差降到 $1/4$, 只用了 $8$ 步.

$\blacksquare$

**(3) $x^{3}-2x-5=0$**. 取 $\varphi\left(x\right)=\left(2x+5\right)^{1/3}$, 初值 $x_0=2$. 在 $\left[2,2.2\right]$ 上 $\varphi$ 递增, $\varphi\left(2\right)=\sqrt[3]{9}=2.080084$, $\varphi\left(2.2\right)=\sqrt[3]{9.4}=2.110424$, 故 $\varphi\left(\left[2,2.2\right]\right)\subset\left[2,2.2\right]$; 又

$$
\varphi'\left(x\right)=\frac{2}{3\left(2x+5\right)^{2/3}}\le\frac{2}{3\sqrt[3]{81}}=0.154,
$$

由**定理 8.2 (用导数界判别不动点迭代的收敛性)** 收敛.

| $n$ | $0$ | $1$ | $2$ | $3$ | $4$ | $5$ | $6$ |
|---|---|---|---|---|---|---|---|
| $x_n$ | $2.000000$ | $2.080084$ | $2.092351$ | $2.094217$ | $2.094501$ | $2.094544$ | $2.094550$ |

$\left|x_6-x_5\right|=\left|2.09455031-2.09454376\right|=6.55\times10^{-6}<10^{-5}$, 故 $x^{*}\approx2.0945503$, 真值 $2.0945515$, 误差 $1.2\times10^{-6}$.

$\blacksquare$

**注**. 三个方程都满足同样的停步准则, 但所需步数从 $28$ 步降到 $8$ 步再到 $6$ 步, 差别完全由压缩率决定: $L_1=0.783$ 需要约 $28$ 步, $L_2=0.25$ 需要约 $8$ 步, $L_3=0.154$ 需要约 $6$ 步, 因为每步误差按 $L$ 的幂次衰减, 步数约等于 $\dfrac{\ln\left(\varepsilon/\left|x_0-x^{*}\right|\right)}{\ln L}$. 另外要提醒: 停步准则 $\left|x_{n+1}-x_n\right|<\varepsilon$ 并不自动保证误差不超过 $\varepsilon$. 由**定理 8.1 (压缩映射原理)** 的 $\left|x^{*}-x_n\right|\le\dfrac{L}{1-L}\left|x_n-x_{n-1}\right|$, 本题 (1) 的放大因子是 $\dfrac{0.783}{0.217}=3.61$, 故第 $28$ 步的真实误差界约 $2.99\times10^{-5}$, 已超过 $10^{-5}$; 若既要满足"步差"判据又要误差真的在 $10^{-5}$ 以内, 应做到 $\left|x_n-x_{n-1}\right|<\dfrac{1-L}{L}\varepsilon=2.77\times10^{-6}$, 即再迭代到第 $31$ 步 ($\left|x_{31}-x_{30}\right|=2.52\times10^{-6}$).

$\blacksquare$

## 习题 8-7 (全局收敛性与收敛阶)

设有解方程 $12-3x+2\cos x=0$ 的迭代法

$$
x_{n+1}=4+\frac{2}{3}\cos x_n.
$$

(1) 证明对任意 $x_0\in\mathbb{R}$, 此迭代法均收敛到方程的根; (2) 取 $x_0=4$, 用此迭代法求方程根的近似值, 使其误差不超过 $\dfrac{1}{2}\times10^{-5}$; (3) 此迭代法的收敛阶是多少? 说明理由.

### 解答 8-7

**(1) 全局收敛性**. 方程等价于 $x=\varphi\left(x\right)$, $\varphi\left(x\right)=4+\dfrac{2}{3}\cos x$, 定义域为整个 $\mathbb{R}$.

第一步, 值域有界. 对任意 $x\in\mathbb{R}$,

$$
\varphi\left(x\right)\in\left[4-\frac{2}{3},4+\frac{2}{3}\right]=\left[\frac{10}{3},\frac{14}{3}\right].
$$

第二步, 在 $\left[\dfrac{10}{3},\dfrac{14}{3}\right]$ 上 $\varphi$ 把区间映入自身. 该区间长 $1.3333$ 且跨过 $\pi$, 故 $\cos$ 的最小值为 $\cos\pi=-1$ (在 $x=\pi$ 处), 最大值在右端点 $\cos\dfrac{14}{3}=-0.045706$ (左端 $\cos\dfrac{10}{3}=-0.981674$ 更小), 于是

$$
\varphi\left(\left[\frac{10}{3},\frac{14}{3}\right]\right)=\left[4+\frac{2}{3}\times\left(-1\right),4+\frac{2}{3}\times\left(-0.045706\right)\right]=\left[3.333333,3.969529\right]\subset\left[\frac{10}{3},\frac{14}{3}\right].
$$

第三步, 导数界. $\left|\varphi'\left(x\right)\right|=\dfrac{2}{3}\left|\sin x\right|\le\dfrac{2}{3}=L<1$, 对一切 $x$ 成立.

于是 $\varphi$ 在 $\left[\dfrac{10}{3},\dfrac{14}{3}\right]$ 上满足**定理 8.1 (压缩映射原理)** 的两个条件, 该区间内有唯一根 $x^{*}$, 且对任意初值 $x_0\in\left[\dfrac{10}{3},\dfrac{14}{3}\right]$ 迭代收敛到 $x^{*}$. 对任意 $x_0\in\mathbb{R}$, 由于 $x_1=\varphi\left(x_0\right)\in\left[\dfrac{10}{3},\dfrac{14}{3}\right]$, 从 $x_1$ 起的迭代收敛, 故整个迭代序列收敛. 这就证明了全局收敛.

$\blacksquare$

**(2) 数值计算**. 由**定理 8.2 (用导数界判别不动点迭代的收敛性)** 的误差估计, 取 $L=\dfrac{2}{3}$, 有

$$
\left|x^{*}-x_n\right|\le\frac{L}{1-L}\left|x_n-x_{n-1}\right|=2\left|x_n-x_{n-1}\right|,
$$

故要求误差不超过 $\dfrac{1}{2}\times10^{-5}$ 时, 只需 $\left|x_n-x_{n-1}\right|\le\dfrac{1}{4}\times10^{-5}=2.5\times10^{-6}$. 计算得

| $n$ | $x_n$ | $\left|x_n-x_{n-1}\right|$ | $\left|x_n-x^{*}\right|$ |
|---|---|---|---|
| $0$ | $4.000000000$ | — | $6.53\times10^{-1}$ |
| $1$ | $3.564237586$ | $4.36\times10^{-1}$ | $2.17\times10^{-1}$ |
| $2$ | $3.391995167$ | $1.72\times10^{-1}$ | $4.46\times10^{-2}$ |
| $3$ | $3.354124827$ | $3.79\times10^{-2}$ | $6.72\times10^{-3}$ |
| $4$ | $3.348333385$ | $5.79\times10^{-3}$ | $9.31\times10^{-4}$ |
| $5$ | $3.347529903$ | $8.03\times10^{-4}$ | $1.27\times10^{-4}$ |
| $6$ | $3.347420159$ | $1.10\times10^{-4}$ | $1.73\times10^{-5}$ |
| $7$ | $3.347405202$ | $1.50\times10^{-5}$ | $2.36\times10^{-6}$ |
| $8$ | $3.347403165$ | $2.04\times10^{-6}$ | $3.21\times10^{-7}$ |

第 $8$ 步满足 $\left|x_8-x_7\right|=2.04\times10^{-6}<2.5\times10^{-6}$, 故 $x^{*}\approx3.3474032$, 实际误差 $3.2\times10^{-7}$, 结论为

$$
x^{*}=3.34740\ldots
$$

($12-3\times3.3474032+2\cos3.3474032=-9.2\times10^{-7}$, 说明残差也已在 $10^{-6}$ 量级; 注意 $x^{*}\approx3.3474$ 落在 $\left(\pi,\dfrac{3\pi}{2}\right)$ 内, 故 $\cos x^{*}=-0.978896$ 为负).

$\blacksquare$

**(3) 收敛阶**. $\varphi'\left(x^{*}\right)=-\dfrac{2}{3}\sin x^{*}$, 而 $x^{*}=3.3474028$ 落在 $\left(\pi,\dfrac{3\pi}{2}\right)$ 内, $\sin x^{*}=-0.204360$, 故

$$
\varphi'\left(x^{*}\right)=-\frac{2}{3}\times\left(-0.204360\right)=0.136240\ne0.
$$

按**定理 8.4 (迭代序列收敛阶的判别)**, 若 $0<\left|\varphi'\left(x^{*}\right)\right|<1$ 则序列线性收敛; 按**定义 8.2 (收敛阶)**, 此时

$$
\lim_{n\to\infty}\frac{\left|x_{n+1}-x^{*}\right|}{\left|x_n-x^{*}\right|}=\left|\varphi'\left(x^{*}\right)\right|=0.136240,
$$

即收敛阶 $r=1$, 渐进误差常数为 $0.136240$. 数值上也可以核对: $\dfrac{\left|x_8-x^{*}\right|}{\left|x_7-x^{*}\right|}=\dfrac{3.21\times10^{-7}}{2.36\times10^{-6}}=0.136$, 与 $0.136240$ 相符.

$\blacksquare$

**注**. 本题迭代虽然全局收敛, 但只是线性收敛, 原因正是 $\varphi'\left(x^{*}\right)\ne0$: 迭代函数在根处的斜率不为零, 每步只能把误差乘上 $0.136$. 若要达到二阶收敛, 须让 $\varphi'\left(x^{*}\right)=0$, 即把迭代函数改造成 Newton 型 $\varphi\left(x\right)=x-\dfrac{f\left(x\right)}{f'\left(x\right)}$. 取 $f\left(x\right)=12-3x+2\cos x$, $f'\left(x\right)=-3-2\sin x$, 在根处 $f'\left(x^{*}\right)=-3-2\times\left(-0.204360\right)=-3.408720$, Newton 格式为

$$
x_{n+1}=x_n-\frac{12-3x_n+2\cos x_n}{-3-2\sin x_n}.
$$

它每步误差按平方下降, 从 $x_0=4$ 出发三四步即可到 $10^{-9}$, 但每步要同时算 $\sin$ 与 $\cos$, 而简单迭代每步只要一次余弦, $8$ 步就到 $3\times10^{-7}$; 在本题这种"斜率本来就小"的场合, 简单迭代的性价比更高. 这也说明收敛阶不是唯一指标, 每步的计算代价同样重要.

$\blacksquare$
