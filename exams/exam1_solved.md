
# MIT 18.06 Exam 1 (solved)
Feb 3 2026
## Question 1


### (a) Possible values for $m$, $n$, and rank $r$ of $A$

We have $Ax = \begin{bmatrix}1 \\ 0\end{bmatrix}$ has no solutions, and $Ax = \begin{bmatrix}1 \\ 1\end{bmatrix}$ has exactly one solution.

So, the right-hand side is a 2-vector, but the solution says $m=3$ (so the right-hand side should be 3-vectors). That means $A$ is $3 \times n$.

If $Ax = b$ has no solution for some $b$, $A$ can't be full rank (not all $b$ are in the column space), so $r < m$. But $Ax = b$ has exactly one solution for some $b$, so $A$ must have $r = n$ (so the nullspace is trivial). So $r = n < m$, so $n = r = 1$ or $2$, and $m = 3$.

So possible: $m=3$, $n=1$ or $2$, $r=n$.

---


### (b) All solutions to $Ax = 0$

If $r = n$, then the nullspace is just $x = 0$. So the only solution is $x = 0$.

---


### (c) Example of a matrix $A$ that fits the description

Let $A = \begin{bmatrix}1 & 0 \\ 0 & 1 \\ 1 & 1\end{bmatrix}$ (so $3 \times 2$, rank 2).

Check: $Ax = \begin{bmatrix}1 \\ 0 \\ 1\end{bmatrix}$, try $x = \begin{bmatrix}1 \\ 0\end{bmatrix}$, get $\begin{bmatrix}1 \\ 0 \\ 1\end{bmatrix}$, so that works. But $Ax = \begin{bmatrix}1 \\ 0 \\ 0\end{bmatrix}$, no solution (since third row is sum of first two, but right side doesn't match).

---

## Question 2

Given: The $3 \times 3$ matrix $A$ reduces to the identity matrix $I$ by the following row operations (in order):
- $E_{21}$: Subtract 4 times row 1 from row 2.
- $E_{31}$: Subtract 3 times row 1 from row 3.
- $E_{23}$: Subtract row 3 from row 2.

---

### (a) Write $A^{-1}$ in terms of the $E$'s and compute $A^{-1}$



#### Solution:
To get $A^{-1}$, since $E_{23} E_{31} E_{21} A = I$, $A^{-1} = E_{23} E_{31} E_{21}$.

$E_{21} = \begin{bmatrix}1 & 0 & 0 \\ -4 & 1 & 0 \\ 0 & 0 & 1\end{bmatrix}$
$E_{31} = \begin{bmatrix}1 & 0 & 0 \\ 0 & 1 & 0 \\ -3 & 0 & 1\end{bmatrix}$
$E_{23} = \begin{bmatrix}1 & 0 & 0 \\ 0 & 1 & -1 \\ 0 & 0 & 1\end{bmatrix}$

Multiply them in order:

First $E_{31} E_{21}$:
$\begin{bmatrix}1 & 0 & 0 \\ -4 & 1 & 0 \\ -3 & 0 & 1\end{bmatrix}$

Now $E_{23}$ times that:
Row 1: stays the same.
Row 2: $(-4,1,0) - (-3,0,1) = (-1,1,-1)$
Row 3: stays the same.

So $A^{-1} = \begin{bmatrix}1 & 0 & 0 \\ -1 & 1 & -1 \\ -3 & 0 & 1\end{bmatrix}$

---

### (b) What is the original matrix $A$?


#### Solution:
To get $A$, invert the $E$ matrices (add instead of subtract):
$E_{21}^{-1} = \begin{bmatrix}1 & 0 & 0 \\ 4 & 1 & 0 \\ 0 & 0 & 1\end{bmatrix}$
$E_{31}^{-1} = \begin{bmatrix}1 & 0 & 0 \\ 0 & 1 & 0 \\ 3 & 0 & 1\end{bmatrix}$
$E_{23}^{-1} = \begin{bmatrix}1 & 0 & 0 \\ 0 & 1 & 1 \\ 0 & 0 & 1\end{bmatrix}$

Multiply in order:
First $E_{31}^{-1} E_{23}^{-1}$:
Row 1: $(1,0,0)$
Row 2: $(0,1,1)$
Row 3: $(3,0,1)$

Now $E_{21}^{-1}$ times that:
Row 1: $(1,0,0)$
Row 2: $4\times(1,0,0)+(0,1,1) = (4,1,1)$
Row 3: $(3,0,1)$

So $A = \begin{bmatrix}1 & 0 & 0 \\ 4 & 1 & 1 \\ 3 & 0 & 1\end{bmatrix}$

---

### (c) What is the lower triangular factor $L$ in $A = LU$?


#### Solution:
$L$ is just the product of the inverses of the $E$ matrices (the ones with the multipliers below the diagonal):

$L = \begin{bmatrix}1 & 0 & 0 \\ 4 & 1 & 0 \\ 3 & 0 & 1\end{bmatrix}$

---
## Question 3

Given: The $3 \times 4$ matrix $A$ depends on $c$:
$$A = \begin{bmatrix}1 & 1 & 2 & 4 \\ 3 & c & 2 & 8 \\ 0 & 0 & 2 & 2\end{bmatrix}$$

---

### (a) For each $c$, find a basis for the column space of $A$


#### Solution:
Let $a_1 = \begin{bmatrix}1 \\ 3 \\ 0\end{bmatrix}$, $a_2 = \begin{bmatrix}1 \\ c \\ 0\end{bmatrix}$, $a_3 = \begin{bmatrix}2 \\ 2 \\ 2\end{bmatrix}$, $a_4 = \begin{bmatrix}4 \\ 8 \\ 2\end{bmatrix}$.

If $c \neq 3$, $a_1, a_2, a_3$ are independent (since $a_2$ isn't a multiple of $a_1$ unless $c=3$). $a_4$ can be written as a combination of the others. So basis: $a_1, a_2, a_3$.

If $c=3$, $a_2 = a_1$, so basis: $a_1, a_3$.

---

### (b) For each $c$, find a basis for the nullspace of $A$
\

#### Solution:
Set up $Ax = 0$:
1. $x_1 + x_2 + 2x_3 + 4x_4 = 0$
2. $3x_1 + c x_2 + 2x_3 + 8x_4 = 0$
3. $2x_3 + 2x_4 = 0$ so $x_3 = -x_4$

Plug $x_3 = -x_4$ into the first two:
1. $x_1 + x_2 + 2(-x_4) + 4x_4 = x_1 + x_2 + 2x_4 = 0$
2. $3x_1 + c x_2 + 2(-x_4) + 8x_4 = 3x_1 + c x_2 + 6x_4 = 0$

Let $x_4 = t$ (free). From (1): $x_1 = -x_2 - 2t$. Plug into (2):
$3(-x_2 - 2t) + c x_2 + 6t = -3x_2 - 6t + c x_2 + 6t = (c-3)x_2 = 0$

So if $c \neq 3$, $x_2 = 0$, so $x_1 = -2t$, $x_3 = -t$, $x_4 = t$. Nullspace basis: $(-2,0,-1,1)$.

If $c=3$, $x_2$ is free, so basis: $(-1,1,0,0)$ and $(-2,0,-1,1)$.

---


### (c) For each $c$, find the complete solution $x$ to $Ax = \begin{bmatrix}1 \\ c \\ 0\end{bmatrix}$

Let $x_4 = t$ (free). $x_3 = -t$. From the first equation: $x_1 + x_2 + 2(-t) + 4t = x_1 + x_2 + 2t = 1$, so $x_1 = 1 - x_2 - 2t$.
Second equation: $3x_1 + c x_2 + 6t = c$. Plug $x_1$ in:
$3(1 - x_2 - 2t) + c x_2 + 6t = c$
$3 - 3x_2 - 6t + c x_2 + 6t = c$
$3 + (c-3)x_2 = c$
So $(c-3)x_2 = c-3$

If $c \neq 3$, $x_2 = 1$, $x_1 = 1 - 1 - 2t = -2t$, $x_3 = -t$, $x_4 = t$. Take $t=0$ for a particular solution: $(0,1,0,0)$. General solution: $(0,1,0,0) + \alpha(-2,0,-1,1)$.

If $c=3$, $x_2$ is free, $x_1 = 1 - x_2 - 2t$, $x_3 = -t$, $x_4 = t$. Take $t=0$: $(1-x_2, x_2, 0, 0)$. General solution: $(1-x_2, x_2, 0, 0) + \beta(-1,1,0,0) + \gamma(-2,0,-1,1)$.

---

## Question 4


### (a) If $A$ is a $3 \times 5$ matrix, what information do you have about the nullspace of $A$?


#### Solution:
$A$ is $3 \times 5$, so $Ax = 0$ for $x \in \mathbb{R}^5$. The nullspace has dimension $5 - r$, and $r \leq 3$, so nullspace is at least 2-dimensional.

---

### (b) Suppose row operations on $A$ lead to $R = \operatorname{rref}(A)$:
$$R = \begin{bmatrix}1 & 4 & 0 & 0 & 0 \\ 0 & 0 & 0 & 1 & 0 \\ 0 & 0 & 0 & 0 & 1\end{bmatrix}$$
Write all known information about the columns of $A$.


#### Solution:
Looking at the rref, pivots are in columns 1, 4, 5. So columns 1, 4, 5 of $A$ are linearly independent and form a basis for the column space. Column 2 is $4$ times column 1, and column 3 is zero.

---

### (c) In the vector space $M$ of all $3 \times 3$ matrices, what subspace $S$ is spanned by all possible row reduced echelon forms $R$?


#### Solution:
All possible RREFs for $3 \times 3$ matrices are upper triangular, so the subspace $S$ is the set of all $3 \times 3$ upper triangular matrices (dimension 6).