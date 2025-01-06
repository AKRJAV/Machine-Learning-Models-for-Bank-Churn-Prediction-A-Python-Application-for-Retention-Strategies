# Machine-Learning-Models-for-Bank-Churn-Prediction-A-Python-Application-for-Retention-Strategies

## **Project Overview**
This project aims to predict customer churn in the banking sector using machine learning models and a Python-based GUI application. The solution leverages customer behavior and demographic data to provide churn probabilities and risk levels, aiding banks in implementing effective retention strategies.

---

## **Dataset Information**
### **Input CSV File**:
The input CSV file should include the following columns:
- `RowNumber`: Record identifier (not used for processing).
- `CustomerId`: Unique customer ID (not used for processing).
- `Surname`: Customer surname (not used for processing).
- `CreditScore`: Customer's credit score.
- `Geography`: Customer's region.
- `Gender`: Customer's gender.
- `Age`: Customer's age.
- `Tenure`: Number of years with the bank.
- `Balance`: Account balance.
- `NumOfProducts`: Number of products the customer uses.
- `HasCrCard`: Indicates if the customer has a credit card.
- `IsActiveMember`: Indicates if the customer is an active member.
- `EstimatedSalary`: Estimated salary of the customer.
- `Exited`: Target variable (used only during model training).

### **Output CSV File**:
The application generates an output CSV file containing the following columns:
- **Input Columns**: All input columns except `RowNumber` and `Exited`.
- **Computed Columns**:
  - `ChurnProbability`: Predicted churn probability for each customer.
  - `RiskLevel`: Risk category based on churn probability:
    - Low (0-25)
    - Medium (26-50)
    - High (51-75)
    - Very High (76+)
  - Aggregated feature ranges:
    - `AgeGroup`: Categorized age range.
    - `TenureGroup`: Categorized tenure range.
    - `SalaryRange`: Categorized salary range.
    - `SatisfactionRange`: Categorized satisfaction score range.
    - `PointsRange`: Categorized points earned range.
    - `CreditScoreRange`: Categorized credit score range.
    - `BalanceRange`: Categorized balance range.

---

## **Preprocessing and Model Development**
1. **Data Cleaning**:
   - Removed irrelevant columns: `RowNumber`, `CustomerId`, `Surname`.
   - Analyzed data using histograms and bar charts for numeric and nominal columns.

2. **Feature Engineering**:
   - One-hot encoded categorical columns.
   - Correlation analysis identified `Complain` as perfectly correlated with `Exited`, so it was removed.

3. **Splitting Data**:
   - Features (`X`): All columns except `Complain` and `Exited`.
   - Target (`y`): `Exited`.
   - Data split into 80% training and 20% testing datasets.

4. **Balancing and Scaling**:
   - Balanced training data using SMOTE.
   - Scaled features using `StandardScaler`.

5. **Model Training and Evaluation**:
   - Models used: Logistic Regression, SVC, KNN, Decision Tree, Random Forest, Gradient Boosting, and Bernoulli Naive Bayes.
   - Evaluated using Accuracy, Precision, Recall, F1-Score, and AUC-ROC.

6. **Best Model**:
   - Gradient Boosting was selected as the best model for deployment based on evaluation metrics.

---

## **Model Performance**
The performance of all trained models (accuracy, precision, recall, F1-score, and AUC-ROC) is saved in a dedicated file (e.g., `model_performance.csv`). You can include this file in the repository under a directory named `Model_Performance`. 

---

## **GUI Application Features**
### **Outputs**:
1. **Churn Predictions**:
   - Churn probabilities and risk levels (`Low`, `Medium`, `High`, `Very High`) for each customer.

2. **Summary Metrics**:
   - Total Customers.
   - Count of customers in each risk category.
   - Average, maximum, and minimum churn probabilities.
   - Highest risk level.

3. **Visualizations**:
   - **Risk Level Distribution**: Pie chart displaying the proportion of customers in each risk level.
   - **Churn Probability Distribution**: Histogram showing the distribution of predicted churn probabilities.
   - **Clustered Bar Charts**: Contribution of features (e.g., `Age`, `Balance`, `CreditScore`) to different risk levels.

### **Example Visualizations**:
Include the following examples in the repository under a directory named `Sample_Visualizations`:
1. **Stacked Bar Chart**:
   - Example: `Age vs Risk Levels`.
2. **Churn Probability Distribution**:
   - Example: Histogram of churn probabilities.
3. **Risk Level Distribution**:
   - Example: Pie chart of risk levels.

---
