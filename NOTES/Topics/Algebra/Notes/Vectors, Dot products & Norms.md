## Vectors, Dot Products & Norms

### 1. Vectors in ℝⁿ

#vector

A **vector** is an ordered list of numbers representing a point or direction in n-dimensional space. Vectors can be represented as:

- **Row vector**:
    
    $$\mathbf{v} = [v_1, v_2, \dots, v_n]$$
- **Column vector**:
    
    $$\mathbf{v} = \begin{bmatrix} v_1 \\ v_2 \\ \vdots \\ v_n \end{bmatrix}$$

Vectors are fundamental in AI for representing data points, weights in models, directions in space, and more.

---

### 2. Dot Product

#DotProduct

The **dot product** (also known as the scalar product) is a way to multiply two vectors to obtain a scalar.

- **Algebraic Definition**:
    
    $$\mathbf{a} \cdot \mathbf{b} = \sum_{i=1}^{n} a_i b_i$$
- **Geometric Definition**:
    
    $$\mathbf{a} \cdot \mathbf{b} = \|\mathbf{a}\| \|\mathbf{b}\| \cos(\theta)$$

#### Properties:

- **Commutative**:
    
    $$\mathbf{a} \cdot \mathbf{b} = \mathbf{b} \cdot \mathbf{a}$$
- **Distributive over addition**:
    
    $$\mathbf{a} \cdot (\mathbf{b} + \mathbf{c}) = \mathbf{a} \cdot \mathbf{b} + \mathbf{a} \cdot \mathbf{c}$$
- **Scalar multiplication**:
    
    $$(k\mathbf{a}) \cdot \mathbf{b} = k(\mathbf{a} \cdot \mathbf{b})$$

#### Orthogonality:

- Vectors **a** and **b** are **orthogonal** if:
    
    $$\mathbf{a} \cdot \mathbf{b} = 0$$
- Orthogonality is essential in feature independence and dimensionality reduction.
    

#### Cosine of Angle Between Vectors:

- The **angle** θ between two vectors tells us their direction similarity:
    
    - θ = 0° → same direction
        
    - θ = 90° → orthogonal
        
    - θ = 180° → opposite direction
        

---

### 3. Vector Norms

#Norm

A **norm** is a function that assigns a non-negative length or size to vectors in a vector space.

#### **Euclidean Norm (ℓ₂ norm)**:

The most common norm:

$$\|\mathbf{a}\| = \sqrt{\sum_{i=1}^{n} a_i^2} = \sqrt{\mathbf{a} \cdot \mathbf{a}}$$

#### Properties:

- **Non-negativity**:
    
    $$\|\mathbf{a}\| \geq 0,\quad \|\mathbf{a}\| = 0 \Leftrightarrow \mathbf{a} = \mathbf{0}$$
- **Scalar multiplication**:
    
    $$\|k\mathbf{a}\| = |k| \|\mathbf{a}\|$$
- **Triangle inequality**:
    
    $$\|\mathbf{a} + \mathbf{b}\| \leq \|\mathbf{a}\| + \|\mathbf{b}\|$$

#### Other Common Norms:

- **ℓ₁ norm (Manhattan distance)**:
    
    $$\|\mathbf{a}\|_1 = \sum_{i=1}^n |a_i|$$
- **ℓ∞ norm (Max norm)**:
    
    $$\|\mathbf{a}\|_\infty = \max_i |a_i|$$

####  Unit Vectors:

A **unit vector** has norm 1:

$$\mathbf{u} = \frac{\mathbf{a}}{\|\mathbf{a}\|}$$

---

###  4. Vector Projection

#Projection #VectorProjection

To **project vector a onto b**:

$$\text{proj}_{\mathbf{b}} \mathbf{a} = \frac{\mathbf{a} \cdot \mathbf{b}}{\|\mathbf{b}\|^2} \mathbf{b}$$

- This gives the component of **a** that lies in the direction of **b**.
    
- Crucial in PCA, gradient descent intuition, and shadow calculations.
    

---

### 🐍 5. Python Implementation with NumPy

```python
import numpy as np

# Define two vectors
a = np.array([1, 3, -5])
b = np.array([4, -2, -1])

# Compute the dot product
dot_product = np.dot(a, b)

# Compute the norms
norm_a = np.linalg.norm(a)
norm_b = np.linalg.norm(b)

# Cosine of angle between a and b
cos_theta = dot_product / (norm_a * norm_b)

# Angle in radians
theta = np.arccos(cos_theta)

# Projection of a onto b
proj_ab = (dot_product / norm_b**2) * b

# Unit vector
unit_a = a / norm_a

print(f"Dot product: {dot_product}")
print(f"Norm of a: {norm_a}")
print(f"Norm of b: {norm_b}")
print(f"Cosine of angle: {cos_theta}")
print(f"Angle (in radians): {theta}")
print(f"Projection of a onto b: {proj_ab}")
print(f"Unit vector of a: {unit_a}")
```
---

### 📚 6. Further Reading & Resources

- [Dot Product and Norms – LibreTexts](https://math.libretexts.org/Bookshelves/Linear_Algebra/A_First_Course_in_Linear_Algebra_\(Kuttler\)/04%3A_R/4.07%3A_The_Dot_Product)
    
- [NumPy’s dot function](https://numpy.org/doc/stable/reference/generated/numpy.dot.html)
    
- [Vector Norms Explained – LibreTexts](https://math.libretexts.org/Bookshelves/Linear_Algebra/Book%3A_Linear_Algebra_\(Schilling_Nachtergaele_and_Lankham\)/09%3A_Inner_product_spaces/9.02%3A_Norms)
    

---