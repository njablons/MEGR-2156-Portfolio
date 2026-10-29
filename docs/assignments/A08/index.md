# Assignment 8: Gearbox Design & Analysis

## Overview
The goal of this assignment is to perform comprehensive mechanical design, stress analysis, bearing sizing, and parametric CAD modeling for a 24:9 spur gear reduction system. The custom assembly features a 2.0" × 2.0" × 1.0" two-part housing, precise 0.6875" center-to-center shaft spacing to ensure proper gear mesh, press-fit input/output shafts, and McMaster-Carr sleeve journal bearings.

---

## 1. Design of the Shafts

### 1.a. Input Shaft (Power-Transmission)
The input shaft transfers torque from the primary power source to the pinion gear (*d*<sub>in</sub> = 0.125 in, *L*<sub>in</sub> = 1.0 in).

* **Knowns:**
  * Output Torque (*T*<sub>out</sub>) = 1.25 in-lbf
  * Gear Ratio (*i*) = 24 : 9 = 2.667
  * Input Shaft Diameter (*d*<sub>in</sub>) = 0.125 in
  * Input Shaft Length (*L*) = 1.0 in
* **Unknowns:** Input Torque (*T*<sub>in</sub>), Maximum Shear Stress (&tau;<sub>in</sub>), Safety Factor.
* **Calculations:** 
  * *T*<sub>in</sub> = *T*<sub>out</sub> / *i* = 1.25 / 2.667 = 0.46875 in-lbf
  * &tau;<sub>in</sub> = 16 *T*<sub>in</sub> / (&pi; *d*<sub>in</sub><sup>3</sup>) = 16(0.46875) / (&pi; * 0.125<sup>3</sup>) &approx; 1,222.3 psi

![Input Shaft Calculations](images/input_shaft_calc.png)
*Figure 1: Handwritten Engineering Calculations for Input Shaft Stress*

![Input Shaft CAD Model](images/input_shaft_cad.png)
*Figure 2: Parametric Solid Model of the Input Shaft (0.125 in Diameter)*

* **Verdict:** *Sufficient.* The calculated shear stress of 1,222.3 psi is well below the yield shear strength of standard steel shafting (&approx; 15,000 psi - 30,000 psi), providing a high safety factor against torsional yield.

---

### 1.b. Output Shaft (Short Shaft)
The output shaft supports the driven output gear (*d*<sub>out</sub> = 0.250 in, *L*<sub>out</sub> = 1.0 in).

* **Knowns:**
  * Output Torque (*T*<sub>out</sub>) = 1.25 in-lbf
  * Output Shaft Diameter (*d*<sub>out</sub>) = 0.250 in
  * Output Shaft Length (*L*) = 1.0 in
* **Unknowns:** Maximum Shear Stress (&tau;<sub>out</sub>), Safety Factor.
* **Calculations:** 
  * &tau;<sub>out</sub> = 16 *T*<sub>out</sub> / (&pi; *d*<sub>out</sub><sup>3</sup>) = 16(1.25) / (&pi; * 0.25<sup>3</sup>) &approx; 407.4 psi

![Output Shaft Calculations](images/output_shaft_calc.png)
*Figure 3: Handwritten Engineering Calculations for Output Shaft Stress*

![Output Shaft CAD Model](images/output_shaft_cad.png)
*Figure 4: Parametric Solid Model of the Output Shaft (0.250 in Diameter)*

* **Verdict:** *Sufficient.* The maximum shear stress of 407.4 psi is well within allowable material limits.

---

## 2. Design of Journal Bearings

### 2.a. Bearing Size, Pressure, Velocity, and PV Rating
Journal bearings were sized to support the shafts while maintaining smooth rotational operation and minimal wear.

* **Knowns:** Speed *N* = 1100 rpm, Shaft Diameters (0.125 in and 0.250 in), Radial Forces derived from gear pitch loads.
* **Calculations:**
  * **Bearing Pressure (*P*):** *P* = *F*<sub>radial</sub> / (*d* &middot; *L*<sub>bearing</sub>)
  * **Surface Velocity (*V*):** *V* = (&pi; &middot; *d* &middot; *N*) / 12 (ft/min)
  * **PV Rating:** *PV* = *P* &times; *V*

![McMaster-Carr Component Selection](images/mcmaster_bearing_selection.png)
*Figure 5: McMaster-Carr Sleeve Journal Bearing Selection*

* **Material Selection:** Bronze/Oil-Impregnated Alloy sleeve bearings selected based on low friction coefficient and high allowable PV continuous limits (*PV*<sub>allowable</sub> > 10,000 psi&middot;ft/min).

---

### 2.b. Journal Bearing Wall Thickness
Wall thickness was verified to ensure adequate rigidity under press-fit mounting and radial gear loads.

![Journal Bearing Pressure, Velocity, and PV Sizing](images/journal_bearing_calc.png)
*Figure 7: Calculations for Journal Bearing Pressure, Velocity, and PV Ratings*

---

## 3. Gearbox Housing Concept & Layout
The gearbox housing consists of a two-part split design engineered for ease of manufacturing and assembly. 

---

## 4. Parametric CAD Assembly & Solid Models
Parametric 3D solid models were created in Creo Parametric to ensure proper spatial clearance and gear alignment.

---

## 5. Lessons Learned
- Accounting for full outer diameters of gears when designing housing clearance prevents interference during assembly.
- Proper shaft extension lengths must be maintained beyond external housing faces for coupling access.

---

## Downloadable Deliverables

### CAD Files
- [Assembly.zip](files/Assembly.zip) – Complete ZIP package containing all CAD files (`.prt`, `.asm`, `.drw`), STEP exports (`.stp`), and 2D engineering drawings (`.pdf`).
