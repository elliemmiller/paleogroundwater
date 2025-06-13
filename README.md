# Paleo Exfiltration Modeling – Project Files Overview

## 📂 Files

### `SiteMetadata.csv`
Contains site-level metadata:
- `Site`, `Sub-region`, ICE-D short name
- Geographic coordinates (`Longitude`, `Latitude`)
- LGM ice thickness
- Associated publication

### `PaleoExfiltrationAllFigs.ipynb`
Main Jupyter notebook for running splined transects through the hydromechanical model.

Also includes functionality to:
- Plot thickness vs. time for a specified site
- Plot elevation vs. thickness vs. time for the same site
- Export:
  - `max_exfiltration_per_site.csv`
  - `full_exfiltration_timeseries.csv`
- Generate:
  - Exfiltration heatmap figure
  - Site map using BedMap3 and `Antarctic_hydropotential.nc` (from Wilson)
  - Mean exfiltration value map
  - Sampled model outputs at 500-year intervals for GIF animation

### `ANT_iced_sensitivity_BOOSTRAP2.ipynb`
Core notebook for:
- Bootstrapping and generating elevation splines
- Plotting and sampling spline outputs
- Exporting results used in `PaleoExfiltrationAllFigs.ipynb`

### `icedcurrent_v14_EM.xlsx`
Master dataset containing all cosmogenic nuclide data.
Read into `ANT_iced_sensitivity_BOOSTRAP2.ipynb` for spline construction.

### `Exfiltration_AllFigsAR.ipynb`
Original hydromechanical model by Alex.
Used to replicate his results at the same permeability intervals as current model runs.

### `PaleoExfiltrationComplexHistory.ipynb`
Runs the hydromechanical model using retreat–readvance histories from Nichols et al. (2024).

### `GRL Groundwater Supplement`
Supplementary document currently in progress for manuscript submission.

---

## 🎨 Figures

### `methods.afdesign`
Figure outlining the spline construction method.
Intended for inclusion in the supplementary materials.

### `ComplexTimeSeriesFigure.afdesign`
Affinity Designer file for finalizing the complex time series figure from `PaleoExfiltrationComplexHistory.ipynb`.

### `Groundwater Diagram Figure copy.afdesign`
Primary figure for the manuscript introduction.
Visual depiction of groundwater infiltration and exfiltration processes.
