## Gradients & Partial Derivatives

## 1. Partial Derivatives Recap

A **partial derivative** of a function $f(x, y, \dots)$ with respect to $x$ holds all other variables constant:

$\frac{\partial f}{\partial x} = \lim_{\Delta x \to 0} \frac{f(x + \Delta x, y, \dots) - f(x, y, \dots)}{\Delta x}$

Similarly, the partial derivative with respect to $y$ is:

$\frac{\partial f}{\partial y} = \lim_{\Delta y \to 0} \frac{f(x, y + \Delta y, \dots) - f(x, y, \dots)}{\Delta y}$

These derivatives measure how $f$ changes as each variable varies individually.

---

## 2. The Gradient Vector

For a differentiable function $f: \mathbb{R}^n \to \mathbb{R}$, the **gradient** is the vector of all partial derivatives:

$\nabla f(x_1, \dots, x_n) = \begin{bmatrix} \frac{\partial f}{\partial x_1} \\ \frac{\partial f}{\partial x_2} \\ \vdots \\ \frac{\partial f}{\partial x_n} \end{bmatrix}$.

- **Direction of Steepest Ascent**: The gradient points toward the direction of maximal increase in $f$.
    
- **Orthogonality to Level Sets**: At any point, $\nabla f$ is perpendicular to the level surface $f(x) = \text{constant}$.
    
- **Linearity**: $\nabla(af + bg) = a \, \nabla f + b \, \nabla g$ for scalars $a, b$.
    

---

## 3. Directional Derivative

The **directional derivative** of $f$ at point $\mathbf{x}$ in the direction of a unit vector $/mathbf{u}$ is:

$D_{\mathbf{u}} f(\mathbf{x}) = \nabla f(\mathbf{x}) \cdot \mathbf{u}$.

This gives the rate of change of $f$ moving along $\mathbf{u}$.

---

## 4. Computing Gradients in Practice

### 4.1 Analytical Example

Let $f(x, y) = x^2 y + e^{xy}$. Then:

$\frac{\partial f}{\partial x} = 2xy + y \, e^{xy}, \quad \frac{\partial f}{\partial y} = x^2 + x \, e^{xy}$.

So the gradient is:

$\nabla f(x, y) = \begin{bmatrix} 2xy + y \, e^{xy} \\ x^2 + x \, e^{xy} \end{bmatrix}$.

### 4.2 Numerical Approximation

Use finite differences to approximate partials:

```python
import numpy as np

def f(x, y):
    return x**2 * y + np.exp(x * y)

h = 1e-5
x0, y0 = 1.0, 2.0

# Partial wrt x
df_dx = (f(x0 + h, y0) - f(x0 - h, y0)) / (2 * h)
# Partial wrt y
df_dy = (f(x0, y0 + h) - f(x0, y0 - h)) / (2 * h)

grad = np.array([df_dx, df_dy])
print(grad)
```

This calculates the gradient numerically at $(x_0, y_0)$.

---

## 5. Gradients in Machine Learning

In ML, one often optimizes a **loss function** $\mathcal{L}(\boldsymbol{\theta})$ over parameters $\boldsymbol{\theta}$. The gradient $\nabla_{\boldsymbol{\theta}} \mathcal{L}$ indicates how to adjust parameters to decrease loss using gradient descent.

### 5.1 Gradient Descent Update Rule

Given learning rate $\alpha > 0$, update:

$\boldsymbol{\theta} \leftarrow \boldsymbol{\theta} - \alpha \, \nabla_{\boldsymbol{\theta}} \mathcal{L}(\boldsymbol{\theta})$.

Each iteration computes $\nabla_{\boldsymbol{\theta}} \mathcal{L}$ (analytically or via automatic differentiation) to move toward a local minimum.

---

## 6. Python Example: Gradient of a Loss

For a simple linear model $y = w x + b$ with data $(x_i, t_i)$, the **mean squared error** is:

$\mathcal{L}(w, b) = \frac{1}{N} \sum_{i=1}^N (w x_i + b - t_i)^2$.

The gradients are:

∂$\frac{\partial \mathcal{L}}{\partial w} = \frac{2}{N} \sum_{i=1}^N (w x_i + b - t_i) \, x_i, \quad \frac{\partial \mathcal{L}}{\partial b} = \frac{2}{N} \sum_{i=1}^N (w x_i + b - t_i)$.

Implementation:

```python
import numpy as np

# Synthetic data
x = np.array([1., 2., 3., 4.])
t = np.array([2.3, 4.1, 5.9, 8.2])
w, b = 0.5, 0.0
lr = 0.01
N = x.size

def gradients(w, b, x, t):
    y = w * x + b
    error = y - t
    dw = (2 / N) * np.dot(error, x)
    db = (2 / N) * np.sum(error)
    return dw, db

# Single update step
dw, db = gradients(w, b, x, t)
w -= lr * dw
b -= lr * db
print("Updated w, b:", w, b)
```

This demonstrates one gradient descent step.

---
