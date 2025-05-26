## Singular Value Decomposition (SVD) & Principal Component Analysis (PCA)

### 1. Singular Value Decomposition (SVD)
#SVD

#### 1.1 Definition

The Singular Value Decomposition of a real $m\times n$ matrix $A$ is given by:

$A = U \Sigma V^T$

where:

- $U$ is an $m\times m$ orthogonal matrix whose columns are the left-singular vectors of $A$.
    
- $\Sigma$ is an $m\times n$ diagonal matrix with non-negative entries (the singular values) in descending order.
    
- $V$ is an $n\times n$ orthogonal matrix whose columns are the right-singular vectors of $A$.  
    $\sigma_i = \Sigma_{ii}$ are the singular values, and $r = \mathrm{rank}(A)$ equals the number of non-zero singular values.  
    ${{U = U, Σ = Σ, V^T = V^T}}$
    

#### 1.2 Key Properties

- Multiplicativity of rank: $r\mathrm{rank}(A) = r$ equals the number of non-zero singular values.
    
- Pseudoinverse: $A^+ = V \Sigma^+ U^T$, where $\Sigma^+$ inverts non-zero singular values
    
- Low-rank approximation (Eckart–Young theorem): Best rank-k approximation $A_k = U_k \Sigma_k V_k^T$ 
    

### 2. Principal Component Analysis (PCA)
#PCA

#### 2.1 Relationship to SVD

PCA performs eigendecomposition of the data covariance matrix; equivalently, PCA can be computed via SVD on the centered data matrix $X$ as:

$X = U \Sigma V^T \quad\Longrightarrow\quad \text{Principal components} = V,\; \text{variances} = (\Sigma_{ii})^2/(n-1)$

Thus, PCA is a special case of SVD applied to zero-mean data.

#### 2.2 Steps for PCA via SVD

1. Center the data: subtract column means from $X$.
    
2. Compute SVD: $X = U \Sigma V^T$.
    
3. Select top $k$ singular values and vectors: $V_k$.
    
4. Project data: $X_k = X V_k$ yields the reduced k-dimensional representation.
    

### 3. Python Example

```python
import numpy as np
# Sample data matrix (observations × features)
X = np.array([[2.5, 2.4],
              [0.5, 0.7],
              [2.2, 2.9],
              [1.9, 2.2],
              [3.1, 3.0],
              [2.3, 2.7],
              [2.0, 1.6],
              [1.0, 1.1],
              [1.5, 1.6],
              [1.1, 0.9]])
# Center
X_centered = X - np.mean(X, axis=0)
# SVD
U, S, VT = np.linalg.svd(X_centered)
# Principal components (loadings)
V = VT.T
# Project onto first component
X_pca1 = X_centered @ V[:, 0]
print("Singular values:", S)
print("First principal component (direction):", V[:, 0])
print("Projected data (1D):", X_pca1)
```
