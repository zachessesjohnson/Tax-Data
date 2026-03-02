# Tax Data

Various state-level tax revenue data collected, cleaned, and compiled for research purposes.

---

## Table of Contents

1. [Overview](#overview)
2. [Data Inventory](#data-inventory)
3. [Data Sources](#data-sources)
4. [Repository Structure](#repository-structure)
5. [Requirements](#requirements)
6. [Setup](#setup)
7. [Usage](#usage)
8. [Data Dictionary / Metadata](#data-dictionary--metadata)
9. [Reproducibility](#reproducibility)
10. [Citation](#citation)
11. [License](#license)
12. [Contributing](#contributing)
13. [Contact](#contact)

---

## Overview

This repository contains U.S. state-level tax revenue datasets spanning **2010–2022** for all 50 states plus the District of Columbia. The data covers several major tax categories — including property tax, sales tax, income tax, and corporate income tax — as well as license taxes and miscellaneous taxes.

The datasets were collected from public sources, cleaned, and compiled to support research into state fiscal policy, tax structure, and revenue trends.

---

## Data Inventory

| File | Description | States | Years | Rows |
|------|-------------|--------|-------|------|
| `individual_tax_data_by_state.csv` | Per-capita and total tax revenue broken down by major tax category for each state | 50 states + DC | 2010–2022 | 669 |
| `license_misc_taxes_by_state.csv` | License tax and miscellaneous tax revenue for each state | 50 states + DC | 2010–2022 | 669 |

---

## Data Sources

> **Note:** The specific primary source(s) used to compile these datasets should be documented here. Common sources for U.S. state tax revenue data include:

- [U.S. Census Bureau — Annual Survey of State Government Tax Collections](https://www.census.gov/programs-surveys/stc.html)
- [Tax Foundation — State Tax Data](https://taxfoundation.org/data/)
- [National Association of State Budget Officers (NASBO)](https://www.nasbo.org/)

<!-- TODO: Replace the placeholder above with the actual source(s) used. -->

---

## Repository Structure

```
Tax-Data/
├── individual_tax_data_by_state.csv   # State-level individual/total tax revenue by category
├── license_misc_taxes_by_state.csv    # State-level license and miscellaneous tax revenue
├── LICENSE                            # Apache 2.0 license
└── README.md                          # This file
```

---

## Requirements

No special software is required to use the data files — they are plain CSV files and can be opened with any spreadsheet application (e.g., Microsoft Excel, Google Sheets, LibreOffice Calc) or any data analysis tool.

Common tools for programmatic access:

| Language | Suggested library |
|----------|------------------|
| Python   | `pandas`, `csv` (standard library) |
| R        | `readr`, `data.table` |
| Julia    | `CSV.jl`, `DataFrames.jl` |
| Command line | `csvkit`, `miller` |

---

## Setup

1. **Clone the repository:**
   ```bash
   git clone https://github.com/zachessesjohnson/Tax-Data.git
   cd Tax-Data
   ```

2. **Install any optional dependencies** for your preferred analysis tool (see [Requirements](#requirements) above). For example, with Python:
   ```bash
   pip install pandas
   ```

---

## Usage

### Python

```python
import pandas as pd

# Load individual tax data
individual = pd.read_csv("individual_tax_data_by_state.csv")
print(individual.head())

# Load license and miscellaneous tax data
license_misc = pd.read_csv("license_misc_taxes_by_state.csv")
print(license_misc.head())

# Example: Filter to a single state and year range
ca_taxes = individual[individual["state"] == "California"]
print(ca_taxes)
```

### R

```r
library(readr)

# Load individual tax data
individual <- read_csv("individual_tax_data_by_state.csv")
head(individual)

# Load license and miscellaneous tax data
license_misc <- read_csv("license_misc_taxes_by_state.csv")
head(license_misc)

# Example: Filter to a single state
ca_taxes <- individual[individual$state == "California", ]
print(ca_taxes)
```

### Command Line

```bash
# Preview the first few rows
head individual_tax_data_by_state.csv
head license_misc_taxes_by_state.csv

# Count rows
wc -l *.csv
```

---

## Data Dictionary / Metadata

### `individual_tax_data_by_state.csv`

| Column | Type | Description |
|--------|------|-------------|
| `state` | string | State name (50 states + DC) |
| `year` | integer | Tax year (2010–2022) |
| `total_revenue` | currency string | Total state tax revenue |
| `prop_tax` | currency string | Property tax revenue |
| `gen_sales_tax` | currency string | General sales and gross receipts tax revenue |
| `select_sales_tax` | currency string | Selective sales tax revenue (e.g., motor fuel, tobacco, alcohol) |
| `income_tax` | currency string | Individual income tax revenue |
| `net_corp_income_tax` | currency string | Net corporate income tax revenue |
| `gift_death_tax` | currency string | Estate, inheritance, gift, and related tax revenue |
| `unemployment_tax` | currency string | Unemployment insurance tax revenue |

> **Note:** Currency values are expressed as dollar amounts per capita (strings formatted with `$` and commas). Verify units against the original source before analysis; you may need to strip `$` and commas before converting to numeric values.

---

### `license_misc_taxes_by_state.csv`

| Column | Type | Description |
|--------|------|-------------|
| `state` | string | State name (50 states + DC + national aggregate) |
| `year` | integer | Tax year (2010–2022) |
| `license_taxes` | currency string | License tax revenue |
| `misc_tax` | currency string | Miscellaneous tax revenue |

> **Note:** Same currency formatting note as above applies here.

---

## Reproducibility

<!-- TODO: Add specific steps for reproducing the data collection and cleaning process if scripts exist or are added in the future. -->

The raw data files in this repository represent the final, cleaned output. To fully reproduce the dataset:

1. Download the raw data from the sources listed in [Data Sources](#data-sources).
2. Apply cleaning steps including: standardizing state names, handling missing values, and normalizing currency formats.
3. *(Any processing scripts, if available, should be placed in a `scripts/` directory and referenced here.)*

---

## Citation

If you use this data in your research, please cite this repository:

```
zachessesjohnson. (2024). Tax-Data: Various data collected, cleaned, and compiled for research.
GitHub. https://github.com/zachessesjohnson/Tax-Data
```

> **Note:** Update the year above to reflect the version of the data you used.

---

## License

This project is licensed under the **Apache License 2.0**. See the [LICENSE](LICENSE) file for details.

You are free to use, modify, and distribute the data and any derivative works, provided you include the original license and attribution.

---

## Contributing

Contributions are welcome! To propose additions or corrections:

1. Fork the repository.
2. Create a new branch: `git checkout -b feature/your-feature-name`
3. Make your changes and commit: `git commit -m "Add: description of change"`
4. Push to your fork: `git push origin feature/your-feature-name`
5. Open a Pull Request against the `main` branch.

Please ensure any new data files include corresponding documentation updates (data dictionary entries, data sources, etc.).

---

## Contact

**Repository maintainer:** [@zachessesjohnson](https://github.com/zachessesjohnson)

For questions, bug reports, or collaboration inquiries, please [open an issue](https://github.com/zachessesjohnson/Tax-Data/issues) in this repository.
