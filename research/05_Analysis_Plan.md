# Analysis Plan: Statistical Approach

**Document Created**: December 3, 2025
**Part of**: DRIVER Research Program
**Purpose**: Specify all statistical analyses for hypothesis testing and robustness checks
**Note**: This plan should be pre-registered before T2 data collection

---

## Part I: Analysis Overview

### 1.1 Analysis Phases

```
Phase 1: Data Preparation (Weeks 15-16)
├── Data cleaning and validation
├── Missing data assessment
├── Attrition analysis
└── Variable computation

Phase 2: Psychometric Validation (Week 17)
├── Confirmatory Factor Analysis
├── Reliability assessment
└── Measurement invariance

Phase 3: Descriptive Analysis (Week 17-18)
├── Sample characteristics
├── Balance assessment
├── Propensity score estimation

Phase 4: Primary Analyses (Week 18-19)
├── Main effects (H1)
├── Effect sizes and CIs
└── Sensitivity analyses

Phase 5: Mechanism Analyses (Week 19-20)
├── Mediation (H2)
├── Moderation (H3)
└── Trajectory analysis (H4)

Phase 6: Robustness Checks (Week 20-21)
├── Alternative specifications
├── Placebo tests
├── Subgroup analyses
```

### 1.2 Software

- **Primary**: R (version 4.3+)
  - `lavaan` for CFA and SEM
  - `lme4` for multilevel models
  - `MatchIt` for propensity score matching
  - `mediation` for causal mediation
  - `ggplot2` for visualization

- **Alternative**: Mplus (version 8+) for complex SEM models

---

## Part II: Data Preparation

### 2.1 Data Cleaning Protocol

**Step 1: Import and Merge**
```r
# Merge survey waves by participant ID
data_t0 <- read_csv("survey_t0.csv")
data_t1 <- read_csv("survey_t1.csv")
data_t2 <- read_csv("survey_t2.csv")
data_t3 <- read_csv("survey_t3.csv")

data_long <- bind_rows(
  data_t0 %>% mutate(time = 0),
  data_t1 %>% mutate(time = 1),
  data_t2 %>% mutate(time = 2),
  data_t3 %>% mutate(time = 3)
)

data_wide <- data_long %>%
  pivot_wider(id_cols = participant_id,
              names_from = time,
              values_from = everything())
```

**Step 2: Data Quality Checks**
- Flag cases with failed attention checks
- Identify straight-line responses (SD = 0 across scale)
- Flag impossible values (out of range)
- Identify unusually fast completion (< 5 min for any survey)

**Decision Rule**: Exclude cases with 2+ quality indicators; note in supplement.

**Step 3: Missing Data Assessment**
```r
# Assess missing data pattern
library(naniar)
vis_miss(data_wide)
mcar_test(data_wide)  # Little's MCAR test
```

**Decision Rules**:
- < 5% missing on any variable: Complete case analysis acceptable
- 5-20% missing: Multiple imputation (m = 20)
- > 20% missing: Assess for non-ignorable missingness; sensitivity analysis

### 2.2 Variable Computation

**Scale Scores**:
```r
# Example: AI Mental Model
data <- data %>%
  mutate(
    # Reverse code items
    mm_oracle1_r = 8 - mm_oracle1,  # Reverse scale
    mm_oracle5_r = 8 - mm_oracle5,

    # Compute subscales
    mm_oracle = rowMeans(select(., mm_oracle1_r, mm_oracle2:mm_oracle4, mm_oracle5_r)),
    mm_partner = rowMeans(select(., mm_partner1:mm_partner5)),
    mm_error = rowMeans(select(., mm_error1:mm_error5)),

    # Compute total
    mental_model_total = rowMeans(select(., mm_oracle, mm_partner, mm_error))
  )
```

**Composite Scores**:
```r
# AI Reliance Index (standardize components)
data <- data %>%
  mutate(
    query_freq_z = scale(query_frequency),
    early_consult_z = scale(early_consultation),
    solution_attr_z = scale(solution_attribution),

    ai_reliance_index = 0.3 * query_freq_z +
                        0.3 * early_consult_z +
                        0.4 * solution_attr_z
  )

# Capability Ratio
data <- data %>%
  mutate(
    capability_ratio = ipa_without_ai / ipa_with_ai,
    capability_ratio = ifelse(is.infinite(capability_ratio), NA, capability_ratio)
  )
```

### 2.3 Attrition Analysis

**Document attrition at each wave**:
```r
attrition_table <- data_long %>%
  group_by(time, condition) %>%
  summarise(
    n = n(),
    retention = n / n_baseline * 100
  )
```

**Test for differential attrition**:
```r
# Logistic regression predicting attrition
attrition_model <- glm(
  dropped_out ~ condition * gpa + condition * tech_exp + condition * gender,
  data = data_t0,
  family = binomial
)
summary(attrition_model)
```

**Decision Rule**: If differential attrition, include baseline predictors of attrition as covariates in all models.

---

## Part III: Psychometric Validation

### 3.1 Confirmatory Factor Analysis

**For Custom Scales** (AI Mental Model, Cognitive Dependency):

```r
library(lavaan)

# AI Mental Model: 3-factor model
mm_model <- '
  oracle =~ mm1 + mm2 + mm3 + mm4 + mm5
  partner =~ mm6 + mm7 + mm8 + mm9 + mm10
  error =~ mm11 + mm12 + mm13 + mm14 + mm15

  # Second-order factor
  mental_model =~ oracle + partner + error
'

mm_fit <- cfa(mm_model, data = data_t0,
              estimator = "MLR",  # Robust ML
              std.lv = TRUE)

summary(mm_fit, fit.measures = TRUE, standardized = TRUE)
```

**Fit Criteria**:
- CFI ≥ 0.95 (acceptable ≥ 0.90)
- TLI ≥ 0.95 (acceptable ≥ 0.90)
- RMSEA ≤ 0.06 (acceptable ≤ 0.08)
- SRMR ≤ 0.08

### 3.2 Measurement Invariance

**Test invariance across time** (for repeated measures):

```r
# Configural invariance (same factor structure)
config_model <- '
  mm_t0 =~ mm1_t0 + mm2_t0 + ...
  mm_t2 =~ mm1_t2 + mm2_t2 + ...
'

# Metric invariance (equal factor loadings)
metric_model <- '
  mm_t0 =~ a*mm1_t0 + b*mm2_t0 + ...
  mm_t2 =~ a*mm1_t2 + b*mm2_t2 + ...
'

# Scalar invariance (equal intercepts)
# Required for mean comparisons across time

# Compare models
anova(config_fit, metric_fit, scalar_fit)
```

**Decision Rule**: ΔCFI < 0.01 and ΔRMSEA < 0.015 indicates invariance holds.

### 3.3 Reliability Assessment

```r
library(psych)

# Cronbach's alpha
alpha(data[, mm_items])

# McDonald's omega (preferred)
omega(data[, mm_items])

# For multidimensional scales
omega(data[, mm_items], nfactors = 3)
```

**Targets**:
- α/ω ≥ 0.80 for primary outcomes
- α/ω ≥ 0.70 for subscales
- α/ω ≥ 0.65 minimum for exploratory measures

---

## Part IV: Balance and Matching

### 4.1 Pre-Matching Balance

```r
library(tableone)

balance_vars <- c("gpa", "tech_exp", "finance_exp", "tam_total",
                  "mental_model_t0", "deep_approach", "age", "gender")

table1 <- CreateTableOne(vars = balance_vars,
                         strata = "condition",
                         data = data)
print(table1, smd = TRUE)
```

**Imbalance Criteria**: |SMD| > 0.10 indicates meaningful imbalance.

### 4.2 Propensity Score Estimation

```r
library(MatchIt)

# Estimate propensity scores
ps_model <- glm(
  condition ~ gpa + tech_exp + finance_exp + tam_total +
              mental_model_t0 + deep_approach + age + gender,
  data = data,
  family = binomial
)

# Check overlap
data$pscore <- predict(ps_model, type = "response")
ggplot(data, aes(x = pscore, fill = factor(condition))) +
  geom_density(alpha = 0.5)
```

### 4.3 Matching

**Primary Approach: Nearest Neighbor 1:1**

```r
match_out <- matchit(
  condition ~ gpa + tech_exp + finance_exp + tam_total +
              mental_model_t0 + deep_approach + age + gender,
  data = data,
  method = "nearest",
  caliper = 0.2,  # Within 0.2 SD of propensity score
  ratio = 1
)

summary(match_out)
plot(match_out, type = "jitter")

matched_data <- match.data(match_out)
```

**Alternative Specifications** (for robustness):
- 1:2 matching
- Kernel matching
- Coarsened exact matching (CEM)
- Inverse probability weighting (IPW)

### 4.4 Post-Matching Balance

```r
# Verify balance improved
table1_matched <- CreateTableOne(vars = balance_vars,
                                 strata = "condition",
                                 data = matched_data)
print(table1_matched, smd = TRUE)
```

**Target**: All |SMD| < 0.10 after matching.

---

## Part V: Primary Analyses (H1)

### 5.1 Main Effects: ANCOVA

**Model Specification**:
```r
# H1a: AI Mental Model
model_mm <- lm(
  mental_model_t2 ~ condition + mental_model_t0 + gpa + tech_exp,
  data = matched_data
)

# H1b: Cognitive Capability
model_cap <- lm(
  ipa_score_t2 ~ condition + ipa_score_t0 + gpa + tech_exp,
  data = matched_data
)

# H1c: Cognitive Dependency (reverse scored so higher = less dependent)
model_dep <- lm(
  dependency_t2 ~ condition + dependency_t1 + gpa + tech_exp,
  data = matched_data
)
```

### 5.2 Difference-in-Differences

```r
# Long format for DiD
data_did <- matched_data %>%
  select(id, condition, mental_model_t0, mental_model_t2) %>%
  pivot_longer(cols = starts_with("mental_model"),
               names_to = "time",
               values_to = "mental_model") %>%
  mutate(post = ifelse(time == "mental_model_t2", 1, 0))

# DiD regression
did_model <- lm(
  mental_model ~ condition * post + gpa + tech_exp,
  data = data_did
)

# Coefficient on condition:post is DiD estimate
summary(did_model)
```

### 5.3 Effect Sizes

```r
library(effectsize)

# Cohen's d for group differences
cohens_d(mental_model_t2 ~ condition, data = matched_data)

# Standardized regression coefficient (β)
standardize_parameters(model_mm)

# R² change due to treatment
anova(
  lm(mental_model_t2 ~ mental_model_t0, data = matched_data),
  model_mm
)
```

**Interpretation Guidelines**:
- d = 0.20: Small
- d = 0.50: Medium
- d = 0.80: Large

### 5.4 Confidence Intervals

```r
# 95% CI for treatment effect
confint(model_mm, "condition", level = 0.95)

# Bootstrap CI (more robust)
library(boot)
boot_ci <- Boot(model_mm, R = 5000)
confint(boot_ci, type = "perc")
```

---

## Part VI: Mediation Analyses (H2)

### 6.1 Conceptual Models

**H2a**: DRIVER → Prompt Skills → AI Mental Model
**H2b**: DRIVER → Metacognition → Cognitive Capability
**H2c**: DRIVER → Critical Evaluation → Reduced Dependency

### 6.2 Structural Equation Model

```r
library(lavaan)

mediation_model <- '
  # Measurement models
  prompt_skills =~ ps1 + ps2 + ps3 + ps4
  metacognition =~ mc1 + mc2 + mc3 + mc4
  critical_eval =~ ce1 + ce2 + ce3 + ce4
  mental_model =~ mm1 + mm2 + mm3 + mm4

  # Structural paths
  prompt_skills ~ a1*condition
  metacognition ~ a2*condition
  critical_eval ~ a3*condition

  mental_model ~ b1*prompt_skills + b2*metacognition + c*condition
  capability ~ b3*metacognition + d*condition
  dependency ~ b4*critical_eval + e*condition

  # Indirect effects
  indirect_mm := a1*b1
  indirect_cap := a2*b3
  indirect_dep := a3*b4

  # Total effects
  total_mm := indirect_mm + c
'

med_fit <- sem(mediation_model, data = matched_data,
               estimator = "MLR",
               bootstrap = 5000)

summary(med_fit, fit.measures = TRUE, standardized = TRUE)
```

### 6.3 Causal Mediation Analysis

```r
library(mediation)

# Step 1: Mediator model
med_model <- lm(prompt_skills_t2 ~ condition + prompt_skills_t0,
                data = matched_data)

# Step 2: Outcome model
out_model <- lm(mental_model_t2 ~ condition + prompt_skills_t2 + mental_model_t0,
                data = matched_data)

# Step 3: Mediation analysis
med_out <- mediate(med_model, out_model,
                   treat = "condition",
                   mediator = "prompt_skills_t2",
                   boot = TRUE,
                   sims = 5000)

summary(med_out)
```

**Key Statistics**:
- ACME (Average Causal Mediation Effect)
- ADE (Average Direct Effect)
- Total Effect
- Proportion Mediated

---

## Part VII: Moderation Analyses (H3)

### 7.1 Interaction Models

**H3a**: Deep Learning Approach × DRIVER

```r
# Center moderator
matched_data$deep_c <- scale(matched_data$deep_approach, scale = FALSE)

# Interaction model
mod_model <- lm(
  mental_model_t2 ~ condition * deep_c + mental_model_t0,
  data = matched_data
)

summary(mod_model)

# Simple slopes
library(interactions)
sim_slopes(mod_model, pred = condition, modx = deep_c)
interact_plot(mod_model, pred = condition, modx = deep_c)
```

**H3b**: Tech Acceptance × DRIVER

```r
matched_data$tam_c <- scale(matched_data$tam_total, scale = FALSE)

mod_model_tam <- lm(
  mental_model_t2 ~ condition * tam_c + mental_model_t0,
  data = matched_data
)

# Johnson-Neyman analysis
johnson_neyman(mod_model_tam, pred = condition, modx = tam_c)
```

**H3c**: Prior Experience × DRIVER (Inverted-U)

```r
# Test quadratic moderation
matched_data$tech_exp_sq <- matched_data$tech_exp^2

mod_model_quad <- lm(
  mental_model_t2 ~ condition * tech_exp + condition * tech_exp_sq + mental_model_t0,
  data = matched_data
)
```

---

## Part VIII: Trajectory Analysis (H4)

### 8.1 Latent Growth Curve Model

```r
# Three timepoints: T0, T1, T2
lgcm_model <- '
  # Intercept and slope factors
  intercept =~ 1*mm_t0 + 1*mm_t1 + 1*mm_t2
  slope =~ 0*mm_t0 + 1*mm_t1 + 2*mm_t2

  # Predict growth factors from condition
  intercept ~ condition
  slope ~ condition

  # Residual variances
  mm_t0 ~~ e*mm_t0
  mm_t1 ~~ e*mm_t1
  mm_t2 ~~ e*mm_t2
'

lgcm_fit <- growth(lgcm_model, data = matched_data)
summary(lgcm_fit, fit.measures = TRUE)
```

### 8.2 Testing Nonlinear Trajectories

```r
# Quadratic growth model
lgcm_quad <- '
  intercept =~ 1*mm_t0 + 1*mm_t1 + 1*mm_t2
  slope =~ 0*mm_t0 + 1*mm_t1 + 2*mm_t2
  quad =~ 0*mm_t0 + 1*mm_t1 + 4*mm_t2

  intercept ~ condition
  slope ~ condition
  quad ~ condition
'

# Compare linear vs quadratic
anova(lgcm_fit, lgcm_quad_fit)
```

### 8.3 Growth Mixture Modeling (Exploratory)

```r
library(tidyLPA)

# Identify distinct trajectory classes
profiles <- matched_data %>%
  select(mm_t0, mm_t1, mm_t2) %>%
  estimate_profiles(n_profiles = 1:4,
                    models = 1)

compare_solutions(profiles, statistics = c("AIC", "BIC", "Entropy"))
```

---

## Part IX: Robustness Checks

### 9.1 Alternative Matching Specifications

```r
# 1:2 Matching
match_1_2 <- matchit(..., ratio = 2)

# Kernel matching
match_kernel <- matchit(..., method = "full")

# CEM
match_cem <- matchit(..., method = "cem")

# Re-run primary analyses with each specification
# Report if results differ meaningfully
```

### 9.2 Sensitivity Analysis

```r
library(sensemakr)

# Sensitivity to unobserved confounding
sensitivity <- sensemakr(model_mm,
                         treatment = "condition",
                         benchmark_covariates = "gpa")

summary(sensitivity)
plot(sensitivity)
```

**Report**: "How strong would an unobserved confounder need to be to explain away the treatment effect?"

### 9.3 Placebo Tests

```r
# Test for pre-treatment differences
placebo_model <- lm(
  mental_model_t0 ~ condition + gpa + tech_exp,
  data = matched_data
)

# Should find NO significant effect of condition
summary(placebo_model)
```

### 9.4 Subgroup Analyses

```r
# By major
results_finance <- filter(matched_data, major == "Finance") %>%
  lm(mental_model_t2 ~ condition + mental_model_t0, data = .)

results_other <- filter(matched_data, major != "Finance") %>%
  lm(mental_model_t2 ~ condition + mental_model_t0, data = .)

# By baseline capability
results_high <- filter(matched_data, ipa_t0 >= median(ipa_t0)) %>%
  lm(mental_model_t2 ~ condition + mental_model_t0, data = .)

results_low <- filter(matched_data, ipa_t0 < median(ipa_t0)) %>%
  lm(mental_model_t2 ~ condition + mental_model_t0, data = .)
```

### 9.5 Multiple Comparison Correction

```r
# Family-wise error rate correction
# For 3 primary outcomes:
alpha_corrected <- 0.05 / 3  # Bonferroni

# Or FDR correction
p_values <- c(p_mm, p_cap, p_dep)
p.adjust(p_values, method = "BH")  # Benjamini-Hochberg
```

---

## Part X: Power Analysis Results

### 10.1 Achieved Power

```r
library(pwr)

# Post-hoc power for observed effect size
# Example: observed d = 0.45 with N = 150
pwr.t.test(d = 0.45, n = 75, sig.level = 0.05)
```

### 10.2 Minimum Detectable Effect

```r
# With actual N, what's the smallest effect we can detect?
pwr.t.test(n = 75, sig.level = 0.05, power = 0.80)
```

---

## Part XI: Tables and Figures

### 11.1 Required Tables

1. **Table 1**: Sample characteristics by condition (demographics, baseline measures)
2. **Table 2**: Balance before and after matching (SMDs)
3. **Table 3**: Scale reliability and validity (α, ω, CFA fit)
4. **Table 4**: Primary outcome results (coefficients, SEs, 95% CIs, effect sizes)
5. **Table 5**: Mediation results (indirect, direct, total effects)
6. **Table 6**: Moderation results (interaction coefficients, simple slopes)
7. **Table 7**: Robustness checks (alternative specifications)

### 11.2 Required Figures

1. **Figure 1**: Conceptual model with hypotheses
2. **Figure 2**: Propensity score distributions (overlap)
3. **Figure 3**: Mean outcome trajectories by condition
4. **Figure 4**: Mediation path diagram with coefficients
5. **Figure 5**: Moderation plots (simple slopes)
6. **Figure 6**: Forest plot of effect sizes across outcomes

---

## Part XII: Reporting Standards

### 12.1 JARS (APA Journal Article Reporting Standards)

For quasi-experimental studies, report:
- Sample size determination
- Participant flow diagram
- Balance on measured confounders
- Sensitivity to unmeasured confounding
- Effect sizes with confidence intervals

### 12.2 Pre-Registration

**Pre-register on OSF** before T2 data collection:
- Hypotheses
- Analysis plan (this document)
- Decision rules for modifications
- Criteria for exploratory vs. confirmatory

### 12.3 Data Availability

- De-identified data available on OSF
- Analysis code available on GitHub
- Supplementary materials with full results

---

## Summary: Analysis Checklist

### Before Analysis
- [ ] Data cleaning complete
- [ ] Missing data handled
- [ ] Attrition analyzed
- [ ] Scales validated (CFA)
- [ ] Measurement invariance tested
- [ ] Matching conducted
- [ ] Balance verified

### Primary Analyses
- [ ] H1a: Mental Model (ANCOVA/DiD)
- [ ] H1b: Cognitive Capability (ANCOVA/DiD)
- [ ] H1c: Cognitive Dependency (ANCOVA/DiD)
- [ ] Effect sizes calculated
- [ ] Confidence intervals computed

### Mechanism Analyses
- [ ] H2a: Prompt Skills mediation
- [ ] H2b: Metacognition mediation
- [ ] H2c: Critical Evaluation mediation
- [ ] H3a: Deep Learning moderation
- [ ] H3b: Tech Acceptance moderation
- [ ] H3c: Prior Experience moderation (inverted-U)
- [ ] H4: Trajectory analysis

### Robustness
- [ ] Alternative matching specifications
- [ ] Sensitivity to unobserved confounding
- [ ] Placebo tests
- [ ] Subgroup analyses
- [ ] Multiple comparison correction

### Reporting
- [ ] All tables complete
- [ ] All figures complete
- [ ] JARS compliance checked
- [ ] Pre-registration updated with results

---

**Document Version:** 1.0
**Last Updated:** December 3, 2025
**Next Document:** 06_Publication_Strategy.md
