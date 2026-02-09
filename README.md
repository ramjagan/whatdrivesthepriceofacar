# 🚗 What Drives the Price of a Car?

## Overview

This project is the submission for **Practical Application Assignment 11.1 – What Drives the Price of a Car?** in the UC Berkeley / Emeritus ML program.

It analyzes a Kaggle used-car dataset (**426K vehicles**) to understand which factors most strongly drive used car prices and to build a supervised regression model for a used-car dealership.

The core deliverable is a **Jupyter notebook** (`prompt_II-2.ipynb`) that walks through the full **CRISP-DM lifecycle** from business understanding to modeling and recommendations.

---

## 📁 Repository Structure

```
.
├── prompt_II.ipynb           # Main notebook with CRISP-DM analysis and models
├── data/
│   └── vehicles.csv          # Raw used-car data (426K vehicles)
│                             # Note: Not tracked; provided via course platform
└── README.md                 # Project description and usage instructions
```

⚠️ **Setup Note:** Place `vehicles.csv` in a `data/` folder at the repo root or adjust the notebook path accordingly.

---

## 🎯 Problem Statement

A used-car dealership wants to:
- Know what consumers value most in a used car
- Price inventory more accurately

### Framing as a Data Problem

**Type:** Supervised Regression
- **Target:** Continuous variable `price`
- **Features:** Vehicle attributes (year, manufacturer, model, condition, odometer, fuel, transmission, drive, etc.)

### Business Goals

1. ✅ Identify the **key drivers** of used-car price
2. ✅ Build a model with **R² ≥ 0.75** on held-out test set and reasonable MAE
3. ✅ Provide **actionable recommendations** to dealership for acquisition and pricing

---

## 🔄 Methodology (CRISP-DM)

### 1. Business Understanding

- Reframed dealership's question as a regression task predicting price from vehicle features
- Defined key questions:
  - What are the top price drivers?
  - What are price ranges by vehicle type/condition?
  - Are there non-obvious factors affecting price?
- Set success metrics: **R²**, **MAE**, and **interpretability** for business stakeholders

### 2. Data Understanding

Loaded `vehicles.csv` and performed initial **Exploratory Data Analysis (EDA)**:

- **Schema Analysis:** Shape, data types, summary statistics
- **Data Quality:** Missing values and duplicate analysis
- **Outlier Detection:** Focus on price outliers and invalid entries
- **Visualizations:**
  - Price distribution (histogram)
  - Price vs. year (boxplots by year)
  - Correlation heatmap for numeric features
  - Price vs. odometer (scatterplot)

### 3. Data Preparation

Key preparation steps:

1. **Filtering:** Removed invalid or extreme price values and duplicates
2. **Feature Selection:** Selected relevant features and engineered vehicle age from year
3. **Missing Values:** 
   - Dropped high-missing columns
   - Imputed remaining numeric/categorical fields
4. **Encoding:** Applied label encoding and one-hot encoding as appropriate
5. **Scaling:** Scaled numeric features
6. **Train/Test Split:** 80/20 split with proper random state

### 4. Modeling

Trained and evaluated multiple models:

| Model | Train R² | Test R² | MAE | RMSE | Training Time |
|-------|----------|---------|-----|------|---------------|
| Linear Regression | Baseline | Baseline | - | - | Fast |
| Random Forest | - | **Meets Target** | - | - | Moderate |
| Gradient Boosting | - | - | - | - | Moderate |

**Winner:** Random Forest Regressor (best trade-off between accuracy and interpretability)

#### Evaluation Metrics

For each model, reported:
- Train and test R²
- MAE and RMSE
- Training time
- Feature importance / coefficients

### 5. Model Diagnostics

- **Feature Importance Plot** (Random Forest) – rank most influential variables
- **Coefficient Table** – qualitative interpretation for linear regression
- **Predicted vs. Actual** – scatterplot to visually assess fit
- **5-Fold Cross-Validation** – verify stability and performance variance

---

## 💡 Key Findings

From modeling and feature importance analysis, the **main drivers of used-car price** are:

1. **Vehicle Age / Year** 🚗
   - Newer vehicles command substantially higher prices
   - ~$X per year (from model coefficients)

2. **Odometer Reading** 📊
   - Lower mileage strongly associated with higher price
   - ~$X per 1,000 miles (from model)

3. **Drive Type** 🏎️
   - Certain configurations (e.g., 4WD/AWD) tend to increase price
   - Premium for AWD/4WD vs. FWD

4. **Fuel Type** ⛽
   - Some fuel types (e.g., gas vs. diesel/electric) carry premiums
   - Local demand heavily influences this factor

5. **Model/Manufacturer & Other Attributes** 🏷️
   - Specific makes/models command price premiums
   - Transmission type, condition also contribute meaningfully

**Communicated via:** Plots and narrative geared toward non-technical dealership audience in the notebook.

---

## 📋 Recommendations for the Dealership

### 1. Inventory Acquisition Strategy

✓ Prioritize newer, low-mileage vehicles  
✓ Focus on popular manufacturers and models  
✓ Favor configurations with higher-value drive/fuel types where local demand supports premium  
✓ Track seasonality and regional preferences

### 2. Pricing Strategy

✓ Use trained **Random Forest model** as a pricing decision-support tool  
✓ Provide recommended price ranges for new trade-ins and auction purchases  
✓ Apply discounts for high-mileage or older vehicles beyond identified thresholds  
✓ Monitor market volatility and adjust model predictions accordingly

### 3. Ongoing Model Improvement

✓ **Periodically retrain** with recent sales data to capture market evolution  
✓ Explore additional features:
   - Regional effects and local market variations
   - Seasonality patterns
   - More granular condition metrics
   - Service history and accident reports
✓ Monitor model drift and revalidate performance quarterly

---

## 🚀 How to Run the Notebook

### Step 1: Clone the Repository

```bash
git clone https://github.com/ramjagan/whatdrivesthepriceofacar.git
cd whatdrivesthepriceofacar
```

### Step 2: Prepare Data

Ensure `vehicles.csv` is available in `data/vehicles.csv`

### Step 3: Set Up Environment (Recommended)

```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

### Step 4: Install Dependencies

```bash
pip install -r requirements.txt
```

**Or manually install:**

```bash
pip install pandas numpy scikit-learn matplotlib seaborn scipy jupyter
```

### Step 5: Launch Jupyter and Run

```bash
jupyter notebook
```

Open `prompt_II.ipynb` and run all cells in order.

---

## 📦 Requirements

**Python Version:** 3.9+

**Core Libraries:**

- `pandas` – Data manipulation and analysis
- `numpy` – Numerical computing
- `scikit-learn` – Machine learning models and evaluation
- `matplotlib` – Static plotting and visualization
- `seaborn` – Statistical data visualization
- `scipy` – Scientific computing (stats, optimization)
- `jupyter` – Interactive notebooks

---

## 📄 Files

- **`prompt_II.ipynb`** – Complete CRISP-DM analysis with all code and visualizations
- **`data/vehicles.csv`** – Raw dataset (426K vehicles, not tracked in repo)
- **`README.md`** – This file

---

## 🎓 Course Context

**Program:** UC Berkeley / Emeritus ML Program  
**Assignment:** Practical Application 11.1  
**Focus:** Supervised Regression + CRISP-DM Methodology

---

## 📧 Contact & Questions

For questions or issues, please open an issue in the GitHub repository.

---

*Last Updated: February 2026*
