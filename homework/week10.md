# week10

> **公式 (7.34) (梯形公式的逐次分半计算公式)**
> 
> 将 $\left[a,b\right]$ 分成 $2^{m}$ 等份, $h_m=\dfrac{b-a}{2^{m}}$, 则 $T_{2^{m}}=\dfrac{1}{2}T_{2^{m-1}}+h_m\sum_{k=1}^{2^{m-1}}f\left(a+\left(2k-1\right)h_m\right)$, $m=1,2,\ldots$. (教材 $\S7.3.3$, p210)

> **公式 (7.41) (Romberg 求积公式)**
> 
> 记 $T_0^{\left(k\right)}$ 为 $2^{k}$ 等分的复化梯形值, 令 $T_m^{\left(k\right)}=\dfrac{4^{m}T_{m-1}^{\left(k+1\right)}-T_{m-1}^{\left(k\right)}}{4^{m}-1}$ ($m=1,2,\ldots$; $k=0,1,2,\ldots$), 则 $R\left(f,T_m^{\left(k\right)}\right)=O\left(\left(\dfrac{b-a}{2^{k}}\right)^{2m+2}\right)$. (教材 $\S7.4.2$, p214)

> **定义 7.2 (Gauss 点与 Gauss 型求积公式)**
> 
> 若节点 $x_1,x_2,\ldots,x_n\in\left[a,b\right]$ 使带权求积公式 $\int_a^b\rho\left(x\right)f\left(x\right)\mathrm{d}x\approx\sum_{k=1}^{n}A_kf\left(x_k\right)$ 具有 $2n-1$ 次代数精确度, 则称 $\left\{x_k\right\}$ 为 Gauss 点, 该公式称为带权函数 $\rho\left(x\right)$ 的 Gauss 型求积公式. (教材 $\S7.5.1$, p218)

> **定理 7.4 (节点为 Gauss 点的充要条件)**
> 
> 求积公式 $\int_a^b\rho\left(x\right)f\left(x\right)\mathrm{d}x\approx\sum_{k=1}^{n}A_kf\left(x_k\right)$ 的节点是 Gauss 点的充要条件是 $\omega_n\left(x\right)=\prod_{k=1}^{n}\left(x-x_k\right)$ 与任意次数不超过 $n-1$ 的多项式 $p\left(x\right)$ 在 $\left[a,b\right]$ 上关于权函数 $\rho\left(x\right)$ 正交, 即 $\int_a^b\rho\left(x\right)p\left(x\right)\omega_n\left(x\right)\mathrm{d}x=0$. (教材 $\S7.5.1$, p220)

> **公式 (7.50) (Gauss 型求积公式的求积系数)**
> 
> $A_k=\displaystyle\int_a^b\rho\left(x\right)\frac{\omega_n\left(x\right)}{\left(x-x_k\right)\omega_n'\left(x_k\right)}\mathrm{d}x$, $k=1,2,\ldots,n$. (教材 $\S7.5.1$, p221)

## 习题 7-13(1) (梯形公式的逐次分半算法)

用梯形公式的逐次分半算法计算积分 $\displaystyle\int_0^{\pi}\frac{\mathrm{d}x}{x+\cos x}$, 要求误差不超过 $\varepsilon=3\times10^{-4}$.

### 解答 7-13(1)

**准备**. $f\left(x\right)=\dfrac{1}{x+\cos x}$, $a=0$, $b=\pi$. 在 $\left[0,\pi\right]$ 上 $x+\cos x$ 单调递增 (其导数为 $1-\sin x\ge0$), 取值从 $1$ 增至 $\pi-1=2.141593$, 故

$$
f\left(0\right)=1,\qquad f\left(\pi\right)=\frac{1}{\pi-1}=0.466943,
$$

被积函数在区间上光滑无奇点.

**递推**. 由**公式 (7.34) (梯形公式的逐次分半计算公式)**, 每次只需在已有节点中点处补算函数值, 而不必重算旧节点:

$$
T_1=\frac{b-a}{2}\left[f\left(a\right)+f\left(b\right)\right]=\frac{\pi}{2}\left(1+0.466943\right)=2.30426743,
$$

$$
T_2=\frac{1}{2}T_1+h_1f\left(\frac{\pi}{2}\right),\qquad h_1=\frac{b-a}{2}=\frac{\pi}{2},\quad f\left(\frac{\pi}{2}\right)=\frac{1}{\pi/2}=\frac{2}{\pi},
$$

$$
T_2=\frac{1}{2}\times2.30426743+\frac{\pi}{2}\times\frac{2}{\pi}=1.15213372+1=2.15213372.
$$

$\blacksquare$

**逐次分半表**. 按同一递推继续计算, 得

| $2^{m}$ | $h_m$ | $T_{2^{m}}$ | $\left|T_{2^{m}}-T_{2^{m-1}}\right|$ | $\left|T_{2^{m}}-I\right|$ |
|---|---|---|---|---|
| $1$ | $3.141593$ | $2.30426743$ | — | $2.612\times10^{-1}$ |
| $2$ | $1.570796$ | $2.15213372$ | $1.521\times10^{-1}$ | $1.091\times10^{-1}$ |
| $4$ | $0.785398$ | $2.07855725$ | $7.358\times10^{-2}$ | $3.549\times10^{-2}$ |
| $8$ | $0.392699$ | $2.05274729$ | $2.581\times10^{-2}$ | $9.684\times10^{-3}$ |
| $16$ | $0.196350$ | $2.04555069$ | $7.197\times10^{-3}$ | $2.488\times10^{-3}$ |
| $32$ | $0.098175$ | $2.04368958$ | $1.861\times10^{-3}$ | $6.265\times10^{-4}$ |
| $64$ | $0.049087$ | $2.04322000$ | $4.696\times10^{-4}$ | $1.569\times10^{-4}$ |
| $128$ | $0.024544$ | $2.04310233$ | $1.177\times10^{-4}$ | $3.925\times10^{-5}$ |

其中 $I=\displaystyle\int_0^{\pi}\frac{\mathrm{d}x}{x+\cos x}=2.04306309$ (由高精度复化梯形与 Romberg 校核).

$\blacksquare$

**停步判定**. 教材给出的停步准则是 $\left|T_{2^{m}}-T_{2^{m-1}}\right|<3\varepsilon$, 理由是由 $T_{2^{m}}-T_{2^{m-1}}\approx3R\left(f,T_{2^{m}}\right)$ 知后一次误差约为前后两次差的三分之一. 本题 $3\varepsilon=9\times10^{-4}$, 而

$$
\left|T_{64}-T_{32}\right|=4.696\times10^{-4}<9\times10^{-4},
$$

故应在 $2^{m}=64$ 处停止, 取

$$
I\approx T_{64}=2.04322000,
$$

其实际误差 $1.569\times10^{-4}<\varepsilon=3\times10^{-4}$, 满足要求.

$\blacksquare$

**附注**. 若把停步准则取作更保守的 $\left|T_{2^{m}}-T_{2^{m-1}}\right|<\varepsilon=3\times10^{-4}$, 则 $T_{64}$ 尚不满足 ($4.696\times10^{-4}>3\times10^{-4}$), 需继续分半到 $2^{m}=128$: $\left|T_{128}-T_{64}\right|=1.177\times10^{-4}<\varepsilon$, 得 $T_{128}=2.04310233$, 误差 $3.9\times10^{-5}$. 两种口径都给出满足精度的结果, 前者省一半函数值. 另可用 Richardson 外推校核: $T_{128}+\dfrac{T_{128}-T_{64}}{3}=2.04310233-3.922\times10^{-5}=2.04306311$, 与真值 $2.04306309$ 只差 $2\times10^{-8}$, 说明阶梯形的误差主要就是 $O\left(h^{2}\right)$ 主项, 事后估计很准.

$\blacksquare$

## 习题 7-15 (Romberg 方法)

用 Romberg 方法计算积分 $I=\displaystyle\int_0^1e^{-x^{2}}\mathrm{d}x$, 要求误差不超过 $\varepsilon=10^{-4}$.

### 解答 7-15

**梯形值序列**. $f\left(x\right)=e^{-x^{2}}$, 由**公式 (7.34) (梯形公式的逐次分半计算公式)** 得

$$
T_0^{\left(0\right)}=0.68393972,\quad T_0^{\left(1\right)}=0.73137025,\quad T_0^{\left(2\right)}=0.74298410,
$$

$$
T_0^{\left(3\right)}=0.74586561,\quad T_0^{\left(4\right)}=0.74658460.
$$

其中 $T_0^{\left(k\right)}$ 为 $2^{k}$ 等分的复化梯形值, 例如 $T_0^{\left(1\right)}=\dfrac{1}{2}\left[T_0^{\left(0\right)}+f\left(0.5\right)\right]=\dfrac{1}{2}\left(0.68393972+0.77880078\right)$.

**外推**. 按**公式 (7.41) (Romberg 求积公式)** 逐列外推:

$$
T_1^{\left(k\right)}=\frac{4T_0^{\left(k+1\right)}-T_0^{\left(k\right)}}{3},\qquad T_2^{\left(k\right)}=\frac{16T_1^{\left(k+1\right)}-T_1^{\left(k\right)}}{15},\qquad T_3^{\left(k\right)}=\frac{64T_2^{\left(k+1\right)}-T_2^{\left(k\right)}}{63}.
$$

$\blacksquare$

**Romberg 表** (按行依次计算)

| $k$ | $T_0^{\left(k\right)}$ (梯形) | $T_1^{\left(k\right)}$ (Simpson) | $T_2^{\left(k\right)}$ (Cotes) | $T_3^{\left(k\right)}$ (Romberg) |
|---|---|---|---|---|
| $0$ | $0.68393972$ | $0.74718043$ | $0.74683371$ | $0.74682402$ |
| $1$ | $0.73137025$ | $0.74685538$ | $0.74682417$ | $0.74682413$ |
| $2$ | $0.74298410$ | $0.74682612$ | $0.74682413$ | |
| $3$ | $0.74586561$ | $0.74682426$ | | |
| $4$ | $0.74658460$ | | | |

$\blacksquare$

**停步判定**. 判据为 $\left|T_m^{\left(0\right)}-T_{m-1}^{\left(0\right)}\right|<\varepsilon$. 本题

$$
\left|T_3^{\left(0\right)}-T_2^{\left(0\right)}\right|=\left|0.74682402-0.74683371\right|=9.69\times10^{-6}<10^{-4},
$$

故停止, 取 $I\approx T_3^{\left(0\right)}=0.74682402$.

$\blacksquare$

**核对与比较**. 真值为 $I=0.74682413$, 实际误差 $1.1\times10^{-7}$, 远小于 $\varepsilon$. 达到这一精度只用到 $T_0^{\left(0\right)}$ 至 $T_0^{\left(4\right)}$, 即 $1+1+2+4+8=16$ 个新增函数值共 $17$ 个点; 而纯复化梯形 $T_0^{\left(4\right)}=0.74658460$ 的误差是 $2.4\times10^{-4}$, 还不满足要求, 需要约 $n\approx290$ 才能达到 $10^{-4}$. 可见外推的价值在于不增加节点, 只靠误差展开的结构把 $O\left(h^{2}\right)$ 逐级消成 $O\left(h^{8}\right)$.

$\blacksquare$

## 习题 7-16(2) (权系数给定, 确定节点)

确定积分公式 $\displaystyle\int_0^2f\left(x\right)\mathrm{d}x\approx f\left(x_1\right)+f\left(x_2\right)$ 中的节点 $x_1,x_2$, 使公式具有尽可能高的代数精确度, 并指出该精确度.

### 解答 7-16(2)

**自由度分析**. 公式的权系数已给定为 $1$ 和 $1$, 只剩两个未知量 $x_1,x_2$, 故最多能精确满足两个独立条件. 先看 $f\equiv1$:

$$
1+1=2=\int_0^2 1\,\mathrm{d}x,
$$

自动成立, 这一条件不消耗自由度.

**确定节点**. 用 $f\left(x\right)=x$ 与 $f\left(x\right)=x^{2}$ 作条件:

$$
x_1+x_2=\int_0^2x\,\mathrm{d}x=2,
$$

$$
x_1^{2}+x_2^{2}=\int_0^2x^{2}\,\mathrm{d}x=\frac{8}{3}.
$$

由第一式平方得 $x_1^{2}+2x_1x_2+x_2^{2}=4$, 与第二式相减得 $2x_1x_2=4-\dfrac{8}{3}=\dfrac{4}{3}$, 即 $x_1x_2=\dfrac{2}{3}$. 于是 $x_1,x_2$ 是方程

$$
t^{2}-2t+\frac{2}{3}=0
$$

的两根, 解得 $t=1\pm\dfrac{\sqrt{3}}{3}$, 即

$$
x_1=1-\frac{\sqrt{3}}{3}=0.422650,\qquad x_2=1+\frac{\sqrt{3}}{3}=1.577350.
$$

$\blacksquare$

**验证三次与四次**. 由 $x_1+x_2=2$, $x_1x_2=\dfrac{2}{3}$,

$$
x_1^{3}+x_2^{3}=\left(x_1+x_2\right)^{3}-3x_1x_2\left(x_1+x_2\right)=8-3\times\frac{2}{3}\times2=4=\int_0^2x^{3}\,\mathrm{d}x,
$$

$$
x_1^{4}+x_2^{4}=\left(x_1^{2}+x_2^{2}\right)^{2}-2\left(x_1x_2\right)^{2}=\frac{64}{9}-2\times\frac{4}{9}=\frac{56}{9}=6.2222\ne\frac{32}{5}=6.4=\int_0^2x^{4}\,\mathrm{d}x.
$$

$\blacksquare$

**结论**. 公式对 $1,x,x^{2},x^{3}$ 精确成立, 对 $x^{4}$ 不成立, 故代数精确度为 $3$. 注意求得的节点可写成 $x_{1,2}=1\mp\dfrac{1}{\sqrt{3}}$, 正是标准二点 Gauss-Legendre 公式在 $\left[0,2\right]$ 上的节点 (把 $\left[-1,1\right]$ 上的 $\pm\dfrac{1}{\sqrt{3}}$ 平移 $1$), 而两个权系数在仿射变换下被乘以 $\dfrac{b-a}{2}=1$, 恰好仍是 $1$. 所以这组给定的权系数 $1,1$ 并非随意指定, 它正是二点 Gauss 公式的权, 公式确为带权 $\rho\equiv1$ 的 Gauss 型求积公式, 达到了**定义 7.2 (Gauss 点与 Gauss 型求积公式)** 中 $2n-1=3$ 的上界. 若题目给定的权系数不是 $1,1$ (例如 $1,2$), 则两条件变为 $x_1+2x_2$ 与 $x_1^{2}+2x_2^{2}$ 的方程组, 解出的节点就一般不再具有 Gauss 性.

$\blacksquare$

## 习题 7-16(3) (三个参数, 确定节点与权)

确定积分公式 $\displaystyle\int_{-1}^{1}f\left(x\right)\mathrm{d}x\approx A_1f\left(x_1\right)+A_2f\left(0\right)+f\left(1\right)$ 中的 $A_1,A_2,x_1$, 使公式具有尽可能高的代数精确度.

### 解答 7-16(3)

**自由度分析**. 未知量为 $A_1$, $A_2$, $x_1$ 三个, 故最多精确满足三个条件. 注意 $\int_{-1}^{1}x\,\mathrm{d}x=0$ 与 $\int_{-1}^{1}x^{3}\,\mathrm{d}x=0$ 这类零矩条件会自然简化方程组.

**建立方程**. 依次取 $f=1,x,x^{2}$:

$$
A_1+A_2+1=\int_{-1}^{1}1\,\mathrm{d}x=2,
$$

$$
A_1x_1+0+1=\int_{-1}^{1}x\,\mathrm{d}x=0,
$$

$$
A_1x_1^{2}+0+1=\int_{-1}^{1}x^{2}\,\mathrm{d}x=\frac{2}{3}.
$$

$\blacksquare$

**求解**. 由第二式 $A_1x_1=-1$; 第一式给 $A_1+A_2=1$. 把 $x_1=-\dfrac{1}{A_1}$ 代入第三式:

$$
A_1\cdot\frac{1}{A_1^{2}}=\frac{1}{A_1}=\frac{2}{3}-1=-\frac{1}{3},
$$

故 $A_1=-3$, 从而 $x_1=-\dfrac{1}{-3}=\dfrac{1}{3}$, $A_2=1-A_1=4$. 即

$$
\int_{-1}^{1}f\left(x\right)\mathrm{d}x\approx-3f\left(\frac{1}{3}\right)+4f\left(0\right)+f\left(1\right).
$$

$\blacksquare$

**验证更高次**. 对 $f\left(x\right)=x^{3}$:

$$
-3\times\frac{1}{27}+0+1=\frac{8}{9}\ne0=\int_{-1}^{1}x^{3}\,\mathrm{d}x,
$$

故对 $x^{3}$ 已不成立, 代数精确度为 $2$. 由于只有 $3$ 个未知量, 无法再提高.

$\blacksquare$

**附注**. 该公式有三个节点, 精确度却只有 $2$, 远低于三节点可达的 $5$ 次. 原因是节点 $0$ 与 $1$ 被固定, 真正自由的只有 $x_1$ 一个, 而权 $A_1,A_2$ 虽自由却随 $x_1$ 一起被前三阶矩锁死. 更重要的是 $A_1=-3$ 为负且绝对值很大, 稳定性差: 若 $f\left(\dfrac{1}{3}\right)$ 有 $\delta$ 的误差, 结果就被放大 $3\delta$; 且 $f\left(0\right)$ 的系数 $4>2$ 也意味着权系数之和虽等于区间长度 $2$, 但分布极不均匀. 这说明"待定系数法"虽然总能凑出高精确度, 却不保证数值稳定, 实际使用必须是 Gauss 型 (权系数全正).

$\blacksquare$

## 习题 7-18 (带权 $\sqrt{x}$ 的 Gauss 型公式)

试确定 $x_1,x_2,A_1,A_2$, 使求积公式

$$
\int_0^1\sqrt{x}\,f\left(x\right)\mathrm{d}x\approx A_1f\left(x_1\right)+A_2f\left(x_2\right)
$$

成为 Gauss 型求积公式.

### 解答 7-18

**权函数的矩**. $\rho\left(x\right)=\sqrt{x}$, $\left[a,b\right]=\left[0,1\right]$, 各阶矩为

$$
\mu_l=\int_0^1x^{l+1/2}\,\mathrm{d}x=\frac{1}{l+3/2}=\frac{2}{2l+3}:\qquad \mu_0=\frac{2}{3},\quad \mu_1=\frac{2}{5},\quad \mu_2=\frac{2}{7},\quad \mu_3=\frac{2}{9}.
$$

**求 Gauss 点**. 由**定理 7.4 (节点为 Gauss 点的充要条件)**, 二节点情形需 $\omega_2\left(x\right)=x^{2}+px+q$ 与 $1$ 及 $x$ 都关于 $\rho$ 正交:

$$
\mu_2+p\mu_1+q\mu_0=0,\qquad \mu_3+p\mu_2+q\mu_1=0,
$$

即

$$
\frac{2}{7}+\frac{2p}{5}+\frac{2q}{3}=0,\qquad \frac{2}{9}+\frac{2p}{7}+\frac{2q}{5}=0.
$$

消去分母 (第一式乘 $105$, 第二式乘 $315$):

$$
30+42p+70q=0,\qquad 70+90p+126q=0.
$$

由第一式 $p=\dfrac{-30-70q}{42}$, 代入第二式得 $90\cdot\dfrac{-30-70q}{42}+126q=-70$, 即 $-64.2857-150q+126q=-70$, 故 $q=\dfrac{5}{21}$, 回代得 $p=-\dfrac{10}{9}$. 于是

$$
\omega_2\left(x\right)=x^{2}-\frac{10}{9}x+\frac{5}{21},
$$

其判别式 $\dfrac{100}{81}-\dfrac{20}{21}=\dfrac{100\times21-20\times81}{1701}=\dfrac{2100-1620}{1701}=\dfrac{480}{1701}>0$, 两根为

$$
x_{1,2}=\frac{1}{2}\left(\frac{10}{9}\mp\sqrt{\frac{480}{1701}}\right)=0.2899492,\ 0.8211619,
$$

均在 $\left(0,1\right)$ 内, 故确为 Gauss 点.

$\blacksquare$

**求权系数**. 由**公式 (7.50) (Gauss 型求积公式的求积系数)**, 或用更省事的线性插值基函数法: $A_1$ 是 $\omega_2$ 在 $x_1$ 处的插值基函数的权积分, 即

$$
A_1=\int_0^1\sqrt{x}\,\frac{x-x_2}{x_1-x_2}\mathrm{d}x=\frac{\mu_1-x_2\mu_0}{x_1-x_2},\qquad A_2=\mu_0-A_1.
$$

代入数值: $\mu_0=\dfrac{2}{3}=0.6666667$, $\mu_1=\dfrac{2}{5}=0.4$,

$$
A_1=\frac{0.4-0.8211619\times0.6666667}{0.2899492-0.8211619}=\frac{0.4-0.5474413}{-0.5312127}=0.2775560,
$$

$$
A_2=0.6666667-0.2775560=0.3891107.
$$

$\blacksquare$

**校验**. 权系数之和 $0.2775560+0.3891107=0.6666667=\mu_0$, 一阶矩 $0.2775560\times0.2899492+0.3891107\times0.8211619=0.4000000=\mu_1$, 二阶矩

$$
0.2775560\times0.2899492^{2}+0.3891107\times0.8211619^{2}=0.2857143=\frac{2}{7}=\mu_2,
$$

三阶矩 $=0.2222222=\dfrac{2}{9}=\mu_3$, 四阶矩 $=0.1788864\ne\dfrac{2}{11}=0.1818182$. 故公式对 $0$ 至 $3$ 次多项式精确, 对 $4$ 次不精确, 代数精确度 $2n-1=3$, 符合**定义 7.2 (Gauss 点与 Gauss 型求积公式)**.

$\blacksquare$

**结论**. 所求公式为

$$
\int_0^1\sqrt{x}\,f\left(x\right)\mathrm{d}x\approx0.2775560f\left(0.2899492\right)+0.3891107f\left(0.8211619\right).
$$

权系数都为正, 数值稳定; 两个节点偏向区间右端, 这是因为权函数 $\sqrt{x}$ 在左端很小, 左端的贡献本来就弱, 节点自然向权重大处集中.

$\blacksquare$
