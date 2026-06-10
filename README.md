# Customer Sign-Up Behaviour & Data Quality Audit

## Overview
This project evaluates customer sign-up behaviour and audits data quality for Rapid Scale, a SaaS business that offers multiple subscription plans.

The analysis transforms raw customer registration data into clean, reliable data and delivers clear business insights for marketing, onboarding, and support decisions.

## What This Project Covers
- Data loading and initial inspection.
- Cleaning and standardising customer sign-up records.
- Detecting missing, inconsistent, and invalid values.
- Producing summary metrics for sign-ups by week, source, region, plan, age, and gender.
- Answering key business questions about acquisition performance, data quality, and support activity.
- Exporting clean data and summary results for reporting.

## Files in the Repository
- `customer_signups.csv`: raw customer sign-up dataset.
- `customer_signups_cleaned.csv`: cleaned dataset produced by the notebook.
- `support_tickets.csv`: optional support ticket dataset for stretch analysis.
- `weekly_signups.csv`: weekly sign-up totals.
- `source_summary.csv`: sign-ups by acquisition source.
- `region_summary.csv`: sign-ups by region.
- `plan_summary.csv`: sign-ups by plan.
- `Week1_Project.ipynb`: notebook containing the full data workflow.

## How to Use the Notebook
1. Open `Week1_Project.ipynb`.
2. Run cells in order from top to bottom.
3. Review the cleaning and validation steps.
4. Inspect the summary outputs and charts.
5. Review the business answers and recommendations.
6. Use the exported CSV files for further analysis or dashboards.

## Detailed Workflow

### 1. Load and inspect the data
- Load `customer_signups.csv` with pandas.
- Look at the first rows to understand the fields.
- Check column data types, row count, and missing values.
- Identify duplicate `customer_id` values.

### 2. Clean the dataset
- Convert `signup_date` from text to datetime.
- Standardise text fields such as `plan_selected`, `gender`, and `source`.
- Convert `age` to numeric and identify invalid ages.
- Remove duplicate rows using `customer_id`.
- Replace invalid category values with `NaN` or `Unknown`.
- Fill missing values using appropriate defaults:
  - `age` → median age.
  - `region` → `Unknown`.
  - `marketing_opt_in` → most frequent value.
  - `plan_selected` and `gender` → `Unknown`.

### 3. Validate data quality
- Recompute missing values after cleaning.
- Measure the percentage of missing data per column.
- Confirm the number of duplicates removed.
- Track how many invalid values were corrected.

### 4. Create summary outputs
- Weekly sign-up counts (`weekly_signups.csv`).
- Sign-ups by acquisition source (`source_summary.csv`).
- Sign-ups by region (`region_summary.csv`).
- Sign-ups by selected plan (`plan_summary.csv`).
- Marketing opt-in behaviour by gender.
- Age distribution and summary statistics.

### 5. Answer business questions
The notebook answers these questions:
- Which acquisition source brought the most users last month?
- Which region shows signs of missing or incomplete data?
- Are older users more or less likely to opt in to marketing?
- Which plan is most commonly selected, and which age group selects it most?
- (Optional) Which plan’s customers are most likely to contact support?

### 6. Export results
- Save the cleaned dataset to `customer_signups_cleaned.csv`.
- Save summary tables to `weekly_signups.csv`, `source_summary.csv`, `region_summary.csv`, and `plan_summary.csv`.

## Business Questions and Findings

### Top acquisition source
- **Answer:** `Youtube`
- YouTube generated the highest number of customer sign-ups.
- **Insight:** This channel is the strongest acquisition source in the current data.

### Region data quality issue
- **Answer:** `Unknown`
- Records tagged with `Unknown` region show incomplete geographic data.
- **Impact:** Regional analysis is less reliable until registration data improves.

### Marketing opt-in by age
- Older customers are slightly more likely to opt in to marketing.
- The 46–60 age group shows the highest opt-in rate.
- **Insight:** Older customers may be more receptive to promotional communications.

### Most common plan and age group
- **Answer:** `Premium` is the most common plan.
- Premium adoption is strongest in the `31–45` age group.
- **Insight:** Mid-career customers appear to value the Premium offering most.

### Support contact rate by plan
- **Answer:** `Pro` plan users contact support most often among defined subscription plans.
- Premium users have the lowest support contact rate.
- **Insight:** The Pro plan may need better onboarding, support guidance, or self-service resources.

## Data Quality Issues Identified
Key issues found in the dataset:
- Missing or `Unknown` region values.
- Inconsistent plan values such as `PREMIUM`, `prem`, and `basic`.
- Invalid `gender` values and inconsistent capitalization.
- Unrealistic ages outside the expected range.
- Missing email values or incomplete customer fields.

### Risk and recommendation
- These issues reduce the accuracy of customer segmentation and trend analysis.
- Recommend adding validation at data entry: required fields, dropdown menus, and standardized categories.

## Key Recommendations
- Continue or expand investment in YouTube marketing.
- Improve registration data collection for region, plan, and customer demographics.
- Review onboarding and support resources for Pro plan customers.
- Target the 31–45 age group with Premium plan promotion.

## Notes
- The notebook is the primary source of truth for data cleaning and analysis.
- Exported CSV files are ready for reporting and dashboard use.
- The support ticket analysis is optional and uses `support_tickets.csv` for extended insight.

