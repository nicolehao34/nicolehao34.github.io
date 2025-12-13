---
title: "Starshade Station Keeping"
excerpt: "Orbital dynamics simulation for starshade spacecraft alignment<br/><img src='/images/portfolio/starshade-stationkeeping.png'>"
collection: portfolio
date: 2022-08-01
---

## Overview

This project focuses on station keeping for a starshade spacecraft, maintaining precise position and orientation relative to a telescope for exoplanet direct imaging. The work replicates methodologies from "Minimal Differential Lateral Acceleration Configurations for Starshade Stationkeeping" by Jackson Kulik.

## Research Context

Station keeping refers to maintaining a spacecraft's position and orientation relative to a target. For starshade missions, this requires minimizing differential lateral acceleration between the starshade and telescope to ensure precise alignment for scientific observations.

## Key Components

### 1. Orbital Dynamics Simulation

Models the orbital dynamics of the starshade and calculates required adjustments using:

* **Gravitational Force**: Newton's law of gravitation
* **Orbital Perturbations**: J2 perturbation for Earth's oblateness and third-body interactions
* **Control Maneuvers**: Proportional-derivative (PD) control for position maintenance

### 2. Control Algorithm

Implements PD control law for station keeping maneuvers:

* Computes necessary thruster firings to correct deviations
* Optimizes fuel consumption while maintaining alignment
* Continuously monitors position and adjusts in real-time

## Mathematical Framework

The simulation solves equations numerically using Runge-Kutta methods:

* **F = G(m₁m₂)/r²**: Gravitational force
* **J2 Perturbation**: Δa = -3/2 * J₂ * (R²/r⁴) * (1 - 3sin²(φ))
* **PD Control**: F_control = k_p * e + k_d * de/dt

## Achievements

* Accurate simulation of orbital dynamics for station keeping scenarios
* Efficient control algorithm minimizing fuel usage while maintaining precise alignment
* Foundation for understanding station keeping challenges in exoplanet imaging missions

## Acknowledgments

Special thanks to Prof. Dmitry Savransky, Prof. Jackson Kulik, and Dr. Grace Genszler at the Cornell Space Imaging and Optical Systems Lab.

## Links

* [GitHub Repository](https://github.com/nicolehao34/starshade-stationkeeping)
* [arXiv Paper](https://arxiv.org/abs/2105.05898)
* Topics: Applied Mathematics, Simulation Modeling, Orbital Mechanics
