# 📊 Data Transformations and Analytical Summary

## 1. Data Cleaning and Preparation

The original dataset (`spotify_churn_dataset.csv`) was loaded into Google Sheets. Initial inspection showed the data was clean, with no missing values (8000 non-null entries for all 12 columns). Therefore, no additional cleaning was required.

The main preparation steps involved creating new categorical features and calculating core analytical metrics.

### 1.1. Categorical Transformations

| New Feature | Purpose | Formula (Google Sheets Style) | Segments |
| :--- | :--- | :--- | :--- |
| **`churn_status`** | Text label for the target variable (`is_churned`). | `=IF(Q2=1, "Churned Users", "Active Users")` | Active Users (0), Churned Users (1) |
| **`age_group`** | Grouping users into demographic cohorts. | `=IF(C2 < 18, "<18", IF(C2 < 25, "18-24", IF(C2 < 35, "25-34", IF(C2 < 55, "35-54", "55+"))))` | <18, 18-24, 25-34, 35-54, 55+ |
| **`skip_category`** | Grouping based on the level of song skipping. | `=IF(K2 < 0.25, "Low", IF(K2 < 0.35, "Medium", "High"))` | Low, Medium, High |
| **`engagement_group`** | Grouping based on activity level. | `IFS(H2<=0.33, "Low", H2<=0.66, "Medium", H2<=1, "High")` | Low, Medium, High |

### 1.2. Metric Calculation: Engagement Score and Index Calculation

The engagement metrics were transformed into a single, normalized score using a two-step process: calculating a raw score and then normalizing it to provide an `engagement_index` scaled between 0 and 1.

#### Step 1: Calculating the Engagement Score

The **`engagement_score`** represents the effective listening time, penalizing the raw listening time based on the user's skip rate.

| Feature | Purpose | Formula (Google Sheets Style) | Variables |
| :--- | :--- | :--- | :--- |
| **`engagement_score`** | Effective time spent listening (raw score). | `F2 * (1 - Data_raw!H2)` | F2: `listening_time` (Minutes)<br>Data\_raw!H2: `skip_rate` (as a decimal) |

#### Step 2: Normalizing to Engagement Index

The raw `engagement_score` was normalized using **Min-Max Scaling** to provide the final **`engagement_index`** (0 to 1), allowing for easy comparison and interpretation across all users.

| Feature | Purpose | Formula (Google Sheets Style) | Variables |
| :--- | :--- | :--- | :--- |
| **`engagement_index`** | Final normalized engagement score (scaled 0 to 1). | `=(G2 - MIN($G$2:$G$8001)) / (MAX($G$2:$G$8001) - MIN($G$2:$G$8001))` | G2: `engagement_score` (from Step 1) |

## 2. Key Analytical Findings and Conclusions

### 2.1. General Overview

The analysis covers **8,000 Spotify users**, offering detailed insights into churn behavior, engagement levels, listening patterns, and subscription dynamics. The overall churn rate is **25.9%**, while the average listening time is **154 minutes per day**. The average skip rate reaches **30%**, and Premium users represent **26.4%** of the total audience.

### 2.2. Demographic and Behavioral Insights

#### Age Groups:
* **Skip Rate:** Differences in skip rate across age groups are minimal, ranging between **29.7%** and **31%**. This indicates that age has limited influence on content skipping behavior.
* **Churn Rate:** Churn rate is also evenly distributed among age categories (approximately **25%**–**27%**), suggesting similar retention challenges across all demographics.

#### Engagement Levels:
* Engagement has a noticeable impact on churn. Users with **high engagement** show a lower **24.6%** churn rate, compared to **26.6%** among low-engagement users. This confirms that increased interaction with the platform contributes to higher loyalty and lower risk.

### 2.3. Subscription and Device Analysis

#### Subscription Type:
* The **Family plan** demonstrates the highest churn (**27.5%**), which is an unusual finding that requires further investigation into shared account behavior or pricing differentiation.
* **Free users** have a slightly lower churn (**24.9%**) than Family, which contradicts typical industry expectations.
* **Premium users** show moderate churn (**25.1%**), implying that simply having a paid subscription does not guarantee loyalty.

#### Device Usage:
* Churn is highest among **mobile users** (**26.9%**), indicating potential usability or stability issues on mobile platforms, which are critical for daily usage.
* Desktop (**25.7%**) and web (**25.0%**) users exhibit slightly better retention, possibly due to more stable or long-session usage behavior.

### 2.4. Country-Level Insights

* **Listening Time:** Average listening time varies slightly across countries (ranging from **152** to **157** minutes per day). Germany, France, India, and USA show the highest average listening time (**157** and **155** minutes), indicating stronger engagement.
* However, these differences are **not significant enough** to directly explain churn variations, suggesting that country of origin is a secondary factor compared to direct user behavior.

### 2.5. Key Conclusions

1.  **Engagement is the Strongest Predictor:** User engagement is the most reliable predictor of churn. **High-engagement users are less likely to churn**, highlighting the importance of personalized playlists, recommendations, and interactive features.
2.  **Subscription Value is Critical:** Subscription type **does not guarantee retention**. Premium and Family users still show notable churn levels, suggesting the need for **enhanced value differentiation** and loyalty programs that go beyond basic ad removal.
3.  **Mobile Experience Requires Optimization:** The **higher churn among mobile users** points to potential design, stability, or feature-related issues that must be addressed, given that mobile is the primary touchpoint for most users.
4.  **Behavioral Factors Dominate:** Age and geography play minor roles in user retention compared to immediate behavioral factors such as engagement level and device usage.
