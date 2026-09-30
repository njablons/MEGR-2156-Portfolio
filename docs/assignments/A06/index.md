# A6 – Bracket Design for Strength and Stiffness II

## Objective
The objective of this assignment is to generate a comprehensive 3D solid model and a fully dimensioned multi-view engineering drawing in CAD representing the structural bracket designed in assignment A05. The design incorporates all features to ensure both strength and stiffness requirements are met under an applied load of 600 lbf using Aluminum 6061-T6 with a safety factor of 4.0.

---

## Design

### Step 1: Strength vs Stiffness
Before creating any CAD models or drawings, I evaluated which analysis design from Assignment A05 would govern the final part geometry. I selected the stiffness-governed design because it provided more conservative section depths, ensuring that maximum beam deflection remains strictly below the $0.005\text{ in}$ limit under the full load. Once confirmed, I configured the Creo software material to Aluminum 6061-T6 and set the working unit system to `in-lbf`.

![3D Model Isometric View](step1_model.png)

### Step 2: Parametric Modeling
Using Creo Parametric, I constructed a single, continuous 3D solid part by sketching sequentially from Feature A through Feature E. To ensure model flexibility, I entered all critical dimensions into the Creo Parameters table and linked them to driving relations. 

For example, the primary cantilever depth for Feature B was driven by the relation `d5 = (6 * P * L_B) / (w_B * SIGMA_ALLOW)`, which automatically updates the feature geometry if load parameters change. Modeling the full part parametrically highlighted geometric clearances near the wall attachment, allowing me to refine feature transition radii without altering the underlying stress/stiffness constraints.

![Parametric Table](parametric_table.png)
![Feature A Modeling](feature_a_cad.png)
![Feature B Modeling](feature_b_cad.png)
![Feature C Modeling](feature_c_cad.png)
![Feature D Modeling](feature_d_cad.png)
![Feature E Modeling](feature_e_cad.png)

### Step 3: Tolerances and Drawing
To prepare the model for manufacturing, I assigned functional tolerances to all interface surfaces. The bracket features sliding fit interfaces over the mating rigid beam, so I applied a functional loose fit tolerance of $-0.001\text{ in}$ to the Feature D slot height to allow smooth installation while maintaining a tight mechanical fit.

Using the B-size (11x17) UNCC engineering drawing template, I created a third-angle projection layout containing top, front, and right-side orthographic views alongside a 3D isometric reference view. I enabled tolerance display in Creo configuration settings and incorporated the required standard title block tolerance block:
* $X.X \pm 0.02\text{ in}$
* $X.XX \pm 0.01\text{ in}$
* $X.XXX \pm 0.005\text{ in}$

![A06 Engineering Drawing](A06_Drawing.png)

---

## Reflection
* **Time Spent:** Completing the CAD modeling, parametric relation setup, GD&T tolerancing, multi-view drawing layout, and portfolio documentation took approximately 4.5 hours in total.
* **Parametric Equation Driving Geometry:** The section depth for Feature B was directly controlled by the analytical bending equation $h_B = \sqrt{(6 P L_B) / (w_B \sigma_{\text{allow}})}$ entered as a relation in Creo. When driving parameters were updated, the model rebuilt automatically without requiring manual sketch edits.
* **Tolerance Selection & Cost Justification:** A tight tolerance class ($X.XXX \pm 0.005\text{ in}$) was applied strictly to the mating sliding fit slot on Feature D to ensure proper alignment with the mounting rail. Non-critical exterior edges were assigned looser tolerances ($X.X \pm 0.02\text{ in}$). Applying tight tolerances across non-critical features unnecessarily increases manufacturing costs by forcing machinists to take slower, multi-pass cuts and increasing part scrap rates.

---

## CAD Files
[Download Bracket CAD Files (.zip)](bracket_cad_files.zip)
