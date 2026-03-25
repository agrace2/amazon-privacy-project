# Amazon Shopping Behavior and Privacy Attitudes

Analyzing whether shopping habits predict privacy concern using logistic regression on 5,000+ users.

---

## Executive Summary

**Key Finding:** Heavy spenders are 15% less likely to be privacy-conscious (OR=0.85, p<0.001). This counter-intuitive result suggests users who are deeply invested in a platform accept privacy trade-offs for convenience.

**Business Implication:** Privacy messaging should target light/casual users, not heavy spenders. Simple spending-based segmentation is effective; complex behavioral profiling is not needed.

**Method:** Logistic regression on 5,027 Amazon users with demographic controls. Model R²=0.02, which is low but expected for behavioral data.

---

## Research Question

**Main Question:**  
What predicts whether Amazon customers are willing to allow the company to sell their purchase data?

**Specific Hypotheses:**
1. Does total spending predict privacy attitudes?
2. Do people who buy sensitive products (health, beauty) care more about privacy?
3. Does shopping across many categories matter?
4. Does purchase recency matter?

---

## Data

**Source:** Harvard Dataverse - Open e-commerce 1.0 dataset

**What's included:**
- 5,027 survey respondents 
- 1.8 million Amazon transactions
- Privacy attitudes (willing vs unwilling to allow data sales)
- Demographics (age, income, education)

---

## Methodology

**Approach:**
- Logistic regression (statsmodels in Python)
- Progressive model building (5 models testing each hypothesis)
- Controlled for age, education, income
- Standardized variables to fix multicollinearity

**Features created:**
- Total spending (log-transformed and standardized)
- Sensitive purchases flag (health/beauty/personal care)
- Number of product categories
- Days since last purchase

---

## Results

| Variable | Odds Ratio | p-value | Result |
|----------|-----------|---------|--------|
| Total spending | 0.85 | <0.001 | **Significant** - Heavy spenders less privacy-conscious |
| Sensitive purchases | 1.20 | 0.061 | Marginal effect |
| Purchase diversity | 1.00 | 0.003 | No meaningful effect |
| Purchase recency | 1.00 | 0.089 | Not significant |

**Model fit:** McFadden R² = 0.021, AIC = 6,755, n = 5,027

---

## Key Insights

**What matters:**
- Spending amount is the only meaningful predictor
- Heavy spenders have accepted the privacy-convenience trade-off

**What doesn't matter:**
- How many categories you shop
- When you last made a purchase
- Sensitive purchases show weak signal but not statistically significant

**Business recommendation:**
- Segment privacy messaging by spending level
- Target privacy protections to new/light users
- Heavy users don't need extensive privacy messaging

---

## Limitations

- Cross-sectional data (can't prove causality)
- Low R² - many unmeasured factors affect privacy attitudes
- Self-reported attitudes may differ from actual behavior
- Sample from Harvard study may not represent all Amazon users

---

## Project Files

```
├── amazon_privacy_multifactor_analysis.ipynb    # Complete analysis
├── README.md                                     # This file
└── requirements.txt                              # Dependencies
```

Data files not included - download from [Harvard Dataverse](https://dataverse.harvard.edu/dataset.xhtml?persistentId=doi:10.7910/DVN/YGLYDY)

---

## How to Run

```bash
git clone https://github.com/agrace2/amazon-privacy-analysis.git
cd amazon-privacy-analysis
pip install -r requirements.txt
jupyter notebook amazon_privacy_multifactor_analysis.ipynb
```

Download `survey.csv` and `amazon-purchases.csv` from the Harvard Dataverse link above.

---

## Tools Used

Python • Pandas • Statsmodels • Matplotlib • Seaborn • Jupyter
