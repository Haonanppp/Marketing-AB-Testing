# Marketing A/B Testing: Ads vs PSA

This repository contains a simple, end-to-end **marketing A/B test analysis** using a randomized experiment dataset. Most users were shown an **advertisement** (treatment group), while a smaller portion were shown a **PSA** (control group) in the same placement. The notebook evaluates whether ads drive higher conversions and explores whether conversion varies by the time users saw the most ads.

---

## Business Questions

1. **Would the campaign be successful?**  

2. **If the campaign was successful, how much of that success could be attributed to the ads?**  

---

## Dataset

A marketing A/B testing dataset with experiment and control groups.

### Data Dictionary 
| Column          | Description |
|-----------------|---|
| `index`         | Row index |
| `user id`       | Unique user identifier |
| `test group`    | `"ad"` if user saw advertisement; `"psa"` if user saw PSA |
| `converted`     | `True` if user purchased, else `False` |
| `total ads`     | Number of ads shown to user |
| `most ads day`  | Day of week with the most ads shown to the user |
| `most ads hour` | Hour of day with the most ads shown to the user |

---

## What the Notebook Does

### 1) Load & Inspect
- Reads the CSV
- Checks basic shape, types, and summary stats
- Reviews unique values for key fields

### 2) Preprocess
- Drops non-analytic identifier columns (`index`, `user id`)
- Converts `converted` from boolean to numeric (0/1) for analysis

### 3) Visualize
- Conversion rate comparison: **ad vs psa**
- Conversion rate by:
  - `most ads day`
  - `most ads hour`

### 4) Statistical Testing
- **A/B comparison (ad vs psa):**  
  - Uses an **independent two-sample t-test** on `converted` (0/1) to test whether average conversion differs across groups.
- **Timing effects (exploratory):**
  - **One-way ANOVA** to test whether conversion differs across:
    - `most ads day`
    - `most ads hour`