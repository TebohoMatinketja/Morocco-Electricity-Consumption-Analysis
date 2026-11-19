# Morocco Electricity Consumption Analysis

## Project Overview

This project explores electricity consumption patterns across three
geographical zones in Morocco using Python. It examines how recorded
consumption varies by zone, time of day, season and selected
environmental measurements.

The analysis was completed as part of a Data Analytics internship
assessment. It focuses on exploratory data analysis (EDA), data
preparation, descriptive statistics, visualisation and the translation
of analytical findings into business insights and recommendations.

> **Interpretation note:** The consumption measurement unit and whether
> each 10-minute reading represents instantaneous demand, average power
> or energy consumed during the interval must be confirmed from the
> original data dictionary or source documentation. Until verified,
> values and sums in this project are described as recorded consumption
> values, not as confirmed kWh or total energy.

## Business Problem

An energy management organisation wants to understand electricity
consumption across three geographical zones. It needs to identify
recurring consumption patterns, compare zones, examine associations
between consumption and environmental conditions, and use historical
observations to support improved energy planning.

The analysis addresses these questions:

1.  What consumption patterns are visible across the three zones?
2.  During which hours and days does consumption tend to be highest and
    lowest?
3.  How does consumption vary across the months and seasons represented
    in the data?
4.  Are temperature, humidity and wind speed associated with
    consumption?
5.  Which zone records the highest and lowest average consumption?
6.  How can historical patterns inform energy planning and operational
    monitoring?

## Dataset

The project uses the following source files:

-   `powerconsumption.csv` --- main electricity consumption dataset.
-   `powerconsumption_datadictionary.csv` --- data dictionary describing
    the dataset fields.

The supplied project brief describes approximately 52,416 observations
recorded at 10-minute intervals during 2017, across three consumption
zones.

The nine fields described in the brief are:

  -----------------------------------------------------------------------
  Field                               Description
  ----------------------------------- -----------------------------------
  `Datetime`                          Date and time of each observation

  `Temperature`                       Recorded temperature

  `Humidity`                          Recorded humidity

  `WindSpeed`                         Recorded wind speed

  `GeneralDiffuseFlows`               Diffuse-flow measurement; confirm
                                      exact physical meaning and unit in
                                      the data dictionary

  `DiffuseFlows`                      Diffuse-flow measurement; confirm
                                      exact physical meaning and unit in
                                      the data dictionary

  `PowerConsumption_Zone1`            Recorded electricity consumption
                                      for Zone 1

  `PowerConsumption_Zone2`            Recorded electricity consumption
                                      for Zone 2

  `PowerConsumption_Zone3`            Recorded electricity consumption
                                      for Zone 3
  -----------------------------------------------------------------------

**Data validation still required before final submission:** confirm the
exact definitions and units of all fields from the supplied data
dictionary; verify the 10-minute timestamp sequence and missing
intervals; and establish how the consumption values should be
interpreted. The analysis period observed in the shared results runs
from `2017-01-01 00:00` to `2017-12-30 23:50`; do not describe this as a
complete calendar year without checking the final date and timestamp
completeness.

## Tools and Libraries

-   Python
-   Jupyter Notebook
-   Pandas
-   NumPy
-   Matplotlib
-   Seaborn
-   Plotly

## Project Workflow

### 1. Data understanding and inspection

-   Loaded the electricity consumption dataset.
-   Examined dataset dimensions, column names and data types.
-   Reviewed the data dictionary.
-   Inspected missing values, duplicate records and timestamp coverage.
-   Converted the timestamp field to a date-time data type.
-   Checked the expected observation frequency.

### 2. Data cleaning and preparation

-   Reviewed missing and duplicate records.
-   Investigated timestamp consistency and unusual values.
-   Prepared date and time attributes for analysis, including year,
    month, day, hour, day of week and date.
-   Retained unusual consumption readings for investigation rather than
    automatically deleting them.

### 3. Exploratory consumption analysis

-   Compared average consumption across the three zones.
-   Examined hourly and seasonal patterns.
-   Compared consumption variability using standard deviation and
    coefficient of variation.
-   Investigated associations between consumption and environmental
    variables.

### 4. Outlier analysis

-   Applied the Interquartile Range (IQR) method to identify unusually
    low or high values by zone.
-   Investigated the timing and distribution of high Zone 3 readings.
-   Compared normal and outlier observations by hour and selected
    weather variables.

### 5. Business interpretation

-   Summarised evidence-based findings.
-   Identified operational implications and opportunities.
-   Developed proposed recommendations and an action plan.

## Key Findings

The following figures are the results reported during the analysis and
should be reconciled against the final, fully executed notebook before
publication.

### Average consumption by zone

  Zone       Average recorded consumption   Share of combined zone values
  -------- ------------------------------ -------------------------------
  Zone 1                        32,344.97                          45.41%
  Zone 2                        21,042.51                          29.54%
  Zone 3                        17,835.41                          25.04%

Zone 1 has the highest average recorded consumption and the largest
share of the combined zone values. Zone 3 has the lowest average.

The percentages represent each zone's share of the combined recorded
values used in the analysis. They should not be interpreted as shares of
verified annual energy until the measurement definition is confirmed.

### Relative consumption variability

  Zone       Coefficient of variation
  -------- --------------------------
  Zone 1                       22.05%
  Zone 2                       24.72%
  Zone 3                       37.13%

Zone 3 has the highest relative variability, indicating that its
readings are more dispersed in relation to its mean than those of the
other zones.

### Zone 3 outlier investigation

The IQR screening reported:

-   Zone 1: 0 outliers.
-   Zone 2: 7 high outliers.
-   Zone 3: 1,191 high outliers.

The 1,191 Zone 3 high outliers represent approximately 2.27% of all
52,416 dataset records.

Reported timing of Zone 3 outliers:

  Month      Number of outliers
  -------- --------------------
  July                      760
  August                    431

Most frequent outlier hours:

  Hour      Number of outliers
  ------- --------------------
  20:00                    317
  21:00                    299
  19:00                    222
  22:00                    217

The findings identify July and August evenings as a priority for further
investigation. IQR outliers are statistically unusual observations; they
are not automatically errors or confirmed operational incidents.

### Normal versus outlier weather comparison

  Variable        Normal observations   Zone 3 outliers
  ------------- --------------------- -----------------
  Temperature                   18.62             27.04
  Humidity                      68.48             58.87
  Wind speed                     1.90              4.59

Outlier observations coincided with higher average temperature and wind
speed and lower average humidity in the reported comparison. These are
descriptive associations and do not demonstrate causation.

### Hourly pattern

The Zone 3 hourly profile showed lower average consumption in the early
morning, with a rise towards the evening. The highest normal hourly
average was around 19:00--20:00. This supports further monitoring of
evening demand.

## Business Recommendations

1.  **Prioritise Zone 1 in demand and capacity planning.** Its higher
    average recorded consumption and contribution make it important for
    routine demand monitoring and distribution-capacity review.
2.  **Investigate Zone 3's high variability and unusual readings.**
    Review relevant meter, network and operational records before
    deciding whether the spikes are genuine demand events or
    data-quality issues.
3.  **Focus investigation on July and August evenings.** Prioritise the
    19:00--22:00 period, particularly 20:00 and 21:00, based on the
    outlier distribution observed in the dataset.
4.  **Use hourly and seasonal patterns in operational planning.** Review
    summer and evening demand patterns when planning monitoring,
    maintenance and capacity assessments.
5.  **Explore weather-informed demand analysis.** Test whether
    environmental variables add predictive value using appropriate
    statistical methods and validated data.
6.  **Extend the analysis with additional years.** Additional
    observations are needed to assess whether the 2017 patterns recur
    and to support more reliable forecasting.

These are proposed actions based on exploratory findings. Their
operational benefits have not been measured in this project.

## Repository Structure

A suggested GitHub repository structure is:

``` text
morocco-electricity-consumption-analysis/
│
├── data/
│   ├── powerconsumption.csv
│   └── powerconsumption_datadictionary.csv
│
├── notebooks/
│   └── morocco_electricity_analysis.ipynb
│
├── reports/
│   ├── analytical_report.pdf
│   ├── business_insights.md
│   └── business_recommendations_action_plan.md
│
├── visualisations/
│   └── [exported charts]
│
├── README.md
└── requirements.txt
```

Update the filenames and folders to match the actual repository. Do not
commit confidential or restricted data. If the dataset licence or
assessment rules do not permit redistribution, document how an
authorised user can obtain the data instead of uploading it.

## Reproducing the Analysis

### 1. Clone the repository

``` bash
git clone <your-repository-url>
cd morocco-electricity-consumption-analysis
```

### 2. Create and activate a virtual environment (optional but recommended)

``` bash
python -m venv .venv
```

Windows:

``` bash
.venv\Scripts\activate
```

macOS/Linux:

``` bash
source .venv/bin/activate
```

### 3. Install dependencies

Create a `requirements.txt` file containing the libraries used by the
notebook, then run:

``` bash
pip install -r requirements.txt
```

A starting dependency list is:

``` text
pandas
numpy
matplotlib
seaborn
plotly
jupyter
notebook
```

If the notebook uses additional packages, add them to this file.

### 4. Add the dataset

Place the authorised source CSV files in the `data/` folder, or update
the notebook's file paths to match your local data location.

### 5. Run the notebook

``` bash
jupyter notebook
```

Open the analysis notebook in the `notebooks/` folder and run the cells
in order.

## Limitations and Further Work

-   The dataset covers 2017 only. It cannot establish long-term or
    year-on-year trends.
-   The observed timestamp range and 10-minute interval completeness
    must be validated.
-   The consumption measurement unit and interval interpretation must be
    confirmed before converting readings into energy totals or reporting
    kWh.
-   The definitions and units of `GeneralDiffuseFlows` and
    `DiffuseFlows` require confirmation from the data dictionary.
-   IQR identifies statistical outliers but does not determine their
    cause.
-   Environmental comparisons are observational and do not prove causal
    relationships.
-   Further correlation, regression and predictive modelling could be
    explored after data definitions, quality and coverage have been
    validated.

## Project Deliverables

The project assessment calls for:

-   Completed Jupyter Notebook (`.ipynb`).
-   Cleaned dataset or reproducible data-preparation steps.
-   Relevant charts and visualisations.
-   Analytical report in PDF format.
-   Business insights and recommendations.
-   This README file explaining the project and how to reproduce the
    analysis.

## Author

**Data Analytics Student**

Project: Morocco Electricity Consumption Analysis\
Track: Data Analytics\
Tools: Python, Pandas, NumPy, Matplotlib, Seaborn and Plotly
