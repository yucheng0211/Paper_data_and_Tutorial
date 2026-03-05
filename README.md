# Paper_data_and_Tutorial

This repository **contains** paper data and tutorials for **"Nano-Focusing by Topology Optimization"**.

## 📁 Repository Structure

| Directory | Description |
|-----------|-------------|
| [Paper_data](Paper_data/) | Simulation results and analysis notebooks |
| [tutorial](tutorial/) | Step-by-step inverse design tutorials |

## 🔬 Research Overview

**Photonic Crystal Cavity Design** using topology optimization:
- Unit cell: `$0.8\,\mu\mathrm{m} \times 0.8\,\mu\mathrm{m}$`
- FoM monitor: `$0.2\,\mu\mathrm{m} \times 0.2\,\mu\mathrm{m}$`
- **Figure of Merit**: `$$\text{FoM} = \frac{1}{N_\text{grid}}\sum |E_y|^2$$`

## 🚀 Quick Start

```bash
# Clone repository
git clone https://github.com/yucheng0211/Paper_data_and_Tutorial.git

cd Paper_data_and_Tutorial

# Create conda environment (default name: pmp)
conda env create -f env/pmp.yaml

# Activate environment
conda activate pmp

# Run caseA simulation
cd Paper_data/fom1_caseA
python casea.py
```
## 📖 Detailed Guides

**Fewer steps**: Click each folder for detailed instructions:

| Case | Link | Description |
|------|------|-------------|
| [env](env/) | Environment files (`pmp.yaml`) |
| [figure_in_paper](Paper_data/figure_in_paper/) | Figures used in paper |
| [fom1_caseA](Paper_data/fom1_caseA/) | **FoM1** size 0.8μm (baseline) |
| [fom1_caseB](Paper_data/fom1_caseB/) | **FoM1** size 0.9μm |
| [fom1_caseC](Paper_data/fom1_caseC/) | **FoM1** size 1.0μm |
| [fom2](Paper_data/fom2/) | **FoM2** case |
| [fom3](Paper_data/fom3/) | **FoM3** case |
| [fom4](Paper_data/fom4/) | **FoM4** case |
| [fom5](Paper_data/fom5/) | **FoM5** case (**best**) |
| [finite_ABpair](Paper_data/finite_ABpair/) | AB pair for Q-factor enhancement |
| [tutorial](tutorial/) | Simple tutorial examples |

