# Research Design: Methodology and Identification

**Document Created**: December 3, 2025
**Part of**: DRIVER Research Program
**Purpose**: Establish methodological rigor for causal inference

---

## Preamble: The Methodological Challenge

DRIVER research faces a common challenge in educational research: we cannot randomly assign students to courses. Students self-select based on:
- Schedule preferences
- Instructor reputation
- Course description interpretation
- Peer recommendations

This creates potential selection bias: students who choose DRIVER sections may differ systematically from those who don't. Any outcome differences might reflect these pre-existing differences rather than intervention effects.

This document addresses this challenge with:
1. The strongest feasible identification strategy
2. Multiple robustness checks
3. Design features that strengthen causal inference
4. Transparency about limitations

---

## Part I: Research Design Overview

### 1.1 Design Type

**Primary Design**: Quasi-experimental longitudinal study with comparison group

**Design Classification**: Pre-test/post-test with nonequivalent comparison group

**Timeline**:
- T0 (Week 1): Baseline
- T1 (Week 7): Mid-intervention
- T2 (Week 14): Post-intervention
- T3 (+6 months): Follow-up

### 1.2 Study Arms

| Arm | Description | N (Target) |
|-----|-------------|------------|
| Treatment | DRIVER Financial Management course | 100-150 |
| Comparison | Traditional Financial Management course | 100-150 |

**Same Content, Different Method**: Both arms cover the same financial management curriculum (time value of money, valuation, portfolio theory, capital budgeting). The difference is pedagogical approach:

| Feature | DRIVER | Traditional |
|---------|--------|-------------|
| AI Integration | Structured, central | Permitted, peripheral |
| Framework | DRIVER methodology | Conventional instruction |
| Assessment | Video presentations | Exams and problem sets |
| Peer Learning | Structured partner activities | Ad hoc |

### 1.3 Design Diagram

```
     T0              T1              T2              T3
   (Week 1)       (Week 7)       (Week 14)      (+6 months)
      │               │               │               │
      ▼               ▼               ▼               ▼
┌─────────────────────────────────────────────────────────────┐
│                      TREATMENT (DRIVER)                      │
│  O₁ ─────────── X ─────────── O₂ ─────────── O₃ ─────── O₄  │
│  Baseline       Intervention    Post           Follow-up     │
└─────────────────────────────────────────────────────────────┘
                              vs.
┌─────────────────────────────────────────────────────────────┐
│                    COMPARISON (Traditional)                  │
│  O₁ ─────────── - ─────────── O₂ ─────────── O₃ ─────── O₄  │
│  Baseline       No DRIVER       Post           Follow-up     │
└─────────────────────────────────────────────────────────────┘

O = Observation/measurement
X = DRIVER intervention
- = Traditional instruction (no DRIVER)
```

---

## Part II: Identification Strategy

### 2.1 The Fundamental Problem

We want to estimate:
**τ = E[Y(1) - Y(0)]**

Where:
- Y(1) = outcome with DRIVER treatment
- Y(0) = outcome without DRIVER treatment

But we observe each student in only one condition. The comparison group provides estimates of Y(0) for treated students, but only if the groups are comparable.

### 2.2 Primary Strategy: Propensity Score Matching + Difference-in-Differences

**Step 1: Propensity Score Estimation**

Estimate probability of selecting DRIVER section based on observable characteristics:

```
P(DRIVER = 1 | X) = logit(β₀ + β₁GPA + β₂Major + β₃TechExp + β₄AIAttitude + β₅Year + ε)
```

Matching variables:
- **Prior GPA**: Academic capability
- **Major**: Domain interest/requirements
- **Tech Experience**: Self-reported prior AI/coding experience
- **AI Attitude**: Baseline technology acceptance (TAM)
- **Year in School**: Stage of program

**Step 2: Matching**

For each DRIVER student, identify comparison students with similar propensity scores.

Options (in order of preference):
1. **Nearest neighbor matching** (1:1 or 1:k)
2. **Caliper matching** (restrict distance)
3. **Kernel matching** (weighted average)

Assess balance using:
- Standardized mean differences (target < 0.1)
- Variance ratios (target 0.8-1.25)
- Visual inspection of propensity score distributions

**Step 3: Difference-in-Differences**

Even with matched samples, time-invariant unobservables may differ. DiD controls for these:

```
Y_it = α + β₁(DRIVER_i) + β₂(Post_t) + β₃(DRIVER_i × Post_t) + γX_i + ε_it
```

Where:
- Y_it = outcome for student i at time t
- DRIVER_i = treatment indicator
- Post_t = post-intervention indicator
- β₃ = **treatment effect** (coefficient of interest)
- X_i = covariates

**Key Assumption**: Parallel trends in absence of treatment

### 2.3 Identification Assumptions

**Assumption 1: Conditional Independence (Unconfoundedness)**
> Given observed covariates, treatment assignment is independent of potential outcomes.
> P(DRIVER | X, Y(0), Y(1)) = P(DRIVER | X)

**Testable Implications**:
- Balance on observables after matching
- Placebo tests on pre-treatment outcomes

**Assumption 2: Common Support (Overlap)**
> For all values of covariates, both treatment and comparison are possible.
> 0 < P(DRIVER = 1 | X) < 1

**Verification**:
- Inspect propensity score distributions
- Trim sample to common support region

**Assumption 3: Parallel Trends (for DiD)**
> In absence of treatment, treatment and comparison groups would have followed parallel outcome trajectories.

**Testable Implications**:
- If multiple pre-treatment periods available, test parallel pre-trends
- Placebo treatment timing tests

**Assumption 4: No Spillovers (SUTVA)**
> Treatment of one unit doesn't affect outcomes of others.

**Potential Violations**:
- Students in different sections may interact
- AI tools used by DRIVER students may benefit comparison students

**Mitigation**:
- Measure and control for cross-section interaction
- Document any information sharing

### 2.4 Alternative Identification Strategies

If primary strategy faces challenges, consider:

**Alternative 1: Regression Discontinuity (if applicable)**
If section assignment has any threshold-based component (e.g., registration timing, waitlist order), exploit discontinuity.

**Alternative 2: Instrumental Variables**
Potential instruments:
- Distance to campus (if sections at different times)
- Schedule conflicts with other courses
- Advisor recommendations (if documented)

**Alternative 3: Bounds Analysis**
Following Manski (1990), estimate bounds on treatment effects under different assumptions about selection.

**Alternative 4: Difference-in-Differences-in-Differences**
If DRIVER is offered in multiple courses (e.g., Financial Management AND Financial Modeling), compare DRIVER vs. traditional within each course, then difference across courses.

---

## Part III: Sample and Power

### 3.1 Target Sample

| Group | Target N | Source |
|-------|----------|--------|
| DRIVER | 100-150 | Dr. Zhang's sections |
| Comparison | 100-150 | Colleague's sections |
| **Total** | **200-300** | |

### 3.2 Power Analysis

**For ANCOVA (primary analysis):**

Parameters:
- α = 0.05 (two-tailed)
- Power = 0.80
- Effect size = d = 0.50 (medium, conservative estimate)

**Required N per group: 64**

With N = 100 per group:
- Detectable effect size: d = 0.40
- Power for d = 0.50: 0.92

**For Mediation (SEM):**

Following Fritz & MacKinnon (2007), for medium effect sizes (a = b = 0.39):
- Bias-corrected bootstrap: N = 148 required

**For Moderation:**

Following Aguinis et al. (2005), for detecting interaction effects:
- N = 200+ recommended for adequate power

### 3.3 Attrition Considerations

**Expected Attrition:**
- T0 → T2: 10-15% (course dropout)
- T2 → T3: 30-40% (graduation, non-response)

**Mitigation:**
- Incentives for T3 participation ($20 gift card)
- Multiple contact methods (email, phone, LinkedIn)
- Planned analysis of attrition patterns

**Analysis Implications:**
- Conduct intention-to-treat (ITT) analysis as primary
- Treatment-on-treated (TOT) as sensitivity analysis
- Model attrition and assess differential attrition by condition

---

## Part IV: Threats to Validity

### 4.1 Internal Validity Threats

| Threat | Description | Mitigation |
|--------|-------------|------------|
| **Selection** | Students differ systematically | PSM + DiD; extensive baseline |
| **History** | External events affect outcomes | Both groups same semester |
| **Maturation** | Natural development over time | Comparison group controls |
| **Testing** | Practice effects from repeated measurement | Same measures both groups |
| **Instrumentation** | Measurement changes over time | Standardized instruments |
| **Attrition** | Differential dropout | Model and assess |
| **Diffusion** | Treatment spreads to comparison | Monitor cross-group interaction |
| **Compensatory rivalry** | Comparison tries harder | Blind to hypotheses |

### 4.2 External Validity Threats

| Threat | Description | Mitigation |
|--------|-------------|------------|
| **Population** | Sample not representative | Document demographics |
| **Setting** | Results specific to this context | Plan multi-site replication |
| **Treatment variation** | DRIVER varies across implementations | Fidelity measurement |
| **Outcome measures** | Measures may not generalize | Multiple outcome types |

### 4.3 Construct Validity Threats

| Threat | Description | Mitigation |
|--------|-------------|------------|
| **Mono-operation bias** | Single operationalization | Multiple measures per construct |
| **Mono-method bias** | Single measurement method | Multi-method (survey, behavioral, performance) |
| **Social desirability** | Self-reports biased | Include behavioral measures |
| **Experimenter expectancy** | Researcher influences | Blind coding; standardized protocols |

---

## Part V: Measurement Design

### 5.1 Multi-Method Triangulation

Each primary construct measured through multiple methods:

| Construct | Self-Report | Behavioral | Performance |
|-----------|-------------|------------|-------------|
| AI Mental Model | Survey scale | Prompt coding | — |
| Cognitive Capability | Self-efficacy | — | IPA (unplugged) |
| Cognitive Dependency | Survey scale | AI Reliance Index | IPA ratio |
| Critical Evaluation | Disposition scale | — | AOET task |
| Prompt Engineering | Self-assessment | Transcript coding | — |

### 5.2 The "Unplugged Assessment" Innovation

**Core Design Feature**: Administer parallel performance assessments with and without AI access.

**Rationale**:
- Productivity studies (Brynjolfsson et al.) measure only AI-assisted performance
- Cannot distinguish capability from dependency
- Independent performance reveals whether skills transfer

**Implementation**:
- Same problem types administered twice (within-subjects)
- Counterbalance order across students
- Calculate Capability Ratio: Performance_without_AI / Performance_with_AI
  - Ratio → 1.0: Independent capability developed
  - Ratio → 0.0: Complete dependency on AI

**Timing**:
- T0: Baseline capability (no AI training yet)
- T2: Post-intervention capability
- Compare change in ratio across treatment/comparison

### 5.3 AI Reliance Index

**Objective measure of AI usage patterns extracted from LMS:**

```
AI_Reliance_Index = (
    0.3 × Query_Frequency +
    0.3 × Early_Consultation +
    0.4 × Solution_Attribution
)
```

Components:
- **Query Frequency**: Number of AI interactions per assignment (normalized)
- **Early Consultation**: How early in problem-solving AI is first consulted
- **Solution Attribution**: Proportion of final solution directly from AI output

Interpretation:
- High ARI + High Performance = Effective AI partnership
- High ARI + Low Independent Performance = Dependency
- Low ARI + High Independent Performance = Self-sufficient capability

---

## Part VI: Data Collection Protocol

### 6.1 Timeline

| Week | Data Collection Activity |
|------|-------------------------|
| 0 | Instructor coordination; comparison group recruitment |
| 1 | T0 survey administration (both groups) |
| 2-6 | Course delivery; LMS data collection |
| 7 | T1 survey administration |
| 8-13 | Course delivery; LMS data collection |
| 14 | T2 survey + performance assessments |
| 15-16 | Data cleaning; preliminary analysis |
| +6 mo | T3 follow-up survey |

### 6.2 Survey Administration

**T0 (Week 1)**:
- Administered in class (first day)
- ~20 minutes
- Include consent form
- Collect contact information for T3

**T1 (Week 7)**:
- Online administration (Qualtrics)
- Email invitation with 2 reminders
- 7-day completion window
- Small incentive (extra credit or raffle entry)

**T2 (Week 14)**:
- In-class for survey portion
- Separate session for performance assessments
- ~30 minutes total

**T3 (+6 months)**:
- Online administration
- Email + phone/text follow-up
- $20 gift card incentive
- 14-day completion window

### 6.3 Behavioral Data Collection

**Prompt Quality Coding:**
- Sample 3 AI interactions per student per timepoint
- Two trained coders independently rate
- Inter-rater reliability (κ > 0.70) established before main coding
- Disagreements resolved by third coder

**LMS Data Extraction:**
- Weekly automated extraction
- Variables: login frequency, time-on-task, submission patterns
- AI tool usage logs (if platform permits)

### 6.4 Performance Assessment Administration

**Independent Performance Assessment (IPA):**
- Administered in controlled environment (proctored)
- No AI access permitted
- 45-minute time limit
- 3 problems covering different financial concepts
- Scored by blind raters (unaware of condition)

**AI Output Evaluation Task (AOET):**
- Part of T2 assessment session
- 6 AI-generated solutions to evaluate
- 30-minute time limit
- Objective scoring possible

---

## Part VII: Analysis Roadmap

### 7.1 Analysis Sequence

```
Phase 1: Data Preparation
├── Data cleaning and validation
├── Attrition analysis
├── Missing data assessment and handling
└── Construct validation (CFA)

Phase 2: Balance Assessment
├── Pre-matching balance tables
├── Propensity score estimation
├── Post-matching balance verification
└── Common support assessment

Phase 3: Primary Analyses
├── ANCOVA for each primary outcome
├── DiD estimation
├── Effect size calculation
└── Sensitivity analyses

Phase 4: Mechanism Analyses
├── Mediation models (SEM)
├── Moderation tests
└── Trajectory analysis

Phase 5: Robustness Checks
├── Alternative matching specifications
├── Placebo tests
├── Bounds analysis
└── Subgroup analyses
```

### 7.2 Pre-Registration

Before T2 data collection, pre-register:
- Primary hypotheses
- Analysis plan
- Decision rules for robustness checks
- Rules for handling multiple comparisons

Platform: OSF (Open Science Framework) or AsPredicted

---

## Part VIII: Ethical Considerations

### 8.1 IRB Protocol Elements

**Risks**:
- Minimal risk study
- Potential discomfort from performance assessment
- Privacy concerns with LMS data

**Benefits**:
- Contribution to knowledge
- Improved instruction based on findings
- Professional development for participants

**Protections**:
- Informed consent at each wave
- Right to withdraw without penalty
- Data de-identification
- Secure storage

### 8.2 Comparison Group Ethics

**Concern**: Is it ethical to provide potentially inferior instruction to comparison group?

**Response**:
1. Equipoise exists—we don't know DRIVER is superior
2. Comparison receives standard, established instruction
3. Research findings will benefit future students
4. Comparison students can access DRIVER resources after study

### 8.3 Compensation

| Activity | Compensation |
|----------|--------------|
| T0 Survey | Course requirement |
| T1 Survey | Small extra credit |
| T2 Survey + Assessment | Course requirement |
| T3 Follow-up | $20 gift card |

---

## Part IX: Feasibility Assessment

### 9.1 Resource Requirements

| Resource | Status | Notes |
|----------|--------|-------|
| Treatment sections | ✓ Available | Dr. Zhang's courses |
| Comparison sections | ⚠ Needs coordination | Colleague recruitment |
| Survey platform | ✓ Available | Institutional Qualtrics |
| LMS access | ⚠ Needs approval | IT coordination |
| Statistical software | ✓ Available | R/Stata/Mplus |
| Research assistant | ⚠ Desirable | Coding, administration |
| IRB approval | 🔲 Pending | Submit immediately |

### 9.2 Timeline Feasibility

| Phase | Duration | Realistic? |
|-------|----------|------------|
| IRB + Setup | 4-6 weeks | Yes |
| T0-T2 Data Collection | 14 weeks | Yes (one semester) |
| T3 Follow-up | 6 months post | Yes |
| Analysis + Writing | 6-12 months | Yes |
| Total to Paper 1 | 18-24 months | Achievable |

### 9.3 Risk Mitigation

| Risk | Probability | Impact | Mitigation |
|------|-------------|--------|------------|
| Low comparison N | Medium | High | Recruit multiple instructors |
| High attrition | Medium | Medium | Incentives; multiple contacts |
| Poor balance | Low | High | Extensive baseline measures |
| Measurement issues | Low | Medium | Pilot testing; validated scales |
| IRB delays | Medium | Medium | Submit early; standard protocol |

---

## Part X: Design Strengths and Limitations

### 10.1 Strengths

1. **Longitudinal design** with 4 measurement points
2. **Multi-method measurement** (survey, behavioral, performance)
3. **"Unplugged assessment" innovation** distinguishes capability from dependency
4. **Career outcome tracking** links intervention to labor market
5. **Comparison group** enables causal inference
6. **Large sample** provides adequate power
7. **Extensive baseline** supports matching
8. **Pre-registration** prevents HARKing

### 10.2 Limitations

1. **No random assignment** — selection bias possible despite matching
2. **Single institution** — generalizability unknown
3. **Single instructor** delivers treatment — instructor effects confounded
4. **Self-report measures** — social desirability bias possible
5. **Finance-specific** — may not generalize to other domains
6. **Treatment package** — cannot isolate specific mechanisms

### 10.3 Future Design Improvements

**For Future Iterations:**

1. **Cluster randomization**: Randomize sections to condition (requires institutional support)
2. **Waitlist control**: Students who want DRIVER but can't get in
3. **Factorial design**: Isolate specific DRIVER components
4. **Multi-site replication**: Test across institutions
5. **Active control**: Another structured AI methodology
6. **Professional sample**: Extend to working analysts

---

## Summary: The Design in One Page

**Question**: Does structured AI collaboration (DRIVER) build analytical capabilities or create dependency?

**Design**: Quasi-experimental, longitudinal, comparison group

**Sample**: N ≈ 200-300 (100-150 per condition)

**Identification**: Propensity Score Matching + Difference-in-Differences

**Key Innovation**: "Unplugged assessment" measures performance with and without AI access

**Timeline**: One semester (T0-T2) + 6-month follow-up (T3)

**Primary Outcomes**: AI Mental Model, Cognitive Capability, Cognitive Dependency, Career Outcomes

**Mechanisms**: Prompt Engineering, Metacognition, Critical Evaluation

**Strengths**: Multi-method, longitudinal, career tracking, pre-registered

**Limitations**: Non-random assignment, single institution, instructor confound

**Feasibility**: Achievable with current resources + IRB + colleague coordination

---

**Document Version:** 1.0
**Last Updated:** December 3, 2025
**Next Document:** 03_Construct_Operationalization.md
