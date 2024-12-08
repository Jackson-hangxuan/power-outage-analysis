# power-outage-analysis
Portofolio Analysis report for EECS 398

# Power Outage Exploration Report

## Step 1: Introduction
The dataset analyzes major power outages in the U.S. from 2000 to 2015, focusing on the annual frequency of such outages and trends. The central question is:

**Can we predict the trend in the frequency of major outages over time?**

This question is critical for mitigating the socioeconomic impact of outages caused by natural disasters or operational failures, which disrupt lives and economic activities.

### Dataset Details:
- **Number of Rows:** Varies per state but covers a nationwide dataset over 15 years.
- **Relevant Columns:**
  - `YEAR`: Indicates the year of the outage event.
  - `POSTAL.CODE`: Represents the state affected.
  - `CAUSE.CATEGORY`: Describes the primary cause of the outage (e.g., severe weather, intentional attack).
  - `OUTAGE.START.DATE` and `OUTAGE.RESTORATION.DATE`: Define the time frame of outages.

---


## Step 2: Data Cleaning and Exploratory Data Analysis

### Data Cleaning Steps
Data cleaning was a critical step to ensure the accuracy and reliability of the analysis. Below are the steps taken, explained in reference to the data-generating process, and how they affected the analyses:

### Univariate of Outage Cause in Washington State
<iframe
  src="washington.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

### Bivariate Scatter of Intentional Attack vs Year in Washington State
<iframe
  src="Bivar.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

### Aggregated Table of Intentional Attack vs Year in Washington State
|   YEAR |   Intentional Attack Count |
|-------:|---------------------------:|
|   2011 |                         29 |
|   2012 |                         23 |
|   2013 |                          4 |
|   2014 |                          2 |
|   2015 |                          1 |
|   2016 |                          5 |

## Step 3: Prediction Problem
The prediction problem is a **regression task**, aiming to predict the **annual frequency of major outages**.

- **Response Variable:** `Count` of outages per year.
- **Justification:** Tracking this variable helps observe trends, which is critical for preparing states for resource allocation and disaster mitigation.
- **Metric Used:** Mean Squared Error (MSE) was chosen as it effectively measures error magnitude, providing insight into the predictive accuracy.

---

## Step 4: Model and Features

### Model Description:
- A linear regression model was built to predict trends using the year (`YEAR`) as the feature.

### Feature Types:
- **Quantitative:** `YEAR`
- **Nominal:** `POSTAL.CODE` (used for customized state-level modeling)
- **Ordinal:** Not applicable for this model

### Encodings:
The model used numerical data directly (no categorical encodings were necessary).

### Performance:
- **Baseline Model:**
  - Predictions were overly simplistic, leading to unrealistic projections (e.g., predicting 320 outages annually within 10 years).
  - MSE for baseline model: 3003.17.
- **Limitations:** The baseline model highlights the need for refinement to handle anomalies and provide realistic trend predictions.

---

## Step 5: Refinements and Improvements

### Feature Additions:
- Cause-specific modeling for each state (e.g., focusing on severe weather for Michigan and Texas).
- Filtering out outliers from anomalous years (e.g., 2011 extreme weather).

### Modeling Approach:
- Customized linear models for states with sufficient data.
- Extended predictions for up to 10 years while excluding outlier years to improve accuracy.
- Visualized results with scatter plots and prediction lines to compare model output with historical trends.

### Hyperparameters:
- No hyperparameters were applicable for simple linear regression.
- Preprocessing (state-specific filtering) significantly improved performance.

### Comparison:
- **Baseline Model:** Linear regression with `YEAR` for all states.
- **Final Model:** Refined linear regression considering state-specific causes, leading to better trend alignment and improved predictions.

---

## Conclusion
The refined models demonstrate the importance of addressing data anomalies and regional characteristics in predictive modeling. These insights emphasize actionable strategies for managing power outages, highlighting the value of customized, data-driven decision-making.
