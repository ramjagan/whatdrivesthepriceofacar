# whatdrivesthepriceofacar

What Drives the Price of a Car?
Overview
This project is the submission for Practical Application Assignment 11.1 – What Drives the Price of a Car? in the UC Berkeley / Emeritus ML program. It analyzes a Kaggle used‑car dataset (426K vehicles) to understand which factors most strongly drive used car prices and to build a supervised regression model for a used‑car dealership.

The core deliverable is a Jupyter notebook (prompt_II-2.ipynb) that walks through the full CRISP‑DM lifecycle from business understanding to modeling and recommendations.

Repository structure
prompt_II.ipynb – main notebook with CRISP‑DM analysis and models

data/vehicles.csv (not tracked here; provided via course platform) – raw used‑car data

README.md – project description and usage instructions

Note: Place vehicles.csv in a data/ folder at the repo root or adjust the notebook path accordingly.

Problem statement
A used‑car dealership wants to know what consumers value most in a used car and how to price inventory more accurately. From a data perspective, this is framed as:

A supervised regression problem where the target is the continuous variable price.

Features include vehicle attributes such as year, manufacturer, model, condition, odometer, fuel, transmission, drive, and others.

Business goals:

Identify the key drivers of used‑car price.

Build a model with R² ≥ 0.75 on a held‑out test set and reasonable MAE.

Provide actionable recommendations to the dealership for acquisition and pricing.

Methodology (CRISP‑DM)
Business understanding
Reframed the dealership’s question as a regression task predicting price from vehicle features.

Defined key questions (top price drivers, price ranges by vehicle type/condition, presence of non‑obvious factors).

Set success metrics: R², MAE, and interpretability for business stakeholders.

Data understanding
Loaded vehicles.csv and performed initial EDA:

Shape, schema, data types, summary statistics.

Missing values and duplicate analysis.

Outlier detection for price.

Visualizations:

Price distribution.

Price vs. year (boxplots).

Correlation heatmap for numeric features.

Price vs. odometer scatterplot.

Data preparation
Key preparation steps:

Filtered out invalid or extreme price values and removed duplicates.

Selected a subset of relevant features and engineered vehicle age from year.

Handled missing values (dropping high‑missing columns and imputing remaining numeric/categorical fields).

Encoded categorical variables (label encoding and one‑hot encoding as appropriate).

Scaled numeric features.

Split data into train/test sets (80/20).

Modeling
The notebook trains and evaluates several models:

Baseline Linear Regression

Random Forest Regressor

Gradient Boosting Regressor

For each model, the notebook reports:

Train and test R²

MAE and RMSE

Training time

The Random Forest model achieved the best trade‑off between accuracy and interpretability, meeting the target R² threshold on the test set.

Model diagnostics
Feature importance plot (Random Forest) to rank the most influential variables.

Coefficient table and qualitative interpretation for linear regression.

Predicted vs. actual price scatterplot to visually assess model fit.

5‑fold cross‑validation for key models to check stability and variance of performance.

Key findings
From the modeling and feature importance analysis, the main drivers of used‑car price include:

Vehicle age / year – newer vehicles command substantially higher prices.

Odometer – lower mileage is strongly associated with higher price.

Drive type – certain drive configurations (e.g., 4WD/AWD) tend to increase price.

Fuel type – some fuel types (e.g., gas vs. others) carry pricing premiums.

Model/manufacturer and selected categorical attributes (transmission, condition) also contribute meaningfully.

These findings are communicated in the notebook with plots and narrative geared toward a non‑technical dealership audience.

Recommendations for the dealership
Based on the analysis:

Inventory acquisition

Prioritize newer, low‑mileage vehicles, especially in popular manufacturers and models.

Favor configurations with higher‑value drive and fuel types where local demand supports the premium.

Pricing strategy

Use the trained Random Forest model as a pricing decision‑support tool, providing recommended price ranges for new trade‑ins and auction purchases.

Apply discounts for high‑mileage or older vehicles beyond typical thresholds identified in the data.

Ongoing model improvement

Periodically retrain the model with recent sales data to capture changing market conditions.

Explore additional features (e.g., regional effects, seasonality, more granular condition metrics) to further improve accuracy.

How to run the notebook
Clone the repository:

bash
git clone https://github.com/ramjagan/whatdrivesthepriceofacar.git
cd whatdrivesthepriceofacar
Ensure vehicles.csv is available, for example in data/vehicles.csv.

Create and activate a Python environment (optional but recommended).

Install dependencies (typical stack: pandas, numpy, scikit-learn, matplotlib, seaborn, scipy):

bash
pip install -r requirements.txt
or manually:
pip install pandas numpy scikit-learn matplotlib seaborn scipy

Launch Jupyter:

bash
jupyter notebook
Open prompt_II.ipynb and run all cells in order.

Requirements
Python 3.9+

Libraries:

pandas

numpy

scikit-learn

matplotlib

seaborn

scipy
