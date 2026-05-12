# FabricSim
A MuJoCo-based deformable object simulator parameterized directly from Kawabata Evaluation System (KES) measurements.

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![Status: Active Development](https://img.shields.io/badge/Status-Active_Development-amber.svg)]()

## 📌 Overview
FabricSim is a physics-calibrated simulation environment built on MuJoCo, designed explicitly for robotic manipulation of deformable objects (textiles). Unlike generic cloth simulators that rely on arbitrary domain randomization, FabricSim parameterizes its physics engine directly from the Kawabata Evaluation System (KES) measurements.

By mapping empirical textile mechanics—such as bending rigidity ($B$), shear stiffness ($G$), and surface friction ($\mu$)—to an anisotropic mass-spring-damper system, FabricSim provides a mathematically rigorous foundation for transferring Deep Reinforcement Learning (RL) policies from Sim2Real.

## 📐 Core Architecture
The simulation relies on an anisotropic mass-spring-damper model where spring constants are dynamically adjusted based on warp and weft orientations extracted from KES literature:

$$m \ddot{x}_i = \sum_{j \in N(i)} \left[ k_s(\theta_{ij}) (|x_i - x_j| - L_0) \hat{n}_{ij} + k_d (\dot{x}_i - \dot{x}_j) \hat{n}_{ij} \right] + m g + f_{\text{contact}}(x_i)$$

Where the anisotropic stiffness is defined as:
$$k_s(\theta) = k_{\text{warp}} \cos^2(\theta) + k_{\text{weft}} \sin^2(\theta)$$

## 🚀 Roadmap & Integration
- **v0.1:** MuJoCo environment setup and gravity validation.
- **v0.2:** KES parameter mapping for Cotton, Polyester, and Denim.
- **v0.3:** Baseline SAC agent deployment for corner-grasping tasks.
- **v1.0:** Sim-to-Real gap validation against real-world dataset trajectories.

## ⚙️ Installation & Usage
*(Setup instructions will be populated as the environment reaches v0.1)*
