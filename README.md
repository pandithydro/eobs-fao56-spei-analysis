# eobs-fao56-spei-analysis

# E-OBS Hydro-Statistical Analysis: FAO-56 PET & SPEI Fitting

This repository features an advanced hydrological workflow for drought analysis at the **Hamerstorf Agricultural Experimental Site** (Germany). The project integrates raw European gridded climate data (E-OBS) with physical modeling of evapotranspiration and a comparative statistical study of drought index parameter estimation.

## Source Information
- **Source:** [E-OBS European Gridded Dataset](https://www.ecad.eu/download/ensembles/download.php)
- **Resolution:** 0.1 degree (~10 km)
- **Input Variables:** 
  - **Land Surface Elevation (m):** Derived from GTOPO30.
  - **Maximum, Mean & Minimum Temperature (°C):** Measured at 2m height.
  - **Relative Humidity (%):** Daily mean relative humidity.
  - **Surface Shortwave Downwelling Radiation (W m⁻²):** Solar radiation flux.
  - **Wind Speed (m s⁻¹):** Measured at 10m height.
  - **Precipitation (mm):** Total daily liquid water equivalent.

    
## Study Site: Hamerstorf
- **Location:** Lower Saxony, Germany
- **Context:** A key site for evaluating hydrological extremes, crop water demand, and the performance of gridded climate products against point-scale agricultural needs.

## Hydrological Modeling (FAO-56)
Reference Evapotranspiration (ET0) was calculated using the full **FAO-56 Penman-Monteith equation**. All variables listed above (excluding pressure) were utilized to satisfy the energy and aerodynamic components of the model:

1.  **Energy Balance:** Utilizes Surface Shortwave Radiation and Temperature to determine net radiation.
2.  **Aerodynamic Transport:** Utilizes Wind Speed and Relative Humidity to determine the vapor pressure deficit and atmospheric moisture transport.
3.  **Elevation Adjustment:** Land surface elevation is used to adjust psychrometric constants and atmospheric pressure for the site-specific altitude.


## Statistical Analysis: SPEI-6 (September)
The analysis focuses on the 6-month SPEI ending in September, capturing the cumulative water balance ($P - ET_0$) across the primary German growing season (April–September).

### Parameter Estimation Comparison
A core feature of this project is the robust comparison of distribution fitting for the September water balance:
1.  **Distributions:** Log-Logistic (Standard SPEI) vs. Generalized Extreme Value (GEV).
2.  **Estimation Methods:**
    - **Maximum Likelihood Estimation (MLE):** Standard frequentist optimization.
    - **Probability Weighted Moments (PWM):** Known for superior performance in hydrological extremes and smaller samples.

## Workflow Summary
1.  **Data Cleaning:** Automated identification and imputation of missing E-OBS values.
2.  **Downscaling:** Bilinear interpolation from the 0.1° grid to the Hamerstorf coordinates.
3.  **ET0 Calculation:** Implementation of the FAO-56 Penman-Monteith algorithm using the multi-variable input suite.
4.  **Fitting & Comparison:** Evaluation of MLE vs. PWM for drought tail-behavior stability.
