# Project 3 — NHTS + NGSIM Visualization and IDM Simulation

## Summary

This folder holds the Project 3 analysis that explores travel behavior using the NHTS household travel survey and vehicle trajectory data from NGSIM. The notebook and supporting scripts generate visualizations of NHTS summary statistics, extract and visualize NGSIM trajectory time-series (leader/follower speeds and headway), and run an Intelligent Driver Model (IDM) simulation to compare simulated follower behavior with observations.

Key goals:

- Create clear visualizations for assignment deliverables
- Allow targeted inspection of individual NGSIM trajectories
- Run a simple IDM simulation and report error metrics (RMSE)

## Contents

- `NHTS.csv` — Household travel survey data used for summary plots
- `NGSIM.csv` — Trajectory-level vehicle data used for time-series and IDM
- `Code Files/CIVE202_SPR26_OETKEN_FINALP3.ipynb` — Main analysis notebook (open and run interactively)
- `Code Files/*.ipynb` — Additional lab/notebook materials

## Requirements

- Python 3.8+ recommended
- Required packages: `pandas`, `numpy`, `matplotlib`, `seaborn`

Install requirements (example):

```bash
python -m pip install pandas numpy matplotlib seaborn
```

## How to run (Notebook)

1. Open the notebook `Code Files/CIVE202_SPR26_OETKEN_FINALP3.ipynb` in Jupyter Notebook, JupyterLab, or VS Code.
2. Initiate a Python environment, run all cells, and proceed to fill out the prompts asked.
3. To run a different IDM, locate the parameter cells at the bottom of the page ( 6) Intelligent Driver Model (IDM) Simulation Study ).  Example assignments you will see in the notebook:

```python
a_max = ____ #Maximum acceleration (m/s^2)
b = ____ #Comfortable deceleration (m/s^2)
delta = ____ #Acceleration exponent
t_headway = ____ #Desired time headway (s)
s0 = ____ #Minimum spacing (m)
v0 = ____ #Desired speed (m/s)
vehicle_length = ____ #Average vehicle length (m)
```

## Code Walkthrough

This notebook implements the full analysis in a sequence of logical steps. Below is a concise explanation of each stage and the key functions or cells you will encounter:

- **Load data**: the notebook reads `NHTS.csv` and `NGSIM.csv` into pandas DataFrames.
- **Prepare NHTS**: a preparation step derives fields used by plots (month/year split, numeric `vehicle_age`).
- **NHTS plots**: three plotting cells create (1) a bar chart of trips by weekday, (2) a histogram of vehicle ages, and (3) a boxplot of vehicle age by census region. These cells call plotting routines that either display inline or save to an `output_dir` when defined.
- **Select NGSIM trajectory**: a parameter cell sets `trajectory_id1` (e.g., `trajectory_id1 = 12`) and the notebook creates a subset `traj = ngsim.loc[ngsim['trajectory_number']==trajectory_id1].copy().sort_values('Time')` for all downstream analyses.
  - This happens twice, to allow comparison between two selected trajectories.
- **NGSIM time-series plots**: the notebook plots leader vs follower speeds over time and a customized dual-axis plot showing space headway and relative speed. These visualize driving behavior for the chosen trajectory.
- **IDM simulation**: the notebook integrates a simple Intelligent Driver Model using parameters shown above (`a_max`, `b`, `delta`, `t_headway`, `s0`, `v0`, `vehicle_length`). It simulates follower position and speed through time, compares the simulation with observed follower data, plots comparisons, and computes RMSE metrics for speed and position.

Where to change behavior:

- Trajectory IDs will be changed using user inputs.
- Adjust IDM parameters in the IDM parameter cell to experiment with different driving behaviors via explanation above.
