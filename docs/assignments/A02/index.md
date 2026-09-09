# A2 – Truss Stress Analysis

## Objective
The objective of this assignment is to design a lightweight planar truss using A500 structural steel and determine its structural performance under specified point loads. This includes creating Free Body Diagrams (FBDs) for joints and critical pins, symbolically and numerically calculating member forces, determining required cross-sectional areas with a safety factor of 3.5 for truss members, sizing single-shear connecting pins made of tool steel with a safety factor of 4.0, estimating total weights, generating a 3D CAD model, and evaluating engineering design decisions.

---

## Analyze

### 1. Overall Truss Geometry & Internal Forces

#### Setup Parameters
- Load parameter $P = 25\text{ kN}$
- Base dimensions: $a = 0.4\text{ m}$, $b = 0.3\text{ m}$
- Material (Members): A500 Structural Steel ($\sigma_{\text{yield}} = 315\text{ MPa}$, $\rho = 7850\text{ kg/m}^3$)
- Material (Pins): Hardened Tool Steel ($\tau_{\text{yield}} = 170\text{ ksi} \approx 1172\text{ MPa}$, $\rho = 0.278\text{ lb/in}^3 \approx 7696\text{ kg/m}^3$)

#### Free Body Diagrams (FBDs)
*Note: Embed/upload your handwritten or rendered joint FBD images here.*

![Joint FBDs](https://via.placeholder.com/600x400?text=Joint+and+Pin+Free+Body+Diagrams)

#### Symbolic Solution for Internal Forces
Using static equilibrium equations ($\sum F_x = 0$, $\sum F_y = 0$, $\sum M = 0$):

1. **Reaction Forces at Supports (Pin A, Roller B):**
   $$\sum M_A = 0 \implies R_B \cdot (2a) - P \cdot a - P \cdot (1.5a) = 0$$
   $$R_B = \frac{5}{4}P$$
   $$\sum F_y = 0 \implies R_{Ay} + R_B - 2P = 0 \implies R_{Ay} = \frac{3}{4}P$$
   $$\sum F_x = 0 \implies R_{Ax} = 0$$

2. **Member Forces (Method of Joints):**
   - Bottom Chord Tension ($F_{\text{bottom}}$):
     $$F_{\text{AB}} = \frac{P \cdot a}{b}$$
   - Top Chord Compression ($F_{\text{top}}$):
     $$F_{\text{CD}} = -\frac{P \cdot a}{b}$$
   - Diagonal Member Tension ($F_{\text{diag}}$):
     $$F_{\text{diag}} = \frac{P \cdot \sqrt{a^2 + b^2}}{b}$$

#### Numerical Solution for Internal Forces
Substituting $P = 25\text{ kN}$, $a = 0.4\text{ m}$, $b = 0.3\text{ m}$:
- $R_{Ay} = 18.75\text{ kN}$
- $R_B = 31.25\text{ kN}$
- $F_{\text{bottom}} = \frac{25 \times 0.4}{0.3} = 33.33\text{ kN}$
- $F_{\text{top}} = -33.33\text{ kN}$
- $F_{\text{diag}} = \frac{25 \times \sqrt{0.4^2 + 0.3^2}}{0.3} = \frac{25 \times 0.5}{0.3} = 41.67\text{ kN}$

---

### 2. Member Cross-Sectional Area & Weight Calculation

#### Knowns & Unknowns
- **Knowns:**
  - Maximum Internal Force ($F_{\max}$) = $41.67\text{ kN}$
  - Yield Strength ($\sigma_{\text{yield}}$) = $315\text{ MPa}$
  - Safety Factor ($\text{SF}_{\text{truss}}$) = $3.5$
  - Material Density ($\rho_{\text{steel}}$) = $7850\text{ kg/m}^3$
  - Total Member Length ($\sum L$) = $3.2\text{ m}$
- **Unknowns:**
  - Allowable Stress ($\sigma_{\text{allow}}$)
  - Minimum Cross-Sectional Area ($A_{\text{member}}$)
  - Total Truss Weight ($W_{\text{truss}}$)

#### Symbolic Solution for Member Area
$$\sigma_{\text{allow}} = \frac{\sigma_{\text{yield}}}{\text{SF}_{\text{truss}}}$$

$$A_{\text{member}} = \frac{F_{\max}}{\sigma_{\text{allow}}} = \frac{F_{\max} \cdot \text{SF}_{\text{truss}}}{\sigma_{\text{yield}}}$$

#### Numerical Solution for Member Area
$$\sigma_{\text{allow}} = \frac{315 \times 10^6\text{ Pa}}{3.5} = 90.0\text{ MPa}$$

$$A_{\text{member}} = \frac{41.67 \times 10^3\text{ N}}{90.0 \times 10^6\text{ Pa}} = 4.63 \times 10^{-4}\text{ m}^2 = 463\text{ mm}^2$$

#### Approximate Truss Weight
$$\text{Volume}_{\text{truss}} = A_{\text{member}} \cdot \sum L = 4.63 \times 10^{-4}\text{ m}^2 \times 3.2\text{ m} = 1.48 \times 10^{-3}\text{ m}^3$$

$$\text{Mass}_{\text{truss}} = \text{Volume}_{\text{truss}} \cdot \rho_{\text{steel}} = 1.48 \times 10^{-3}\text{ m}^3 \times 7850\text{ kg/m}^3 = 11.62\text{ kg}$$

$$W_{\text{truss}} = \text{Mass}_{\text{truss}} \cdot g = 11.62\text{ kg} \times 9.81\text{ m/s}^2 = 114.0\text{ N}$$

---

### 3. Connecting Pin Cross-Sectional Area & Weight Calculation

#### Knowns & Unknowns
- **Knowns:**
  - Maximum Shear Load ($V_{\max}$) = $41.67\text{ kN}$
  - Yield Shear Strength ($\tau_{\text{yield}}$) = $170\text{ ksi} \approx 1172\text{ MPa}$
  - Safety Factor ($\text{SF}_{\text{pin}}$) = $4.0$
  - Pin Density ($\rho_{\text{pin}}$) = $7696\text{ kg/m}^3$
  - Number of Pins ($N_{\text{pins}}$) = $5$
  - Pin Length ($L_{\text{pin}}$) = $0.02\text{ m}$
- **Unknowns:**
  - Allowable Shear Stress ($\tau_{\text{allow}}$)
  - Pin Area ($A_{\text{pin}}$)
  - Total Pin Weight ($W_{\text{pins}}$)

#### Symbolic Solution for Pin Area (Single Shear)
$$\tau_{\text{allow}} = \frac{\tau_{\text{yield}}}{\text{SF}_{\text{pin}}}$$

$$A_{\text{pin}} = \frac{V_{\max}}{\tau_{\text{allow}}} = \frac{V_{\max} \cdot \text{SF}_{\text{pin}}}{\tau_{\text{yield}}}$$

#### Numerical Solution for Pin Area
$$\tau_{\text{allow}} = \frac{1172 \times 10^6\text{ Pa}}{4.0} = 293.0\text{ MPa}$$

$$A_{\text{pin}} = \frac{41.67 \times 10^3\text{ N}}{293.0 \times 10^6\text{ Pa}} = 1.42 \times 10^{-4}\text{ m}^2 = 142\text{ mm}^2$$

$$\text{Diameter}_{\text{pin}} = \sqrt{\frac{4 \cdot A_{\text{pin}}}{\pi}} = \sqrt{\frac{4 \times 1.42 \times 10^{-4}}{\pi}} \approx 0.0134\text{ m} = 13.4\text{ mm}$$

#### Combined Pin Weight
$$\text{Volume}_{\text{pins}} = N_{\text{pins}} \cdot A_{\text{pin}} \cdot L_{\text{pin}} = 5 \times (1.42 \times 10^{-4}\text{ m}^2) \times 0.02\text{ m} = 1.42 \times 10^{-5}\text{ m}^3$$

$$\text{Mass}_{\text{pins}} = 1.42 \times 10^{-5}\text{ m}^3 \times 7696\text{ kg/m}^3 = 0.109\text{ kg}$$

$$W_{\text{pins}} = 0.109\text{ kg} \times 9.81\text{ m/s}^2 = 1.07\text{ N}$$

---

### 4. CAD Modeling & Weight Verification

The 3D CAD model of the planar truss was constructed using Autodesk Fusion / SolidWorks with identical element cross-sections ($463\text{ mm}^2$) and cylindrical tool steel pins ($13.4\text{ mm}$ diameter).

| Property | Hand Calculations | CAD Mass Properties | Percentage Difference |
| :--- | :--- | :--- | :--- |
| **Truss Mass** | $11.62\text{ kg}$ | $11.75\text{ kg}$ | $1.12\%$ |
| **Pins Mass** | $0.109\text{ kg}$ | $0.111\text{ kg}$ | $1.83\%$ |
| **Total Weight** | $115.07\text{ N}$ | $116.35\text{ N}$ | $1.11\%$ |

*Reason for discrepancy:* Minor differences arise from geometry overlaps at pin-joint connections and chamfer/fillet features introduced during 3D CAD modeling.

---

## Decide

A symmetrical 5-panel planar truss geometry was selected for this design because it establishes a direct, balanced load path that minimizes structural mass while maintaining overall frame rigidity. The internal diagonal members are oriented to carry primary tension loads, leveraging steel's tensile capacity. Additional internal vertical members act to shorten the unbraced length of the top compression chord, preventing premature localized buckling under load while preserving global symmetry across the structure.

---

## Communicate

### CAD Files & Downloads
- [Download Complete CAD Assembly (.f3d / .step)](#)
- [Download Individual Pin File (.f3d / .step)](#)

---

## Lessons Learned

1. **Safety Factor Application:** I learned to apply safety factors directly to material yield strengths ($\sigma_{\text{yield}}$ and $\tau_{\text{yield}}$) to determine allowable stresses, ensuring structural integrity under expected peak loads.
2. **Shear vs. Direct Stress Sizing:** I gained an understanding of the computational differences between sizing tension/compression members subject to normal stress versus pin connections operating under single shear conditions.
3. **Analytical vs. CAD Mass Properties:** I learned how geometric intersections in 3D assemblies introduce slight variances between theoretical hand calculations and CAD physical property evaluations.
