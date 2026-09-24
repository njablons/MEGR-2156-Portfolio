# Assignment 5: Bracket Design

## Objective
To design, analyze, and optimize a structural bracket supporting an applied load using Aluminum 6061-T6, ensuring a minimum Factor of Safety of 4.0 and limiting deflections across all critical features to under 0.005 inches.

---

## Description
* **Material:** Aluminum 6061-T6
  * Yield Strength ($\sigma_y$): $40,000\text{ psi}$
  * Modulus of Elasticity ($E$): $10 \times 10^6\text{ psi}$
* **Applied Load ($F$):** $600\text{ lbf}$
* **Factor of Safety ($N$):** $4.0$
* **Allowable Stress ($\sigma_{\text{allow}}$):** 
  $$\sigma_{\text{allow}} = \frac{\sigma_y}{N} = \frac{40,000\text{ psi}}{4} = 10,000\text{ psi}$$
* **Allowable Deflection ($\delta_{\text{max}}$):** $0.005\text{ in}$
* **Symmetry:** Each symmetrical half carries half of the total applied force ($P = 300\text{ lbf}$).

---

## Bracket Design

### Hand Calculations & Multiview Sketches
<iframe src="CamScanner 9-23-26 19.56.pdf" width="100%" height="800px"></iframe>

---

## Lessons Learned
1. **Governing Failure Mode:** Comparing stress and stiffness requirements showed that Feature B was governed by stiffness ($1.090\text{ in}$) rather than stress ($1.039\text{ in}$), requiring an additional $0.051\text{ in}$ of material to remain within the allowable deflection limit.
2. **Error Propagation:** Reaction loads determined at the strap support (Feature A) transferred directly downstream into Feature B as an end point load, generating a $900\text{ lb}\cdot\text{in}$ moment that governed the required thickness of the base attachment (Feature E).
3. **Assumption Sensitivity:** Neglecting direct shear simplified the beam models; however, incorporating transverse shear stress near the wall attachment would increase local thickness requirements.
4. **Time Requirements:** Completing the full hand calculations, free body diagrams, stiffness/stress evaluations, and multiview sketches for this assignment took approximately 4 to 5 hours in total.
