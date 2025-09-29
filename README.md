MESA Inlist and run_stars_extras file to reproduce the results from Sabhahit et. al (2022) - Mass-loss implementation and temperature evolution of very massive stars (https://arxiv.org/pdf/2205.09125.pdf)

Mass loss from optically-thin winds of classical massive stars (10-50 Msun) is typically taken from Vink et al. (2000, 2001). The mass loss from Vink et al. (2000, 2001) has a shallow dependence on the Eddington parameter. However a steeper scaling of mass loss in proximity to the Eddington limit has been found in Vink et al. (2011). This study implements mass loss scaling from Vink et al. (2011) for very massive stars. The switch from a shallow to steeper scaling occurs at the transition mass loss point as proposed in Vink et al. (2012).

We use two different ways to estimate the transition mass loss point based on the presence or absecne of observed VMS. 

For high metallicity (GAL and LMC-like), the transition point is calibrated using observed Of/WNh stars in the Arches cluster in our own galaxy and the 30 Dor in the LMC. 

However, we do not have observed individual VMS in low metallicity environments (SMC-like or below) to calibrate the transition point. In the absence of such a large sample of VMS, we make use of both the concepts of transition mass loss point from Vink et al. (2012) and hydro-dynamically consistent PoWR atmosphere models to construct the new implementation. For the low Z implementation, see the VMS_paper2 repository and Sabhahit et. al (2023) - Very Massive Stars and Pair-Instability Supernovae: Mass-loss Framework for low Metallicity.

The applicable Z range for the VMS mass loss framework in this study is 0.02 to 0.008 (solar-like to LMC-like). A summary of mass loss used is
1. O stars : Vink et al. (2000, 2001)
2. VMS : Scaling from Vink et al. (2011) and absolute rate fixed by the concept of transition mass loss point from Vink et al (2012) to Arches cluster in the Galaxy and 30 Dor in the LMC

----- Relevant files and what they do -----
MESA version r12115
1. run_iteration.py: python script to run multiple models back to back. 
2. inlist_project and inlist_project_LOGS: for core H burning
3. /src/run_stars_extras.f: run_stars file with the low Z VMS mass loss framework


