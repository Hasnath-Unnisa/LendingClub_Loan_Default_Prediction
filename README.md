# 🏦 LendingClub Loan Default Prediction

> **Machine Learning Project** — Predicting borrower loan default probability using LendingClub data through Exploratory Data Analysis (EDA), Feature Engineering, and Classification Models (Logistic Regression & Random Forest).

---

## 🎯 **Objective**

The goal of this project is to build and evaluate classification models that predict the probability of loan default using LendingClub’s borrower-level data.

---

## 📊 **Workflow Overview**

```text
Data Preprocessing → Exploratory Data Analysis → 
Bivariate Analysis → Model Development →
Evaluation → Business Insights → Recommendations
```

---

## 🧹 **1. Data Preprocessing**

- Handled missing values and encoded categorical variables
- Scaled numerical features
- Removed outliers and redundant columns
- Prepared clean dataset for modeling

---

## 🔍 **2. Bivariate Analysis — Relationship Between Predictors and Default**

### 📈 Numeric Predictors

| Variable | Median (Non-Default) | Median (Default) | Key Insight |
|-----------|----------------------|------------------|-------------|
| Loan Amount | 9,800 | 10,000 | Higher loan amounts slightly increase default risk |
| Interest Rate | 11.49% | 13.61% | Higher interest rates → higher risk |
| Annual Income | 60,000 | 53,000 | Defaulters have lower incomes |
| DTI | 13.25 | 14.29 | High DTI = higher leverage and risk |
| Revolving Utilization | 47.8% | 58.4% | Over-leverage strongly linked to default |

### 🏠 Categorical Predictors

| Variable | Categories with Higher Default | Interpretation |
|-----------|--------------------------------|----------------|
| Home Ownership | OTHER (18.3%), RENT (15.0%) | Renters are riskier than homeowners |
| Loan Purpose | Small Business (25.9%), Education (17.2%) | Business/education loans show higher risk |
| State | NV (21.7%), FL (17.6%) | Regional differences reflect economic variation |

---

## ⚙️ **3. Model Development**

Two models were developed:

- **Logistic Regression:** Baseline interpretable model
- **Random Forest:** Ensemble model for higher predictive accuracy

---

## 📈 **4. Model Evaluation Summary**

| Model | Accuracy | Precision | Recall | F1-score | ROC-AUC |
|--------|-----------|------------|----------|------------|-----------|
| Logistic Regression | 0.640 | 0.221 | 0.626 | 0.327 | 0.685 |
| Random Forest | 0.665 | 0.231 | 0.602 | 0.334 | 0.685 |

✅ **Interpretation:**
- Random Forest slightly outperforms Logistic Regression.
- Both achieve moderate discriminative ability (**ROC-AUC ≈ 0.68**).
- **Recall (~0.60)** is crucial — better at identifying true defaulters.
- **Precision (~0.23)** is acceptable in credit risk contexts.

---

## 🧩 **5. Top 5 Important Features**

| Rank | Feature | Importance | Interpretation |
|------|----------|-------------|----------------|
| 🥇 | `int_rate` | 0.272 | Higher interest rates → higher default probability |
| 🥈 | `term_months` | 0.135 | Longer tenures increase risk |
| 🥉 | `revol_util` | 0.099 | High utilization = financial stress |
| 4️⃣ | `annual_inc` | 0.086 | Lower income = higher risk |
| 5️⃣ | `dti` | 0.043 | Over-leveraged borrowers more likely to default |

---

## 💡 **6. Business Insights**

💰 **Risk-based pricing works:**
Borrowers with higher interest rates are riskier, validating LendingClub’s pricing model.

📊 **Borrower leverage matters:**
High DTI and revol_util strongly predict repayment stress.

📍 **Income & geography matter:**
Lower-income borrowers and certain states (e.g., NV, FL) show higher default rates.

---

## 🧭 **7. Recommendations**

- Integrate behavioral features like `revol_util` and `dti` into scoring models.
- Tighten approval for **high-interest** and **long-term loans**.
- Deploy **early warning systems** for borrowers with rising DTI or utilization.
- Reward low-risk borrowers with better interest rates.
- Combine **Logistic Regression (interpretability)** + **Random Forest (accuracy)** for robust decision-making.

---

## 🏁 **8. Conclusion**

Machine learning effectively predicts borrower default risk using LendingClub data.
Key drivers: `int_rate`, `term_months`, `revol_util`, `annual_inc`, and `dti`.
Random Forest provides stronger predictive power, while Logistic Regression adds transparency — together forming a solid credit risk framework.

---

## 🗂️ **Project Structure**

```
Lendingclub_Loan_Default/
│
├── Data_and_Dictionary/         # Raw data & data dictionary
├── Report/                      # Final project report (DOCX)
├── Source_Code/                 # Jupyter notebook & scripts
├── Visuals/                     # Charts & plots
│
├── README.md                    # Project documentation
├── requirements.txt              # Python dependencies
├── .gitignore                    # Ignored files/folders
└── results_summary.json          # Auto-generated results summary
```

---

## 👩‍💻 Author  

**Name:** Hasnath Unnisa  
**Email:** unnisahasnath@gmail.com  
**LinkedIn:** www.linkedin.com/in/hasnath22  

---

## ⭐ **If you found this helpful, consider giving the repository a star!**
