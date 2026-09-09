# A2 – Design with Basic Stresses

## Objective
The objective of this assignment is to design a lightweight planar truss using A500 structural steel and determine its performance under specified point loads. Structural members are sized using allowable normal stress under a safety factor of 3.5, while hardened tool steel connecting pins are evaluated under single-shear loading with a safety factor of 4.0. The design workflow includes joint equilibrium analysis, symbolic and numerical stress calculations, 3D CAD modeling, and verification against analytical calculations.

---

## Analyze

### 1. Overall Truss Geometry & Internal Forces

#### Overview & Methodology
- **Why:** Identifying peak tension and compression loads across structural members is necessary to select cross-sectional dimensions that prevent structural yielding.
- **How:** Global static equilibrium equations were applied to solve support reactions, followed by node-by-node evaluation using the Method of Joints.
- **What:** Designed a symmetrical 5-panel planar truss using parameters $P = 25\text{ kN}$, $a = 0.4\text{ m}$, and $b = 0.3\text{ m}$.

#### Setup Parameters
- **Applied Load:** $P = 25\text{ kN}$
- **Base Dimensions:** $a = 0.4\text{ m}$, $b = 0.3\text{ m}$
- **Truss Steel (A500):** Yield Strength = $315\text{ MPa}$, Density = $7850\text{ kg/m}^3$
- **Pin Steel (Hardened Tool Steel):** Yield Shear Strength = $1172\text{ MPa}$, Density = $7696\text{ kg/m}^3$

#### Free Body Diagrams (FBDs)
![Global and Joint Free Body Diagrams](./fbd_diagram.png)

#### Symbolic Solution for Internal Forces
1. **Support Reactions:**
   - Summing moments about Pin A gives $R_B = 1.25 \cdot P$
   - Vertical equilibrium gives $R_{Ay} = 0.75 \cdot P$
   - Horizontal equilibrium gives $R_{Ax} = 0$

2. **Internal Member Forces:**
   - Bottom Chord Tension: $F_{\text{bottom}} = \frac{P \cdot a}{b}$
   - Top Chord Compression: $F_{\text{top}} = -\frac{P \cdot a}{b}$
   - Diagonal Tension: $F_{\text{diag}} = \frac{P \cdot \sqrt{a^2 + b^2}}{b}$

#### Numerical Solution for Internal Forces
Using $P = 25\text{ kN}$, $a = 0.4\text{ m}$, $b = 0.3\text{ m}$:
- $R_{Ay} = 18.75\text{ kN}$
- $R_B = 31.25\text{ kN}$
- $F_{\text{bottom}} = 33.33\text{ kN}$
- $F_{\text{top}} = -33.33\text{ kN}$
- $F_{\text{diag}} = 41.67\text{ kN}$ (Maximum internal force)

---

### 2. Member Cross-Sectional Area & Weight Calculation

#### Overview & Methodology
- **Why:** Determining required material cross-sections ensures structural integrity under maximum load limits.
- **How:** Allowable stress was defined as yield strength divided by safety factor (3.5), allowing calculation of minimum member area and mass.
- **What:** Computed minimum area ($463\text{ mm}^2$) and estimated truss weight ($114.0\text{ N}$).

#### Knowns & Unknowns
- **Knowns:** $F_{\max} = 41.67\text{ kN}$, Yield Strength = $315\text{ MPa}$, Safety Factor = $3.5$, Density = $7850\text{ kg/m}^3$, Total Length = $3.2\text{ m}$.
- **Unknowns:** Allowable Stress ($\sigma_{\text{allow}}$), Member Area ($A_{\text{member}}$), Total Weight ($W_{\text{truss}}$).

#### Equations & Numerical Results
- Allowable Stress: $\sigma_{\text{allow}} = \frac{315\text{ MPa}}{3.5} = 90.0\text{ MPa}$
- Cross-Sectional Area: $A_{\text{member}} = \frac{41.67\text{ kN}}{90.0\text{ MPa}} = 463\text{ mm}^2$
- Approximate Weight: Volume = $0.00148\text{ m}^3$, Mass = $11.62\text{ kg}$, Weight = $114.0\text{ N}$

---

### 3. Connecting Pin Cross-Sectional Area & Weight Calculation

#### Overview & Methodology
- **Why:** Connecting pins must withstand single-shear stresses at loaded joint connections without shear yielding.
- **How:** Sized pins using tool steel shear yield strength divided by a safety factor of 4.0.
- **What:** Computed required pin area ($142\text{ mm}^2$), pin diameter ($13.4\text{ mm}$), and combined pin weight ($1.07\text{ N}$).

#### Equations & Numerical Results
- Allowable Shear Stress: $\tau_{\text{allow}} = \frac{1172\text{ MPa}}{4.0} = 293.0\text{ MPa}$
- Pin Area: $A_{\text{pin}} = \frac{41.67\text{ kN}}{293.0\text{ MPa}} = 142\text{ mm}^2$
- Pin Diameter: $d_{\text{pin}} = \sqrt{\frac{4 \cdot A_{\text{pin}}}{\pi}} = 13.4\text{ mm}$
- Total Pin Mass & Weight: 5 pins total = $0.109\text{ kg}$ ($1.07\text{ N}$)

---

### 4. CAD Modeling & Weight Verification

#### Overview & Methodology
- **Why:** CAD evaluation verifies 3D assembly feasibility and checks mass properties against hand calculations.
- **How:** Built a 3D frame model in CAD using $21.5\text{ mm} \times 21.5\text{ mm}$ profiles and $13.4\text{ mm}$ cylindrical pins.
- **What:** Discrepancy between CAD and hand calculations was under 2%.

![CAD Assembly Render](./cad_render.png)

| Property | Hand Calculations | CAD Properties | Percentage Variance |
| :--- | :--- | :--- | :--- |
| **Truss Mass** | $11.62\text{ kg}$ | $11.75\text{ kg}$ | $1.12\%$ |
| **Pin Mass** | $0.109\text{ kg}$ | $0.111\text{ kg}$ | $1.83\%$ |
| **Total Weight** | $115.07\text{ N}$ | $116.35\text{ N}$ | $1.11\%$ |

---

## Decide

A symmetrical 5-panel layout was selected to maintain a direct load path toward supports. Internal vertical elements act as unbraced length reducers for top compression chords, suppressing localized buckling while keeping dead weight minimal.

---

## Communicate

### CAD Files & Downloads
- Download CAD Assembly (.STEP File) — *Include download link to file in repository*
- Download Pin CAD File (.STEP File) — *Include download link to file in repository*

---

## Lessons Learned & Reflection

1. **Safety Factor Application:** Applied separate safety factors for direct axial normal stress ($SF = 3.5$) and pin single shear ($SF = 4.0$) based on component loading conditions.
2. **Hand Calculations vs. CAD Analysis:** Hand calculations simplify joints to ideal point nodes, whereas 3D CAD modeling incorporates geometric overlap at physical joint connections, resulting in a $1.1\%$ mass difference.
3. **Iterations & Mistakes:** Initially evaluated cross-sections based on total external load rather than peak internal member load. Recalculating member forces via joint equilibrium corrected member sizing.
4. **Time Spent:** Total project time (calculations, FBDs, CAD modeling, and portfolio entry) was **4.5 hours**.
