# heatshield
Heatshield Repo
HeatShield

HeatShield is my attempt at a data-driven research notebook that predicts and visualizes urban heat and environmental risk for vulnerable communities across California.
It integrates temperature, air quality, wildfire, and smoke data with socioeconomic indicators from the U.S. Census to highlight where climate and equity pressures overlap most strongly.
I consider data from the 2024 season - 6/1/2024 through 10/31/2024


Overview
The project maps California into 3 km grid cells, linking each grid’s daily environmental exposure to census tract–level vulnerability indicators (income, poverty, elderly population).
The app calculates two composite indices:
	•	SVI – Social Vulnerability Index: higher for tracts with more poverty and elderly residents, lower for higher income.
	•	EEI – Environmental Exposure Index: combines PM₂.₅, maximum temperature, and smoke presence using normalized (z-score) values.

By merging these, HeatShield identifies double-burden communities—places where social vulnerability and environmental stress coincide.

Key Features
	•	Unified data processing
	•	Air quality (AirNow, AQS)
	•	Temperature (GHCND, USCRN)
	•	Fire and smoke (HMS)
	•	Land cover and NDVI
	•	Socioeconomic data (ACS 2023, TIGER/Line 2024)
	•	3 km statewide spatial grid in EPSG 3310
	•	Automated daily aggregation (June–October 2024)
	•	Equity analytics
	•	Temporal burden comparison (how heat and PM₂.₅ accumulate in high- vs low-SVI areas)
	•	Multi-factor clustering to reveal “hotspots” (e.g., High heat + poverty, Frequent smoke + elderly)
	•	Double-burden and bivariate maps linking SVI × EEI

How to run:
	1.	Create the conda environment (python 3.11):
conda env create -f environment.yml
conda activate heatshield
	2.	Launch Jupyter and open heatshield.ipynb.
	3.	Run cells sequentially. All outputs save under results/.

Insights
HeatShield demonstrates that environmental hazards are not distributed equally.
Across California’s 2024 wildfire season:
	•	High-vulnerability areas experienced more smoke days and higher PM₂.₅ on average.
	•	The double-burden cells—top quartile for both SVI and EEI—represent less than 1 % of land but mark the state’s most at-risk communities.

