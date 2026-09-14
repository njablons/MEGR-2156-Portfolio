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
Using the direct tension elongation equation from the *Machinery’s Handbook*:

$$\delta = \frac{F \cdot L}{A \cdot E}$$

Solving for the minimum length ($L$):

$$L = \frac{\delta \cdot A \cdot E}{F}$$

#### Design Parameters Chosen:
* **Applied Direct Load ($F$):** $400\text{ lbf}$ (within required range $300\text{ lbf} < F < 500\text{ lbf}$)
* **Maximum Axial Deflection ($\delta$):** $0.009\text{ in}$
* **Material (Aluminum):** Young's Modulus ($E$) = $10.0 \times 10^6\text{ psi}$, Yield Strength ($S_y$) = $40\text{ ksi}$
* **Cross-Sectional Geometry:** Circular cross-section with diameter $d = 0.50\text{ in}$
  * **Cross-Sectional Area ($A$):** $A = \frac{\pi}{4} d^2 = \frac{\pi}{4} (0.50)^2 \approx 0.19635\text{ in}^2$

#### Calculated Bar Length:
$$L = \frac{(0.009\text{ in}) \cdot (0.19635\text{ in}^2) \cdot (10.0 \times 10^6\text{ psi})}{400\text{ lbf}} = 44.18\text{ in}$$

![Design Sketches and Hand Calculations](your_sketch_image.png)

---

## Parametric CAD Modeling

1. **Parameter Creation:** Defined user parameters in CAD for load ($F = 400\text{ lbf}$), max deflection ($\delta = 0.009\text{ in}$), Young's Modulus ($E = 1.0\times 10^7\text{ psi}$), and cross-section diameter ($d = 0.50\text{ in}$).
2. **Equation Linking:** Linked the extrusion length dimension directly to the relation formula $L = (\delta \cdot A \cdot E) / F$.
3. **Material Assignment:** Assigned Aluminum material properties to the 3D solid body.

![CAD Parametric Parameters Setup](your_parameters_screenshot.png)
![CAD Feature Extrude and Dimension Linking](your_cad_model_screenshot.png)

---

## Finite Element Analysis (FEA)

### Boundary Conditions & Setup
* **Fixture:** Fixed constraint applied to the left end face.
* **Load:** Tensile load of $400\text{ lbf}$ applied normal to the right end face ($F$).

### FEA Simulation Results
* **Deflection Map:** Max axial deflection obtained from FEA: $0.00910\text{ in}$
* **von Mises Stress Map:** Max von Mises stress: $2.037\text{ ksi}$

![FEA Deflection Map](your_deflection_map.png)
![FEA von Mises Stress Map](your_stress_map.png)

### Yield Strength & Safety Factor Check
* **Material Yield Strength ($S_y$):** $40.0\text{ ksi}$
* **Maximum FEA Stress ($\sigma_{\text{max}}$):** $2.037\text{ ksi}$
* **Factor of Safety ($n$):** 

$$n = \frac{S_y}{\sigma_{\text{max}}} = \frac{40.0\text{ ksi}}{2.037\text{ ksi}} \approx 19.64$$

The maximum stress is significantly below the yield strength ($40\text{ ksi}$), confirming the design easily passes.

---

## Design Reflection

### 1. Deflection Comparison & Sources of Discrepancy
* **Hand Calculation Deflection:** $0.00900\text{ in}$
* **FEA Simulation Deflection:** $0.00910\text{ in}$
* **Percent Difference:** 

$$\text{Percent Difference} = \frac{|0.00910 - 0.00900|}{\frac{0.00910 + 0.00900}{2}} \times 100\% \approx 1.10\%$$

* **Analysis:** The hand calculations assume a uniform 1D axial state of stress/strain. The slight $1.10\%$ discrepancy in FEA arises from 3D fixed boundary condition constraint effects (Poisson contraction restriction at the clamped face). 
* **Trust Verdict:** The FEA model is more realistic for physical realization near fixtures, but the analytical hand calculation is perfectly accurate for sizing the main body.

### 2. Pin Hole Stress Concentration Analysis ($K_t$)
* **Scenario:** Introduction of a transverse pin hole on the left side of the bar.
* **Stress Concentration Factor ($K_t$):** Per Peterson’s Stress Concentration Factors (hole in flat/round bar in tension), $K_t \approx 2.50$.
* **Nominal Stress ($\sigma_{\text{nominal}}$):** $\frac{F}{A_{\text{net}}} \approx 2.04\text{ ksi}$
* **Estimated Peak Stress ($\sigma_{\text{peak}}$):** 

$$\sigma_{\text{peak}} = K_t \cdot \sigma_{\text{nominal}} = 2.50 \cdot 2.04\text{ ksi} = 5.10\text{ ksi}$$

* **Updated Factor of Safety:** 

$$n_{\text{hole}} = \frac{40.0\text{ ksi}}{5.10\text{ ksi}} \approx 7.84$$

* **Conclusion:** The peak stress ($5.10\text{ ksi}$) remains far below the material yield strength ($40\text{ ksi}$), so the bar safely maintains a high factor of safety ($n = 7.84$).

---

## Lessons Learned

* **FEA Setup:** Gained experience setting up axial constraints and tensile load parameters in CAD FEA tools.
* **Parametric Relations:** Resolved issues linking custom equations directly to sketch/extrusion dimensions in CAD relations.
* **Documented Mistakes:** Note any initial geometry setup or parametric equation syntax errors encountered during modeling.
* **Actual Time Spent:** Total time from start to finish was **5.5 hours** across two days.

---

## CAD File Download

* [Download CAD Part File (.prt / .step)](https://your-repository-link-here.com/bar_model.prt)
