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
```math
T(0,t) = T_\infty,
```
```math
x=0, \qquad \xi = 0.
```
```math
\theta = \frac{T_i-T_\infty}{T_i-T_\infty} = 1
```
So
```math
\theta(0,Fo) = 1
```

Right Face:
```math
T(L,t) = T_\infty,
```
```math
x=L l \qquad \xi = 1.
```
```math
\theta = \frac{T_i-T_\infty}{T_i-T_\infty} = 1
```
So
```math
\theta(1,Fo) = 1
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
Since each side of equaiton depends on different independent variables, we set:
```math
\frac{X'}{X} = -\lambda = \frac{\tau"}{\tau}

```