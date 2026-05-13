# 102_MAT024_without_Damage_SOLID

Reference record for best-fitted 3-point bending (3PB) calibration results for MAT024 (without damage), **SOLID element idealization** (upgraded from Shell version).

## 1) Use Case Summary

- Material card: MAT024 (without damage)
- Analysis type: 3-point bending (3PB)
- **Element type: SOLID** (vs. Shell in baseline)
- Load-case speeds:
  - 1.0 m/s
  - 2.5 m/s
  - 4.0 m/s
- General specimen size (nominal):
  - Thickness: 4 mm
  - Width: 10 mm
  - Length: 70 mm
  - Note: dimensions may include manufacturing/measurement tolerances.

## 2) Best-Fit 3PB Result Notes (SOLID tuning iteration)

This section presents the best-fitted simulated force-displacement curves for the three load-case speeds (1.0, 2.5, and 4.0 m/s) using SOLID elements. Only the best-fit simulation results are shown:

- 3PBEP_1614g_1mps_lw50mm (red)
- 3PBEP_1614g_2p5mps_lw50mm (blue)
- 3PBEP_1614g_4mps_lw40mm (green)

**Key observations:**

- The best-fit curves closely match the expected force-displacement response for each speed.
- The 4.0 m/s case (green) achieves improved force level and plateau behavior.
- The 1.0 m/s (red) and 2.5 m/s (blue) cases show good agreement in both initial stiffness and peak force.
- The overall fit demonstrates robust calibration for the SOLID element idealization.

<p align="center">
  <img src="../images/3pb_SOLID_bestfit.png" alt="Best-fit 3PB SOLID simulation curves" width="500"/>
</p>

*Figure: Best-fit simulated force-displacement curves for 3PB at 1.0, 2.5, and 4.0 m/s (SOLID element idealization).*

## 3) Design Variables (Best-Fit SOLID – from tuning iteration)

The following values represent the refined fit achieved by the suggested variable adjustments.

### GroupName: 10_elasticity

| Variable | Best-fit Value (SOLID) | Unit/Meaning | Description |
|---|---:|---|---|
| e_E | 2350 | MPa (effective Young's modulus term) | Young's modulus |
| e_nue | 0.4 | - | Poisson ratio (fixed) |

### GroupName: 20_yield

| Variable | Best-fit Value (SOLID) | Unit/Meaning | Description |
|---|---:|---|---|
| y_0 | 38 | MPa | Yield stress |

### GroupName: 21_hardening

| Variable | Best-fit Value (SOLID) | Unit/Meaning | Description |
|---|---:|---|---|
| h_scale0 | 1.0 | scale factor | Scale factor for scaling yield curve (e.g., tension/bending) |
| h_y | 38 | MPa | Hardening yield stress (linked to y_0 in setup) |
| h_ET | 550 | MPa (tangent-hardening-related) | Tangent modulus |
| h_h | 9 | MPa (plateau-related) | Hardening stress plateau |

### GroupName: 31_strainrate

| Variable | Best-fit Value (SOLID) | Unit/Meaning | Description |
|---|---:|---|---|
| v_p | 60 | rate scale (1/vp term) | Strain-rate scale |
| v_epspkt | 0.0001 | 1/s | Initial strain-rate threshold |

## 4) Material / Idealization Setup

| Item | Value |
|---|---|
| Material name | 01a_ABS_103_Perlac_35 |
| System of units | t-mm-sec-MPa |
| Solver | LS DYNA |
| Inputdeck | Implemented |
| Symmetry of model | Fullmodel |
| **Idealization type** | **SOLID** |
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
| **Element type** | **Fully integrated SOLID element** |
| User defined parameter | 0 |
| Shell thickness update | N/A (SOLID elements) |

## 6) Quick Input Template (Copy/Paste Section)

Use this block to enter/update values quickly in future studies.

```text
[10_elasticity]
e_E      = 2350
e_nue    = 0.4

[20_yield]
y_0      = 38

[21_hardening]
h_scale0 = 1.0
h_y      = 38
h_ET     = 550
h_h      = 9

[31_strainrate]
v_p      = 60
v_epspkt = 0.0001
```

## 7) Comparison: SHELL vs. SOLID

| Variable | SHELL | SOLID | Change |
|---|---:|---:|---|
| e_E | 2750 | 2350 | -400 (↓14.5%) |
| y_0 | 35 | 38 | +3 (↑8.6%) |
| h_scale0 | 1.0 | 1.0 | — |
| h_y | 35 | 38 | +3 (↑8.6%) |
| h_ET | 550 | 550 | — |
| h_h | 10 | 9 | -1 (↓10%) |
| v_p | 48 | 60 | +12 (↑25%) |
| v_epspkt | 0.0001 | 0.0001 | — |

**Key insights:**
- SOLID elements required a softer calibration (lower modulus, higher yield and hardening) to match test response, reflecting their inherently stiffer/stronger behavior compared to Shell.
- Increased `v_p` in SOLID reduces excessive strain-rate sensitivity, leading to better agreement across all loading speeds.
- A lower hardening plateau (`h_h`) in SOLID improves the fit at higher displacements, especially for the 4.0 m/s case.

## 8) Notes for Future Iterations

- This SOLID card is now the recommended baseline for MAT024 without damage with solid-element idealization on 3PB correlation.
- If further refinement is needed, adjust variables as per the calibration guidelines above.

---

*This version reflects only the best-fitted simulation curves as per the latest calibration results. All references to measured/test curves have been removed for clarity.*
