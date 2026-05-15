# EXAM BIBLE: Statistics & Econometrics (70 Marks)

## 1. COURSE MAP

**Module Structure:**
- **OLS Regression Fundamentals** (Lectures 1-3): Core estimation framework
- **Hypothesis Testing** (Lectures 3-4): t-tests, F-tests, model comparison
- **Multiple Regression Issues** (Lecture 5): Multicollinearity, omitted variable bias, heteroskedasticity
- **Discrete Dependent Variables** (Lectures 6-7): Linear probability, logit, probit models
- **Time-Series Analysis** (Lectures 8-9): AR models, stationarity, unit roots
- **Advanced Time-Series** (Lecture 10): ARCH/GARCH models, volatility
- **Panel Data & Policy Evaluation** (Lecture 11): Fixed effects, random effects, difference-in-differences

## 2. 70-MARK EXAM PRIORITY MAP

| Topic | Est. Marks | Question Types |
|-------|-----------|-----------------|
| OLS Estimation & Interpretation | 12 | Derive estimate, interpret coefficient |
| Hypothesis Testing (t, F tests) | 10 | Conduct test, reject/fail to reject, p-value |
| Multicollinearity & OVB | 8 | Identify problem, explain bias direction |
| Multiple Regression Output | 10 | Read Stata output, calculate SE, test |
| Discrete DV Models (logit/probit) | 8 | Setup likelihood, interpret marginal effect |
| Time-Series (AR, stationarity) | 12 | ACF/PACF, augmented Dickey-Fuller test |
| ARCH/GARCH | 5 | Volatility modeling |
| Panel Data (FE/RE) | 10 | Hausman test, choose estimator |
| Difference-in-Differences | 5 | DiD setup, parallel trends assumption |
| **TOTAL** | **70** | Mix of theory, calculation, interpretation |

## 3. EXAM PHRASES TABLE

| Phrase | Interpretation | Action |
|--------|-----------------|--------|
| "Construct a 95% confidence interval" | Use: point est ± 1.96×SE | Calculate t-critical for small samples |
| "Test at 5% significance level" | Use α=0.05, two-tailed (unless stated) | Compare |t-stat| to 1.96 or p-value to 0.05 |
| "Estimate the model by OLS" | Run regression, report coefficients | Include standard errors and R² |
| "Is the coefficient significant?" | Check p-value < 0.05 (or given α) | If yes: coefficient ≠ 0 at significance level |
| "What is the economic significance?" | Interpret point estimate magnitude | "One unit increase in X → β unit change in Y" |
| "Discuss potential endogeneity" | Identify reverse causality or omitted variable | Suggest IV or control variable solution |
| "Assume errors are i.i.d. N(0,σ²)" | Errors: independent, identically distributed, normal | Justifies t-test and confidence intervals |
| "Compare two models using F-test" | H₀: restricted model correct | F = (SSR_r - SSR_u)/q / (SSR_u/(n-k-1)) |

## 4. FORMULA BANK

### OLS Estimation
**Beta hat (slope):** β̂ = Σ(Xᵢ - X̄)(Yᵢ - Ȳ) / Σ(Xᵢ - X̄)²
**Standard Error:** SE(β̂) = σ̂ / √Σ(Xᵢ - X̄)²; where σ̂² = SSR/(n-2)
**t-statistic:** t = β̂ / SE(β̂)
**R²:** R² = 1 - SSR/SST = (TSS - SSR) / TSS

### Hypothesis Testing
**F-statistic (overall):** F = (TSS - SSR)/k / (SSR/(n-k-1)) ~ F(k, n-k-1)
**F-test restricted vs unrestricted:** F = (SSR_r - SSR_u)/q / (SSR_u/(n-k-1)) ~ F(q, n-k-1)
**Confidence Interval:** β̂ ± t_{α/2,n-k-1} × SE(β̂)

### Multiple Regression Issues
**Multicollinearity VIF:** VIF_j = 1 / (1 - R²_j) where R²_j = R² from regressing Xⱼ on other X's
**Omitted Variable Bias:** β̂ ≈ β + δ × corr(X, Z) where δ = effect of omitted Z on Y
**Heteroskedasticity-robust SE:** Use White standard errors in Stata

### Discrete Dependent Variables
**Linear Probability Model:** P(Y=1|X) = β₀ + β₁X (issues: predicted probs outside [0,1])
**Logit:** P(Y=1|X) = exp(β₀ + β₁X) / (1 + exp(β₀ + β₁X))
**Probit:** P(Y=1|X) = Φ(β₀ + β₁X) where Φ = standard normal CDF
**Marginal Effect (Logit):** dP/dX = β × P(1-P)

### Time-Series Models
**AR(1):** Yₜ = ρYₜ₋₁ + εₜ (stationary if |ρ| < 1)
**Augmented Dickey-Fuller:** ΔYₜ = γYₜ₋₁ + Σ φᵢΔYₜ₋ᵢ + εₜ; H₀: γ=0 (unit root)
**ARCH(1):** σₜ² = ω + αεₜ₋₁²

### Panel Data
**Fixed Effects:** Yᵢₜ = αᵢ + β₁Xᵢₜ + εᵢₜ (within-transformation removes αᵢ)
**Random Effects:** Yᵢₜ = α + β₁Xᵢₜ + αᵢ* + εᵢₜ where αᵢ* ~ N(0, σ²_α)
**Hausman Test:** H₀: RE consistent (no correlation between αᵢ and X); test: (β̂_FE - β̂_RE)'Var⁻¹(β̂_FE - β̂_RE)

## 5. CALCULATION TEMPLATES

### Template 1: Simple OLS Regression
Given: n=25, ΣXᵢYᵢ=800, ΣXᵢ=100, ΣYᵢ=150, X̄=4, Ȳ=6, ΣXᵢ²=500

**Step 1:** Calculate slope: β̂ = [ΣXᵢYᵢ - nX̄Ȳ] / [ΣXᵢ² - nX̄²] = [800 - 25×4×6] / [500 - 25×16] = [800-600]/[500-400] = 200/100 = 2

**Step 2:** Calculate intercept: α̂ = Ȳ - β̂X̄ = 6 - 2×4 = -2

**Step 3:** Fitted model: Ŷ = -2 + 2X

**Step 4:** Calculate SSR: SSR = ΣYᵢ² - nȲ² - β̂²(ΣXᵢ² - nX̄²) [compute via residuals if needed]

### Template 2: T-Test for Coefficient Significance
Given: β̂ = 0.5, SE(β̂) = 0.2, n=30

**Step 1:** Calculate t-statistic: t = 0.5/0.2 = 2.5
**Step 2:** Critical value: t_{0.025,28} ≈ 2.048 (two-tailed, 5% level)
**Step 3:** Decision: |2.5| > 2.048 → Reject H₀: β=0 → Coefficient is statistically significant
**Step 4:** Confidence interval: 0.5 ± 2.048×0.2 = 0.5 ± 0.41 = [0.09, 0.91]

### Template 3: F-Test (Restricted vs Unrestricted)
Given: SSR_restricted=150, SSR_unrestricted=120, q=2 (restrictions), n=50, k=4 (unrestricted)

**Step 1:** Calculate F-statistic: F = (150-120)/2 / (120/45) = 30/2 / 2.67 = 15/2.67 = 5.62
**Step 2:** Critical value: F_{0.05,2,45} ≈ 3.20
**Step 3:** Decision: 5.62 > 3.20 → Reject H₀ (restricted model) → Unrestricted model better

## 6. MCQ TRAP BANK

**Trap 1: Sign of Omitted Variable Bias**
*False statement:* "If Z is omitted and corr(X,Z)>0, then β̂ is always upward biased"
*Truth:* Direction depends on: bias = correlation(X,Z) × effect_of_Z_on_Y; need both effects

**Trap 2: Multicollinearity**
*False:* "High multicollinearity makes OLS estimates biased"
*Truth:* High VIF makes SEs large and t-stats small, but β̂ remains unbiased

**Trap 3: R² interpretation**
*False:* "R² > 0.8 means the model is correctly specified"
*Truth:* R² only measures fit; omitted variables or wrong functional form still problematic

**Trap 4: Heteroskedasticity**
*False:* "Heteroskedasticity causes biased OLS coefficients"
*Truth:* OLS remains unbiased but SEs are wrong; use robust SEs

**Trap 5: Stationarity & Differencing**
*False:* "If ADF test p-value = 0.06, series is non-stationary"
*Truth:* At 5% level, fail to reject H₀ (unit root); borderline—check robustness

**Trap 6: Logit Coefficient Interpretation**
*False:* "β₁ = 0.5 in logit means Y increases by 0.5 units when X increases by 1"
*Truth:* β₁ = 0.5 is log-odds coefficient; marginal effect = 0.5×P(Y=1)×P(Y=0)

## 7. REGRESSION INTERPRETATION TEMPLATES

### Template A: Two-Variable OLS
*"Ŷ = 50 + 0.8X, R²=0.72, SE(β̂)=0.1, n=100"*

**Interpretation:** 
- **Intercept:** Predicted Y = 50 when X = 0
- **Slope:** 1-unit increase in X → 0.8-unit increase in Y (holding other factors constant)
- **Significance:** t = 0.8/0.1 = 8 → Highly significant (p < 0.001)
- **Fit:** 72% of Y variation explained by X
- **Confidence interval:** 0.8 ± 1.96×0.1 = [0.604, 0.996] (95% CI)

### Template B: Multiple Regression with Control Variables
*"Ŷ = 20 + 5X₁ + 2X₂ - 0.1X₃"*

**Interpretation:**
- **X₁ effect:** 5-unit increase in Y per X₁ unit, **holding X₂ and X₃ constant**
- **Ceteris paribus:** Each coefficient isolates the effect of that variable alone
- **X₃ effect:** Negative; 1-unit increase in X₃ → 0.1-unit decrease in Y (negative relationship)

### Template C: Logarithmic Specification
*"ln(Y) = 2 + 0.5ln(X)"*

**Interpretation:** 1% increase in X → 0.5% increase in Y (elasticity = 0.5)

### Template D: Log-Linear
*"ln(Y) = 3 + 0.02X"*

**Interpretation:** 1-unit increase in X → 2% increase in Y (semi-elasticity = 0.02)

## 8. ASSUMPTION DECISION TREE

```
START: Multiple Regression Assumptions

1. E(ε|X) = 0 (zero conditional mean)?
   → If NO → Endogeneity problem; consider IV, lagged dependent variables
   → If YES → Continue

2. Errors i.i.d.?
   → If autocorrelated → Newey-West SEs; re-estimate model
   → If heteroskedastic → Robust (White) SEs
   → If YES → Continue

3. No multicollinearity (VIF < 10)?
   → If NO → Drop/combine highly correlated X; PCA; accept larger SEs
   → If YES → Continue

4. X variables exogenous?
   → If NO (reverse causality, omitted Z) → Use IV; add controls
   → If YES → Continue

5. Errors ~ N(0,σ²)?
   → For large n: justified by CLT (less critical)
   → For small n: test normality; use robust SEs if violated
   → If YES → Proceed with t-tests, F-tests

6. Correct functional form?
   → Test: RESET test; add nonlinear terms
   → If NO → Transform X or Y; add interaction terms
```

## 9. MODEL COMPARISON TABLES

### Discrete Dependent Variable Models

| Feature | Linear Prob. | Logit | Probit |
|---------|-------------|-------|--------|
| **Functional form** | β₀ + β₁X | Logistic CDF | Normal CDF |
| **Predicted prob range** | (-∞, ∞) | [0,1] | [0,1] |
| **Issue** | Probs outside [0,1] | Heavier tails | Standard choice |
| **Interpretation** | Direct effect | Coefficient: log-odds | Similar to logit |
| **Marginal effect** | β₁ (constant) | β₁×P(1-P) | β₁×φ(β₀+β₁X) |
| **When to use** | Rarely (simple but wrong) | Common in econometrics | Robustness check |

### Time-Series Models

| Model | Equation | Stationarity | Application |
|-------|----------|--------------|-------------|
| **White noise** | εₜ ~ N(0,σ²) | Stationary | Residuals should be WN |
| **AR(1)** | Yₜ = ρYₜ₋₁ + εₜ | \|ρ\|<1 | Autocorrelated series |
| **Random walk** | Yₜ = Yₜ₋₁ + εₜ | Non-stationary (ρ=1) | Stock prices, exchange rates |
| **ARCH(1)** | σₜ² = ω + αεₜ₋₁² | Volatility persistence | Asset returns |
| **GARCH(1,1)** | σₜ² = ω + αεₜ₋₁² + βσₜ₋₁² | Mean-reverting volatility | Long-memory volatility |

### Panel Data Estimators

| Estimator | Assumption | Pros | Cons |
|-----------|-----------|------|------|
| **Pooled OLS** | αᵢ uncorrelated with X | Simple, efficient if valid | Biased if αᵢ correlated with X |
| **Fixed Effects** | αᵢ correlated with X (allowed) | Controls for all time-invariant unobservables | Drops time-invariant X; smaller SEs |
| **Random Effects** | αᵢ ~ N(0,σ²_α) uncorrelated with X | Efficient; uses both within & between variation | Biased if assumption violated |
| **Use Hausman Test** | H₀: RE consistent | — | Reject H₀ → Use FE; fail to reject → RE is OK |

## 10. EXAM ANSWER TEMPLATES

### Answer Template: "Explain omitted variable bias"
**Structure:**
1. **Definition:** OVB occurs when a relevant variable Z is excluded from regression; β̂ on X mixes effect of X with effect of Z
2. **Condition:** OVB = 0 if (a) Z truly has no effect on Y, OR (b) Z uncorrelated with X
3. **Direction:** Sign(OVB) = Sign[corr(X,Z)] × Sign[effect of Z on Y]
4. **Example:** If Y=wage, X=education, Z=ability; Z unobserved but corr(X,Z)>0 and effect of Z on Y>0 → β̂_X is **upward biased**
5. **Solution:** Add Z if available; use IV; or discuss direction and magnitude

### Answer Template: "Conduct an F-test to compare two models"
**Structure:**
1. **Null hypothesis:** H₀: Coefficients of excluded variables = 0 (restricted model is correct)
2. **Test statistic:** F = (SSR_r - SSR_u)/q / (SSR_u/(n-k-1)) where q = # restrictions
3. **Distribution:** F ~ F(q, n-k-1)
4. **Decision rule:** If F > F_c (critical value at α level), reject H₀; unrestricted model better
5. **Interpretation:** If reject, additional variables improve fit significantly

### Answer Template: "Interpret logit output β₁ = 0.4"
**Structure:**
1. **Log-odds:** 0.4 is the coefficient on the log-odds scale
2. **Odds ratio:** exp(0.4) ≈ 1.49; one unit increase in X → odds of Y=1 increase by 49%
3. **Marginal effect:** dP/dX = 0.4 × P(Y=1) × [1 - P(Y=1)]; depends on X value
4. **At mean X:** If P(Y=1|X̄) = 0.5, then marginal effect = 0.4×0.5×0.5 = 0.10 (1-unit increase in X → 10 pp increase in probability)

### Answer Template: "Diagnose and fix heteroskedasticity"
**Structure:**
1. **Diagnosis:** Plot residuals vs fitted values; Breusch-Pagan test; White test
2. **Consequence:** OLS coefficients unbiased but SEs wrong → t-stats, confidence intervals invalid
3. **Solution:** Use heteroskedasticity-robust (White) standard errors
4. **In practice:** In Stata: `reg Y X, robust`
5. **If severe:** Consider WLS or log-transform if heteroskedasticity proportional to X

## 11. MOCK EXAM (70 Marks)

**SECTION A: Short Answer (30 marks)**

**Q1** (6 marks): You estimate Ŷ = 10 + 2X with SE(β̂)=0.5, n=50. 
  a) Construct a 95% confidence interval for the slope. (3 marks)
  b) At 5% significance, is the slope significant? Explain. (3 marks)

**Q2** (6 marks): A researcher omits ability (Z) from a wage equation where Y=wage, X=education. 
  a) Under what conditions is there OVB? (2 marks)
  b) If corr(education,ability)=0.6 and ability increases wages by 2 units, what is direction and approximate magnitude of bias? (4 marks)

**Q3** (6 marks): Explain why high multicollinearity is problematic. Does it bias OLS estimates? (6 marks)

**Q4** (6 marks): You have a logit model with coefficient β₁=0.5 on ln(income). 
  a) Interpret this coefficient. (2 marks)
  b) Calculate marginal effect at P(Y=1)=0.3. (4 marks)

**Q5** (6 marks): Describe the ADF test for unit roots. What does rejection imply? (6 marks)

**SECTION B: Calculation Problems (25 marks)**

**Q6** (8 marks): Conduct an F-test comparing models.
  Restricted: Y = α + β₁X₁ + ε; SSR = 200
  Unrestricted: Y = α + β₁X₁ + β₂X₂ + β₃X₃ + ε; SSR = 150
  n=60, α=0.05. Should you reject the restricted model? (8 marks)

**Q7** (8 marks): Panel data: 100 firms, 10 years. Hausman test statistic = 15.2 with 3 degrees of freedom.
  At 5% level, should you use FE or RE? (Critical value: χ²(3)=7.81) (8 marks)

**Q8** (9 marks): Given regression table, answer:
  ```
  Variable | Coefficient | Std. Error | t-stat | p-value
  Constant | 5.2         | 1.0        | 5.2    | 0.000
  X1       | 2.1         | 0.5        | 4.2    | 0.001
  X2       | -0.3        | 0.15       | -2.0   | 0.062
  ```
  a) Interpret β₁ coefficient. (2 marks)
  b) Is X2 significant at 5% level? At 10%? (3 marks)
  c) What is the predicted Y when X1=2, X2=1? (2 marks)
  d) Discuss model adequacy based on this output. (2 marks)

**SECTION C: Essays (15 marks)**

**Q9** (7 marks): Compare FE and RE panel estimators. Under what conditions should each be used? (7 marks)

**Q10** (8 marks): Explain difference-in-differences estimation. Include: (a) setup with treatment/control groups, (b) parallel trends assumption, (c) DiD estimator interpretation. (8 marks)

---

**Total: 70 marks**  
*Suggested Time Allocation: 15 min (Section A), 25 min (Section B), 20 min (Section C)*

