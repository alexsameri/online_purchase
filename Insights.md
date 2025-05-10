# Insights from Online Shoppers Intention Dataset

This document summarizes the key insights derived from the analysis of the Online Shoppers Intention dataset.

---

## 1. General Dataset Insights
- The dataset contains **12,330 rows** and **18 columns**.
- The target variable is `Revenue`, which indicates whether a session resulted in a purchase.
- The dataset includes both numerical and categorical features:
  - **Numerical Features**: `Administrative_Duration`, `Informational_Duration`, `ProductRelated_Duration`, `BounceRates`, `ExitRates`, `PageValues`.
  - **Categorical Features**: `Month`, `VisitorType`, `Weekend`, `TrafficType`.

---

## 2. Missing Values and Duplicates
- **Missing Values**: No missing values were found in the dataset.
- **Duplicates**: No duplicate rows were identified.

---

## 3. Feature Distributions
### Numerical Features:
- **`Administrative_Duration`**, **`Informational_Duration`**, and **`ProductRelated_Duration`** are highly skewed, with most sessions having low durations.
- **`BounceRates`** and **`ExitRates`** are concentrated near 0, indicating that most users do not leave immediately or exit frequently.
- **`PageValues`** has a large number of zero values, suggesting that many sessions did not lead to purchases.

### Categorical Features:
- **`Month`**: Certain months (e.g., November) have higher activity, likely due to seasonal shopping trends.
- **`VisitorType`**: Most visitors are `Returning_Visitor`, followed by `New_Visitor`.
- **`Weekend`**: A significant portion of sessions occurs on weekends.

---

## 4. Correlation Analysis
### Revenue Correlation:
- **`PageValues`** has a strong positive correlation with `Revenue`, indicating that higher page values are associated with purchases.
- **`BounceRates`** has a negative correlation with `Revenue`, suggesting that sessions with higher bounce rates are less likely to result in purchases.
- **`ExitRates`** also negatively correlates with `Revenue`.

### Feature Relationships:
- **`BounceRates`** and **`ExitRates`** are positively correlated, indicating that sessions with high bounce rates also tend to have high exit rates.

---

## 5. Revenue Distribution
- The dataset is **imbalanced**:
  - A majority of sessions did not result in a purchase (`Revenue = 0`).
  - Only a small percentage of sessions resulted in a purchase (`Revenue = 1`).

---

## 6. Feature Engineering Insights
- **`Total_Duration`**:
  - Combines `Administrative_Duration`, `Informational_Duration`, and `ProductRelated_Duration` to provide a holistic view of the total time spent on the website.
- **`PageValue_to_ExitRatio`**:
  - Higher ratios indicate that users are more likely to purchase before exiting.
- **`BounceExit_Interaction`**:
  - Captures the combined effect of bounce and exit rates on user behavior.

---

## 7. Categorical Feature Impact on Revenue
- **`Month`**:
  - Certain months (e.g., November) have higher purchase rates, likely due to holiday shopping.
- **`VisitorType`**:
  - Returning visitors are more likely to make purchases compared to new visitors.
- **`Weekend`**:
  - Sessions on weekends have a slightly higher likelihood of resulting in purchases.

---

## 8. Model Performance Insights
- **Top Models**:
  - **Neural Network** and **Gradient Boosting** are the best-performing models based on ROC AUC scores.
- **Confusion Matrices**:
  - Both models perform well in identifying sessions that result in purchases (`Revenue = 1`), but there may still be some false positives and false negatives.
- **Feature Importance**:
  - Models like Random Forest and Gradient Boosting highlight the most important features influencing purchase behavior.

---

## 9. Business Insights
- **Key Drivers of Purchases**:
  - High `PageValues` and low `BounceRates` are strong indicators of purchase likelihood.
  - Sessions with longer durations across multiple page types are more likely to result in purchases.
- **Seasonal Trends**:
  - Marketing efforts should focus on months with higher purchase activity (e.g., November).
- **Returning Visitors**:
  - Retargeting campaigns for returning visitors may yield higher conversion rates.

---

## Conclusion
These insights provide actionable information for improving user experience, optimizing marketing strategies, and enhancing predictive modeling for purchase behavior.