# Marketing-Class-Project

# 🍿 Dataflix: Netflix Content Longevity Analysis

## 📌 Executive Summary

In an era of infinite content and rising production costs, Netflix faces a critical challenge: identifying which titles will *retain audience attention over time*, not just debut strongly.  
Our team, **Dataflix**, analyzed global Netflix Top 10 rankings to uncover the structural drivers of content longevity.

Rather than relying solely on early popularity metrics, we examined how **content format**, **language**, and **initial performance** interact to influence how long a title remains in the Top 10.

---

## 🔬 Methodology & Technical Approach

### 1. Data Source & Preparation

We utilized a publicly available **global Netflix Top 10 dataset from Kaggle**, covering weekly rankings across **190+ countries**.

**Data Preparation Steps**
- Cleaned missing and null values in season-level fields
- Differentiated **Films** vs. **TV Series** based on episode continuity
- Standardized ranking variables across countries and weeks

**Feature Engineering**
- `Format`: TV Series vs. Film  
- `Language`: English vs. Non-English  
- `Weekly Rank`: Early-stage performance indicator  
- `Cumulative Weeks`: Total longevity in the Top 10

---

## 🔬 Statistical Modeling & Inference

To quantify the drivers of content longevity, we employed a **Multiple Linear Regression (MLR)** framework using **Ordinary Least Squares (OLS)**.  
This approach allows us to isolate the marginal effect of each content attribute while controlling for early performance.

### 📐 Model Specification

Our dependent variable is **Longevity**, defined as total weeks a title remains in the Top 10.

Longevityi​=β0​+β1​(WeeklyRanki​)+β2​(TVi​)+β3​(NonEnglishi​)+ϵi​


**Where:**
- \(\beta_0\): Baseline longevity  
- \(WeeklyRank\): Early performance signal  
- \(TV\): Binary indicator for TV Series  
- \(NonEnglish\): Binary indicator for non-English content  
- \(\epsilon\): Unobserved factors

---

### 📊 Regression Results

| Variable | Coefficient | Significance | Interpretation |
|-------|------------|-------------|---------------|
| **Intercept** | 0.141 | — | Baseline expected longevity |
| **TV Series** | 2.187 | ✅ Significant | TV shows remain ~2.2 weeks longer than films |
| **Non-English** | 2.012 | ✅ Significant | Non-English content benefits from global long-tail demand |
| **Weekly Rank** | 0.091 | Moderate | Higher early rank slightly improves longevity |

---

### 📈 Partial Regression Analysis

To validate our findings, we employed **Partial Regression Plots**, isolating each predictor’s relationship with longevity while controlling for all others.

**Key Observations**
- TV series display a consistently positive slope, confirming episodic retention effects
- Non-English titles cluster at higher longevity levels, supporting Netflix’s global localization strategy
- Weekly rank contributes incrementally, but far less than content format or language

---

### 🛠 Model Implementation (Python)

```python
import statsmodels.api as sm

X = df[['week', 'weekly_rank', 'category_TV', 'language_Non-English']]
X = sm.add_constant(X)
y = df['cumulative_weeks_in_top_10']

model = sm.OLS(y, X).fit()
print(model.summary())
```
<p align="center"> <img src="https://img.shields.io/badge/Model-OLS_Regression-E50914?style=flat-square" /> <img src="https://img.shields.io/badge/Confidence-95%25-green?style=flat-square" /> </p>
📊 Key Findings
🏎️ Drivers of Staying Power
Factor	Impact	Insight
TV Series Format	+2.19 weeks	Episodic structure encourages repeat engagement
Non-English Content	+2.01 weeks	International content benefits from global audience overlap
Weekly Rank	+0.09	Early popularity helps, but does not dominate

Insight:
Structural attributes (format & language) are stronger predictors of longevity than early ranking alone.

💡 Strategic Recommendations

Renewal Strategy: A mid-ranked Non-English TV series may outperform a high-ranked English film over time

Portfolio Mix: Increase investment in international episodic content to stabilize Top 10 churn

Global Partnerships: Prioritize creator pipelines in non-English markets to leverage long-tail demand

⚠️ Limitations & Future Work

Weekly rank is a proxy; future work should incorporate viewership hours

Marketing spend and social media sentiment were not modeled

Survival analysis could provide deeper time-to-exit insights

👥 Team

Edward Dai

Meghna Preme

Prakash Chinpattanakul

Alex Huang

Srinidhi Chevvuri

