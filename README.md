# Overview of Classification+Regression Approach to predict Best Solver and Best Solver Time



### Pipeline Overview

1. **Step 1 — Run inside the PorePy environment**  
   **Input:** Model setup and fracture configuration.  
   **Output:**  
   - Mesh files: `mesh2d_Xfr_id.msh`  
   - Fracture metadata: `mesh_meta_id.json`  
   - Solver log: `solver_times.csv` (convergence, solve time, etc.)  

   **Example:**  
   `.../Data_Large4` contains 4000 meshes, matching fracture files with IDs in `0.4d` format, and one `solver_times.csv`.

---

2. **Step 2 — Create the feature dataset** 
   **Input:**  
   - Mesh files `*.msh`  
   - Fracture metadata `*.json`  
   - Solver log `solver_times.csv`  

   **Output:**  
   - Feature table `mesh_features.csv` combining mesh geometry, fracture stats, and solver outcomes.  

   **Usage example:**
   ```python
   from dataset_builder import MeshFeatureDatasetBuilder

   builder = MeshFeatureDatasetBuilder(
       mesh_dir="D:/ML4pmg/Data_Large4/",
       solver_csv="D:/ML4pmg/Data_Large4/solver_times.csv",
       output_csv="D:/ML4pmg/Data_Large4/mesh_features.csv",
       log_transform=True
   )
   
---

3. **Step 3 – Run `Clf_and_Reg_Combined.ipynb`**  
   - Train models and generate predictions.  
   - Compare results against baseline and clairvoyant approaches.

