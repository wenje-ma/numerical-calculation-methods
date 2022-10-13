# 作业 1

> **定义 1.1** (绝对误差与误差限) <br>设 $x^{*}$ 为准确值 $x$ 的一个近似值, 称 $e\left(x^{*}\right)=x-x^{*}$ 为近似值 $x^{*}$ 的绝对误差, 简称误差. 一般情况下准确值难以求出, 从而也不能算出绝对误差 $e\left(x^{*}\right)$ 的准确值, 但可以根据测量工具或计算的情况估计出它的取值范围, 即估计出误差绝对值的一个上界 $\varepsilon$: $$\left|e\left(x^{*}\right)\right|=\left|x-x^{*}\right|\le\varepsilon.$$ 通常称 $\varepsilon$ 为近似值 $x^{*}$ 的绝对误差限, 简称误差限.

> **定义 1.2** (相对误差与相对误差限) <br>设 $x^{*}$ 为准确值 $x$ 的近似值, 称绝对误差与准确值之比为近似值 $x^{*}$ 的相对误差, 记为 $e_r\left(x^{*}\right)$, 即 $$e_r\left(x^{*}\right)=\frac{e\left(x^{*}\right)}{x}=\frac{x-x^{*}}{x}.$$ 由于在计算过程中准确值 $x$ 总是未知的, 故一般取相对误差为 $$e_r\left(x^{*}\right)=\frac{e\left(x^{*}\right)}{x^{*}}.$$ 同样, 相对误差也只能估计其上限. 如果存在正数 $\varepsilon_r$, 使得 $$\left|e_r\left(x^{*}\right)\right|=\left|\frac{e\left(x^{*}\right)}{x^{*}}\right|\le\varepsilon_r,$$ 则称 $\varepsilon_r$ 为 $x^{*}$ 的相对误差限.

> **定义 1.3** (有效数字) <br>如果近似值 $x^{*}$ 的误差限是 $\frac{1}{2}\times10^{-n}$, 则称 $x^{*}$ 准确到小数点后第 $n$ 位, 并从第一个非零数字到这一位的所有数字均称为有效数字. 一般地, 如果近似值 $x^{*}$ 的规格化形式为 $$x^{*}=\pm0.a_1a_2\cdots a_n\cdots\times10^{m},$$ 其中 $m$ 为整数, $a_1\ne0$, $a_i\left(i=1,2,\dots\right)$ 为 $0$ 到 $9$ 之间的整数, 且 $$\left|x-x^{*}\right|\le\frac{1}{2}\times10^{m-n},$$ 则称近似值 $x^{*}$ 有 $n$ 位有效数字.

> **定理 1.1** (相对误差限与有效数字的关系) <br>若 $x$ 的近似值 $x^{*}=\pm0.a_1a_2\cdots a_n\times10^{m}\left(a_1\ne0\right)$ 有 $n$ 位有效数字, 则 $\frac{1}{2a_1}\times10^{-n+1}$ 为其相对误差限. 反之, 若 $x^{*}$ 的相对误差限 $\varepsilon_r$ 满足 $\varepsilon_r\le\frac{1}{2}\times10^{-n}$, 则 $x^{*}$ 至少具有 $n$ 位有效数字.

> **误差传播** (基本运算中的误差估计) <br>设数值计算中求得的解与参量 $x_1,x_2,\dots,x_n$ 有关, 记为 $y=f\left(x_1,x_2,\dots,x_n\right)$, 参量 $x_i$ 的近似值为 $x_i^{*}$. 假定 $f$ 在点 $\left(x_1^{*},x_2^{*},\dots,x_n^{*}\right)$ 处可微, 则当参量误差较小时, 解的绝对误差与相对误差分别为 $$e\left(y^{*}\right)\approx\sum_{i=1}^n\frac{\partial f\left(x_1^{*},x_2^{*},\dots,x_n^{*}\right)}{\partial x_i}e\left(x_i^{*}\right),$$ $$e_r\left(y^{*}\right)\approx\sum_{i=1}^n\frac{\partial f\left(x_1^{*},x_2^{*},\dots,x_n^{*}\right)}{\partial x_i}\frac{x_i^{*}}{f\left(x_1^{*},x_2^{*},\dots,x_n^{*}\right)}e_r\left(x_i^{*}\right).$$ 特别地, 由上述公式可得和, 差, 积, 商之误差公式: $$\begin{cases}e\left(x_1\pm x_2\right)=e\left(x_1\right)\pm e\left(x_2\right),\\e_r\left(x_1\pm x_2\right)\approx\frac{x_1}{x_1\pm x_2}e_r\left(x_1\right)\pm\frac{x_2}{x_1\pm x_2}e_r\left(x_2\right),\end{cases}$$ $$\begin{cases}e\left(x_1x_2\right)\approx x_2e\left(x_1\right)+x_1e\left(x_2\right),\\e_r\left(x_1x_2\right)\approx e_r\left(x_1\right)+e_r\left(x_2\right),\end{cases}$$ $$\begin{cases}e\left(\frac{x_1}{x_2}\right)\approx\frac{1}{x_2}e\left(x_1\right)-\frac{x_1}{x_2^2}e\left(x_2\right),\\e_r\left(\frac{x_1}{x_2}\right)\approx e_r\left(x_1\right)-e_r\left(x_2\right).\end{cases}$$ 因此, 和, 差的误差限不超过各数的误差限之和, 积, 商的相对误差限不超过各数的相对误差限之和.

> **1.4 数值计算中应注意的问题** (避免两个相近的数相减) <br>由**误差传播**, 两数之差 $u=x-y$ 的相对误差为 $$e_r\left(u\right)\approx\frac{x}{x-y}e_r\left(x\right)-\frac{y}{x-y}e_r\left(y\right).$$ 当 $x$ 与 $y$ 很接近时, $\left|x-y\right|$ 很小, $u$ 的相对误差很大, 有效数字位数将严重丢失. 为避免这种情形出现, 常常改变计算公式.

### 习题一 (习题 1-3)

已知 $a=1.2031$, $b=0.978$ 是经过四舍五入后得到的近似值, 问 $a+b$, $a\times b$ 有几位有效数字? ### 解答 习题一

由**定义 1.1** (绝对误差与误差限) , $a=1.2031$ 有 5 位有效数字, 误差限为 $\frac{1}{2}\times10^{-4}$; $b=0.978$ 有 3 位有效数字, 误差限为 $\frac{1}{2}\times10^{-3}$.

先看和 $a+b=1.2031+0.978=2.1811$. 由**误差传播** (和, 差的误差限不超过各数的误差限之和) , $$
\left|e\left(a+b\right)\right|\le\left|e\left(a\right)\right|+\left|e\left(b\right)\right|\le\frac{1}{2}\times10^{-4}+\frac{1}{2}\times10^{-3}=0.00055.
$$

又 $2.1811=0.21811\times10^{1}$ ($m=1$) , 而 $\frac{1}{2}\times10^{1-4}=\frac{1}{2}\times10^{-3}=0.0005<0.00055\le\frac{1}{2}\times10^{1-3}=\frac{1}{2}\times10^{-2}=0.005$, 故由**定义 1.3** (有效数字) , $a+b$ 有 3 位有效数字.

再看积 $a\times b=1.2031\times0.978=1.17663$. 由**定义 1.2** (相对误差与相对误差限) 及**误差传播** (积的相对误差限不超过各数的相对误差限之和) , $$
\left|e_r\left(a\right)\right|\le\frac{\frac{1}{2}\times10^{-4}}{1.2031}\approx4.156\times10^{-5},\qquad\left|e_r\left(b\right)\right|\le\frac{\frac{1}{2}\times10^{-3}}{0.978}\approx5.113\times10^{-4},
$$

故

$$
\left|e_r\left(a\times b\right)\right|\le\left|e_r\left(a\right)\right|+\left|e_r\left(b\right)\right|\approx5.528\times10^{-4},
$$

$$
\left|e\left(a\times b\right)\right|\approx\left|a\times b\right|\cdot\left|e_r\left(a\times b\right)\right|\approx1.17663\times5.528\times10^{-4}\approx6.505\times10^{-4}.
$$

又 $1.17663=0.117663\times10^{1}$ ($m=1$) , 且 $\frac{1}{2}\times10^{-3}=0.0005<6.505\times10^{-4}\le\frac{1}{2}\times10^{-2}=0.005$, 故由**定义 1.3**, $a\times b$ 有 3 位有效数字. $\blacksquare$

### 习题二 (习题 1-7)

正方形的边长约 $100$ 厘米, 问测量边长时误差应多大, 才能保证面积的误差不超过 $1$ 厘米$^{2}$? ### 解答 习题二

设正方形边长为 $a\approx100$ 厘米, 面积为 $S=a^{2}$. 由**误差传播** (绝对误差估计) , 面积的绝对误差满足

$$
\left|e\left(S\right)\right|\approx\left|S'\left(a\right)\right|\cdot\left|e\left(a\right)\right|=2a\left|e\left(a\right)\right|=200\left|e\left(a\right)\right|.
$$

要保证面积的误差不超过 $1$ 厘米$^{2}$, 即 $\left|e\left(S\right)\right|\le1$, 只需

$$
200\left|e\left(a\right)\right|\le1\ \Rightarrow\ \left|e\left(a\right)\right|\le\frac{1}{200}=0.005.
$$

故测量边长时, 边长误差 (的误差限) 应不超过 $0.005$ 厘米. $\blacksquare$

### 习题三 (习题 1-9)

设 $s=\frac{1}{2}gt^{2}$, 假定 $g$ 是准确的, 而对 $t$ 的测量有 $\pm0.1$ 秒的误差, 试证当 $t$ 增大时, $s$ 的绝对误差增大而相对误差却减小.

### 解答 习题三

由**误差传播** (绝对误差估计) , $s=\frac{1}{2}gt^{2}$, 因 $g$ 准确即 $e\left(g\right)=0$, 故 $s$ 的绝对误差近似为

$$
\left|e\left(s\right)\right|\approx\left|\frac{\partial s}{\partial t}\right|\left|e\left(t\right)\right|=gt\left|e\left(t\right)\right|=0.1gt.
$$

当 $t$ 增大时, $0.1gt$ 增大, 故 $s$ 的绝对误差增大.

又由**误差传播** (相对误差 $e_r\left(y^{*}\right)\approx d\left(\ln f\right)$) , 对 $\ln s=\ln\frac{g}{2}+2\ln t$, 有

$$
\left|e_r\left(s\right)\right|\approx\left|2\frac{e\left(t\right)}{t}\right|=\frac{2\times0.1}{t}=\frac{0.2}{t}.
$$

当 $t$ 增大时, $\frac{0.2}{t}$ 减小, 故 $s$ 的相对误差减小. 综上, 当 $t$ 增大时, $s$ 的绝对误差增大而相对误差减小. $\blacksquare$

### 习题四 (习题 1-10)

已知 $\sqrt{783}\approx27.983$ 有 5 位有效数字, 试求方程 $x^{2}-56x+1=0$ 的两个根, 使它们至少有 4 位有效数字.

### 解答 习题四

方程 $x^{2}-56x+1=0$ 的判别式为

$$
\Delta=56^{2}-4=3136-4=3132=4\times783,
$$

故 $\sqrt{\Delta}=2\sqrt{783}\approx2\times27.983=55.966$. 由求根公式, 两根可写为

$$
x_1=\frac{56+\sqrt{\Delta}}{2}=28+\sqrt{783}\approx28+27.983=55.983,
$$

$$
x_2=\frac{56-\sqrt{\Delta}}{2}=28-\sqrt{783}\approx28-27.983=0.017.
$$

若直接按 $28-\sqrt{783}$ 计算 $x_2$, 则是两个相近的数相减, 由**1.4 数值计算中应注意的问题** (避免两个相近的数相减) , 有效数字会严重丢失, 故不能直接这样算.

由韦达定理, 两根之积 $x_1x_2=1$, 故 $x_2=\frac{1}{x_1}$ (注意 $x_1\ne0$) . 先算 $x_1$: 由**定义 1.3** (有效数字) , $\sqrt{783}\approx27.983=0.27983\times10^{2}$ 有 5 位有效数字, 误差限为 $\frac{1}{2}\times10^{2-5}=\frac{1}{2}\times10^{-3}=0.0005$, 故

$$
\left|e\left(x_1\right)\right|=\left|e\left(\sqrt{783}\right)\right|\le0.0005\le\frac{1}{2}\times10^{2-4}=0.005,
$$

即 $x_1\approx55.983$ 至少有 4 位有效数字.

再由**误差传播** (商的相对误差) , $x_2=\frac{1}{x_1}$, 有

$$
\left|e_r\left(x_2\right)\right|\approx\left|e_r\left(x_1\right)\right|\le\frac{0.0005}{55.983}\approx8.93\times10^{-6},
$$

而 $x_2=\frac{1}{55.983}\approx0.017862=0.17862\times10^{-1}$, 故

$$
\left|e\left(x_2\right)\right|\approx x_2\left|e_r\left(x_2\right)\right|\approx0.017862\times8.93\times10^{-6}\approx1.595\times10^{-7}\le\frac{1}{2}\times10^{-1-4}=\frac{1}{2}\times10^{-5},
$$

由**定义 1.3**, $x_2\approx0.017862$ 至少有 4 位有效数字.

故所求两根为 $x_1\approx55.983$, $x_2\approx0.017862$, 均至少有 4 位有效数字. $\blacksquare$

### 习题五 (习题 1-12)

试改变下列表达式, 使计算结果比较精确: (1) $\frac{1}{1+2x}-\frac{1-x}{1+x}$, $\left|x\right|\ll1$; (2) $\sqrt{x+\frac{1}{x}}-\sqrt{x-\frac{1}{x}}$, $\left|x\right|\gg1$; (3) $\frac{\tan x-\sin x}{x^{2}}$, $\left|x\right|\ll1$ 且 $x\ne0$. (仅要求第 (1) 小题) ### 解答 习题五

由**1.4 数值计算中应注意的问题** (避免两个相近的数相减) , 当 $\left|x\right|\ll1$ 时, $\frac{1}{1+2x}$ 与 $\frac{1-x}{1+x}$ 都接近 $1$, 直接相减会严重丢失有效数字. 对表达式通分合并: $$
\frac{1}{1+2x}-\frac{1-x}{1+x}=\frac{\left(1+x\right)-\left(1-x\right)\left(1+2x\right)}{\left(1+2x\right)\left(1+x\right)}.
$$

而

$$
\left(1-x\right)\left(1+2x\right)=1+2x-x-2x^{2}=1+x-2x^{2},
$$

$$
\left(1+x\right)-\left(1-x\right)\left(1+2x\right)=\left(1+x\right)-\left(1+x-2x^{2}\right)=2x^{2},
$$

故

$$
\frac{1}{1+2x}-\frac{1-x}{1+x}=\frac{2x^{2}}{\left(1+2x\right)\left(1+x\right)}.
$$

当 $\left|x\right|\ll1$ 时, $\left(1+2x\right)\left(1+x\right)$ 接近 $1$, 改写后的分母不涉及相近数相减, 分子 $2x^{2}$ 很小, 从而避免了有效数字的丢失. 故应改用 $\frac{2x^{2}}{\left(1+2x\right)\left(1+x\right)}$ 计算. $\blacksquare$
