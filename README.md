# VMS Mass-Loss Implementation (High Metallicity)

MESA Inlist and run_stars_extras file to reproduce the results from [Sabhahit et al. (2022)](https://ui.adsabs.harvard.edu/abs/2022MNRAS.514.3736S/abstract) - Mass-loss implementation and temperature evolution of very massive stars

**Links:**
- https://arxiv.org/pdf/2205.09125.pdf
- https://academic.oup.com/mnras/article/514/3/3736/6592150
- https://ui.adsabs.harvard.edu/abs/2022MNRAS.514.3736S/abstract

# Overview

Mass loss for classical massive stars (10-50 M☉) with optically-thin winds is typically taken from Vink et al. (2000, 2001), which show a shallow scaling with the Eddington parameter. However, a steeper scaling of mass loss in proximity to the Eddington limit has been found in [Vink et al. (2011)](https://ui.adsabs.harvard.edu/abs/2011A%26A...531A.132V/abstract). This study implements a switch in the mass loss from a shallow to steeper scaling at the transition mass loss point where the single scattering limit is approximately breached as proposed in [Vink & Gräfener (2012)](https://ui.adsabs.harvard.edu/abs/2012ApJ...751L..34V/abstract).

We use two different ways to estimate the transition mass loss point based on the presence or absence of observed VMSs:

**For high metallicity (GAL and LMC-like):** The transition mass-loss rate is obtained using the observed luminosities of the Of/WNh stars in the Arches cluster in our own galaxy and the 30 Dor in the LMC. We use the eta ~ 0.6 to get the transition mass-loss rate from the luminosity.

**For low metallicity (SMC-like or below):** We do not have observed individual VMS in low metallicity environments to get the transition point. In the absence of such a large sample of VMS, we make use of both the concepts of transition mass loss point from [Vink & Gräfener (2012)](https://ui.adsabs.harvard.edu/abs/2012ApJ...751L..34V/abstract) and hydro-dynamically consistent PoWR atmosphere models to construct the new implementation. For the low Z implementation, see the [VMS_paper2 repository](https://github.com/gautham-sabhahit/VMS_paper2) and [Sabhahit et al. (2023)](https://ui.adsabs.harvard.edu/abs/2023MNRAS.524.1529S/abstract) - Very Massive Stars and Pair-Instability Supernovae: Mass-loss Framework for Low Metallicity.

**Applicable metallicity range:** Z = 0.008 to 0.02 (LMC-like to solar-like, 0.4-1.0 Z☉)

### Summary of Mass Loss Used

1. **O stars:** Vink et al. (2000, 2001)
2. **VMS:** Scaling from [Vink et al. (2011)](https://ui.adsabs.harvard.edu/abs/2011A%26A...531A.132V/abstract) and absolute rate fixed by the concept of transition mass loss point from [Vink & Gräfener (2012)](https://ui.adsabs.harvard.edu/abs/2012ApJ...751L..34V/abstract) calibrated to Arches cluster in the Galaxy and 30 Dor in the LMC

## Relevant Files and What They Do

**MESA version:** r12115

1. **`run_iteration.py`**: Python script to run multiple models back to back
2. **`inlist_project`** and **`inlist_project_LOGS`**: MESA inlists for core H burning evolution
3. **`/src/run_star_extras.f`**: run_stars file with the high metallicity VMS mass loss framework implementation

## Usage

Compile the provided `run_star_extras.f` file. Modify `inlist_project` to set initial mass and metallicity parameters. Run single models directly with MESA or use `run_iteration.py` to run multiple models sequentially.

**Grid parameter range:**
- **Mass range:** 10-500 M☉
- **Metallicity range:** Z = 0.008 to 0.02 (LMC-like to solar)
- **Evolutionary phase:** Core hydrogen burning
  
## Citation

If you use this mass loss implementation in your research, please cite:
```bibtex
@ARTICLE{2022MNRAS.514.3736S,
       author = {{Sabhahit}, Gautham N. and {Vink}, Jorick S. and {Higgins}, Erin R. and {Sander}, Andreas A.~C.},
        title = "{Mass-loss implementation and temperature evolution of very massive stars}",
      journal = {\mnras},
     keywords = {stars: evolution, stars: massive, stars: mass-loss, stars: winds, outflows, Astrophysics - Solar and Stellar Astrophysics, Astrophysics - Astrophysics of Galaxies, Astrophysics - High Energy Astrophysical Phenomena},
         year = 2022,
        month = aug,
       volume = {514},
       number = {3},
        pages = {3736-3753},
          doi = {10.1093/mnras/stac1410},
archivePrefix = {arXiv},
       eprint = {2205.09125},
 primaryClass = {astro-ph.SR},
       adsurl = {https://ui.adsabs.harvard.edu/abs/2022MNRAS.514.3736S},
      adsnote = {Provided by the SAO/NASA Astrophysics Data System}
}
