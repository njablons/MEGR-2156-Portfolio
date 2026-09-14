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
* **Applied Direct Load ($F$):** $400\text{ lbf}$ (within required range $300\textTo ensure maximum scoring across all rubrics for [A3: Parametric and FEA](https://instructure.charlotte.edu/courses/272052/assignments/2902670) while adhering strictly to submission requirements, here is the original structural Markdown template tailored for your portfolio file at `docs/assignments/A03/index.md`.

This version uses distinct structural formatting and original phrasing to fulfill every rubric item while preventing header and link point deductions.

```markdown
# A3: Parametric Design and Finite Element Analysis

## Objective
* Develop a parametric CAD model of a structural bar subjected to direct tensile loading.
* Use axial deformation mechanics to establish geometric dimensions matching target deflection limits.
* Perform Finite Element Analysis (FEA) to map von Mises stress levels and displacement across the component.
* Compare theoretical hand-calculated values against computational simulation data.
* Evaluate structural integrity, safety margins, and localized stress concentrations.

---

## Analytical Design & Parametric Sizing

### Analytical Formulation
The axial deformation ($\delta$) of a prismatic member in tension is given by:

$$\delta = \frac{F \cdot L}{A \cdot E}$$

Rearranging the terms to isolate the minimum required length ($L$):

$$L = \frac{\delta \cdot A \cdot E}{F}$$

#### Selected Design Criteria:
* **Applied Axial Load ($F$):** $400\text{ lbf}$ (satisfies $300\text{ lbf} < F < 500\text{ lbf}$)
* **Target Axial Deflection ($\delta$):** $0.009\text{ in}$
* **Material Selection (Aluminum):** Elastic Modulus ($E$) = $10.0 \times 10^6\text{ psi}$, Yield Strength ($S_y$) = $40\text{ ksi}$
* **Cross-Section Profile:** Solid circular rod with diameter $d = 0.50\text{ in}$
  * **Cross-Sectional Area ($A$):** $A = \frac{\pi}{4} (0.50\text{ in})^2 \approx 0.19635\text{ in}^2$

#### Calculated Nominal Length:
$$L = \frac{(0.009\text{ in}) \cdot (0.19635\text{ in}^2) \cdot (10.0 \times 10^6\text{ psi})}{400\text{ lbf}} = 44.18\text{ in}$$

![Hand Calculations and Hand-Drawn Diagrams](your_sketch_image.png)

---

## Parametric CAD Implementation

1. **Parameter Definition:** Established key input variables ($F$, $\delta$, $E$, $d$) inside the CAD environment.
2. **Equation Feature
