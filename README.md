# Antarctic Ice Thinning and Subglacial Groundwater Dynamics Since the Last Glacial Maximum

This repository contains the Python workflows used to reconstruct Antarctic ice-thinning histories from cosmogenic-nuclide exposure ages and model the resulting subglacial groundwater response over the past 20,000 years.

The code accompanies the thesis:

**Antarctic Ice Thinning and Subglacial Groundwater Dynamics Since the Last Glacial Maximum**  
Ellie M. Miller, Colorado School of Mines, 2026

The workflows include cosmogenic-nuclide data processing, Bayesian ice-thickness reconstruction, sensitivity testing, regional thinning-rate calculations, hydropotential mapping, paleo-groundwater modeling, and numerical model validation.

## Archived version and data

A version-tagged snapshot of the code and associated materials corresponding to the analyses presented in the thesis is archived on Zenodo:

**DOI:** https://doi.org/10.5281/zenodo.21865418

Please cite the archived Zenodo version when using or adapting the code associated with the thesis.

---

## Repository contents

### A.3.1 Bayesian Penalized-Spline Reconstruction of Antarctic Ice-Thinning Histories

**Notebook:** `BayesianSplineandSensitivity...ipynb`

Reconstructs continuous ice-thickness and thinning-rate histories from cosmogenic-nuclide age-elevation data using a bootstrapped Bayesian penalized-spline approach.

The workflow:

- loads and cleans site-specific age-elevation datasets and associated uncertainties;
- generates bootstrap resamples to characterize reconstruction uncertainty;
- fits B-spline models to reconstruct continuous ice-surface elevation histories;
- calculates thinning rates from the fitted splines;
- evaluates model fit and sensitivity to methodological choices; and
- produces the posterior-mean and percentile thickness histories used in subsequent groundwater modeling.

This workflow corresponds primarily to Section 2.2.3 of the thesis.

---

### A.3.2 Antarctic Drainage Basin Visualization and Selection Tool

**Notebook:** `CallByBasin.ipynb`

Visualizes Antarctic drainage-basin polygons and supports selection and inspection of individual basins.

The notebook plots basin boundaries in a polar stereographic projection, labels drainage basins, and allows selected regions to be extracted for subsequent analyses and figures.

This workflow supports the basin assignments reported in Table A.2.11 and the basin outlines shown in Figure 2.2.

---

### A.3.3 One-Dimensional Hydromechanical Model of Antarctic Subglacial Groundwater Exfiltration

Models time-varying groundwater exfiltration and infiltration driven by reconstructed changes in ice thickness during Antarctic deglaciation.

For each site, reconstructed age-thickness histories are converted to time-varying ice-thickness change and used as forcing in the one-dimensional hydromechanical groundwater model described in Section 2.2.5 of the thesis.

The workflow calculates groundwater-flux histories across five prescribed sediment-permeability scenarios:

- 1×10⁻¹¹ m²
- 1×10⁻¹² m²
- 1×10⁻¹³ m²
- 1×10⁻¹⁴ m²
- 1×10⁻¹⁵ m²

Outputs include site-specific paleo-groundwater flux time series and the datasets summarized in Tables A.2.5–A.2.9.

---

### A.3.4 Extended Groundwater Model for Complex Ice-Thinning Histories

**Notebook:** `PaleoExfiltrationComplexSuperpo...ipynb`

Extends the groundwater model to non-linear and non-monotonic ice-thickness histories using interval superposition.

Rather than representing a site's history with a single mean thinning rate, the model evaluates the contribution of successive loading and unloading intervals to the groundwater-flux history. This allows the model to represent episodic thinning, pauses in thinning, rethickening, groundwater-memory effects, and transitions between exfiltration and infiltration.

This workflow is also used to examine the Kay Peak Ridge retreat-readvance case study described in Section 2.4.2.

---

### A.3.5 Hydropotential Mapping and Site Visualization for Antarctic Subglacial Drainage

**Notebook:** `PaleogroundwaterFigures.ipynb`

Generates site-location and hydropotential visualizations used in the thesis.

The workflow:

- plots sampling sites using Antarctic geospatial datasets;
- calculates subglacial hydropotential from BedMachine v3 surface and bed topography;
- visualizes hydropotential across Antarctica;
- produces regional maps for Queen Maud Land, Northern TAMs, Central TAMs, Southern TAMs, Antarctic Peninsula, Weddell Sea, Marie Byrd Land, and Amundsen Sea;
- supports visualization of modeled paleo-groundwater flux; and
- can generate animations of groundwater-model evolution through time.

This workflow supports Figure 2.2 and related groundwater visualizations.

---

### A.3.6 Hydromechanical Model Validation for Paleo-Groundwater Exfiltration

**Notebook:** `PaleoExfiltrationModelValidation...ipynb`

Validates the numerical implementation of the interval-superposition groundwater model using four idealized loading histories with analytical or independently testable behavior.

The validation suite includes:

1. **Constant-rate thinning benchmark**  
   Compares the numerical implementation with the analytical constant-rate solution used by Robel et al. (2023).

2. **Interval-subdivision consistency**  
   Tests whether the same constant-rate forcing produces the same groundwater response when represented using different numbers of discrete loading intervals.

3. **Retreat-readvance cancellation and memory**  
   Tests the long-time response following equal unloading and reloading and evaluates the expected \(t^{-3/2}\) asymptotic decay after cancellation of the leading-order response.

4. **Fresnel analytical solution**  
   Compares the interval-superposition model with an independent Fresnel-integral solution for continuously varying sinusoidal loading and evaluates numerical convergence as temporal resolution is increased.

Together, these tests verify the implementation used to calculate paleo-groundwater flux from reconstructed ice-thickness histories.

---

### A.3.7 Regional and Site-Level Antarctic Ice-Thinning Rate Calculations

**Notebook:** `RegionalandSiteThinningRates.ipynb`

Calculates the regional and site-level thinning-rate statistics reported in Tables 2.5 and 2.6.

For regional calculations, posterior-mean site histories are averaged within eight Antarctic regions, interpolated onto a regular 500-year grid, differenced to obtain thinning rates, and smoothed using a centered 2.5 kyr moving average.

For site-level calculations, posterior-mean thickness histories evaluated on a two-year grid are converted to finite-difference thinning rates and smoothed using the same 2.5 kyr window.

Outputs include:

- regional minimum, mean, and maximum thinning rates;
- site-level minimum and maximum thinning rates; and
- signed negative minima where the fitted reconstruction contains local intervals of apparent thickening.

Rates are reported in m kyr⁻¹.

---

## Additional analysis notebooks

### `BestTestStats.ipynb`

Summarizes sensitivity-test performance across candidate reconstruction configurations and supports identification of the preferred configuration used for each retained site.

### `DataBreakdownPaleoandModern...ipynb`

Compares modeled paleo-groundwater flux with modern groundwater-flux estimates generated using the same hydromechanical parameterization. This workflow supports the paleo-modern comparisons reported in the thesis, including the summary statistics in Table 2.8.

---

## Model conventions

Positive groundwater flux represents **exfiltration**, or upward groundwater movement toward the ice-bed interface.

Negative groundwater flux represents **infiltration**, or downward groundwater movement into the sediment.

The paleo-groundwater calculations use reconstructed ice-thickness histories spanning 20 ka to present. Because the hydromechanical solution is history dependent, modeled flux at a given time reflects both the current loading or unloading interval and residual contributions from preceding changes in ice thickness.

The analytical model assumes a one-dimensional, vertically homogeneous, fully saturated sediment column with prescribed hydraulic properties. These assumptions and their implications are discussed in detail in the accompanying thesis.

---

## Data availability

Input and output datasets associated with the thesis analyses are archived through Zenodo. The archived code release and links to the associated datasets are available through:

https://doi.org/10.5281/zenodo.21865418

---

## Citation

If you use this repository, please cite the archived Zenodo release:

**Miller, E. M. (2026). Antarctic Ice Thinning and Subglacial Groundwater Dynamics Since the Last Glacial Maximum: Analysis Code and Model Workflows. Zenodo. https://doi.org/10.5281/zenodo.21865418**

Individual datasets and external data products should also be cited according to the references provided in the accompanying thesis and notebook documentation.
