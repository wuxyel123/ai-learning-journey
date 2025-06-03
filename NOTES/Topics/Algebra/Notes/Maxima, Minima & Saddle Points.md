## Optimization Basics – Maxima, Minima & Saddle Points

## 1. Critical Points of Single-Variable Functions

### 1.1 Definition

A **critical point** of a differentiable function $f(x)$ occurs where $f′(x)=0$ or $f'$ is undefined. These points are candidates for local maxima, minima, or inflection points.

### 1.2 First Derivative Test

1. Find $f'(x)$.
    
2. Solve $f′(x)=0$ for critical points $x_c$.
    
3. Determine sign of $f′(x)$ on intervals around each $x_c$:
    
    - If $f'$ changes from positive to negative at $x_c$, $f(x_c)$ is a local maximum.
        
    - If $f'$ changes from negative to positive at $x_c, f(x_c)$ is a local minimum.
        
    - If no sign change, $x_c$ is neither max nor min (possible inflection).
        

### 1.3 Second Derivative Test

1. Compute $f''(x)$.
    
2. Evaluate $f''(x_c)$:
    
    - If $f''(x_c) > 0, f(x_c)$ is a local minimum.
        
    - If $f''(x_c) < 0$, $f(x_c)$ is a local maximum.
        
    - If $f''(x_c) = 0$, the test is inconclusive; use higher derivatives or first derivative behavior.
        

### 1.4 Example

For $f(x) = x^3 - 3x^2 + 4$:

1. $f'(x) = 3x^2 - 6x = 3x(x - 2)$.
    
2. Critical points: $x = 0, 2$.
    
3. $f''(x) = 6x - 6$:
    
    - $f''(0) = -6 < 0 \Rightarrow x=0$ is a local maximum.
        
    - $f''(2) = 6 \cdot 2 - 6 = 6 > 0 \Rightarrow x=2$ is a local minimum.
        

---

## 2. Critical Points of Multivariable Functions

### 2.1 Gradient and Stationary Points

For f$f(x,y)$, a **stationary point** satisfies:

$abla f(x,y) = \begin{bmatrix} \frac{\partial f}{\partial x} \\ \frac{\partial f}{\partial y} \end{bmatrix} = \begin{bmatrix} 0 \\ 0 \end{bmatrix}$

### 2.2 Hessian Matrix

The **Hessian** of $f(x,y)$ is the matrix of second-order partials:

$H = \begin{bmatrix} \frac{\partial^2 f}{\partial x^2} & \frac{\partial^2 f}{\partial x \partial y} \\ \frac{\partial^2 f}{\partial y \partial x} & \frac{\partial^2 f}{\partial y^2} \end{bmatrix}$

### 2.3 Second Derivative Test (Multivariable)

1. Compute the Hessian $H$ at a stationary point $(x_c, y_c)$.
    
2. Compute the determinant $D = \det(H(x_c, y_c))$.
    
3. Classify:
    
    - If $D > 0$ and $\frac{\partial^2 f}{\partial x^2}(x_c, y_c) > 0, (x_c, y_c)$ is a local minimum.
        
    - If $D > 0$ and $\frac{\partial^2 f}{\partial x^2}(x_c, y_c) < 0, (x_c, y_c)$ is a local maximum.
        
    - If $D < 0, (x_c, y_c)$ is a saddle point.
        
    - If $D = 0$, the test is inconclusive.
        

### 2.4 Example

For $f(x,y) = x^3 + y^3 - 3xy$:

1. Compute partials:
    
    - $f_x = 3x^2 - 3y$
        
    - $f_y = 3y^2 - 3x$
        Set equal to zero: $3x^2 - 3y = 0$ and $3y^2 - 3x = 0$. Solve yields $(0,0)$ and $(1,1)$.
        
2. Hessian:
    
    $H = \begin{bmatrix} 6x & -3 \\ -3 & 6y \end{bmatrix}$
3. Evaluate at $(0,0): H = \begin{bmatrix} 0 & -3 \\ -3 & 0 \end{bmatrix}, D=(−3)(−3)−0=9>0D = (-3)(-3) - 0 = 9 > 0$, and $f_{xx} = 0$ (inconclusive via this test), further analysis shows a saddle at $(0,0)$.
    
4. Evaluate at $(1,1): H = \begin{bmatrix} 6 & -3 \\ -3 & 6 \end{bmatrix}, D = 36 - 9 = 27 > 0, f_{xx} = 6 > 0$, so $(1,1)$ is a local minimum.
    

---

## 3. Constrained Optimization (Intro)

### 3.1 Lagrange Multipliers (Single Constraint)

To optimize $f(x,y)$ subject to constraint $g(x,y) = 0$, form the **Lagrangian**:

$\mathcal{L}(x,y,\lambda) = f(x,y) - \lambda \, g(x,y)$

Set

$\nabla_{x,y,\lambda} \mathcal{L} = 0$

solves
$$\begin{cases}  
\frac{\partial f}{\partial x} - \lambda \frac{\partial g}{\partial x} = 0 \  
\frac{\partial f}{\partial y} - \lambda \frac{\partial g}{\partial y} = 0 \  
g(x,y) = 0.  
\end{cases}$$

### 3.2 Example (Circle Constraint)

Maximize $f(x,y) = x + y$ subject to $g(x,y) = x^2 + y^2 - 1 = 0$:

1. Lagrangian: $\mathcal{L} = x + y - \lambda(x^2 + y^2 - 1)$
    
2. Equations:
    
    - $1 - 2\lambda x = 0 \Rightarrow x = \frac{1}{2\lambda}$
        
    - $1 - 2\lambda y = 0 \Rightarrow y = \frac{1}{2\lambda}$
        
    - x$x^2 + y^2 = 1$
        Solve yields $x = y = \pm\frac{1}{\sqrt{2}}$. Evaluating shows maximum at igl $(\frac{1}{\sqrt{2}}, \frac{1}{\sqrt{2}})$ and minimum at igl$(-\frac{1}{\sqrt{2}}, -\frac{1}{\sqrt{2}})$
        

---