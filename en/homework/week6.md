# Assignment 6

> **General Form of the Linear Least-Squares Method** (Formulas (6.7)–(6.9)) <br>For a data set $\left(x_i,y_i\right)\left(i=1,2,\dots,n\right)$, take a set of linearly independent functions on $\left[a,b\right]$ $\varphi_k\left(x\right)\left(k=0,1,\dots,m\right)$, and find $p\left(x\right)=\sum_{k=0}^m a_k\varphi_k\left(x\right)$ that minimizes the weighted sum of squared residuals $\sum_{i=1}^n w_i\left[y_i-p\left(x_i\right)\right]^2$. The coefficients satisfy the normal equations $$\sum_{k=0}^m a_k\left(\varphi_k,\varphi_j\right)=\left(y,\varphi_j\right)\quad\left(j=0,1,\dots,m\right),\quad\left(\varphi_k,\varphi_j\right)=\sum_{i=1}^n w_i\varphi_k\left(x_i\right)\varphi_j\left(x_i\right),\quad\left(y,\varphi_j\right)=\sum_{i=1}^n w_i y_i\varphi_j\left(x_i\right).$$ In particular, taking $\varphi_k\left(x\right)=x^k$ gives polynomial fitting; for a linear fit $y=a_0+a_1x$ ($w_i=1$), the normal equations are $$\begin{cases}n a_0+a_1\sum\limits_{i=1}^n x_i=\sum\limits_{i=1}^n y_i,\\a_0\sum\limits_{i=1}^n x_i+a_1\sum\limits_{i=1}^n x_i^2=\sum\limits_{i=1}^n x_i y_i.\end{cases}$$

> **Linearization of Nonlinear Fitting** (6.1.2 Exponential Fitting, 6.1.3 Fractional Linear Fitting) <br>For the exponential form $y=ae^{bx}$, taking logarithms on both sides gives $\ln y=\ln a+bx$; first perform a linear fit on the transformed data set $\left(x_i,\ln y_i\right)$ according to the **General Form of the Linear Least-Squares Method**, then take exponentials to recover. For the separable fractional form $y=\frac{x}{ax+b}$, taking reciprocals on both sides gives $\frac{1}{y}=a+b\frac{1}{x}$; first perform a linear fit on the data set $\left(\frac{1}{x_i},\frac{1}{y_i}\right)$, then take reciprocals to recover.

> **Definition 6.2** (Orthogonal Function System) <br>If a function system $\left\{\varphi_k\left(x\right)\right\}$ on $\left[a,b\right]$ satisfies $\left(\varphi_j,\varphi_k\right)=\int_a^b w\left(x\right)\varphi_j\left(x\right)\varphi_k\left(x\right)\,\mathrm dx=0\ \left(j\ne k\right)$ and $\left(\varphi_k,\varphi_k\right)> 0$, then it is called an orthogonal function system on $\left[a,b\right]$ with respect to the weight function $w\left(x\right)$, where $\left(\varphi,\psi\right)=\int_a^b w\left(x\right)\varphi\left(x\right)\psi\left(x\right)\,\mathrm dx$ is called the inner product of the functions.

> **Definition 6.3** (Best Least-Squares Approximation Function) <br>Let $f\left(x\right)$ be continuous on $\left[a,b\right]$, $H=\operatorname{Span}\left\{\varphi_0,\varphi_1,\dots,\varphi_m\right\}$; if $p\left(x\right)=\sum_{k=0}^m a_k\varphi_k\left(x\right)$ makes $\int_a^b w\left(x\right)\left[f\left(x\right)-p\left(x\right)\right]^2\,\mathrm dx$ minimal, then $p\left(x\right)$ is called the best least-squares approximation function to $f\left(x\right)$ in $H$ with respect to the weight function $w\left(x\right)$.

> **Normal Equations for Best Least-Squares Approximation** (Formulas (6.32), (6.35), (6.36)) <br>By **Definition 6.3**, the coefficients $a_k$ satisfy the normal equations $\sum_{k=0}^m a_k\left(\varphi_k,\varphi_j\right)=\left(f,\varphi_j\right)\ \left(j=0,1,\dots,m\right)$, where $\left(f,\varphi_j\right)=\int_a^b w\left(x\right)f\left(x\right)\varphi_j\left(x\right)\,\mathrm dx$. If $\left\{\varphi_k\right\}$ is an orthogonal function system, the equations are diagonalized and the solution is $a_k=\frac{\left(f,\varphi_k\right)}{\left(\varphi_k,\varphi_k\right)}$, so that the best least-squares approximation function is $p\left(x\right)=\sum_{k=0}^m\frac{\left(f,\varphi_k\right)}{\left(\varphi_k,\varphi_k\right)}\varphi_k\left(x\right)$.

> **Legendre Polynomials** (Formulas (6.18), (6.19)) <br>The first few are $P_0\left(x\right)=1$, $P_1\left(x\right)=x$, $P_2\left(x\right)=\frac{3x^2-1}{2}$, $P_3\left(x\right)=\frac{5x^3-3x}{2}$. They form an orthogonal polynomial system on $\left[-1,1\right]$ with weight $w\left(x\right)\equiv1$, with $\left(P_n,P_m\right)=0\ \left(n\ne m\right)$ and $\left(P_n,P_n\right)=\frac{2}{2n+1}$. When used on an interval $\left[a,b\right]$, make the change of variable $t=\frac{2x-\left(b+a\right)}{b-a}$ and take $\varphi_k\left(x\right)=P_k\left(t\right)$.

### Problem 1 (Problem 6-1)

Given the following data table: $x_i=1.36,1.49,1.73,1.81,1.95,2.16,2.28,2.48$; $y_i=14.094,15.069,16.844,17.378,18.435,19.949,20.963,22.495$. Find its least-squares linear fitting polynomial.

### Solution to Problem 1

Let the linear fitting polynomial be $y=a_0+a_1x$. By the **General Form of the Linear Least-Squares Method** (normal equations for a linear fit), with $n=8$, compute the sums: $$
\sum_{i=1}^8 x_i=15.26,\quad\sum_{i=1}^8 y_i=145.227,\quad\sum_{i=1}^8 x_i^2=30.1556,\quad\sum_{i=1}^8 x_i y_i=284.83628.
$$

Substituting into the normal equations: $$
\begin{cases}8a_0+15.26a_1=145.227,\\15.26a_0+30.1556a_1=284.83628.\end{cases}
$$

Solving gives $a_0\approx3.9161$, $a_1\approx7.4639$. Therefore the desired least-squares linear fitting polynomial is

$$
P_1\left(x\right)=3.9161+7.4639x.
$$

$\blacksquare$

### Problem 2 (Problem 6-3)

The production records of a certain open-hearth furnace are given in the table: $i=1,2,3,4,5$; $x_i=165,123,150,121,141$ (carbon content of the molten steel); $y_i=187,126,172,125,148$ (smelting time). Find the functional relationship between the carbon content of the molten steel and the smelting time.

### Solution to Problem 2

The scatter plot is approximately a straight line, so let the functional relationship between carbon content $x$ and smelting time $y$ be $y=a_0+a_1x$. By the **General Form of the Linear Least-Squares Method** (normal equations for a linear fit), with $n=5$, the sums are

$$
\sum_{i=1}^5 x_i=700,\quad\sum_{i=1}^5 y_i=758,\quad\sum_{i=1}^5 x_i^2=99376,\quad\sum_{i=1}^5 x_i y_i=108146.
$$

Substituting into the normal equations: $$
\begin{cases}5a_0+700a_1=758,\\700a_0+99376a_1=108146.\end{cases}
$$

Solving gives $a_0\approx-54.534$, $a_1\approx1.4724$. Therefore the functional relationship between the carbon content of the molten steel and the smelting time is approximately

$$
y=-54.534+1.4724x.
$$

$\blacksquare$

### Problem 3 (Problem 6-4)

Use the least-squares method to find an empirical formula of the form $y=a+bx^2$ ($a,b$ are constants) fitting the following data: $x_i=19,25,31,38,44$; $y_i=19.0,32.3,49.0,73.3,97.8$.

### Solution to Problem 3

Let $u=x^2$; then the fitting function becomes $y=a+bu$, which is a linear least-squares problem with basis functions $\varphi_0\left(x\right)=1$, $\varphi_1\left(x\right)=x^2$. By the **General Form of the Linear Least-Squares Method**, the transformed data are

$$
u_i=x_i^2=361,625,961,1444,1936\quad\left(n=5\right),
$$

and the sums are

$$
\sum u_i=5327,\quad\sum y_i=271.4,\quad\sum u_i^2=7277699,\quad\sum u_i y_i=369321.5.
$$

Substituting into the normal equations for $a,b$: $$
\begin{cases}5a+5327b=271.4,\\5327a+7277699b=369321.5.\end{cases}
$$

Solving gives $a\approx0.9726$, $b\approx0.05004$. Therefore the desired empirical formula is

$$
y=0.9726+0.05004x^2.
$$

$\blacksquare$

### Problem 4 (Problem 6-6)

Use the least-squares method to find an empirical formula of the form $y=ae^{bx}$ ($a,b$ are constants) fitting the following data: $x_i=1,2,3,4,5,6,7,8$; $y_i=15.3,20.5,27.4,36.6,49.1,65.6,87.87,117.6$.

### Solution to Problem 4

By **Linearization of Nonlinear Fitting** (Exponential Fitting), let $Y=\ln y$; then $Y=\left(\ln a\right)+bx$. Perform a linear least-squares fit on the data set $\left(x_i,\ln y_i\right)$, with $n=8$, $$
Y_i=\ln y_i=2.7279,3.0204,3.3105,3.6001,3.8939,4.1836,4.4759,4.7673,
$$

and the sums are

$$
\sum x_i=36,\quad\sum Y_i=29.9795,\quad\sum x_i^2=204,\quad\sum x_iY_i=147.1406.
$$

Substituting into the normal equations: $$
\begin{cases}8\left(\ln a\right)+36b=29.9795,\\36\left(\ln a\right)+204b=147.1406.\end{cases}
$$

Solving gives $\ln a\approx2.4367$, $b\approx0.2913$, and hence $a=e^{2.4367}\approx11.436$. Therefore the desired empirical formula is

$$
y=11.436\,e^{0.2913x}.
$$

$\blacksquare$

### Problem 5 (Problem 6-7)

In a certain chemical reaction, the relationship between the mass concentration $y$ of the product and time $t$ is measured as in the table (units omitted): $t_i=1,2,3,4,6,8,10,12,14,16$; $y_i=4.00,6.41,8.01,8.79,9.53,9.86,10.33,10.42,10.53,10.61$. Use the least-squares method to find an empirical formula of the form $y=\frac{t}{at+b}$ ($a,b$ are constants) fitting the above data.

### Solution to Problem 5

By **Linearization of Nonlinear Fitting** (Fractional Linear Fitting), taking reciprocals on both sides of $y=\frac{t}{at+b}$ gives

$$
\frac{1}{y}=a+b\frac{1}{t}.
$$

Let $u=\frac{1}{t}$, $z=\frac{1}{y}$; then $z=a+bu$, and perform a linear least-squares fit on the data set $\left(u_i,z_i\right)=\left(\frac{1}{t_i},\frac{1}{y_i}\right)$. With $n=10$, one computes

$$
\sum u_i=2.6923,\quad\sum z_i=1.2330,\quad\sum u_i^2=1.4930,\quad\sum u_i z_i=0.45858.
$$

Substituting into the normal equations: $$
\begin{cases}10a+2.6923b=1.2330,\\2.6923a+1.4930b=0.45858.\end{cases}
$$

Solving gives $a\approx0.07891$, $b\approx0.16486$. Therefore the desired empirical formula is

$$
y=\frac{t}{0.07891\,t+0.16486}.
$$

$\blacksquare$

### Problem 6 (Problem 6-10)

Prove that the function system $\left\{\varphi_0,\varphi_1,\dots,\varphi_n\right\}$ is linearly independent if and only if the Gram determinant $G\left(\varphi_0,\varphi_1,\dots,\varphi_n\right)\ne0$.

### Solution to Problem 6

Denote the Gram matrix by $\boldsymbol G=\left[\left(\varphi_i,\varphi_j\right)\right]_{i,j=0}^n$, where the inner product is given by **Definition 6.2** as $\left(\varphi_i,\varphi_j\right)=\int_a^b w\left(x\right)\varphi_i\left(x\right)\varphi_j\left(x\right)\,\mathrm dx$, and the Gram determinant is $G=\det\boldsymbol G$.

For any vector $\boldsymbol c=\left(c_0,c_1,\dots,c_n\right)^{\top}$,

$$
\boldsymbol c^{\top}\boldsymbol G\boldsymbol c=\sum_{i=0}^n\sum_{j=0}^n c_i c_j\left(\varphi_i,\varphi_j\right)=\left(\sum_{i=0}^n c_i\varphi_i,\sum_{j=0}^n c_j\varphi_j\right)=\int_a^b w\left(x\right)\left[\sum_{i=0}^n c_i\varphi_i\left(x\right)\right]^2\,\mathrm dx\ge0.
$$

Sufficiency. Suppose $G\ne0$; assume for contradiction that $\left\{\varphi_i\right\}$ is linearly dependent, then there exists a nonzero $\boldsymbol c$ such that $\sum_{i=0}^n c_i\varphi_i\left(x\right)\equiv0$, and hence $\boldsymbol c^{\top}\boldsymbol G\boldsymbol c=0$. But when $G\ne0$, $\boldsymbol G$ is invertible (positive-definite), so for $\boldsymbol c\ne0$ one necessarily has $\boldsymbol c^{\top}\boldsymbol G\boldsymbol c> 0$, a contradiction. Thus $\left\{\varphi_i\right\}$ is linearly independent.

Necessity. Suppose $\left\{\varphi_i\right\}$ is linearly independent; assume for contradiction that $G=0$, then $\boldsymbol G$ is singular, and there exists a nonzero $\boldsymbol c$ such that $\boldsymbol G\boldsymbol c=\boldsymbol0$, hence $\boldsymbol c^{\top}\boldsymbol G\boldsymbol c=0$, i.e.

$$
\int_a^b w\left(x\right)\left[\sum_{i=0}^n c_i\varphi_i\left(x\right)\right]^2\,\mathrm dx=0.
$$

Since $w\left(x\right)> 0$ and the integrand is nonnegative, it follows that $\sum_{i=0}^n c_i\varphi_i\left(x\right)\equiv0$, contradicting the linear independence of $\left\{\varphi_i\right\}$. Thus $G\ne0$.

In summary, the function system $\left\{\varphi_0,\varphi_1,\dots,\varphi_n\right\}$ is linearly independent if and only if the Gram determinant $G\ne0$.$\blacksquare$

### Problem 7 (Problem 6-13)

Find the degree-one best least-squares approximation polynomial with respect to $f\left(x\right)$ on the specified interval for the following functions: (1) $f\left(x\right)=\sqrt{x}$, $\left[0,1\right]$; (2) $f\left(x\right)=e^x$, $\left[0,1\right]$; (3) $f\left(x\right)=\sin\frac{\pi}{2}x$, $\left[0,1\right]$. (Only part (2) is required.) ### Solution to Problem 7

For $f\left(x\right)=e^x$ on $\left[0,1\right]$, take weight $w\left(x\right)\equiv1$, basis functions $\varphi_0\left(x\right)=1$, $\varphi_1\left(x\right)=x$, i.e. $H=\operatorname{Span}\left\{1,x\right\}$. By **Definition 6.3** and the **Normal Equations for Best Least-Squares Approximation** (Formula (6.32)), first compute the inner products: $$
\left(\varphi_0,\varphi_0\right)=\int_0^1\mathrm dx=1,\quad\left(\varphi_0,\varphi_1\right)=\left(\varphi_1,\varphi_0\right)=\int_0^1x\,\mathrm dx=\frac12,\quad\left(\varphi_1,\varphi_1\right)=\int_0^1x^2\,\mathrm dx=\frac13,
$$

$$
\left(f,\varphi_0\right)=\int_0^1 e^x\,\mathrm dx=e-1,\quad\left(f,\varphi_1\right)=\int_0^1x e^x\,\mathrm dx=\left[x e^x-e^x\right]_0^1=1.
$$

Substituting into the normal equations: $$
\begin{cases}a_0+\frac12 a_1=e-1,\\\frac12 a_0+\frac13 a_1=1.\end{cases}
$$

Solving gives $a_0\approx0.8731$, $a_1\approx1.6903$. Therefore the degree-one best least-squares approximation polynomial to $f\left(x\right)=e^x$ on $\left[0,1\right]$ is

$$
p\left(x\right)=0.8731+1.6903x.
$$

$\blacksquare$

### Problem 8 (Problem 6-15)

Using Legendre polynomials, find the degree-3 best least-squares approximation polynomial $P_3\left(x\right)$ to $f\left(x\right)=\sin x$ on $\left[-\frac{\pi}{2},\frac{\pi}{2}\right]$, and compute the mean-square error $\int_{-\pi/2}^{\pi/2}\left[\sin x-P_3\left(x\right)\right]^2\,\mathrm dx$.

### Solution to Problem 8

By the **Normal Equations for Best Least-Squares Approximation** (orthogonal case, Formulas (6.35), (6.36)), take **Legendre polynomials** as the basis on $\left[-\frac{\pi}{2},\frac{\pi}{2}\right]$. Make the change of variable $t=\frac{2x}{\pi}$; then $x=\frac{\pi}{2}t$, $\mathrm dx=\frac{\pi}{2}\mathrm dt$, $t\in\left[-1,1\right]$, and take $\varphi_k\left(x\right)=P_k\left(t\right)=P_k\!\left(\frac{2x}{\pi}\right)$.

By the orthogonality of Legendre polynomials, $\left(P_n,P_m\right)=\frac{2}{2n+1}\delta_{nm}$, so

$$
\left(\varphi_k,\varphi_k\right)=\frac{\pi}{2}\int_{-1}^1P_k^2\left(t\right)\,\mathrm dt=\frac{\pi}{2}\cdot\frac{2}{2k+1}=\frac{\pi}{2k+1},
$$

$$
\left(f,\varphi_k\right)=\frac{\pi}{2}\int_{-1}^1\sin\!\left(\frac{\pi t}{2}\right)P_k\left(t\right)\,\mathrm dt.
$$

Since $\sin\!\left(\frac{\pi t}{2}\right)$ is odd and $P_0\left(t\right)=1$, $P_2\left(t\right)=\frac{3t^2-1}{2}$ are even, we have $\left(f,\varphi_0\right)=\left(f,\varphi_2\right)=0$, and only $a_1,a_3$ need be computed. Compute the integrals: $$
\int_{-1}^1 t\sin\!\left(\frac{\pi t}{2}\right)\mathrm dt=\frac{8}{\pi^2},\quad\int_{-1}^1 t^3\sin\!\left(\frac{\pi t}{2}\right)\mathrm dt=\frac{24}{\pi^2}-\frac{192}{\pi^4},
$$

hence

$$
\left(f,\varphi_1\right)=\frac{\pi}{2}\cdot\frac{8}{\pi^2}=\frac{4}{\pi},\quad\left(f,\varphi_3\right)=\frac{\pi}{2}\left[\frac52\left(\frac{24}{\pi^2}-\frac{192}{\pi^4}\right)-\frac32\cdot\frac{8}{\pi^2}\right]=\frac{24}{\pi}-\frac{240}{\pi^3}.
$$

By Formula (6.35): $$
a_1=\frac{\left(f,\varphi_1\right)}{\left(\varphi_1,\varphi_1\right)}=\frac{4/\pi}{\pi/3}=\frac{12}{\pi^2}\approx1.2159,
$$

$$
a_3=\frac{\left(f,\varphi_3\right)}{\left(\varphi_3,\varphi_3\right)}=\frac{24/\pi-240/\pi^3}{\pi/7}=\frac{168}{\pi^2}-\frac{1680}{\pi^4}\approx-0.2249.
$$

Therefore the degree-3 best least-squares approximation polynomial is

$$
P_3\left(x\right)=a_1P_1\!\left(\frac{2x}{\pi}\right)+a_3P_3\!\left(\frac{2x}{\pi}\right)=1.2159\cdot\frac{2x}{\pi}-0.2249\cdot\frac{5\left(2x/\pi\right)^3-3\left(2x/\pi\right)}{2}\approx0.9888x-0.1451x^3.
$$

By orthogonality, the mean-square error is

$$
\int_{-\pi/2}^{\pi/2}\left[\sin x-P_3\left(x\right)\right]^2\mathrm dx=\left(f,f\right)-a_1^2\left(\varphi_1,\varphi_1\right)-a_3^2\left(\varphi_3,\varphi_3\right),
$$

where $\left(f,f\right)=\int_{-\pi/2}^{\pi/2}\sin^2x\,\mathrm dx=\frac{\pi}{2}$; substituting gives

$$
\int_{-\pi/2}^{\pi/2}\left[\sin x-P_3\left(x\right)\right]^2\mathrm dx=\frac{\pi}{2}-\frac{12^2}{\pi^4}\cdot\frac{\pi}{3}-\left(\frac{168}{\pi^2}-\frac{1680}{\pi^4}\right)^2\frac{\pi}{7}\approx2.42\times10^{-5}.
$$

$\blacksquare$
