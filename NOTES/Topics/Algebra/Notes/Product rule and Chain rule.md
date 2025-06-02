## Product Rule & Chain Rule

## 1. Product Rule

**Statement**  
For differentiable functions $f$ and $g$:

$\frac{d}{dx}[f(x)\,g(x)] = f'(x)\,g(x) + f(x)\,g'(x)$.

**Proof Sketch**

$\begin{aligned} \frac{d}{dx}[f(x)g(x)] &= \lim_{h\to0}\frac{f(x+h)g(x+h)-f(x)g(x)}{h}\\ &= \lim_{h\to0}\Bigl[\frac{f(x+h)-f(x)}{h}g(x+h) + f(x)\frac{g(x+h)-g(x)}{h}\Bigr]\\ &= f'(x)\,g(x) + f(x)\,g'(x). \end{aligned}$

**Example**  
Differentiate $h(x)=x^2\sin(x)$:
$h'(x) = 2x\sin(x) + x^2\cos(x)$.

---

## 2. Chain Rule

**Statement**  
For $h(x)=f(g(x))$:

$\frac{d}{dx}[f(g(x))] = f'(g(x))\,g'(x)$

**Proof Sketch**

$\frac{dy}{dx} = \lim_{h\to0}\frac{f(g(x+h))-f(g(x))}{h} = f'(g(x))\,g'(x)$

**Example**

1. For $y=\exp(\sin(x^2))$:
    

$y' = \exp(\sin(x^2))\,\cos(x^2)\,(2x)$

2. For $y=(3x+2)^5$:
    

$y' = 5(3x+2)^4\cdot3 = 15(3x+2)^4$

---

## 3. Extensions

- **Triple Product Rule**:
    
    $\frac{d}{dx}[fgh] = f'gh + fg'h + fgh'$
- **Nested Compositions**: apply chain rule repeatedly for $f(g(h(x)))$.
    
- **Logarithmic Differentiation**: for functions like $y=x^x$, use $\ln y = x\ln x$ then differentiate.
    

---

## 4. Verification (Optional)

```python
import sympy as sp
x = sp.symbols('x')
f = x**2 * sp.sin(x)
sp.diff(f, x)  # 2*x*sin(x) + x**2*cos(x)
```

---