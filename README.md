# Project 3 — NHTS + NGSIM Visualization and IDM Simulation

## Summary

This project analyzes transportation behavior using two major datasets provided by the Federal Highway Administration (FHWA):

- **NHTS (National Household Travel Survey)** — provides insight into travel behavior and usage trends
- **NGSIM (Next Generation Simulation)** — provides high-resolution vehicle trajectory data for analyzing driving behavior

The objective of this project is to create clear visualizations of transportation trends and perform a simulation study using the Intelligent Driver Model (IDM) to compare observed and simulated vehicle-following behavior.

This work supports visualization and simulation tasks commonly requested for transportation planning and analysis.

---

## Repository Contents

- `NHTS.csv` — Travel survey dataset used for summary visualizations
- `NGSIM.csv` — Vehicle trajectory dataset used for time-series analysis and IDM simulation
- `Code Files/CIVE202_SPR26_OETKEN_FINALP3.ipynb` — **Main notebook (run this file)**
- Miscellaneous supporting lab materials (not required for execution)

---

## Requirements

- Python 3.8+
- Required libraries:
  - `pandas`
  - `numpy`
  - `matplotlib`
  - `seaborn`

Install dependencies:

```bash
python -m pip install pandas numpy matplotlib seaborn
```

## How to Run (Step-by-Step)

1. Open the main notebook: `Code Files/CIVE202_SPR26_OETKEN_FINALP3.ipynb`.
2. Ensure the following files are in the working directory: `NHTS.csv` and `NGSIM.csv`.
3. Start a Python kernel and run cells sequentially from top to bottom.
4. When prompted, enter the requested NGSIM trajectory IDs (examples given below).
5. Continue running the remaining cells to generate all visualizations and complete the IDM simulation study.

Example trajectory IDs used in the report analysis:

```python
trajectory_id1 = 12
trajectory_id2 = 13
trajectory_id3 = 13
trajectory_id4 = 13
```

---

## Sequential User Inputs (Required)

The notebook requires two sets of user-defined inputs.

1. Trajectory Selection

```python
trajectory_id1 = ____
trajectory_id2 = ____
trajectory_id3 = ____
trajectory_id4 = ____
```

These values determine which vehicle trajectories are analyzed:
Trajectory IDs 1 and 2 are used to compare leader-follower dynamics and car-following behaviors, and IDs 3 and 4 are then used for the time-series plots and the IDM simulation, respectively.

1. IDM Parameters

Located in the IDM simulation section of the notebook:

```python
a_max = ____          # Maximum acceleration (m/s^2)
b = ____              # Comfortable deceleration (m/s^2)
delta = ____          # Acceleration exponent
t_headway = ____      # Desired time headway (s)
s0 = ____             # Minimum spacing (m)
v0 = ____             # Desired speed (m/s)
vehicle_length = ____ # Average vehicle length (m)
```

These parameters define the simulated driver behavior and directly impact IDM accuracy. The notebook includes sensible defaults which are used and analyzed in the report:

```python
a_max = 1.2
b = 1.8
delta = 4
t_headway = 1.5
s0 = 2.0
v0 = 30.0
vehicle_length = 5.0
```

---

## Outputs Generated

### NHTS Visualizations

- Bar chart — Trips by weekday
- Histogram — Distribution of vehicle age
- Boxplot — Vehicle age by census region

### NGSIM Time-Series Analysis

- Leader vs follower speed over time
- Space headway and relative speed (dual-axis plot)

### IDM Simulation Results

- Simulated vs observed follower speed
- Simulated vs observed vehicle position
- RMSE (Root Mean Square Error) for speed and position

---

## Code Workflow

The notebook executes the following sequence:

1. Load datasets (`NHTS.csv`, `NGSIM.csv`).
2. Clean and prepare NHTS variables and derived fields.
3. Generate required NHTS visualizations (bar, histogram, boxplot).
4. Select two trajectories from the NGSIM dataset and create subsets for each.
5. Generate time-series plots for driving behavior for each selected trajectory.
6. Apply the Intelligent Driver Model (IDM) to the follower vehicle for each trajectory.
7. Compare simulated vs observed results and compute RMSE error metrics.

Run the notebook top-to-bottom, once prompted, set `trajectory_id` values and, if desired, change the IDM parameters to reproduce all figures and metrics.

---

### Note on plotting and saving figures

- By default, the notebook displays figures inline using `plt.show()`.
  - There is no saved output of plots created within the notebook.

---
