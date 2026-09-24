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

<object data="CamScanner 9-23-26 19.56.pdf" type="application/pdf" width="100%" height="900px">
    <p>Your browser does not support inline PDF viewing. You can <a href="CamScanner 9-23-26 19.56.pdf">download the PDF document here</a> to view your calculations and sketches.</p>
</object>

---

## Lessons Learned
1. **Governing Failure Mode:** Comparing stress and stiffness requirements showed that Feature B was governed by stiffness (1.090 in) rather than stress (1.039 in), requiring an additional 0.051 in of material to remain within the allowable deflection limit.
2. **Error Propagation:** Reaction loads determined at the strap support (Feature A) transferred directly downstream into Feature B as an end point load, generating a 900 lb·in moment that governed the required thickness of the base attachment (Feature E).
3. **Assumption Sensitivity:** Neglecting direct shear simplified the beam models; however, incorporating transverse shear stress near the wall attachment would increase local thickness requirements.
4. **Time Requirements:** Completing the full hand calculations, free body diagrams, stiffness/stress evaluations, and multiview sketches for this assignment took approximately 4 to 5 hours in total.
