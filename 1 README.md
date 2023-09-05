# Bilayer-Graphene

Reference: Liu, Wenxiang, et al. "Anisotropic thermal transport in twisted bilayer graphene." Physical Chemistry Chemical Physics 24.36 (2022): 21722-21728.


## Introduction:
Utilized non-equilibrium molecular dynamics to estimate thermal conductivity.<br>
Sample is AA stacked bilayer-graphene with different twist angles. <br>
Structure creation: ASE (Python) <br>
Software: LAMMPS  <br>
Visualization: Matplotlib (Python) <br>
.lammps-data are structure files <br>
.langevin files show temperature variation across the sample <br>
.dat files are outputs of the lammps script "input.lmp"

## Step1: Creation of Structure file.
LAMMPS require orthogonal structures. <br>
The primitive cell of monolayer graphene with 2 atoms was modified.<br>  
The unit cell now consists of 4 atoms, and the supercell is orthogonal. <br>
Refer to Jupyter notebook "bilayer_arm.ipynb" to get LAMMPS readable data files.<br>
All files are generated for arm_chair configuration 

## Step2: Relaxations  
Used NPT with periodic boundaries in monolayer graphene to get the relaxed bond lengths (Prior to Step1)<br>
Used these bond lengths for the creation of the bilayer structure files in step1.<br>
In the given script used  NVT for relaxation.<br>
Potential: Optimized Tersoff (intralayer) + LJ (interlayer)

## Step3: Running the input script.
LAMMPS script "input.lmp" reads the structure files and potential file "C.tersoff".<br>
It uses the NVE microcanonical ensemble to maintain energy of the the system.<br>
Langevin thermostats are used for maintaining temperature gradient in the sample. <br>
The script generates a few files such as heat input values, dimensions of samples etc. which acts as input for post processing python file.<br> 

## Step4: Post processing
k_anisotropic.ipynb is the file for post processing <br>
Similar steps can be run for zig-zag configuration. <br>
Finally compare results for both.
