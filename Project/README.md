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

