# Exam 3 (solved)
Feb 9 2026
## Question 1

### (a) If a square matrix $A$ has all $n$ of its singular values equal to 1 in the SVD, what basic classes of matrices does $A$ belong to? (Singular, symmetric, orthogonal, positive definite or semidefinite, diagonal)

If all singular values of $A$ are $1$, then $A$ is an orthogonal matrix (or unitary, if complex). This is because the SVD of $A$ is $A = U \operatorname{diag}(1, \ldots, 1) V^T = U V^T$, and $U, V$ are orthogonal matrices, so $A$ is a product of orthogonal matrices, which is itself orthogonal. Orthogonal matrices have all singular values equal to $1$, and their inverse is their transpose. $A$ could also be diagonal if $U = V$ and $A$ is diagonal with $\operatorname{diag}(\pm 1, \ldots, \pm 1)$, but the key class is orthogonal.

**Step 1:** The singular values of $A$ are the entries of $\operatorname{diag}(\sigma_1, \ldots, \sigma_n)$ in the SVD $A = U \operatorname{diag}(\sigma_1, \ldots, \sigma_n) V^T$.

**Step 2:** If all $\sigma_i = 1$, then $A = U V^T$.

**Step 3:** $U$ and $V$ are orthogonal, so $A$ is orthogonal (since the product of orthogonal matrices is orthogonal).

**Step 4:** $A$ could also be diagonal if $U = V$ and $A$ is diagonal with all entries $\pm 1$, but the main class is orthogonal.

**Conclusion:** $A$ is orthogonal (and possibly also diagonal if $U = V$). $A$ is not necessarily symmetric, positive definite, or positive semidefinite, and is not singular.

---

### (b) Suppose the (orthonormal) columns of $H$ are eigenvectors of $B$:

$$ H = \frac{1}{2} \begin{bmatrix} 1 & 1 & -1 & -1 \\ 1 & -1 & -1 & 1 \\ 1 & 1 & 1 & 1 \\ 1 & -1 & 1 & -1 \end{bmatrix} \qquad H^{-1} = H^{\mathrm{T}} $$

The eigenvalues of $B$ are $\lambda = 0, 1, 2, 3$. Write $B$ as the product of 3 specific matrices. Write $C = (B + I)^{-1}$ as the product of 3 matrices.

Since $H$ is orthogonal and its columns are eigenvectors of $B$, $B$ is diagonalizable as $B = H \Lambda H^T$, where $\Lambda = \text{diag}(0, 1, 2, 3)$. This is the spectral decomposition.

**Step 1:** $B$ is diagonalizable with $B = H \Lambda H^T$, where $\Lambda = \text{diag}(0, 1, 2, 3)$.

**Step 2:** $H$ is orthogonal, so $H^{-1} = H^T$.

**Step 3:** $B$ as a product of 3 matrices: $B = H \Lambda H^T$.

**Step 4:** $C = (B + I)^{-1} = H (\Lambda + I) H^T)^{-1} = H (\Lambda + I)^{-1} H^T$ (since $H$ is orthogonal, $H^T = H^{-1}$ and $H$ commutes with diagonal matrices in this form).

**Step 5:** $\Lambda + I = \text{diag}(1, 2, 3, 4)$, so $(\Lambda + I)^{-1} = \text{diag}(1, 1/2, 1/3, 1/4)$.

**Conclusion:**
- $B = H \Lambda H^T$ with $\Lambda = \text{diag}(0, 1, 2, 3)$.
- $C = (B + I)^{-1} = H \text{diag}(1, 1/2, 1/3, 1/4) H^T$.

---

### (c) Using the list in question (a), which basic classes of matrices do $B$ and $C$ belong to? (Separate question for $B$ and $C$)


$B$ is symmetric (since $B = H \Lambda H^T$ with $H$ orthogonal and $\Lambda$ diagonal and real), and diagonalizable. $B$ is not orthogonal (its eigenvalues are not all $\pm 1$), not positive definite (it has a zero eigenvalue), and is **singular** (since $\det B = 0$ or equivalently, $0$ is an eigenvalue). Furthermore, since all eigenvalues are $0,1,2,3$ (all $\geq 0$), $B$ is **positive semidefinite**. $B$ is not diagonal in the standard basis, but is diagonalizable.

$C$ is also symmetric (since $C = H D H^T$ with $D$ diagonal and real), and all its eigenvalues are positive ($1, 1/2, 1/3, 1/4$), so $C$ is positive definite. $C$ is not orthogonal, not diagonal in the standard basis, and not singular.


**Step 1:** $B$ is symmetric and diagonalizable, but not orthogonal, not positive definite, and not diagonal in the standard basis. $B$ is **singular** and **positive semidefinite**.

**Step 2:** $C$ is symmetric and positive definite (all eigenvalues $> 0$), but not orthogonal, not diagonal in the standard basis.

**Conclusion:**
- $B$ is symmetric, diagonalizable, **singular**, and **positive semidefinite**.
- $C$ is symmetric and positive definite.

## Question 2

### (a) Find three eigenvalues of $A$, and an eigenvector matrix $S$:

Let's find the eigenvalues of
$$
A = \begin{bmatrix} -1 & 2 & 4 \\ 0 & 0 & 5 \\ 0 & 0 & 1 \end{bmatrix}
$$

**Step 1:** $A$ is upper triangular, so its eigenvalues are the diagonal entries: $-1, 0, 1$.

**Step 2:** To find an eigenvector matrix $S$, we solve $(A - \lambda I)x = 0$ for each eigenvalue.

- For $\lambda = -1$:
  $A + I = \begin{bmatrix} 0 & 2 & 4 \\ 0 & 1 & 5 \\ 0 & 0 & 2 \end{bmatrix}$
  The first row gives $2x_2 + 4x_3 = 0$, the second $x_2 + 5x_3 = 0$, the third $2x_3 = 0$ so $x_3 = 0$, $x_2 = 0$, $x_1$ free. So eigenvector is $[1, 0, 0]^T$.

- For $\lambda = 0$:
  $A - 0I = A$. The third row: $x_3 = 0$. Second row: $5x_3 = 0$ so $x_3 = 0$. First row: $-x_1 + 2x_2 = 0$ so $x_1 = 2x_2$. So eigenvector is $[2, 1, 0]^T$.

- For $\lambda = 1$:
  $A - I = \begin{bmatrix} -2 & 2 & 4 \\ 0 & -1 & 5 \\ 0 & 0 & 0 \end{bmatrix}$
  Third row: $0 = 0$ (free). Second row: $-y_2 + 5y_3 = 0 \implies y_2 = 5y_3$. First row: $-2y_1 + 2y_2 + 4y_3 = 0$. Substitute $y_2 = 5y_3$:
  $-2y_1 + 10y_3 + 4y_3 = 0 \implies -2y_1 + 14y_3 = 0 \implies y_1 = 7y_3$. So eigenvector is $[7, 5, 1]^T$.

**Conclusion:** The eigenvalues are $-1, 0, 1$ and an eigenvector matrix is
$$
S = \begin{bmatrix} 1 & 2 & 7 \\ 0 & 1 & 5 \\ 0 & 0 & 1 \end{bmatrix}
$$

---

### (b) Explain why $A^{1001} = A$. Is $A^{1000} = I$? Find the three diagonal entries of $e^{At}$.

Because $A$ is upper triangular with eigenvalues $-1, 0, 1$, and its eigenvector matrix $S$ is invertible, $A$ is diagonalizable: $A = S \Lambda S^{-1}$ with $\Lambda = \text{diag}(-1, 0, 1)$. Then $A^k = S \Lambda^k S^{-1}$.

**Step 1:** $\Lambda^k = \text{diag}((-1)^k, 0^k, 1^k)$. For $k \geq 1$, $0^k = 0$.

**Step 2:** $A^{1001} = S \Lambda^{1001} S^{-1}$. $(-1)^{1001} = -1$, $0^{1001} = 0$, $1^{1001} = 1$. So $\Lambda^{1001} = \Lambda$.

**Step 3:** Therefore $A^{1001} = S \Lambda S^{-1} = A$.

**Step 4:** $A^{1000} = S \Lambda^{1000} S^{-1}$. $(-1)^{1000} = 1$, $0^{1000} = 0$, $1^{1000} = 1$. So $\Lambda^{1000} = \text{diag}(1, 0, 1)$. This is not the identity matrix, so $A^{1000} \neq I$.

**Step 5:** The diagonal entries of $e^{At}$ are $e^{-t}, 1, e^{t}$, since $e^{At} = S e^{\Lambda t} S^{-1}$ and $e^{\Lambda t} = \text{diag}(e^{-t}, 1, e^{t})$.

**Conclusion:**
- $A^{1001} = A$.
- $A^{1000} \neq I$.
- The diagonal entries of $e^{At}$ are $e^{-t}, 1, e^{t}$.

---

### (c) The matrix $A^{\mathrm{T}} A$ (for the same $A$) is

$$
A^{\mathrm{T}} A = \begin{bmatrix} 1 & -2 & -4 \\ -2 & 4 & 8 \\ -4 & 8 & 42 \end{bmatrix}
$$

How many eigenvalues of $A^{\mathrm{T}} A$ are positive? zero? negative? (Don't compute them but explain your answer.) Does $A^{\mathrm{T}} A$ have the same eigenvectors as $A$?

$A^{\mathrm{T}} A$ is always symmetric and positive semidefinite (see notes on SVD and least squares). Its eigenvalues are the squares of the singular values of $A$, so they are all $\geq 0$.

**Step 1:** $A$ is $3 \times 3$ and has rank 2 (since the second and third rows are linearly independent, but the first row is a combination of the others), so $A^{\mathrm{T}} A$ has rank 2.

**Step 2:** Therefore, $A^{\mathrm{T}} A$ has two positive eigenvalues and one zero eigenvalue.

**Step 3:** $A^{\mathrm{T}} A$ cannot have negative eigenvalues because it is positive semidefinite.

**Step 4:** $A^{\mathrm{T}} A$ does not generally have the same eigenvectors as $A$ (see notes on SVD and diagonalization: the eigenvectors of $A$ and $A^{\mathrm{T}} A$ are generally different unless $A$ is normal or symmetric).

**Conclusion:**
- $A^{\mathrm{T}} A$ has two positive eigenvalues and one zero eigenvalue; none are negative.
- $A^{\mathrm{T}} A$ does not have the same eigenvectors as $A$ in general.

---

## Question 3

### (a) What are the eigenvalues and eigenvectors of $A^{-1}$? Prove that your answer is correct.

If $A$ has orthonormal eigenvectors $q_1, \dots, q_n$ and positive eigenvalues $\lambda_1, \dots, \lambda_n$, then $A^{-1}$ has the same eigenvectors $q_j$, but its eigenvalues are $1/\lambda_j$. This follows from the definition of eigenvalues and the invertibility of $A$ (since all $\lambda_j > 0$).

1. By definition, $A q_j = \lambda_j q_j$ for each $j$.
2. Since $A$ is invertible (all $\lambda_j > 0$), we can apply $A^{-1}$ to both sides: $A^{-1} (A q_j) = A^{-1} (\lambda_j q_j)$.
3. This gives $q_j = \lambda_j A^{-1} q_j$, so $A^{-1} q_j = (1/\lambda_j) q_j$.
4. Therefore, $q_j$ is an eigenvector of $A^{-1}$ with eigenvalue $1/\lambda_j$.

Therefore the eigenvalues of $A^{-1}$ are $1/\lambda_1, \dots, 1/\lambda_n$, and the eigenvectors are $q_1, \dots, q_n$ (the same as for $A$).

---

### (b) Any vector $b$ is a combination of the eigenvectors: $b = c_1 q_1 + \dots + c_n q_n$. What is a quick formula for $c_1$ using orthogonality of the $q$'s?

Because the $q_j$ are orthonormal, the coefficient $c_1$ is simply the dot product $q_1^T b$ (or $q_1 \cdot b$). This is a direct result of the orthonormality property.

1. Write $b = \sum_{j=1}^n c_j q_j$.
2. Take the dot product of both sides with $q_1$: $q_1^T b = \sum_{j=1}^n c_j q_1^T q_j$.
3. Since the $q_j$ are orthonormal, $q_1^T q_j = 0$ for $j \neq 1$ and $q_1^T q_1 = 1$.
4. Therefore, $q_1^T b = c_1$.

Therefore $c_1 = q_1^T b$.

---

### (c) The solution to $Ax = b$ is also a combination of the eigenvectors: $A^{-1}b = d_1 q_1 + \dots + d_n q_n$. What is a quick formula for $d_1$? You can use the $c$'s even if you didn't answer part (b).

The coefficient $d_1$ is $c_1/\lambda_1$, where $c_1$ is the coefficient of $q_1$ in $b$. This is because $A^{-1}$ acts on each eigenvector by scaling it by $1/\lambda_j$.

1. $b = \sum_{j=1}^n c_j q_j$.
2. $A^{-1} b = A^{-1} (\sum_{j=1}^n c_j q_j) = \sum_{j=1}^n c_j A^{-1} q_j$.
3. From part (a), $A^{-1} q_j = (1/\lambda_j) q_j$.
4. Therefore, $A^{-1} b = \sum_{j=1}^n (c_j/\lambda_j) q_j$.
5. So $d_1 = c_1/\lambda_1$.

Therefore $d_1 = c_1/\lambda_1$ (and in general $d_j = c_j/\lambda_j$).