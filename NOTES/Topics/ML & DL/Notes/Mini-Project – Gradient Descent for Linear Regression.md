## Mini-Project – Gradient Descent for Linear Regression

## 1. Objective

- Implement linear regression with one or more variables
- Use gradient descent to minimize the mean squared error (MSE)
- Visualize the loss over epochs
- Compare with scikit-learn's `LinearRegression`

---

## 2. Math Recap

Linear regression predicts:

$$[
\hat{y} = w_0 + w_1 x_1 + w_2 x_2 + \dots + w_n x_n = \mathbf{w}^\top \mathbf{x}
]$$

Loss (mean squared error):

$$[
\mathcal{L} = \frac{1}{m} \sum_{i=1}^m (y^{(i)} - \hat{y}^{(i)})^2
]$$

Gradient descent update rule:

$$[
\mathbf{w} := \mathbf{w} - \alpha \nabla_\mathbf{w} \mathcal{L}
]$$

---

## 3. Python Implementation

### 🔧 From Scratch
```python
import numpy as np
import matplotlib.pyplot as plt

# Generate toy dataset
np.random.seed(0)
X = 2 * np.random.rand(100, 1)
y = 4 + 3 * X + np.random.randn(100, 1)

# Add bias term
X_b = np.c_[np.ones((100, 1)), X]

# Initialize weights
theta = np.random.randn(2, 1)
learning_rate = 0.1
n_epochs = 1000
m = len(X_b)

losses = []

for epoch in range(n_epochs):
    gradients = 2/m * X_b.T @ (X_b @ theta - y)
    theta -= learning_rate * gradients

    loss = np.mean((X_b @ theta - y) ** 2)
    losses.append(loss)

print("Learned weights:", theta.ravel())

plt.plot(losses)
plt.xlabel("Epochs")
plt.ylabel("MSE Loss")
plt.title("Gradient Descent Progress")
plt.grid(True)
plt.show()
```

### Comparison with sklearn
```python
from sklearn.linear_model import LinearRegression

lin_reg = LinearRegression()
lin_reg.fit(X, y)

print("scikit-learn coefficients:", lin_reg.intercept_, lin_reg.coef_)
```
## 4. Stretch Goals

- Extend to multiple input variables
    
- Normalize data and compare convergence speed
    
- Add early stopping or momentum
    
- Implement mini-batch version