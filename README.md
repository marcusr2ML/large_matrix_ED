# large_matrix_ED_container
THIS README IS AI-GENERATED. Under **src** and **drivers**, the pdf **documentation** (written by a human) outlines submitting jobs and generating outputs.

A parallelized framework for exact diagonalization (ED) of large matrices using a divide-and-conquer strategy.

This project provides a C++-based infrastructure for efficiently diagonalizing large Hamiltonians or general matrices by splitting the computation across independent blocks and aggregating results. It is designed for HPC environments and integrates with job scheduling systems (e.g., SLURM).

---

## Overview

The core idea behind this project is to scale exact diagonalization beyond small systems by:

- Decomposing large matrix problems into smaller subproblems
- Solving subproblems in parallel
- Reconstructing global spectral information from local solutions
- Supporting HPC batch execution via SLURM job scripts

The repository includes both:
- A **solver backend (C++)**
- A **containerized execution + job management system**

---

## Repository Structure

### `solver-cpp/` (THIS MODULE IS INCLUDED IN A SEPARATE REPO AS OF NOW: solver-cpp_large_ED)
Core C++ implementation of the exact diagonalization engine.

- Implements matrix construction and diagonalization routines
- Handles block decomposition logic
- Core numerical routines for eigenvalue/eigenvector computation
- Designed for performance and scalability

---

### `src/`
High-level source code used to interface with the solver.

- Orchestration logic for ED runs
- Construction of physical or model-specific matrices
- Entry points for simulations

---

### `utils/`
Utility functions and helper modules.

- Linear algebra helpers
- File I/O utilities
- Debugging and logging tools
- Miscellaneous shared components

---

### `drivers/`
Executable drivers and experiment entry points.

- Scripts to launch specific ED tasks
- Example workflows and test cases
- Bridges between input configuration and solver backend

---

### `config/`
Configuration files for simulations and runs.

- System parameters
- Matrix size and decomposition settings
- Runtime options and solver tuning

---

### `slurm_jobs/`
HPC job submission scripts.

- Batch scripts for SLURM scheduler
- Parallel execution configurations
- Resource allocation templates
- Designed for cluster-scale computation

---

### `data/`
Input/output data directory.

- Stored Hamiltonians or matrices
- Simulation outputs (spectra, eigenstates, etc.)
- Intermediate checkpoint files

---

## Features

- Parallel divide-and-conquer diagonalization
- Designed for large-scale matrix problems
- HPC-ready (SLURM integration)
- Modular C++ architecture
- Extensible solver backend for custom models

---

## Current Status

This repository is under active development. The current version includes:

- Initial ED API implementation
- First working parallel decomposition pipeline
- Basic SLURM job integration
- Core solver framework structure

---

## Future Work

- Improved scalability for larger Hilbert spaces
- MPI for portability and scalability
- More robust API layer for model definition
- Automated result stitching and analysis tools
- Expanded benchmarking suite

---

## Usage (basic idea)

Typical workflow:

1. Define system in `config/`
2. Launch job via `slurm_jobs/`
3. Solver executes parallel decomposition via `solver-cpp/`
4. Results stored in `data/`
5. Post-processing via `src/` and `utils/`

---

## Notes

This project is optimized for research-scale computations where brute-force diagonalization becomes infeasible. It is intended for use in high-performance computing environments.

---

## License

(Add your preferred license here)
