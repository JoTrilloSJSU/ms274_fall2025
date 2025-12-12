# Comparing TKE and KPP Closure Schemes in San Luis Obispo Bay
## Project Description

In this modeling project I plan to investigate the effect of altering mixing in San Luis Obispo Bay. This will be accomplished through runnning two identical model simulations on MITgcm, changing only the mixing package for each simulation. My aim for this project is to answer the following science question:

_How does using K-profile parameterization (KPP) compare with a turbulent kinetic enrgy scheme (GGL90) on the magnitude of mixing and intensity of stratification across the SLO bay._

To investigate this question, I initially palnned to construct a model spanning the length of SLO Bay and run it for the month of June 2024. This would allow for comparison with observational data collected during the same time period. I would run my model once with KPP and once with GGL90 and compare the outputs. This data would then be compared to observational data. Due to ECCO data being unavailable for the year of 2025, and a longer model run time than expected as a result of the fine resultion, these plans were modified and only model output for the January 2024 will be analyzed.

### Model Setup
For initial conditions, I will use the state of the ECCO Version 5 Model in January of 2017. Similarly, I will construct boundary and external forcing conditions for this model from the ECCO Version 5 model output. 

Bathymetry
* Bathymetry data was sourced from ....

Grid Resolution
*

Temporal Resulion
* deltaT: 10 seconds

### Analysis
To analyze the results, I will create a timeseries of the buoyancy frequency, eddy viscosity, and temperature in SLO bay for both a sampling point used in collected in situ data, and averages for the entire grid. Additionally, I will compare the response of these variables with wind stress in order to compare the two models responses to external forcing through time. For visualization, I will create a movie of temperature differences between the model with wind and the model without wind.

## Reproducing Model Results

The following steps outline how to construct the model files, configure and run the model, and assess the model results.

### Step 1: Create the Model Files

Several input files need to be created to run the model. Generate the following list of files using the notebooks indicated in paratheses:

* Model Grid (notebooks/Creating the Model Grid.ipynb)
* Bathymetry (notebooks/Creating the Bathymetry.ipynb)
* Initial Conditions (notebooks/Creating the Initial Conditions.ipynb)
* External Forcing Conditions (notebooks/Creating the External Forcing Conditions.ipynb)
* Boundary Conditions (notebooks/Creating the Boundary Conditions.ipynb)
* The model files should be placed into the  input directory.
  
### Step 2: Add files to the computing cluster

Once the input files have been created, the model files can be transferred to the computing cluster. Begin by cloning a copy of MITgcm into your scratch directory and make a folder for the configuration. I made two directories, one for the KPP run and onther for the TKE(GGL90) run e.g.

`mkdir MITgcm/configurations/slo_mixing_kpp`
`mkdir MITgcm/configurations/slo_mixing_tke`

Then, use the scp command to send the corresponding code, input, and namelist directories to each configuration directory (two separate folder should be provided for this under "GGL90_model_files" and "KPP_model_files".

### Step 3: Compile the model

Once all of the files are on the computing cluster, the model can be compiled. Make a build directory in the configuration directory for each directory and run the following lines:

`../../../tools/genmake2 -of ../../../tools/build_options/darwin_amd64_gfortran -mods ../code -mpi
make depend
make`

### Step 4.1: Run the model with KPP mixing scheme

After the compilation is complete, run the model model using the KPP mixing scheme. (The order in which each model is ran is optional, and running the TKE model first would not affect the outcome of th experiment) Move to the run directory, link everything from input and code, and the submit the job script:

`sbatch ms27405.slm`
### Step 4.2: Run the model with TKE mixing scheme

Next, run the model using the TKE mixing scheme to complete the experiment. Then, submit the job script again to rerun the model. This run can be done simultaneously with the KPP run.

### Step 5: Analyze the Results

There are two notebooks provided for analysis:

_Analyzing Model Results_

This notebook serves as an initial assessment of mixing and stratification in SLO Bay. Eddy viscosity is used to quantify mixing while temperature is used to visualize stratification.

This notebook is divided into two main parts:

1. Averaged time series for the total analysed grid area

  * Mean eddy viscosity and temperature for the surface
  * Mean eddy viscosity and temperature for a transect
2. Movie creation

  * Eddy viscosity and temperature for the surface
  * Eddy viscosity and temperature for a transect
First, import packages to re-create and visualize the model fields here:

_Answering the Science Question_

This notebooks provided some analysis plot to address the science question posed above.
