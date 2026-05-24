# A Data-Driven Analysis of Health Insurance Costs

**University of Newcastle · Business Analytics · 2024**  
`Python` `R` `Regression Analysis` `EDA` `Data Visualisation` `Statistical Modelling` `Healthcare Analytics` `Decision Support`

---

## 📌 Project Overview

Health insurance premiums vary significantly across individuals based on a range of demographic, lifestyle, and medical risk factors. Understanding which factors most strongly drive cost is valuable for insurers setting fair premiums, policymakers designing healthcare funding models, and individuals making informed coverage decisions. This project applies **exploratory data analysis and regression modelling** to a health insurance dataset to identify the key predictors of insurance charges and build an interpretable cost prediction model.

---

## 🎯 Business Problem

Health insurers, actuaries, and healthcare economists face a common analytical challenge:
- Premium pricing must reflect underlying risk fairly and accurately — but risk factors interact in complex ways
- Poorly calibrated premiums lead to adverse selection (high-risk individuals dominating the pool) or customer attrition (low-risk individuals seeking cheaper alternatives)
- Identifying the relative contribution of each risk factor enables more transparent, defensible premium structures

Key analytical questions this project addresses:
- Which factors most significantly predict higher insurance charges?
- Are some risk factors more influential than others (e.g. smoking vs. BMI vs. age)?
- Can a regression model accurately estimate individual insurance charges from demographic and lifestyle data?
- How do interaction effects between factors (e.g. smoking combined with high BMI) amplify cost?

---

## 📂 Repository Contents

| File | Description |
|---|---|
| `*.ipynb` / `*.R` | Analysis notebook — EDA, statistical testing, regression modelling, and visualisation |
| `insurance.csv` | Health insurance dataset (age, sex, BMI, children, smoker status, region, charges) |
| `*.pdf` | Project report — methodology, findings, regression results, and business interpretation |

---

## 🔧 Methodology

### 1. Dataset Overview

| Variable | Type | Description |
|---|---|---|
| `age` | Numerical | Age of the primary beneficiary |
| `sex` | Categorical | Gender of the insured (male/female) |
| `bmi` | Numerical | Body Mass Index — measure of body fat relative to height/weight |
| `children` | Numerical | Number of dependents covered |
| `smoker` | Categorical | Whether the individual smokes (yes/no) |
| `region` | Categorical | Residential region in the US (northeast, northwest, southeast, southwest) |
| `charges` | Numerical | **Target variable** — individual medical costs billed by health insurance |

### 2. Exploratory Data Analysis (EDA)
- Analysed distributions of all variables — charges show a strong right skew with a high-cost outlier population
- Produced correlation analysis and scatter plots between numerical features and charges
- Generated boxplots to compare charges across categorical groups (smoker/non-smoker, region, sex)
- Identified interaction patterns: smokers with high BMI showed disproportionately higher charges

### 3. Key EDA Findings

| Factor | Relationship with Charges |
|---|---|
| **Smoking status** | Strongest single predictor — smokers incur significantly higher charges than non-smokers |
| **Age** | Positive linear relationship — charges increase consistently with age |
| **BMI** | Positive relationship, amplified significantly for smokers with BMI > 30 |
| **Number of children** | Modest positive effect |
| **Region** | Limited effect — southeast region shows marginally higher charges |
| **Sex** | Minimal effect after controlling for other variables |

### 4. Regression Modelling

**Models built and compared:**

| Model | Approach |
|---|---|
| **Simple Linear Regression** | Single predictor (age or BMI) — baseline understanding |
| **Multiple Linear Regression** | All features included — interpretable coefficient-based model |
| **Regression with Interaction Terms** | Captures the amplified effect of smoking × BMI interaction |

**Preprocessing:**
- One-hot encoded categorical variables (sex, smoker, region)
- Applied log transformation to charges to address right-skewed distribution
- Split data into training (80%) and test (20%) sets

**Evaluation metrics:**

| Metric | Description |
|---|---|
| **R² Score** | Proportion of charge variance explained by the model |
| **RMSE** | Root Mean Squared Error — average prediction error in dollars |
| **MAE** | Mean Absolute Error — interpretable average deviation |
| **Residual plots** | Check model assumptions: normality, homoscedasticity |

---

## 📊 Key Results

| Finding | Detail |
|---|---|
| Smoker status impact | Smokers pay on average **3–4× higher** charges than non-smokers — by far the largest single factor |
| Age effect | Each additional year of age increases predicted charges by a consistent, quantifiable margin |
| BMI × Smoking interaction | The combination of high BMI and smoking produces charges significantly higher than either factor alone — a critical interaction term |
| Model accuracy | Multiple regression with interaction terms achieved strong R² performance, substantially outperforming single-variable baselines |
| Regional variation | Minimal — region is not a material predictor after controlling for lifestyle factors |

---

## 💡 Business & Policy Interpretation

| Stakeholder | Insight |
|---|---|
| **Actuaries / Pricing Teams** | Smoking status and age should carry the highest weight in premium calculation; BMI interaction with smoking justifies risk-loading for high-BMI smokers |
| **Health Insurers** | Wellness incentive programs targeting smoking cessation offer the highest potential ROI in reducing claim costs |
| **Policymakers** | Data supports targeted public health investment in smoking reduction — with quantifiable downstream cost benefits to the health system |
| **Individuals** | Model can be used to demonstrate how lifestyle changes (e.g. quitting smoking) would affect estimated insurance costs |

---

## 🛠️ Tools & Libraries

| Category | Tools |
|---|---|
| Language | Python / R |
| Statistical Modelling | Scikit-learn (Python) / lm() (R) |
| Data Processing | Pandas, NumPy / dplyr, tidyr |
| Visualisation | Matplotlib, Seaborn / ggplot2 |
| Environment | Jupyter Notebook / R Studio |

---

## ⚠️ Ethical Considerations

- **Fairness in pricing:** Using demographic factors (age, sex, region) in premium calculation may raise equity concerns — particularly where these factors act as proxies for socioeconomic disadvantage
- **Smoking status disclosure:** Premium loading based on self-reported smoking status creates incentives for non-disclosure; verification mechanisms are needed
- **Model transparency:** Insurers should be able to explain premium calculation to policyholders — interpretable regression models support this obligation better than black-box approaches
- **Data limitations:** The dataset represents a US insurance context; findings may not generalise directly to other healthcare systems (e.g. Australia's Medicare-based model)

---

*Project completed as part of the Bachelor of Business Analytics at the University of Newcastle, 2024.*
