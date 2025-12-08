# Combinatorial Optimization-FINAL-PROJECT-README

## Project Overview

This project solves a **Weighted Maximum Coverage Problem** to optimally place security cameras on a road network to maximize coverage of accident hotspots. The problem is solved using two algorithms:
1. **Greedy Algorithm**: A heuristic approach that selects camera locations sequentially
2. **Simulated Annealing**: A metaheuristic optimization algorithm

The implementation uses real street data from JJefferson County KY Street Centerlines and generates visualizations showing the camera placement solutions and coverage progression.
## Prerequisites

### Required Software
- **Python 3.7+**
- **Jupyter Notebook** or **JupyterLab**

### Required Python Packages

Install the following packages using pip:

```bash
pip install geopandas
pip install networkx
pip install matplotlib
pip install shapely
pip install pandas
pip install numpy
pip install imageio
```


## Input Files

### Required Input Files

1. **Jefferson_County_KY_Street_Centerlines.shp** (and associated files)
   - **Location**: Root directory of the project
   - **Description**: Shapefile containing street centerline data for Jefferson County, Kentucky
   - **Required companion files** (must be in same directory):
     - `Jefferson_County_KY_Street_Centerlines.shx` (index file)
     - `Jefferson_County_KY_Street_Centerlines.dbf` (attribute data)
     - `Jefferson_County_KY_Street_Centerlines.prj` (projection information)
     - `Jefferson_County_KY_Street_Centerlines.cpg` (code page)
   - **Format**: ESRI Shapefile
   - **Coordinate System**:

### Input File Structure

The project expects the following directory structure:
```
project_root/
├── CSE620-Final-Picture-Perfect.ipynb
├── Jefferson_County_KY_Street_Centerlines.shp
├── Jefferson_County_KY_Street_Centerlines.shx
├── Jefferson_County_KY_Street_Centerlines.dbf
├── Jefferson_County_KY_Street_Centerlines.prj
├── Jefferson_County_KY_Street_Centerlines.cpg
|── graphs/  (created automatically)
```

## Parameters

### Main Algorithm Parameters

**Cell 4**

1. **NUM_CAMERAS** (default: 10)
   - Description: Number of cameras to place on the road network

2. **COVERAGE_RADIUS** (default: 2000)
   - Description: Coverage radius in meters
   - Note: Each camera covers all hotspots within this radius

### Simulated Annealing Parameters

**Cell 9**

1. **max_iters** (default: 10000)
   - Type: Integer
   - Description: Maximum number of iterations for simulated annealing

2.  **starting_temp** (default: 1000)
     - Description: Initial temperature for simulated annealing
     - Range: Positive number (typically 100-10000)
   
   **alpha** (default: 1.525 for linear method)
     - Description: Cooling rate parameter
     - Range: 
       - Exponential: 0.8-0.99
       - Linear: 0.1-2.0
       - Logarithmic: 1.1-10.0

   **Schedule Paramtetrs** (in 'Schedule() class)
     - Description: Cooling schedule method
     - bool
     - options: "exponential, linear, logarithmic"

3. **stop_temp** (default: 1e-5)
   - Description: Stopping temperature threshold
   - Range: Very small positive number

### Hotspot Generation Parameters

**Cell 2**

1. **num_hotspots** (default: 150)
   - Number of accident hotspots to generate
   
2. **cluster_radius** (default: 200)
   - Radius in meters for clustering hotspots
   
3. **num_clusters** (default: 8)
   - Number of hotspot clusters to create


## Pre-conditions

Before running the notebook, ensure:

1. ✅ All required Python packages are installed (see Prerequisites)
2. ✅ The shapefile `Jefferson_County_KY_Street_Centerlines.shp` and all companion files are in the project root directory
3. ✅ You have write permissions in the project directory (for creating the `graphs/` output folder)
4. ✅ Sufficient disk space (approximately 50-100 MB for output images)
5. ✅ The Jupyter kernel has access to the project directory

## How to Run

### Step 1: Install Dependencies

```bash
pip install geopandas networkx matplotlib shapely pandas numpy imageio
```

### Step 2: Launch Jupyter Notebook

```bash
jupyter notebook
```

Or if using JupyterLab:

```bash
jupyter lab
```

### Step 3: Open the Notebook

1. Navigate to the project directory
2. Open `CSE620-Final-Picture-Perfect.ipynb`

### Step 4: Run All Cells

- `Cell → Run All` from the menu

### Step 5: View Results

All output images and GIFs will be saved in the `graphs/` directory and displayed inline in the notebook.

## Output Files

All outputs are saved in the `graphs/` directory:

### Greedy Algorithm Outputs

1. **greedy_step_1.png** through **greedy_step_5.png**
2. **greedy_final_solution.png**
3. **greedy_coverage_progression.png**
4. **greedy_algorithm.gif**

### Simulated Annealing Outputs

1. **annealing_step_*.png** (multiple files, e.g., annealing_step_1.png, annealing_step_477.png, etc.)
2. **annealing_coverage_progression.png**
3. **annealing_best_coverage_progression.png**
4. **annealing_algorithm.gif**


### General Outputs

1. **hotspots_map.png**
   - Description: Initial visualization of road network with all accident hotspots

### Example Output

```
Greedy Algorithm - Coverage Statistics
============================================================
Hotspot Coverage:
  - Covered Hotspots: 77 / 150
  - Weighted Coverage: 45.50 / 85.89
  - Coverage Percentage: 53.0%

Map Coverage:
  - Area Covered: 125.46 km²
  - Map Coverage Percentage: 5.7%
============================================================
```