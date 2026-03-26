# system directory (numerical and control settings)

Base from tutorial:
- `fvSchemes`: steady-state treatment, upwind for convective fluxes, Gauss linear for gradients and diffusion.
- `fvSolution`: standard p_rgh + U/k/epsilon solvers with relaxation factors.

Adapted for project:
- `controlDict`: `application buoyantSimpleFoam`, stopAt endTime 2000, deltaT 1, write every 100.

This ensures correct solver dispatch and stable convergence for your steady buoyant simulation.
