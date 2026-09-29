# Marketing A/B Test Analysis

## 📊 Project Overview

This project analyzes the results of a marketing A/B experiment to determine whether an advertising treatment improved user conversion compared with a PSA control group.

The analysis goes beyond a simple conversion-rate comparison by evaluating:

* Conversion performance
* Absolute and relative lift
* Statistical significance
* Confidence intervals
* Risk and odds ratios
* Effect size
* Statistical power
* Minimum detectable effect (MDE)
* Experimental group allocation
* Day-level treatment consistency
* Ad-exposure patterns

The goal is to distinguish **statistical significance from practical business impact** and provide a data-driven interpretation of the experiment.

---

## 🎯 Business Problem

A marketing team wants to understand whether showing users the advertising treatment leads to higher conversion than showing the PSA control.

The key business question is:

> **Did the advertising treatment generate a meaningful improvement in conversion compared with the control group?**

The analysis evaluates both whether a difference exists statistically and whether the observed difference is meaningful from a business perspective.

---

## 📁 Dataset

The dataset contains user-level records from a marketing experiment, including:

* Experimental group (`ad` / `psa`)
* Conversion outcome
* Day of the week
* Total number of ads seen

The experiment contains approximately **588,101 users**.

### Experimental Allocation

| Group |   Users | Share |
| ----- | ------: | ----: |
| Ad    | 564,577 |  ~96% |
| PSA   |  23,524 |   ~4% |

The experiment therefore has a strongly unequal treatment/control allocation rather than a 50/50 split.

---

## 🔬 Methodology

The analysis was performed using Python and statistical methods appropriate for comparing two independent conversion proportions.

### 1. Exploratory Analysis

The dataset was examined to understand:

* Group sizes
* Conversion counts
* Conversion rates
* Distribution across days
* Ad exposure patterns

### 2. A/B Test

The primary metric was the conversion rate.

The null hypothesis was:

**H₀:** The conversion rates of the advertising and PSA groups are equal.

**H₁:** The conversion rates are different.

A **two-sided two-proportion z-test** was used with:

* Significance level: α = 0.05

### 3. Confidence Interval

A 95% confidence interval was calculated for the difference in conversion rates using an unpooled standard error.

### 4. Effect Size

The analysis calculated:

* Absolute lift
* Relative lift
* Risk ratio
* Odds ratio
* Cohen's h

### 5. Statistical Power & MDE

Power analysis was performed using Cohen's h to evaluate the experiment's sensitivity to different effect sizes.

The minimum detectable effect was calculated for:

* α = 0.05
* 80% statistical power
* Two-sided testing
* Observed treatment/control allocation ratio

### 6. Experiment Quality Checks

Additional analyses examined:

* Treatment/control allocation imbalance
* Conversion consistency across days
* Relationship between ad exposure and conversion

The ad-exposure analysis is treated as **observational/descriptive**, because exposure frequency was not itself randomly assigned.

---

## 📈 Key Results

### Conversion Performance

| Metric              |                               Result |
| ------------------- | -----------------------------------: |
| PSA conversion rate |                           **1.785%** |
| Ad conversion rate  |                           **2.555%** |
| Absolute lift       |         **+0.769 percentage points** |
| Relative lift       |                          **+43.09%** |
| 95% CI              | **[0.595, 0.943] percentage points** |

The advertising group had a higher observed conversion rate than the PSA group.

---

## 📊 Statistical Test

The two-proportion z-test produced:

| Metric      |            Result |
| ----------- | ----------------: |
| Z-statistic |        **7.3701** |
| P-value     | **1.705 × 10⁻¹³** |

The p-value is substantially below the 0.05 significance level, providing strong statistical evidence against the null hypothesis of equal conversion rates.

The 95% confidence interval for the treatment effect is entirely above zero.

---

## 📐 Effect Size

| Measure    |     Result |
| ---------- | ---------: |
| Risk ratio | **1.4309** |
| Odds ratio | **1.4421** |
| Cohen's h  | **0.0530** |

The standardized effect size is relatively small, while the observed business-facing difference is approximately **0.769 percentage points**.

This distinction is important: with a very large sample, a relatively modest conversion difference can be estimated with high statistical precision.

---

## ⚡ Statistical Power & MDE

The observed effect corresponds to a Cohen's h of approximately **0.053**.

The estimated statistical power for detecting the observed effect was approximately:

**100%**

At 80% statistical power, the estimated minimum detectable effect corresponded to approximately:

* **14.3% relative lift**
* **0.255 percentage points** above the baseline conversion rate

This indicates that the experiment had sufficient statistical sensitivity to detect effects smaller than the observed relative improvement.

---

## 🧪 Experimental Allocation

The observed allocation was highly imbalanced:

* **Ad:** ~96%
* **PSA:** ~4%

A hypothetical 50/50 allocation would have placed approximately 294,051 users in each group.

The unequal allocation does not prevent the two-proportion test from being performed, but it is important when interpreting experiment efficiency and precision. The smaller PSA group provides less information for estimating the control conversion rate.

---

## 📅 Time-Based Stability

Conversion rates were compared across the seven days represented in the dataset.

The advertising group had a higher observed conversion rate than the PSA group on each day.

This provides **directional consistency** with the overall treatment effect.

However, day-level comparisons are supporting evidence rather than independent replications of the experiment.

---

## 📺 Ad Exposure Analysis

Conversion rates were also examined across observed ad-exposure bands.

Conversion increased substantially across the exposure bands, with the highest observed conversion rates among users who saw the most ads.

However, this analysis is **observational rather than causal**.

Users were not randomly assigned to different ad-exposure frequencies, so the analysis cannot establish that increasing the number of ads shown would itself cause higher conversion.

---

## 💡 Business Interpretation

The experiment shows a statistically detectable difference in conversion between the advertising and PSA groups.

The observed difference was:

> **+0.769 percentage points, corresponding to approximately +43.09% relative lift.**

However, statistical significance alone should not determine a business rollout decision.

A complete business decision should also consider:

* Campaign cost
* Incremental revenue
* Customer acquisition economics
* User experience
* Ad fatigue
* Long-term retention
* Potential diminishing returns
* Whether the observed conversion lift translates into sufficient economic value

The ad-exposure analysis should not be used as evidence that simply increasing ad frequency will cause higher conversion.

---

## ⚠️ Limitations

### 1. Highly Unequal Group Allocation

The experiment contains approximately 96% advertising users and 4% PSA users.

The smaller control group limits the efficiency of the experimental comparison.

### 2. Large Sample Size

The very large sample makes it possible for relatively small differences to achieve statistical significance.

Therefore, statistical significance should be interpreted alongside effect size and business impact.

### 3. Exposure Analysis Is Observational

Ad exposure was not the randomized treatment variable.

Therefore, the relationship between exposure and conversion should not be interpreted as causal.

### 4. Conversion Is the Primary Outcome

The analysis focuses on conversion and does not directly evaluate downstream metrics such as revenue, retention, customer lifetime value, or profitability.

---

## 🛠️ Technologies Used

* **Python**
* **Pandas**
* **NumPy**
* **SciPy**
* **Statsmodels**
* **Matplotlib**
* **Jupyter Notebook**

---

## 📂 Project Structure

```text
marketing-ab-test-analysis/
│
├── data/
│   └── marketing_ab_test.csv
│
├── notebooks/
│   └── marketing_ab_test_analysis.ipynb
│
├── README.md
│
└── requirements.txt
```

---

## 📌 Key Takeaways

1. The advertising group recorded a **2.555% conversion rate**, compared with **1.785%** for the PSA group.
2. The observed absolute improvement was **0.769 percentage points**.
3. The corresponding relative lift was approximately **43.09%**.
4. The 95% confidence interval for the treatment effect was **[0.595, 0.943] percentage points**.
5. The two-proportion z-test produced a **z-statistic of 7.37** and a **p-value of 1.705 × 10⁻¹³**.
6. The observed treatment effect was directionally consistent across the seven days represented in the dataset.
7. The experiment had approximately **100% estimated power** for the observed effect under the specified assumptions.
8. The relationship between ad exposure and conversion is descriptive and **should not be interpreted as causal**.
9. Business rollout decisions should consider **incremental economic value and user impact**, not statistical significance alone.

---

## 👩‍💻 Skills Demonstrated

This project demonstrates practical skills in:

* A/B testing
* Hypothesis testing
* Statistical inference
* Confidence intervals
* Conversion-rate analysis
* Effect-size analysis
* Statistical power
* Minimum detectable effect
* Experimental design evaluation
* Data visualization
* Business interpretation
* Python-based data analysis
* Translating statistical results into business insights