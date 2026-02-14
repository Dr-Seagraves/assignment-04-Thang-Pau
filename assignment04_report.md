# Assignment 04 Interpretation Memo

**Student Name:** [Thang Pau]
**Date:** [ 2/13/2026]
**Assignment:** REIT Annual Returns and Predictors (Simple Linear Regression)

---

## 1. Regression Overview

You estimated **three** simple OLS regressions of REIT *annual* returns on different predictors:

| Model | Y Variable | X Variable | Interpretation Focus |
|-------|------------|------------|----------------------|
| 1 | ret (annual) | div12m_me | Dividend yield |
| 2 | ret (annual) | prime_rate | Interest rate sensitivity |
| 3 | ret (annual) | ffo_at_reit | FFO to assets (fundamental performance) |

For each model, summarize the key results in the sections below.

---

## 2. Coefficient Comparison (All Three Regressions)

**Model 1: ret ~ div12m_me**
- Intercept (β₀): 0.108196 (SE: 0.005987, p-value: 0.0000)
- Slope (β₁): -0.068682 (SE: 0.032495, p-value: 0.0346)
- R²: 0.0018 | N: 2527

**Model 2: ret ~ prime_rate**
- Intercept (β₀): 0.199799 (SE: 0.015764, p-value: 0.0000)
- Slope (β₁): -0.019449 (SE: 0.002998, p-value: 0.0000)
- R²: 0.0164 | N: 2527

**Model 3: ret ~ ffo_at_reit**
- Intercept (β₀): 0.097273 (SE: 0.009194, p-value: 0.0000)
- Slope (β₁): 0.577042 (SE: 0.567462, p-value: 0.3093)
- R²: 0.0004 | N: 2518

*Note: Model 3 may have fewer observations if ffo_at_reit has missing values; statsmodels drops those rows.*

---

## 3. Slope Interpretation (Economic Units)

**Dividend Yield (div12m_me):**
- A 1 percentage point increase in dividend yield (12-month dividends / market equity) is associated with a -0.068682 (approximately -6.87 percentage point) change in annual return.
- Higher dividend yield is associated with lower returns. This negative relationship may reflect that REITs with higher dividend yields are underperforming operationally.

**Prime Loan Rate (prime_rate):**
- A 1 percentage point increase in the year-end prime rate is associated with a -0.019449 (approximately -1.94 percentage point) change in annual return.
- Yes, the evidence suggests REIT returns are negatively sensitive to interest rates. Higher interest rates are associated with lower REIT returns.

**FFO to Assets (ffo_at_reit):**
- A 1 unit increase in FFO/Assets (fundamental performance) is associated with a 0.577042 (approximately 57.7 percentage point) change in annual return.
- The coefficient suggests more profitable REITs earn higher returns, but this relationship is not statistically significant, so we cannot conclude with confidence that performance drives returns.

---

## 4. Statistical Significance

For each slope, at the 5% significance level:
- **div12m_me:** Significant (p = 0.0346) — Higher dividend yields are significantly associated with lower annual returns.
- **prime_rate:** Significant (p = 0.0000) — Higher prime rates are significantly associated with lower annual returns with very strong statistical evidence.
- **ffo_at_reit:** Not significant (p = 0.3093) — There is insufficient evidence to conclude that FFO/Assets is related to annual returns.

**Which predictor has the strongest statistical evidence of a relationship with annual returns?** Prime rate has the strongest statistical evidence (p < 0.0001), followed by dividend yield (p = 0.0346).

---

## 5. Model Fit (R-squared)

Compare R² across the three models:
- Prime rate explains the most variation in returns, followed by dividend yield, and FFO/Assets. Overall, R² is very low across all three models, meaning that these individual predictors explain very little of the variation in annual REIT returns. This suggests that other factors are the primary drivers of REIT returns.

---

## 6. Omitted Variables

By using only one predictor at a time, we might be omitting:
- **Market conditions (e.g., S&P 500 returns):** REITs tend to move with broader market trends, and excluding market returns could bias our estimates.
- **Inflation rates:** Inflation affects both interest rates and real estate values, potentially confounding the prime rate relationship.
- **Property sector and geographic location:** Different REIT types (retail, residential, office) respond differently to economic conditions, and omitting these controls could bias firm-specific predictor effects.

**Potential bias:** For example, if prime rates are high during periods of strong economic growth (when returns are high for other reasons), omitting economic growth indicators could bias the prime rate coefficient. Similarly, high dividend yields might correlate with REIT sector distress, making it difficult to isolate the true effect of dividend policy from sector-specific shocks.

---

## 7. Summary and Next Steps

**Key Takeaway:**


**What we would do next:**
- Extend to multiple regression (include two or more predictors)
- Test for heteroskedasticity and other OLS assumption violations
- Examine whether relationships vary by time period or REIT sector

---

## Reproducibility Checklist
- [ ] Script runs end-to-end without errors
- [ ] Regression output saved to `Results/regression_div12m_me.txt`, `regression_prime_rate.txt`, `regression_ffo_at_reit.txt`
- [ ] Scatter plots saved to `Results/scatter_div12m_me.png`, `scatter_prime_rate.png`, `scatter_ffo_at_reit.png`
- [ ] Report accurately reflects regression results
- [ ] All interpretations are in economic units (not just statistical jargon)
