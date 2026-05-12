# AutoFit MAT024 - 4a Model

Source: slide titled **"AutoFit MAT024 - 4a_Model"** (Date: 30 September 2025).

## Overview

The 4a model describes plastic behavior using:

1. The **meta model of Schmachtenberg** for hardening evolution.
2. A **linear hardening increase** controlled by coefficient \(h_{ET} / e_E\).
3. **Strain-rate dependency** based on **Johnson-Cook**.

## Constitutive Terms Captured from Slide

### 1) Plastic behavior (Schmachtenberg meta model)

\[
h_y + e_E \cdot \varepsilon_{pl} \cdot
\frac{1 + \dfrac{h_{ET}\,\varepsilon_{pl}}{e_E}}
{1 + \dfrac{e_E\,\varepsilon_{pl}}{h_n}}
\]

### 2) Linear hardening increase coefficient

\[
\frac{h_{ET}}{e_E}
\]

### 3) Strain-rate dependency (Johnson-Cook form)

\[
1 + \frac{1}{v_p} \cdot \log\!\left(
\frac{\max(\dot{\varepsilon},\,\dot{\varepsilon}_0)}{\dot{\varepsilon}_0}
\right)
\]

## Diagram Interpretation (stress-strain plot)

- Vertical axis: **stress**.
- Horizontal axis: **strain**.
- Initial slope region marked near **arctan \(e_E\)** (elastic modulus-related region).
- Baseline stress offset indicated by **\(h_y\)**.
- Additional hardening component indicated by **\(h_h\)**.
- Family of curves (different colors) shows variation with model parameters and rate effects.
- Annotations indicate influence of **\(v_p\)**, **\(\dot{\varepsilon}_0\)**, and **\(\dot{\varepsilon}\)**.
- Upper trend indicates effect of hardening ratio **\(h_{ET}/e_E\)**.

## Symbol Notes (from slide context)

- \(\varepsilon_{pl}\): plastic strain.
- \(\dot{\varepsilon}\): strain rate.
- \(\dot{\varepsilon}_0\): reference strain rate.
- \(h_y\): yield-related stress level term.
- \(h_h\): hardening contribution term.
- \(h_{ET}\): tangent hardening-related parameter.
- \(e_E\): elastic-modulus-related parameter.
- \(h_n\): denominator hardening-shape parameter.
- \(v_p\): Johnson-Cook rate sensitivity parameter.

## Practical Reminder

This note is a transcription for quick reference. If this model is to be implemented in code or solver cards, confirm exact variable definitions and units from the original material database/specification.
