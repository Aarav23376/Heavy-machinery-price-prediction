# Heavy Machinery Price Prediction

A machine learning project to predict the transaction prices of heavy machinery using historical transaction data. The project covers exploratory data analysis, data preprocessing, regression model development, and CatBoost hyperparameter tuning.

## Project Overview

Predicting the transaction value of used heavy machinery is a regression problem influenced by factors such as manufacturing year, operating hours, machine specifications, utilization, and transaction history.

This project explores historical machinery transaction data to identify useful patterns and build regression models for price prediction. Multiple regression approaches are evaluated, with a focus on **CatBoost's native categorical feature handling** and hyperparameter tuning.

## Objectives

- Explore historical heavy machinery transaction data through exploratory data analysis (EDA).
- Examine relationships between machine characteristics and transaction prices.
- Investigate missing values and anomalous data.
- Prepare numerical and categorical features for machine learning.
- Train and evaluate multiple regression models.
- Use CatBoost to handle categorical features natively.
- Tune model hyperparameters and evaluate the selected model using RMSLE.

## Tech Stack

- **Language:** Python
- **Data analysis:** Pandas, NumPy
- **Visualization:** Matplotlib, Seaborn
- **Machine learning:** Scikit-learn
- **Gradient boosting:** CatBoost
- **Development environment:** Jupyter Notebook

## Project Workflow

### 1. Exploratory Data Analysis

The dataset was explored to understand its structure, feature distributions, missing values, and relationships with the target variable.

The analysis included:

- Numerical feature distributions, including manufacturing year and operating hours.
- Target value distribution.
- Relationships between numerical features and transaction prices.
- Categorical feature distributions, including drivetrain type and utilization tier.
- Transaction-year trends.
- Price variation across machine base classes.
- Correlation analysis.

### 2. Data Preprocessing

The preprocessing stage focused on preparing the data for regression modelling.

Key considerations included:

- Analysing missing values.
- Investigating anomalous values in manufacturing year.
- Reviewing columns and feature relevance.
- Separating input features from the target variable.
- Preparing numerical and categorical features for model training.
- Maintaining consistent preprocessing between training and validation data.

### 3. Regression Model Development

Multiple regression models were explored and evaluated to compare their predictive performance.

The modelling workflow progressed from initial regression approaches to gradient-boosting methods, with validation metrics used to assess model performance.

### 4. CatBoost and Native Categorical Feature Handling

CatBoost was used as a key modelling approach because it supports categorical features directly.

Rather than requiring every categorical variable to be manually one-hot encoded, CatBoost can process categorical features through its native categorical-feature mechanism.

This was particularly relevant for a dataset containing categorical variables with many distinct values.

### 5. Hyperparameter Tuning

`RandomizedSearchCV` was used to explore selected CatBoost hyperparameters across multiple cross-validation folds.

The search considered parameters such as:

- Number of boosting iterations
- Tree depth
- Learning rate
- L2 regularization

The selected configuration was then evaluated on the held-out validation set using RMSLE.

## Results

| Metric | Result |
|---|---:|
| Model | CatBoost Regressor |
| Evaluation metric | RMSLE |
| Tuned validation RMSLE | **0.2061** |

The tuned CatBoost model achieved a validation RMSLE of **0.2061**.

RMSLE, or Root Mean Squared Logarithmic Error, evaluates prediction errors on a logarithmic scale. It is useful for price-prediction tasks where relative differences between actual and predicted values matter.

The reported score is the result on the project's validation data. It should not be interpreted as a guaranteed score on unseen data or as a leaderboard result.

## Repository Structure

The repository is expected to follow this structure:

```text
heavy-machinery-price-prediction/
├── Data/
│   ├── train.csv
│   ├── test.csv
│   └── metadata.csv
├── heavy_machinery_price_prediction.ipynb
├── .gitignore
└── README.md
```

The `Data/` directory contains the input CSV files used by the notebook. The notebook contains the project's EDA, preprocessing, model development, evaluation, and CatBoost tuning workflow.


## Getting Started

### Prerequisites

- Python 3.10 or newer
- Jupyter Notebook or JupyterLab
- The project CSV files

### 1. Clone the repository

```bash
git clone https://github.com/Aarav23376/Heavy-machinery-price-prediction
cd heavy-machinery-price-prediction
```



### 2. Create a virtual environment

```bash
python -m venv .venv
```

Activate it on Windows:

```bash
.venv\Scripts\activate
```

On macOS or Linux:

```bash
source .venv/bin/activate
```

### 3. Install dependencies

```bash
pip install pandas numpy matplotlib seaborn scikit-learn catboost jupyter
```

### 4. Place the dataset files

Ensure the required files are available at the paths expected by the notebook:

```text
Data/train.csv
Data/test.csv
Data/metadata.csv
```

The notebook assumes these relative paths. If you use a different directory structure, update the corresponding file paths in the data-loading cells.

### 5. Launch the notebook

```bash
jupyter notebook
```

Open `heavy_machinery_price_prediction.ipynb` and execute the cells in order.

**Note:** Model training and hyperparameter tuning can take several minutes or longer depending on dataset size, hardware, and configuration. GPU support depends on the installed CatBoost build and compatible hardware.

## Limitations

- **Validation performance:** The reported RMSLE of 0.2061 reflects the validation setup used in this project. Performance may differ on new data.
- **Data quality:** Missing values and anomalous records can affect model behaviour.
- **Feature engineering:** Additional domain-informed features may improve the modelling approach, but their impact has not been established here.
- **Generalization:** Historical relationships may not fully represent future machinery transactions or changing market conditions.
- **Reproducibility:** Exact results may depend on library versions, random seeds, data files, and hardware configuration.
- **Dataset availability:** Users must have access to the original dataset files to reproduce the workflow.

## Future Improvements

Potential extensions include:

- Exploring domain-informed features such as machine age.
- Further evaluating feature importance and model behaviour.
- Comparing additional CatBoost configurations.
- Performing more extensive validation to assess generalization.
- Refining the final prediction workflow and documenting reproducibility details.

These are possible next steps, not completed or verified improvements.

## Key Learnings

This project provided practical experience with:

- Exploratory data analysis on structured tabular data.
- Handling missing and anomalous values.
- Regression modelling and validation metrics.
- Working with high-cardinality categorical features.
- Using CatBoost's native categorical feature support.
- Hyperparameter optimization with cross-validation.
- Structuring an end-to-end machine learning notebook.

## Author

**Aarav Gupta**

B.Tech, Electrical Engineering — Maulana Azad National Institute of Technology (MANIT), Bhopal

IIT Madras BS in Data Science and Applications

---

*This project was developed as a practical exploration of machine learning techniques for historical heavy machinery transaction price prediction.*
