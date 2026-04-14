### `README.md`

# Used Cars Data Preparation for Price Prediction

## Overview

This project cleans and prepares a messy used-car listings dataset for a price prediction task. The raw data contains inconsistent formats, unit strings, missing values, duplicates, and unrealistic prices. The notebook transforms it into a clean, numeric, ML-ready dataset and computes a baseline MAE.

---

## Dataset

Public used-car dataset from GitHub / Kaggle mirror.
**Target variable:** `selling_price`

---

## Tasks Performed

### 1. Data Cleaning

* Removed rows where `selling_price` is missing
* Cleaned unit strings from:

  * `mileage` (kmpl)
  * `engine` (CC)
  * `max_power` (bhp)
* Converted to numeric using `pd.to_numeric(errors='coerce')`
* Filled null values using column median
* Removed unrealistic prices (`999999999` and `< 10000`)
* Dropped duplicate rows

### 2. Feature Encoding

* Label encoded `transmission_type`

  * Manual → 0
  * Automatic → 1
* One-hot encoded:

  * `fuel_type`
  * `seller_type`
* Used `drop_first=True` to avoid dummy variable trap
  Rows of all zeros represent the base category.

### 3. Train/Test Split

* 80% training, 20% testing
* Removed all non-numeric columns before modeling

### 4. Baseline Model

* Predicted mean of training prices for all test rows
* Evaluated using Mean Absolute Error (MAE)

---

## Repository Structure

used-cars-data-prep/

* used_cars_data_prep.ipynb
* README.md

---

## Requirements

pip install pandas numpy scikit-learn jupyter

---

## How to Run

jupyter notebook

Open `used_cars_data_prep.ipynb` and run all cells.

---

## Outcome

* Clean, encoded, ML-ready dataset
* Reproducible preprocessing pipeline
* Baseline MAE benchmark for future regression models
