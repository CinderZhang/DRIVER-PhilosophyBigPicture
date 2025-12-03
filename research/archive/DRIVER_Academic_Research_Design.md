# DRIVER Framework: Academic Research Design

**Document Created**: December 3, 2025
**Author**: Dr. Cinder Zhang
**Status**: Research Design for Academic Publication Track

---

## Executive Summary

This document reframes DRIVER from a teaching methodology to a rigorous academic research program. The central research question:

> **"How do humans develop expertise when AI systems can perform expert-level cognitive tasks?"**

DRIVER represents **design science research**—building systematic interventions, deploying at scale, and studying outcomes empirically. This document provides the complete architecture for positioning DRIVER as academic research with publication potential in top finance, management, and education journals.

---

## Part 1: Academic Positioning Strategy

### 1.1 The Intellectual Repositioning

| From | To |
|------|-----|
| Teaching methodology | Empirical research program |
| Training framework | Field experiment on human capital development |
| Certification system | Evidence base for financial labor market evolution |
| Pedagogical philosophy | Testable hypotheses about AI-human collaboration |

### 1.2 The Research Question Hierarchy

**Primary Research Question:**
How do humans develop expertise when AI systems can perform expert-level cognitive tasks?

**Secondary Questions:**
1. Does structured AI collaboration build analytical capabilities or create dependency?
2. What predicts successful adaptation versus displacement?
3. How do different training architectures affect development of AI-complementary skills?
4. How do mental models of AI partnership evolve over time?

**Tertiary Questions (Mechanisms):**
5. What role does metacognitive awareness play in capability vs. dependency outcomes?
6. How does prompt engineering skill development mediate learning outcomes?
7. What characteristics predict resistance vs. adoption of AI partnership models?

### 1.3 Positioning for Different Audiences

**For Traditional Finance Departments:**
> "I study how AI disrupts information production and financial labor markets, with empirical evidence from the first systematic field experiment on human-AI collaboration in financial analysis."

**For Innovation-Focused Programs:**
> "I've engineered and deployed the first systematic methodology for developing financial professionals' capabilities in AI-augmented environments, generating unique data on human capital formation in finance."

**For Business Schools with Practice Orientation:**
> "I've built and validated a framework that transforms how finance students learn, with demonstrated outcomes (280+ students, placements at Goldman, JPMorgan, State Street) and active research generating evidence on financial workforce evolution."

**For Education/Learning Science Departments:**
> "I study cognitive development in technology-mediated learning environments, with a field experiment demonstrating how structured AI collaboration can build rather than erode analytical capabilities."

---

## Part 2: Literature Positioning

### 2.1 The Four Literatures DRIVER Bridges

**Literature 1: Financial Labor Markets**
- Hong & Kacperczyk (2010) - Competition and analyst behavior
- Groysberg et al. (2011) - Analyst mobility and performance
- Clement & Tse (2005) - Analyst characteristics and accuracy

**DRIVER Contribution:** First evidence on how AI training affects financial analyst labor market outcomes.

**Literature 2: AI and Professional Work**
- Brynjolfsson et al. (2024) - Generative AI at Work (QJE)
- Dell'Acqua et al. (2023) - "Jagged Frontier" (Harvard/BCG)
- Noy & Zhang (2023) - ChatGPT and worker productivity

**DRIVER Contribution:** Extends from productivity measurement to cognitive capability development.

**Literature 3: Human Capital Development**
- Kaiser & Menkhoff (2017) - Financial education meta-analysis
- Karlan & Valdivia (2011) - Entrepreneurship training field experiment
- Bruhn et al. (2018) - Business training program evaluation

**DRIVER Contribution:** First training intervention with both cognitive AND labor market outcomes.

**Literature 4: Technology-Mediated Learning**
- Chi & Wylie (2014) - ICAP framework for learning activities
- Kapur (2008) - Productive failure in learning
- Collins, Brown, & Newman (1989) - Cognitive apprenticeship

**DRIVER Contribution:** Operationalizes theoretical frameworks in AI-augmented professional education.

### 2.2 The Research Gap Statement

> "While recent field experiments demonstrate that generative AI tools increase worker productivity (Brynjolfsson et al., 2024), and financial education shows modest knowledge effects (Kaiser & Menkhoff, 2020), **no existing research examines whether AI-integrated training can simultaneously enhance both productivity and independent cognitive capability**. We address this gap with the DRIVER framework—producing 100% placement rates and $90,000 median starting salaries while building **portable** human capital that **accelerates** performance in new organizational contexts."

### 2.3 Critical Gap DRIVER Fills

| Existing Research | Gap | DRIVER Contribution |
|-------------------|-----|---------------------|
| AI productivity studies | Focus on speed/output, not cognitive development | Measures capability building vs. dependency |
| Financial education | Modest effects on knowledge, unclear on behavior | 100% placement rate, documented career outcomes |
| Technology training | Self-report measures only | Performance-based assessment (video, projects) |
| Professional training | No AI integration | First systematic AI-integrated methodology |
| Deskilling literature | Documents problem, no solutions | Tests intervention that prevents deskilling |

---

## Part 3: Research Design

### 3.1 Design Framework

**Design Type:** Quasi-experimental longitudinal study with embedded mixed methods

**Treatment:** DRIVER Financial Management course (structured AI collaboration)
**Comparison:** Traditional Financial Management course (same content, no DRIVER framework)

**Timeline:**
- T0 (Week 1): Baseline measurement
- T1 (Week 7): Mid-intervention process measures
- T2 (Week 14): Post-intervention outcomes
- T3 (6 months): Follow-up for sustained effects and career outcomes

### 3.2 Identification Strategy

Given likely inability to randomize students to sections, we employ:

**Primary Strategy: Propensity Score Matching + Difference-in-Differences**
- Match DRIVER students to traditional students on:
  - Prior GPA
  - Major
  - Prior tech experience
  - Baseline AI attitudes
- Estimate treatment effects using DiD to control for time-invariant confounds

**Robustness Checks:**
- Inverse probability weighting
- Sensitivity analysis for unobserved confounders (Rosenbaum bounds)
- Placebo tests on pre-treatment outcomes

**Alternative Strategy (if multiple sections exist):**
- Section fixed effects
- Instructor fixed effects (if multiple instructors)

### 3.3 Sample Size and Power

**Target:** N = 200 minimum (100 per condition)

**Power Analysis:**
- For medium effect size (d = 0.50): N = 128 for 80% power
- For mediation models: N = 150-200 recommended
- For moderation: N = 200+ for adequate power
- For trajectory models: N = 250+ ideal

**Current Status:** 280-300 students across courses provides adequate power for primary analyses.

---

## Part 4: Construct Operationalization

### 4.1 Primary Dependent Variables

#### A. AI Mental Model Evolution
**Definition:** The qualitative shift in students' conceptualization of AI's role in learning, from simplistic instrumental views ("answer machine") to sophisticated partnership models ("thinking partner").

**Measurement:** Custom scale adapted from Epistemic Beliefs Inventory (Schraw et al., 2002)

**Sample Items (7-point Likert):**
1. "When AI gives me an answer, I can be confident it's correct" (reverse)
2. "AI is most useful when it helps me think through problems, not when it gives me answers"
3. "I can predict when AI will be helpful vs. when I should work independently"
4. "Good AI collaboration requires me to already understand the topic"

#### B. Cognitive Capability (Independent Performance)
**Definition:** Ability to perform analytical tasks independently, without AI assistance.

**Measurement:**
- Performance-based assessment: Parallel finance problems administered with and without AI access
- Scoring: Solution quality, time to completion, explanation depth
- Calculate "Capability Ratio": (Performance without AI) / (Performance with AI)
  - Ratio → 1.0 = capability developed
  - Ratio → 0.0 = dependency created

#### C. Cognitive Dependency
**Definition:** Reliance on AI that erodes independent capability.

**Measurement (Multi-method):**

*Behavioral:*
- AI Reliance Index: Query frequency, timing of first AI consultation, proportion of solution from AI
- Extracted from LMS analytics and assignment submissions

*Self-Report (7-point Likert):*
1. "I feel lost when I can't access AI tools"
2. "I rely on AI to check even simple calculations"
3. "Without AI, I would struggle to complete assignments"
4. "I'm not sure I truly understand concepts I've learned with AI"

### 4.2 Mediating Variables (Process Mechanisms)

#### A. Prompt Engineering Skill Development
**Definition:** Ability to construct effective prompts that elicit useful AI responses while maintaining cognitive engagement.

**Measurement:** Behavioral coding of AI interaction transcripts

**Coding Rubric:**

| Dimension | Level 1 (Novice) | Level 2 (Developing) | Level 3 (Proficient) | Level 4 (Advanced) |
|-----------|------------------|----------------------|----------------------|---------------------|
| Specificity | Vague ("help with bonds") | Topic-specific ("explain bond pricing") | Contextual ("explain why prices fall when rates rise") | Strategic ("verify my logic and show gaps") |
| Engagement | Answer-seeking | Process-seeking | Verification-seeking | Extension-seeking |
| Self-awareness | No hypothesis | Admits confusion | States preliminary thinking | Articulates specific knowledge gap |
| Follow-up | Accepts first response | Asks clarification | Challenges AI | Tests AI boundaries deliberately |

#### B. Critical Evaluation Skills
**Definition:** Ability and propensity to identify errors, limitations, and biases in AI-generated content.

**Measurement:** AI Output Evaluation Task (AOET)
- Present 6 AI-generated finance solutions:
  - 2 correct and well-reasoned
  - 2 with subtle mathematical errors
  - 2 with correct math but flawed reasoning
- Students rate confidence, identify errors, propose verification methods
- Score: Detection accuracy, calibration, verification strategy sophistication

#### C. Metacognitive Awareness
**Definition:** Awareness of own thinking processes and ability to monitor/regulate learning.

**Measurement:** Metacognitive Awareness Inventory (MAI) - Schraw & Dennison (1994)
- 52 items (or 20-item short form)
- Subscales: Knowledge of Cognition, Regulation of Cognition

**DRIVER-Specific Additions:**
1. "Working with AI helps me notice gaps in my understanding"
2. "AI prompts me to think about HOW I'm thinking"
3. "The DRIVER framework helps me plan my approach systematically"

### 4.3 Moderating Variables

#### A. Technology Acceptance/Resistance
**Measurement:** Technology Acceptance Model (TAM3) - Venkatesh & Balasubramanian (2008)
- Perceived usefulness, perceived ease of use, anxiety subscales

**DRIVER Addition:**
- "I learn better through traditional methods than with AI"
- "AI takes away from authentic learning experiences"

#### B. Learning Approach
**Measurement:** Revised Study Process Questionnaire (R-SPQ-2F) - Biggs et al. (2001)
- Deep Approach: Seeking meaning, relating ideas
- Surface Approach: Memorization, minimizing effort

#### C. Prior Experience
- Tech experience (self-report items)
- Prior finance knowledge (quiz or self-report)
- Academic performance (GPA)

### 4.4 Distal Outcomes

#### A. Career Outcomes (6-month follow-up)
- Employment status
- Starting salary
- Employer prestige
- Job function (analyst, associate, etc.)
- Self-reported use of AI in job
- Interview performance (retrospective)

#### B. Transfer Performance
- Novel problem-solving (different domain)
- Application to other courses
- Sustained AI use patterns

---

## Part 5: Hypotheses

### 5.1 Main Effects

**H1a:** Students in DRIVER condition will show greater increase in AI Mental Model sophistication (oracle → partner) compared to control.

**H1b:** DRIVER students will demonstrate higher Independent Performance (capability) with lower AI Reliance Index (dependency).

**H1c:** DRIVER students will achieve better career outcomes (placement rate, salary) compared to control.

### 5.2 Mediation

**H2a:** Prompt Engineering Skill development mediates the relationship between DRIVER intervention and AI Mental Model sophistication.

**H2b:** Metacognitive Awareness growth mediates the relationship between DRIVER and Cognitive Capability.

**H2c:** Critical Evaluation Skills mediate the relationship between DRIVER and reduced Cognitive Dependency.

### 5.3 Moderation

**H3a:** Technology Acceptance moderates DRIVER effectiveness (positive relationship).

**H3b:** Baseline Learning Approach moderates outcomes (deep learners benefit more).

**H3c:** Prior Tech Experience shows inverted-U moderation (moderate experience benefits most).

### 5.4 Developmental Trajectories

**H4a:** AI Mental Model evolution follows non-linear trajectory: confusion → clarity → integration.

**H4b:** Cognitive Dependency shows U-shaped curve: initial increase → peak → decrease.

**H4c:** "Productive struggle" (moderate difficulty + AI support) predicts optimal outcomes.

---

## Part 6: Measurement Timeline

### T0 (Week 1): Baseline Survey (~20 min)

**Section 1: Demographics & Background**
- Prior tech experience (5 items)
- Prior finance knowledge (3 items)
- Academic background (GPA, major, year)

**Section 2: Predictors**
- Technology Acceptance (TAM - 9 items)
- Learning Approach (R-SPQ-2F - 20 items)
- AI Mental Model baseline (10 items)

**Section 3: Pre-Intervention Capability**
- Independent Performance Assessment (2 problems)
- AI Self-Efficacy (8 items)

### T1 (Week 7): Midpoint Survey (~25 min)

**Section 1: Process Variables**
- Prompt Engineering self-report (6 items)
- AI Self-Efficacy (8 items)
- Metacognitive Awareness (MAI short form - 20 items)

**Section 2: Interim Outcomes**
- AI Mental Model (10 items)
- Cognitive Dependency (8 items)
- Critical Evaluation Disposition (6 items)

**Section 3: Open-Ended (for qualitative analysis)**
- "Describe how your thinking about AI has changed"
- "What's the most important thing you've learned about working with AI?"
- "What do you still find confusing?"

**Behavioral Data:**
- Code 3 AI interaction transcripts per student (Weeks 3-6)
- Extract LMS analytics

### T2 (Week 14): Post-Intervention Survey (~30 min)

**Section 1: Primary Outcomes**
- AI Mental Model (10 items)
- Cognitive Capability: Independent Performance (3 problems)
- Cognitive Dependency (8 items)
- AI Self-Efficacy (8 items)

**Section 2: Mechanism Verification**
- Learning Approach (R-SPQ-2F - 20 items)
- Metacognitive Awareness (MAI short form - 20 items)
- Critical Evaluation Disposition (6 items)

**Section 3: Performance Assessments**
- AI Output Evaluation Task (6 problems)
- Transfer task (novel problem, no AI access)

**Section 4: Reflection (qualitative)**
- "How has DRIVER changed how you learn?"
- "Will you continue using AI? How?"

**Behavioral Data:**
- Code 3 AI transcripts (Weeks 10-13)
- Final prompt quality scoring

### T3 (6 months): Follow-Up Survey (~15 min)

**Section 1: Sustained Effects**
- AI Mental Model (10 items)
- Current AI usage patterns (8 items)
- Transfer to other courses/work (5 items)

**Section 2: Career Outcomes**
- Employment status
- Starting salary (if employed)
- Workplace AI use
- Job search experience

**Section 3: Retrospective**
- "Looking back, what was most valuable?"
- "How do you use AI differently now?"

---

## Part 7: Analysis Plan

### 7.1 Construct Validation

1. **Confirmatory Factor Analysis (CFA)** for adapted scales
2. **Measurement invariance** testing across time
3. **Reliability** (Cronbach's α, McDonald's ω)
4. **Inter-rater reliability** for behavioral coding (Cohen's κ > 0.70)

### 7.2 Intervention Effects

1. **ANCOVA** controlling for baseline
2. **Multilevel models** (observations nested in students)
3. **Effect sizes** (Cohen's d) with confidence intervals

### 7.3 Mediation Analysis

1. **Structural Equation Modeling (SEM)** for simultaneous pathways
2. **Bootstrapped indirect effects** (Preacher & Hayes, 2008)
3. **Time-lagged cross-panel models**

### 7.4 Moderation Analysis

1. **Regression with interaction terms**
2. **Johnson-Neyman regions of significance**
3. **Subgroup analyses** for categorical moderators

### 7.5 Trajectory Analysis

1. **Latent Growth Curve Modeling (LGCM)**
2. **Latent Class Growth Modeling** for distinct trajectories
3. **Predictors of trajectory membership**

### 7.6 Qualitative Analysis

1. **Thematic analysis** of open-ended responses
2. **Pattern matching** with quantitative profiles
3. **Explanatory case studies**

---

## Part 8: Publication Strategy

### 8.1 Paper Pipeline

**Paper 1: Primary Intervention Study**
*"Human Capital Development in AI-Augmented Financial Analysis: Evidence from a Field Experiment"*

Target: Management Science, JFE
Timeline: Submit Year 1-2

Abstract direction:
> "We study how financial professionals develop expertise when AI can perform expert-level analytical tasks. Using a designed intervention (DRIVER) deployed with 280+ participants and longitudinal tracking of cognitive development, we find that structured AI collaboration builds analytical capabilities rather than creating dependency. Treatment effects are concentrated among participants who engage with AI as 'cognitive partner' rather than 'answer machine.' These findings have implications for training investments in financial services and financial labor market evolution."

**Paper 2: Mechanism Study**
*"Who Adapts to AI? Predictors of Successful Human-AI Collaboration in Professional Training"*

Target: Organization Science, Academy of Management Journal
Timeline: Submit Year 2-3

Focus: What predicts adaptation vs. resistance? Moderation and mediation.

**Paper 3: Mental Model Evolution**
*"From Oracle to Partner: Mental Model Development in AI-Augmented Learning"*

Target: Journal of Educational Psychology, Learning and Instruction
Timeline: Submit Year 2-3

Focus: Trajectory modeling of mental model evolution, qualitative integration.

**Paper 4: Career Outcomes**
*"Does AI Training Pay? Labor Market Returns to Structured AI Collaboration Skills"*

Target: Review of Financial Studies, Journal of Labor Economics
Timeline: Submit Year 3-4 (requires 6-month follow-up data)

Focus: Employment, salary, career trajectory outcomes.

### 8.2 Journal Targets by Discipline

**Finance:**
- Journal of Financial Economics (JFE)
- Review of Financial Studies (RFS)
- Journal of Financial and Quantitative Analysis (JFQA)
- Finance Research Letters (shorter pieces)

**Management/Organization:**
- Management Science
- Organization Science
- Academy of Management Journal
- Strategic Management Journal

**Education/Learning:**
- Journal of Educational Psychology
- Learning and Instruction
- Computers & Education
- Academy of Management Learning & Education

**HCI/Technology:**
- CHI Conference Proceedings
- CSCW Conference Proceedings
- Human-Computer Interaction journal

### 8.3 Conference Strategy

**Year 1:**
- AFA (American Finance Association) - working paper presentation
- FMA (Financial Management Association) - research session

**Year 2:**
- AOM (Academy of Management) - symposium on AI and learning
- ICIS (Information Systems) - AI in organizations track

**Year 3:**
- NBER (if invited) - labor economics implications
- Kauffman Entrepreneurship Conference - training outcomes

---

## Part 9: Next Steps

### Immediate Actions (Next 30 days)

1. **IRB Application**
   - Submit protocol for longitudinal data collection
   - Include consent for LMS data extraction
   - Plan for control group ethical considerations

2. **Instrument Development**
   - Finalize custom scales (AI Mental Model, Cognitive Dependency)
   - Pilot test with N = 30 students
   - Conduct cognitive interviews (N = 5-8)

3. **Coding Rubric Development**
   - Finalize Prompt Engineering coding rubric
   - Train coders and establish inter-rater reliability
   - Code existing video/transcript data retrospectively

4. **Comparison Group Identification**
   - Identify traditional Finance Management sections
   - Coordinate with instructors for parallel data collection
   - Plan propensity score matching variables

### Medium-term Actions (Next 6 months)

5. **Pre-registration**
   - Pre-register hypotheses on OSF or AsPredicted
   - Establishes credibility, prevents HARKing

6. **Data Infrastructure**
   - Set up secure data storage
   - Automate LMS data extraction
   - Create analysis pipelines

7. **Advisory Board**
   - Recruit 2-3 senior scholars for input
   - Finance + Education/Psychology representation
   - Establish co-authorship expectations

### Long-term Actions (Next 12 months)

8. **Grant Applications**
   - NSF CAREER (if tenure-track)
   - Spencer Foundation (education focus)
   - Lilly Endowment (current opportunity)

9. **Paper Writing**
   - Draft Paper 1 introduction and literature review
   - Prepare data description and preliminary results
   - Target conference presentations

---

## Part 10: Connection to DRIVER Philosophy

This research design operationalizes DRIVER's core theoretical claims:

| DRIVER Principle | Research Operationalization |
|------------------|----------------------------|
| "Productive Struggle Sweet Spot" | Measured via cognitive load indicators, difficulty ratings, growth trajectories |
| "AI as Spotter, Not Weight Machine" | Measured via AI Reliance Index, Independent Performance, Capability without AI |
| "Teaching Itself Obsolete" | Measured via 6-month sustained performance, framework transcendence indicators |
| "Jazz Principle" | Measured via adaptation patterns, custom vs. prescribed approach usage |
| "Mental Model Evolution" | Measured via AI Mental Model Scale, prompt sophistication trajectory |
| "Intelligence vs. Wisdom" | Measured via Capability (can execute) vs. Judgment (knows when/how) |

---

## Summary: The Academic Research Narrative

**The Problem:**
AI is transforming financial services, but we lack evidence on how to develop professionals who can partner with AI effectively rather than becoming dependent on it.

**The Gap:**
Existing research documents AI's productivity effects but not cognitive development; financial education shows modest effects but no AI integration; professional training lacks rigorous evaluation.

**The Contribution:**
DRIVER provides the first systematic field experiment on AI-integrated professional training with both cognitive AND labor market outcomes.

**The Data:**
280+ participants, longitudinal tracking (Week 1, 7, 14, +6 months), multi-method (survey, performance, behavioral, qualitative).

**The Findings (expected):**
Structured AI collaboration builds capability rather than dependency, mediated by prompt engineering skills and metacognitive awareness, moderated by baseline learning approach.

**The Implications:**
For financial services firms: how to train talent. For universities: how to prepare students. For policymakers: how to develop workforce. For labor economists: how human capital evolves in AI age.

---

**Document Version:** 1.0
**Last Updated:** December 3, 2025
**Core Philosophy:** "In an age where intelligence is infinite and free, only wisdom commands a premium."
**Research Question:** "How do humans develop expertise when AI systems can perform expert-level cognitive tasks?"
