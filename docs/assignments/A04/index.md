# A4 – Motor Mount

## Objective

Design a motor mount attached to a rigid wall for a 24V DC Gear Motor (3.6 kg·cm / 46 RPM w/ 99.5:1 Planetary Gearbox) subjected to a load *P = 300 N* at the free end. The design evaluates both yield strength (with a safety factor *N = 3*) and deflection constraints (*$\delta_{\text{max}} \le 0.30\text{ mm}$*) using beam bending equations.

---

## Material Selection

* **Material**: PLA (Polylactic Acid)
* **Yield Strength ($\sigma_y$)**: $60\text{ MPa}$
* **Elastic Modulus ($E$)**: $3.5\text{ GPa}$ ($3500\text{ MPa}$)
* **Factor of Safety ($N$)**: $3$
* **Allowable Bending Stress ($\sigma_{\text{allow}}$)**: $\sigma_{\text{allow}} = \frac{\sigma_y}{N} = \frac{60\text{ MPa}}{3} = 20\text{ MPa}$

---

## Feature 1 (Motor Attachment Plate)

### Knowns & Unknowns

* **Knowns**: $P = 300\text{ N}$, $L_1 = 35\text{ mm}$, $\sigma_{\text{allow}} = 20\text{ MPa}$, $E = 3500\text{ MPa}$, $\delta_{\text{max}} = 0.30\text{ mm}$, beam width $b_1 = 40\text{ mm}$.
* **Unknowns**: Thickness $h_1$ based on stress, thickness $h_1$ based on deflection, final governing thickness $h_1$.

### Free Body Diagram (FBD) & Calculations

![Feature 1 Hand Calculations and FBD](IMG_4085.jpeg)
*Figure 1: Hand calculations, FBD, and moment analysis for Feature 1 (Motor Attachment Plate).*

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

* **Governing Dimension ($h_1$)**: **$10.70\text{ mm}$** (DefHere is the updated, corrected Markdown code. The image paths include proper alt captions, and all single backslashes in your LaTeX math syntax are escaped so MkDocs renders the formulas correctly without breaking:

```markdown
# A4 – Motor Mount

## Objective

Design a motor mount attached to a rigid wall for a 24V DC Gear Motor (3.6 kg·cm / 46 RPM w/ 99.5:1 Planetary Gearbox) subjected to a load *P = 300 N* at the free end. The design evaluates both yield strength (with a safety factor *N = 3*) and deflection constraints ($\delta_{\text{max}} \le 0.30\text{ mm}$) using beam bending equations.

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

![Feature 1 Hand Calculations, Free Body Diagram, and Moment Derivation](IMG_4085.jpeg)
*Figure 1: Hand calculations, FBD, and moment derivation for Feature 1 (Motor Attachment Plate).*

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

### Known
