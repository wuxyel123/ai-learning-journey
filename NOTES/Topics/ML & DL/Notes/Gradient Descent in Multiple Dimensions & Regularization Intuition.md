## Gradient Descent in Multiple Dimensions & Regularization Intuition

## 1. Multidimensional Gradient Descent

For parameters $(\boldsymbol{\theta} \in \mathbb{R}^n)$ and loss $(L(\boldsymbol{\theta}))$:

$$[
\boldsymbol{\theta}_{t+1} = \boldsymbol{\theta}_t - \alpha \nabla_{\boldsymbol{\theta}} L(\boldsymbol{\theta}_t)
]$$

Where $(\nabla_{\boldsymbol{\theta}}L)$ is the vector of partial derivatives for each parameter.

### Properties:
- Requires a **vector gradient** of dimension \(n\).
- Choose $( \alpha )$ small enough to ensure stable convergence. If $(\alpha)$ is too large, may diverge; too small, convergence is slow.

---

## 2. Learning Rate Schedules in Multi-D

Adapting $(\alpha)$ over time can boost performance:
- **Step decay**: reduce $( \alpha )$ at fixed epochs (e.g., reload by 0.1 at epochs 30, 60)
- **Cosine or exponential decay** are common.
- Adaptive optimizers like RMSprop and Adam handle per-parameter adjustments automatically

---

## 3. Regularization Intuition

### 3.1 L2 Regularization (Weight Decay)
Add penalty $(\frac{\lambda}{2}\|\boldsymbol{\theta}\|^2)$ to loss:
$$[
L_{\text{reg}}(\boldsymbol{\theta}) = L(\boldsymbol{\theta}) + \frac{\lambda}{2}\|\boldsymbol{\theta}\|^2
]$$
Encourages smaller weights, improving generalization.

### 3.2 L1 Regularization
Penalty term $(\lambda\|\boldsymbol{\theta}\|_1)$:
- Promotes **sparsity** (many weights become zero).
- Useful for feature selection.

### 3.3 Dropout (Brief Intuition)
During training, randomly drop units with probability $(p)$:
- Prevents **co-adaptation** of neurons.
- Acts as model ensemble; effective regularization in neural nets.

---

## 4. Practical Tips

- **Choose $(\lambda)$** via cross-validation; common values: $(0.01)$ to $(0.001)$.
- Use **mini-batches** to estimate gradients efficiently—often enough for large-scale tasks.
- **Monitor validation performance**: if train error decreases but validation increases, regularization may be too weak or $( \alpha )$ too high.

---