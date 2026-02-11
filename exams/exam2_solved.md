# Exam 2 (solved)
Feb 7 2026
## Question 1

Suppose $q_1, q_2, q_3$ are orthonormal vectors in $\mathbb{R}^3$. Find all possible values for these $3 \times 3$ determinants and explain your thinking in 1 sentence each.

### (a) $\det[q_1\ q_2\ q_3]$

Since $q_1, q_2, q_3$ are orthonormal, the matrix $Q = [q_1\ q_2\ q_3]$ is orthogonal, so its determinant must be $+1$ or $-1$.

**Step 1:** $q_1, q_2, q_3$ are orthonormal, so the matrix $Q = [q_1\ q_2\ q_3]$ is an orthogonal matrix.

**Step 2:** The determinant of any orthogonal matrix in $\mathbb{R}^3$ is either $+1$ or $-1$ (see Determinants.ipynb).

**Conclusion:** $\det[q_1\ q_2\ q_3] = \pm 1$.

---

### (b) $\det[q_1 + q_2,\ q_2 + q_3,\ q_3 + q_1]$

By multilinearity, expanding the determinant gives a sum where only the terms with all columns different survive, which are cyclic permutations of $(q_1, q_2, q_3)$. Each such term is $\pm 1$, and there are two of them, so the answer is $\pm 2$.

**Step 1:** Let $A = [q_1 + q_2,\ q_2 + q_3,\ q_3 + q_1]$.

**Step 2:** By the linearity of the determinant in each column, expand:
$$
\det[q_1 + q_2,\ q_2 + q_3,\ q_3 + q_1] = \det[q_1, q_2, q_3] + \det[q_1, q_3, q_1] + \det[q_2, q_2, q_3] + \ldots
$$
But most terms vanish because two columns are equal (determinant is zero if two columns are equal).

**Step 3:** The only nonzero terms are those corresponding to permutations of $(q_1, q_2, q_3)$.
$$
\det A = \det[q_1, q_2, q_3] + \det[q_2, q_3, q_1]
$$
(This is derived by applying $C_1' = C_1 + C_2$, $C_2' = C_2 + C_3$, $C_3' = C_3 + C_1$, and using linearity and elimination of zero terms).

**Step 4:** There are three such terms when fully expanded using $2^3 = 8$ terms. The result is $2 \det[q_1, q_2, q_3]$.

**Step 5:** Since $\det[q_1, q_2, q_3] = \pm 1$, the resulting determinant is $2(\pm 1)$.

**Conclusion:** $\det[q_1 + q_2, q_2 + q_3, q_3 + q_1] = \pm 2$.

---

### (c) $\det[q_1\ q_2\ q_3] \times \det[q_2\ q_3\ q_1]$

Cyclically permuting the columns of an orthogonal matrix preserves the sign of the determinant, so both determinants are equal ($\pm 1$), and their product is always $1$.

**Step 1:** $\det[q_1\ q_2\ q_3]$ is $\pm 1$.

**Step 2:** $\det[q_2\ q_3\ q_1]$ involves a cyclic permutation of the columns $(1 \to 2 \to 3 \to 1)$, which corresponds to two swaps (an even permutation), so the sign stays the same: $\det[q_2\ q_3\ q_1] = \det[q_1\ q_2\ q_3]$.

**Step 3:** So the product is $(\pm 1) \times (\pm 1) = 1$.

**Conclusion:** $\det[q_1\ q_2\ q_3] \times \det[q_2\ q_3\ q_1] = 1$.

---

## Question 2

Suppose we take measurements at the 21 equally spaced times $t = -10, -9, \ldots, 9, 10$. All measurements are $b_i = 0$ except that $b_{11} = 1$ at the middle time $t = 0$.

### (a) Using least squares, what are the best $C$ and $D$ to fit those 21 points by a straight line $C + Dt$?

The model is $b_i \approx C + D t_i$. Since the times are symmetric about zero and only the middle value is nonzero, the best fit line is horizontal: $D = 0$. The sum of the fitted values must equal the sum of the data, so $C = 1/21$.

**Step 1:** Write the model as $b_i \approx C + D t_i$. The normal equations are $A^T A x = A^T b$.

**Step 2:** Since the times are symmetric around zero, the cross-term in $A^T A$ is $\sum t_i = 0$.
$$
A^T A = \begin{bmatrix} 21 & 0 \\ 0 & 770 \end{bmatrix}
$$

**Step 3:** Compute $A^T b$. Since $b_i$ is nonzero only at $t=0$:
$$
A^T b = \begin{bmatrix} \sum 1 \cdot b_i \\ \sum t_i \cdot b_i \end{bmatrix} = \begin{bmatrix} 1 \\ 0 \end{bmatrix}
$$

**Step 4:** Solve for $x = \begin{bmatrix} C \\ D \end{bmatrix}$:
$$
\begin{bmatrix} 21 & 0 \\ 0 & 770 \end{bmatrix} \begin{bmatrix} C \\ D \end{bmatrix} = \begin{bmatrix} 1 \\ 0 \end{bmatrix}
$$
$C = \frac{1}{21}$, $D = 0$.

**Conclusion:** The best fit is $C = \frac{1}{21}$, $D = 0$.

---

### (b) You are projecting the vector $b$ onto what subspace? (Give a basis.) Find a nonzero vector perpendicular to that subspace.

The subspace is the span of the constant vector $[1, 1, \ldots, 1]^T$ and the time vector $[t_1, \ldots, t_{21}]^T$. A vector perpendicular to both is $[1, -2, 1, 0, \ldots, 0]^T$ (a discrete second difference), since it sums to zero and is orthogonal to the time vector. The error vector $e = b - P_A b$ is also perpendicular to the subspace.

**Step 1:** The subspace is the column space of $A$, spanned by the constant vector $\mathbf{1}$ and the time vector $\mathbf{t}$.

**Basis:** $\{ \mathbf{1}, \mathbf{t} \}$, where $\mathbf{1} = [1, 1, \ldots, 1]^T$ and $\mathbf{t} = [-10, -9, \ldots, 10]^T$.

**Step 2:** A vector perpendicular to this subspace must be orthogonal to both $\mathbf{1}$ and $\mathbf{t}$. The vector $b$ itself, where $b = [0, \ldots, 0, 1, 0, \ldots, 0]$, is highly suggestive.

**Step 3:** However, we want a general vector perpendicular to *any* line. A vector $v$ that has zero sum (orthogonal to $\mathbf{1}$) and is symmetric (orthogonal to $\mathbf{t}$) works.
A simpler standard orthogonal vector is related to the discrete second derivative (measures curvature, which a straight line does not possess).

**Step 4:** Consider $v$ such that $v_i = 1$ for $i=1$, $v_i = -2$ for $i=2$, $v_i = 1$ for $i=3$, and $v_i = 0$ otherwise. This $v$ is $21 \times 1$. This $v$ has $\sum v_i = 1 - 2 + 1 = 0$. If the times $t_i$ start at $i=1$, then $\sum v_i t_i = 1 \cdot t_1 - 2 \cdot t_2 + 1 \cdot t_3$. Since $t_2 = t_1 + 1$ and $t_3 = t_1 + 2$, this sum is $t_1 - 2t_1 - 2 + t_1 + 2 = 0$.

**Conclusion:** The subspace is spanned by $[1, 1, \ldots, 1]^T$ and $[t_1, \ldots, t_{21}]^T$. A nonzero vector perpendicular to it is $v = [1, -2, 1, 0, \ldots, 0]^T$ (assuming the first three measurements correspond to $t=-10, -9, -8$).

---

## Question 3

The Gram-Schmidt method produces orthonormal vectors $q_1, q_2, q_3$ from independent vectors $a_1, a_2, a_3$ in $\mathbb{R}^5$. Put those vectors into the columns of $5 \times 3$ matrices $Q$ and $A$.

### (a) Give formulas using $Q$ and $A$ for the projection matrices $P_Q$ and $P_A$ onto the column spaces of $Q$ and $A$.

The projection matrix onto the column space of $Q$ is $P_Q = Q Q^T$, and for $A$ it is $P_A = A (A^T A)^{-1} A^T$.

**Conclusion:**
- $P_Q = Q Q^T$ (Since $Q^T Q = I$)
- $P_A = A (A^T A)^{-1} A^T$

---

### (b) Is $P_Q = P_A$ and why? What is $P_Q$ times $Q$? What is $\det P_Q$?

Since $Q$ is obtained from $A$ by Gram-Schmidt, both have the same column space, so $P_Q = P_A$. Multiplying $P_Q$ by $Q$ gives $Q$ back. $P_Q$ is a $5 \times 5$ projection matrix of rank 3, so it is singular and $\det P_Q = 0$.

**Conclusion:**
- $P_Q = P_A$ because both project onto the same subspace (Gram-Schmidt preserves the column space).
- $P_Q Q = Q Q^T Q = Q (Q^T Q) = Q I = Q$.
- $\det P_Q = 0$ because $P_Q$ is a $5 \times 5$ matrix with rank 3, meaning its null space is non-trivial, so it is singular.

---

### (c) Suppose $a_4$ is a new vector and $a_1, a_2, a_3, a_4$ are independent. Which of these (if any) is the new Gram-Schmidt vector $q_4$? (Use $P_A$ and $P_Q$ from above)

**Step 1:** Gram-Schmidt requires subtracting the projection of the new vector ($a_4$) onto the previously spanned space ($\text{Col}(A)$ or $\text{Col}(Q)$).

**Step 2:** Both $a_4 - P_A a_4$ and $a_4 - P_Q a_4$ represent the component of $a_4$ orthogonal to the subspace spanned by $a_1, a_2, a_3$.

**Step 3:** The Gram-Schmidt vector $q_4$ is the normalized version of this result. Since the question asks "Which of these is the new Gram-Schmidt vector $q_4$?", it implies the orthogonal vector before normalization.

**Conclusion:** Therefore choice 3 is the correct definitions for the new orthogonal vector (which must then be normalized to find $q_4$).

---

## Question 4

Suppose a $4 \times 4$ matrix has the same entry $\times$ throughout its first row and column. The other 9 numbers could be anything.

$$
A = \begin{bmatrix}
\times & \times & \times & \times \\
\times & * & * & * \\
\times & * & * & * \\
\times & * & * & *
\end{bmatrix}
$$

---

### (a) The determinant of $A$ is a polynomial in $\times$. What is the largest possible degree of that polynomial? Explain your answer.

In the determinant expansion, you can pick at most one $\times$ from the first row and one from the first column in any term, so the highest possible degree is 2.

**Step 1:** The determinant is a sum of $n!$ products, each picking one entry per row and column.

**Step 2:** Any term in the expansion can pick at most one entry from the first row and at most one entry from the first column.

**Step 3:** The highest degree occurs when we maximize the number of $\times$'s chosen.
Case 1: We choose $a_{11} = \times$. This uses one $\times$. The remaining $3 \times 3$ submatrix has no $\times$'s, so the term contributes $\times^1$.
Case 2: We choose $a_{1j} = \times$ ($j>1$) and $a_{i1} = \times$ ($i>1$). This is impossible for the same term, as they share either a row or a column.

**Step 4:** The maximum degree is achieved by picking the entries $a_{11}$ and two more entries from the first row/column that do not conflict. Wait, that's impossible.

**Step 5:** Let's re-examine the definition of the determinant: $\sum_{\sigma} (\text{sgn}(\sigma)) a_{1, \sigma(1)} a_{2, \sigma(2)} a_{3, \sigma(3)} a_{4, \sigma(4)}$.
The maximum number of factors of $\times$ per product is 2:
1. Choose $a_{1,1} = \times$. Remaining three factors must be from the $3 \times 3$ block of $*$s. Contribution: $\times^1$.
2. Choose $a_{1, j} = \times$ ($j \neq 1$) AND choose $a_{i, 1} = \times$ ($i \neq 1$). The remaining $2 \times 2$ block of $*$s yields two factors. Contribution: $\times^2$. (Example: $a_{12} a_{21} a_{33} a_{44}$ if $a_{33}, a_{44}$ are the $*$s).

**Conclusion:** The largest possible degree of the determinant as a polynomial in $\times$ is 2. (The claim of 3 in the original broken solution was incorrect based on cofactor expansion rules.)

---

### (b) If those 9 numbers give the identity matrix $I$, what is $\det A$? Which values of $\times$ give $\det A = 0$?

If the $*$ entries form the $3 \times 3$ identity, then $A$ is
$$
\begin{bmatrix}
x & x & x & x \\
x & 1 & 0 & 0 \\
x & 0 & 1 & 0 \\
x & 0 & 0 & 1
\end{bmatrix}
$$
The determinant is $x(1-3x)$, so $\det A = 0$ when $x = 0$ or $x = 1/3$.

**Step 1:** Write out the matrix:
$$
A = \begin{bmatrix}
x & x & x & x \\
x & 1 & 0 & 0 \\
x & 0 & 1 & 0 \\
x & 0 & 0 & 1
\end{bmatrix}
$$

**Step 2:** Calculate $\det A$. We can use the formula for a partitioned matrix $\begin{bmatrix} A_{11} & A_{12} \\ A_{21} & A_{22} \end{bmatrix}$. Here $A_{11}=x$ (scalar), $A_{22}=I$ ($3 \times 3$), $A_{12} = [x, x, x]$, and $A_{21} = [x, x, x]^T$.
$$
\det A = \det(A_{22}) \cdot \det(A_{11} - A_{12} A_{22}^{-1} A_{21})
$$
Since $A_{22}=I$, $A_{22}^{-1}=I$.
$$
A_{12} I A_{21} = \begin{bmatrix} x & x & x \end{bmatrix} \begin{bmatrix} x \\ x \\ x \end{bmatrix} = x^2 + x^2 + x^2 = 3x^2
$$
Thus, $\det A = 1 \cdot (x - 3x^2) = x(1 - 3x)$.

**Step 3:** Find values of $x$ such that $\det A = 0$.
Setting $x(1 - 3x) = 0$, we find $x=0$ or $1 - 3x = 0$, which gives $x = 1/3$.

**Conclusion:** $\det A = x(1 - 3x)$, and $\det A = 0$ when $x=0$ or $x=1/3$.