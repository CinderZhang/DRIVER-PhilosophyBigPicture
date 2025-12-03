# Construct Operationalization: Variables and Measurement

**Document Created**: December 3, 2025
**Part of**: DRIVER Research Program
**Purpose**: Define all variables with precise operational definitions and measurement approaches

---

## Preamble: From Theory to Measurement

This document translates theoretical constructs into measurable variables. Each construct is defined at three levels:

1. **Conceptual Definition**: What the construct means theoretically
2. **Operational Definition**: How we measure it in practice
3. **Psychometric Properties**: Expected reliability and validity evidence

Constructs are organized by their role in the research model:
- **Primary Outcomes** (Dependent Variables)
- **Process Mechanisms** (Mediating Variables)
- **Individual Differences** (Moderating Variables)
- **Background Characteristics** (Control Variables)
- **Distal Outcomes** (Long-term Dependent Variables)

---

## Part I: Conceptual Model Overview

### 1.1 The Full Model

```
┌─────────────────────────────────────────────────────────────────────────────────────┐
│                              DRIVER RESEARCH MODEL                                   │
└─────────────────────────────────────────────────────────────────────────────────────┘

CONTROLS (T0)              MODERATORS                MEDIATORS (T1)           OUTCOMES (T2)
─────────────              ──────────                ──────────────           ────────────

┌───────────────┐     ┌───────────────────┐     ┌───────────────────┐    ┌───────────────────┐
│ Demographics  │     │ Learning Approach │     │ Prompt Engineering│    │ AI Mental Model   │
│ • Age         │     │ • Deep (R-SPQ)    │     │ Skills            │    │ Sophistication    │
│ • Gender      │     │ • Surface (R-SPQ) │     │                   │    │                   │
│ • Major       │     │                   │     │ Metacognitive     │    │ Cognitive         │
│ • Year        │     │ Tech Acceptance   │     │ Awareness         │    │ Capability        │
│               │     │ • Usefulness      │     │                   │    │ (Independent)     │
│ Academic      │     │ • Ease of Use     │     │ Critical          │    │                   │
│ • Prior GPA   │     │ • Anxiety         │     │ Evaluation        │    │ Cognitive         │
│               │     │ • Resistance      │     │ Skills            │    │ Dependency        │
│ Experience    │     │                   │     │                   │    │ (Low = Good)      │
│ • Tech Exp    │     │ Prior Experience  │     │ AI Self-Efficacy  │    │                   │
│ • Finance Exp │     │ • Tech            │     │                   │    │ Course Performance│
│               │     │ • Finance         │     │                   │    │                   │
└───────────────┘     └───────────────────┘     └───────────────────┘    └───────────────────┘
        │                      │                         │                        │
        │                      │                         │                        │
        └──────────────────────┴─────────────────────────┴────────────────────────┘
                                           │
                                           ▼
                              ┌───────────────────────┐
                              │   DISTAL OUTCOMES     │
                              │        (T3)           │
                              │                       │
                              │ • Employment Status   │
                              │ • Starting Salary     │
                              │ • Employer Prestige   │
                              │ • AI Use at Work      │
                              │ • Skill Transfer      │
                              └───────────────────────┘
```

### 1.2 Variable Classification Summary

| Category | Variables | Role in Model |
|----------|-----------|---------------|
| **Primary Outcomes** | AI Mental Model, Cognitive Capability, Cognitive Dependency | DVs at T2 |
| **Process Mechanisms** | Prompt Skills, Metacognition, Critical Evaluation, AI Self-Efficacy | Mediators |
| **Individual Differences** | Learning Approach, Tech Acceptance, Prior Experience | Moderators |
| **Background** | Demographics, Academic Performance | Controls |
| **Distal Outcomes** | Employment, Salary, AI Use, Transfer | DVs at T3 |
| **Intervention** | DRIVER vs. Traditional | IV (Treatment indicator) |

---

## Part II: Primary Outcome Variables

### 2.1 AI Mental Model Sophistication

#### Conceptual Definition
The degree to which an individual's mental representation of AI has evolved from simplistic, instrumental views ("AI as oracle/answer machine") to sophisticated partnership models ("AI as thinking partner/cognitive collaborator").

#### Theoretical Grounding
- **Mental Models Theory** (Norman, 1983; Johnson-Laird, 1983): Internal representations that guide interaction with systems
- **Epistemic Cognition** (Hofer & Pintrich, 1997): Beliefs about the nature of knowledge and knowing
- **Technology Frames** (Orlikowski & Gash, 1994): Interpretive schemas for understanding technology

#### Operational Definition
A multi-dimensional construct measured via self-report scale with three subdimensions:

**Dimension 1: Oracle vs. Tool Orientation**
- High scores = Views AI as tool to augment thinking
- Low scores = Views AI as oracle providing answers

**Dimension 2: Error and Limitation Awareness**
- High scores = Recognizes AI fallibility and boundaries
- Low scores = Assumes AI reliability

**Dimension 3: Partnership Sophistication**
- High scores = Engages in collaborative, iterative dialogue
- Low scores = Issues commands and accepts outputs

#### Measurement
**Source**: Custom scale developed for this research
**Items**: 15 items across 3 subdimensions (5 each)
**Response Format**: 7-point Likert (1 = Strongly Disagree, 7 = Strongly Agree)
**Administration**: T0, T1, T2, T3

**Sample Items**:
- "AI is most useful when it helps me think through problems, not when it gives me answers." (Oracle vs. Tool)
- "AI frequently makes mistakes that I need to catch." (Error Awareness)
- "I can predict when AI will be helpful vs. when I should work independently." (Partnership)

#### Scoring
- Reverse code items where high agreement indicates naive view
- Calculate subdimension means
- Calculate total score as mean of all items
- Range: 1-7 (higher = more sophisticated)

#### Expected Psychometric Properties
- **Internal Consistency**: α ≥ 0.80 for total scale; α ≥ 0.70 for subdimensions
- **Test-Retest Reliability**: r ≥ 0.70 (for stable individual differences)
- **Construct Validity**: Correlate positively with metacognition, critical thinking; negatively with technology anxiety

#### Validation Plan
1. **Pilot test** with N=50 students
2. **Exploratory Factor Analysis** to verify structure
3. **Confirmatory Factor Analysis** in main sample
4. **Convergent validity**: Correlate with related constructs
5. **Discriminant validity**: Distinguish from tech acceptance

---

### 2.2 Cognitive Capability (Independent Performance)

#### Conceptual Definition
The ability to perform analytical tasks effectively without AI assistance, demonstrating that skills and knowledge have been internalized rather than remaining externalized in tools.

#### Theoretical Grounding
- **Cognitive Load Theory** (Sweller, 1988): Learning builds schema that reduce working memory demands
- **Transfer of Learning** (Barnett & Ceci, 2002): Application of knowledge to new contexts
- **Expertise Research** (Ericsson & Charness, 1994): Expert performance as internalized skill

#### Operational Definition
Performance on standardized financial analysis problems completed without AI access, compared to performance with AI access.

#### Measurement
**Source**: Performance-based assessment (Independent Performance Assessment - IPA)

**Design**:
- 3 problems per assessment
- Each problem maps to course content (TVM, valuation, portfolio)
- Difficulty calibrated to course level
- Administered under proctored conditions
- No AI, internet, or external resources permitted
- 45-minute time limit

**Problem Types**:
1. **Time Value of Money**: Present/future value calculation with interpretation
2. **Valuation**: Stock or bond valuation with justification
3. **Portfolio/Decision**: Risk-return tradeoff or capital budgeting decision

**Scoring Rubric** (per problem, 0-5 scale):

| Score | Criteria |
|-------|----------|
| 0 | No attempt or completely incorrect |
| 1 | Partial attempt, major conceptual errors |
| 2 | Correct approach, significant calculation errors |
| 3 | Correct answer, limited explanation |
| 4 | Correct answer, clear explanation |
| 5 | Correct answer, insightful explanation with extensions |

**Inter-rater Reliability Target**: ICC ≥ 0.85

#### Derived Measures

**Raw Capability Score**: Sum of 3 problem scores (0-15)

**Capability Ratio**:
```
Capability_Ratio = Score_without_AI / Score_with_AI
```
- Ratio → 1.0: Full capability (independent = assisted)
- Ratio → 0.0: Complete dependency (cannot perform without AI)
- Ratio > 1.0: Possible if AI introduces errors student catches

**Capability Change**:
```
Capability_Change = Score_T2 - Score_T0
```
- Positive = improvement in independent capability
- Negative = decline (rare but possible)

#### Administration
- **T0**: Baseline capability (before DRIVER training)
- **T2**: Post-intervention capability
- Both conditions administer same difficulty problems (different specific problems to prevent practice effects)

---

### 2.3 Cognitive Dependency

#### Conceptual Definition
The degree to which reliance on AI has undermined rather than augmented independent cognitive capability—a maladaptive relationship where the individual cannot function effectively without the tool.

#### Theoretical Grounding
- **Cognitive Offloading** (Risko & Gilbert, 2016): Using external tools to reduce cognitive demand
- **Automation Complacency** (Parasuraman & Riley, 1997): Over-reliance on automated systems
- **Desirable Difficulties** (Bjork, 1994): Easy conditions may impair long-term learning

#### Operational Definition
A multi-method construct combining self-report and behavioral indicators:

**Component 1: Self-Reported Dependency** (Survey)
**Component 2: Behavioral AI Reliance** (LMS Data)
**Component 3: Performance Gap** (IPA with vs. without AI)

#### Measurement Component 1: Self-Report Scale

**Source**: Custom scale developed for this research
**Items**: 8 items
**Response Format**: 7-point Likert

**Sample Items**:
- "I feel lost when I can't access AI tools."
- "Without AI, I would struggle to complete assignments."
- "I rely on AI to check even simple calculations."
- "I'm not sure I truly understand concepts I've learned with AI."

**Scoring**: Mean of items (after appropriate reverse coding)
- Range: 1-7
- Higher = more dependent

#### Measurement Component 2: AI Reliance Index (Behavioral)

**Source**: LMS and assignment data
**Components**:

```
AI_Reliance_Index = 0.3 × Query_Frequency_Z +
                    0.3 × Early_Consultation_Z +
                    0.4 × Solution_Attribution_Z
```

Where:
- **Query_Frequency**: Number of AI interactions per assignment (z-scored within sample)
- **Early_Consultation**: Proportion of work time before first AI query (reversed, z-scored)
- **Solution_Attribution**: Proportion of final solution from AI (coded from submissions, z-scored)

**Range**: Approximately -3 to +3 (standardized)
**Interpretation**: Higher = more reliant on AI

#### Measurement Component 3: Performance Gap

```
Dependency_Gap = Score_with_AI - Score_without_AI
```

- **Large positive gap**: Can only perform with AI (dependency)
- **Small/zero gap**: Performs similarly regardless (capability)
- **Negative gap**: AI actually hurts performance (rare)

#### Composite Dependency Score

Standardize each component and average:
```
Composite_Dependency = mean(Z_SelfReport, Z_AIReliance, Z_PerformanceGap)
```

#### Critical Note on Interpretation
Dependency is **distinct from AI use intensity**. High AI use combined with high independent capability indicates effective partnership, not dependency. Dependency is specifically the **erosion** of independent capability.

```
                    AI Use Intensity
                    Low         High
                 ┌─────────┬─────────┐
Independent  High│ Self-   │ Effective│
Capability       │ Reliant │Partnership│
                 ├─────────┼─────────┤
             Low │ Low     │ Dependency│
                 │ Engagement│        │
                 └─────────┴─────────┘
```

---

## Part III: Process Mechanism Variables (Mediators)

### 3.1 Prompt Engineering Skill Development

#### Conceptual Definition
The ability to construct effective AI prompts that elicit useful responses while maintaining cognitive engagement—moving beyond simple queries to strategic, iterative dialogue that enhances rather than replaces thinking.

#### Theoretical Grounding
- **Question Generation** (Graesser & Person, 1994): Quality of questions reflects depth of understanding
- **Self-Explanation** (Chi et al., 1994): Generating explanations improves learning
- **Metacognitive Prompting** (Bannert & Mengelkamp, 2008): Prompts that trigger reflection

#### Operational Definition
Multi-method measurement combining self-report and behavioral coding of actual prompts.

#### Measurement Component 1: Self-Report Assessment

**Source**: Custom scale
**Items**: 12 items across 3 phases (Before, During, After prompting)

**Sample Items**:
- Before: "I think about the problem myself before asking AI for help."
- During: "I challenge AI responses that don't match my expectations."
- After: "I can explain in my own words what AI told me."

**Response Format**: 7-point frequency scale (1 = Never, 7 = Always)

#### Measurement Component 2: Behavioral Coding

**Source**: AI interaction transcripts from assignments
**Sample**: 3 interactions per student per timepoint (T0, T1, T2)

**Coding Rubric**:

| Dimension | Level 1 | Level 2 | Level 3 | Level 4 |
|-----------|---------|---------|---------|---------|
| **Specificity** | Vague query | Topic-specific | Contextual | Strategic with hypothesis |
| **Cognitive Engagement** | Answer-seeking | Process-seeking | Verification-seeking | Extension-seeking |
| **Self-Awareness** | No hypothesis stated | Admits confusion | States preliminary thinking | Articulates specific gap |
| **Follow-up Quality** | Accepts first response | Asks clarification | Challenges response | Tests boundaries |

**Scoring**: Each dimension 1-4; Total 4-16
**Inter-rater Reliability Target**: κ ≥ 0.70

#### Composite Score
```
Prompt_Skill = 0.4 × Z_SelfReport + 0.6 × Z_BehavioralCoding
```
(Weight behavioral higher due to objectivity)

---

### 3.2 Metacognitive Awareness

#### Conceptual Definition
Awareness of one's own thinking processes and the ability to monitor, evaluate, and regulate cognitive activities—knowing what you know, knowing what you don't know, and adjusting strategies accordingly.

#### Theoretical Grounding
- **Metacognition** (Flavell, 1979): Thinking about thinking
- **Self-Regulated Learning** (Zimmerman, 2002): Cyclical process of forethought, performance, reflection
- **Calibration** (Dunning et al., 2003): Accuracy of self-assessment

#### Operational Definition
Measured via adapted version of established metacognition inventory plus custom AI-specific items.

#### Measurement

**Primary Source**: Metacognitive Awareness Inventory (MAI) - Schraw & Dennison (1994)

**Established Subscales**:
- **Knowledge of Cognition** (17 items): Declarative, procedural, conditional knowledge
- **Regulation of Cognition** (35 items): Planning, monitoring, evaluation, debugging, information management

**For Feasibility**: Use 20-item short form (Tock & Moxley, 2017)

**DRIVER-Specific Additions** (6 items):
- "Working with AI helps me notice gaps in my understanding."
- "I've become better at monitoring my own thought process through AI discussions."
- "AI prompts me to think about HOW I'm thinking, not just what I'm thinking."
- "The DRIVER framework helps me plan my approach to problems systematically."
- "Using AI has made me more aware of my learning strategies."
- "I reflect on my AI interactions to improve future problem-solving."

**Response Format**: 7-point Likert (1 = Never/Rarely true, 7 = Always/Almost always true)

#### Scoring
- MAI Short Form: Mean of 20 items
- DRIVER Addition: Mean of 6 items
- Composite: Mean of all 26 items
- Range: 1-7 (higher = greater metacognitive awareness)

#### Psychometric Properties (from literature)
- MAI Short Form: α = 0.90 (Tock & Moxley, 2017)
- Two-factor structure confirmed (Knowledge, Regulation)

---

### 3.3 Critical Evaluation Skills

#### Conceptual Definition
The ability and propensity to identify errors, limitations, biases, and inappropriate applications in AI-generated outputs—combining detection capability with disposition to actually engage in evaluation.

#### Theoretical Grounding
- **Critical Thinking** (Facione, 1990; Ennis, 1996): Skills and dispositions for reasoned judgment
- **Epistemic Vigilance** (Sperber et al., 2010): Mechanisms for evaluating communicated information
- **Automation Bias** (Skitka et al., 1999): Tendency to defer to automated recommendations

#### Operational Definition
Multi-method measurement: dispositional tendency (self-report) + actual detection ability (performance task).

#### Measurement Component 1: Critical Evaluation Disposition Scale

**Source**: Custom scale adapted from Critical Thinking Disposition Inventory (Sosu, 2013)
**Items**: 8 items

**Sample Items**:
- "I always verify AI calculations against my own work."
- "I look for errors in AI reasoning, not just AI answers."
- "I test AI responses by asking the same question in different ways."
- "I trust my own judgment over AI when they conflict."

**Response Format**: 7-point Likert
**Scoring**: Mean (higher = stronger disposition to evaluate)

#### Measurement Component 2: AI Output Evaluation Task (AOET)

**Source**: Performance-based assessment
**Design**: 6 AI-generated finance solutions to evaluate

| Problem | True Status | Error Type |
|---------|-------------|------------|
| 1 | Correct | — |
| 2 | Correct | — |
| 3 | Incorrect | Mathematical error |
| 4 | Incorrect | Mathematical error |
| 5 | Incorrect | Reasoning/logic error |
| 6 | Incorrect | Reasoning/logic error |

**Student Tasks** (per problem):
1. Rate confidence in solution (1-10)
2. Identify as Correct / Incorrect / Unsure
3. Explain any errors found
4. Describe how you would verify

**Scoring**:
- **Detection Accuracy**: Number correctly identified (0-6)
- **Calibration**: Correlation between confidence and correctness
- **Explanation Quality**: Depth of error explanation (coded 0-2)
- **Verification Strategy**: Quality of proposed verification (coded 0-2)

**Composite AOET Score**:
```
AOET_Score = 0.4 × Detection + 0.2 × Calibration_r + 0.2 × Explanation + 0.2 × Verification
```
(Standardize each component first)

---

### 3.4 AI Self-Efficacy

#### Conceptual Definition
Confidence in one's ability to effectively use AI tools for learning and problem-solving tasks—belief that one can successfully harness AI as a productive tool.

#### Theoretical Grounding
- **Self-Efficacy Theory** (Bandura, 1986): Task-specific confidence predicts performance
- **Computer Self-Efficacy** (Compeau & Higgins, 1995): Confidence with computing technology

#### Operational Definition
Adapted from established Computer Self-Efficacy Scale for AI context.

#### Measurement

**Source**: Adapted Computer Self-Efficacy Scale (Compeau & Higgins, 1995)
**Items**: 10 items

**Stem**: "I could effectively use AI to..."

**Sample Items**:
- "...explore a topic I know nothing about"
- "...verify the accuracy of my own analysis"
- "...identify when AI outputs are incorrect or misleading"
- "...craft prompts that get me useful responses"
- "...decide when NOT to use AI and work independently"

**Response Format**: 10-point scale (1 = Not at all confident, 10 = Completely confident)

**Scoring**: Mean of items (range 1-10)

**Psychometric Properties** (expected based on parent scale):
- α ≥ 0.90
- Single-factor structure

---

## Part IV: Moderating Variables

### 4.1 Learning Approach

#### Conceptual Definition
The characteristic way students engage with learning material—either seeking deep understanding through meaning-making and integration, or approaching superficially through memorization and minimum effort.

#### Theoretical Grounding
- **Approaches to Learning** (Marton & Säljö, 1976; Biggs, 1987)
- **Deep vs. Surface Processing** (Craik & Lockhart, 1972)

#### Measurement

**Source**: Revised Study Process Questionnaire (R-SPQ-2F) - Biggs et al. (2001)
**Items**: 20 items
**Subscales**:
- Deep Approach (10 items): Seeking meaning, relating ideas
- Surface Approach (10 items): Memorization, minimum effort

**Response Format**: 7-point Likert (adapted from original 5-point)

**Psychometric Properties** (from literature):
- Deep Approach: α = 0.73
- Surface Approach: α = 0.64
- Two-factor structure confirmed

**Scoring**:
- Deep Approach: Mean of items 1, 2, 5, 6, 9, 10, 13, 14, 17, 18
- Surface Approach: Mean of items 3, 4, 7, 8, 11, 12, 15, 16, 19, 20

**Moderation Hypothesis**: Deep learners benefit more from DRIVER (larger treatment effects)

---

### 4.2 Technology Acceptance

#### Conceptual Definition
Attitudes toward AI integration in learning, including perceived usefulness, ease of use, anxiety, and resistance—predicting engagement with and benefit from AI-integrated instruction.

#### Theoretical Grounding
- **Technology Acceptance Model** (Davis, 1989; Venkatesh & Bala, 2008)
- **Resistance to Change** (Oreg, 2003)

#### Measurement

**Source**: Technology Acceptance Model 3 (TAM3) - adapted subscales
**Items**: 16 items across 4 subscales

**Subscales**:
1. **Perceived Usefulness** (4 items): AI enhances learning effectiveness
2. **Perceived Ease of Use** (4 items): AI is easy to learn and use
3. **Technology Anxiety** (4 items): Apprehension about AI (reverse coded)
4. **AI Resistance** (4 items): Preference for traditional methods (reverse coded)

**Response Format**: 7-point Likert

**Scoring**:
- Each subscale: Mean of 4 items
- Total Tech Acceptance: Mean of all 16 items (after reverse coding)
- Range: 1-7 (higher = more accepting)

**Moderation Hypothesis**: Higher acceptance → stronger engagement → larger effects

---

### 4.3 Prior Experience

#### Conceptual Definition
Previous exposure to and facility with technology (especially AI) and finance content—baseline starting points that may moderate intervention effects.

#### Measurement

**Technology Experience** (5 items):
- Experience using AI tools (ChatGPT, Gemini, etc.)
- Experience writing code
- Experience with spreadsheets
- Experience with data visualization
- Experience with financial databases

**Response Format**: 7-point (1 = No experience, 7 = Expert)
**Scoring**: Mean of 5 items

**Finance Knowledge** (5 items):
- Time value of money concepts
- Stock valuation methods
- Bond pricing
- Financial statement analysis
- Portfolio theory

**Response Format**: 7-point (1 = None, 7 = Advanced)
**Scoring**: Mean of 5 items

**Moderation Hypothesis**: Inverted-U relationship—moderate experience benefits most (enough to engage, not so much that ceiling effects limit growth)

---

## Part V: Control Variables

### 5.1 Demographics

| Variable | Type | Measurement | Coding |
|----------|------|-------------|--------|
| Age | Continuous | Single item | Years |
| Gender | Categorical | Single item | 1=M, 2=F, 3=NB, 4=Other |
| Major | Categorical | Single item | Categories |
| Year | Ordinal | Single item | 1-5 (Fresh to Grad) |

### 5.2 Academic Background

| Variable | Type | Measurement | Source |
|----------|------|-------------|--------|
| Cumulative GPA | Continuous | Self-report | 0.0-4.0 |
| Math Courses | Count | Self-report | Number completed |
| Finance Courses | Count | Self-report | Number completed |

---

## Part VI: Distal Outcome Variables (T3)

### 6.1 Employment Outcomes

| Variable | Measurement |
|----------|-------------|
| Employment Status | Categorical: Full-time, Part-time, Internship, Seeking, Not Seeking, Student |
| Job Title | Open text, coded |
| Employer | Open text, coded for prestige |
| Industry | Categorical |
| Starting Salary | Ordinal ranges (to encourage response) |

### 6.2 AI Integration at Work

| Variable | Measurement |
|----------|-------------|
| AI Use Frequency | 7-point (1=Never, 7=Daily) |
| Comparative AI Skill | 7-point vs. colleagues |
| AI Training Role | Binary: Have you trained others? |
| AI Recognition | Binary: Has skill been recognized? |

### 6.3 Skill Transfer

| Variable | Measurement |
|----------|-------------|
| Application to Other Courses | 7-point extent |
| Application to Work | 7-point extent |
| Continued AI Use | 7-point frequency |
| DRIVER Framework Use | 7-point extent |

---

## Part VII: Measurement Timeline Matrix

| Construct | T0 | T1 | T2 | T3 |
|-----------|:--:|:--:|:--:|:--:|
| **PRIMARY OUTCOMES** |
| AI Mental Model | ✓ | ✓ | ✓ | ✓ |
| Cognitive Capability (IPA) | ✓ | | ✓ | |
| Cognitive Dependency | | ✓ | ✓ | |
| **MEDIATORS** |
| Prompt Engineering (Self) | | ✓ | ✓ | |
| Prompt Engineering (Coded) | ✓ | | ✓ | |
| Metacognitive Awareness | | ✓ | ✓ | |
| Critical Evaluation (Disposition) | | ✓ | ✓ | |
| Critical Evaluation (AOET) | | | ✓ | |
| AI Self-Efficacy | ✓ | ✓ | ✓ | |
| **MODERATORS** |
| Learning Approach | ✓ | | ✓ | |
| Technology Acceptance | ✓ | | | |
| Prior Experience | ✓ | | | |
| **CONTROLS** |
| Demographics | ✓ | | | |
| Academic Background | ✓ | | | |
| **DISTAL OUTCOMES** |
| Employment | | | | ✓ |
| AI at Work | | | | ✓ |
| Transfer | | | | ✓ |

---

## Part VIII: Hypothesized Relationships

### 8.1 Main Effects (H1)

```
DRIVER → AI Mental Model (+)
DRIVER → Cognitive Capability (+)
DRIVER → Cognitive Dependency (-)
DRIVER → Career Outcomes (+)
```

### 8.2 Mediation (H2)

```
DRIVER → Prompt Engineering → AI Mental Model
DRIVER → Metacognitive Awareness → Cognitive Capability
DRIVER → Critical Evaluation → Reduced Dependency
DRIVER → AI Self-Efficacy → Sustained AI Use
```

### 8.3 Moderation (H3)

```
Learning Approach (Deep) × DRIVER → Amplified effects
Tech Acceptance × DRIVER → Engagement moderation
Prior Experience × DRIVER → Inverted-U (moderate benefits most)
```

### 8.4 Structural Model

```
┌─────────────┐
│   DRIVER    │
│ Intervention│
└──────┬──────┘
       │
       ├───────────────────────────────────────────────────────────────┐
       │                                                               │
       ▼                                                               ▼
┌─────────────┐    ┌─────────────┐    ┌─────────────┐    ┌─────────────┐
│   Prompt    │    │Metacognitive│    │  Critical   │    │     AI      │
│   Skills    │    │  Awareness  │    │ Evaluation  │    │Self-Efficacy│
└──────┬──────┘    └──────┬──────┘    └──────┬──────┘    └──────┬──────┘
       │                  │                  │                  │
       ▼                  ▼                  ▼                  ▼
┌─────────────┐    ┌─────────────┐    ┌─────────────┐    ┌─────────────┐
│  AI Mental  │    │  Cognitive  │    │  Cognitive  │    │   Sustained │
│    Model    │    │ Capability  │    │ Dependency  │    │   AI Use    │
│             │    │             │    │ (reduced)   │    │             │
└─────────────┘    └─────────────┘    └─────────────┘    └─────────────┘
       │                  │                  │                  │
       └──────────────────┴──────────────────┴──────────────────┘
                                    │
                                    ▼
                          ┌─────────────────┐
                          │  Career Outcomes │
                          │  (T3 Follow-up)  │
                          └─────────────────┘
```

---

## Part IX: Psychometric Development Plan

### 9.1 For Custom Scales (AI Mental Model, Dependency, Prompt Skills)

**Phase 1: Item Development**
- Generate item pool (2x target items)
- Expert review for content validity
- Cognitive interviews (N=5-8) for clarity

**Phase 2: Pilot Testing**
- Administer to N=50 students
- Item analysis (means, SDs, corrected item-total correlations)
- Remove items with poor properties

**Phase 3: Exploratory Factor Analysis**
- Verify expected factor structure
- Examine cross-loadings
- Refine scale

**Phase 4: Confirmatory Factor Analysis (Main Study)**
- Confirm structure in independent sample
- Test measurement invariance across time

### 9.2 For Adapted Scales (TAM, R-SPQ, MAI)

**Verification Steps**:
- Confirm original factor structure with CFA
- Assess reliability in our sample
- Document any adaptations

### 9.3 For Behavioral Coding (Prompts, AOET)

**Coder Training**:
- Develop detailed coding manual with examples
- Train 2-3 coders on 20 practice cases
- Establish reliability before main coding

**Reliability Assessment**:
- Double-code 20% of cases
- Calculate Cohen's κ (target ≥ 0.70)
- Resolve disagreements through discussion

---

## Part X: Summary Tables

### 10.1 All Variables Quick Reference

| Variable | Type | Items | Scale | Timing |
|----------|------|-------|-------|--------|
| AI Mental Model | Custom | 15 | 1-7 | T0-T3 |
| Cognitive Capability | Performance | 3 problems | 0-15 | T0, T2 |
| Cognitive Dependency | Multi-method | 8 + behavioral | Composite | T1, T2 |
| Prompt Skills | Multi-method | 12 + coding | Composite | T0-T2 |
| Metacognition | Adapted MAI | 26 | 1-7 | T1, T2 |
| Critical Evaluation | Multi-method | 8 + AOET | Composite | T1, T2 |
| AI Self-Efficacy | Adapted CSE | 10 | 1-10 | T0-T2 |
| Learning Approach | R-SPQ-2F | 20 | 1-7 | T0, T2 |
| Tech Acceptance | Adapted TAM | 16 | 1-7 | T0 |
| Prior Experience | Custom | 10 | 1-7 | T0 |
| Career Outcomes | Custom | ~15 | Various | T3 |

### 10.2 Reliability Targets

| Construct | Target α | Rationale |
|-----------|----------|-----------|
| AI Mental Model | ≥ 0.80 | Primary outcome |
| Cognitive Dependency | ≥ 0.75 | Novel construct |
| Prompt Skills (Self) | ≥ 0.80 | Multi-item |
| Metacognition | ≥ 0.85 | Established scale |
| Critical Evaluation | ≥ 0.75 | Novel construct |
| AI Self-Efficacy | ≥ 0.90 | Established scale |
| Learning Approach | ≥ 0.70 | Per subscale |
| Tech Acceptance | ≥ 0.80 | Established construct |

---

## Appendix: Variable Definitions Quick Reference

### A1. Construct Definitions (One Sentence Each)

**AI Mental Model**: How sophisticated is the student's understanding of AI's capabilities and appropriate use?

**Cognitive Capability**: Can the student perform analytical tasks effectively without AI assistance?

**Cognitive Dependency**: Has AI reliance eroded independent capability?

**Prompt Engineering**: Can the student construct effective AI prompts that enhance rather than replace thinking?

**Metacognitive Awareness**: Does the student monitor and regulate their own thinking effectively?

**Critical Evaluation**: Can and does the student identify errors in AI outputs?

**AI Self-Efficacy**: Is the student confident in their ability to use AI effectively?

**Learning Approach**: Does the student seek deep understanding or surface memorization?

**Technology Acceptance**: Is the student receptive to AI-integrated learning?

### A2. Key Distinctions

**Capability vs. Dependency**: High capability + High AI use = Partnership. Low capability + High AI use = Dependency.

**Performance vs. Mental Model**: Performance is behavioral; Mental Model is cognitive representation guiding behavior.

**Disposition vs. Ability**: Critical Evaluation includes both willingness (disposition) and skill (ability) to evaluate.

**Deep vs. Surface**: Not intelligence but approach—how the student engages with material.

---

**Document Version:** 1.0
**Last Updated:** December 3, 2025
**Next Document:** 04_Survey_Instruments.md
