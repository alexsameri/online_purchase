# Online Shoppers Intention Analysis

This project analyzes online shoppers' behavior and predicts whether a session will result in a purchase (`Revenue`). The dataset is sourced from the [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/Online+Shoppers+Purchasing+Intention+Dataset).

---

## Table of Contents
1. [Dataset Overview](#dataset-overview)
2. [Project Workflow](#project-workflow)
    - [Data Preprocessing](#1-data-preprocessing)
    - [Exploratory Data Analysis (EDA)](#2-exploratory-data-analysis-eda)
    - [Machine Learning Pipeline](#3-machine-learning-pipeline)
    - [Model Training and Evaluation](#4-model-training-and-evaluation)
    - [Results](#5-results)
    - [Visualization](#6-visualization)
3. [How to Run](#how-to-run)
4. [Dependencies](#dependencies)
5. [Dataset Source](#dataset-source)
6. [Author](#author)

---

## Dataset Overview

The dataset contains **12,330 rows** and **18 columns**. Below is a summary of the key features:

| **Category**        | **Column Name**           | **Description**                                | **Values**                     |
|---------------------|---------------------------|------------------------------------------------|---------------------------------|
| Administrative      | `Administrative`          | Number of administrative pages visited         | Integer (e.g., 0, 3, 5)        |
|                     | `Administrative_Duration` | Time spent on administrative pages (seconds)   | Float (e.g., 0.0, 45.3, 120.8) |
| Informational       | `Informational`           | Number of informational pages visited          | Integer                        |
|                     | `Informational_Duration`  | Time spent on informational pages (seconds)    | Float                          |
| Product-Related     | `ProductRelated`          | Number of product pages visited                | Integer                        |
|                     | `ProductRelated_Duration` | Time spent on product pages (seconds)          | Float                          |
| User Engagement     | `BounceRates`             | Percentage of visitors who left immediately    | Float (0–1)                    |
|                     | `ExitRates`               | Percentage of pageviews that were last in session | Float (0–1)                  |
|                     | `PageValues`              | Average value of pages viewed before purchase  | Float (≥ 0)                    |
| Traffic Source      | `TrafficType`             | Source of traffic (20 categories)              | Integer (1–20)                 |
| Visitor Type        | `VisitorType`             | Type of visitor                                | 'New_Visitor', 'Returning_Visitor', 'Other' |
| Weekend             | `Weekend`                | Whether session occurred on weekend            | Boolean (True/False)           |
| Temporal            | `Month`                  | Month of the year                              | Abbreviated (e.g., 'Feb', 'Nov') |
| Special Day         | `SpecialDay`             | Proximity to special shopping day              | Float (0–1, where 1 = day of event) |
| Target Variable     | `Revenue`                | Whether purchase occurred                      | Boolean (True/False)           |

---

## Project Workflow

### 1. Data Preprocessing
- Checked for missing values and duplicates.
- Performed feature engineering:
  - Created `Total_Duration` as the sum of `Administrative`, `Administrative_Duration`, and `ProductRelated_Duration`.
  - Created `PageValue_to_ExitRatio` as the ratio of `PageValues` to `ExitRates`.
  - Created `BounceExit_Interaction` as the product of `BounceRates` and `ExitRates`.

### 2. Exploratory Data Analysis (EDA)
- Visualized the distribution of numerical features using histograms.
- Analyzed the relationship between categorical features and the target variable (`Revenue`) using count plots.
- Generated a correlation heatmap to identify relationships between features.

### 3. Machine Learning Pipeline
- Split the data into training and testing sets (80/20 split).
- Preprocessed the data:
  - Applied `PowerTransformer` and `StandardScaler` to numerical features.
  - Applied `OneHotEncoder` to categorical features.
- Used `SMOTE` to handle class imbalance.

### 4. Model Training and Evaluation
Trained and evaluated the following models using `RandomizedSearchCV` for hyperparameter tuning:
- Logistic Regression
- Neural Network (MLPClassifier)
- Random Forest
- Gradient Boosting

#### Metrics:
- Accuracy
- ROC AUC Score
- Confusion Matrix
- Classification Report

### 5. Results
The best-performing models are stored in the `results` dictionary. The top models based on ROC AUC are:
- **Neural Network**
- **Gradient Boosting**

### 6. Visualization
- Confusion matrices for each model.
- A summary table of model performance metrics.

---

## How to Run

1. Clone the repository:
   ```bash
   git clone https://github.com/alexsameri/online_purchase.git
   cd online_purchase