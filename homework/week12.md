# week12

> **公式 (8.16) (Newton 迭代格式)**
> 
> $x_{n+1}=x_n-\dfrac{f\left(x_n\right)}{f'\left(x_n\right)}$, $n=0,1,2,\ldots$. (教材 $\S8.3.1$, p259)

> **公式 (8.17) (重根情形的改进 Newton 格式)**
> 
> 若 $x^{*}$ 是 $f\left(x\right)=0$ 的 $r$ 重根 ($r\ge2$), 则取 $x_{n+1}=x_n-r\dfrac{f\left(x_n\right)}{f'\left(x_n\right)}$, $n=0,1,2,\ldots$. (教材 $\S8.3.1$, p260)

> **公式 (8.19) (弦截法迭代格式)**
> 
> $x_{n+1}=x_n-\dfrac{f\left(x_n\right)}{f\left(x_n\right)-f\left(x_{n-1}\right)}\left(x_n-x_{n-1}\right)$, $n=1,2,\ldots$. (教材 $\S8.3.2$, p261)

> **定义 8.2 (收敛阶)**
> 
> 设序列 $\left\{x_n\right\}$ 收敛于 $x^{*}$, 若存在正数 $r$ 和 $a$, 使 $\lim_{n\to\infty}\dfrac{\left|x_{n+1}-x^{*}\right|}{\left|x_n-x^{*}\right|^{r}}=a$ 成立, 则称 $\left\{x_n\right\}$ 是 $r$ 阶收敛的 ($r=1$ 时要求 $a<1$). $r=1$ 称线性收敛, $r=2$ 称平方收敛. (教材 $\S8.2.3$, p256)

> **定理 8.4 (迭代序列收敛阶的判别)**
> 
> 若 $\varphi\left(x\right)$ 在 $x^{*}$ 邻近有 $r$ 阶连续导数 ($r\ge2$), $x^{*}=\varphi\left(x^{*}\right)$, $\varphi^{\left(k\right)}\left(x^{*}\right)=0$ ($k=1,2,\ldots,r-1$), $\varphi^{\left(r\right)}\left(x^{*}\right)\ne0$, 则迭代序列是 $r$ 阶收敛的; 若 $0<\left|\varphi'\left(x^{*}\right)\right|<1$, 则序列是线性收敛的. (教材 $\S8.2.3$, p257)

> **定理 8.5 (Newton 法的局部收敛性)**
> 
> 设 $f\left(x\right)$ 在其零点 $x^{*}$ 邻近二阶连续可微, 且 $f'\left(x^{*}\right)\ne0$, 则存在 $\delta>0$, 使得对任意 $x_0\in\left[x^{*}-\delta,x^{*}+\delta\right]$, Newton 法所产生的序列 $\left\{x_n\right\}$ 至少二阶收敛于 $x^{*}$. (教材 $\S8.3.1$, p260)

> **定理 8.6 (弦截法的收敛阶)**
> 
> 设 $f\left(x\right)$ 在 $x^{*}$ 邻近二阶连续可微, $f\left(x^{*}\right)=0$, $f'\left(x^{*}\right)\ne0$, 则存在 $\delta>0$, 当 $x_0,x_1\in\left[x^{*}-\delta,x^{*}+\delta\right]$ 时, 弦截法产生的序列收敛于 $x^{*}$, 且收敛阶至少为 $\dfrac{\sqrt{5}+1}{2}\approx1.618$. (教材 $\S8.3.2$, p262)

## 习题 8-8 (迭代序列收敛到 $\sqrt{2}$ 且二阶收敛)

证明由迭代格式

$$
x_{n+1}=\frac{x_n}{2}+\frac{1}{x_n}\qquad\left(n=0,1,2,\ldots\right)
$$

产生的迭代序列 $\left\{x_n\right\}$, 对任意 $x_0>1$ 均收敛到 $\sqrt{2}$, 且是二阶收敛的.

### 解答 8-8

**识别来源**. 该格式正是**公式 (8.16) (Newton 迭代格式)** 用于 $f\left(x\right)=x^{2}-2$ 的结果:

$$
x-\frac{x^{2}-2}{2x}=x-\frac{x}{2}+\frac{1}{x}=\frac{x}{2}+\frac{1}{x}.
$$

故只需证明 Newton 法从 $x_0>1$ 出发时的收敛性, 而不能直接引用**定理 8.5 (Newton 法的局部收敛性)**, 因为它只保证初值在根的充分小邻域内收敛.

$\blacksquare$

**第一步: 从第二项起不小于 $\sqrt{2}$**. 记 $g\left(x\right)=\dfrac{x}{2}+\dfrac{1}{x}$ ($x>0$). 由均值不等式,

$$
g\left(x\right)=\frac{x}{2}+\frac{1}{x}\ge2\sqrt{\frac{x}{2}\cdot\frac{1}{x}}=2\sqrt{\frac{1}{2}}=\sqrt{2},
$$

等号当且仅当 $\dfrac{x}{2}=\dfrac{1}{x}$, 即 $x=\sqrt{2}$ 时成立. 于是对 $n\ge1$ 恒有 $x_n\ge\sqrt{2}$.

$\blacksquare$

**第二步: 单调性**. 对 $x>0$,

$$
g\left(x\right)-x=\frac{1}{x}-\frac{x}{2}=\frac{2-x^{2}}{2x},
$$

故 $g\left(x\right)<x$ 当且仅当 $x>\sqrt{2}$, $g\left(x\right)=x$ 当且仅当 $x=\sqrt{2}$. 于是对 $n\ge1$, 若 $x_n>\sqrt{2}$ 则 $x_{n+1}<x_n$; 若 $x_n=\sqrt{2}$ 则序列从该步起停在 $\sqrt{2}$ (已是精确根).

$\blacksquare$

**第三步: 收敛**. 分两种情形. 若某个 $x_n=\sqrt{2}$, 结论已成. 否则对一切 $n\ge1$ 有 $x_n>\sqrt{2}$, 由第二步 $\left\{x_n\right\}_{n\ge1}$ 单调递减且以 $\sqrt{2}$ 为下界, 故收敛, 记极限为 $L\ge\sqrt{2}>0$. 在递推式两端取极限, 由 $g$ 在 $L$ 处连续得

$$
L=\frac{L}{2}+\frac{1}{L}\implies L^{2}=2\implies L=\sqrt{2},
$$

(另有一根 $-\sqrt{2}$ 与 $L>0$ 矛盾). 所以对任意 $x_0>1$ 序列收敛到 $\sqrt{2}$.

$\blacksquare$

**第四步: 二阶收敛**. 记 $e_n=x_n-\sqrt{2}$, 直接配方:

$$
e_{n+1}=g\left(x_n\right)-\sqrt{2}=\frac{x_n}{2}+\frac{1}{x_n}-\sqrt{2}=\frac{x_n^{2}-2\sqrt{2}x_n+2}{2x_n}=\frac{\left(x_n-\sqrt{2}\right)^{2}}{2x_n}=\frac{e_n^{2}}{2x_n}.
$$

由 $x_n\to\sqrt{2}$ 得 $\dfrac{1}{2x_n}\to\dfrac{1}{2\sqrt{2}}$, 于是

$$
\lim_{n\to\infty}\frac{\left|e_{n+1}\right|}{\left|e_n\right|^{2}}=\frac{1}{2\sqrt{2}}=0.353553\ne0,
$$

按**定义 8.2 (收敛阶)**, 序列为二阶 (平方) 收敛, 渐进误差常数为 $\dfrac{1}{2\sqrt{2}}$. 从迭代函数看, $g'\left(\sqrt{2}\right)=0$, 与**定理 8.4 (迭代序列收敛阶的判别)** 中"$\varphi'$ 在根处为零则升阶"一致.

$\blacksquare$

**数值验证**. 取 $x_0=1.5$:

| $n$ | $0$ | $1$ | $2$ | $3$ | $4$ |
|---|---|---|---|---|---|
| $x_n$ | $1.5$ | $1.4166667$ | $1.4142157$ | $1.4142135624$ | $1.4142135624$ |
| $\left|x_n-\sqrt{2}\right|$ | $8.58\times10^{-2}$ | $2.45\times10^{-3}$ | $2.12\times10^{-6}$ | $1.6\times10^{-12}$ | $0$ |

误差比 $\dfrac{2.45\times10^{-3}}{\left(8.58\times10^{-2}\right)^{2}}=0.333$, $\dfrac{2.12\times10^{-6}}{\left(2.45\times10^{-3}\right)^{2}}=0.353$, 逐步趋于 $0.353553$. 取 $x_0=10$ 时前几步为 $10,5.1,2.7460784,1.7371949,1.4442381,1.4145257$, 虽然开头几步下降得并不算快, 但一旦进入 $\sqrt{2}$ 附近, 每步有效数字就翻倍.

$\blacksquare$

## 习题 8-10 (用 Newton 法解三个方程)

用 Newton 法求解下列方程, 要求 $\left|x_{n+1}-x_n\right|<10^{-6}$: (1) $x-\ln x=2$; (2) $xe^{x}-1=0$; (3) $x+\sin x=1$.

### 解答 8-10

统一按**公式 (8.16) (Newton 迭代格式)** 计算. 各题在初值附近都满足**定理 8.5 (Newton 法的局部收敛性)** 的条件 (根为单根且 $f$ 二阶连续可微), 故收敛为二阶.

**(1) $x-\ln x=2$**. $f\left(x\right)=x-\ln x-2$, $f'\left(x\right)=1-\dfrac{1}{x}$, 迭代格式

$$
x_{n+1}=x_n-\frac{x_n-\ln x_n-2}{1-1/x_n}.
$$

取 $x_0=3$:

| $n$ | $0$ | $1$ | $2$ | $3$ |
|---|---|---|---|---|
| $x_n$ | $3.000000000$ | $3.147918433$ | $3.146193441$ | $3.146193221$ |
| $\left|x_n-x_{n-1}\right|$ | — | $1.48\times10^{-1}$ | $1.72\times10^{-3}$ | $2.2\times10^{-7}$ |

$n=3$ 时满足要求, 故 $x^{*}\approx3.146193221$. 校验 $f\left(x^{*}\right)=x^{*}-\ln x^{*}-2=2.6\times10^{-10}$.

**注**. 该方程其实有两个正根: $x-\ln x-2$ 在 $x=1$ 处取最小值 $-1<0$, 而 $f\left(0.1\right)=0.40>0$, $f\left(4\right)=0.61>0$, 故在 $\left(0.1,1\right)$ 与 $\left(3,4\right)$ 内各有唯一根. 上表得到的是大根. 若取 $x_0=0.2$, 得到小根

$$
0.2\to0.152359478\to0.158447821\to0.158594259\to0.158594340,
$$

即 $x^{*}\approx0.158594340$ (四步, $\left|x_4-x_3\right|=8.1\times10^{-8}$). 注意 $f'\left(x\right)=1-1/x$ 在 $x=1$ 处为零, 故初值不能取在 $1$ 附近, 否则 Newton 法失效或跳到另一侧.

$\blacksquare$

**(2) $xe^{x}-1=0$**. $f\left(x\right)=xe^{x}-1$, $f'\left(x\right)=e^{x}\left(1+x\right)$, 迭代格式

$$
x_{n+1}=x_n-\frac{x_ne^{x_n}-1}{e^{x_n}\left(1+x_n\right)}.
$$

取 $x_0=0.5$:

| $n$ | $0$ | $1$ | $2$ | $3$ | $4$ |
|---|---|---|---|---|---|
| $x_n$ | $0.500000000$ | $0.571020440$ | $0.567155569$ | $0.567143291$ | $0.567143290$ |
| $\left|x_n-x_{n-1}\right|$ | — | $7.10\times10^{-2}$ | $3.86\times10^{-3}$ | $1.23\times10^{-6}$ | $1\times10^{-9}$ |

$n=4$ 时 $\left|x_4-x_3\right|=1\times10^{-9}<10^{-6}$, 故 $x^{*}\approx0.567143290$ ($f\left(x^{*}\right)=-1.1\times10^{-9}$). 该根正是方程 $x=e^{-x}$ 的根, 也等于 $\dfrac{1}{e^{x^{*}}}=0.567143$.

$\blacksquare$

**(3) $x+\sin x=1$**. $f\left(x\right)=x+\sin x-1$, $f'\left(x\right)=1+\cos x$, 迭代格式

$$
x_{n+1}=x_n-\frac{x_n+\sin x_n-1}{1+\cos x_n}.
$$

取 $x_0=0.5$:

| $n$ | $0$ | $1$ | $2$ | $3$ |
|---|---|---|---|---|
| $x_n$ | $0.500000000$ | $0.510957953$ | $0.510973429$ | $0.510973429$ |
| $\left|x_n-x_{n-1}\right|$ | — | $1.096\times10^{-2}$ | $1.55\times10^{-5}$ | $4\times10^{-10}$ |

$n=3$ 时满足要求, 故 $x^{*}\approx0.510973429$ ($f\left(x^{*}\right)=-7.3\times10^{-10}$). 由于 $f'\left(x^{*}\right)=1+\cos0.510973=1.872$, 二阶收敛的渐进常数约 $\dfrac{\left|f''\left(x^{*}\right)\right|}{2f'\left(x^{*}\right)}=\dfrac{\sin0.510973}{2\times1.872}=0.130$.

$\blacksquare$

## 习题 8-12 (Newton 法求 $x^{3}-x-1=0$ 的根)

证明方程 $f\left(x\right)=x^{3}-x-1=0$ 在区间 $\left[1,2\right]$ 内仅有一个根. 取 $x_0=1.5$ 用 Newton 法求此根, 要求精确到 $5$ 位有效数字, 并说明其收敛阶数为 $2$.

### 解答 8-12

**唯一性**. $f\left(1\right)=1-1-1=-1<0$, $f\left(2\right)=8-2-1=5>0$, 由连续函数的介值定理, $f$ 在 $\left(1,2\right)$ 内至少有一个零点. 又 $f'\left(x\right)=3x^{2}-1\ge3\times1-1=2>0$ 对 $x\in\left[1,2\right]$ 成立, $f$ 在 $\left[1,2\right]$ 上严格单调增加, 故零点唯一.

$\blacksquare$

**迭代与计算**. $f'\left(x\right)=3x^{2}-1$, 按**公式 (8.16) (Newton 迭代格式)**,

$$
x_{n+1}=x_n-\frac{x_n^{3}-x_n-1}{3x_n^{2}-1}=\frac{2x_n^{3}+1}{3x_n^{2}-1}.
$$

取 $x_0=1.5$:

| $n$ | $x_n$ | $\left|x_n-x^{*}\right|$ |
|---|---|---|
| $0$ | $1.5000000000$ | $1.753\times10^{-1}$ |
| $1$ | $1.3478260870$ | $2.311\times10^{-2}$ |
| $2$ | $1.3252003990$ | $4.824\times10^{-4}$ |
| $3$ | $1.3247181740$ | $2.168\times10^{-7}$ |
| $4$ | $1.3247179572$ | $4.4\times10^{-14}$ |

$n=3$ 时 $\left|x_3-x^{*}\right|=2.2\times10^{-7}<\dfrac{1}{2}\times10^{-5}$, 已精确到 $5$ 位有效数字, 故

$$
x^{*}\approx1.324718,
$$

校验 $f\left(1.3247179572\right)=-1.9\times10^{-10}$.

$\blacksquare$

**收敛阶**. 相邻误差满足

$$
\frac{e_{n+1}}{e_n^{2}}:\quad0.752,\ 0.903,\ 0.932,\ 0.931\ \longrightarrow\ 0.9319,
$$

而理论上由 $f\left(x^{*}\right)=0$ 得

$$
e_{n+1}=\frac{f''\left(x^{*}\right)}{2f'\left(x^{*}\right)}e_n^{2}+O\left(e_n^{3}\right),\qquad \frac{f''\left(x^{*}\right)}{2f'\left(x^{*}\right)}=\frac{6\times1.324718}{2\times4.264633}=0.9319,
$$

两者吻合. 按**定义 8.2 (收敛阶)**, 第二个极限

$$
\lim_{n\to\infty}\frac{\left|e_{n+1}\right|}{\left|e_n\right|^{2}}=0.9319\ne0
$$

存在且非零, 故收敛阶恰为 $2$. 也可由**定理 8.5 (Newton 法的局部收敛性)** 直接断言"至少二阶", 再结合上式确认常数非零即恰为二阶. $f'\left(x^{*}\right)=4.264633\ne0$ 说明 $x^{*}$ 是单根, 这是二阶收敛的前提; 若是重根, 就会退化为线性收敛.

$\blacksquare$

## 习题 8-13 (重根时 Newton 法的收敛性)

若 $x^{*}$ 是方程 $f\left(x\right)=0$ 的 $r$ 重根, 即 $f\left(x\right)=\left(x-x^{*}\right)^{r}\varphi\left(x\right)$, 其中 $\varphi\left(x^{*}\right)\ne0$, 试证明: (1) Newton 法在 $x^{*}$ 邻近是线性收敛的; (2) **公式 (8.17) (重根情形的改进 Newton 格式)** 所产生的序列是二阶收敛的.

### 解答 8-13

**公共记号**. 记 $h\left(x\right)=\left(x-x^{*}\right)\varphi\left(x\right)$, 则 $f\left(x\right)=\left(x-x^{*}\right)^{r-1}h\left(x\right)$. 求导得

$$
f'\left(x\right)=\left(x-x^{*}\right)^{r-1}\left[r\varphi\left(x\right)+\left(x-x^{*}\right)\varphi'\left(x\right)\right].
$$

记 $D\left(x\right)=r\varphi\left(x\right)+\left(x-x^{*}\right)\varphi'\left(x\right)$, 则 $f'\left(x\right)=\left(x-x^{*}\right)^{r-1}D\left(x\right)$, 从而

$$
\frac{f\left(x\right)}{f'\left(x\right)}=\frac{h\left(x\right)}{D\left(x\right)}.
$$

在 $x^{*}$ 处, $h\left(x^{*}\right)=0$, $h'\left(x^{*}\right)=\varphi\left(x^{*}\right)$, $D\left(x^{*}\right)=r\varphi\left(x^{*}\right)$, $D'\left(x^{*}\right)=\left(r+1\right)\varphi'\left(x^{*}\right)$, $h''\left(x^{*}\right)=2\varphi'\left(x^{*}\right)$, $D''\left(x^{*}\right)=\left(r+2\right)\varphi''\left(x^{*}\right)$. 又

$$
\left(\frac{h}{D}\right)'\left(x^{*}\right)=\frac{h'D-hD'}{D^{2}}\left(x^{*}\right)=\frac{\varphi\left(x^{*}\right)\cdot r\varphi\left(x^{*}\right)-0}{\left(r\varphi\left(x^{*}\right)\right)^{2}}=\frac{1}{r}.
$$

$\blacksquare$

**(1) Newton 法是线性收敛**. Newton 法的迭代函数为

$$
g\left(x\right)=x-\frac{h\left(x\right)}{D\left(x\right)},
$$

故

$$
g'\left(x^{*}\right)=1-\frac{1}{r}=\frac{r-1}{r}.
$$

因为 $r\ge2$, 有 $0<\dfrac{r-1}{r}<1$, 由**定理 8.4 (迭代序列收敛阶的判别)** 的第二部分, $\left\{x_n\right\}$ 线性收敛, 且由

$$
\lim_{n\to\infty}\frac{\left|x_{n+1}-x^{*}\right|}{\left|x_n-x^{*}\right|}=\left|g'\left(x^{*}\right)\right|=\frac{r-1}{r}
$$

知渐进误差常数就是 $\dfrac{r-1}{r}$, 与**定义 8.2 (收敛阶)** 中 $r=1$ 的情形相符 (这里是"$1$ 阶", 即线性). $r$ 越大收敛越慢: $r=2$ 时为 $1/2$, $r=10$ 时达 $0.9$.

$\blacksquare$

**(2) 改进格式是二阶收敛**. 记改进格式的迭代函数

$$
G\left(x\right)=x-r\frac{h\left(x\right)}{D\left(x\right)}=x-r\frac{f\left(x\right)}{f'\left(x\right)}.
$$

由上一段的 $\left(\dfrac{h}{D}\right)'\left(x^{*}\right)=\dfrac{1}{r}$,

$$
G'\left(x^{*}\right)=1-r\cdot\frac{1}{r}=0.
$$

再算二阶导数. 对上式用商的二阶导数公式, 并注意 $\dfrac{h}{D}$ 在 $x^{*}$ 处为零而其一, 二阶导数不为零:

$$
\left(\frac{h}{D}\right)''\left(x^{*}\right)=\frac{h''}{D}\bigg|_{x^{*}}-2\frac{h'D'}{D^{2}}\bigg|_{x^{*}}-\frac{hD''}{D^{2}}\bigg|_{x^{*}}+2\frac{h\left(D'\right)^{2}}{D^{3}}\bigg|_{x^{*}}
$$

$$
=\frac{2\varphi\left(x^{*}\right)}{r\varphi\left(x^{*}\right)}-2\frac{\varphi\left(x^{*}\right)\left(r+1\right)\varphi'\left(x^{*}\right)}{\left(r\varphi\left(x^{*}\right)\right)^{2}}
$$

$$
=\frac{2}{r}-\frac{2\left(r+1\right)\varphi'\left(x^{*}\right)}{r^{2}\varphi\left(x^{*}\right)}=\frac{2\varphi'\left(x^{*}\right)}{r\varphi\left(x^{*}\right)}\left(1-\frac{r+1}{r}\right)=-\frac{2\varphi'\left(x^{*}\right)}{r^{2}\varphi\left(x^{*}\right)}.
$$

于是

$$
G''\left(x^{*}\right)=-r\left(\frac{h}{D}\right)''\left(x^{*}\right)=\frac{2\varphi'\left(x^{*}\right)}{\varphi\left(x^{*}\right)}.
$$

在 $x^{*}$ 处把 $G$ 作 Taylor 展开 (由 $G\left(x^{*}\right)=x^{*}$, $G'\left(x^{*}\right)=0$):

$$
x_{n+1}-x^{*}=G\left(x_n\right)-G\left(x^{*}\right)=\frac{G''\left(x^{*}\right)}{2}\left(x_n-x^{*}\right)^{2}+O\left(\left(x_n-x^{*}\right)^{3}\right),
$$

即

$$
\lim_{n\to\infty}\frac{\left|x_{n+1}-x^{*}\right|}{\left|x_n-x^{*}\right|^{2}}=\frac{\left|\varphi'\left(x^{*}\right)\right|}{\left|\varphi\left(x^{*}\right)\right|}\ne0,
$$

按**定义 8.2 (收敛阶)**, 改进格式为二阶收敛, 渐进误差常数为 $\dfrac{\left|\varphi'\left(x^{*}\right)\right|}{\left|\varphi\left(x^{*}\right)\right|}$. 这里用到 $\varphi\left(x^{*}\right)\ne0$ (保证 $\varphi$ 在根处不为零, 是"$r$ 重"定义的组成部分) 与 $\varphi'\left(x^{*}\right)\ne0$; 若 $\varphi'\left(x^{*}\right)=0$ 则阶数还会更高, 但此时公式给出的是三阶以上的收敛, 不影响"至少二阶"的结论.

$\blacksquare$

**说明**. 两道结论的对照很直观: Newton 法在根处的迭代函数斜率为 $\dfrac{r-1}{r}\ne0$, 每步只把误差乘上这个常数, 是线性收敛; 改进格式乘了因子 $r$, 恰好把这个 $1/r$ 抵消成 $0$, 于是升为二阶. 这也解释了**公式 (8.17) (重根情形的改进 Newton 格式)** 中为什么必须用重数 $r$ 而不是 $1$: 用 $1$ 就是普通 Newton, 用 $r$ 才是"对 $f$ 的 $r$ 次根做一次去重".

$\blacksquare$

## 习题 8-16(1) (用割线法解 $x-\ln x=2$)

试用割线法求解方程 $x-\ln x=2$, 要求 $\left|x_{n+1}-x_n\right|<10^{-5}$.

### 解答 8-16(1)

**格式与初值**. 按**公式 (8.19) (弦截法迭代格式)**,

$$
x_{n+1}=x_n-\frac{f\left(x_n\right)}{f\left(x_n\right)-f\left(x_{n-1}\right)}\left(x_n-x_{n-1}\right),\qquad f\left(x\right)=x-\ln x-2.
$$

由 $f\left(3\right)=-0.098612<0$, $f\left(4\right)=0.613706>0$, 取 $x_0=3$, $x_1=4$.

$\blacksquare$

**计算**.

| $n$ | $x_n$ | $f\left(x_n\right)$ | $\left|x_n-x_{n-1}\right|$ |
|---|---|---|---|
| $0$ | $3.000000000$ | $-0.098612$ | — |
| $1$ | $4.000000000$ | $0.613706$ | $1.000000$ |
| $2$ | $3.138438589$ | $-0.005287$ | $0.861561$ |
| $3$ | $3.145797196$ | $-0.000270$ | $0.007359$ |
| $4$ | $3.146193449$ | $0.000000156$ | $0.000396$ |
| $5$ | $3.146193221$ | $0$ | $0.000000228$ |

$n=5$ 时 $\left|x_5-x_4\right|=2.28\times10^{-7}<10^{-5}$, 故

$$
x^{*}\approx3.1461932,
$$

校验 $f\left(x^{*}\right)=2.6\times10^{-10}$, 与第 8-10(1) 题 Newton 法所得的大根 $3.146193221$ 完全一致.

$\blacksquare$

**收敛速度**. 由**定理 8.6 (弦截法的收敛阶)**, 弦截法在单根邻近的收敛阶为 $\dfrac{\sqrt{5}+1}{2}=1.618$. 数值核对: 记 $e_n=\left|x_n-x^{*}\right|$, 则 $e_2=7.755\times10^{-3}$, $e_3=3.960\times10^{-4}$, 比值为

$$
\frac{e_3}{e_2^{1.618}}=\frac{3.960\times10^{-4}}{\left(7.755\times10^{-3}\right)^{1.618}}=1.029,
$$

与阶 $1.618$ 相应的常数同一量级 (这一步的误差主要来自表中 $f$ 值的舍入). 最后一步 $e_4=2.28\times10^{-7}$ 已到表格精度, 不再作比值.

$\blacksquare$

**与 Newton 法的比较**. 同一方程, Newton 法从 $x_0=3$ 出发 $3$ 步就达到 $2.2\times10^{-7}$; 弦截法用了 $5$ 步才到 $2.3\times10^{-7}$. 但弦截法每步只需算一次 $f$ 值 (Newton 法每步要算 $f$ 与 $f'$ 各一次), 于是两者的"函数调用次数"是 $\left(3\times2\right)$ 对 $\left(1+4\right)$, 相近; 而弦截法的优点是**根本不需要导数**, 在 $f'$ 难以写出或计算昂贵时更实用. 另需注意弦截法是两步法, 必须给两个初值, 且两个初值要落在根附近 ($\left[3,4\right]$ 恰好把根夹住), 否则收敛性没有保证.

$\blacksquare$
