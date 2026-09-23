# Hybrid-Quantum-Energy-Optimization

[![License: Proprietary](https://img.shields.io/badge/License-All%20Rights%20Reserved-red.svg)](LICENSE)
[![Python 3.10+](https://img.shields.io/badge/python-3.10%2B-blue.svg)](https://www.python.org/)
[![Qiskit](https://img.shields.io/badge/Qiskit-1.x-purple.svg)](https://qiskit.org/)
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/amirkabirian/Hybrid-Quantum-Energy-Optimization/blob/main/notebooks/Hybrid_Quantum_Energy_Optimization_Master.ipynb)

A research-grade hybrid quantum-classical framework designed to optimize heavy industrial energy load scheduling (Steel Arc Furnaces, Petrochemical Compressors, etc.) using the Quantum Approximate Optimization Algorithm (QAOA) coupled with official tariff structures from the Iran Grid Management Company (IGMC).

---

## 🚀 Quick Start / Run in Google Colab

You can run the complete end-to-end pipeline (from data ingestion and QUBO formulation to QAOA execution and cost benchmarking) directly in your browser using Google Colab:

* **[Open Master Notebook in Google Colab](https://colab.research.google.com/github/amirkabirian/Hybrid-Quantum-Energy-Optimization/blob/main/notebooks/Hybrid_Quantum_Energy_Optimization_Master.ipynb)**

---

## 📂 Repository Structure

```text
Hybrid-Quantum-Energy-Optimization/
│
├── data/
│   └── iran_industrial_energy_data.csv   # Official IGMC tariff and peak load structures
│
├── notebooks/
│   └── Hybrid_Quantum_Energy_Optimization_Master.ipynb  # Complete master notebook
│
├── LICENSE                               # Proprietary All Rights Reserved License
└── README.md                             # Project documentation
