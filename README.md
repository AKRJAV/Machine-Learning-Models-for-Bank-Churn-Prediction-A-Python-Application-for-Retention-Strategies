# Machine-Learning-Models-for-Bank-Churn-Prediction-A-Python-Application-for-Retention-Strategies

## **Project Overview**
This project focuses on predicting customer churn in the banking sector using a Gradient Boosting model. The project includes a comprehensive pipeline starting from data cleaning and preprocessing to the deployment of a Python-based GUI application. The application processes customer data, predicts churn probabilities, assigns risk levels, and visualizes results, offering actionable insights for banks.

---

## **Data Cleaning and Preprocessing**

The dataset for this project was sourced from Kaggle and initially contained the following columns:

| RowNumber | CustomerId | Surname | CreditScore | Geography | Gender | Age | Tenure | Balance | NumOfProducts | HasCrCard | IsActiveMember | EstimatedSalary | Exited | Complain | Satisfaction Score | Card Type | Point Earned |

### **Steps in Data Cleaning and Preprocessing**:
1. **Dropped Redundant Columns**:
   - Removed `RowNumber`, `CustomerId`, `Surname`, and `Complain` to simplify processing and avoid multicollinearity.<br>
     ![image](https://github.com/user-attachments/assets/f44f65a3-c0c9-44d4-9360-9934e37e6d32)

3. **Handled Missing Values**:
   - Checked for null values.
4. **Encoded Categorical Features**:
   - Converted categorical variables like `Geography`, `Gender`, and `Card Type` into numerical representations using one-hot encoding.<br>
     <img width="872" alt="image" src="https://github.com/user-attachments/assets/8748a9a0-eddb-408e-8234-73151e76ff85" />

5. **Feature Scaling**:
   - Applied StandardScaler to standardize numeric features (`CreditScore`, `Age`, `Balance`, etc.) for better model performance.<br>
     <img width="330" alt="image" src="https://github.com/user-attachments/assets/1abe6527-4528-41d8-a1d6-d880fffeeccd" />

6. **Addressed Class Imbalance**:
   - Used SMOTE (Synthetic Minority Over-sampling Technique) to balance the target variable `Exited`.<br>
     <img width="577" alt="image" src="https://github.com/user-attachments/assets/aa766b57-c2c1-43f0-ad8c-907bc3d7c1d9" />



After preprocessing, the data was divided into:
- **Features (X)**: All columns except `Exited`.
- **Target (y)**: The `Exited` column indicating whether a customer churned.

---

## **Model Training and Evaluation**

Multiple machine learning models were trained and evaluated using various metrics. The Gradient Boosting model outperformed others, with the following evaluation scores:
<br>
<img width="404" alt="image" src="https://github.com/user-attachments/assets/8e09dd8c-c74d-4b81-a3cb-6c8ec0ebaf60" />
<br>


### **AUC-ROC Curve**
<br>
![image](https://github.com/user-attachments/assets/ba4226c8-f81b-4f84-bdf3-3d868f5a18c1)
<br>
---

## **Python GUI Application**

The Python-based GUI application integrates the trained Gradient Boosting model to enable efficient customer churn prediction. 

### **Functionality**:
1. **Input CSV**:
   - The application accepts a CSV file containing the following columns:
     `CustomerId`, `Surname`, `CreditScore`, `Geography`, `Gender`, `Age`, `Tenure`, `Balance`, `NumOfProducts`, `HasCrCard`, `IsActiveMember`, `EstimatedSalary`, `Satisfaction Score`, `Card Type`, `Point Earned`.

2. **Outputs**:
   - **Predicted Churn Probability**: A value between 0 and 1.
   - **Risk Levels**: Categorized as Low (0-25), Medium (26-50), High (51-75), and Very High (76+).
   - **Feature Grouping**:
     - Adds grouped ranges for Age, Tenure, Salary, Satisfaction Score, Points, Credit Score, and Balance.
   - **Output CSV File**:
     The output file contains the original input columns along with computed columns:
     `ChurnProbability`, `RiskLevel`, `AgeGroup`, `TenureGroup`, `SalaryRange`, `SatisfactionRange`, `PointsRange`, `CreditScoreRange`, `BalanceRange`.

3. **Visualizations**:
   - Risk level distribution (pie chart).
   - Churn probability distribution (histogram).
   - Stacked bar charts showing feature contributions to risk levels.

4. **Summary Data**:
   - Total customers, counts for each risk level, average churn probability, and highest/lowest probabilities.

---

### **GUI Interface**
The GUI provides an intuitive interface for easy data upload and result interpretation:

![GUI Interface](./Sample_Visualizations/gui_interface.png)

---

## **Processed Visualizations**

### **Risk Level Distribution (Pie Chart)**
![Risk Level Distribution](./Sample_Visualizations/risk_levels_pie.png)

### **Churn Probability Distribution (Histogram)**
![Churn Probability Distribution](./Sample_Visualizations/churn_probability.png)

### **Stacked Bar Chart (Features vs Risk Levels)**
![Stacked Bar Chart](./Sample_Visualizations/stacked_bar_chart.png)

---

## **Input and Output Examples**

### **Sample Input File**
An example input file (`test_2k_customer.csv`) is included:

| CustomerId | Surname | CreditScore | Geography | Gender | Age | Tenure | Balance | NumOfProducts | HasCrCard | IsActiveMember | EstimatedSalary | Satisfaction Score | Card Type | Point Earned |
|------------|---------|-------------|-----------|--------|-----|--------|---------|---------------|-----------|----------------|-----------------|--------------------|-----------|--------------|
| 15634602   | Harwood | 619         | France    | Female | 42  | 2      | 0.00    | 1             | 1         | 1              | 101348.88       | 3                  | Gold      | 20           |

### **Sample Output File**
The processed output file (`output_file.xlsx`) includes:
1. **Main Sheet**:
   Contains original and computed columns.
2. **Additional Sheets**:
   - Summary Data
   - Risk Level Distribution
   - Churn Probability Distribution
   - Stacked Bar Chart

#### **Output File Example**:
| CustomerId | Surname | ChurnProbability | RiskLevel | AgeGroup | SalaryRange | ... |
|------------|---------|------------------|-----------|----------|-------------|-----|
| 15634602   | Harwood | 0.87             | High      | 40-50    | 100k-150k   | ... |
