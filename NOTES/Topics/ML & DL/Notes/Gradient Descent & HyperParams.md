## Gradient Descent & Hyperparameters

## 1. Gradient Descent Overview

Gradient descent seeks to find a local minimum of a differentiable function $L(\boldsymbol{\theta})$ by iteratively updating parameters $\boldsymbol{\theta}$ in the opposite direction of the gradient:

$\boldsymbol{\theta}_{t+1} = \boldsymbol{\theta}_t - \alpha \, \nabla_{\boldsymbol{\theta}} L(\boldsymbol{\theta}_t)$

where $\alpha > 0$ is the **learning rate**. At each step, $\nabla L$ points toward steepest ascent, so stepping opposite moves toward a minimum.

---

## 2. Convergence & Learning Rate

- **Learning Rate $\alpha$**: Controls step size. Too large may cause divergence; too small leads to slow convergence.
    
- **Convergence Criteria**:
    
    - Norm of gradient $\|\nabla L\|$ below a threshold.
        
    - Change in loss $\Delta L$ or parameters $\|\Delta \boldsymbol{\theta}\|$ below tolerance.
        
    - Maximum number of iterations.
        
- **Learning Rate Schedules**:
    
    - **Constant**: $\alpha$ fixed.
        
    - **Decay**: $\alpha_t = \alpha_0 / (1 + \gamma t)$ or exponential decay.
        
    - **Step decay**: Drop by factor at preset epochs.
        

---

## 3. Variants of Gradient Descent

### 3.1 Batch Gradient Descent

- Computes $\nabla L$ using all $N$ data points each iteration.
    
- Pros: Converges smoothly. Cons: Expensive for large datasets.
    

### 3.2 Stochastic Gradient Descent (SGD)

- Updates using one randomly sampled example per iteration:  
    $\boldsymbol{\theta}_{t+1} = \boldsymbol{\theta}_t - \alpha \nabla_{\boldsymbol{\theta}} L_i(\boldsymbol{\theta}_t)$ 
    where $i$ is random.
    
- Pros: Faster updates, can escape shallow minima. Cons: Noisy, fluctuations in loss.
    

### 3.3 Mini-Batch Gradient Descent

- Uses a small batch of size $b$ (e.g., 32, 64) per update:  
    $\boldsymbol{\theta}_{t+1} = \boldsymbol{\theta}_t - \alpha \, \frac{1}{b} \sum_{i=1}^b \nabla L_i(\boldsymbol{\theta}_t)$
    
- Balances stability and speed; most common in practice.
    

---

## 4. Momentum & Adaptive Methods

### 4.1 Momentum

- Introduces velocity vector $t\mathbf{v}_t$:
    
    $\mathbf{v}_{t} = \beta \mathbf{v}_{t-1} + (1 - \beta) \nabla L(\boldsymbol{\theta}_t), \quad \boldsymbol{\theta}_{t+1} = \boldsymbol{\theta}_t - \alpha \mathbf{v}_t$
    
    where $\beta\in[0,1)$ (e.g., 0.9) damps oscillations and accelerates convergence.
    

### 4.2 RMSprop

- Maintains running average of squared gradients $\mathbf{s}_t$:
    
     $\mathbf{s}_t = \gamma \mathbf{s}_{t-1} + (1 - \gamma) [\nabla L(\boldsymbol{\theta}_t)]^2, \quad \boldsymbol{\theta}_{t+1} = \boldsymbol{\theta}_t - \frac{\alpha}{\sqrt{\mathbf{s}_t + \epsilon}} \nabla L(\boldsymbol{\theta}_t)$
    
    Common choices: $\gamma=0.9, \epsilon=10^{-8}$
    

### 4.3 Adam

- Combines momentum and RMSprop:
    
    $\mathbf{m}_t = \beta_1 \mathbf{m}_{t-1} + (1 - \beta_1) \nabla L(\boldsymbol{\theta}_t), \quad \mathbf{v}_t = \beta_2 \mathbf{v}_{t-1} + (1 - \beta_2) [\nabla L(\boldsymbol{\theta}_t)]^2$
    
    bias-corrected:
    
    $\hat{\mathbf{m}}_t = \frac{\mathbf{m}_t}{1 - \beta_1^t}, \quad \hat{\mathbf{v}}_t = \frac{\mathbf{v}_t}{1 - \beta_2^t}$
    
    update:
    
    $\boldsymbol{\theta}_{t+1} = \boldsymbol{\theta}_t - \alpha \frac{\hat{\mathbf{m}}_t}{\sqrt{\hat{\mathbf{v}}_t} + \epsilon}$
    
    Typical defaults: $\beta_1=0.9, \beta_2=0.999, \epsilon=10^{-8}$.
    

---

## 5. Python Implementation Example

```python
import numpy as np

# Sample quadratic function L(w) = (w-3)^2

def L(w):
    return (w - 3) ** 2

def grad_L(w):
    return 2 * (w - 3)

# Gradient descent parameters
w = 0.0  # initial
alpha = 0.1  # learning rate
num_iters = 50

for t in range(num_iters):
    dw = grad_L(w)
    w -= alpha * dw
    if t % 10 == 0:
        print(f"Iter {t}: w={w:.4f}, L(w)={L(w):.4f}")
```

---
