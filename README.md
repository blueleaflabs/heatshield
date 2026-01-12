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

| Domain | Source | Access | Output naming (examples) | URL |
| --- | --- | --- | --- |
| Air quality | AirNow API | API | `airnow_PM25_YYYY-MM-DD.csv`, `airnow_pm25_clean.parquet` | https://www.airnowapi.org/ |
| Air quality | EPA AQS API | API | `aqs_88101_YYYY-MM-DD.csv`, `aqs_pm25_clean.parquet` | https://aqs.epa.gov/aqsweb/documents/data_api.html |
| Temperature/precip | NOAA CDO (GHCND) | API | `ghcnd_{datatype}_YYYY-MM.csv`, `ghcnd_daily_raw_all.csv` | https://www.ncei.noaa.gov/cdo-web/webservices/v2 |
| Temperature/precip | NOAA USCRN | HTTP | `uscrn_2024_hourly_clean.parquet` | https://www.ncei.noaa.gov/pub/data/uscrn/products/hourly02/ |
| Smoke/fire | NOAA HMS | HTTP | `hms_smoke_YYYYMMDD.parquet`, `hms_fire_YYYYMMDD.parquet` | https://www.ospo.noaa.gov/products/land/hms.html |
| HRRR (optional) | NOAA HRRR (AWS) | HTTP | `hrrr_YYYYMMDD_HHz_f00.grib2`, `hrrr_ca_YYYYMMDD_HHz.nc` | https://registry.opendata.aws/noaa-hrrr-pds/ |
| Land cover | NLCD 2024 | Manual | `nlcd_2024_ca_summary.csv`, `nlcd_2024_ca_clip.tif` | https://www.mrlc.gov/data/nlcd-2024-land-cover-conus |
| Vegetation | Sentinel-2 NDVI (GEE) | API | `ndvi_ca_{date_tag}_tile{idx}.tif` | https://developers.google.com/earth-engine/datasets/catalog/COPERNICUS_S2_SR |
| Socioeconomic | ACS 2023 | API | `acs_2023_california_tracts.csv` | https://api.census.gov/data.html |
| Boundaries | TIGER/Line | HTTP | `cb_2023_us_state_20m.zip` | https://www2.census.gov/geo/tiger/GENZ2023/shp/ |

Detailed naming rules and parameters live in `config/config.yaml` under `DATA_SOURCES`.

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
