# Data Sources and Provenance

## 1. Purpose

This document describes the origin, coverage, processing, and intended use of the datasets used in the Climate–Agriculture Decision Support System.

The project investigates the relationship between climate change and agricultural productivity in Kenya using national-level annual climate, vegetation, agricultural-input, and crop-yield data.

The datasets included in this repository are Kenya-specific research extracts prepared from larger global datasets. The original global datasets remain the property of their respective providers.

---

## 2. Geographic and Temporal Scope

- **Study area:** Kenya
- **Geographic scale:** National
- **Temporal resolution:** Annual
- **Primary modelling period:** 1990–2023
- **Extended climate and crop-trend periods:** Determined by the availability of individual datasets

The full multivariable modelling period is limited to 1990–2023 because pesticide-use data are available only for this period. Longer historical records are used where appropriate for climate and crop-yield trend analysis.

---

## 3. Data Source Summary

| Dataset | Original provider | Coverage used in the project | Main variables | Primary analytical purpose |
|---|---|---:|---|---|
| Rainfall | World Bank Climate Change Knowledge Portal | 1950–2024 | Annual rainfall | Climate trend analysis, feature engineering, machine-learning prediction, and climate scenarios |
| Temperature | World Bank Climate Change Knowledge Portal | 1950–2023 | Annual mean temperature | Warming-trend analysis, temperature anomalies, heat-stress indicators, prediction, and scenario simulation |
| Crop yield | Food and Agriculture Organization of the United Nations, FAOSTAT | 1961–2024 | Crop yield in hectograms per hectare | Target variable for crop-specific modelling and forecasting |
| Pesticide use | Food and Agriculture Organization of the United Nations, FAOSTAT | 1990–2023 | National pesticide use in tonnes | Agricultural-input indicator |
| NDVI-related data | Food and Agriculture Organization of the United Nations / source used in the project notebook | 1984–2026 | NDVI and long-term vegetation indicators | Vegetation-condition analysis and NDVI anomaly construction |

---

## 4. Original Data Platforms

### 4.1 World Bank Climate Change Knowledge Portal

The World Bank Climate Change Knowledge Portal provides historical and projected climate information for countries and regions.

Official portal:

https://climateknowledgeportal.worldbank.org/

Kenya country page:

https://climateknowledgeportal.worldbank.org/country/kenya

The project uses historical rainfall and temperature data extracted for Kenya.

---

### 4.2 FAOSTAT

FAOSTAT is the statistical database of the Food and Agriculture Organization of the United Nations.

Official portal:

https://www.fao.org/faostat/en/#home

The project uses FAOSTAT agricultural data for:

- crop yield;
- pesticide use;
- crop-specific national agricultural records.

Relevant FAOSTAT domains include:

- Production: Crops and Livestock Products;
- Inputs: Pesticides Use;
- associated agricultural and environmental statistical domains.

---

## 5. Kenya-Specific Data Extraction

The original data platforms contain information for many countries and regions.

For this project, the global datasets were filtered to retain only records associated with Kenya.

The general extraction process was:

1. Download the relevant global or country-level dataset from the official source.
2. Identify the geographic field, such as `Area`, `Country`, or equivalent.
3. Filter the dataset to retain Kenya.
4. Select the variables required for the research.
5. Standardize year fields, variable names, and measurement units.
6. Aggregate records to annual national values where required.
7. Merge the processed datasets using year as the common temporal key.

The Kenya-specific files included in this repository are therefore derived research datasets rather than complete copies of the original global databases.

---

## 6. Representative Crops

The study evaluates five representative crops:

| Crop | Agricultural representation |
|---|---|
| Sugar cane | Industrial cash crop with high water demand |
| Potatoes | Staple root and tuber crop important for food security |
| Tomatoes | Vegetable crop representing horticultural production |
| Bananas | Tropical perennial food crop |
| Avocados | High-value export fruit crop |

The selected crops represent different agricultural production systems and allow crop-specific comparison of climate sensitivity, predictive performance, scenario response, future forecasts, and vulnerability.

---

## 7. Data Preparation

### 7.1 Rainfall

Rainfall records were processed to obtain annual national rainfall values.

The processed rainfall variable is used for:

- historical trend analysis;
- rainfall anomaly calculation;
- drought and wet-condition indicators;
- climate-only machine-learning models;
- climate-plus-lag forecasting models;
- climate scenario simulation.

---

### 7.2 Temperature

Temperature records were processed to obtain annual national average temperature values.

The processed temperature variable is used for:

- long-term warming analysis;
- temperature anomaly calculation;
- heat-stress indicators;
- machine-learning prediction;
- climate scenario simulation;
- recursive forecasting.

---

### 7.3 Crop Yield

Crop-yield records were filtered for the five representative crops.

The principal target variable is:

```text
Yield_hg_ha