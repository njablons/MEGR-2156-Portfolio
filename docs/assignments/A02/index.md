# A2 – Design with Basic Stresses

## Objective
The goal of this assignment is to design a lightweight planar truss using A500 structural steel and size its critical joints and pins under specified point loads. To achieve an optimal strength-to-weight ratio, structural members are evaluated using allowable normal stress criteria with a safety factor of 3.5, while hardened tool steel connecting pins are sized under single-shear conditions with a safety factor of 4.0. The complete workflow involves creating joint Free Body Diagrams (FBDs), executing symbolic and numerical stress calculations, building a 3D CAD model, and comparing hand-calculated mass predictions against CAD analytical data.

---

## Analyze

### 1. Overall Truss Geometry & Internal Forces

#### Overview & Methodology
- **Why:** Determining internal forces across all structural members is required to identify the peak tension and compression loads for member sizing.
- **How:** Static equilibrium equations ($\sum F_x = 0$, $\sum F_y = 0$, $\sum M = 0$) were applied to the global frame to find support reactions, followed by the Method of Joints applied node-by-node.
- **What:** A symmetrical 5-panel planar truss geometry was established using specified parameters ($P = 25\text{ kN}$, $a = 0.4\text{ m}$, $b = 0.3\text{ m}$).

#### Setup Parameters
- Load Parameter: $P = 25\text{ kN}$
- Geometric Dimensions: $a = 0.4\text{ m}$, $b = 0.3\text{ m}$
- Truss Material: A500 Structural Steel ($\sigma_{\text{yield}} = 315\text{ MPa}$, $\rho = 7850\text{ kg/m}^3$)
- Pin Material: Hardened Tool Steel ($\tau_{\text{yield}} = 170\text{ ksi} \approx 1172\text{ MPa}$, $\rho = 7696\text{ kg/m}^3$)

#### Free Body Diagrams (FBDs)
Below are the detailed Free Body Diagrams illustrating global support reactions at Pin A and Roller B, alongside node equilibrium diagrams for critical joints.

![Truss Global and Joint Free Body Diagrams](https://raw.githubusercontent.com/njablons/MEGR-2156-Portfolio/main/docs/assignments/A02/fbd_diagram.png)

#### Symbolic Solution for Internal Forces
1. **Reaction Forces at Supports:**
   $$\sum M_A = 0 \implies R_B \cdot (2a) - P \cdot a - P \cdot (1.5a) = 0 \implies R_B = \frac{5}{4}P$$
   $$\sum F_y = 0 \implies R_{Ay} + R_B - 2P = 0 \implies R_{Ay} = \frac{3}{4}P$$
   $$\sum F_x = 0 \implies R_{Ax} = 0$$

2. **Member Forces (Method of Joints):**
   - Bottom Chord Tension ($F_{\text{bottom}}$): $F_{\text{bottom}} = \frac{P \cdot a}{b}$
   - Top Chord Compression ($F_{\text{top}}$): $F_{\text{top}} = -\frac{P \cdot a}{b}$
   - Diagonal Member Tension ($F_{\text{diag}}$): $F_{\text{diag}} = \frac{P \cdot \sqrt{a^2 + b^2}}{b}$

#### Numerical Solution for Internal Forces
Substituting $P = 25\text{ kN}$, $a = 0.4\text{ m}$, and $b = 0.3\text{ m}$:
- $R_{Ay} = 18.75\text{ kN}$
- $R_B = 31.25\text{ kN}$
- $F_{\text{bottom}} = \frac{25 \times 0.4}{0.3} = 33.33\text{ kN}$
- $F_{\text{top}} = -33.33\text{ kN}$
- $F_{\text{diag}} = \frac{25 \times \sqrt{0.4^2 + 0.3^2}}{0.3} = 41.67\text{ kN}$

---

### 2. Member Cross-Sectional Area & Weight Calculation

#### Overview & Methodology
- **Why:** Sizing the truss members based on the peak internal load ensures the structure will not yield under full operational loading conditions.
- **How:** The allowable normal stress was calculated using material yield strength divided by a safety factor of 3.5, which was then used to determine the minimum cross-sectional area and total structural volume.
- **What:** Calculated the required cross-sectional area ($463\text{ mm}^2$) and estimated total truss weight ($114.0\text{ N}$).

#### Knowns & Unknowns
- **Knowns:**
  - $F_{\max} = 41.67\text{ kN}$
  - $\sigma_{\text{yield}} = 315\text{ MPa}$
  - $SF_{\text{truss}} = 3.5$
  - $\rho_{\text{steel}} = 7850\text{ kg/m}^3$
  - $\sum L_{\text{members}} = 3.2\text{ m}$
- **Unknowns:**
  - Allowable Stress ($\sigma_{\text{allow}}$)
  - Minimum Cross-Sectional Area ($A_{\text{member}}$)
  - Total Truss Weight ($W_{\text{truss}}$)

#### Symbolic Solution for Member Area
$$\sigma_{\text{allow}} = \frac{\sigma_{\text{yield}}}{SF_{\text{truss}}}$$

$$A_{\text{member}} = \frac{F_{\max}}{\sigma_{\text{allow}}} = \frac{F_{\max} \cdot SF_{\text{truss}}}{\sigma_{\text{yield}}}$$

#### Numerical Solution for Member Area
$$\sigma_{\text{allow}} = \frac{315 \times 10^6\text{ Pa}}{3.5} = 90.0\text{ MPa}$$

$$A_{\text{member}} = \frac{41.67 \times 10^3\text{ N}}{90.0 \times 10^6\text{ Pa}} = 4.63 \times 10^{-4}\text{ m}^2 = 463\text{ mm}^2$$

#### Approximate Truss Weight
$$\text{Volume}_{\text{truss}} = A_{\text{member}} \cdot \sum L = 4.63 \times 10^{-4}\text{ m}^2 \times 3.2\text{ m} = 1.48 \times 10^{-3}\text{ m}^3$$

$$\text{Mass}_{\text{truss}} = \text{Volume}_{\text{truss}} \cdot \rho_{\text{steel}} = 1.48 \times 10^{-3} \times 7850 = 11.62\text{ kg}$$

$$W_{\text{truss}} = \text{Mass}_{\text{truss}} \cdot g = 11.62\text{ kg} \times 9.81\text{ m/s}^2 = 114.0\text{ N}$$

---

### 3. Connecting Pin Cross-Sectional Area & Weight Calculation

#### Overview & Methodology
- **Why:** Connecting pins must be properly sized to prevent failure from direct single-shear stresses at joint interfaces.
- **How:** The allowable shear stress was computed by dividing tool steel yield shear strength by a safety factor of 4.0, which yielded the required pin diameter and combined fastener mass.
- **What:** Determined pin cross-sectional area ($142\text{ mm}^2$), pin diameter ($13.4\text{ mm}$), and combined pin weight ($1.07\text{ N}$).

#### Free Body Diagram of Peak Load Pin
![Pin Single Shear Free Body Diagram](https://raw.githubusercontent.com/njablons/MEGR-2156-Portfolio/main/docs/assignments/A02/pin_fbd.png)

#### Knowns & Unknowns
- **Knowns:**
  - $V_{\max} = 41.67\text{ kN}$
  - $\tau_{\text{yield}} = 170\text{ ksi} \approx 1172\text{ MPa}$
  - $SF_{\text{pin}} = 4.0$
  - $\rho_{\text{pin}} = 7696\text{ kg/m}^3$
  - $N_{\text{pins}} = 5$, $L_{\text{pin}} = 0.02\text{ m}$
- **Unknowns:**
  - Allowable Shear Stress ($\tau_{\text{allow}}$)
  - Pin Area ($A_{\text{pin}}$) and Diameter ($d_{\text{pin}}$)
  - Combined Pin Weight ($W_{\text{pins}}$)

#### Symbolic Solution for Pin Area (Single Shear)
$$\tau_{\text{allow}} = \frac{\tau_{\text{yield}}}{SF_{\text{pin}}}$$

$$A_{\text{pin}} = \frac{V_{\max}}{\tau_{\text{allow}}} = \frac{V_{\max} \cdot SF_{\text{pin}}}{\tau_{\text{yield}}}$$

#### Numerical Solution for Pin Area & Weight
$$\tau_{\text{allow}} = \frac{1172 \times 10^6\text{ Pa}}{4.0} = 293.0\text{ MPa}$$

$$A_{\text{pin}} = \frac{41.67 \times 10^3\text{ N}}{293.0 \times 10^6\text{ Pa}} = 1.42 \times 10^{-4}\text{ m}^2 = 142\text{ mm}^2$$

$$d_{\text{pin}} = \sqrt{\frac{4 \cdot A_{\text{pin}}}{\pi}} = \sqrt{\frac{4 \times 1.42 \times 10^{-4}}{\pi}} = 0.0134\text{ m} = 13.4\text{ mm}$$

$$\text{Volume}_{\text{pins}} = 5 \times (1.42 \times 10^{-4}\text{ m}^2) \times 0.02\text{ m} = 1.42 \times 10^{-5}\text{ m}^3$$

$$W_{\text{pins}} = (1.42 \times 10^{-5}\text{ m}^3 \times 7696\text{ kg/m}^3) \times 9.81\text{ m/s}^2 = 1.07\text{ N}$$

---

### 4. CAD Modeling & Weight Verification

#### Overview & Methodology
- **Why:** CAD modeling verifies the geometric feasibility of the assembly and provides accurate physical property measurements to check against analytical hand calculations.
- **How:** The 3D model was constructed using Autodesk Fusion using calculated cross-sections ($21.5\text{ mm} \times 21.5\text{ mm}$ square profile) and $13.4\text{ mm}$ tool steel pins, followed by automated mass property evaluation.
- **What:** Verified hand calculations against CAD models, observing less than $2\%$ variance across all component weights.

![CAD 3D Model Assembly Render](https://raw.githubusercontent.com/njablons/MEGR-2156-Portfolio/main/docs/assignments/A02/cad_model_render.png)

| Property | Hand Calculations | CAD Mass Properties | Percentage Difference |
| :--- | :--- | :--- | :--- |
| **Truss Mass** | $11.62\text{ kg}$ | $11.75\text{ kg}$ | $1.12\%$ |
| **Pins Mass** | $0.109\text{ kg}$ | $0.111\text{ kg}$ | $1.83\%$ |
| **Total Weight** | $115.07\text{ N}$ | $116.35\text{ N}$ | $1.11\%$ |

*Discrepancy Evaluation:* The slight mass increase in CAD stems from geometric material overlaps at joint connections and small shoulder features added to secure the pins.

---

## Decide

A 5-panel symmetrical planar configuration was selected because it distributes external loads direct to supports along balanced force vectors. Intermediate zero-force vertical members were strategically placed to reduce the unbraced column length of top compression members. This prevents premature local buckling failure without adding excessive dead weight to the structure.

---

## Communicate

### CAD Files & Downloads
- [Download Complete CAD Assembly (.STEP File)](https://github.com/njablons/MEGR-2156-Portfolio/tree/main/docs/assignments/A02)
- [Download Pin Connection CAD Model (.STEP File)](https://github.com/njablons/MEGR-2156-Portfolio/tree/main/docs/assignments/A02)

---

## Lessons Learned & Project Reflection

1. **Safety Factor Differentiation:** Applied distinct safety factors for normal axial stress ($SF = 3.5$) versus shear stress ($SF = 4.0$), gaining an understanding of how failure modes dictate allowable design stress limits.
2. **CAD vs. Hand Calculation Variances:** Documented how standard hand calculations simplify joint geometry as point nodes, whereas full 3D CAD modeling accounts for material overlaps and realistic hardware features.
3. **Mistakes & Iterations:** Initially, member cross-sections were calculated using total structural load rather than isolated joint maximums, leading to an oversized preliminary structure. Re-analyzing maximum internal forces via Method of Joints corrected the design.
4. **Time Tracking:** The total time to complete the analytical calculations, FBD sketches, CAD modeling, and documentation was **4.5 hours**.
