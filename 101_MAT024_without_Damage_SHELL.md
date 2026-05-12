# 101_MAT024_without_Damage_SHELL

Reference record for best-fitted 3-point bending (3PB) calibration results for MAT024 (without damage), Shell idealization.

## 1) Use Case Summary

- Material card: MAT024 (without damage)
- Analysis type: 3-point bending (3PB)
- Load-case speeds:
  - 1.0 m/s
  - 2.5 m/s
  - 4.0 m/s
- General specimen size (nominal):
  - Thickness: 4 mm
  - Width: 10 mm
  - Length: 70 mm
  - Note: dimensions may include manufacturing/measurement tolerances.

## 2) Best-Fit 3PB Result Notes (from plot)

Plot legend indicates fitted/simulated curves against measured responses for:

- 3PBEP_1614g_1mps_lw50mm
- 3PBEP_1614g_2p5mps_lw50mm
- 3PBEP_1614g_4mps_lw40mm

Observed trend from the plotted force-displacement curves:

- 4.0 m/s case shows the highest force level.
- 1.0 m/s and 2.5 m/s are lower and closer to each other than to 4.0 m/s.
- Typical fitted quality text shown in the legend includes avg/max percentage error for each case.

## 3) Design Variables (Grouped for Easy Future Input)

The following grouping mirrors the screenshot layout so users can quickly input/update values.

### GroupName: 10_elasticity

| Variable | Best-fit/Current Value | Unit/Meaning | Description |
|---|---:|---|---|
| e_E | 2750 | MPa (effective Young's modulus term) | Young's modulus |
| e_nue | 0.4 | - | Poisson ratio |

### GroupName: 20_yield

| Variable | Best-fit/Current Value | Unit/Meaning | Description |
|---|---:|---|---|
| y_0 | 35 | MPa | Yield stress |

### GroupName: 21_hardening

| Variable | Best-fit/Current Value | Unit/Meaning | Description |
|---|---:|---|---|
| h_scale0 | 1.0 | scale factor | Scale factor for scaling yield curve (e.g., tension/bending) |
| h_y | 35 | MPa | Hardening yield stress (linked to y_0 in setup) |
| h_ET | 550 | MPa (tangent-hardening-related) | Tangent modulus |
| h_h | 10 | MPa (plateau-related) | Hardening stress plateau |

### GroupName: 31_strainrate

| Variable | Best-fit/Current Value | Unit/Meaning | Description |
|---|---:|---|---|
| v_p | 48 | rate scale (1/vp term) | Strain-rate scale |
| v_epspkt | 0.0001 | 1/s | Initial strain-rate threshold |

## 4) Material / Idealization Setup

| Item | Value |
|---|---|
| Material name | 01a_ABS_103_Perlac_35 |
| System of units | t-mm-sec-MPa |
| Solver | LS DYNA |
| Inputdeck | Implemented |
| Symmetry of model | Fullmodel |
| Idealization type | Shell |
| Element size | 1 |

## 5) Additional Settings

| Item | Value |
|---|---|
| Friction coefficient | 0.3 |
| Contact thickness | 1 |
| Young's Modulus of support / fin | 210000 |
| Density of support / fin | 7800 |
| Time scaling | 0 |
| Number of element layers | 5 |
| Write part/section | Yes |
| Scale the thickness to the measured specimen thickness | Yes |
| Element type | 16: Fully integrated shell element (very fast) |
| User defined parameter | 0 |
| Shell thickness update | with change in thickness |

## 6) Quick Input Template (Copy/Paste Section)

Use this block to enter/update values quickly in future studies.

```text
[10_elasticity]
e_E      = 2750
e_nue    = 0.4

[20_yield]
y_0      = 35

[21_hardening]
h_scale0 = 1.0
h_y      = 35
h_ET     = 550
h_h      = 10

[31_strainrate]
v_p      = 48
v_epspkt = 0.0001
```

## 7) Notes for Future Iterations

- Keep this file as the baseline for MAT024 without damage (Shell) for 3PB correlation.
- When updating values, preserve the same variable grouping to avoid input mistakes.
- Record specimen tolerance bands here when available (thickness/width/length min-max), since they affect bending stiffness and force response.
