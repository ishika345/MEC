# MEC Hydrogen Production Prediction Using Machine Learning

## 📌 Overview

This project explores the use of **machine learning regression models to predict hydrogen (H₂) production in a Microbial Electrolysis Cell (MEC) system**.

The notebook analyzes the relationship between important MEC operating parameters and hydrogen production, and compares the performance of three machine learning approaches:

* Linear Regression
* Random Forest Regression
* XGBoost Regression

The project also includes exploratory data analysis, correlation analysis, feature importance analysis, and visualization of actual versus predicted hydrogen production.

> **Note:** The current notebook uses a synthetic MEC dataset (`synthetic_mec_data.csv`). Therefore, the model results demonstrate the machine learning workflow and relationships within the synthetic data and should not be interpreted as experimentally validated MEC performance.

---

## 🎯 Objectives

The main objectives of this project are:

1. Analyze MEC operating parameters affecting hydrogen production.
2. Prepare and validate the dataset for machine learning.
3. Split the dataset into training and testing sets.
4. Train multiple regression models.
5. Evaluate model performance using standard regression metrics.
6. Identify important features influencing H₂ production.
7. Analyze correlations between MEC variables.
8. Compare Linear Regression, Random Forest, and XGBoost models visually and numerically.



## ⚙️ Input Features

The models use the following MEC parameters as input features:

| Feature         | Description                                      |
| --------------- | ------------------------------------------------ |
| `Temperature`   | Operating temperature of the MEC                 |
| `pH`            | pH of the system                                 |
| `COD`           | Chemical Oxygen Demand                           |
| `Voltage`       | Applied voltage                                  |
| `Current`       | Electrical current                               |
| `H2_Production` | Target variable representing hydrogen production |

### Target Variable

```text
H2_Production
```

The objective of the regression models is to predict hydrogen production from the five input parameters.



## 📊 Dataset

The project uses:

```text
synthetic_mec_data.csv
```

The dataset contains **500 observations** and the following six variables:

```text
Temperature
pH
COD
Voltage
Current
H2_Production
```

The notebook uses an **80:20 train-test split**:

* Training samples: **400**
* Testing samples: **100**



## 🔬 Methodology

The overall workflow is:

```text
MEC Dataset
     ↓
Data Loading
     ↓
Column Validation
     ↓
Missing Value Handling
     ↓
Exploratory Data Analysis
     ↓
Feature / Target Selection
     ↓
Train-Test Split
     ↓
 ┌───────────────────────────────┐
 │                               │
 ▼                               ▼
Linear Regression        Random Forest Regression
 │                               │
 └───────────────┬───────────────┘
                 │
                 ▼
          XGBoost Regression
                 │
                 ▼
       Model Performance Evaluation
                 │
                 ▼
       Feature Importance Analysis
                 │
                 ▼
       Correlation & Visualization
```



## 🤖 Machine Learning Models

### 1. Linear Regression

Linear Regression is used as the baseline model to determine whether a linear relationship exists between MEC operating parameters and hydrogen production.

The model also provides coefficients that indicate the direction and magnitude of the relationship between each input feature and the predicted H₂ production.



### 2. Random Forest Regression

A Random Forest Regressor is trained using:

```text
n_estimators = 200
random_state = 42
```

Random Forest is useful for capturing nonlinear relationships between MEC operating conditions and hydrogen production.

The notebook also extracts the model's **feature importance values**.



### 3. XGBoost Regression

The project also uses an XGBoost Regressor with:

```text
n_estimators = 100
learning_rate = 0.1
random_state = 42
```

XGBoost is a gradient-boosting approach capable of modeling complex nonlinear relationships.

Feature importance is also extracted from the trained XGBoost model.



## 📏 Model Evaluation

The models are evaluated using four regression metrics:

### Mean Squared Error (MSE)

Measures the average squared difference between actual and predicted values.

Lower MSE indicates better performance.

### Root Mean Squared Error (RMSE)

The square root of MSE.

```text
RMSE = √MSE
```

Lower values indicate predictions closer to the actual values.

### Mean Absolute Error (MAE)

Measures the average absolute difference between actual and predicted values.

Lower MAE indicates better performance.

### R² Score

Measures how well the model explains the variation in the target variable.

A value closer to **1.0** indicates better predictive performance.



## 📈 Results

The notebook produced the following test-set results:

| Model             |  MSE | RMSE |  MAE |   R² |
| ----------------- | ---: | ---: | ---: | ---: |
| Linear Regression | 0.01 | 0.12 | 0.09 | 0.96 |
| Random Forest     | 0.02 | 0.14 | 0.11 | 0.95 |
| XGBoost           | 0.02 | 0.13 | 0.11 | 0.95 |

Based on the current synthetic dataset, **Linear Regression achieved the highest R² score (0.96)** and the lowest MAE and RMSE among the three models.

However, because the dataset is synthetic, these results should be considered a demonstration of the modeling workflow rather than evidence that Linear Regression will outperform the other models on real MEC experimental data.



## 📊 Exploratory Data Analysis

The notebook includes several visual analyses.

### Distribution Analysis

Histograms are generated for:

* Temperature
* pH
* COD
* Voltage
* Current
* H₂ Production

This helps understand the distribution and range of each variable.

### Correlation Heatmap

A correlation matrix is visualized to investigate linear relationships between the MEC parameters and hydrogen production.

The correlation values range from:

```text
-1 → Strong negative correlation
 0 → Little/no linear correlation
+1 → Strong positive correlation
```

### Feature vs H₂ Production

Scatter plots are generated for each input variable against `H2_Production`.

These plots help visually examine potential relationships between individual operating parameters and hydrogen production.

### Box Plots

Box plots are generated for all variables to inspect:

* Median
* Spread
* Distribution
* Potential outliers



## 📌 Feature Importance

The project calculates feature importance for both:

* Random Forest
* XGBoost

This helps identify which MEC operating parameters contribute most strongly to the predictions made by the respective tree-based models.

The notebook visualizes these importance values using bar charts.



## 🛠️ Technologies Used

### Programming Language

* Python

### Libraries

* NumPy
* Pandas
* Matplotlib
* Scikit-learn
* XGBoost

### Machine Learning

* Linear Regression
* Random Forest Regression
* XGBoost Regression

### Environment

* Google Colab
* Jupyter Notebook



## 📁 Project Structure

A recommended GitHub repository structure is:

```text
MEC-Hydrogen-Production/
│
├── README.md
├── Untitled22.ipynb
├── synthetic_mec_data.csv
└── requirements.txt
```

For a cleaner final repository, the notebook can be renamed to something more descriptive:

```text
MEC_H2_Production_ML.ipynb
```

---

## 🚀 How to Run

### 1. Clone the repository

```bash
git clone <your-repository-url>
cd MEC-Hydrogen-Production
```

### 2. Install the required libraries

```bash
pip install numpy pandas matplotlib scikit-learn xgboost
```

Alternatively:

```bash
pip install -r requirements.txt
```

### 3. Open the notebook

The notebook can be opened using:

* Google Colab
* Jupyter Notebook
* JupyterLab
* VS Code

### 4. Run the notebook

Make sure the dataset is located in the same directory as the notebook:

```text
synthetic_mec_data.csv
```

Then execute the notebook cells sequentially.



## 🔮 Future Work

The current project provides a foundation for developing a more realistic MEC hydrogen-production prediction system.

Future improvements could include:

* Using real experimental MEC datasets.
* Increasing the dataset size.
* Incorporating additional operating parameters.
* Performing systematic hyperparameter tuning.
* Applying cross-validation.
* Comparing additional regression algorithms.
* Using explainable AI techniques such as SHAP.
* Developing a physics-informed machine learning model.
* Integrating experimentally measured MEC data.
* Studying model performance under different operating conditions.
* Developing an optimization framework to determine operating conditions for maximizing H₂ production.



## ⚠️ Limitations

The primary limitation of the current implementation is that it relies on a **synthetic dataset**.

Therefore:

* The learned relationships may not represent real MEC behavior.
* Model performance may differ substantially on experimental data.
* High R² values on synthetic data do not guarantee real-world predictive accuracy.
* Experimental validation is required before using the model for actual MEC process optimization.



## 👩‍💻 Project Status

**Current Status:** Machine Learning Modeling and Exploratory Analysis

The current version implements the complete workflow from dataset loading and exploratory analysis through regression modeling, evaluation, feature importance, and visualization.

Future versions can extend the project toward **real-data validation, optimization, and physics-informed machine learning for MEC systems**.



