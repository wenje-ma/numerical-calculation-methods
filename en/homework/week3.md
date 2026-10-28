# week3

> **Basic Knowledge: Jacobi Iteration**<br>Componentwise update.

> **Basic Knowledge: Gauss-Seidel Iteration**<br>Use new components immediately.

> **Basic Knowledge: SOR Method**<br>Relaxation factor $\omega$.

> **Basic Knowledge: Sufficient Convergence Conditions**<br>Strict diagonal dominance.

> **Definition 3.3 (Spectral Radius)**<br>$\rho(A)=\max|\lambda_i|$.

> **Definition 3.4 (Diagonally Dominant Matrix)**<br>$|a_{ii}|\ge\sum_{j\ne i}|a_{ij}|$.

> **Theorem 3.6 (Convergence Criterion)**<br>$\rho(M)<1$.
---

## Exercise 3-3

Solve by Jacobi and Gauss-Seidel, 4 iterations.

### Solution Exercise 3-3

Jacobi converges, Gauss-Seidel diverges. $\blacksquare$

---

## Exercise 3-5

Find range of $a$ for convergence.

### Solution Exercise 3-5

$|a|>2$. $\blacksquare$

---

## Exercise 3-7

Write formulas and check convergence.

### Solution Exercise 3-7

GS and SOR converge, Jacobi diverges. $\blacksquare$

---

## Exercise 3-8

Write a convergent iteration.

### Solution Exercise 3-8

Permute rows to get diagonal dominance. $\blacksquare$
