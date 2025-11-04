LendingClub Loan Analysis

Predicting loan default probability using LendingClub borrower data through Exploratory Data Analysis (EDA) and Machine Learning classification models (Logistic Regression and Random Forest).

🎯 Objective

To build and evaluate classification models that predict the probability of loan default using LendingClub’s borrower-level data.
The analysis includes:

-Data preprocessing and transformation

-Exploratory and bivariate analysis

-Model development (Logistic Regression, Random Forest)

-Feature importance interpretation

-Credit risk insights and actionable recommendations

🧩 Workflow & Methodology

1. Data Preprocessing

Handled missing values, encoded categorical variables, and scaled numeric predictors.

Removed redundant features and ensured target balance checks.

2. Exploratory Data Analysis (EDA)

Summary statistics, distribution plots, and correlation heatmaps to identify patterns.

3.Bivariate Analysis — Relationship Between Predictors and Loan Default

Examined how borrower and loan characteristics differ between defaulters and non-defaulters.

Key Numeric Predictors:

| Variable                             | Median (Non-Default) | Median (Default) | Observation                                         |
| ------------------------------------ | -------------------- | ---------------- | --------------------------------------------------- |
| Loan Amount (`loan_amnt`)            | 9,800                | 10,000           | Slightly higher loan amounts increase default risk. |
| Interest Rate (`int_rate`)           | 11.49%               | 13.61%           | Higher rates strongly linked to defaults.           |
| Installment                          | 278.6                | 293.9            | Larger monthly installments → higher risk.          |
| Annual Income (`annual_inc`)         | 60,000               | 53,000           | Defaulters earn less on average.                    |
| Debt-to-Income Ratio (`dti`)         | 13.25                | 14.29            | Higher DTI among defaulters.                        |
| Revolving Utilization (`revol_util`) | 47.8%                | 58.4%            | Over-leverage is a key risk factor.                 |
| Revolving Balance (`revol_bal`)      | 8,802                | 9,211            | Slightly higher balances among defaulters.          |
| Open Accounts (`open_acc`)           | 9                    | 8                | Fewer active accounts among defaulters.             |
| Employment Length (`emp_length_num`) | 4 yrs                | 5 yrs            | Tenure alone not a strong predictor.                |

Key Categorical Predictors:

| Variable            | Categories with Higher Default Rate                                   | Interpretation                                  |
| ------------------- | --------------------------------------------------------------------- | ----------------------------------------------- |
| Home Ownership      | OTHER (18.3%), RENT (15.0%)                                           | Renters and non-homeowners show higher default. |
| Verification Status | Verified (16.0%) > Source Verified (14.4%) > Not Verified (12.7%)     | Verified loans correspond to riskier profiles.  |
| Purpose             | Small Business (25.9%), Renewable Energy (18.4%), Educational (17.2%) | Certain loan purposes carry higher risk.        |
| State               | NV (21.7%), AK (18.7%), FL (17.6%)                                    | Regional differences highlight localized risks. |


Insights:

-Higher risk borrowers are charged higher rates → validates risk-based pricing.

-Lower income, higher DTI, and higher credit utilization → major drivers of default.

-Certain purposes and states show structural risk patterns.

⚙️ Model Development

Models were developed to predict borrower default likelihood:

-Logistic Regression (Baseline)

-Random Forest Classifier (Ensemble)

Both models were trained on the preprocessed dataset, with train-test split evaluation.

📈 Model Evaluation Summary

| Model               | Accuracy | Precision | Recall | F1-score | ROC-AUC |
| ------------------- | -------- | --------- | ------ | -------- | ------- |
| Logistic Regression | 0.640    | 0.221     | 0.626  | 0.327    | 0.685   |
| Random Forest       | 0.665    | 0.231     | 0.602  | 0.334    | 0.685   |

Interpretation:

-Random Forest marginally outperforms Logistic Regression in accuracy and F1-score.

-Both achieve ROC-AUC ≈ 0.68, indicating moderate discriminative ability.

-Recall (~0.60) shows good identification of actual defaulters.

-Precision (~0.23) indicates a few false positives, acceptable in credit risk where missing defaulters is costlier.

📊 Confusion Matrix Interpretation

[[5598 2692]
 [ 536  809]]

-True Negatives (5598): Correctly identified non-defaulters

-False Positives (2692): Non-defaulters incorrectly flagged

-True Positives (809): Correctly identified defaulters

-False Negatives (536): Missed defaulters

✅ The model successfully captures most true defaults while maintaining reasonable accuracy.

🔍 Top 5 Important Features

| Rank | Feature       | Importance | Interpretation                              |
| ---- | ------------- | ---------- | ------------------------------------------- |
| 1️⃣  | `int_rate`    | 0.272      | Higher rates = higher default probability   |
| 2️⃣  | `term_months` | 0.135      | Longer loan terms increase default risk     |
| 3️⃣  | `revol_util`  | 0.099      | High utilization indicates financial stress |
| 4️⃣  | `annual_inc`  | 0.086      | Low income → higher default risk            |
| 5️⃣  | `dti`         | 0.043      | High debt ratios → over-leverage            |


These align with credit risk theory,  interest rate, loan term, and utilization are dominant predictors.

💡 Business Insights

-Risk-based pricing is effective: Higher-risk borrowers receive higher rates.

-Leverage and utilization matter: Borrowers with high DTI and revol_util exhibit higher risk.

-Income segmentation: Lower-income borrowers show greater default risk.

-Purpose and geography matter: Certain loan purposes and states (e.g., NV, FL) have higher defaults.

-Repayment burden: Larger loans and installments slightly increase default risk.

🧭 Recommendations

-Integrate behavioral and income-based features in credit scoring models.

-Tighten approval for high-interest or long-term loans with high DTI.

-Develop early warning systems to track high revol_util and DTI borrowers.

-Use differentiated pricing — reward low-risk borrowers with better rates.

-Combine Logistic Regression (interpretability) and Random Forest (performance) for hybrid decision-making.

🏁 Conclusion

Machine learning models can effectively assess borrower risk using LendingClub data.
Key risk factors include interest rate, term, utilization, income, and DTI.
While Random Forest provides stronger predictive ability, Logistic Regression enhances interpretability — together forming a robust risk prediction framework.

🗂️ Project Structure

```
Lendingclub_Loan_Analysis/
│
├── Data_and_Dictionary/         # Raw dataset files and data dictionary
│   └── LendingClub_Loan_Data.csv
│
├── Report/                      # Final project report and documentation
│   └── LendingClub_Loan_Report.pdf
│
├── Source_Code/                 # Jupyter notebook and source scripts
│   └── Lendingclub_Loan_Analysis.ipynb
│
├── Visuals/                     # Charts and visualization outputs
│   └── feature_importance.png
│
├── .gitignore                   # Git ignore file for data, cache, and temporary files
├── README.md                    # Project documentation (this file)
└── requirements.txt             # Python dependencies for reproducibility

```
🧰 How to Reproduce

1.Clone this repository:

git clone https://github.com/Hasnath-Unnisa/Lendingclub_Loan_Analysis.git

2. Navigate into the folder:

cd Lendingclub_Loan_Analysis

3. Install dependencies:

pip install -r requirements.txt

4. Open the notebook:

jupyter notebook Source_Code/Lendingclub_Loan_Analysis.ipynb

5. Run all cells sequentially to reproduce the analysis and results.


## 👩‍💻 Author  

**Name:** Hasnath Unnisa  
**Email:** unnisahasnath@gmail.com  
**LinkedIn:** www.linkedin.com/in/hasnath22  




