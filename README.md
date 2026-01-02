# heatshield

# HeatShield
HeatShield is my attempt at a data-driven research notebook that predicts and visualizes urban heat and environmental risk for vulnerable communities across California.
It integrates temperature, air quality, wildfire, and smoke data with socioeconomic indicators from the U.S. Census to highlight where climate and equity pressures overlap most strongly.
I consider data from the 2024 season - 6/1/2024 through 10/31/2024

---

## What problem this answers

Environmental hazards are not evenly distributed. HeatShield quantifies *where* environmental exposure and social vulnerability overlap, and produces maps + statistics that can be audited and reproduced. It maps California into 3 km grid cells, linking each grid’s daily environmental exposure to census tract–level vulnerability indicators (income, poverty, elderly population).

---

## Approach (high level)

1) Standardize diverse datasets onto a uniform statewide grid (target resolution ~3 km).  
2) Construct two interpretable composite indices:
   - **SVI (Social Vulnerability Index)** from census-derived indicators (e.g., income, poverty, age).
   - **EEI (Environmental Exposure Index)** from environmental stressors (heat, PM2.5, smoke), normalized to allow comparisons.
3) Identify **double-burden** areas (high SVI × high EEI) and summarize patterns across time.

---

## Data sources (initial build)

- Air quality: AirNow / EPA AQS
- Temperature: NOAA station products (e.g., GHCND / USCRN)
- Smoke: NOAA HMS
- Socioeconomic: ACS + TIGER/Line

(Exact sources, versions, and preprocessing notes should be logged in the notebook and/or a `docs/data_sources.md`.)

---

## Repository layout

- `heatshield.ipynb` — end-to-end analysis notebook  
- `README.md` — project overview (this file)

Recommended additions (high leverage):
- `environment.yml` or `requirements.txt` (exact reproducibility)
- `results/` (generated artifacts; optionally gitignored with a sample subset committed)
- `docs/` (data dictionary + index definitions)

---

## Quickstart

Option A — run locally:
	1.	Create the conda environment (python 3.11):
conda env create -f environment.yml
conda activate heatshield
	2.	Launch Jupyter and open heatshield.ipynb.
	3.	Run cells sequentially. All outputs save under results/.

Option B — view-only:
- Open the notebook directly in GitHub for a readable narrative of the analysis.

---

## Outputs you should expect

- Statewide bivariate maps (SVI × EEI)
- Ranked “double-burden” grid cells / tracts
- Time-window summaries (e.g., smoke-day concentration vs vulnerability)

---

## Roadmap and Future TODO as I get time:

- Formalize index definitions + sensitivity checks
- Add a small “example run” dataset slice for fast validation
- Export a clean `results/` bundle suitable for sharing with external reviewers

---

## License

MIT

---

## Contact

Blue Leaf Labs — https://www.blueleaflabs.org

