**Files**

‘SiteMetdata.csv'
  Includes: Site, sub-region, ICE-D short name, longitude, latitude, LGM ice thickness, publication
  
‘PaleoExfiltrationAllFigs.ipynb’
Main file where I am running my splined transects through the hydromechanical model
It also includes cells that:
Create a thickness vs time plot for an individual site that you call
Creates an elevation vs thickness vs time plot for the same individual site
Creates two CSV files: one is ‘max_exfiltration_per_site.csv' and the other is ‘full_exfiltration_timeseries.csv’
Creates the heat map figure I have been working on and tweaking 
Creates the site map I have been working on using BedMap3 and calling in the ‘Antarctic_hydropotential.nc’ file that Wilson gave me 
Plots the mean exfiltration values from each site on a map
Samples the model at 500-year intervals so that you can make a GIF of the model run 

‘ANT_iced_sensitivity_BOOSTRAP2.ipynb’
Main file that is both bootstrapping and creating the splines, as well as plotting and sampling the splines, so that those results can be read into ‘PaleoExfiltrationAllFigs.ipynb’

‘icedcurrent_v14_EM.xlsx
Document that contains all the cosmo data that  ‘ANT_iced_sensitivity_BOOSTRAP2.ipynb’ reads in to create the splines  

‘Exfiltration_AllFigsAR.ipynb’
Alex’s original hydromechanical model code
Currently using this to run his model at the same permeability intervals that I am running my model at

‘PaleoExfiltrationComplexHistory.ipynb’
Another file that runs the hydromechanical model for just retreat-readvance time series from Nichols et al. (2024) 

‘GRL Groundwater Supplement’ 
Supplement document that is in progress 

**Figures**
‘methods.afdesign’
Figure describing how we construct the spline that we are going to move into the supplement 

‘ComplexTimeSeriesFigure.afdesign’
Affinity Design file to clean up the complex time series figure that ‘PaleoExfiltrationComplexHistory.ipynb’ spits out 

‘Groundwater Diagram Figure  copy.afdesign’
The main figure in the introduction describes infiltration and exfiltration visually 
