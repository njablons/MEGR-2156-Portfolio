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

<div style="display: flex; flex-direction: column; gap: 20px; align-items: center; width: 100%;">
  <img src="https://v3.camscanner.com/user/download?page=1" alt="Page 1 - Calculations" style="width: 100%; max-width: 800px; border: 1px solid #ccc; box-shadow: 0 4px 8px rgba(0,0,0,0.1);">
  <img src="https://v3.camscanner.com/user/download?page=2" alt="Page 2 - Calculations" style="width: 100%; max-width: 800px; border: 1px solid #ccc; box-shadow: 0 4px 8px rgba(0,0,0,0.1);">
  <img src="https://v3.camscanner.com/user/download?page=3" alt="Page 3 - Calculations" style="width: 100%; max-width: 800px; border: 1px solid #ccc; box-shadow: 0 4px 8px rgba(0,0,0,0.1);">
  <img src="https://v3.camscanner.com/user/download?page=4" alt="Page 4 - Calculations" style="width: 100%; max-width: 800px; border: 1px solid #ccc; box-shadow: 0 4px 8px rgba(0,0,0,0.1);">
  <img src="https://v3.camscanner.com/user/download?page=5" alt="Page 5 - Calculations" style="width: 100%; max-width: 800px; border: 1px solid #ccc; box-shadow: 0 4px 8px rgba(0,0,0,0.1);">
  <img src="https://v3.camscanner.com/user/download?page=6" alt="Page 6 - Stress Multiview Sketch" style="width: 100%; max-width: 800px; border: 1px solid #ccc; box-shadow: 0 4px 8px rgba(0,0,0,0.1);">
  <img src="https://v3.camscanner.com/user/download?page=7" alt="Page 7 - Stiffness Multiview Sketch" style="width: 100%; max-width: 800px; border: 1px solid #ccc; box-shadow: 0 4px 8px rgba(0,0,0,0.1);">
</div>

---

## Lessons Learned
1. **Governing Failure Mode:** Comparing stress and stiffness requirements showed that Feature B was governed by stiffness (1.090 in) rather than stress (1.039 in), requiring an additional 0.051 in of material to remain within the allowable deflection limit.
2. **Error Propagation:** Reaction loads determined at the strap support (Feature A) transferred directly downstream into Feature B as an end point load, generating a 900 lb·in moment that governed the required thickness of the base attachment (Feature E).
3. **Assumption Sensitivity:** Neglecting direct shear simplified the beam models; however, incorporating transverse shear stress near the wall attachment would increase local thickness requirements.
4. **Time Requirements:** Completing the full hand calculations, free body diagrams, stiffness/stress evaluations, and multiview sketches for this assignment took approximately 4 to 5 hours in total.
