## Derivatives & Notation

## 1. Definition of the Derivative

The **derivative** of a function ff at a point xx is its instantaneous rate of change, defined by:

$f'(x) = \lim_{\Delta x \to 0} \frac{f(x+\Delta x)-f(x)}{\Delta x}$

---

## 2. Common Notations

- **Lagrange (prime) notation**: $f'(x),\ f''(x),\ f^{(n)}(x)$
    
- **Leibniz notation**: $\frac{dy}{dx},\ \frac{d^2y}{dx^2}$
    
- **Newton (dot) notation**: $\dot y = \frac{dy}{dt},\ \ddot y = \frac{d^2y}{dt^2}$
    
- **D-operator**: $Df = \frac{df}{dx},\ D^n f = \frac{d^n f}{dx^n}$
    

---

## 3. Basic Differentiation Rules

1. **Power rule**: $\frac{d}{dx}[x^n] = n x^{n-1}$
    
2. **Sum rule**: $\frac{d}{dx}[f+g] = f' + g'$
    
3. **Constant rule**: $\frac{d}{dx}[c] = 0$
    
4. **Product rule**: $\frac{d}{dx}[f g] = f'g + fg'$
    
5. **Quotient rule**:$\frac{d}{dx}[f/g] = \frac{f'g - fg'}{g^2}$
    
6. **Chain rule**: For$ $h(x)=f(g(x)), h′(x)=f′(g(x))g′(x)$
    

---

## 4. Partial Derivatives

For a multivariable function $ff(x,y,\dots)$, the partial derivative with respect to $x$ holds other variables constant:

$\frac{\partial f}{\partial x} = \lim_{\Delta x \to 0} \frac{f(x+\Delta x,y,\dots)-f(x,y,\dots)}{\Delta x}$

---

## 5. Numerical Differentiation with NumPy

```python
import numpy as np
x = np.linspace(0, 10, 1000)
y = np.sin(x)
dydx = np.gradient(y, x[1] - x[0])
print(dydx[:5])
```

---