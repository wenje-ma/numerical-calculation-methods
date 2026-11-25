# week9

> **定义 7.1 (求积公式的代数精确度)**
> 
> 若求积公式 $\int_a^bf\left(x\right)\mathrm{d}x\approx\sum_{k=0}^{n}A_kf\left(x_k\right)$ 对任意次数不高于 $m$ 的多项式均能准确成立, 而对 $m+1$ 次多项式不能准确成立, 则称该求积公式具有 $m$ 次代数精确度. (教材 $\S7.2$, p202)

> **公式 (7.23) (梯形公式)**
> 
> $\int_a^bf\left(x\right)\mathrm{d}x\approx\dfrac{b-a}{2}\left[f\left(a\right)+f\left(b\right)\right]$. (教材 $\S7.2$, p201)

> **公式 (7.24) (Simpson 公式)**
> 
> $\int_a^bf\left(x\right)\mathrm{d}x\approx\dfrac{b-a}{6}\left[f\left(a\right)+4f\left(\dfrac{a+b}{2}\right)+f\left(b\right)\right]$. (教材 $\S7.2$, p202)

> **定理 7.2 (梯形公式的截断误差)**
> 
> 若 $f\in{}C^{\left(2\right)}\left[a,b\right]$, 则 $R_1\left(f\right)=\int_a^bf\left(x\right)\mathrm{d}x-\dfrac{b-a}{2}\left[f\left(a\right)+f\left(b\right)\right]=-\dfrac{\left(b-a\right)^{3}}{12}f''\left(\xi\right)$, $\xi\in\left(a,b\right)$. (教材 $\S7.2$, p204)

> **定理 7.3 (Simpson 公式的截断误差)**
> 
> 若 $f\in{}C^{\left(4\right)}\left[a,b\right]$, 则 $R_2\left(f\right)=\int_a^bf\left(x\right)\mathrm{d}x-\dfrac{b-a}{6}\left[f\left(a\right)+4f\left(\dfrac{a+b}{2}\right)+f\left(b\right)\right]=-\dfrac{\left(b-a\right)^{5}}{2880}f^{\left(4\right)}\left(\xi\right)=-\dfrac{h^{5}}{90}f^{\left(4\right)}\left(\xi\right)$, $\xi\in\left(a,b\right)$, $h=\dfrac{b-a}{2}$. (教材 $\S7.2$, p204)

> **公式 (7.29) (复化梯形公式)**
> 
> 将 $\left[a,b\right]$ 等分为 $n$ 份, $h=\dfrac{b-a}{n}$, $x_k=a+kh$, 则 $\int_a^bf\left(x\right)\mathrm{d}x\approx{}T_n=h\left[\dfrac{1}{2}f\left(a\right)+\sum_{k=1}^{n-1}f\left(x_k\right)+\dfrac{1}{2}f\left(b\right)\right]$. (教材 $\S7.3$, p206)

> **公式 (7.30) (复化梯形公式的截断误差)**
> 
> 若 $f\in{}C^{\left(2\right)}\left[a,b\right]$, 则 $R_T\left(f\right)=\int_a^bf\left(x\right)\mathrm{d}x-T_n=-\dfrac{b-a}{12}h^{2}f''\left(\xi\right)$, $\xi\in\left(a,b\right)$. (教材 $\S7.3$, p207)

> **公式 (7.31) (复化 Simpson 公式)**
> 
> 将 $\left[a,b\right]$ 分成 $n=2m$ 等份, $h=\dfrac{b-a}{n}$, 则 $\int_a^bf\left(x\right)\mathrm{d}x\approx{}S_n=\dfrac{h}{3}\left[f\left(a\right)+f\left(b\right)+2\sum_{k=1}^{m-1}f\left(x_{2k}\right)+4\sum_{k=1}^{m}f\left(x_{2k-1}\right)\right]$. (教材 $\S7.3$, p207)

> **公式 (7.32) (复化 Simpson 公式的截断误差)**
> 
> 若 $f\in{}C^{\left(4\right)}\left[a,b\right]$, 则 $R_S\left(f\right)=\int_a^bf\left(x\right)\mathrm{d}x-S_n=-\dfrac{b-a}{180}h^{4}f^{\left(4\right)}\left(\xi\right)$, $\xi\in\left(a,b\right)$. (教材 $\S7.3$, p208)

## 习题 7-4(2) (梯形公式与 Simpson 公式: $e^{1/x}$)

分别用梯形公式和 Simpson 公式计算 $\displaystyle\int_{0.1}^{0.5}e^{\frac{1}{x}}\mathrm{d}x$ 的近似值并估计误差, 并说明误差估计是否可用.

### 解答 7-4(2)

**函数值**. $f\left(x\right)=e^{1/x}$, 则

$$
f\left(0.1\right)=e^{10}=22026.4658,\quad{}f\left(0.3\right)=e^{10/3}=28.0316,\quad{}f\left(0.5\right)=e^{2}=7.3891.
$$

**梯形公式**. 由**公式 (7.23) (梯形公式)**,

$$
T=\frac{0.5-0.1}{2}\left[f\left(0.1\right)+f\left(0.5\right)\right]=0.2\times22033.8549=4406.7710.
$$

**Simpson 公式**. 由**公式 (7.24) (Simpson 公式)**,

$$
S=\frac{0.4}{6}\left[f\left(0.1\right)+4f\left(0.3\right)+f\left(0.5\right)\right]=\frac{1}{15}\left(22026.4658+112.1264+7.3891\right)=1476.3988.
$$

$\blacksquare$

**真值**. 换元 $u=1/x$ 得 $I=\displaystyle\int_2^{10}\frac{e^{u}}{u^{2}}\mathrm{d}u$, 其原函数为 $\mathrm{Ei}\left(u\right)-\frac{e^{u}}{u}$, 故

$$
I=\left[\mathrm{Ei}\left(u\right)-\frac{e^{u}}{u}\right]_2^{10}=288.3227,
$$

(用高精度数值积分核对, 结果与此一致). 于是实际误差为

$$
T-I=4118.4483,\quad{}S-I=1188.0761,
$$

即梯形值是真值的 $15.3$ 倍, Simpson 值仍有 $5.1$ 倍.

$\blacksquare$

**误差估计**. 先算导数. $f'\left(x\right)=-\dfrac{e^{1/x}}{x^{2}}$, 逐次求导得

$$
f''\left(x\right)=e^{1/x}\left(\frac{1}{x^{4}}+\frac{2}{x^{3}}\right),\quad{}f^{\left(4\right)}\left(x\right)=e^{1/x}\left(\frac{1}{x^{8}}+\frac{12}{x^{7}}+\frac{36}{x^{6}}+\frac{24}{x^{5}}\right).
$$

两者在 $\left[0.1,0.5\right]$ 上都随 $x$ 减小而急剧增大, 故最大值在左端点:

$$
\left|f''\left(0.1\right)\right|=e^{10}\times12000=2.6432\times10^{8},\quad\left|f^{\left(4\right)}\left(0.1\right)\right|=e^{10}\times2.584\times10^{8}=5.6919\times10^{12}.
$$

由**定理 7.2 (梯形公式的截断误差)**,

$$
\left|R_1\right|\le\frac{\left(0.4\right)^{3}}{12}\times2.6432\times10^{8}=\frac{0.064}{12}\times2.6432\times10^{8}=1.410\times10^{6},
$$

由**定理 7.3 (Simpson 公式的截断误差)**,

$$
\left|R_2\right|\le\frac{\left(0.4\right)^{5}}{2880}\times5.6919\times10^{12}=\frac{0.01024}{2880}\times5.6919\times10^{12}=2.024\times10^{7}.
$$

$\blacksquare$

**结论与讨论**. 两个估计都远远超过实际误差 ($4118$ 与 $1188$), 甚至超过真值本身的量级, 因此这两个界在这道题里没有实用价值. 原因是被积函数在左端点附近极其陡峭, $f''$ 与 $f^{\left(4\right)}$ 在 $x=0.1$ 处分别达到 $10^{8}$ 与 $10^{12}$ 量级, 而误差公式取的是区间上的最大模; 实际上 $\left[0.1,0.2\right]$ 这一段贡献了积分的主要部分, 陡峭只发生在很窄的范围内, 所以真实误差远小于界. 这说明导数型误差界只适用于被积函数在区间上变化平缓的情形, 对边界层型函数应改用逐次分半或 Romberg 方法作事后估计. 另需注意 Simpson 的误差系数是 $1/2880$ 而梯形是 $1/12$, 但本题 Simpson 仍不精确, 因为 $h=0.2$ 相对于该函数的特征尺度仍然过大.

$\blacksquare$

## 习题 7-8 (求积公式的代数精确度)

求近似公式

$$
\int_0^1f\left(x\right)\mathrm{d}x\approx\frac{1}{3}\left[2f\left(\frac{1}{4}\right)-f\left(\frac{1}{2}\right)+2f\left(\frac{3}{4}\right)\right]
$$

的代数精确度.

### 解答 7-8

记 $Q\left(f\right)=\dfrac{1}{3}\left[2f\left(\dfrac{1}{4}\right)-f\left(\dfrac{1}{2}\right)+2f\left(\dfrac{3}{4}\right)\right]$, 由**定义 7.1 (求积公式的代数精确度)**, 只需逐一检验 $f\left(x\right)=x^{k}$ ($k=0,1,2,\ldots$), 直到首次失败.

$$
Q\left(1\right)=\frac{1}{3}\left(2-1+2\right)=1=\int_0^11\,\mathrm{d}x,
$$

$$
Q\left(x\right)=\frac{1}{3}\left[2\cdot\frac{1}{4}-\frac{1}{2}+2\cdot\frac{3}{4}\right]=\frac{1}{3}\left(\frac{1}{2}-\frac{1}{2}+\frac{3}{2}\right)=\frac{1}{2}=\int_0^1x\,\mathrm{d}x,
$$

$$
Q\left(x^{2}\right)=\frac{1}{3}\left[2\cdot\frac{1}{16}-\frac{1}{4}+2\cdot\frac{9}{16}\right]=\frac{1}{3}\left(\frac{1}{8}-\frac{1}{4}+\frac{9}{8}\right)=\frac{1}{3}\cdot1=\frac{1}{3}=\int_0^1x^{2}\,\mathrm{d}x,
$$

$$
Q\left(x^{3}\right)=\frac{1}{3}\left[2\cdot\frac{1}{64}-\frac{1}{8}+2\cdot\frac{27}{64}\right]=\frac{1}{3}\left(\frac{1}{32}-\frac{1}{8}+\frac{27}{32}\right)=\frac{1}{3}\cdot\frac{3}{4}=\frac{1}{4}=\int_0^1x^{3}\,\mathrm{d}x,
$$

$$
Q\left(x^{4}\right)=\frac{1}{3}\left[2\cdot\frac{1}{256}-\frac{1}{16}+2\cdot\frac{81}{256}\right]=\frac{1}{3}\left(\frac{1}{128}-\frac{1}{16}+\frac{81}{128}\right)=\frac{1}{3}\cdot\frac{37}{64}=\frac{37}{192}\approx0.192708\ne\frac{1}{5}.
$$

$\blacksquare$

**结论**. 前四次 ($k=0,1,2,3$) 成立, 第五次不成立, 故代数精确度为 $3$.

**附注**. 该公式只有三个节点, 却是三次代数精确度, 比同节点数的 Simpson 公式 (同样三次) 没有优势, 但它有一个刺眼的缺陷: 权重 $\dfrac{2}{3},-\dfrac{1}{3},\dfrac{2}{3}$ 中出现负数. 求积公式的系数不必都是正的, 但负系数会破坏数值稳定性: 只要 $f\left(\dfrac{1}{2}\right)$ 的误差为 $\delta$, 结果就引入 $-\delta/3$. 由此也可看出, 有 $n+1$ 个节点的一般求积公式的代数精确度上限是 $2n+1$ (Gauss 型), 而本题三节点只到 $3$ 次, 尚未达到上限.

$\blacksquare$

## 习题 7-10(1) (复化梯形与复化 Simpson: $x/\left(1+x^{2}\right)$)

分别用复化梯形公式和复化 Simpson 公式计算 $\displaystyle\int_0^1\frac{x}{1+x^{2}}\mathrm{d}x$ 的近似值, 取 $n=8$.

### 解答 7-10(1)

**准备**. $f\left(x\right)=\dfrac{x}{1+x^{2}}$, $h=\dfrac{1}{8}=0.125$, 节点 $x_k=0.125k$ ($k=0,1,\ldots,8$), 函数值为

| $k$ | $0$ | $1$ | $2$ | $3$ | $4$ | $5$ | $6$ | $7$ | $8$ |
|---|---|---|---|---|---|---|---|---|---|
| $x_k$ | $0$ | $0.125$ | $0.250$ | $0.375$ | $0.500$ | $0.625$ | $0.750$ | $0.875$ | $1$ |
| $f\left(x_k\right)$ | $0$ | $0.123077$ | $0.235294$ | $0.328767$ | $0.400000$ | $0.449438$ | $0.480000$ | $0.495575$ | $0.500000$ |

真值为 $\displaystyle\int_0^1\frac{x}{1+x^{2}}\mathrm{d}x=\frac{1}{2}\ln2=0.3465736$.

**复化梯形**. 由**公式 (7.29) (复化梯形公式)**,

$$
T_8=0.125\left[\frac{1}{2}\cdot0+\left(0.123077+0.235294+0.328767+0.400000+0.449438+0.480000+0.495575\right)+\frac{1}{2}\cdot0.500000\right]
$$

$$
=0.125\times\left(2.512151+0.250000\right)=0.125\times2.762151=0.345269.
$$

**复化 Simpson**. $n=8$ 即 $m=4$, 奇数项 $k=1,3,5,7$ 权重 $4$, 偶数项 $k=2,4,6$ 权重 $2$. 由**公式 (7.31) (复化 Simpson 公式)**,

$$
S_8=\frac{0.125}{3}\left[0+0.500000+2\left(0.235294+0.400000+0.480000\right)+4\left(0.123077+0.328767+0.449438+0.495575\right)\right]
$$

$$
=0.0416667\times\left(0.500000+2.230588+5.587428\right)=0.0416667\times8.318016=0.346584.
$$

$\blacksquare$

**误差与估计**. 实际误差 $T_8-I=-1.3046\times10^{-3}$, $S_8-I=1.05\times10^{-5}$.

由**公式 (7.30) (复化梯形公式的截断误差)**, $R_T=-\dfrac{1}{12}h^{2}f''\left(\xi\right)$; 而

$$
f'\left(x\right)=\frac{1-x^{2}}{\left(1+x^{2}\right)^{2}},\quad{}f''\left(x\right)=\frac{2x^{3}-6x}{\left(1+x^{2}\right)^{3}},
$$

在 $\left[0,1\right]$ 上 $\left|f''\right|$ 的最大值为 $1.4571$ (在 $x\approx0.47$ 处), 故

$$
\left|R_T\right|\le\frac{1}{12}\times0.015625\times1.4571=1.897\times10^{-3},
$$

确实覆盖了实际误差 $1.3046\times10^{-3}$.

由**公式 (7.32) (复化 Simpson 公式的截断误差)**, $\left|R_S\right|\le\dfrac{1}{180}h^{4}\left|f^{\left(4\right)}\right|_{\max}$, 而 $\left|f^{\left(4\right)}\right|$ 在 $\left[0,1\right]$ 上的最大值约 $19.49$, 故

$$
\left|R_S\right|\le\frac{1}{180}\times0.000244\times19.49=2.64\times10^{-5},
$$

覆盖了实际误差 $1.05\times10^{-5}$.

$\blacksquare$

**结论**. $T_8=0.345269$, $S_8=0.346584$. 复化 Simpson 的误差是复化梯形的 $\dfrac{1}{124}$, 与 $O\left(h^{2}\right)$ 对 $O\left(h^{4}\right)$ 的阶数差相符. 另外, 本题的被积函数满足 $f\left(x\right)=f\left(1/x\right)/x^{2}$ 类的对称性, 节点取值左右对称, 但复化梯形仍只达到 $10^{-3}$ 的精度, 说明提高阶数比加密节点更有效.

$\blacksquare$

## 习题 7-11 (按精度要求确定等分数)

若用复化梯形公式计算积分 $\displaystyle\int_0^1e^{-x^{2}}\mathrm{d}x$, 问积分区间要等分为多少份才能保证计算结果有四位有效数字 (假定计算过程无舍入误差)? 若用复化 Simpson 公式计算, 区间应等分为多少份?

### 解答 7-11

**真值与精度要求**. 该积分的值为 $\displaystyle\int_0^1e^{-x^{2}}\mathrm{d}x=0.7468241$. 四位有效数字即结果应形如 $0.7468$, 末位在 $10^{-4}$ 位, 故要求

$$
\left|R\right|\le\frac{1}{2}\times10^{-4}=5\times10^{-5}.
$$

$\blacksquare$

**导数估计**. $f\left(x\right)=e^{-x^{2}}$,

$$
f''\left(x\right)=\left(4x^{2}-2\right)e^{-x^{2}},\quad{}f^{\left(4\right)}\left(x\right)=\left(16x^{4}-48x^{2}+12\right)e^{-x^{2}}.
$$

在 $\left[0,1\right]$ 上 $\left|f''\right|$ 的最大值在 $x=0$ 处, 为 $2$; $\left|f^{\left(4\right)}\right|$ 的最大值也在 $x=0$ 处, 为 $12$ (在 $x=1$ 处为 $\left|16-48+12\right|e^{-1}=7.358<12$).

$\blacksquare$

**复化梯形**. 由**公式 (7.30) (复化梯形公式的截断误差)**,

$$
\left|R_T\right|\le\frac{b-a}{12}h^{2}\left|f''\right|_{\max}=\frac{1}{12}h^{2}\times2=\frac{h^{2}}{6}\le5\times10^{-5},
$$

$$
h\le\sqrt{3\times10^{-4}}=0.0173205,\quad{}n=\frac{1}{h}\ge57.735,
$$

故需 $n=58$ 等分 (此时 $h=1/58=0.017241$, $\dfrac{h^{2}}{6}=4.954\times10^{-5}$, 刚好满足).

$\blacksquare$

**复化 Simpson**. 由**公式 (7.32) (复化 Simpson 公式的截断误差)**,

$$
\left|R_S\right|\le\frac{b-a}{180}h^{4}\left|f^{\left(4\right)}\right|_{\max}=\frac{12h^{4}}{180}=\frac{h^{4}}{15}\le5\times10^{-5},
$$

$$
h^{4}\le7.5\times10^{-4},\quad{}h\le0.165488,\quad{}n\ge6.043,
$$

复化 Simpson 要求 $n$ 为偶数, 故取 $n=8$ (此时 $\dfrac{h^{4}}{15}=1.628\times10^{-5}$).

$\blacksquare$

**说明**. 两者相差 $58/8\approx7.25$ 倍. 粗略看, $h^{2}$ 与 $h^{4}$ 同时满足 $5\times10^{-5}$ 时步长之比约为 $\left(5\times10^{-5}\right)^{1/2-1/4}=\left(5\times10^{-5}\right)^{1/4}=0.084$, 折合成等分数之比即 $1/0.084\approx12$; 实际只有 $7.25$ 倍, 是因为两个误差公式的常数 $1/6$ 与 $1/15$ 相差 $2.5$ 倍. 无论怎样, 高阶层数在精度要求提高时更省节点这一结论不变. 若把"四位有效数字"按较宽的口径 $\left|R\right|\le0.5\times10^{-3}$ 理解, 则梯形需 $n\ge19$, Simpson 需 $n\ge4$; 本题按上一种更严的口径作答.

$\blacksquare$

## 习题 7-12 (由函数表计算积分并估计误差)

根据函数表

| $i$ | $0$ | $1$ | $2$ | $3$ | $4$ | $5$ | $6$ | $7$ | $8$ |
|---|---|---|---|---|---|---|---|---|---|
| $x_i$ | $0$ | $0.125$ | $0.250$ | $0.375$ | $0.500$ | $0.625$ | $0.750$ | $0.875$ | $1$ |
| $f\left(x_i\right)$ | $1$ | $0.997398$ | $0.989616$ | $0.976727$ | $0.958851$ | $0.936156$ | $0.908852$ | $0.877193$ | $0.841471$ |

计算积分 $I=\displaystyle\int_0^1f\left(x\right)\mathrm{d}x$ 的近似值, 并估计误差.

### 解答 7-12

**识别被积函数**. 表中数据满足 $f\left(0\right)=1$ 与 $f\left(x\right)=\dfrac{\sin{}x}{x}$ ($x>0$), 例如 $f\left(0.125\right)=\dfrac{\sin0.125}{0.125}=0.997398$, $f\left(1\right)=\sin1=0.841471$. 故 $I=\displaystyle\int_0^1\frac{\sin{}x}{x}\mathrm{d}x$, 其值为 $0.9460831$.

**复化梯形** ($n=8$, $h=0.125$). 由**公式 (7.29) (复化梯形公式)**,

$$
T_8=0.125\left[\frac{1}{2}\cdot1+\sum_{k=1}^{7}f\left(x_k\right)+\frac{1}{2}\cdot0.841471\right]=0.125\times\left(0.9207355+7.644208\right)=0.945691.
$$

**复化 Simpson** ($n=8$, $m=4$). 由**公式 (7.31) (复化 Simpson 公式)**,

$$
S_8=\frac{0.125}{3}\left[1+0.841471+2\left(0.989616+0.958851+0.908852\right)+4\left(0.997398+0.976727+0.936156+0.877193\right)\right]
$$

$$
=0.0416667\times\left(1.841471+5.714638+15.149896\right)=0.0416667\times22.706005=0.946084.
$$

$\blacksquare$

**误差估计 (靠表内数据) **. 因只有节点值, 只能用差商近似导数. 由**公式 (7.30) (复化梯形公式的截断误差)**, $R_T=-\dfrac{1}{12}h^{2}f''\left(\xi\right)$, 而 $f''$ 可用二阶差分估计:

$$
f''\left(x_i\right)\approx\frac{f_{i+1}-2f_i+f_{i-1}}{h^{2}},\quad{}i=1,\ldots,7,
$$

七个值依次为 $-0.3315$, $-0.3268$, $-0.3192$, $-0.3084$, $-0.2950$, $-0.2787$, $-0.2600$, 绝对值最大 $0.3315$ (与真值 $f''\left(0\right)=-\dfrac{1}{3}$ 相符). 于是

$$
\left|R_T\right|\le\frac{1}{12}\times0.015625\times0.3315=4.32\times10^{-4}.
$$

由**公式 (7.32) (复化 Simpson 公式的截断误差)**, $\left|R_S\right|\le\dfrac{1}{180}h^{4}\left|f^{\left(4\right)}\right|_{\max}$; 用四阶差分 $\dfrac{\Delta^{4}f_i}{h^{4}}$ 估计得 $0.1925$, $0.1966$, $0.1720$, $0.1802$, $0.1556$, 最大 $0.1966$ (真值 $f^{\left(4\right)}\left(0\right)=\dfrac{1}{5}=0.2$), 故

$$
\left|R_S\right|\le\frac{1}{180}\times0.000244\times0.1966=2.7\times10^{-7}.
$$

$\blacksquare$

**与真值核对**. $T_8-I=0.945691-0.9460831=-3.92\times10^{-4}$, 落在界 $4.32\times10^{-4}$ 之内; $S_8-I=0.946084-0.9460831=4.7\times10^{-7}$, 略超上面的 $2.7\times10^{-7}$. 后者并非公式失效, 而是表中数据只给六位小数: 每个 $f\left(x_i\right)$ 的舍入误差不超过 $0.5\times10^{-6}$, 在 $S_8$ 中被权重的绝对值之和放大为

$$
\frac{h}{3}\left(1+1+2\times3+4\times4\right)\times0.5\times10^{-6}=0.0416667\times23\times0.5\times10^{-6}=4.79\times10^{-7},
$$

正好与 $4.7\times10^{-7}$ 同量级, 说明误差的主源是数据舍入而非求积公式. 这也解释了为什么复化 Simpson 在这种"给定表值"的题目中往往已经达到表的精度极限, 再加密节点没有意义.

$\blacksquare$
