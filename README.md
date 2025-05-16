# 🚀 MPC Rocket Controller – Mini Project (Autumn 2023)

This repository contains the code (in `.zip` format) and final report for the **Model Predictive Control** mini-project completed in Autumn 2023 at EPFL. The goal was to design and test a set of MPC and NMPC controllers to simulate and control a 12-state rocket system under various dynamic and environmental conditions.


🗂️ **Source code included as ZIP archive**
📄 [Download the full report (PDF)](./MPC_Project_Report.pdf)


If the Github Preview for the report does not work, please download the raw file to view it.



---

## 📌 Project Summary

The rocket's dynamics are described using 12 state variables including angular velocities, orientations, velocities, and positions. The project proceeded in the following stages:

1. **Linearization** of the nonlinear rocket system and decomposition into 4 independent subsystems.
2. **Design of individual MPC controllers** for X, Y, Z, and roll using constrained optimization.
3. **Extension to tracking MPC**, allowing controllers to follow reference points.
4. **Merging linear controllers** into a full nonlinear rocket simulation.
5. **Offset-free tracking** using observer-based correction.
6. **Handling mass loss** during flight (e.g., due to fuel consumption).
7. **Design and evaluation of a full NMPC controller** capable of tracking complex paths like the letters "TVC".

---

## 📊 Key Results

- ✅ Fast settling times (<7s in open-loop, <5s in tracking)
- ✅ Offset-free tracking with disturbance observers
- ✅ Support for time-varying system mass (e.g., fuel consumption)
- ✅ NMPC tracks non-convex trajectories with higher accuracy than linear MPC
- ⚠️ NMPC has higher computational cost (~3x slower than linear MPC)

---

## 🧠 System Design Highlights

- **Subsystem Decomposition**:
  - `sysx`, `sysy`, `sysz`, and `sysroll` treated independently for initial control design.
- **Optimization Formulation**:
  - LQR-based cost functions with hand-tuned Q and R matrices.
  - Input/state constraints enforced through inequality bounds.
- **NMPC Implementation**:
  - Full-state RK4 discretization
  - Relaxed constraints compared to linear MPC
  - Tuned Q = `diag([30; 30; 30; ...; 100])`, R = `0.001 * I`

---



