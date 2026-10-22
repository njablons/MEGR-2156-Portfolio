# Assignment 7: FEA Bracket Design Optimization

## Overview
The goal of this assignment is to perform finite element analysis (FEA) on a structural bracket using PTC Creo Simulate, iteratively refining the design through an inner-loop mesh convergence process and outer-loop structural modifications to meet safety factor and deflection requirements under a 600 lbf load.

---

## Design Iterations

### Design 1 (Baseline)
The initial baseline geometry was evaluated under primary loading conditions (600 lbf downward load on Section A with Section E fully constrained). High stress concentration was observed at the sharp re-entrant corner between Section A and Section B.

![Design 1 Von Mises Stress](Screenshot%202026-10-21%20200028.png)
*Figure 1: Design 1 Von Mises Stress Contour Plot*

![Design 1 Deformation](Screenshot%202026-10-21%20200044.png)
*Figure 2: Design 1 Deformation / Displacement Plot*

---

### Design 2 (Fillet Enhancement)
To reduce the severe stress riser at the neck, a 0.10 in fillet radius was added to the re-entrant corner between Section A and Section B.

![Design 2 Von Mises Stress](Screenshot%202026-10-21%20204853.png)
*Figure 3: Design 2 Von Mises Stress Contour Plot*

![Design 2 Deformation](Screenshot%202026-10-21%20204846.png)
*Figure 4: Design 2 Deformation / Displacement Plot*

---

### Design 3 (Final Optimized Design)
To achieve a passing safety factor (> 1.0) and satisfy stiffness criteria, major topology enhancements were implemented:
1. Section B was widened to increase the area moment of inertia against bending.
2. A structural support rib was added between Section A and Section C to redistribute the primary stress path away from the neck.

![Design 3 Von Mises Stress](Screenshot%202026-10-21%20204732.png)
*Figure 5: Design 3 Von Mises Stress Contour Plot*

![Design 3 Deformation](Screenshot%202026-10-21%20204746.png)
*Figure 6: Design 3 Deformation / Displacement Plot*

---

## Results Summary & Comparison

| Parameter | Design I | Design II | Design III |
| :--- | :---: | :---: | :---: |
| Safety Factor | 0.18 | 0.24 | **1.59** |
| Max Stress (ksi) / Location | 221.76 / Interface A & B | 165.74 / Interface A & B | **25.10 / Support Rib** |
| Deflection (in) / Location | 0.000616 / Section B | 0.000626 / Section B | **0.0000216 / Section B** |
| Mass (lbm) | 0.268 | 0.268 | **0.293** |
| Element Count | 10,021 | 27,831 | **61,431** |

---

## Lessons Learned
This assignment required approximately 8 hours total. A majority of the time was spent executing inner-loop mesh convergence runs, capturing high-resolution stress and deflection plots, and managing CAD files within Apporto. 

Key engineering insights gained from this assignment include:
- **Mesh Convergence Mechanics:** Refining the global element size increases computational fidelity near high-stress gradients. Achieving an inner-loop convergence threshold of ≤ 7% validates that numerical stress singularities are minimized and the FEA model has stabilized.
- **Stress Concentration Mitigation:** Sharp re-entrant corners act as severe geometric stress risers. Introducing a simple 0.10 in transition fillet redistributed the load path, reducing peak stress from 221.76 ksi to 165.74 ksi.
- **Structural Topology Optimization:** Adding a structural support rib effectively transformed the bending moment at the neck into axial compression and tension across the rib, increasing the overall Safety Factor to 1.59 while maintaining a minimal mass penalty (+0.025 lbm).

---

## Downloadable Deliverables

### CAD Files
- [Download Design 1 (.zip)](a06bracketdesign.zip)
