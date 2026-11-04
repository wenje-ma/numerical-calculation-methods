# week3

> **Definition 1.1 (Absolute Error and Error Bound)**
> 
> Let $x^{*}$ be an approximation to the exact value $x$. The quantity $e\left(x^{*}\right)=x-x^{*}$ is called the absolute error of $x^{*}$, or error for short. If there exists a positive number $\varepsilon$ such that $\left|e\left(x^{*}\right)\right|=\left|x-x^{*}\right|\le\varepsilon$, then $\varepsilon$ is called the absolute error bound of $x^{*}$, or error bound for short.

> **Theorem 1.1 (Relation Between the Relative Error Bound and Significant Digits)**
> 
> If the approximation $x^{*}=\pm0.a_1a_2\cdots a_n\times10^{m}\left(a_1\ne0\right)$ of $x$ has $n$ significant digits, then $\frac{1}{2a_1}\times10^{-n+1}$ is its relative error bound. Conversely, if the relative error bound $\varepsilon_r$ of $x^{*}$ satisfies $\varepsilon_r\le\frac{1}{2}\times10^{-n}$, then $x^{*}$ has at least $n$ significant digits.

> **Definition 1.2 (Relative Error and Relative Error Bound)**
> 
> Let $x^{*}$ be an approximation to the exact value $x$. The quantity $e_r\left(x^{*}\right)=\frac{e\left(x^{*}\right)}{x^{*}}$ is called the relative error of $x^{*}$. If there exists a positive number $\varepsilon_r$ such that $\left|e_r\left(x^{*}\right)\right|\le\varepsilon_r$, then $\varepsilon_r$ is called the relative error bound of $x^{*}$.

> **Definition 1.3 (Significant Digits)**
> 
> If the normalized form of the approximation $x^{*}$ is $x^{*}=\pm0.a_1a_2\cdots a_n\cdots\times10^{m}$, where $m$ is an integer, $a_1\ne0$, and $\left|x-x^{*}\right|\le\frac{1}{2}\times10^{m-n}$, then $x^{*}$ is said to have $n$ significant digits.

## 1-10

Given that $\sqrt{783}\approx27.983$ has 5 significant digits, find the two roots of the equation $x^{2}-56x+1=0$ so that they each have at least 4 significant digits.

### Solution to 1-10

The discriminant of the equation $x^{2}-56x+1=0$ is

$$
\Delta=56^{2}-4=3136-4=3132=4\times783,
$$

so $\sqrt{\Delta}=2\sqrt{783}\approx2\times27.983=55.966$. By the quadratic formula, the two roots can be written as

$$
x_1=\frac{56+\sqrt{\Delta}}{2}=28+\sqrt{783}\approx28+27.983=55.983,
$$

$$
x_2=\frac{56-\sqrt{\Delta}}{2}=28-\sqrt{783}\approx28-27.983=0.017.
$$

If $x_2$ is computed directly as $28-\sqrt{783}$, this is the subtraction of two nearly equal numbers; by Avoid Subtracting Two Nearly Equal Numbers, significant digits would be seriously lost, so this direct computation cannot be used.

By Vieta's formulas, the product of the two roots is $x_1x_2=1$, so $x_2=\frac{1}{x_1}$ (note $x_1\ne0$). First compute $x_1$: by **Definition 1.3 (Significant Digits)**, $\sqrt{783}\approx27.983=0.27983\times10^{2}$ has 5 significant digits with error bound $\frac{1}{2}\times10^{2-5}=\frac{1}{2}\times10^{-3}=0.0005$, so

$$
\left|e\left(x_1\right)\right|=\left|e\left(\sqrt{783}\right)\right|\le0.0005\le\frac{1}{2}\times10^{2-4}=0.005,
$$

i.e. $x_1\approx55.983$ has at least 4 significant digits.

Then by Error Propagation in Basic Operations, for $x_2=\frac{1}{x_1}$, the relative error of a quotient is approximately the difference of the relative errors of numerator and denominator, so

$$
\left|e_r\left(x_2\right)\right|\approx\left|e_r\left(x_1\right)\right|\le\frac{0.0005}{55.983}\approx8.93\times10^{-6},
$$

while $x_2=\frac{1}{55.983}\approx0.017862=0.17862\times10^{-1}$, so

$$
\left|e\left(x_2\right)\right|\approx x_2\left|e_r\left(x_2\right)\right|\approx0.017862\times8.93\times10^{-6}\approx1.595\times10^{-7}\le\frac{1}{2}\times10^{-1-4}=\frac{1}{2}\times10^{-5},
$$

by **Definition 1.3 (Significant Digits)**, $x_2\approx0.017862$ has at least 4 significant digits.

Therefore the two roots are $x_1\approx55.983$ and $x_2\approx0.017862$, each having at least 4 significant digits. $\blacksquare$
