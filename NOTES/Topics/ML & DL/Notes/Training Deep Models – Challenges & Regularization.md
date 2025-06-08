## Training Deep Models – Challenges & Regularization

## 1. Vanishing & Exploding Gradients  
- **Vanishing Gradients**: Gradients shrink through backprop, especially with sigmoid, tanh activations or deep models, causing early layers to learn too slowly.  
- **Exploding Gradients**: Gradients grow and cause instability or overflow during training.  
**Solutions**:
- Use non-saturating activations (ReLU).
- Apply careful weight initialization and batch normalization.
- Clip gradients to limit magnitude.
- Use architectural techniques like skip connections (ResNets).

---

## 2. Dropout – Breaking Co‑Adaptation  
- Randomly deactivate neurons during training with probability \(p\) to prevent dependence between neurons.  
- Use dropout rates ~0.5 in hidden layers, ~0.8 in input.  
- At test time, use the full network with scaled node outputs.  
This simulates training an ensemble and improves generalization.

---

## 3. Norm‑Based Regularization  
- **L2 (weight decay)**: Adds $(\frac{\lambda}{2}\|\theta\|^2)$ to the loss—encourages small weights.  
- **L1 (Lasso)**: Adds $(\lambda\|\theta\|_1)$ to promote sparsity in weights.

---

## 4. Early Stopping – Time as Regularization  
- Monitor validation loss during training; stop when it no longer improves (uses a patience threshold).  
- Prevents overfitting by halting before the model becomes overly complex.

---

## 5. Practical Training Tips  
- Always track **training vs validation metrics** to detect issues.  
- Combine methods (e.g. L2 + dropout + early stopping) for best effect.  
- Adjust dropout rate (typically between 0.2–0.5) and use **gradient clipping** to improve stability.

---