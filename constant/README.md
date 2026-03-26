# constant directory (physical and turbulence properties)

From tutorial base to project:
- `physicalProperties`: switched to Boussinesq air properties and to `sensibleInternalEnergy` for the solver.
- `turbulenceProperties`: direct assignment to RAS kEpsilon (steady-state turbulence model desired).
- `g`: set global gravity to (0 0 -9.81).

These settings are aligned with floating-room buoyant convection and 33kV equipment buoyancy.
