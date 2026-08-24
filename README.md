# Aerospace Predictive Maintenance with Machine Learning

Predictive maintenance project focused on estimating the **Remaining Useful Life (RUL)** of turbofan engines using NASA C-MAPSS sensor data and machine-learning models.

## Project Overview

Predictive maintenance aims to anticipate equipment degradation before failure by analyzing operational and sensor data.

In this project, the objective is to estimate the number of operating cycles remaining before a simulated turbofan engine reaches failure.

The project is based on the **NASA C-MAPSS FD001 dataset** and applies a complete machine-learning workflow including exploratory data analysis, preprocessing, feature selection, model training and performance evaluation.

## Dataset

The project uses the **NASA C-MAPSS FD001 dataset**, which contains:

- 100 simulated turbofan engines
- Run-to-failure operating cycles
- 3 operational settings
- 21 sensor measurements

Files used:

```text
data/
├── train_FD001.txt
├── test_FD001.txt
└── RUL_FD001.txt
```

## Machine Learning Workflow

### 1. Exploratory Data Analysis

The sensor data is analyzed to understand degradation trends and identify variables that provide little useful information.

The analysis includes:

- Sensor evolution over operating cycles
- Standard-deviation analysis
- Correlation analysis
- Identification of low-variance sensors

### 2. Remaining Useful Life Generation

For the training dataset, the target variable is calculated as:

```text
RUL = maximum engine cycle - current cycle
```

This represents the estimated number of operating cycles remaining before failure.

### 3. Data Preprocessing

The preprocessing pipeline includes:

- Removal of identifiers and cycle columns from model inputs
- Removal of constant or near-constant sensors
- Feature scaling with `MinMaxScaler`
- Preparation of train and test datasets

Sensors excluded during the analysis:

```text
sensor_1
sensor_5
sensor_10
sensor_16
sensor_18
sensor_19
```

## Models

Two regression approaches were evaluated.

### Linear Regression

Used as a baseline model.

| Metric | Value |
|---|---:|
| RMSE | 32.04 |
| MAE | 25.59 |
| R² | 0.40 |

### Random Forest Regressor

A nonlinear ensemble model using:

```python
n_estimators = 200
random_state = 42
```

| Metric | Value |
|---|---:|
| RMSE | 33.85 |
| MAE | 24.79 |
| R² | 0.33 |

## Model Comparison

| Model | RMSE | MAE | R² |
|---|---:|---:|---:|
| Linear Regression | 32.04 | 25.59 | 0.40 |
| Random Forest | 33.85 | 24.79 | 0.33 |

In this implementation, Linear Regression produced the lower RMSE and higher R², while Random Forest achieved a slightly lower MAE.

The results provide a baseline for future improvements using more advanced degradation models and time-series approaches.

## Technologies

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- Jupyter Notebook

## Repository Structure

```text
aerospace-predictive-maintenance-ai/
├── Maintenance_Prédictive_Aéronautique_par_IA.ipynb
├── README.md
└── data/
    ├── train_FD001.txt
    ├── test_FD001.txt
    └── RUL_FD001.txt
```

## Applications

The same predictive-maintenance principles can be applied to:

- Aircraft propulsion systems
- Industrial turbines
- Rotating machinery
- Smart manufacturing equipment
- Industrial IoT systems

## Possible Improvements

Future work could include:

- Gradient Boosting or XGBoost
- LSTM or other sequence models
- Feature engineering based on degradation trends
- Hyperparameter optimization
- Health-index generation
- Uncertainty estimation for RUL predictions

## Author

**Ahmed EL YAMINI**  
Aeronautical Engineering & Space Technologies