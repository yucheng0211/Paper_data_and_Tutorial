# Paper_data_and_Tutorial

This repository **contains** paper data and tutorials for **"Nano-Focusing by Topology Optimization"**.

## 📁 Repository Structure

| Directory | Description |
|-----------|-------------|
| [Paper_data](Paper_data/) | Simulation results and analysis notebooks |
| [tutorial](tutorial/) | Step-by-step inverse design tutorials |


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

| Folder | Link | Description |
|--------|------|-------------|
| env | [env](env/) | Environment files (`pmp.yaml`) |
| figure_in_paper | [figure_in_paper](Paper_data/figure_in_paper/) | Figures used in paper |
| fom1_caseA | [fom1_caseA](Paper_data/fom1_caseA/) | **FoM1** size 0.8μm (baseline) |
| fom1_caseB | [fom1_caseB](Paper_data/fom1_caseB/) | **FoM1** size 0.9μm |
| fom1_caseC | [fom1_caseC](Paper_data/fom1_caseC/) | **FoM1** size 1.0μm |
| fom2 | [fom2](Paper_data/fom2/) | **FoM2** case |
| fom3 | [fom3](Paper_data/fom3/) | **FoM3** case |
| fom4 | [fom4](Paper_data/fom4/) | **FoM4** case |
| fom5 | [fom5](Paper_data/fom5/) | **FoM5** case (**best**) |
| tutorial | [tutorial](tutorial/) | Simple tutorial examples |

> [!NOTE]
> When running the code in the **Paper_data** directory, please ensure you are using the virtual environment created from the `pmp.yaml` configuration file to guarantee compatibility.

### 💻 Environment Configuration
* **Meep Version**: `1.29.0`
* **MPI Version**: `4.1`

> [!CAUTION]
> **Version Compatibility Warning**: The plotting scripts in this project were developed specifically for Meep `1.29.0`. If you use Meep version `1.30.0` or later, the plotting functions may encounter errors. For users on version 1.30+, please refer to the `tutorial` folder for updated instructions.


