# A4 – Motor Mount

## Objective
Design a motor mount attached to a rigid wall for a 24V DC Gear Motor (3.6 kg·cm / 46 RPM w/ 99.5:1 Planetary Gearbox) subjected to a load **P = 300 N** at the free end. The design evaluates both yield strength (with a safety factor **N = 3**) and deflection constraints (**δ_max ≤ 0.30 mm**) using beam bending equations.

---

## Material Selection
* **Material**: PLA (Polylactic Acid)
* **Yield Strength (σ_y)**: 60 MPa
* **Elastic Modulus (E)**: 3.5 GPa (3500 MPa)
* **Factor of Safety (N)**: 3
* **Allowable Bending Stress (σ_allow)**: σ_allow = σ_y / N = 60 / 3 = **20 MPa**

---

## Feature 1 (Motor Attachment Plate)

### Knowns & Unknowns
* **Knowns**: P = 300 N, L_1 = 35 mm, σ_allow = 20 MPa, E = 3500 MPa, δ_max = 0.30 mm, beam width b_1 = 40 mm.
* **Unknowns**: Thickness h_1 based on stress, thickness h_1 based on deflection, final thickness h_1.

### Free Body Diagram (FBD)
*(Insert Image 1: FBD of Feature 1 treated as a cantilever beam with force P at the free end, length L_1, wall reaction moment M = P · L_1, and shear force V = P)*

### Equations & Symbolic Solution
* **Moment**: M_1 = P · L_1
* **Section Modulus**: Z_1 = (b_1 · h_1²) / 6
* **Bending Stress Constraint**: σ = M_1 / Z_1 ≤ σ_allow  ⇒  **h_1 ≥ √[(6 · P · L_1) / (b_1 · σ_allow)]**
* **Deflection Constraint**: δ = (P · L_1³) / (3 · E · I_1) ≤ δ_max  where  I_1 = (b_1 · h_1³) / 12  ⇒  **h_1 ≥ ∛[(4 · P · L_1³) / (E · b_1 · δ_max)]**

### Numerical Solution
* **Strength Design**:
  h_1 = √[(6 · 300 · 35) / (40 · 20)] = √(78.75) ≈ **8.87 mm**
* **Stiffness/Deflection Design**:
  h_1 = ∛[(4 · 300 · 35³) / (3500 · 40 · 0.30)] = ∛(51,450,000 / 42,000) = ∛(1225) ≈ **10.70 mm**
* **Governing Dimension (h_1)**: **10.70 mm** (Deflection governs)

---

## Feature 2 (Wall Mount Plate)

### Knowns & Unknowns
* **Knowns**: P = 300 N, effective length L_2 = 50 mm, σ_allow = 20 MPa, E = 3500 MPa, δ_max = 0.30 mm, beam width b_2 = 50 mm.
* **Unknowns**: Thickness h_2 based on stress, thickness h_2 based on deflection, final thickness h_2.

### Free Body Diagram (FBD)
*(Insert Image 2: FBD of Feature 2 showing wall mounting reaction forces at bolt locations and applied load P)*

### Equations & Symbolic Solution
* **Moment**: M_2 = P · L_2
* **Bending Stress Constraint**: **h_2 ≥ √[(6 · P · L_2) / (b_2 · σ_allow)]**
* **Deflection Constraint**: **h_2 ≥ ∛[(4 · P · L_2³) / (E · b_2 · δ_max)]**

### Numerical Solution
* **Strength Design**:
  h_2 = √[(6 · 300 · 50) / (50 · 20)] = √(90) ≈ **9.49 mm**
* **Stiffness/Deflection Design**:
  h_2 = ∛[(4 · 300 · 50³) / (3500 · 50 · 0.30)] = ∛(150,000,000 / 52,500) = ∛(2857.14) ≈ **14.19 mm**
* **Governing Dimension (h_2)**: **14.19 mm** (Deflection governs)

---

## Sketch (Isometric View)
*(Insert Image 3: Hand-drawn isometric sketch of the L-bracket motor mount with calculated thickness dimensions, motor mounting face, wall mounting face, and side gussets)*

---

## CAD Model (Parametric)
* Parametric dimensions were established in CAD linking calculated variables **h_1 = 10.7 mm** and **h_2 = 14.2 mm**.
* Added side triangular gussets/ribs to reduce deflection and reinforce the 90° bend.
* Features include **3.4 mm** clearance holes for standard M3 wall/motor mounting bolts and a center clearance hole for the planetary gearbox shaft.

*(Insert Image 4: 3D CAD render or screenshot of the parametric motor mount model)*

---

## CAD File Downloads
* [Download Motor Mount 3D Model File (STEP / SLDPRT)](https://github.com/njablons/MEGR-2156-Portfolio)
* [Download Motor Mount Drawing (PDF)](https://github.com/njablons/MEGR-2156-Portfolio)

---

## Appendix (Motor Mount Inspiration & Links)
* [StepperOnline Motor Specifications](https://www.omc-stepperonline.com/brushed-24v-dc-gear-motor-3-6kg-cm-46rpm-w-99-5-1-planetary-gearbox-pa28-28245800-g100)
* [Standard NEMA L-Bracket Motor Mount Design](https://www.dhgate.com/product/steel-42-stepper-motor-mount-bracket-nema17/996764543.html)

---

## Documentation & Lessons Learned
* **Total Time Spent**: Approximately 4.5 hours from calculations to CAD modeling and drawing creation.
* **Lessons Learned**: Calculating deflection for both features revealed that stiffness—rather than stress—governs the required wall thickness for 3D printed materials like PLATo fix the illegible formatting on your site, you need to add a space between the MathJax dollar signs (`$`) and surrounding punctuation, or wrap your inline math in standard Markdown code blocks or LaTeX syntax. 
