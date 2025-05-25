#  Eigenvalues & Eigenvectors
#eigenvalue #eigenvector

## 1. Eigenvalue & Eigenvector Definitions

- A **nonzero vector** $\mathbf{v}$ is an **eigenvector** of a square matrix $A\in\mathbb{R}^{n\times n}$ if it satisfies:
    
    $A\mathbf{v} = \lambda\mathbf{v}$
    
    where $\lambda$ is a scalar called the **eigenvalue** associated with $\mathbf{v}$
    
- Geometrically, eigenvectors are directions that the transformation $A$ stretches or compresses without changing direction, and $\lambda$ measures the scale factor.
    

---

## 2. Characteristic Polynomial & Computation

- **Characteristic polynomial**:
    
    $p(\lambda) = \det(A - \lambda I) = 0$
    
    Solving this degree-n polynomial yields the eigenvalue $\lambda_1, \ldots, \lambda_n$.
    
- **2×2 example**: For
    
    $A = \begin{pmatrix}2 & 1 \\ 1 & 2\end{pmatrix}, \quad p(\lambda) = (2-\lambda)^2 - 1 = 0$
    
    giving $\lambda=3$ and $\lambda=1$. Eigenvectors satisfy $(A-\lambda I)\mathbf{v}=0$ .
    

---

## 3. Properties & Diagonalization

- **Distinct eigenvalues** of a matrix guarantee a set of linearly independent eigenvectors, allowing **diagonalization**:
    
    $A = PDP^{-1}$
    
    where $D$ is diagonal of eigenvalues and columns of $P$ are eigenvectors.
    
- **Multiplicity & Jordan form**: If eigenvalues repeat, one may need the Jordan canonical form for non-diagonalizable cases.
    

---

## 4. Applications in AI & Data Science

- **PCA**: Eigendecomposition of the covariance matrix extracts principal components (directions of maximum variance) and projects data onto them. #PCA
    
- **Spectral clustering**: Uses eigenvalues of the Laplacian matrix of a graph to partition data points into clusters. #spectralClustering
    
- **Stability analysis**: Largest eigenvalue of a system matrix determines long-term behavior in iterative processes and neural network dynamics.
    

---

## 5. Python Implementation with NumPy

```python
import numpy as np

# Example matrix
A = np.array([[2, 1], [1, 2]])

# Compute eigenvalues and eigenvectors
eigenvalues, eigenvectors = np.linalg.eig(A)

print("Eigenvalues:", eigenvalues)
print("Eigenvectors:")
print(eigenvectors)
```

---