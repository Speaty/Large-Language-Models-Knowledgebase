## Matrix Multiplication
Given 2 matrices: $A \in \mathbb{R}^{m \times n}$ and $B \in \mathbb{R}^{k \times p}$, $A^n$ must equal $B^k$ in order for multiplication to be valid. The resulting matrix is: $C^{m\times p}$ 



$$
A = \begin{bmatrix} 
	a_1 & b_1 \\ c_1 & d_1 
	\end{bmatrix}
\quad
B = 
	\begin{bmatrix}
	a_2 & b_2 \\ c_2 & d_2
	\end{bmatrix}

$$
$$
A \cdot B =  \begin{bmatrix}
	a_1 \cdot a_2 + b_1 \cdot c_2 & a_1 \cdot b_2 + b_1 \cdot d_2 
	\\ 
	c_1 \cdot a_2 + d_1 \cdot c_2 & c_1 \cdot b_2 + d_1 \cdot d_2 
\end{bmatrix}

$$
## Matrix Equation
Find $x$ such that $Ax=b$, where:
- $A$ is a **known** matrix
- $b$ is a **known** vector
- $x$ is an **unknown** vector

Matrix equation problems can be solved using:
```python
np.linalg.solve(A, b) # will find an x for Ax=b
```

