# Assignment 5: Bracket Design

## Objective
To design, analyze, and optimize a structural bracket supporting an applied load using Aluminum 6061-T6, ensuring a minimum Factor of Safety of 4.0 and limiting deflections across all critical features to under 0.005 inches.

---

## Description
* **Material:** Aluminum 6061-T6
  * **Yield Strength:** 40,000 psi
  * **Modulus of Elasticity:** 10,000,000 psi
* **Applied Load (F):** 600 lbf
* **Factor of Safety (N):** 4.0
* **Allowable Stress:** 40,000 / 4 = 10,000 psi
* **Allowable Deflection:** 0.005 inches
* **Symmetry:** Each symmetrical half carries half of the total applied force (P = 300 lbf).

---

## Bracket Design

### Hand Calculations & Multiview Sketches

### Structural Analysis Justification
The complete hand calculations for Features A through E evaluate structural integrity under two distinct mechanics criteria: stress analysis and stiffness analysis. Stress analysis focuses strictly on material yielding, calculating the minimum cross-sectional dimensions required to keep internal bending and axial stresses below the allowable yield strength ($\sigma_{\text{allow}} = 10,000\text{ psi}$). Each feature is modeled using fundamental beam and axial equations, assuming standard boundary conditions such as simple supports for span members and fixed conditions for cantilever sections. Direct transverse shear stresses are assumed negligible relative to primary bending and tensile stresses to streamline section sizing.

Stiffness analysis evaluates elastic deformation to ensure the bracket maintains positional stability under the full $600\text{ lbf}$ load. By enforcing a strict displacement constraint ($\delta_{\text{max}} = 0.005\text{ in}$), the required cross-sectional properties are solved using beam deflection formulas and axial elongation models. Evaluating both criteria independently ensures the component is sized to prevent permanent plastic deformation while remaining rigid enough for precise mechanical operation.

<object data="CamScanner 9-23-26 19.56.pdf" type="application/pdf" width="100%" height="900px">
    <p>Your browser does not support inline PDF viewing. You can <a href="CamScanner 9-23-26 19.56.pdf">download the PDF document here</a> to view your calculations and sketches.</p>
</object>

### Key Differences Between Stress and Stiffness Results
Comparing the analytical outcomes between Pages 1–5 reveals how geometric constraints shift depending on member length and loading mode. Short, direct-load features—such as the axial tensile link (Feature C) and strap support (Feature A)—are dominated by yield stress limits. For these features, the cross-sectional area needed to prevent yielding easily satisfies the deflection requirement, meaning stress acts as the governing sizing constraint.

Conversely, long cantilevered spans subject to large bending moments—such as the main arm (Feature B)—are heavily governed by stiffness rather than strength. While a smaller cross-sectional height satisfies yield stress limits, elastic bending over the length of the cantilever results in deflections exceeding $0.005\text{ in}$. Consequently, Feature B requires an increased height ($1.090\text{ in}$ vs $1.039\text{ in}$) strictly to fulfill the rigidity constraint. The hand-drawn multiview sketches on Pages 6 and 7 visually map out these differences, showing how the stiffness-governed layout expands critical cross-sections relative to the baseline stress layout.

---

## Lessons Learned
1. **Governing Failure Mode:** Comparing stress and stiffness requirements showed that Feature B was governed by stiffness (1.090 in) rather than stress (1.039 in), requiring an additional 0.051 in of material to remain within the allowable deflection limit.
2. **Error Propagation:** Reaction loads determined at the strap support (Feature A) transferred directly downstream into Feature B as an end point load, generating a 900 lb·in moment that governed the required thickness of the base attachment (Feature E).
3. **Assumption Sensitivity:** Neglecting direct shear simplified the beam models; however, incorporating transverse shear stress near the wall attachment would increase local thickness requirements.
4. **Time Requirements:** Completing the full hand calculations, free body diagrams, stiffness/stress evaluations, and multiview sketches for this assignment took approximately 4 to 5 hours in total.
