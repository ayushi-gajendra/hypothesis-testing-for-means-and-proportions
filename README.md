# 🌙 Statistical Analysis of Human Sleep Patterns & Stress

### *Hypothesis Testing for Health Metrics and Behavioral Insights*

-----

## 🎯 Project Overview

Using a dataset of **179 daily observations** from a wearable fitness tracker, I conducted a statistical deep dive into a user's sleep architecture. The goal was to move beyond descriptive summaries and use **Inferential Statistics** to determine if the user is suffering from stress-induced sleep deprivation.

This project specifically applies **Hypothesis Testing for Means** (REM Sleep) and **Hypothesis Testing for Proportions** (Sleep Duration) to validate health claims with statistical significance.

-----

## 📂 Data Source & Feature Glossary

The analysis was conducted using the [Sleep Data from FitBit Tracker](https://www.kaggle.com/datasets/riinuanslan/sleep-data-from-fitbit-tracker) dataset.

### **Dataset Features**

| Feature | Description | Analytical Utility |
| :--- | :--- | :--- |
| **DATE** | The calendar date of the sleep session. | Identifies longitudinal trends. |
| **SLEEP SCORE** | Aggregate quality metric (0-100). | Represents overall sleep health. |
| **HOURS OF SLEEP** | Total time spent asleep. | Variable for testing sleep duration proportions. |
| **REM SLEEP** | % of sleep in Rapid Eye Movement stage. | Variable for testing stress-related cognitive recovery. |
| **DEEP SLEEP** | % of sleep in physically restorative stage. | Indicator of physical recovery. |
| **HEART RATE BELOW RESTING** | % of sleep with HR lower than daily resting. | Proxy for cardiovascular recovery and low stress. |

### **Sample Data Reference**

| DATE | SLEEP SCORE | HOURS OF SLEEP | REM SLEEP | DEEP SLEEP | HEART RATE BELOW RESTING |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 04/01/2022 | 90 | 7.37 | 18 | 21 | 98 |
| 04/02/2022 | 89 | 8.67 | 21 | 21 | 73 |
| 04/03/2022 | 81 | 8.87 | 21 | 17 | 26 |
| 04/04/2022 | 83 | 6.83 | 17 | 19 | 99 |

-----

## ⚙️ Methodology & Analytical Process

### 🔍 Phase 1: Analyzing REM Sleep (Testing for Means)

**Objective:** Determine if the user's REM sleep is significantly below the healthy threshold of 20%, which would indicate high stress levels.

**1. Steps Followed:**

  * Set the significance levels at $\alpha = 0.05$ and $\alpha = 0.01$.
  * Calculated sample metrics using `AVERAGE`, `STDEV`, and `COUNT`.
  * Computed the **Test Statistic ($z$)** to find the distance from the mean.
  * Calculated p-values using both Normal and t-distributions.

**2. Hypotheses:**

  * **$H_0$ (Null):** $\mu = 20$ (Normal)
  * **$H_1$ (Alternative):** $\mu < 20$ (Stress-impacted)
  * **Test Type:** Left-tailed test.

**3. Formulas Used:**

  * **Test Statistic ($z$):** $z = \frac{\bar{x} - \mu}{s / \sqrt{n}}$
  * **p-value (Normal):** `NORM.S.DIST(z, TRUE)` or `1 - Z.TEST(array, 20)`

**4. Results Table:**
| Metric | Calculated Value |
| :--- | :--- |
| **Sample Mean ($\bar{x}$)** | 19.39 |
| **Standard Deviation ($s$)** | 3.91 |
| **Sample Size ($n$)** | 179 |
| **Test Statistic ($z$)** | -2.08 |
| **p-value (Normal)** | **0.0187** |
| **p-value (t-dist)** | **0.0194** |

-----

### 📊 Phase 2: Analyzing Sleep Duration (Testing for Proportions)

**Objective:** Confirm if the user meets the healthy 7-hour sleep goal in at least 75% of their tracked nights.

**1. Steps Followed:**

  * Used `COUNTIF` to find the number of nights where sleep $\ge$ 7 hours.
  * Calculated the **Sample Proportion ($\hat{p}$)**.
  * Applied the Standard Error formula for proportions to find the Test Statistic.

**2. Hypotheses:**

  * **$H_0$ (Null):** $p = 0.75$
  * **$H_1$ (Alternative):** $p > 0.75$
  * **Test Type:** Right-tailed test.

**3. Formulas Used:**

  * **Sample Proportion:** $\hat{p} = \frac{\text{count}}{n}$
  * **Test Statistic ($z$):** $z = \frac{\hat{p} - p_0}{\sqrt{\frac{p_0(1-p_0)}{n}}}$

**4. Results Table:**
| Metric | Calculated Value |
| :--- | :--- |
| **Count (Nights $\ge$ 7hrs)** | 140 |
| **Total Sample ($n$)** | 179 |
| **Sample Proportion ($\hat{p}$)** | 0.782 |
| **Test Statistic** | 0.99 |
| **p-value (Normal)** | **0.1605** |

-----

## 💡 Final Interpretation & Inference

### **1. The Stress Evidence (REM Sleep)**

  * **Statistical Decision:** At $\alpha = 0.05$, we **Reject the Null Hypothesis** ($0.0187 < 0.05$).
  * **Business Inference:** There is significant evidence that the user is suffering from suppressed REM sleep. This statistically supports the hypothesis that the user is undergoing significant stress, which is inhibiting cognitive recovery stages.
  * **Sensitivity Note:** At a stricter $\alpha = 0.01$, we would fail to reject the null, highlighting the importance of choosing an appropriate significance level for health diagnostics.

### **2. The Consistency Paradox (Sleep Duration)**

  * **Statistical Decision:** We **Fail to Reject the Null Hypothesis** ($0.1605 > 0.05$).
  * **Business Inference:** Although the user's raw proportion (78.2%) is higher than the goal (75%), the difference is not statistically significant. We cannot confidently claim the user is "exceeding" the 7-hour sleep target; their performance is statistically consistent with the baseline.

### **3. Final Conclusion**

The user has a **Quality vs. Quantity** problem. While they are successfully spending enough time in bed (Quantity), their internal sleep architecture—specifically REM sleep—is statistically deficient (Quality). Recommendations would focus on stress-management interventions rather than simply increasing sleep duration.

-----

## 👤 Author

**Ayushi Gajendra**
*Data Analyst | Strategy Specialist*

  * **Portfolio References:**
      * [Confidence Intervals for Means](https://github.com/ayushi-gajendra/confidence-intervals-for-means)
      * [Confidence Intervals for Proportions](https://github.com/ayushi-gajendra/confidence-intervals-for-proportions)
