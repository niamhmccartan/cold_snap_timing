# cold_snap_timing
Timing of a cold snap relative to exposure drives large shifts in disease proliferation.

Niamh McCartan1 (communcating author), Jeremy Piggott1, Sadie DiCarlo1,2, and Pepijn Luijckx1. 

1 School of Natural Sciences, Discipline of Zoology, Trinity College Dublin, Dublin, Ireland.
2 Carleton College, Sayles Hill Campus Center, North College Street, Northfield, MN 55057, USA.

This dataset contains infection prevalence and burden observations collected from Daphnia magna infected with its microsporidian parasite Ordospora colligata at the School of Natural Sciences in Trinity College Dublin during summer 2022. This study looked at the effect of cold snaps, and timing of the cold snap on parasite fitness. Here, a cold snap meant a reduction in baseline temperature (constant mean temperature) at a specific amplitude and duration, occurring either 10-days before exposure, on the day of exposure, or 20-says post exposure. Infection prevalence data included all exposed individuals, while burden data included confirmed infections only. Baseline temperature was a continuous centered variable to reduce issues with collinearity. An orthogonal polynomial (cubic for burden, and quadratic for infection prevalence) was added to account for non-linearity in the response to temperature. Amplitude and duration were ordered factors with two levels each (“-3ºC” and “-6 ºC” for amplitude, “3-days” and “6-days” for duration), both also included the constant treatments with the reference level “0”, this allowed for statistical testing on the two variables both independently and combined. Timing of the cold snap was either before exposure, on the day of exposure, or after exposure, with the constant reference level and no cold snap timing. The packages The package ‘glmmTMB’ was used to model parasite fitness, with confirmatory modelleing carried out with 'brms'. The package ‘emmeans’ was used to compare specific treatments. Data were analyzed using R Studio version 4.1.1. Custom contrast p-values were adjusted for multiple comparisons using the ‘Benjamini-Hochberg’ method.

_________________________________________________


**R scripts for analysis:** 

_CS_Analysis.Rmd_: analysis and graphing for both infection prevalence and burden
_CS_Analysis_glmnet.Rmd: confirmatory old analysis using glmnet to confirm robustness of results (found in supplementals)

-----

**List of datasets used for analysis:**

_CS_Timing.csv_: observations on infection prevalence and burden

```
ID: unique sample number from 1 to 1176
A_Temp: target baseline temperature
Real_Avg: the true temperature per bath read from the HOBO loggers at the end of the experiment
Timing: cold snap timing, either cold snap before, during, after exposure or consant with no cold snap
CS_Temp: target temperature the cold snap reveived
Amplitude: How many degrees the cold snap decreased (“0” constant, “-3” -3 ºC, “-6” -6 ºC)
Duration: Duration of the cold snap (“0” constant, “3” 3-days, “6” 6-days)
Replicate: Replicate number of the treatment
Bath: Location of the individual micrososm (either bath A, B, or C)
Date: Date of death (last day 27/08/2022)
Day: Day of death (starting from day -10 and ending on day 33)
Sex: Sex of the individual 
Infection: Presence (1) or absence (0) of infection 
Spores: Number of spores present if infected, if exposed but uninfected NA entered
Include: Yes if included in analysis, no if excluded from analysis (e.g. before first confirmed infection, any males, or any inconclusive infections) 
Notes: Any important notes given when dissections occurred
Change: Explanation if any changes in the raw data were made
```

_CS_Temp_Logs.xlsx_: raw temperature data per bath per hour, also with overall mean temperature 

```
#: Time point recording ID
Date Time, GMT+00:00: Date and time of time point recording 	
Temp, °C: Temperature recorded
Comment: anything relevant about a temperature recording			
Average Temp: Average temperature only including temperature points ±2 degree
Logger ID: Logger ID used for the specific bath	
```
