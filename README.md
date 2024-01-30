MESA Inlist and run_stars_extras file to reproduce the results from Sabhahit et. al (2022) - Mass-loss implementation and temperature evolution of very massive stars (https://arxiv.org/pdf/2205.09125.pdf)

Mass loss for modelling the evolution of classical massive stars (10-50 Msun) is typically taken from Vink et al. (2000, 2001). However a steeper scaling of mass loss in proximity to the Eddington limit has been found in Vink et al. (2011). This study implements mass loss scaling from Vink et al. (2011) for very massive stars.  The applicable Z range for the VMS mass loss framework in this study is 0.02 to 0.008 (solar-like to LMC-like). A summary of mass loss used is
1. O stars : Vink et al. (2000, 2001)
2. VMS : Scaling from Vink et al. (2011) and absolute rate fixed by the concept of transition mass loss point from Vink et al (2012) to Arches cluster in the Galaxy and 30 Dor in the LMC


----- For high-metallicity VMS recipe -----

!! This recipe is only applicable for LMC-like or above. For low metallicity case, see VMS_paper2 repository

----- Relevant files and what they do -----
MESA version r12115
1. run_iteration.py: python script to run multiple models back to back. 
2. inlist_project_H and inlist_project_H_LOGS: for core H burning
3. inlist_project_He and inlist_project_He_LOGS: for core He burning
4. /src/run_stars_extras.f: run_stars file with the low Z VMS mass loss framework

