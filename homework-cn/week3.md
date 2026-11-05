# week3

> **定义 1.1 (绝对误差与误差限)**
> 
> 设 $x^{*}$ 为准确值 $x$ 的一个近似值, 称 $e\left(x^{*}\right)=x-x^{*}$ 为近似值 $x^{*}$ 的绝对误差, 简称误差. 若存在正数 $\varepsilon$ 使得 $\left|e\left(x^{*}\right)\right|=\left|x-x^{*}\right|\le\varepsilon$, 则称 $\varepsilon$ 为近似值 $x^{*}$ 的绝对误差限, 简称误差限.

> **定理 1.1 (相对误差限与有效数字的关系)**
> 
> 若 $x$ 的近似值 $x^{*}=\pm0.a_1a_2\cdots{a}_n\times10^{m}\left(a_1\ne0\right)$ 有 $n$ 位有效数字, 则 $\frac{1}{2a_1}\times10^{-n+1}$ 为其相对误差限. 反之, 若 $x^{*}$ 的相对误差限 $\varepsilon_r$ 满足 $\varepsilon_r\le\frac{1}{2}\times10^{-n}$, 则 $x^{*}$ 至少具有 $n$ 位有效数字.

> **定义 1.2 (相对误差与相对误差限)**
> 
> 设 $x^{*}$ 为准确值 $x$ 的近似值, 称 $e_r\left(x^{*}\right)=\frac{e\left(x^{*}\right)}{x^{*}}$ 为近似值 $x^{*}$ 的相对误差. 若存在正数 $\varepsilon_r$ 使得 $\left|e_r\left(x^{*}\right)\right|\le\varepsilon_r$, 则称 $\varepsilon_r$ 为 $x^{*}$ 的相对误差限.

> **定义 1.3 (有效数字)**
> 
> 如果近似值 $x^{*}$ 的规格化形式为 $x^{*}=\pm0.a_1a_2\cdots{a}_n\cdots\times10^{m}$, 其中 $m$ 为整数, $a_1\ne0$, 且 $\left|x-x^{*}\right|\le\frac{1}{2}\times10^{m-n}$, 则称近似值 $x^{*}$ 有 $n$ 位有效数字.

## 1-10

已知 $\sqrt{783}\approx27.983$ 有 5 位有效数字, 试求方程 $x^{2}-56x+1=0$ 的两个根, 使它们至少有 4 位有效数字.

### 解答 1-10

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

若直接按 $28-\sqrt{783}$ 计算 $x_2$, 则是两个相近的数相减, 由避免两个相近的数相减, 有效数字会严重丢失, 故不能直接这样算.

由韦达定理, 两根之积 $x_1x_2=1$, 故 $x_2=\frac{1}{x_1}$ (注意 $x_1\ne0$). 先算 $x_1$: 由**定义 1.3 (有效数字)**, $\sqrt{783}\approx27.983=0.27983\times10^{2}$ 有 5 位有效数字, 误差限为 $\frac{1}{2}\times10^{2-5}=\frac{1}{2}\times10^{-3}=0.0005$, 故

$$
\left|e\left(x_1\right)\right|=\left|e\left(\sqrt{783}\right)\right|\le0.0005\le\frac{1}{2}\times10^{2-4}=0.005,
$$

即 $x_1\approx55.983$ 至少有 4 位有效数字.

再由误差在基本运算中的传播, $x_2=\frac{1}{x_1}$, 商的相对误差近似等于分子分母相对误差之差, 故

$$
\left|e_r\left(x_2\right)\right|\approx\left|e_r\left(x_1\right)\right|\le\frac{0.0005}{55.983}\approx8.93\times10^{-6},
$$

而 $x_2=\frac{1}{55.983}\approx0.017862=0.17862\times10^{-1}$, 故

$$
\left|e\left(x_2\right)\right|\approx{x}_2\left|e_r\left(x_2\right)\right|\approx0.017862\times8.93\times10^{-6}\approx1.595\times10^{-7}\le\frac{1}{2}\times10^{-1-4}=\frac{1}{2}\times10^{-5},
$$

由**定义 1.3 (有效数字)**, $x_2\approx0.017862$ 至少有 4 位有效数字.

故所求两根为 $x_1\approx55.983$, $x_2\approx0.017862$, 均至少有 4 位有效数字. $\blacksquare$
