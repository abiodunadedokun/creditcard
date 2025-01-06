

# **Fraud Detection Model Using XGBoost**

---

## **Table of Contents**
1. [Overview](#overview)
2. [Performance Metrics and Business Implications](#performance-metrics-and-business-implications)
3. [Dataset](#dataset)
4. [Procedure](#Procedure)
5. [Model Performance](#model-performance)
6. [Future Work](#future-work)
7. [License](#license)

---
## **Overview**

Detecting fraudulent credit card transactions is critical to safeguarding customers and ensuring they are not charged for unauthorized purchases. It also helps credit card companies minimize financial losses and maintain customer trust. This project addresses this challenge by implementing a machine learning-based fraud detection system using the XGBoost classifier leveraging a publicly available dataset.


---

## **Performance Metrics and Business Implications**

| **Metric**            | **Value**         | **Business Insight**                                                                                           |
|------------------------|-------------------|----------------------------------------------------------------------------------------------------------------|
| **Precision (Fraud)**  | `~0.88`           | **88% of flagged frauds are truly fraudulent** (67 false positives out of **284,315 legitimate transactions**). Reduces unnecessary investigations and operational costs. |
| **Recall (Fraud)**     | `~1.00`           | **100% of fraudulent transactions are detected** (**492 out of 492 fraud cases**). Prevents financial and reputational damage. |
| **F1-Score (Fraud)**   | `~0.94`           | Balances precision and recall, ensuring robust fraud detection while minimizing false positives. |
| **AUPRC**              | `1.00`            | The model perfectly distinguishes fraud from non-fraud cases under imbalanced conditions. |
| **False Positives**    | `~67`             | Around **67 legitimate transactions out of 284,315** are incorrectly flagged as fraud (~0.02%), causing minor inconveniences. |
| **False Negatives**    | `0`               | No fraudulent transactions are missed out of **492 fraud cases** (~0% miss rate). This eliminates potential monetary loss. |
| **True Positives**     | `492`             | All **492 fraudulent transactions are detected** (~100% recall), preventing significant financial loss. |
| **True Negatives**     | `284,248`         | Correctly classifies **284,248 legitimate transactions out of 284,315** (~99.98%), ensuring smooth customer experience. |

---

## **Dataset**

This project uses the **[Credit Card Fraud Detection Dataset](https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud)**.
The dataset contains transactions made by credit cards in September 2013 by European cardholders.
This dataset presents transactions that occurred in two days, where we have 492 frauds out of 284,807 transactions. The dataset is highly unbalanced, the positive class (frauds) account for 0.172% of all transactions.

It contains only numerical input variables which are the result of a PCA transformation. Unfortunately, due to confidentiality issues, we cannot provide the original features and more background information about the data. Features V1, V2, … V28 are the principal components obtained with PCA, the only features which have not been transformed with PCA are 'Time' and 'Amount'. Feature 'Time' contains the seconds elapsed between each transaction and the first transaction in the dataset. The feature 'Amount' is the transaction Amount, this feature can be used for example-dependant cost-sensitive learning. Feature 'Class' is the response variable and it takes value 1 in case of fraud and 0 otherwise.

Given the class imbalance ratio, measuring the accuracy using the Area Under the Precision-Recall Curve (AUPRC) is recommended. 

---

## **Procedure**

1. **Preprocessing**:
   - Handle class imbalance using SMOTE.
   - Scale numerical features like `Time` and `Amount` using `StandardScaler`.

2. **Model Training**:
   - Trained an XGBoost classifier on the preprocessed dataset.
   - Optimize hyperparameters for precision and recall.

3. **Evaluation**:
   - Evaluate the model on both balanced and imbalanced test datasets.
   - Assess performance using precision, recall, F1-score, and AUPRC

---

## **Model Performance**

| **Metric**        | **Value** |
|--------------------|-----------|
| **AUPRC**         | 1.00      |
| **Precision**      | ~0.88     |
| **Recall**         | ~1.00     |
| **F1-Score**       | ~0.94     |

---

## **Future Work**

1. Experiment with alternative resampling techniques.
2. Explore ensemble models for further performance improvement.
3. Add advanced visualizations for better interpretability of fraud patterns.

---

## **License**
This project is licensed under the [MIT License](LICENSE).
