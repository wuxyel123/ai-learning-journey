## Matrix Operations – Addition, Scalar Multiplication, Matrix Multiplication & Transpose

## 1. What Is a Matrix?
#matrix

A **matrix** is a rectangular array of elements (numbers, symbols, or expressions) arranged in rows and columns, denoted $A\in\mathbb R^{m\times n}$. Each entry $A_{ij}$ represents the element at row $i$ and column $j$.

#### Special Matrices

- **Zero matrix**: All entries are zero; serves as the additive identity: $A+0=A$.
    
- **Identity matrix** $I_n$: Square $n\times n$ with ones on the diagonal and zeros elsewhere; multiplicative identity: $AI=IA=A$.
    
- **Symmetric matrix**: A square matrix satisfying $A^T=A$; appears in covariance matrices, quadratic forms, and spectral methods.
    

---

## 2. Matrix Addition & Scalar Multiplication

### 2.1 Matrix Addition
#matrixAddition

- **Definition**: For $A,B\in\mathbb R^{m\times n}$,  
    $(A+B)_{ij} = A_{ij} + B_{ij}$
    
- **Properties**:
    
    - **Commutative**: $A+B = B+A$.
        
    - **Associative**: $(A+B)+C = A+(B+C)$.
        
    - **Additive identity**: $A+0= A$.
        
- **Example**:  
    $\begin{bmatrix}1&2\\3&4\end{bmatrix} + \begin{bmatrix}5&6\\7&8\end{bmatrix} = \begin{bmatrix}6&8\\10&12\end{bmatrix}$
    

### 2.2 Scalar Multiplication
#scalarMultiplication
- **Definition**: For $k\in\mathbb R$ and $A\in\mathbb R^{m\times n}$,  
    $(kA)_{ij} = k\cdot A_{ij}$
    
- **Properties**:
    
    - **Distributive**: $k(A+B) = kA + kB$.
        
    - **Associative with scalars**: $(kl)A = k(lA)$.
        
- **Example**:  
    $2\cdot\begin{bmatrix}1&2\\3&4\end{bmatrix} = \begin{bmatrix}2&4\\6&8\end{bmatrix}.$
    

---

## 3. Matrix Multiplication
#matrixMultiplication

### 3.1 Definition

- **Conformability**: Multiply $A\in\mathbb R^{m\times n}$ with $B\in\mathbb R^{n\times p}$ to get $C\in\mathbb R^{m\times p}$.
    
- **Entry formula**:  
    $C_{ij} = \sum_{k=1}^{n} A_{ik} B_{kj}$
    

### 3.2 Properties

- **Non-commutativity**: Generally $AB \neq BA$.
    
- **Associativity**: $(AB)C = A(BC)$.
    
- **Distributivity**: $A(B+C) = AB + AC$ and $(A+B)C = AC + BC$.
    
- **Transpose rule**: $(AB)^T = B^T A^T$.
    

### 3.3 Computational Complexity

- **Naïve algorithm**: $O(mnp)$ operations for $A_{m\times n}\times B_{n\times p}$.
    
- **Advanced algorithms** (Strassen, Coppersmith–Winograd) reduce exponents but are rare in practice; best known bound is $O(n^{2.37})$ asymptotically.
    

### 3.4 Block Matrix Multiplication

- Partition $A$ and $B$ into conformable blocks and multiply accordingly, useful for parallelism and cache optimization.
    

---

## 4. Matrix Transpose
#transpose

### 4.1 Definition

- For $A\in\mathbb R^{m\times n}$, transpose $A^T\in\mathbb R^{n\times m}$ with  
    ($(A^T)_{ij} = A_{ji}$
    

### 4.2 Key Properties

1. $(A^T)^T = A$.
    
2. $(A+B)^T = A^T + B^T$.
    
3. $(kA)^T = k A^T$.
    
4. $(AB)^T = B^T A^T$.
    
5. A is symmetric iff $A = A^T$.
    

---

## 5. Python Implementation with NumPy

```python
import numpy as np

# Example matrices
A = np.array([[1, 2], [3, 4]])
B = np.array([[5, 6], [7, 8]])

# Matrix addition
C_add = A + B

# Scalar multiplication
C_scalar = 3 * A

# Matrix multiplication
C_mul = A @ B

# Transpose
A_T = A.T

# Identity and zero matrices
I = np.eye(2)
Z = np.zeros((2, 2))

print("A + B =\n", C_add)
print("3 * A =\n", C_scalar)
print("A @ B =\n", C_mul)
print("A^T =\n", A_T)
print("Identity I =\n", I)
print("Zero Z =\n", Z)
```

---