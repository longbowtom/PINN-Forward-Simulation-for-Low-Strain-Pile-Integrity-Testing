# PINN Forward Simulation for Low-Strain Pile Integrity Testing

One-line: Physics-Informed Neural Network (PINN) based forward simulations for low-strain pile integrity testing — a set of Python scripts demonstrating forward-model behavior for different pile defect scenarios.

## What this is
This repository implements forward PINN simulations that model wave propagation along piles under low-strain impact and demonstrate characteristic responses for several common defect types (intact pile and localized defects such as necking, enlargement, segregation, and broken sections). It's intended for researchers and engineers interested in PINN applications to structural health monitoring and non-destructive pile integrity testing.

### Stack
- **Language(s):** Python (primary)
- **Framework / runtime:** plain Python scripts (runs with CPython 3.8+)
- **Notable libraries (typical):** numpy, scipy, matplotlib, and a deep-learning backend (TensorFlow or PyTorch) depending on which PINN implementation you choose

## Repository layout
Top-level scripts (each script implements / demonstrates a case):

- pinn_intact.py        — simulation for an intact pile case
- pinn_broken.py       — simulation demonstrating a broken/discontinuous pile segment
- pinn_necking.py      — simulation of localized reduction in cross-section (necking)
- pinn_enlargement.py  — simulation of localized enlargement (bulb or enlargement)
- pinn_segregation.py  — simulation of material/property segregation along pile

These are single-file examples at the repository root. Each script contains the model definition, physical problem setup, training/optimization loop (PINN forward formulation), and plotting/output code for visualization.

**How it fits together:** Each script defines the physical domain and material/property distribution, constructs a PINN to represent displacement/velocity fields, enforces physics-based residuals and boundary/initial conditions, and runs an optimization to obtain a forward-predicted response (time/space traces). The scripts produce figures and numerical outputs that illustrate the effect of each defect type on the low-strain response.

## Requirements
- Python 3.8 or newer
- Recommended packages (example):
  - numpy
  - scipy
  - matplotlib
  - A DL backend: tensorflow (>=2.0) or torch
  - Optional: jupyter (for interactive exploration)

If this repo includes a requirements.txt in the future, install from it. Otherwise install typical packages manually:
```bash
python -m venv venv
source venv/bin/activate    # or `venv\Scripts\activate` on Windows
pip install numpy scipy matplotlib tensorflow
# or, if using PyTorch:
# pip install numpy scipy matplotlib torch
```

## Quick start — run an example
Each script is standalone. From the repository root:

- Run the intact-pile example:
```bash
python pinn_intact.py
```

- Run the broken-pile example:
```bash
python pinn_broken.py
```

- Run the necking example:
```bash
python pinn_necking.py
```

- Run the enlargement example:
```bash
python pinn_enlargement.py
```

- Run the segregation example:
```bash
python pinn_segregation.py
```

Expected behavior: each script runs the PINN forward solver (training/optimization), prints/logs progress, and saves or displays plots of the simulated signals and/or residuals. Look in the working directory for generated plot files (e.g., .png) or inspect inline figures if running in a Jupyter notebook.

## Example outputs
Typical outputs produced by these scripts:
- Time-history traces of velocity/displacement at top/bottom of the pile
- Space-time fields (wave propagation visualizations)
- Loss and residual convergence plots from PINN training
- Comparison plots between baseline (intact) and defect scenarios

## How to adapt or extend
- Swap DL backend: adapt model code to use TensorFlow or PyTorch layers and optimizers.
- Modify defect geometry/property: edit the block in each script that defines the spatial distribution of stiffness/density to explore other defect shapes and positions.
- Logging & checkpointing: add saving/loading of model weights if you intend to resume long optimizations.

## Development & testing
- Run scripts interactively in a Jupyter notebook to visualize intermediate results.
- Add unit tests that check physics residual computation and simple analytic comparisons (e.g., small-time or small-distance asymptotics).

## Contributing
Contributions are welcome. Suggested changes:
- Add a requirements.txt or environment.yml for reproducible installs.
- Break the monolithic scripts into a small package (e.g., pinn_sim/ with modules for physics, models, training, utils).
- Add example notebooks demonstrating step-by-step use.
Please open issues or PRs with a short description and reproducible example.

## License
Specify a license (e.g., MIT) in a LICENSE file to clarify reuse terms.

## Contact / Citation
If you use this code in published work, please cite or acknowledge the repository author. For questions, open an issue in this repository.
