# Analysis-of-Valuation-Biases-in-Listed-Companies-Based-on-Employee-Sentiment-Data-Glassdoor
Quantifying the "Invisible" Assets: Analyzing the impact of Employee Sentiment (Glassdoor) and Founder-Leadership on Nasdaq 100 valuations using PCA and FGLS models in R.

# Corporate Culture, Leadership & Equity Valuation 📊

![R](https://img.shields.io/badge/Language-R-blue)
![Analysis](https://img.shields.io/badge/Method-Econometrics-orange)
![Status](https://img.shields.io/badge/Status-Completed-success)

## 📖 Overview
In modern quantitative finance, traditional financial statements only tell half the story. This research project investigates the impact of **"Intangible Assets"**—specifically Corporate Culture and Founder Leadership—on the valuation (P/E Ratio) of Nasdaq 100 companies.

Using **Alternative Data** scraped from Glassdoor, this project constructs a statistical model to determine if high employee sentiment and founder-led management command a valuation premium.

## 🧠 Methodology & Technical Approach

### 1. Data Construction
The dataset merges traditional financial fundamentals with unstructured sentiment data:
* **Dependent Variable:** log P/E Ratio (Price-to-Earnings).
* **Key Regressors:** Founder CEO Status (Binary), Glassdoor Ratings (Culture, CEO Approval, Friend Recommandation).
* **Controls:** Market Cap, Net Margin, Revenue Growth.

### 2. Dimensionality Reduction (PCA)
Glassdoor metrics (Recommandation, Culture, CEO Approval) suffer from high **Multicollinearity**. To resolve this, I implemented **Principal Component Analysis (PCA)** to synthesize these variables into a single, orthogonal factor: `sentiment_index`.

### 3. Econometric Modeling (OLS vs. FGLS)
The analysis proceeded in two stages:
1.  **OLS Baseline:** Initial estimation using Ordinary Least Squares.
2.  **Diagnostic Testing:**
    * **Breusch-Pagan Test:** Detected significant Heteroscedasticity ($p < 0.05$), rendering OLS standard errors unreliable.
    * **Shapiro-Wilk Test:** Analyzed residual normality.
3.  **Robust Estimation:** Implemented **Feasible Generalized Least Squares (FGLS)** to correct for heteroscedasticity and provide BLUE (Best Linear Unbiased Estimators).

## 📉 Key Findings
* **The Founder Premium:** Founder-CEO companies show a statistically significant positive correlation with higher P/E ratios.
* **The "Sentiment Paradox":** Interestingly, the interaction term between Founder Status and Culture is *negative*. This suggests that while investors value founder-CEO firms, they may penalize "excessively comfortable" cultures in aggressive growth environments.

## 📂 Repository Structure
* **File:** `ANG-LE.qmd`
* **Description:** The source code (R/Quarto). Contains the full workflow: Data loading, PCA Scree plots, OLS modeling, and Diagnostic testing.
* **File:** `ANG-LE.html`
* **Description:** The rendered report containing the final regression tables and visualizations.
* **File:** `Econometrie.xlsx`
* **Description:** The raw dataset used for the analysis.

---
*Author: Ming Wei ANG & Ba Minh LE*
