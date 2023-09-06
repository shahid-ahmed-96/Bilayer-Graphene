# Bilayer-Graphene

## Reference
**Paper:** Liu, W. et al. "Anisotropic thermal transport in twisted bilayer graphene." Physical Chemistry Chemical Physics 24.36 (2022): 21722-21728.

## Introduction
This project employs non-equilibrium molecular dynamics to estimate thermal conductivity in bilayer graphene. The samples studied consist of AA stacked bilayer-graphene with varying twist angles.

### Tools Used
- **Structure Creation:** Python's ASE
- **Simulation Software:** LAMMPS
- **Visualization:** Python's Matplotlib
- **Data Files:**
  - `.lammps-data`: Structure files (e.g., "bilayer.10.100.250" [10-> twist angle, 100nm sample width, 250nm sample length)
  - `.langevin` files: Record temperature variations
  - `.dat` files: LAMMPS script outputs

## Step 1: Creating Structure Files
- LAMMPS requires orthogonal structures.
- The monolayer graphene's unit cell was created to generate orthogonal supercells.
- Jupyter notebook "bilayer_arm.ipynb" provides the steps for generating LAMMPS-readable data files.
- Files generated are for the armchair configuration. (Similar steps were taken for zig-zag configuration)

## Step 2: Relaxations
- Relaxed bond lengths for Step 1 was obtained using NPT in periodic monolayer graphene (LAMMPS Command-> boundary p p p).
- For bilayer structures NVT relaxation was used as given in the provided script.
- Potential: Optimized Tersoff (intralayer) + LJ (interlayer)

## Step 3: Running the Input Script
- LAMMPS script "input.lmp" reads structure and potential files.
- NVE microcanonical ensemble maintains energy.
- Langevin thermostats create temperature gradients.
- The script generates files, e.g., heat input values and dimensions, for Python post-processing.

## Step 4: Post Processing
- `k_anisotropic.ipynb` performs post-processing.
- Steps can be applied to zig-zag configuration.
- Finally, results for both configurations can be compared.

For detailed insights and analysis, refer to the referenced paper.
