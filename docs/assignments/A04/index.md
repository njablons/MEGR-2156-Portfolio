# A4 – Motor Mount

## Objective

Design a motor mount attached to a rigid wall for a 24V DC Gear Motor (3.6 kg·cm / 46 RPM w/ 99.5:1 Planetary Gearbox) subjected to a load <b>P = 300 N</b> at the free end. The design evaluates both yield strength (with a safety factor <b>N = 3</b>) and deflection constraints (<b>δ<sub>max</sub> ≤ 0.30 mm</b>) using beam bending equations.

---

## Material Selection

* **Material**: PLA (Polylactic Acid)
* **Yield Strength (σ<sub>y</sub>)**: 60 MPa
* **Elastic Modulus (E)**: 3.5 GPa (3500 MPa)
* **Factor of Safety (N)**: 3
* **Allowable Bending Stress (σ<sub>allow</sub>)**: σ<sub>allow</sub> = σ<sub>y</sub> / N = 60 / 3 = **20 MPa**

---

## Feature 1 (Motor Attachment Plate)

### Knowns & Unknowns

* **Knowns**: P = 300 N, L<sub>1</sub> = 35 mm, σ<sub>allow</sub> = 20 MPa, E = 3500 MPa, δ<sub>max</sub> = 0.30 mm, beam width b<sub>1</sub> = 40 mm.
* **Unknowns**: Thickness h<sub>1</sub> based on stress, thickness h<sub>1</sub> based on deflection, final governing thickness h<sub>1</sub>.

### Free Body Diagram (FBD) & Calculations

<img src="../IMG_4085.jpeg" alt="Feature 1 Hand Calculations, Free Body Diagram, and Moment Derivation" width="100%">

*Figure 1: Hand calculations, FBD, and moment derivation for Feature 1 (Motor Attachment Plate).*

### Equations & Symbolic Solution

* **Moment**: M<sub>1</sub> = P · L<sub>1</sub>
* **Section Modulus**: Z<sub>1</sub> = (b<sub>1</sub> · h<sub>1</sub><sup>2</sup>) / 6
* **Bending Stress Constraint**: σ = M<sub>1</sub> / Z<sub>1</sub> ≤ σ<sub>allow</sub>  ⇒  <b>h<sub>1</sub> ≥ √( (6 · P · L<sub>1</sub>) / (b<sub>1</sub> · σ<sub>allow</sub>) )</b>
* **Deflection Constraint**: δ = (P · L<sub>1</sub><sup>3</sup>) / (3 · E · I<sub>1</sub>) ≤ δ<sub>max</sub>  ⇒  <b>h<sub>1</sub> ≥ ∛( (4 · P · L<sub>1</sub><sup>3</sup>) / (E · b<sub>1</sub> · δ<sub>max</sub>) )</b>

### Numerical Solution

* **Strength Design**: h<sub>1</sub> = √( (6 · 300 · 35) / (40 · 20) ) = √78.75 ≈ **8.87 mm**
* **Stiffness/Deflection Design**: h<sub>1</sub> = ∛( (4 · 300 · 35<sup>3</sup>) / (3500 · 40 · 0.30) ) = ∛1225 ≈ **10.70 mm**
* **Governing Dimension (h<sub>1</sub>)**: **10.70 mm** (Deflection governs)

---

## Feature 2 (Wall Mount Plate)

### Knowns & Unknowns

* **Knowns**: P = 300 N, effective length L<sub>2</sub> = 50 mm, σ<sub>allow</sub> = 20 MPa, E = 3500 MPa, δ<sub>max</sub> = 0.30 mm, beam width b<sub>2</sub> = 50 mm.
* **Unknowns**: Thickness h<sub>2</sub> based on stress, thickness h<sub>2</sub> based on deflection, final governing thickness h<sub>2</sub>.

### Free Body Diagram (FBD) & Calculations

<img src="../IMG_4086.jpeg" alt="Feature 2 Hand Calculations, Free Body Diagram, and Stress Derivation" width="100%">

*Figure 2: Hand calculations, FBD, and moment derivation for Feature 2 (Wall Mount Plate).*

### Equations & Symbolic Solution

* **Moment**: M<sub>2</sub> = P · L<sub>2</sub>
* **Bending Stress Constraint**: <b>h<sub>2</sub> ≥ √( (6 · P · L<sub>2</sub>) / (b<sub>2</sub> · σ<sub>allow</sub>) )</b>
* **Deflection Constraint**: <b>h<sub>2</sub> ≥ ∛( (4 · P · L<sub>2</sub><sup>3</sup>) / (E · b<sub>2</sub> · δ<sub>max</sub>) )</b>

### Numerical Solution

* **Strength Design**: h<sub>2</sub> = √( (6 · 300 · 50) / (50 · 20) ) = √90 ≈ **9.49 mm**
* **Stiffness/Deflection Design**: h<sub>2</sub> = ∛( (4 · 300 · 50<sup>3</sup>) / (3500 · 50 · 0.30) ) = ∛2857.14 ≈ **14.19 mm**
* **Governing Dimension (h<sub>2</sub>)**: **14.19 mm** (Deflection governs)

---

## Sketch (Isometric View)

<img src="../IMG_4087.jpeg" alt="Hand-drawn Isometric Sketch of the Motor Mount Assembly" width="100%">

*Figure 3: Hand-drawn isometric sketch detailing dimensions and feature geometry.*

---

## CAD Model (Parametric)

<img src="../Screenshot%202026-09-16%20141452.png" alt="3D Parametric CAD Model rendered in PTC Creo Parametric" width="100%">

*Figure 4: Parametric 3D CAD model in PTC Creo showing the motor clearance hole and wall mounting holes.*

* **Parametric Control**: Driven via Creo Parameters and Relations linking calculated values h<sub>1</sub> = 10.70 mm and h<sub>2</sub> = 14.19 mm.
* **Clearance Features**: Standard Ø3.4 mm clearance holes for M3 wall/motor mounting bolts and a center clearance hole for the planetary gearbox shaft.

---

## CAD File Downloads

* [Download PTC Creo Part File (.prt.1)](../sodesigna4.prt.1)

---

## Appendix (Motor Mount Inspiration & Links)

* [omc-stepperonline.com - 24V DC Gear Motor Technical Drawings](https://www.omc-stepperonline.com/brushed-24v-dc-gear-motor-3-6kg-cm-46rpm-w-99-5-1-planetary-gearbox-pa28-28245800-g100)
* [Aliexpress - NEMA 17 L-Bracket Motor Mount Reference](https://www.aliexpress.com/item/1005005721086783.html)
* [DHgate - Steel Stepper Motor Mounting Bracket Reference](https://www.dhgate.com/product/steel-42-stepper-motor-mount-bracket-nema17/996764543.html)

---

## Documentation & Lessons Learned

### Process Documentation & Timeline
* **Start to Finish Time**: ~3.5 hours total.
  * **Research & Setup**: 30 mins reading specs and identifying beam mechanics equations.
  * **Math & FBDs**: 1 hour solving both features for strength and deflection.
  * **Sketching**: 30 mins drafting the isometric view with dimension callouts.
  * **Creo Parametric Modeling**: 1 hour creating parameters, sketch relations, extrusions, and hole cuts.
  * **Portfolio Markdown Page**: 30 mins formatting and linking files.

### Lessons Learned & Challenges
1. **Deflection Governs Design**: In both features, the thickness required for stiffness (h<sub>1</sub> = 10.70 mm, h<sub>2</sub> = 14.19 mm) was significantly larger than the strength requirement (8.87 mm and 9.49 mm). This proved that stiffness constraints (δ ≤ 0.30 mm) drive geometry for cantilever mounts much more than yield failure.
2. **Creo Parametric Relations**: Linking sketch dimensions directly to parameters (`b1`, `h1`, `b2`, `h2`) ensured that any future design changes automatically regenerate the 3D model without breaking features.
3. **Simple vs. Complex Aesthetics**: While raw blocky geometry satisfies structural math, adding interior fillets or side gussets significantly improves stress distribution and visual appearance.
