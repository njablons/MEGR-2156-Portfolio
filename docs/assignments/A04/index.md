# A4 – Motor Mount

## Objective
Design a motor mount attached to a rigid wall for a 24V DC Gear Motor (3.6 kg·cm / 46 RPM w/ 99.5:1 Planetary Gearbox) subjected to a load $P = 300\text{ N}$ at the free end. The design evaluates both yield strength (with a safety factor $N = 3$) and deflection constraints ($\delta_{\max} \le 0.30\text{ mm}$) using beam bending equations.

---

## Material Selection
* **Material**: PLA (Polylactic Acid)
* **Yield Strength ($\sigma_y$)**: $60\text{ MPa}$
* **Elastic Modulus ($E$)**: $3.5\text{ GPa}$ ($3500\text{ MPa}$)
* **Factor of Safety ($N$)**: $3$
* **Allowable Bending Stress ($\sigma_{\text{allow}}$)**: $\sigma_{\text{allow}} = \frac{\sigma_y}{N} = \frac{60}{3} = 20\text{ MPa}$

---

## Feature 1 (Motor Attachment Plate)

### Knowns & Unknowns
* **Knowns**: $P = 300\text{ N}$, $L_1 = 35\text{ mm}$, $\sigma_{\text{allow}} = 20\text{ MPa}$, $E = 3500\text{ MPa}$, $\delta_{\max} = 0.30\text{ mm}$, beam width $b_1 = 40\text{ mm}$.
* **Unknowns**: Thickness $h_1$ based on stress, thickness $h_1$ based on deflection, final thickness $h_1$.

### Free Body Diagram (FBD)
*(Insert Image 1: FBD of Feature 1 treated as a cantilever beam with force P at the free end, length $L_1$, wall reaction moment $M = P \cdot L_1$, and shear force $V = P$)*

### Equations & Symbolic Solution
* **Moment**: $M_1 = P \cdot L_1$
* **Section Modulus**: $Z_1 = \frac{b_1 \cdot h_1^2}{6}$
* **Bending Stress Constraint**: $\sigma = \frac{M_1}{Z_1} \le \sigma_{\text{allow}} \implies h_1 \ge \sqrt{\frac{6 \cdot P \cdot L_1}{b_1 \cdot \sigma_{\text{allow}}}}$
* **Deflection Constraint**: $\delta = \frac{P \cdot L_1^3}{3 \cdot E \cdot I_1} \le \delta_{\max}$ where $I_1 = \frac{b_1 \cdot h_1^3}{12} \implies h_1 \ge \sqrt[3]{\frac{4 \cdot P \cdot L_1^3}{E \cdot b_1 \cdot \delta_{\max}}}$

### Numerical Solution
* **Strength Design**:
  $$h_1 = \sqrt{\frac{6 \cdot 300 \cdot 35}{40 \cdot 20}} = \sqrt{78.75} \approx 8.87\text{ mm}$$
* **Stiffness/Deflection Design**:
  $$h_1 = \sqrt[3]{\frac{4 \cdot 300 \cdot 35^3}{3500 \cdot 40 \cdot 0.30}} = \sqrt[3]{\frac{51,450,000}{42,000}} = \sqrt[3]{1225} \approx 10.70\text{ mm}$$
* **Governing Dimension ($h_1$)**: $10.70\text{ mm}$ (Deflection governs)

---

## Feature 2 (Wall Mount Plate)

### Knowns & Unknowns
* **Knowns**: $P = 300\text{ N}$, effective length $L_2 = 50\text{ mm}$, $\sigma_{\text{allow}} = 20\text{ MPa}$, $E = 3500\text{ MPa}$, $\delta_{\max} = 0.30\text{ mm}$, beam width $b_2 = 50\text{ mm}$.
* **Unknowns**: Thickness $h_2$ based on stress, thickness $h_2$ based on deflection, final thickness $h_2$.

### Free Body Diagram (FBD)
*(Insert Image 2: FBD of Feature 2 showing wall mounting reaction forces at bolt locations and applied load P)*

### Equations & Symbolic Solution
* **Moment**: $M_2 = P \cdot L_2$
* **Bending Stress Constraint**: $h_2 \ge \sqrt{\frac{6 \cdot P \cdot L_2}{b_2 \cdot \sigma_{\text{allow}}}}$
* **Deflection Constraint**: $h_2 \ge \sqrt[3]{\frac{4 \cdot P \cdot L_2^3}{E \cdot b_2 \cdot \delta_{\max}}}$

### Numerical Solution
* **Strength Design**:
  $$h_2 = \sqrt{\frac{6 \cdot 300 \cdot 50}{50 \cdot 20}} = \sqrt{90} \approx 9.49\text{ mm}$$
* **Stiffness/Deflection Design**:
  $$h_2 = \sqrt[3]{\frac{4 \cdot 300 \cdot 50^3}{3500 \cdot 50 \cdot 0.30}} = \sqrt[3]{\frac{150,000,000}{52,500}} = \sqrt[3]{2857.14} \approx 14.19\text{ mm}$$
* **Governing Dimension ($h_2$)**: $14.19\text{ mm}$ (Deflection governs)

---

## Sketch (Isometric View)
*(Insert Image 3: Hand-drawn isometric sketch of the L-bracket motor mount with calculated thickness dimensions, motor mounting face, wall mounting face, and side gussets)*

---

## CAD Model (Parametric)
* Parametric dimensions were established in SolidWorks/Onshape linking calculated variables $h_1 = 10.7\text{ mm}$ and $h_2 = 14.2\text{ mm}$.
* Added side triangular gussets/ribs to reduce deflection and reinforce the $90^\circ$ bend.
* Features include $3.4\text{ mm}$ clearance holes for standard M3 wall/motor mounting bolts and a center clearance hole for the planetary gearbox shaft.

*(Insert Image 4: 3D CAD render or screenshot of the parametric motor mount model)*

---

## 2157 Engineering Drawing
*(Insert Image 5: ASME standard 2D multiview technical drawing sheet)*

* **Standard**: ASME 3rd Angle Projection
* **Views Included**: Front View, Right Side View, Top View, and Isometric View (upper-right corner).
* **Annotations & Features**:
  * Title block containing: Name, Date, Part Name ("Motor Mount"), Scale (1:1), Material (PLA).
  * Centerlines and center marks on all circular features.
  * Hole Callout: $\varnothing 3.4\text{ mm}$ clearance holes for M3 bolts.
  * Fully dimensioned for manufacturing without needing the 3D model.

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
* **Lessons Learned**: Calculating deflection for both features revealed that stiffness—rather than stress—governs the required wall thickness for 3D printed materials like PLA. Designing side gussets significantly reduces deflection without drastically increasing overall material volume.
