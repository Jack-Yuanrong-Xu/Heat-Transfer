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

## Assumptions For a Plane Wall
- Constant properties, no internal generation, a wall thin in one direction
#depends if we want to set it this way

## Initial Conditions
- Uniform temperature
$T(x, 0) = T_0$
## Boundary Conditions
- Fixed temperature at both faces (Dirichlet)
$T(0,t) = T_s, \quad T(L,t) = T_s$

## Nondimensionalization

**Dimensionless Groups**
We start by choosing dimentionless groups:
```math
\theta = \frac{T-T_\infty}{T_i - T_\infty}; \qquad \xi = \frac{x}{L_c}; \qquad \tau = \frac{t}{t_c}

Re-organizing them we obtain:
```math
T = \theta(T_i-T_\infty) + T_\infty, \qquad x = \xi L_c, \qquad t = \tau t_c
```

**Substitution.** [your chain-rule steps]
Substituting the dimentionless groups into the equation
```math
\frac{\partial T}{\partial t} = \alpha \frac{\partial^2 T}{\partial x^2}
```
we can obtain
```math
\frac{T_i - T_\infty}{t_c} \frac{\partial \theta}{\partial \tau} = alpha \frac{T_i - T_\infty}{L_c^2} \frac{\partial^2 \theta}{\partial \xi^2}
```
cancelling the term $(T_i-T_\infty)$ and regrouping we get:
```math
\frac{\partial \theta}{\partial \tau} = \frac{\alpha t_c}{L_c} \frac{\partial^2 \theta}{\partial \xi^2}
```

**Choice of  scale.** 
we could set the time scale
```math
t_c = 1
```
and the length scale
```math
L_c = \sqrt{\alpha}
```

**Result.**

Notice that the term $\frac{\alpha t_c}{L_c}$ is actually the Fourier's Number $Fo$.

Our dimnetionless equation becomes:
```math
\frac{\partial \theta}{\partial \tau} = Fo \frac{\partial^2 \theta}{\partial \xi^2}
```

$$
\frac{\partial \theta}{\partial \mathrm{Fo}} = \frac{\partial^2 \theta}{\partial \xi^2}, \qquad \mathrm{Fo} = \frac{\alpha t}{L^2}
$$

**Interpretation.** Fo is the ratio of the time elapsed to the diffusion time across the wall, $L^2/\alpha$.

