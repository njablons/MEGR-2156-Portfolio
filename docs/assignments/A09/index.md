# A9 – Pulley System

## Objective

Designed a two-pulley power transmission system transferring rotational power between two parallel shafts separated by a center distance of 5.0 inches. The assignment requires calculating dynamic belt forces, sizing the drive shaft for torsional shear load, selecting a sintered journal bearing via *Machinery's Handbook* $PV$ limits, engineering a supporting frame with side guide walls, and detailing lessons learned.

---

## Belt selection

### Symbolic Model & Derivation
1. **Belt Tension Equilibrium:**
   $$T_1 + T_2 = 2 T_0$$
   $$\frac{T_1}{T_2} = e^{\mu \theta}$$
   Substituting $T_1 = T_2 e^{\mu \theta}$ into the static equilibrium equation:
   $$T_2(1 + e^{\mu \theta}) = 2 T_0 \implies T_2 = \frac{2 T_0}{1 + e^{\mu \theta}}$$
   $$T_1 = 2 T_0 - T_2$$

2. **Allowable Normal Stress & Cross-Sectional Area:**
   $$\sigma_{\text{allow}} = \frac{\sigma_y}{N_s}$$
   $$A_{\text{req}} = \frac{T_1}{\sigma_{\text{allow}}} = \frac{N_s \cdot T_1}{\sigma_y}$$

3. **Minimum Belt Diameter & Outer Circumference:**
   $$d_{\text{belt}} = \sqrt{\frac{4 A_{\text{req}}}{\pi}}$$
   $$L = 2C + \pi D$$

### Numerical Calculations
* **Tension Ratio & Forces:**
  $$\frac{T_1}{T_2} = e^{(0.30)(\pi)} = e^{0.9425} \approx 2.566$$
  $$T_2 = \frac{2(5.0\text{ lbf})}{1 + 2.566} = \frac{10.0}{3.566} = 2.804\text{ lbf}$$
  $$T_1 = 10.0\text{ lbf} - 2.804\text{ lbf} = 7.196\text{ lbf}$$

* **Allowable Stress & Required Cross-Sectional Area:**
  $$\sigma_{\text{allow}} = \frac{471\text{ psi}}{3} = 157.0\text{ psi}$$
  $$A_{\text{req}} = \frac{7.196\text{ lbf}}{157.0\text{ psi}} = 0.04583\text{ in}^2$$

* **Minimum Belt Diameter & Pitch Length:**
  $$d_{\text{belt}} = \sqrt{\frac{4(0.04583\text{ in}^2)}{\pi}} = 0.2416\text{ in} \approx \frac{1}{4}\text{ in}$$
  $$L = 2(5.0\text{ in}) + \pi(3.0\text{ in}) = 10.0 + 9.425 = 19.425\text{ in}$$

### Commercial Component Selection
* **Vendor & Part Number:** [McMaster-Carr Part #3044K606](https://www.mcmaster.com/products/round-belts/diameter~1-4-1/outer-circumference~19-1-2/)
* **Specifications:** Polyurethane Rubber Round Belt, 1/4" Diameter, 19-1/2" Outer Circumference
* **Engineering Justification:** The theoretical pitch length calculated is $L = 19.425\text{ in}$ with a minimum required cross-sectional diameter of $d_{\text{belt}} = 0.2416\text{ in}$. [McMaster-Carr Part #3044K606](https://www.mcmaster.com/products/round-belts/diameter~1-4-1/outer-circumference~19-1-2/) ($1/4\text{ in}$ nominal diameter, polyurethane rubber, 19-1/2" outer circumference) satisfies both the stress limits and length geometry while matching the polyurethane material specified in the prompt.

---

## Shaft Design

### Symbolic Model & Derivation
1. **Applied Torque:**
   $$T = (T_1 - T_2) \cdot r$$

2. **Allowable Shear Stress (Distortion Energy Theory):**
   $$\tau_{\text{allow}} = \frac{S_{sy}}{N_s} = \frac{0.577 \cdot S_y}{N_s}$$

3. **Minimum Shaft Diameter Derivation:**
   $$\tau = \frac{T \cdot c}{J} = \frac{T (d_s / 2)}{\frac{\pi d_s^4}{32}} = \frac{16 T}{\pi d_s^3} \le \tau_{\text{allow}}$$
   $$d_s = \left( \frac{16 T}{\pi \tau_{\text{allow}}} \right)^{\frac{1}{3}}$$

### Numerical Calculations
* **Net Transmitted Torque:**
  $$T = (7.196\text{ lbf} - 2.804\text{ lbf}) \times 1.5\text{ in} = 6.588\text{ in-lbf}$$

* **Allowable Shear Stress:**
  $$\tau_{\text{allow}} = \frac{0.577 \times 90,000\text{ psi}}{3} = \frac{51,930\text{ psi}}{3} = 17,310\text{ psi}$$

* **Minimum Shaft Diameter:**
  $$d_s = \left( \frac{16 \times 6.588\text{ in-lbf}}{\pi \times 17,310\text{ psi}} \right)^{\frac{1}{3}} = (0.001939)^{\frac{1}{3}} = 0.1247\text{ in}$$

**Selected Shaft Size:** Standard $1/8\text{ in}$ nominal ($0.125\text{ in}$) precision ground 1060 hardened steel shafting.

---

## Journal Bearing

### Symbolic Model & Derivation
1. **Projected Bearing Pressure ($P$):**
   $$P = \frac{W}{d_b \cdot L_b} \quad \text{where } W = T_1 + T_2$$

2. **Surface Linear Velocity ($V$):**
   $$V = \frac{\pi \cdot d_b \cdot n}{12} \quad [\text{ft/min}]$$

3. **Pressure-Velocity Product ($PV$):**
   $$PV = P \times V$$

### Numerical Calculations
* **Bearing Inner Diameter:** $d_b = 0.1250\text{ in} + 0.0007\text{ in} = 0.1257\text{ in}$ (RC5 Fit)
* **Projected Pressure ($P$):**
  $$P = \frac{10.0\text{ lbf}}{(0.1257\text{ in})(0.50\text{ in})} = 159.1\text{ psi}$$

* **Linear Velocity ($V$):**
  $$V = \frac{\pi \times 0.1257\text{ in} \times 1500\text{ RPM}}{12} = 49.37\text{ ft/min}$$

* **PV Product Rating:**
  $$PV = 159.1\text{ psi} \times 49.37\text{ ft/min} = 7,855\text{ psi-ft/min}$$

### Material Selection
* **Selected Material:** **Porous Bronze (Sintered)**
* **Justification:** Based on Table 4 (pg. 2440) in *Machinery's Handbook*, oil-impregnated **Porous Bronze** provides a maximum allowable $PV$ capacity of $50,000\text{ psi-ft/min}$, a maximum static load rating of $2,000\text{ psi}$, and a maximum continuous surface speed of $1,200\text{ fpm}$. Our calculated operating parameters ($P = 159.1\text{ psi}$, $V = 49.4\text{ fpm}$, $PV = 7,855\text{ psi-ft/min}$) fall well within these allowable limits.

---

## Frame Design

### Engineering Drawing Specifications & Annotations
* **Front View Dimensions:**
  * **Center-to-Center Distance:** $5.00\text{ in}$ between shaft bores.
  * **Overall Frame Length:** $7.50\text{ in}$ (provides $1.25\text{ in}$ end margin past each $3.00\text{ in}$ pulley radius).
  * **Overall Frame Height:** $3.25\text{ in}$ (provides $0.125\text{ in}$ vertical clearance over the $3.00\text{ in}$ pulley diameter).
  * **Shaft Bores:** $\varnothing 0.1257\text{ in}$ precision bored holes for housing porous bronze journal bushings.

* **Side View Dimensions:**
  * **Overall Frame Width:** $1.25\text{ in}$
  * **Internal Channel Clearance Width:** $1.00\text{ in}$ (provides axial clearance for pulley width and belt line).
  * **Plate Wall Thickness:** $0.125\text{ in}$ (Aluminum 6061-T6 structural plates).

* **Retention Walls / Guide Rails:**
  * Raised $0.125\text{ in}$ flange walls run continuously along the perimeter to guide the round belt, preventing lateral tracking and axial dislodgement off the pulleys during dynamic 1500 RPM operation.

---

## Lessons Learned

* **Tensional Equilibrium in Belt Drives:** I learned how exponential friction engagement ($e^{\mu\theta}$) across the contact arc dictates the maximum force differential between tight ($T_1$) and loose ($T_2$) sides before power-limiting slip occurs.
* **Distortion Energy Application in Shaft Design:** I learned how to apply Distortion Energy Theory ($S_{sy} = 0.577 S_y$) to convert pure tensile yield strength into allowable shear stress when calculating minimum shaft diameters under pure torsional load.
* **$PV$ Rating Evaluation for Journal Bearings:** I learned how to evaluate combined pressure ($P$) and velocity ($V$) parameters against standard industry tables in *Machinery's Handbook* (Table 4) to verify oil-impregnated porous metal sleeve longevity.
* **Constraint Integration in Chassis Design:** I learned how physical operational hazards require integrated structural features, such as perimeter retaining rails on chassis walls, to prevent lateral belt walk under dynamic vibration.
