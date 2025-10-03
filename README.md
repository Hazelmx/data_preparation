# Workflow for Data Preparation and Balance Check
## Step 1. Build the Participant × Time Period Matrix
Run file: Data_preparation and coupon matrix.ipynb, control matrix.ipynb, delivery matrix.ipynb

Each intervention group (Coupon, Delivery, Control) has its own matrix.

Rows = participants (43 coupon, 42 delivery, 41 control).

Columns = 39 time bins (2-week periods: 13 pre-trial, 13 in-trial, 13 post-trial).

Raw data is transformed into a Participant × Time Period panel dataset.

## Step 2. Calculate Outcomes for Each Participant–Period

Sales variables

sales_fv: FV sales in Schnucks records.

sales_fv_a_1 and sales_fv_a_2: Adjusted to include delivery box value for Delivery group.

fv_out_of_pocket: Deducts coupon value from FV sales.

dp_out_of_pocket: Out-of-pocket spending on dietitian-picked items.

sales_diet, sales_other: Dietitian-picked vs other items.

Portion variables

portion_: FV portion standardized from oz/lb/EA.

portion_a: Portion + delivery box portion (Delivery group only).

Other engagement variables

product_count: Unique items per period.

transaction_count: Number of transactions.

unique_day: Shopping frequency (days with purchases).

## Step 3. Add Inactive Transaction Records

Insert rows for participants × time bins where no purchases occurred.

Ensures dataset is balanced panel (complete coverage of all participants and all time periods).

## Step 4. Calculate Adjusted Outcomes

Finalize adjusted variables:

portion_a

sales_fv_a_1

sales_fv_a_2

This provides the full set of outcomes for both per-protocol and intent-to-treat analyses.

# Time Series Analysis
Run file: time series.ipynb

Cohorts (1–11) define start/end dates for pre-trial, in-trial, and post-trial phases.

Outcomes are aggregated using two approaches:

Active participants only (per-protocol, higher values, more variability).

All participants (intent-to-treat, lower values, smoother trends).

# Balance Check Workflow
Run file: Balance_check_outcomes.ipynb
## Step 1. Select Pre-Trial Data

Includes cohorts 1–14 (excluding 5 and 11).

## Step 2. Apply Balance Tests

t-test / ANOVA: compare means.

Kolmogorov–Smirnov (KS test): compare distributions.

Standardized Mean Difference (SMD): effect size relative to pooled SD.

