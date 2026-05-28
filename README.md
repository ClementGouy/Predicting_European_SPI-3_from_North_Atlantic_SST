# Predicting European Drought from North Atlantic SST

ENS M2 WAPE — Research Project (PRP)

Statistical prediction of European drought (SPI-3) using North Atlantic sea surface temperature (SST) as a seasonal predictor.

## Overview

The notebook `main_cl.ipynb` implements the full analysis pipeline:

1. **Data loading** — SPI-3 (Copernicus EDO) and North Atlantic SST (ERA5 or HadISST1)
2. **EOF analysis** — seasonal PCA of SST 
3. **Lagged correlations** — maps and per-region time series
4. **K-means clustering** — spatial clustering of European SPI-3
5. **MCA / CCA** — Maximum Covariance and Canonical Correlation Analysis between SST and SPI-3
6. **Predictive models** — Ridge regression and MLP neural network with block bootstrap significance testing

## Data

Data files are not tracked in this repository due to size (~1.3 GB). Place them in a `data/` folder at the root of the repo.

### SPI-3 (E-OBS, Copernicus EDO)

**File:** `SPI3_monthly_1991-2022_v2.nc`

Download from the [Copernicus European Drought Observatory](https://drought.emergency.copernicus.eu/tumbo/edo/map/).
Select: *SPI E-OBS Short-term (3-month)*, monthly, 1991–2022.

### SST — ERA5 (default)

**File:** `sst_monthly_1940_2025.nc`

Download from the [Copernicus Climate Data Store](https://cds.climate.copernicus.eu/):
*ERA5 monthly averaged data on single levels* → variable: `Sea surface temperature`.

### SST — HadISST1 (alternative but not recommended)

**File:** `SST_1870-2025.nc`

Download from the [Met Office Hadley Centre](https://www.metoffice.gov.uk/hadobs/hadisst/data/download.html).

### Data path

The notebook uses an absolute path. Update `dir_name` in cell 2 to point to your local `data/` folder:

```python
dir_name = "/path/to/your/data/"
```

## Dependencies

```
xarray
numpy
pandas
matplotlib
cartopy
scikit-learn
eofs
xeofs
statsmodels
arch
```

Install with:

```bash
pip install xarray numpy pandas matplotlib cartopy scikit-learn eofs xeofs statsmodels arch
```

## References

- Chevuturi et al. (2025) — methodology reference
- [Hess paper (2017)](hess-21-1397-2017.pdf) — SPI methodology
- [WMO SPI User Guide (2012)](WMO_standardized_precipitation_index_user_guide_en_2012.pdf)
- [SPI Factsheet](factsheet_spi.pdf)
- [Project proposal](PRP_proposal.pdf)
