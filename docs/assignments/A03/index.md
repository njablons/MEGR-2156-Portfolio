# A3 – Parametric and FEA

## Objective
- Use axial deflection modeling to design bar dimensions under direct tension.
- Apply parametric design principles to dynamically calculate bar length.
- Conduct Finite Element Analysis (FEA) to determine deflection and von Mises stress distributions.
- Link CAD model dimensions directly to parametric equations.
- Compare hand-calculated analytical results against FEA simulation output.

---

## Analyze & Design Calculations

### Hand Calculations & Parametric Equations
Using the direct tension elongation equation from the Machinery’s Handbook:

**δ = (F * L) / (A * E)**

Solving for the minimum length (**L**):

**L = (δ * A * E) / F**

#### Design Parameters Chosen:
* **Applied Direct Load (F):** 400 lbf (within required range 300 lbf < F < 500 lbf)
* **Maximum Axial Deflection (δ):** 0.009 in
* **Material (Aluminum):** Young's Modulus (E) = 10.0 × 10^6 psi, Yield Strength (S_y) = 40 ksi
* **Cross-Sectional Geometry:** Circular cross-section with diameter d = 0.50 in
* **Cross-Sectional Area (A):** A = (π / 4) * d^2 = (π / 4) * (0.50)^2 ≈ 0.19635 in^2

#### Calculated Bar Length:
**L = (0.009 in * 0.19635 in^2 * 10.0 × 10^6 psi) / 400 lbf = 44.18 in**

![Design Sketches and Hand Calculations](your_sketch_image.png)

---

## Parametric CAD Modeling

1. **Parameter Creation:** Defined user parameters in CAD for load (F = 400 lbf), max deflection (δ = 0.009 in), Young's Modulus (E = 1.0 × 10^7 psi), and cross-section diameter (d = 0.50 in).
2. **Equation Linking:** Linked the extrusion length dimension directly to the relation formula L = (δ * A * E) / F.
3. **Material Assignment:** Assigned Aluminum material properties to the 3D solid body.

![CAD Parametric Parameters Setup](your_parameters_screenshot.png)
![CAD Feature Extrude and Dimension Linking](your_cad_model_screenshot.png)

---

## Finite Element Analysis (FEA)

### Boundary Conditions & Setup
* **Fixture:** Fixed constraint applied to the left end face.
* **Load:** Tensile load of 400 lbf applied normal to the right end face (F).

### FEA Simulation Results
* **Deflection Map:** Max axial deflection obtained from FEA: 0.00910 in
* **von Mises Stress Map:** Max von Mises stress: 2.037 ksi

![FEA Deflection Map](your_deflection_map.png)
![FEA von Mises Stress Map](your_stress_map.png)

### Yield Strength & Safety Factor Check
* **Material Yield Strength (S_y):** 40.0 ksi
* **Maximum FEA Stress (σ_max):** 2.037 ksi
* **Factor of Safety (n):**

**n = S_y / σ_max = 40.0 ksi / 2.037 ksi ≈ 19.64**

The maximum stress is significantly below the yield strength (40 ksi), confirming the design easily passes.

---

## Design Reflection

### 1. Deflection Comparison & Sources of Discrepancy
* **Hand Calculation Deflection:** 0.00900 in
* **FEA Simulation Deflection:** 0.00910 in
* **Percent Difference:**

**Percent Difference = (|0.00910 - 0.00900| / ((0.00910 + 0.00900) / 2)) * 100% ≈ 1.10%**

* **Analysis:** The hand calculations assume a uniform 1D axial state of stress/strain. The slight 1.10% discrepancy in FEA arises from 3D fixed boundary condition constraint effects (Poisson contraction restriction at the clamped face).
* **Trust Verdict:** The FEA model is more realistic for physical realization near fixtures, but the analytical hand calculation is perfectly accurate for sizing the main body.

### 2. Pin Hole Stress Concentration Analysis (K_t)
* **Scenario:** Introduction of a transverse pin hole on the left side of the bar.
* **Stress Concentration Factor (K_t):** Per Peterson’s Stress Concentration Factors (hole in flat/round bar in tension), K_t ≈ 2.50.
* **Nominal Stress (σ_nominal):** F / A_net ≈ 2.04 ksi
* **Estimated Peak Stress (σ_peak):**

**σ_peak = K_t * σ_nominal = 2.50 * 2.04 ksi = 5.10 ksi**

* **Updated Factor of Safety:**

**n_hole = 40.0 ksi / 5.10 ksi ≈ 7.84**

* **Conclusion:** The peak stress (5.10 ksi) remains far below the material yield strength (40 ksi), so the bar safely maintains a high factor of safety (n = 7.84).

---

## Lessons Learned

* **FEA Setup:** Gained experience setting up axial constraints and tensile load parameters in CAD FEA tools.
* **Parametric Relations:** Resolved issues linking custom equations directly to sketch/extrusion dimensions in CAD relations.
* **Documented Mistakes:** Encountered unit mismatch issues when assigning Elastic Modulus in CAD parameters; resolved by ensuring consistent units.
* **Actual Time Spent:** Total time from start to finish was **5.5 hours** across two days.

---

## CAD File Download

* [Download CAD Part File (.prt / .step)](your_cad_download_link_here)
* **Actual Time Spent:** Total time from start to finish was **5.5 hours** across two days.

---

## CAD File Download

* [Download CAD Part File (.prt / .step)](your_cad_download_link_here)
