# House Price Prediction Using Linear Regression

## Project Overview

This project develops a Machine Learning regression model to predict house prices using housing characteristics such as area, number of bedrooms, bathrooms, stories, parking facilities, and other amenities.

The project uses **Python, Pandas, NumPy, Matplotlib, Seaborn, and Scikit-learn** to perform data analysis, preprocessing, model training, prediction, and evaluation.

The objective is to understand how housing features relate to prices and build a model that estimates house prices for previously unseen data.

## Objectives

- Load and explore a real-world housing dataset from Kaggle.
- Perform data quality checks for missing values and duplicate records.
- Analyze relationships between housing features and house prices.
- Prepare numerical and categorical features for Machine Learning.
- Split the dataset into training and testing sets.
- Train a Linear Regression model.
- Predict house prices for test data and a sample house.
- Evaluate the model using MAE, MSE, RMSE, and R².
- Visualize actual versus predicted prices and analyze model residuals.

## Dataset

**Dataset:** Housing Prices Dataset  
**Source:** [Kaggle – Housing Prices Dataset by Yasser H.](https://www.kaggle.com/datasets/yasserh/housing-prices-dataset)

**File used:** `Housing.csv`

### Dataset Summary

| Property | Value |
|---|---:|
| Total records | 545 |
| Total columns | 13 |
| Target variable | `price` |
| Input features | 12 |
| Missing values found | 0 |
| Duplicate records found | 0 |

### Features Description

| Feature | Description |
|---|---|
| `area` | Area of the house |
| `bedrooms` | Number of bedrooms |
| `bathrooms` | Number of bathrooms |
| `stories` | Number of stories |
| `mainroad` | Whether the house is connected to the main road |
| `guestroom` | Whether a guestroom is available |
| `basement` | Whether the house has a basement |
| `hotwaterheating` | Whether hot-water heating is available |
| `airconditioning` | Whether air conditioning is available |
| `parking` | Number of parking spaces |
| `prefarea` | Whether the house is in a preferred area |
| `furnishingstatus` | Furnished, semi-furnished, or unfurnished |
| `price` | House price; target variable |

**Note:** This dataset does not contain explicit location names or the age of each house. The model therefore uses the features actually available in the dataset.

## Technologies Used

- **Programming language:** Python
- **Data manipulation:** Pandas, NumPy
- **Data visualization:** Matplotlib, Seaborn
- **Machine Learning:** Scikit-learn
- **Development environment:** Jupyter Notebook
- **Version control:** Git and GitHub

## Project Workflow

### 1. Data Collection and Exploration

Loaded `Housing.csv` into a Pandas DataFrame and examined its dimensions, column names, data types, sample records, and statistical summaries.

### 2. Data Quality Checks

Checked for missing values and duplicate records. The dataset contained no missing values or duplicate rows, so no rows needed to be removed for these reasons.

### 3. Exploratory Data Analysis (EDA)

Performed exploratory analysis to understand the distribution of house prices and the relationships between housing characteristics and prices.

Key observations:

- House prices have a right-skewed distribution.
- Area has a positive correlation with price.
- Bathrooms and stories also show positive relationships with price.
- Houses with air conditioning and those in preferred areas have higher average prices in this dataset.

The observed relationships are descriptive and do not establish causation.

### 4. Data Preprocessing

Separated the independent variables (`X`) from the target variable (`y`).

- **Numerical features:** `area`, `bedrooms`, `bathrooms`, `stories`, `parking`
- **Categorical features:** `mainroad`, `guestroom`, `basement`, `hotwaterheating`, `airconditioning`, `prefarea`, `furnishingstatus`

Used `StandardScaler` to scale numerical features and `OneHotEncoder` to convert categorical features into numerical representations.

A Scikit-learn `ColumnTransformer` and `Pipeline` combine preprocessing and model training. The preprocessing steps are fitted on the training data to prevent information leakage from the test set.

### 5. Train-Test Split

Split the dataset into training and testing sets using an 80:20 ratio.

| Dataset | Records |
|---|---:|
| Training set | 436 |
| Testing set | 109 |
| Total | 545 |

**Random state:** `42`

### 6. Model Training

Trained a `LinearRegression` model using Scikit-learn.

The model learns the relationship between housing features and the target price using the training data. It then predicts prices for the unseen test set.

### 7. Model Prediction

Generated predictions for the test set and a sample house.

For the sample house with an area of 6,000, 3 bedrooms, 2 bathrooms, 2 stories, 2 parking spaces, and the specified amenities, the model predicted:

**Predicted price: 7,412,314.49 price units**

This is a model estimate, not a guaranteed market price. The dataset's currency and unit metadata should be verified before assigning a currency symbol.

## Model Evaluation

The Linear Regression model was evaluated on the 109-record test set.

| Metric | Result |
|---|---:|
| Mean Absolute Error (MAE) | 970,043.40 |
| Mean Squared Error (MSE) | 1,754,318,687,330.67 |
| Root Mean Squared Error (RMSE) | 1,324,506.96 |
| R² Score | 0.6529 |

### Interpretation

**MAE — 970,043.40**

The average absolute difference between actual and predicted house prices is approximately 970,043 price units.

**MSE — 1,754,318,687,330.67**

Mean Squared Error averages the squared prediction errors. It penalizes larger errors more heavily than MAE.

**RMSE — 1,324,506.96**

Root Mean Squared Error is expressed in the same price units as the target and gives greater weight to large prediction errors.

**R² Score — 0.6529**

The model explains approximately **65.29% of the variation in test-set house prices**, relative to predicting the test-set mean as the baseline. This indicates a useful baseline relationship, but there is still substantial unexplained variation.

> Regression models are not normally evaluated using classification accuracy. R² is the appropriate score reported here, alongside MAE, MSE, and RMSE.

## Visualizations

The notebook includes visualizations for:

- Distribution of house prices
- Correlation between numerical features and price
- Area versus house price, including a fitted regression line
- Actual versus predicted prices
- Residual analysis to inspect prediction errors

These visualizations help assess the relationships in the dataset and identify where the model performs well or poorly.

## Model Limitations

- The dataset does not include explicit location names or house age.
- Linear Regression may not capture all nonlinear relationships between housing characteristics and prices.
- The model underpredicts some higher-priced houses and overpredicts some lower-priced houses.
- Prediction errors are relatively large for some properties.
- Results depend on the dataset and the chosen train-test split.
- The model should be tested on additional data before being used for real-world pricing decisions.

## How to Run the Project

### Prerequisites

Install Python and Jupyter Notebook, or use an environment that supports `.ipynb` files.

### 1. Clone the repository

Replace the URL below with your actual GitHub repository URL.

```bash
git clone https://github.com/YOUR_USERNAME/YOUR_REPOSITORY.git
cd YOUR_REPOSITORY
```

### 2. Install dependencies

```bash
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
```

### 3. Check the project files

Keep the dataset and notebook in the same directory:

```text
House-Price-Prediction/
├── Housing.csv
├── House_Price_Prediction_Linear_Regression_Final.ipynb
└── README.md
```

The notebook should load the dataset using a relative path:

```python
import pandas as pd

df = pd.read_csv("Housing.csv")
```

### 4. Launch Jupyter Notebook

```bash
jupyter notebook
```

Open the project notebook and select **Run All** to execute the workflow from data loading through evaluation.

## Project Deliverables

- `Housing.csv` — housing dataset used for the project
- `House_Price_Prediction_Linear_Regression_Final.ipynb` — notebook containing analysis, preprocessing, training, predictions, evaluation, and visualizations
- `README.md` — project documentation
- Conclusion PDF — project summary, evaluation results, and limitations

## Conclusion

This project demonstrates an end-to-end Machine Learning workflow for predicting house prices using Linear Regression. It covers data inspection, exploratory analysis, preprocessing of numerical and categorical features, train-test splitting, model training, prediction, and evaluation.

The final model achieved an R² score of **0.6529**, with an MAE of **970,043.40** on the test set. The results indicate that the selected features provide useful predictive information, while the remaining errors show opportunities for improvement.

Future work could evaluate additional regression algorithms, use cross-validation, tune regularization, and investigate more informative features such as location and property age if suitable data becomes available.

## Author

**Chaitanya Reddy**

Computer Science and Engineering | Machine Learning Project

---

*This project was developed for educational purposes to practice data analysis and supervised regression using Python and Scikit-learn.*
