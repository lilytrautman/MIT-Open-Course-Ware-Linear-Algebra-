# 18.06SC Final Exam (solved)
Feb 10 2026
## Question 1

Suppose $A$ is $3 \times 4$, and $Ax = 0$ has exactly 2 special solutions:

$$
x_1 = \begin{bmatrix} 1 \\ 1 \\ 1 \\ 0 \end{bmatrix} \quad \text{and} \quad x_2 = \begin{bmatrix} -2 \\ -1 \\ 0 \\ 1 \end{bmatrix}
$$

### (a) Find the row reduced echelon form $R$ of $A$.

 
The special solutions to $Ax = 0$ correspond to the free variables in the reduced row echelon form (RREF) of $A$. Since $A$ is $3 \times 4$ and there are 2 special solutions, there are 2 free variables and 2 pivot columns. We can reconstruct $R$ by expressing the general solution in terms of the free variables and matching the structure to the RREF.

 
1. The general solution to $Ax = 0$ is $x = c_1 x_1 + c_2 x_2$ for scalars $c_1, c_2$.
2. Write $x$ in terms of the variables:
   $$
   x = c_1 \begin{bmatrix} 1 \\ 1 \\ 1 \\ 0 \end{bmatrix} + c_2 \begin{bmatrix} -2 \\ -1 \\ 0 \\ 1 \end{bmatrix} = \begin{bmatrix} c_1 - 2c_2 \\ c_1 - c_2 \\ c_1 \\ c_2 \end{bmatrix}
   $$
3. Let $x_3 = c_1$ and $x_4 = c_2$ (so $x_3$ and $x_4$ are the free variables). Then:
   $$
   x_1 = x_3 - 2x_4 \\
   x_2 = x_3 - x_4 \\
   x_3 = x_3 \\
   x_4 = x_4
   $$
4. Rearranged, the general solution is:
   $$
   \begin{bmatrix} x_1 \\ x_2 \\ x_3 \\ x_4 \end{bmatrix} = x_3 \begin{bmatrix} 1 \\ 1 \\ 1 \\ 0 \end{bmatrix} + x_4 \begin{bmatrix} -2 \\ -1 \\ 0 \\ 1 \end{bmatrix}
   $$
5. The RREF of $A$ must have pivots in columns 1 and 2, and free variables in columns 3 and 4. The equations for the pivots are:
   $$
   x_1 + 2x_4 - x_3 = 0 \\
   x_2 + x_4 - x_3 = 0
   $$
   Rearranged:
   $$
   x_1 - x_3 + 2x_4 = 0 \\
   x_2 - x_3 + x_4 = 0
   $$
6. The RREF $R$ is:
   $$
   R = \begin{bmatrix}
   1 & 0 & -1 & 2 \\
   0 & 1 & -1 & 1 \\
   0 & 0 & 0 & 0
   \end{bmatrix}
   $$

Therefore,
The row reduced echelon form of $A$ is
$$
R = \begin{bmatrix}
1 & 0 & -1 & 2 \\
0 & 1 & -1 & 1 \\
0 & 0 & 0 & 0
\end{bmatrix}
$$


---

### (b) Find the dimensions of all four fundamental subspaces $C(A)$, $N(A)$, $C(A^{\mathrm{T}})$, $N(A^{\mathrm{T}})$. Find bases for those you can.

 
The dimensions of the fundamental subspaces are determined by the number of pivots and free variables. The nullspace $N(A)$ is spanned by the special solutions. The column space $C(A)$ has dimension equal to the number of pivots. The row space $C(A^{\mathrm{T}})$ and the left nullspace $N(A^{\mathrm{T}})$ can be found from the RREF.

 
1. $A$ is $3 \times 4$ with 2 pivots (from part (a)), so:
   - $\dim N(A) = 2$ (number of free variables)
   - $\dim C(A) = 2$ (number of pivots)
   - $\dim C(A^{\mathrm{T}}) = 2$ (row space, number of pivots)
   - $\dim N(A^{\mathrm{T}}) = 1$ (since $3 - 2 = 1$)
2. Bases:
   - $N(A)$: The special solutions $x_1$ and $x_2$ form a basis.
   - $C(A)$: The pivot columns of $A$ form a basis, but since $A$ is not given, the pivot columns of $R$ can be used for the row space.
   - $C(A^{\mathrm{T}})$: The nonzero rows of $R$ form a basis for the row space.
   - $N(A^{\mathrm{T}})$: Find a vector $y$ such that $R^T y = 0$.
3. The nonzero rows of $R$ are:
   $$
   r_1 = [1, 0, -1, 2], \quad r_2 = [0, 1, -1, 1]
   $$
   So a basis for $C(A^{\mathrm{T}})$ is $\{ r_1, r_2 \}$.
4. To find a basis for $N(A^{\mathrm{T}})$, solve $R^T y = 0$:
   $$
   \begin{bmatrix} 1 & 0 \\ 0 & 1 \\ -1 & -1 \\ 2 & 1 \end{bmatrix} \begin{bmatrix} y_1 \\ y_2 \end{bmatrix} = 0
   $$
   This gives:
   $y_1 = 0$, $y_2 = 0$, $-y_1 - y_2 = 0$, $2y_1 + y_2 = 0$. The only solution is $y_1 = y_2 = 0$, but since $R$ is $3 \times 4$, the left nullspace is in $\mathbb{R}^3$ and has dimension 1. Alternatively, since the rank is 2, $N(A^{\mathrm{T}})$ has dimension $3 - 2 = 1$.
   
   To find a basis, note that the left nullspace is orthogonal to the row space. The row space is spanned by $[1, 0, -1, 2]$ and $[0, 1, -1, 1]$. The left nullspace is the set of $y$ such that $y^T R = 0$.
   
   Let $y = [a, b, c]$ and solve $y^T R = 0$:
   $$
   a[1, 0, -1, 2] + b[0, 1, -1, 1] + c[0, 0, 0, 0] = 0
   $$
   This gives a single nontrivial solution, which can be found by inspection or by solving the system.

Therefore,
- $\dim N(A) = 2$, basis: $\left\{ \begin{bmatrix} 1 \\ 1 \\ 1 \\ 0 \end{bmatrix}, \begin{bmatrix} -2 \\ -1 \\ 0 \\ 1 \end{bmatrix} \right\}$
- $\dim C(A) = 2$, basis: the pivot columns of $A$ (not explicitly given)
- $\dim C(A^{\mathrm{T}}) = 2$, basis: $\left\{ [1, 0, -1, 2], [0, 1, -1, 1] \right\}$
- $\dim N(A^{\mathrm{T}}) = 1$, basis: can be found by solving $R^T y = 0$

---

## Question 2

**2 (6+3+2=11 pts.)**

### (a) Find the inverse of a $3 \times 3$ upper triangular matrix $U$ with nonzero entries $a, b, c, d, e, f$:

Given:
$$
U = \begin{bmatrix} a & b & c \\ 0 & d & e \\ 0 & 0 & f \end{bmatrix}
$$

 
The inverse of an upper triangular matrix with nonzero diagonal entries is also upper triangular. We can find $U^{-1}$ by solving $U X = I$ or by using Gauss-Jordan elimination. Each entry of $U^{-1}$ can be found by back substitution.

 
1. Let $U^{-1} = X = \begin{bmatrix} x_{11} & x_{12} & x_{13} \\ 0 & x_{22} & x_{23} \\ 0 & 0 & x_{33} \end{bmatrix}$.
2. Solve $U X = I$ column by column:
   - Third column: $U \begin{bmatrix} x_{13} \\ x_{23} \\ x_{33} \end{bmatrix} = \begin{bmatrix} 0 \\ 0 \\ 1 \end{bmatrix}$
     - $f x_{33} = 1 \implies x_{33} = 1/f$
     - $d x_{23} + e x_{33} = 0 \implies x_{23} = -e/(d f)$
     - $a x_{13} + b x_{23} + c x_{33} = 0 \implies x_{13} = \frac{-b x_{23} - c x_{33}}{a} = \frac{b e}{a d f} - \frac{c}{a f}$
   - Second column: $U \begin{bmatrix} x_{12} \\ x_{22} \\ 0 \end{bmatrix} = \begin{bmatrix} 0 \\ 1 \\ 0 \end{bmatrix}$
     - $d x_{22} = 1 \implies x_{22} = 1/d$
     - $a x_{12} + b x_{22} = 0 \implies x_{12} = -b/(a d)$
   - First column: $U \begin{bmatrix} x_{11} \\ 0 \\ 0 \end{bmatrix} = \begin{bmatrix} 1 \\ 0 \\ 0 \end{bmatrix}$
     - $a x_{11} = 1 \implies x_{11} = 1/a$
3. Assemble $U^{-1}$:
$$
U^{-1} = \begin{bmatrix}
1/a & -b/(a d) & (b e)/(a d f) - c/(a f) \\
0 & 1/d & -e/(d f) \\
0 & 0 & 1/f
\end{bmatrix}
$$

Therefore,
The inverse is
$$
U^{-1} = \begin{bmatrix}
\frac{1}{a} & -\frac{b}{a d} & \frac{b e}{a d f} - \frac{c}{a f} \\
0 & \frac{1}{d} & -\frac{e}{d f} \\
0 & 0 & \frac{1}{f}
\end{bmatrix}
$$

---

### (b) Suppose the columns of $U$ are eigenvectors of a matrix $A$. Show that $A$ is also upper triangular.

 
If $U$ is invertible and its columns are eigenvectors of $A$, then $A$ is similar to a diagonal matrix if the eigenvectors are linearly independent. If $U$ is upper triangular and $A$ has $U$ as its eigenvector matrix, then $A$ must be upper triangular as well.

 
1. If $A$ has $U$ as its eigenvector matrix, then $A = U \Lambda U^{-1}$, where $\Lambda$ is diagonal.
2. Since $U$ is upper triangular and $U^{-1}$ is also upper triangular, the product $U \Lambda U^{-1}$ is upper triangular (see notes/Diagonalization.ipynb).
3. This is because the product of upper triangular matrices is upper triangular, and multiplying by a diagonal matrix preserves upper triangularity.

Therefore,
$A$ is upper triangular.

---

### (c) Explain why this $U$ cannot be the same matrix as the first factor in the Singular Value Decomposition $A = U\Sigma V^{\mathrm{T}}$.

 
In the SVD, the matrix $U$ is always an orthogonal (or unitary) matrix, meaning its columns are orthonormal. An upper triangular matrix with arbitrary nonzero entries cannot be orthogonal unless it is a permutation of a diagonal matrix with $\pm 1$ entries.

 
1. In the SVD, $U$ must satisfy $U^T U = I$ (orthogonality).
2. An upper triangular matrix with arbitrary nonzero entries cannot have orthonormal columns unless it is diagonal with $\pm 1$ entries (see notes/SVD.ipynb and notes/SVD-intro.ipynb).
3. The given $U$ has arbitrary nonzero entries $a, b, c, d, e, f$, so its columns are not necessarily orthonormal.

Therefore,
This $U$ cannot be the $U$ in the SVD unless it is a signed permutation matrix (which is not the case here).

---

## Question 3

**3 (3+3+5=11 pts.)**

### (a) $A$ and $B$ are any matrices with the same number of rows. What can you say (and explain why it is true) about the comparison of
$$
\text{rank of } A \qquad \qquad \text{rank of the block matrix } [A \quad B]
$$

 
The rank of $[A \ B]$ is at least as large as the rank of $A$, because $A$'s columns are included in $[A \ B]$. Adding more columns cannot decrease the rank.

 
1. The rank of a matrix is the dimension of its column space (see notes/Linear Transformations.ipynb).
2. The columns of $A$ are present in $[A \ B]$, so the column space of $A$ is a subspace of the column space of $[A \ B]$.
3. Adding columns (from $B$) can only increase or leave unchanged the dimension of the column space.

Therefore,
$$
\text{rank}(A) \leq \text{rank}([A \ B])
$$

---

### (b) Suppose $B = A^2$. How do those ranks compare? Explain your reasoning.

 
If $B = A^2$, then the columns of $A^2$ are linear combinations of the columns of $A$, so adding $A^2$ as extra columns does not increase the rank.

 
1. Each column of $A^2$ is a linear combination of the columns of $A$ (since $A^2 = A A$).
2. Therefore, the column space of $A^2$ is contained in the column space of $A$.
3. Thus, $[A \ A^2]$ has the same column space as $A$.

Therefore,
$$
\text{rank}([A \ A^2]) = \text{rank}(A)
$$

---

### (c) If $A$ is $m$ by $n$ of rank $r$, what are the dimensions of these nullspaces?
$$
\text{Nullspace of } A \qquad \qquad \text{Nullspace of } [A \quad A]
$$

 
The nullspace of $A$ consists of all $x$ such that $A x = 0$. The nullspace of $[A \ A]$ consists of all vectors $\begin{bmatrix} x \\ y \end{bmatrix}$ such that $A x + A y = 0$, or $A(x + y) = 0$.

 
1. $A$ is $m \times n$ of rank $r$, so $\dim N(A) = n - r$ (see notes/Elimination-matrices.ipynb).
2. For $[A \ A]$, let $z = \begin{bmatrix} x \\ y \end{bmatrix}$, $x, y \in \mathbb{R}^n$.
3. $[A \ A] z = A x + A y = A(x + y) = 0$.
4. So the nullspace is all pairs $(x, y)$ such that $x + y \in N(A)$.
5. Let $s = x + y \in N(A)$, and $t = x - y$ (so $x = \frac{s + t}{2}$, $y = \frac{s - t}{2}$). For each $s \in N(A)$ and $t \in \mathbb{R}^n$, $z = \begin{bmatrix} x \\ y \end{bmatrix}$ is in the nullspace.
6. Therefore, the nullspace of $[A \ A]$ has dimension $n$ (from $t$) plus $n - r$ (from $s$), so $2n - r$.

Therefore,
- $\dim N(A) = n - r$
- $\dim N([A \ A]) = 2n - r$

---

## Question 4

**4 (3+4+5=12 pts.)**

Suppose $A$ is a $5 \times 3$ matrix and $Ax$ is never zero (except when $x$ is the zero vector).

### (a) What can you say about the columns of $A$?

 
If $Ax = 0$ only when $x = 0$, then the columns of $A$ are linearly independent.

 
1. $Ax = 0$ has only the trivial solution $x = 0$.
2. This means the nullspace of $A$ is $\\{0\\}$.
3. Therefore, the columns of $A$ are linearly independent (see notes/Elimination-matrices.ipynb and notes/Linear Transformations.ipynb).

Therefore,
The columns of $A$ are linearly independent.


---

### (b) Show that $A^{\mathrm{T}}Ax$ is also never zero (except when $x=0$) by explaining this key step:

If $A^{\mathrm{T}}Ax = 0$ then obviously $x^{\mathrm{T}}A^{\mathrm{T}}Ax = 0$ and then (WHY?) $Ax = 0$.

 
If $A^{\mathrm{T}}Ax = 0$, then $x^{\mathrm{T}}A^{\mathrm{T}}Ax = (Ax)^{\mathrm{T}}(Ax) = \|Ax\|^2 = 0$, so $Ax = 0$, which only happens when $x = 0$.

 
1. If $A^{\mathrm{T}}Ax = 0$, then $x^{\mathrm{T}}A^{\mathrm{T}}Ax = 0$.
2. $x^{\mathrm{T}}A^{\mathrm{T}}Ax = (Ax)^{\mathrm{T}}(Ax) = \|Ax\|^2$ (see notes/Least-Square Fitting.ipynb).
3. $\|Ax\|^2 = 0$ implies $Ax = 0$.
4. By part (a), $Ax = 0$ only when $x = 0$.

Therefore,
$A^{\mathrm{T}}Ax = 0$ only when $x = 0$.

---

### (c) We now know that $A^{\mathrm{T}}A$ is invertible. Explain why $B = (A^{\mathrm{T}}A)^{-1}A^{\mathrm{T}}$ is a one-sided inverse of $A$ (which side of $A$?). $B$ is NOT a 2-sided inverse of $A$ (explain why not).

 
$B$ is a left inverse of $A$ because $B A = I_3$, but $A B \neq I_5$ since $A$ is not square or surjective onto $\mathbb{R}^5$.

 
1. $B = (A^{\mathrm{T}}A)^{-1}A^{\mathrm{T}}$.
2. $B A = (A^{\mathrm{T}}A)^{-1}A^{\mathrm{T}}A = (A^{\mathrm{T}}A)^{-1}(A^{\mathrm{T}}A) = I_3$.
3. So $B$ is a left inverse: $B A = I$ on $\mathbb{R}^3$.
4. $A B = A (A^{\mathrm{T}}A)^{-1}A^{\mathrm{T}}$ is a $5 \times 5$ matrix, but it is a projection onto the column space of $A$, not the identity (see notes/Least-Square Fitting.ipynb and notes/Projections.ipynb).
5. Therefore, $B$ is not a two-sided inverse.

Therefore,
$B$ is a left inverse of $A$ ($B A = I$), but not a right inverse ($A B \neq I$).

---

## Question 5

**5 (5+5=10 pts.)**

If $A$ is $3 \times 3$ symmetric positive definite, then $A q_i = \lambda_i q_i$ with positive eigenvalues and orthonormal eigenvectors $q_i$.

Suppose $x = c_1 q_1 + c_2 q_2 + c_3 q_3$.

### (a) Compute $x^{\mathrm{T}}x$ and also $x^{\mathrm{T}}Ax$ in terms of the $c$'s and $\lambda$'s.

 
Expressing $x$ in the orthonormal eigenbasis, $x^T x$ is the sum of squares of the $c_i$, and $x^T A x$ is the sum of $\lambda_i c_i^2$.

 
1. $x = c_1 q_1 + c_2 q_2 + c_3 q_3$ with $q_i$ orthonormal.
2. $x^T x = (c_1 q_1 + c_2 q_2 + c_3 q_3)^T (c_1 q_1 + c_2 q_2 + c_3 q_3)$
3. By orthonormality, $q_i^T q_j = \delta_{ij}$, so cross terms vanish.
4. $x^T x = c_1^2 + c_2^2 + c_3^2$
5. $x^T A x = (c_1 q_1 + c_2 q_2 + c_3 q_3)^T A (c_1 q_1 + c_2 q_2 + c_3 q_3)$
6. $A q_i = \lambda_i q_i$, so $A x = c_1 \lambda_1 q_1 + c_2 \lambda_2 q_2 + c_3 \lambda_3 q_3$
7. $x^T A x = (c_1 q_1 + c_2 q_2 + c_3 q_3)^T (c_1 \lambda_1 q_1 + c_2 \lambda_2 q_2 + c_3 \lambda_3 q_3)$
8. Again, by orthonormality, only diagonal terms remain:
   $x^T A x = c_1^2 \lambda_1 + c_2^2 \lambda_2 + c_3^2 \lambda_3$

Therefore,
- $x^T x = c_1^2 + c_2^2 + c_3^2$
- $x^T A x = c_1^2 \lambda_1 + c_2^2 \lambda_2 + c_3^2 \lambda_3$

---

### (b) Looking at the ratio $x^{\mathrm{T}}Ax$ in part (a) divided by $x^{\mathrm{T}}x$ in part (a), what $c$'s would make that ratio as large as possible? You can assume $\lambda_1 < \lambda_2 < \ldots < \lambda_n$. Conclusion: the ratio $x^{\mathrm{T}}Ax / x^{\mathrm{T}}x$ is a maximum when $x$ is \_\_\_\_\_\_\_\_\_\_.

 
The ratio is maximized when all of $x$ is in the direction of the eigenvector with the largest eigenvalue.

 
1. The ratio is $\frac{x^T A x}{x^T x} = \frac{c_1^2 \lambda_1 + c_2^2 \lambda_2 + c_3^2 \lambda_3}{c_1^2 + c_2^2 + c_3^2}$.
2. This is a weighted average of the $\lambda_i$'s, weighted by $c_i^2$.
3. The maximum occurs when all the weight is on the largest $\lambda_i$ (i.e., $x$ is a multiple of $q_3$ if $\lambda_3$ is largest).
4. So, set $c_3 \neq 0$, $c_1 = c_2 = 0$.

Therefore,
The ratio $x^T A x / x^T x$ is maximized when $x$ is in the direction of the eigenvector with the largest eigenvalue (i.e., $x$ is a multiple of $q_3$ if $\lambda_3$ is the largest).

---

## Question 6

**6 (4+4+4=12 pts.)**

### (a) Find a linear combination $w$ of the linearly independent vectors $v$ and $u$ that is perpendicular to $u$.

 
We want $w = v + \alpha u$ such that $w$ is perpendicular to $u$.

 
1. $w = v + \alpha u$.
2. $w^T u = 0$ (perpendicularity condition).
3. $w^T u = v^T u + \alpha u^T u = 0$.
4. Solve for $\alpha$: $\alpha = -\frac{v^T u}{u^T u}$.

Therefore,
A linear combination is $w = v - \frac{v^T u}{u^T u} u$.

---

### (b) For the 2-column matrix $A = [u \ v]$, find $Q$ (orthonormal columns) and $R$ (2 by 2 upper triangular) so that $A = QR$.

 
This is the Gram-Schmidt process: $Q$ has orthonormal columns, $R$ is upper triangular.

 
1. Let $q_1 = \frac{u}{\|u\|}$.
2. Compute $w = v - \frac{v^T u}{u^T u} u$ (from part (a)).
3. $q_2 = \frac{w}{\|w\|}$.
4. $Q = [q_1 \ q_2]$.
5. $R$ is $2 \times 2$ upper triangular:
   - $R_{11} = \|u\|$
   - $R_{12} = q_1^T v$
   - $R_{22} = \|w\|$
   - $R_{21} = 0$
6. $A = QR$ with $Q$ as above and $R = \begin{bmatrix} \|u\| & q_1^T v \\ 0 & \|w\| \end{bmatrix}$

Therefore,
- $Q = [q_1 \ q_2]$ with $q_1 = \frac{u}{\|u\|}$, $q_2 = \frac{v - \frac{v^T u}{u^T u} u}{\|v - \frac{v^T u}{u^T u} u\|}$
- $R = \begin{bmatrix} \|u\| & q_1^T v \\ 0 & \|w\| \end{bmatrix}$

---

### (c) In terms of $Q$ only, using $A = QR$, find the projection matrix $P$ onto the plane spanned by $u$ and $v$.

 
The projection matrix onto the column space of $Q$ (with orthonormal columns) is $P = Q Q^T$.

 
1. $Q$ has orthonormal columns spanning the same space as $u$ and $v$.
2. The projection matrix onto the column space of $Q$ is $P = Q Q^T$ (see notes/Projections.ipynb).

Therefore,
$P = Q Q^T$.

---

## Question 7

**7 (4+3+4=11 pts.)**

### (a) Find the eigenvalues of
$$
C = \begin{bmatrix} 0 & 0 & 0 & 1 \\ 1 & 0 & 0 & 0 \\ 0 & 1 & 0 & 0 \\ 0 & 0 & 1 & 0 \end{bmatrix} \quad \text{and} \quad C^2 = \begin{bmatrix} 0 & 0 & 1 & 0 \\ 0 & 0 & 0 & 1 \\ 1 & 0 & 0 & 0 \\ 0 & 1 & 0 & 0 \end{bmatrix}.
$$

 
$C$ is a permutation matrix representing a 4-cycle. Its eigenvalues are the 4th roots of unity. $C^2$ is a permutation matrix representing two 2-cycles.

 
1. $C$ cycles the basis vectors: $e_1 \to e_2 \to e_3 \to e_4 \to e_1$.
2. The characteristic polynomial of $C$ is $\lambda^4 - 1 = 0$.
3. The eigenvalues of $C$ are the 4th roots of unity: $1, -1, i, -i$.
4. $C^2$ cycles $e_1 \to e_3 \to e_1$ and $e_2 \to e_4 \to e_2$ (two 2-cycles).
5. The characteristic polynomial of $C^2$ is $(\lambda^2 - 1)^2 = 0$.
6. The eigenvalues of $C^2$ are $1$ (multiplicity 2), $-1$ (multiplicity 2).

Therefore,
- Eigenvalues of $C$: $1, -1, i, -i$
- Eigenvalues of $C^2$: $1$ (twice), $-1$ (twice)

---

### (b) Those are both permutation matrices. What are their inverses $C^{-1}$ and $(C^2)^{-1}$?

 
The inverse of a permutation matrix is its transpose. For a cycle, the inverse cycles in the opposite direction.

 
1. $C$ is a 4-cycle: $e_1 \to e_2 \to e_3 \to e_4 \to e_1$.
2. $C^{-1}$ cycles in the reverse direction: $e_1 \to e_4 \to e_3 \to e_2 \to e_1$.
3. $C^{-1} = C^3$ (since $C^4 = I$).
4. $(C^2)^{-1} = C^2$ (since $(C^2)^2 = I$).
5. Alternatively, the inverse of a permutation matrix is its transpose.

Therefore,
- $C^{-1} = C^3 = C^T$
- $(C^2)^{-1} = C^2 = (C^2)^T$

---

### (c) Find the determinants of $C$ and $C+I$ and $C+2I$.

 
The determinant of a permutation matrix is the sign of the permutation. The determinant of $C + kI$ is the product of its eigenvalues shifted by $k$.

 
1. $C$ is a 4-cycle, which is an odd permutation, so $\det C = -1$.
2. The eigenvalues of $C$ are $1, -1, i, -i$.
3. $\det(C + I) = (1+1)(-1+1)(i+1)(-i+1) = 2 \times 0 \times (1+i) \times (1-i) = 0$
4. $\det(C + 2I) = (1+2)(-1+2)(i+2)(-i+2) = 3 \times 1 \times (2+i) \times (2-i) = 3 \times 1 \times (4 + 0) = 12$

Therefore,
- $\det C = -1$
- $\det(C + I) = 0$
- $\det(C + 2I) = 12$

---

## Question 8

**8 (4+3+4=11 pts.)**

Suppose a rectangular matrix $A$ has independent columns.

### (a) How do you find the best least squares solution $\widehat{x}$ to $Ax = b$? By taking those steps, give a formula (letters not numbers) for $\widehat{x}$ and also for $p = A\widehat{x}$.

 
The least squares solution $\widehat{x}$ minimizes $\|Ax - b\|^2$. For independent columns, the normal equations $A^T A \widehat{x} = A^T b$ have a unique solution.

 
1. Set up the normal equations: $A^T A \widehat{x} = A^T b$.
2. Since $A$ has independent columns, $A^T A$ is invertible.
3. Solve for $\widehat{x}$: $\widehat{x} = (A^T A)^{-1} A^T b$.
4. The projection $p = A \widehat{x}$.

Therefore,
- $\widehat{x} = (A^T A)^{-1} A^T b$
- $p = A \widehat{x}$

---

### (b) The projection $p$ is in which fundamental subspace associated with $A$? The error vector $e = b - p$ is in which fundamental subspace?

 
The projection $p$ is in the column space of $A$. The error $e$ is in the left nullspace of $A$ (the orthogonal complement of the column space).

 
1. $p = A \widehat{x}$ is a linear combination of the columns of $A$, so $p \in C(A)$.
2. The error $e = b - p$ is orthogonal to every column of $A$, so $A^T e = 0$.
3. Therefore, $e$ is in the left nullspace $N(A^T)$.

Therefore,
- $p$ is in the column space $C(A)$
- $e$ is in the left nullspace $N(A^T)$

---

### (c) Find by any method the projection matrix $P$ onto the column space of $A$:
$$
A = \begin{bmatrix} 1 & 0 \\ 3 & 0 \\ 0 & -1 \\ 0 & -3 \end{bmatrix}
$$

The projection matrix onto the column space of $A$ is $P = A (A^T A)^{-1} A^T$.

1. Compute $A^T A$:
   $$
   A^T A = \begin{bmatrix} 1 & 3 & 0 & 0 \\ 0 & 0 & -1 & -3 \end{bmatrix} \begin{bmatrix} 1 & 0 \\ 3 & 0 \\ 0 & -1 \\ 0 & -3 \end{bmatrix} = \begin{bmatrix} 1^2 + 3^2 & 0 \\ 0 & 1^2 + 3^2 \end{bmatrix} = \begin{bmatrix} 10 & 0 \\ 0 & 10 \end{bmatrix}
   $$
2. $A^T A$ is diagonal, so $(A^T A)^{-1} = \begin{bmatrix} 1/10 & 0 \\ 0 & 1/10 \end{bmatrix}$
3. $P = A (A^T A)^{-1} A^T$
4. Compute $A (A^T A)^{-1}$:
   $$
   A (A^T A)^{-1} = \begin{bmatrix} 1/10 & 0 \\ 3/10 & 0 \\ 0 & -1/10 \\ 0 & -3/10 \end{bmatrix}
   $$
5. $P = A (A^T A)^{-1} A^T =$
   $$
   \begin{bmatrix} 1/10 & 0 \\ 3/10 & 0 \\ 0 & -1/10 \\ 0 & -3/10 \end{bmatrix} \begin{bmatrix} 1 & 3 & 0 & 0 \\ 0 & 0 & -1 & -3 \end{bmatrix} =
   $$
   $$
   = \begin{bmatrix}
   (1/10) \cdot 1 & (1/10) \cdot 3 & 0 & 0 \\
   (3/10) \cdot 1 & (3/10) \cdot 3 & 0 & 0 \\
   0 & 0 & (-1/10) \cdot (-1) & (-1/10) \cdot (-3) \\
   0 & 0 & (-3/10) \cdot (-1) & (-3/10) \cdot (-3)
   \end{bmatrix}
   $$
   $$
   = \begin{bmatrix}
   1/10 & 3/10 & 0 & 0 \\
   3/10 & 9/10 & 0 & 0 \\
   0 & 0 & 1/10 & 3/10 \\
   0 & 0 & 3/10 & 9/10
   \end{bmatrix}
   $$

Therefore, the projection matrix is
$$
P = \begin{bmatrix}
1/10 & 3/10 & 0 & 0 \\
3/10 & 9/10 & 0 & 0 \\
0 & 0 & 1/10 & 3/10 \\
0 & 0 & 3/10 & 9/10
\end{bmatrix}
$$

---

## Question 9

**9 (3+4+4=11 pts.)**

This question is about the matrices with 3's on the main diagonal, 2's on the diagonal above, 1's on the diagonal below.

$$
A_1 = \begin{bmatrix} 3 \end{bmatrix} \quad A_2 = \begin{bmatrix} 3 & 2 \\ 1 & 3 \end{bmatrix} \quad A_3 = \begin{bmatrix} 3 & 2 & 0 \\ 1 & 3 & 2 \\ 0 & 1 & 3 \end{bmatrix} \quad A_n = \begin{bmatrix} 3 & 2 & 0 & 0 \\ 1 & 3 & 2 & 0 \\ 0 & 1 & 3 & \cdot \\ 0 & 0 & \cdot & \cdot \end{bmatrix}
$$

### (a) What are the determinants of $A_2$ and $A_3$?

Compute the determinants directly for $A_2$ and $A_3$.

1. $A_2 = \begin{bmatrix} 3 & 2 \\ 1 & 3 \end{bmatrix}$
   $$
   \det(A_2) = 3 \cdot 3 - 1 \cdot 2 = 9 - 2 = 7
   $$
2. $A_3 = \begin{bmatrix} 3 & 2 & 0 \\ 1 & 3 & 2 \\ 0 & 1 & 3 \end{bmatrix}$
   Expand along the first row:
   $$
   \det(A_3) = 3 \begin{vmatrix} 3 & 2 \\ 1 & 3 \end{vmatrix} - 2 \begin{vmatrix} 1 & 2 \\ 0 & 3 \end{vmatrix} + 0 \begin{vmatrix} 1 & 3 \\ 0 & 1 \end{vmatrix}
   $$
   $$
   = 3(9 - 2) - 2(1 \cdot 3 - 0 \cdot 2) + 0 = 3(7) - 2(3) = 21 - 6 = 15
   $$

Therefore, 
- $\det(A_2) = 7$
- $\det(A_3) = 15$

---

### (b) The determinant of $A_n$ is $D_n$. Use cofactors of row 1 and column 1 to find the numbers $a$ and $b$ in the recursive formula for $D_n$:
$$(*) \qquad \qquad D_n = a \, D_{n-1} + b \, D_{n-2} \, .$$

Expand $\det(A_n)$ along the first row to find the recurrence.

1. The first row of $A_n$ is $[3, 2, 0, \ldots, 0]$.
2. Expanding along the first row:
   $$
   D_n = 3 D_{n-1} - 2 \cdot 1 \cdot D_{n-2}
   $$
   (The $-2$ comes from the $2$ in the $(1,2)$ position and the $1$ in the $(2,1)$ position, with a negative sign from the cofactor expansion.)
3. So $a = 3$, $b = -2$.

Therefore, $D_n = 3 D_{n-1} - 2 D_{n-2}$, so $a = 3$, $b = -2$.

---

### (c) This equation $(*)$ is the same as
$$
\begin{bmatrix} D_n \\ D_{n-1} \end{bmatrix} = \begin{bmatrix} a & b \\ 1 & 0 \end{bmatrix} \begin{bmatrix} D_{n-1} \\ D_{n-2} \end{bmatrix} .
$$
From the eigenvalues of that matrix, how fast do the determinants $D_n$ grow? (If you didn't find $a$ and $b$, say how you would answer part (c) for any $a$ and $b$ ) For 1 point, find $D_5$.

The growth rate of $D_n$ is determined by the largest eigenvalue of the recurrence matrix.

1. The recurrence matrix is $M = \begin{bmatrix} 3 & -2 \\ 1 & 0 \end{bmatrix}$.
2. The characteristic polynomial is $\lambda^2 - 3\lambda + 2 = 0$.
3. The eigenvalues are $\lambda = 1, 2$.
4. So $D_n$ grows like $2^n$ for large $n$ (the largest eigenvalue dominates).
5. To find $D_5$, use the recurrence:
   - $D_1 = 3$
   - $D_2 = 7$
   - $D_3 = 15$
   - $D_4 = 3 \cdot 15 - 2 \cdot 7 = 45 - 14 = 31$
   - $D_5 = 3 \cdot 31 - 2 \cdot 15 = 93 - 30 = 63$

Therefore, 
- $D_n$ grows like $2^n$ for large $n$ (since $2$ is the largest eigenvalue).
- $D_5 = 63$

