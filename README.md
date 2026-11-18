Heat Transfer Setup

## Purpose
Simulate 1-D Transient Heat Transfer using numerical methods and plot out the results

## Governing Equation
Starting from the general heat conduction equation with no internal generation:
$$
\nabla \cdot (k \nabla T) = \rho c_p \frac{\partial T}{\partial t}
$$
Select the 1-D heat conduction type:
$$
k \frac{\partial^2 T}{\partial x^2} = \rho c_p \frac{\partial T}{\partial t}
$$
With 
$\alpha = \frac{k}{\rho c_p}$,
the equation becomes:
$\frac{\partial T}{\partial t} = \alpha \frac{\partial^2 T}{\partial x62}$

## Assumptions For a Plane Wall
- Constant properties, no internal generation, a wall thin in one direction
#depends if we want to set it this way

## Initial Conditions
- Uniform temperature
$$
T(x, t=0) = T_o
$$
## Boundary Conditions
- Fixed temperature at both faces (Dirichlet)
$$
T(0,t) = T_s, \quad T(L,t) = T_s
$$
## Dimensionless Groups
We start by choosing dimentionless groups:
$\theta = \frac{T-T_\inf}{T_i - T_\inf} ; \qquad \xi = \frac{x}{L_c} ; \tao = \frac{t}{t_c}$
