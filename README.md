

# **Fraud Detection Model Using XGBoost**

## **Overview**
This project implements a machine learning-based fraud detection system using the XGBoost classifier. The model was trained on a publicly available dataset to identify fraudulent transactions with high accuracy while minimizing false positives. This repository includes scripts for data preprocessing, model training, evaluation, and scripts for predicting new transactions.

---

## **Table of Contents**
1. [Overview](#overview)
2. [Performance Metrics and Business Implications](#performance-metrics-and-business-implications)
3. [Monetary Impact](#monetary-impact)
4. [Dataset](#dataset)
5. [Procedure](#Procedure)
7. [Model Performance](#model-performance)
8. [Future Work](#future-work)
9. [License](#license)

---

## **Performance Metrics and Business Implications**

| **Metric**            | **Value**         | **Business Insight**                                                                                           |
|------------------------|-------------------|----------------------------------------------------------------------------------------------------------------|
| **Precision (Fraud)**  | `~0.88`           | **88% of flagged frauds are truly fraudulent** (67 false positives out of **284,315 legitimate transactions**). Reduces unnecessary investigations and operational costs. |
| **Recall (Fraud)**     | `~1.00`           | **100% of fraudulent transactions are detected** (**492 out of 492 fraud cases**). Prevents financial and reputational damage. |
| **F1-Score (Fraud)**   | `~0.94`           | Balances precision and recall, ensuring robust fraud detection while minimizing false positives. |
| **Accuracy**           | `~1.00`           | The model correctly classifies nearly all transactions but accuracy is less meaningful due to class imbalance. |
| **AUPRC**              | `1.00`            | The model perfectly distinguishes fraud from non-fraud cases under imbalanced conditions. |
| **False Positives**    | `~67`             | Around **67 legitimate transactions out of 284,315** are incorrectly flagged as fraud (~0.02%), causing minor inconveniences. |
| **False Negatives**    | `0`               | No fraudulent transactions are missed out of **492 fraud cases** (~0% miss rate). This eliminates potential monetary loss. |
| **True Positives**     | `492`             | All **492 fraudulent transactions are detected** (~100% recall), preventing significant financial loss. |
| **True Negatives**     | `284,248`         | Correctly classifies **284,248 legitimate transactions out of 284,315** (~99.98%), ensuring smooth customer experience. |

---

## **Monetary Impact**

| **Scenario**            | **Metric**                  | **Estimated Cost/Impact**                             |
|--------------------------|----------------------------|------------------------------------------------------|
| **Fraud Loss Prevention**| Fraudulent Transactions: 492 | **Savings: $492,000** (assuming $1,000/transaction). |
| **Investigation Costs**  | False Positives: ~67        | **Cost: $3,350** (assuming $50/transaction).         |
| **Customer Retention**   | True Negatives: 284,248     | Improved trust, smooth transactions, revenue retained.|
| **Reputational Savings** | False Negatives: 0          | No reputational damage due to undetected fraud.      |

---

## **Dataset**

This project uses the **[Credit Card Fraud Detection Dataset](https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud)**.

### **Dataset Details**
- **Features**: 30
  - `Time`: Seconds elapsed between a transaction and the first transaction.
  - `Amount`: Transaction amount.
  - `V1` to `V28`: Anonymized features from PCA (Principal Component Analysis).
- **Target**: `Class`
  - 0: Legitimate Transaction
  - 1: Fraudulent Transaction
- **Size**: 284,807 transactions
- **Fraud Ratio**: ~0.17% (highly imbalanced).

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
