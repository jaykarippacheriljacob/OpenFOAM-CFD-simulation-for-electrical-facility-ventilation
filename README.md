# OpenFOAM CFD Case — 33kV Switchgear Room Ventilation

## Overview
This project simulates **steady-state turbulent buoyant airflow with heat transfer** in a 33kV switchgear room using OpenFOAM.

### Objectives
- Predict airflow distribution
- Evaluate cooling effectiveness
- Identify thermal hotspots

---

## Geometry

### Room
- Rectangular domain: `10m x 6m x 4m`

### Internal Objects
- 2–4 switchgear cabinets (rectangular blocks)
- Located at center of room
- Represent heat sources

### Ventilation
- Inlet: side wall
- Outlet: opposite wall

---

## Physics

| Feature | Model |
|--------|------|
| Solver | buoyantSimpleFoam |
| Flow | Steady-state |
| Turbulence | k-epsilon |
| Density | Boussinesq |
| Heat Transfer | Enabled |

---

## Case Structure

```text
case/
├── 0/
│   ├── U
│   ├── p_rgh
│   ├── T
│   ├── k
│   ├── epsilon
├── constant/
│   ├── polyMesh/
│   ├── thermophysicalProperties
│   ├── turbulenceProperties
│   ├── g
├── system/
│   ├── blockMeshDict
│   ├── snappyHexMeshDict
│   ├── fvSchemes
│   ├── fvSolution
│   ├── controlDict

```
---

## Boundary Conditions (`0/`)

### Velocity (`U`)
- inlet: `fixedValue` (e.g., 1 m/s)
- outlet: `zeroGradient`
- walls: `noSlip`
- switchgear: `noSlip`

### Temperature (`T`)
- inlet: `fixedValue` (293 K)
- outlet: `zeroGradient`
- walls: `zeroGradient` (adiabatic)
- switchgear: `fixedGradient` (heat flux)

### Pressure (`p_rgh`)
- outlet: `fixedValue` (0)
- others: `fixedFluxPressure`

### Turbulence (`k` & `epsilon`)
- Initialized with small values
- Wall functions on walls and switchgear

---

## Physical Properties (`constant/`)

### thermophysicalProperties
- Air using Boussinesq approximation
- `rhoRef = 1.2`
- `beta = 3.3e-3`
- `TRef = 300 K`

### turbulenceProperties
- RAS model: `kEpsilon`
- Turbulence: on

### Gravity (`g`)
(0 0 -9.81)


---

## Mesh

### Option 1: blockMesh
- Structured grid
- Simple geometry

### Option 2: snappyHexMesh (recommended)
- STL geometry for:
  - switchgear
  - vents
- Refinement near:
  - inlets/outlets
  - heat sources

---

## Numerical Setup (`system/`)

### fvSchemes
- Upwind schemes for stability

### fvSolution
- SIMPLE algorithm
- Relaxation factors:
  - `p_rgh`: 0.3
  - `U`, `T`: 0.7

### controlDict
- Solver: `buoyantSimpleFoam`
- Steady-state
- Write interval configurable

---

## Running the Case

```bash
blockMesh
# optional:
snappyHexMesh -overwrite
buoyantSimpleFoam

## paraFoam
