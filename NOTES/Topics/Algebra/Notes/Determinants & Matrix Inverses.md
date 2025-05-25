## Determinants & Matrix Inverses

## 1. The Determinant
#determinant
### 1.1 Definition

The **determinant** of a square matrix $A \in \mathbb R^{n\times n}$ is a scalar $\det(A)$ that encodes volume scaling and invertibility of $A$.

### 1.2 Key Properties

- **Multiplicativity:** $\det(AB) = \det(A)\det(B)$.
    
- **Transpose Invariance:** $\det(A^T)=\det(A)$.
    
- **Row Operations:** Adding a multiple of one row to another leaves $\det$ unchanged; swapping two rows multiplies $\det$ by $-1$; scaling a row by $k$ multiplies $\det$ by $k$.
    
- **Invertibility Criterion:** $A$ is invertible iff $\det(A) \neq 0$.
    

### 1.3 Computation Methods

- **Cofactor (Laplace) Expansion:** Expand along any row or column using minors and cofactors:  
    $\det(A) = \sum_{j=1}^n (-1)^{i+j}A_{ij}\det(M_{ij})$  
    where $M_{ij}$ is the $(n-1)\times(n-1)$ minor.
    
- **Row Reduction:** Use Gaussian elimination to upper-triangular form and multiply diagonal entries, adjusting for row swaps and scalings.
    

### 1.4 Examples

- **2×2 Matrix:** For $A=\begin{pmatrix}a&b\\c&d\end{pmatrix}$,  
    $\det(A)=ad - bc$ 
    
- **3×3 Matrix:** Given $A=\begin{pmatrix}a&b&c\\d&e&f\\g&h&i\end{pmatrix}$,  
    $\det(A)=a(ei - fh)- b(di - fg) + c(dh - eg)$.
    

---

## 2. Matrix Inverse
#matrixInversion

### 2.1 Definition

A square matrix $A$ is **invertible** if there exists $A^{-1}$ such that $AA^{-1}=A^{-1}A=I$, where $I$ is the identity matrix.

### 2.2 Existence Criterion

$A^{-1}$ exists precisely when $\det(A) \neq 0$.

### 2.3 Inversion Methods

- **Adjugate Formula (Classical):**  
    $A^{-1} = \frac{1}{\det(A)}\operatorname{adj}(A)$,  
    where $\operatorname{adj}(A)$ is the transpose of the cofactor matrix.
    
- **Gauss–Jordan Elimination:** Augment $[A|I]$, then row-reduce to $[I|A^{-1}]$ .
    
- **2×2 Shortcut:** For $A=\begin{pmatrix}a&b\\c&d\end{pmatrix}$,  
    $A^{-1}=\frac{1}{ad - bc}\begin{pmatrix}d&-b\\-c&a\end{pmatrix}$.
    

### 2.4 Computational Considerations

- **Complexity:** Gaussian elimination inversion is $O(n^3)$.
    
- **Numerical Stability:** Pivoting strategies (partial, complete) improve accuracy in floating-point arithmetic.
    

### 2.5 Examples

- **2×2 Example:** $A=\begin{pmatrix}2&1\\1&3\end{pmatrix}$,  
    $\det(A)=5$,  
    $A^{-1}=\tfrac{1}{5} \begin{pmatrix}3&-1\\-1&2\end{pmatrix}$
    
- **3×3 Example via Adjugate:** For $A=\begin{pmatrix}1&2&3\\0&1&4\\5&6&0\end{pmatrix}$, compute cofactors, adjugate, and divide by $\det(A)$.
    

---