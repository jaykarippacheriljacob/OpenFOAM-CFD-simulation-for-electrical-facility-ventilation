# 0 directory (field initial/boundary conditions)

Used tutorial folder `0` fields as template and replaced values for your case.

Fields edited:
- `U`: incoming velocity 1 m/s at inlet, noSlip at walls/switchgear, zeroGradient outlet.
- `p_rgh`: fixedFluxPressure inlet, fixed 0 outlet, fixedFluxPressure walls/switchgear.
- `T`: 300 K initial, inlet fixed 293 K, outlet zeroGradient, walls adiabatic, switchgear fixedGradient 500.
- `k`: 0.01 initial, inlet fixed 0.01, outlet zeroGradient, walls/switchgear kqRWallFunction.
- `epsilon`: 0.001 initial, inlet fixed 0.001, outlet zeroGradient, walls/switchgear epsilonWallFunction.

This matches your project’s boundary condition plan from README and should be adjusted for geometry/vent locations eventually.
