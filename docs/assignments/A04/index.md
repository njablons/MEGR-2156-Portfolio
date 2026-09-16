# A4 – Motor Mount

## Objective

Design a motor mount attached to a rigid wall for a 24V DC Gear Motor (3.6 kg·cm / 46 RPM w/ 99.5:1 Planetary Gearbox) subjected to a load *P = 300 N* at the free end. The design evaluates both yield strength (with a safety factor *N = 3*) and deflection constraints (*δ_max ≤ 0.30 mm*) using beam bending equations.

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

* **Knowns**: $P = 300\text{ N}$, $L_1 = 35\text{ mm}$, $\sigma_{\text{allow}} = 20\text{ MPa}$, $E = 3500\text{ MPa}$, $\delta_{\text{max}} = 0.30\text{ mm}$, beam width $b_1 = 40\text{ mm}$.
* **Unknowns**: Thickness $h_1$ based on stress, thickness $h_1$ based on deflection, final governing thickness $h_1$.

### Free Body Diagram (FBD) & Calculations

![Feature 1 Hand Calculations and FBD](IMG_4085.jpeg)

### Equations & Symbolic Solution

* **Moment**: $M_1 = P \cdot L_1$
* **Section Modulus**: $Z_1 = \frac{b_1 \cdot h_1^2}{6}$
* **Bending Stress Constraint**: $\sigma = \frac{M_1}{Z_1} \le \sigma_{\text{allow}} \implies h_1 \ge \sqrt{\frac{6 \cdot P \cdot L_1}{b_1 \cdot \sigma_{\text{allow}}}}$
* **Deflection Constraint**: $\delta = \frac{P \cdot L_1^3}{3 \cdot E \cdot I_1} \le \delta_{\text{max}} \quad \text{where } I_1 = \frac{b_1 \cdot h_1^3}{12} \implies h_1 \ge \sqrt[3]{\frac{4 \cdot P \cdot L_1^3}{E \cdot b_1 \cdot \delta_{\text{max}}}}$

### Numerical Solution

* **Strength Design**:
  $$h_1 = \sqrt{\frac{6 \cdot 300 \cdot 35}{40 \cdot 20}} = \sqrt{78.75} \approx 8.87\text{ mm}$$

* **Stiffness/Deflection Design**:
  $$h_1 = \sqrt[3]{\frac{4 \cdot 300 \cdot (35)^3}{3500 \cdot 40 \cdot 0.30}} = \sqrt[3]{1225} \approx 10.70\text{ mm}$$

* **Governing Dimension ($h_1$)**: **$10.70\text{ mm}$** (Deflection governs)

---

## Feature 2 (Wall Mount Plate)

### Knowns & Unknowns

* **Knowns**: $P = 300\text{ N}$, effective length $L_2 = 50\text{ mm}$, $\sigma_{\text{allow}} = 20\text{ MPa}$, $E = 3500\text{ MPa}$, $\delta_{\text{max}} = 0.30\text{ mm}$, beam width $b_2 = 50\text{ mm}$.
* **Unknowns**: Thickness $h_2$ based on stress, thickness $h_2$ based on deflection, final governing thickness $h_2$.

### Free Body Diagram (FBD) & Calculations

![Feature 2 Hand Calculations and FBD](IMG_4086.jpeg)

### Equations & Symbolic Solution

* **Moment**: $M_2 = P \cdot L_2$
* **Bending Stress Constraint**: $h_2 \ge \sqrt{\frac{6 \cdot P \cdot L_2}{b_2 \cdot \sigma_{\text{allow}}}}$
* **Deflection Constraint**: $h_2 \ge \sqrt[3]{\frac{4 \cdot P \cdot L_2^3}{E \cdot b_2 \cdot \delta_{\text{max}}}}$

### Numerical Solution

* **Strength Design**:
  $$h_2 = \sqrt{\frac{6 \cdot 300 \cdot 50}{50 \cdot 20}} = \sqrt{90} \approx 9.49\text{ mm}$$

* **Stiffness/Deflection Design**:
  $$h_2 = \sqrt[3]{\frac{4 \cdot 300 \cdot (50)^3}{3500 \cdot 50 \cdot 0.30}} = \sqrt[3]{2857.14} \approx 14.19\text{ mm}$$

* **Governing Dimension ($h_2$)**: **$14.19\text{ mm}$** (Deflection governs)

---

## Sketch (Isometric View)

![Hand-drawn Isometric Sketch of Motor Mount](IMG_4087.jpeg)

---

## CAD Model (Parametric)

![3D Parametric CAD Model in PTC Creo](Screenshot%202026-09-16%20141452.png)

* **Parametric Control**: Driven via Creo Parameters and Relations linking calculated values $h_1 = 10.7\text{ mm}$ and $h_2 = 14.2\text{ mm}$.
* **Clearance Features**: Standard $\varnothing 3.4\text{ mm}$ clearance holes for M3 wall/motor mounting bolts and a center clearance hole for the planetary gearbox shaft.

---

## CAD File Downloads

* [Download PTC Creo Part File (.prt.1)](sodesigna4.prt.1)

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
1. **Deflection Governs Design**: In both features, the thickness required for stiffness ($h_1 = 10.70\text{ mm}$, $h_2 = 14.19\text{ mm}$) was significantly larger than the strength requirement ($8.87\text{ mm}$ and $9.49\text{ mm}$). This proved that stiffness constraints ($\delta \le 0.30\text{ mm}$) drive geometry for cantilever mounts much more than yield failure.
2. **Creo Parametric Relations**: Linking sketch dimensions directly to parameters (`b1`, `h1`, `b2`, `h2`) ensured that any future design changes automatically regenerate the 3D model without breaking features.
3. **Simple vs. Complex Aesthetics**: While raw blocky geometry satisfies structural math, adding interior fillets or side gussets significantly improves stress distribution and visual appearance.
