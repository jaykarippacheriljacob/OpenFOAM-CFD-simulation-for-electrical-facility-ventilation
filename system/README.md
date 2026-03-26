# system directory (numerical and control settings)

Base case: `hotRoomBoussinesqSteady` with modifications for switchgear ventilation.

What was changed:
- `controlDict`: set `application buoyantSimpleFoam`.
- `blockMeshDict`: replaced with project-specific room geometry (10 x 6 x 4 m, central switchgear block, inlet at left wall, outlet at right wall).
- `fvSchemes`: steady-state and Boussinesq-suitable schemes from tutorial.
- `fvSolution`: solver settings for p_rgh, U, h, k, epsilon with relaxation factors.

How to run:
- `./Allclean`
- `./Allrun`

Post-process:
- `foamToVTK`
- ParaView (local or pvpython headless).
