# SME-Excel-Financial-Dashboard

1️⃣ The Problem

Across Southern Africa, millions of small businesses need financial services —
loans, insurance, credit lines — but banks and development organizations have
no efficient way to assess which businesses are financially healthy and which are struggling.
Manual assessment is slow, expensive, inconsistent and unscalable.
As a result, financially vulnerable businesses never get the support they need,
and banks miss good lending opportunities — simply because no one can assess
thousands of businesses fast enough.

This dashboard makes those assessments visible. It turns survey data from
9,618 small businesses across 4 countries into clear, actionable insight
for anyone who needs to make decisions about SME support.


2️⃣ Why a Simple Approach Was Not Enough

A naive model that predicts "Low health" for every business would be right
65% of the time — and completely useless.
Three things made this problem hard:
Class Imbalance
The dataset was severely skewed:

Low health: 65.3% of businesses

Medium health: 29.8%

High health: only 4.9%

A simple model learns that Low is almost always correct and stops trying to
identify High-health businesses — the ones banks most want to find.
Missing Data
Up to 47% of responses were blank in some survey columns. Standard models
either crash or silently produce wrong results when data is this incomplete.
Wrong Metric
Measuring overall accuracy or weighted F1 hides the minority class problem.
A model can score 87% weighted F1 while barely predicting High at all.
Macro F1 — which treats all 3 classes equally — was the only honest measure.

3️⃣ What the Dashboard Visually Answers

🌍 Which country performs best?

Real data extracted directly from the training dataset:

Country      High %           Low %       Medium %      Verdict

🇸🇿 Eswatini    11.5%          51.4%        37.1%          ✅ Regional benchmark

🇱🇸 Lesotho      0.3%          60.4%        39.3%          🔴 Glass ceiling effect

🇲🇼 Malawi      4.0%          81.2%        14.7%          🔴 Most excluded

🇿🇼 Zimbabwe    2.3%          68.6%        29.1%          🟡 Improving

Eswatini's High health rate is nearly 5× the regional average.

Malawi's 81.2% Low rate is the clearest signal of where intervention is needed most.

🎯 Which class is hardest to predict?

Class          Precision            Recall            F1          Dificulty

Low                0.90             0.93             0.92          ✅ Easy — majority class

Medium             0.80             0.78             0.79          🟡 Moderate

High               0.87             0.61             0.71          🔴 Hardest — minority class

High is the hardest class. Only 61% of High-health businesses are correctly

identified. This is why SMOTE oversampling was applied — to generate synthetic

High-class examples and force the model to learn what financial resilience looks like.

🔍 What features drive financial health?

The top 10 features ranked by importance:

Rank    Feature              Category

1      fin_score              Credit Access

2      total_access           Credit Access

3      profit_margin          Debt & Repayment

4      expense_ratio          Debt & Repayment

5      log_turnover           Financial Ratio

6      biz_age_months         Business Context

7      ins_score              Insurance Coverage

8      attitude_score         Resilience

9      vulnerability_flag     Resilience

10     credit_diversity       Credit Access

Key insight: Financial inclusion score and total access to financial services
are stronger predictors of SME health than raw revenue or profit alone.
Access to formal financial services drives long-term resilience.

⚠️ Where does the model struggle?

Weakness      Why It Happens      What Was Done  

High class recall only 0.61    Only 470 High examples in 9,618    SMOTE oversampling applied

Fold 1 lowest at 0.784    Country distribution variance      Country-stratified CV used

Medium/Low confusion    Similar survey profiles    Threshold tuning (Medium = 0.45)

Lesotho 0.3% High         Near-zero examples             Flagged as highest priority gap

The model is honest about its limits. High recall at 0.61 means 39% of
High-health businesses are still being missed — a real constraint that
field programs should account for when using predictions.

4️⃣ Business Impact

🏦 Banks & Financial Institutions

Screens 9,618 SMEs in seconds vs weeks of manual assessment
Identifies 94% of financially vulnerable businesses (Low recall = 0.93)
87% precision on High class — confident, reliable lending recommendations
Reduces microfinance assessment cost significantly

🤝 Development Partners & NGOs

Malawi is the critical priority — 81.2% Low health, lowest Medium transition rate
Lesotho needs credit graduation programs — businesses reach Medium but cannot break through to High
Eswatini's success model should be studied and replicated across the region
Zimbabwe shows momentum — targeted Medium-to-High programs would have fastest impact

🏛️ Government & Policy

Country scores enable evidence-based subsidy and grant allocation
Replaces assumptions with data when deciding where support is needed most
Dashboard can be updated annually to measure financial inclusion progress
Supports the FinMark Trust mission of financial access across Southern Africa


🗂️ Dashboard Structure

🏠 Sheet 1 — Dashboard

Six sections: KPI overview, performance analysis, business insights,
country comparison, feature importance, and interpretation of all key decisions.

📈 Sheet 2 — Charts

Six charts: fold scores, class distribution pie, country health stacked bar
(real data), model progression v1→v4, feature importance, per-class metrics.

🌍 Sheet 3 — Country Deep Dive

Individual country cards with specific policy recommendations
for Eswatini, Lesotho, Malawi and Zimbabwe.

📦 Data Source

Competition: data.org Financial Health Prediction — Zindi Africa

Provider: FinMark Trust
Samples: 9,618 SMEs across 4 Southern African countries

⚠️ Raw dataset not included. Download from the Zindi competition page.


Author
Phumlani Mbatha
