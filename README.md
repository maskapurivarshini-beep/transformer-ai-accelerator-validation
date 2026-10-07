# Transformer-Based AI Workload Accelerator Block Validation

An advanced hardware verification suite deployed to validate the numerical accuracy and pipeline integrity of a matrix-multiplication hardware accelerator block (similar to NVIDIA Tensor Core architectures) dedicated to deep learning inferencing workloads.

## 🚀 Key Features & Architectural Highlights
* **Golden Model Co-Simulation:** Integrated a **MATLAB mathematical reference framework** acting as an exact algorithmic golden model to compare RTL outputs.
* **Vector Stress Generation:** Automated an environment injection script feeding over **10 Million randomized floating-point/INT8 vector inputs** across complex matrix pipelines.
* **SVA Verification:** Authored explicit **SystemVerilog Assertions (SVA)** acting as inline structural check-points to trap floating-point rounding errors and pipeline pipeline stalls.
* **Mathematical Precision:** Successfully validated **100% computational accuracy** across extreme mathematical tensor bounds and edge cases.

## 📂 Repository Structure
```text
├── model/              # MATLAB Golden Model reference scripts (.m files)
├── rtl/                # Matrix Multiplication Accelerator Design files
├── scripts/            # Input vector generation and parsing utilities (Python)
└── tb/                 # Testbench Environment
    ├── assertions/     # SystemVerilog Assertions (SVA) tracking design rules
    ├── pipeline_chk/   # Mathematical Reference Pipeline Checker
    └── tb_accelerator.sv # Top-Level verification wrapper
```

## 🛠️ Tools & Prerequisites
* **EDA Simulators:** Synopsys VCS or Siemens Questa
* **Math Core:** MATLAB Engine API for Python / MATLAB installation

## 💻 How to Run Simulations
1. Generate fresh input vectors from the mathematical golden model:
```bash
python scripts/gen_vectors.py --size 1024x1024
```
2. Run the hardware simulation with pipeline assertions active:
```bash
cd tb
vcs -sverilog -f flist.f -R +test_vector_path=../scripts/vectors.txt
```
