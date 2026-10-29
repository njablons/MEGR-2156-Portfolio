# Assignment 8: Gearbox Design & Analysis

## Overview
The goal of this assignment is to perform comprehensive mechanical design, stress analysis, bearing sizing, and parametric CAD modeling for a 24:9 spur gear reduction system. The custom assembly features a 2.0" × 2.0" × 1.0" two-part housing, precise 0.6875" center-to-center shaft spacing to ensure proper gear mesh, press-fit input/output shafts, and McMaster-Carr sleeve journal bearings.

---

## 1. Design of the Shafts

### 1.a. Input Shaft (Power-Transmission)
The input shaft transfers torque from the primary power source to the pinion gear ($d_{in} = 0.125\text{ in}$, $L_{in} = 1.0\text{ in}$).

* **Knowns:** 
  * Output Torque ($T_{out}$) = $1.25\text{ in}\cdot\text{lb}_f$
  * Gear Ratio ($i$) = $24 : 9 = 2.667$
  * Input Shaft Diameter ($d_{in}$) = $0.125\text{ in}$
  * Input Shaft Length ($L$) = $1.0\text{ in}$
* **Unknowns:** Input Torque ($T_{in}$), Maximum Shear Stress ($\tau_{in}$), Safety Factor.
* **Calculations:**
  $$T_{in} = \frac{T_{out}}{i} = \frac{1.25}{2.667} = 0.46875\text{ in}\cdot\text{lb}_f$$
  $$\tau_{in} = \frac{16 T_{in}}{\pi d_{in}^3} = \frac{16 (0.46875)}{\pi (0.125)^3} \approx 1,222.3\text{ psi}$$

![Input Shaft Calculations](IMG_4193.jpeg)
*Figure 1: Handwritten Engineering Calculations for Input Shaft Stress*

![Input Shaft CAD Model](Screenshot%202026-10-28%20191448.png)
*Figure 2: Parametric Solid Model of the Input Shaft ($0.125\text{ in}$ Diameter)*

* **Verdict:** **Sufficient.** The calculated shear stress of $1,222.3\text{ psi}$ is well below the yield shear strength of standard steel shafting ($\approx 15,000\text{ psi} - 30,000\text{ psi}$), providing a high safety factor against torsional yield.

---

### 1.b. Output Shaft (Short Shaft)
The output shaft supports the driven output gear ($d_{out} = 0.250\text{ in}$, $L_{out} = 1.0\text{ in}$).

* **Knowns:**
  * Output Torque ($T_{out}$) = $1.25\text{ in}\cdot\text{lb}_f$
  * Output Shaft Diameter ($d_{out}$) = $0.250\text{ in}$
  * Output Shaft Length ($L$) = $1.0\text{ in}$
* **Unknowns:** Maximum Shear Stress ($\tau_{out}$), Safety Factor.
* **Calculations:**
  $$\tau_{out} = \frac{16 T_{out}}{\pi d_{out}^3} = \frac{16 (1.25)}{\pi (0.25)^3} \approx 407.4\text{ psi}$$

![Output Shaft Calculations](IMG_4194.jpeg)
*Figure 3: Handwritten Engineering Calculations for Output Shaft Stress*

![Output Shaft CAD Model](Screenshot%202026-10-28%20191455.png)
*Figure 4: Parametric Solid Model of the Output Shaft ($0.250\text{ in}$ Diameter)*

* **Verdict:** **Sufficient.** The maximum shear stress of $407.4\text{ psi}$ is well within allowable material limits.

---

## 2. Design of Journal Bearings

### 2.a. Bearing Size, Pressure, Velocity, and PV Rating
Journal bearings were sized to support the shafts while maintaining smooth rotational operation and minimal wear.

* **Knowns:** Speed $N = 1100\text{ rpm}$, Shaft Diameters ($0.125\text{ in}$ and $0.250\text{ in}$), Radial Forces derived from gear pitch loads.
* **Calculations:**
  * **Bearing Pressure ($P$):** $P = \frac{F_{radial}}{d \cdot L_{bearing}}$
  * **Surface Velocity ($V$):** $V = \frac{\pi \cdot d \cdot N}{12}\text{ (ft/min)}$
  * **PV Rating:** $PV = P \times V$

![Journal Bearing Pressure, Velocity, and PV Sizing](IMG_4195.jpeg)
*Figure 5: Calculations for Journal Bearing Pressure, Velocity, and PV Ratings*

* **Material Selection:** Bronze/Oil-Impregnated Alloy sleeve bearings selected based on low friction coefficient and high allowable PV continuous limits ($PV_{\text{allowable}} > 10,000\text{ psi}\cdot\text{ft/min}$).

---

### 2.b. Journal Bearing Wall Thickness
Wall thickness was evaluated to ensure structural rigidity and proper press-fit tolerance within the 2.0" × 2.0" × 1.0" housing.

![Journal Bearing Thickness Analysis](IMG_4198.jpeg)
*Figure 6: Free Body Diagram and Equations for Journal Bearing Wall Thickness*

---

### 2.c. McMaster-Carr Component Selection
* **Pinion Spur Gear:** [McMaster-Carr 7880K19](https://www.mcmaster.com/catalog/129/1330/7880K19)
* **Output Spur Gear:** [McMaster-Carr 7880K24](https://www.mcmaster.com/catalog/129/1330/7880K24)
* **Sleeve Bearings:** [McMaster-Carr Plain Journal Bearings](https://www.mcmaster.com/products/journal-bearings/sleeve-bearings-3~/)

---

## 3. Gearbox Housing Concept & Layout

The housing consists of a two-part split assembly measuring **2.0 in × 2.0 in × 1.0 in**. 
* **Center Distance:** The shaft center-to-center distance was defined at **0.6875 in** to match the pitch radii sum of the 24T and 9T meshing spur gears, ensuring smooth tooth engagement without binding.
* **Fastening:** The top lid and bottom base fit together securely using recessed mounting fasteners and alignment pins.

![Gearbox Orthographic & Sectional Views](IMG_4196.jpeg)
*Figure 7: Hand Sketches and Layout Views of the Two-Component Housing Assembly*

---

## 4. Parametric CAD Assembly & Solid Models

The complete assembly was generated parametrically in Creo Parametric to ensure all clearances and fits adhere to standard running/sliding fit tolerances.

![Shafts Mounted in Housing Base](Screenshot%202026-10-28%20195315.png)
*Figure 8: Isometric View of Input and Output Shafts Mounted in the 2.0" × 2.0" × 1.0" Housing Base*

![Top View of Open Gearbox showing Gear Mesh](Screenshot%202026-10-28%20200434.png)
*Figure 9: Top View showing Gear Mesh Alignment at the 0.6875 in Center-to-Center Spacing*

![Fully Enclosed Gearbox Assembly](Screenshot%202026-10-28%20200534.png)
*Figure 10: Fully Assembled 2-Part Gearbox Housing with Lid Attached*

---

## 5. Lessons Learned

This assignment required approximately **7 hours** total from initial calculations to final CAD assembly and portfolio rendering. Key engineering insights gained include:

* **Pitch Center Spacing Mechanics:** Setting the precise $0.6875\text{ in}$ center-to-center distance was critical. Even slight deviations in spacing cause either binding due to insufficient backlash or premature tooth wear from loose mesh alignment.
* **Parametric Housing Sizing:** Optimizing the outer housing envelope down to $2.0\text{ in} \times 2.0\text{ in} \times 1.0\text{ in}$ reduced overall material volume while maintaining required clearance for the rotating output gear hub and sleeve bearings.
* **Torsional Shear Stress Limits:** Performing torsional stress analysis verified that standard $0.125\text{ in}$ and $0.250\text{ in}$ shafting operate well below yield thresholds under a $1.25\text{ in}\cdot\text{lb}_f$ torque load.

---

## Downloadable Deliverables

### CAD Files
- [Download Gearbox Assembly (.asm)](gearbox_assembly.asm.1)
