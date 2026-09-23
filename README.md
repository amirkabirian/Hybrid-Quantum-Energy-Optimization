# Hybrid-Quantum-Energy-Optimization

![License: All Rights Reserved](https://img.shields.io/badge/License-All_Rights_Reserved-red.svg)
[![Python 3.10+](https://img.shields.io/badge/python-3.10+-blue.svg)](https://www.python.org/downloads/)
[![Qiskit 1.0+](https://img.shields.io/badge/Qiskit-1.0+-purple.svg)](https://qiskit.org/)

## Executive Summary & Industrial Motivation

Industrial energy management faces severe decision-making bottlenecks when scheduling high-power equipment during peak-demand hours. Traditional mathematical programming methods (e.g., MILP) scale exponentially ($O(2^N)$) as the number of machines, operational constraints, and dynamic energy pricing tiers expand.

**Hybrid-Quantum-Energy-Optimization** offers a NISQ-friendly, variational framework that maps industrial energy load scheduling onto a **Quadratic Unconstrained Binary Optimization (QUBO)** formulation. By utilizing the **Quantum Approximate Optimization Algorithm (QAOA)** in a closed-loop hybrid setup, this framework computes near-optimal schedule topologies that minimize operational energy costs while adhering strictly to physical grid constraints and real-world industrial tariff structures.

---

## Data Sources & Benchmark Policy

Tariff profiles, demand-peak tiers, and capacity constraints are benchmarked using official parameters from the **Iran Grid Management Company (IGMC)** and the **Ministry of Energy**, featuring customizable operational presets for heavy metallurgy (steel arc furnaces), petrochemical processing units, and modular automated manufacturing lines.

---

## 📌 Interactive Notebooks (Run in Google Colab)

Execute the entire pipeline sequentially inside free Google Colab environments:

* **01_industrial_qubo_formulation.ipynb**  
  *Models multi-industry presets, Iranian industrial tariff structures, and constructs the QUBO cost matrix Q.*
* **02_qaoa_hybrid_solver.ipynb**  
  *Builds the QAOA ansatz circuit and updates variational parameters via classical optimizers (COBYLA).*
* **03_energy_benchmark_demo.ipynb**  
  *Benchmarks QAOA solution probability against classical heuristics and visualizes energy cost savings.*

---

## Mathematical Formulation

### 1. QUBO Energy Cost Mapping
The industrial energy scheduling objective is mapped into a binary vector $x \in \{0, 1\}^n$, where $x_{i,t} = 1$ denotes machine $i$ operating during time interval $t$:

$$\min_{x \in \{0,1\}^n} H(x) = x^T Q x + c^T x$$

$$\text{where } Q = Q_{\text{tariff}} + \lambda_1 Q_{\text{interlock}} + \lambda_2 Q_{\text{capacity}}$$

Penalties $\lambda_1, \lambda_2 \gg 0$ guarantee that hard physical constraints are preserved in the ground state energy topology.

### 2. Quantum Approximate Optimization Algorithm (QAOA)
The QUBO Hamiltonian $H_C$ is mapped to Pauli-$Z$ operators. The parameterized quantum state $|\boldsymbol{\gamma}, \boldsymbol{\beta}\rangle$ is constructed by applying alternating cost and mixer layers:

$$|\boldsymbol{\gamma}, \boldsymbol{\beta}\rangle = \prod_{k=1}^p e^{-i \beta_k H_B} e^{-i \gamma_k H_C} |+\rangle^{\otimes n}$$
