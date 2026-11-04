# week1

> **定义 1.1 (绝对误差与误差限)**
> 
> 设 $x^{*}$ 为准确值 $x$ 的一个近似值, 称 $e\left(x^{*}\right)=x-x^{*}$ 为近似值 $x^{*}$ 的绝对误差, 简称误差. 若存在正数 $\varepsilon$ 使得 $\left|e\left(x^{*}\right)\right|=\left|x-x^{*}\right|\le\varepsilon$, 则称 $\varepsilon$ 为近似值 $x^{*}$ 的绝对误差限, 简称误差限.

> **定理 1.1 (相对误差限与有效数字的关系)**
> 
> 若 $x$ 的近似值 $x^{*}=\pm0.a_1a_2\cdots a_n\times10^{m}\left(a_1\ne0\right)$ 有 $n$ 位有效数字, 则 $\frac{1}{2a_1}\times10^{-n+1}$ 为其相对误差限. 反之, 若 $x^{*}$ 的相对误差限 $\varepsilon_r$ 满足 $\varepsilon_r\le\frac{1}{2}\times10^{-n}$, 则 $x^{*}$ 至少具有 $n$ 位有效数字.

> **定义 1.2 (相对误差与相对误差限)**
> 
> 设 $x^{*}$ 为准确值 $x$ 的近似值, 称 $e_r\left(x^{*}\right)=\frac{e\left(x^{*}\right)}{x^{*}}$ 为近似值 $x^{*}$ 的相对误差. 若存在正数 $\varepsilon_r$ 使得 $\left|e_r\left(x^{*}\right)\right|\le\varepsilon_r$, 则称 $\varepsilon_r$ 为 $x^{*}$ 的相对误差限.

> **定义 1.3 (有效数字)**
> 
> 如果近似值 $x^{*}$ 的规格化形式为 $x^{*}=\pm0.a_1a_2\cdots a_n\cdots\times10^{m}$, 其中 $m$ 为整数, $a_1\ne0$, 且 $\left|x-x^{*}\right|\le\frac{1}{2}\times10^{m-n}$, 则称近似值 $x^{*}$ 有 $n$ 位有效数字.

## 1-3

已知 $a=1.2031$, $b=0.978$ 是经过四舍五入后得到的近似值, 问 $a+b$, $a\times b$ 有几位有效数字?

### 解答 1-3

由**定义 1.1 (绝对误差与误差限)** 及四舍五入的含义, $a=1.2031$ 有 5 位有效数字, 其误差限为 $\frac{1}{2}\times10^{-4}$; $b=0.978$ 有 3 位有效数字, 其误差限为 $\frac{1}{2}\times10^{-3}$.

先看和 $a+b=1.2031+0.978=2.1811$. 由误差在基本运算中的传播, 和的误差限不超过各数误差限之和, 故

$$
\left|e\left(a+b\right)\right|\le\left|e\left(a\right)\right|+\left|e\left(b\right)\right|\le\frac{1}{2}\times10^{-4}+\frac{1}{2}\times10^{-3}=0.00055.
$$

又 $2.1811=0.21811\times10^{1}$ ($m=1$), 而 $\frac{1}{2}\times10^{1-4}=\frac{1}{2}\times10^{-3}=0.0005< 0.00055\le\frac{1}{2}\times10^{1-3}=\frac{1}{2}\times10^{-2}=0.005$, 故由**定义 1.3 (有效数字)**, $a+b$ 有 3 位有效数字.

再看积 $a\times b=1.2031\times0.978=1.17663$. 由**定义 1.2 (相对误差与相对误差限)** 及误差在基本运算中的传播, 积的相对误差限不超过各数相对误差限之和, 故

$$
\left|e_r\left(a\right)\right|\le\frac{\frac{1}{2}\times10^{-4}}{1.2031}\approx4.156\times10^{-5},\quad\left|e_r\left(b\right)\right|\le\frac{\frac{1}{2}\times10^{-3}}{0.978}\approx5.113\times10^{-4},
$$

$$
\left|e_r\left(a\times b\right)\right|\le\left|e_r\left(a\right)\right|+\left|e_r\left(b\right)\right|\approx5.528\times10^{-4},
$$

$$
\left|e\left(a\times b\right)\right|\approx\left|a\times b\right|\cdot\left|e_r\left(a\times b\right)\right|\approx1.17663\times5.528\times10^{-4}\approx6.505\times10^{-4}.
$$

又 $1.17663=0.117663\times10^{1}$ ($m=1$), 且 $\frac{1}{2}\times10^{-3}=0.0005< 6.505\times10^{-4}\le\frac{1}{2}\times10^{-2}=0.005$, 故由**定义 1.3 (有效数字)**, $a\times b$ 有 3 位有效数字. $\blacksquare$
