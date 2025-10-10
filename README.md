# 🎧 Spotify Churn Prediction & Engagement Analysis (2025)

## 🌟 Project Overview

This project focuses on **Exploratory Data Analysis (EDA)** and data transformation to understand user engagement patterns and customer churn for a simulated Spotify dataset. The analysis was initially performed using Google Sheets and is now documented and stored here on GitHub.

The primary objective is to identify key factors leading to customer cancellations and provide actionable insights to help Spotify reduce its churn rate.

## 🎯 Key Objectives

1.  **Data Transformation:** Clean and structure the raw dataset for analysis.
2.  **Dashboard Creation:** Develop a data visualization dashboard (initially in Google Sheets) to display key performance indicators (KPIs) and churn drivers.
3.  **Result Analysis:** Analyze engagement metrics, subscription types, and device usage to pinpoint high-risk user segments.

---

## 💾 Dataset Information

| Column (Feature) | Description | Data Type |
| :--- | :--- | :--- |
| `user_id` | Unique identifier for each user. | `int64` |
| `gender` | User gender (Male/Female/Other). | `object` |
| `age` | User age. | `int64` |
| `country` | User location (e.g., US, CA, AU). | `object` |
| `subscription_type` | Type of Spotify subscription (Free, Premium, Family, Student). | `object` |
| `listening_time` | Minutes spent listening per day. | `int64` |
| `songs_played_per_day` | Number of songs played daily. | `int64` |
| `skip_rate` | Percentage of songs skipped (engagement metric). | `float64` |
| `device_type` | Device used (Mobile, Desktop, Web). | `object` |
| `ads_listened_per_week` | Number of ads heard per week. | `int64` |
| `offline_listening` | Binary indicator for offline mode usage (0/1). | `int64` |
| `is_churned`** | Target Variable (0 = Active, 1 = Churned). | `int64` |

* **Total Rows:** 8,000
* **Source:** [Spotify Analysis Dataset 2025 on Kaggle](https://www.kaggle.com/datasets/nabihazahid/spotify-dataset-for-churn-analysis)
* **Author:** **Nabiha Zahid**

---

## 📁 Repository Structure

This repository is structured to mirror the workflow used in the Google Sheets analysis:

| File Name | Corresponds to | Description |
| :--- | :--- | :--- |
| `data` | Raw Data | The original synthetic dataset used for the project. |
| `analysis_summary.md` | Data Transformations & Results | Documentation detailing the methodology, calculations, and analytical results . |
| `dashboard_visual.png` | Final Dashboard | A static image of the complete data dashboard created for visualization. |
| `README.md` | Project Overview | This introductory document. |

---

## 🔗 Accessing the Dashboard

You can explore the final visual output and interactive elements in two ways:

1.  **Original Google Sheets File (Live Dashboard):**
    ➡️ [**View the Live Dashboard**](https://docs.google.com/spreadsheets/d/1sjBFOMVOue-nFIxbvK54OrxckE3BrRtAlOsdBpQJY-w/edit?usp=sharing)

2.  **Dashboard Static Image:**
    The general layout and metrics are visible in the static image file:
    
    *(Refer to the `dashboard_visual.png` file for the full dashboard view.)*
