Heat Transfer Setup

## Purpose
Simulate 1-D Transient Heat Transfer using numerical methods and plot out the results

## Governing Equation
Starting from the general heat conduction equation with no internal generation:
```math
\nabla \cdot (k \nabla T) = \rho c_p \frac{\partial T}{\partial t}
```
Select the 1-D heat conduction type:
```math
k \frac{\partial^2 T}{\partial x^2} = \rho c_p \frac{\partial T}{\partial t}
```
With 
```math
\alpha = \frac{k}{\rho c_p}
```
the equation becomes:
```math
\frac{\partial T}{\partial t} = \alpha \frac{\partial^2 T}{\partial x^2}
```

## Assumptions for a Plane Wall
- Constant properties, no internal generation, a wall thin in one direction
#depends if we want to set it this way

## Initial Conditions
- Uniform temperature
$T(x, 0) = T_i$
## Boundary Conditions
- Fixed temperature at both faces (Dirichlet)
$T(0,t) = T_s, \quad T(L,t) = T_s$

## Nondimensionalization

**Dimensionless Groups**\
We start by choosing dimentionless groups:
```math
\theta = \frac{T-T_\infty}{T_i - T_\infty}, \qquad \xi = \frac{x}{L_c}, \qquad \tau = \frac{t}{t_c}
```
Re-organizing them we obtain:
```math
T = \theta(T_i-T_\infty) + T_\infty, \qquad x = \xi L_c, \qquad t = \tau t_c
```

**Substitution** \
Substituting the dimentionless groups into the equation
```math
\frac{\partial T}{\partial t} = \alpha \frac{\partial^2 T}{\partial x^2}
```
we can obtain
```math
\frac{T_i - T_\infty}{t_c} \frac{\partial \theta}{\partial \tau} = \alpha \frac{T_i - T_\infty}{L_c^2} \frac{\partial^2 \theta}{\partial \xi^2}
```
cancelling the term $(T_i-T_\infty)$ and regrouping we get:
```math
\frac{\partial \theta}{\partial \tau} = \frac{\alpha t_c}{L_c^2} \frac{\partial^2 \theta}{\partial \xi^2}
```

**Choice of  scale** \
Since the dimention is typically given, we choose the length scale
```math
L_c = L
```
and we choose the time scale to allow $\frac{\alpha t_c}{L^2} = 1$:
```math
t_c = \frac{L^2}{\alpha}
```

**Result**\
Notice that the dimentionless time variable $\tau$ actually equals to the Fourier's Number $\mathrm{Fo}$. 

```math
\tau = \frac{t}{t_c} = \frac{\alpha t}{L^2} = \mathrm{Fo}
```
Our dimnetionless equation becomes:
```math
\frac{\partial \theta}{\partial \mathrm{Fo}} = \frac{\partial^2 \theta}{\partial \xi^2}, \qquad \mathrm{Fo} = \frac{\alpha t}{L^2}

```

**Interpretation** \
Fo is the ratio of the time elapsed $t$ to the characteristic diffusion time across the wall, $t_c = L^2/\alpha$.

## Rewriting Initial and Boundary Conditions
We will rewrite the IC and BC's from $T(x,t)$ format to using the dimensionless variables $\theta(\xi,\mathrm{Fo})$ format.\
Recall that
```math
\theta = \frac{T-T_\infty}{T_i - T_\infty}, \qquad \xi = \frac{x}{L_c}, \qquad \tau = \frac{t}{t_c}
```

**IC:** 
```math
T(x,0) = T_i,
```
```math
t = 0,\qquad
\tau = 0,\qquad
```
```math
\theta = \frac{T_i-T_\infty}{T_i-T_\infty} = 1, 
```
We get:
```math
\theta (\xi, 0) = 1, \qquad 0 < \xi < 1
```
**BC:**\
Left face:
Since
```math
T(0,t) = T_\infty,
```
where
```math
x=0, \qquad \xi = 0.
```
Thus
```math
\theta = \frac{T_\infty-T_\infty}{T_i-T_\infty} = 0,
```
Thus
```math
\theta(0,Fo) = 0.
```

Right Face:
Since
```math
T(L,t) = T_\infty,
```
where
```math
x=L, \qquad \xi = 1.
```
Thus
```math
\theta = \frac{T_\infty-T_\infty}{T_i-T_\infty} = 0,
```
thus
```math
\theta(1,Fo) = 0.
```

## Separation of Variables (for Analytical Solution)
Let us set 
```math
\theta (\xi, \mathrm{Fo}) = X(\xi)\tau(\mathrm{Fo})
```
and
```math
\frac{\partial\theta}{\partial\xi} = \tau \frac{\mathrm{d}X}{\mathrm{d}\xi},
\qquad 
\frac{\partial^2\theta}{\partial\mathrm{Fo}^2} = X \frac{\mathrm{d}^2\tau}{\mathrm{d}\mathrm{Fo}^2}.

```
Substituting back in to the dimensionless heat equation, we have:
```math
\tau X'= X \tau",
```
regrouping, we get:
```math
\frac{X'}{X} = \frac{\tau"}{\tau}.
```
Since neither side of equaiton depends on eachothers' independent variables, we conclude they are constants and set:
```math
\frac{X'}{X} = -\lambda = \frac{\tau"}{\tau}

```
This results in:
```math
x'  = -\lambda X , \qquad and \qquad \tau" = - \lambda \tau.
```

Looking at the first equation, the possible and common solution is to have 
```math
X(\xi)= e^{-\lambda \xi}, \qquad and \qquad X' = -\lambda e^{\lambda \xi}.
```
Based on Euler's Formula :
```math
e^{i\theta} = cos \theta + \mathrm{i} sin\theta
```
X can be rewritten as :
```math
X = cos \xi -\lambda sin \xi
```
Now, we look at $\tau(\mathrm{Fo})$,
THe possible solution is:
```math
\tau(\mathrm{Fo}) = e^{\sqrt{-\lambda}\mathrm{Fo}}, \qquad and \qquad \tau" = -\lambda e^{\sqrt{-\lambda}\mathrm{Fo}}
```
To deal with $\sqrt{-\lambda}$, we can set:
```math
\sqrt{-\lambda} = k, and -\lambda = k^2.
```
Implementing Euler's Formula again, we have:
```math
\tau = cos \mathrm{Fo} + \mathrm{k} sin \mathrm{Fo}
```
## Bibliography
1. https://math.libretexts.org/Bookshelves/Differential_Equations/Differential_Equations_for_Engineers_%28Lebl%29/4%3A_Fourier_series_and_PDEs/4.06%3A_PDEs_separation_of_variables_and_the_heat_equation
2. https://www.math.toronto.edu/ivrii/PDE-textbook/Chapter4/S4.1.html
3. https://ocw.mit.edu/courses/18-303-linear-partial-differential-equations-fall-2006/d11b374a85c3fde55ec971fe587f8a50_heateqni.pdf
4. 