# 🛒 Big Mart Sales Prediction

This repository contains a machine learning pipeline for predicting sales at Big Mart stores using historical data. The notebook demonstrates data preprocessing, feature engineering, model training, and prediction correction.

---

## 📊 Feature Engineering

Several transformations are applied to improve model performance:

- **Categorical Encoding**: Variables like `Item_Fat_Content`, `Item_Type`, `Outlet_Size`, and `Outlet_Location_Type` are encoded using label encoding or one-hot encoding.
- **Feature Transformation**:
  - `Item_Visibility` is log-transformed to reduce skewness.
  - A new feature `Item_Type_Combined` is created by grouping similar item types.
- **Outlet Age**: `Outlet_Years` is derived from the establishment year to represent outlet age.

These engineered features help capture meaningful patterns in the data.

---

## 🧹 Null Value Handling

Missing values are handled as follows:

- **Item_Weight**
  - `Problem`: Some entries in the Item_Weight column are missing.
  - `Solution`:
    For each missing value, the notebook looks up the average weight of items with the same Item_Identifier.
    If no matching identifier is found, it falls back to the overall mean weight.
  - `Rationale`: This preserves item-specific characteristics and avoids introducing bias from global averages.
- **Outlet_Size**
  - `Problem`: The Outlet_Size column has missing values, especially for certain outlet types.
  - `Solution`:
    The mode (most frequent value) of Outlet_Size is computed for each Outlet_Type.
    Missing values are filled using the mode corresponding to their Outlet_Type.
  - `Rationale`: This leverages known relationships between outlet type and size, maintaining consistency in categorical distributions.

This ensures a complete and unbiased dataset for training.

---

## 🤖 Model Training

Multiple regression models are trained and evaluated:

- Linear Regression
- Ridge Regression
- Decision Tree
- Random Forest
- XGBoost

Models are trained on the processed dataset and evaluated using RMSE.

---
