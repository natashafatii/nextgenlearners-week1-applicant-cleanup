# 🧹 DataWrangle: Applicant Records Cleanup & Insights

[![Python](https://img.shields.io/badge/Python-3.10+-3776AB?logo=python&logoColor=white)](https://www.python.org/)
[![Pandas](https://img.shields.io/badge/Pandas-2.x-150458?logo=pandas&logoColor=white)](https://pandas.pydata.org/)
[![Matplotlib](https://img.shields.io/badge/Matplotlib-visualization-11557c?logo=plotly&logoColor=white)](https://matplotlib.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?logo=jupyter&logoColor=white)](https://jupyter.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

> NextGenLearners Data Science Internship — cleaning a messy applicant dataset with Pandas, then exploring it to find real, actionable patterns.

## 📌 Overview

Raw data is never clean, and clean data doesn't explain itself. This project covers both halves of that problem using a bootcamp applicant-tracking dataset:

- **Week 1** takes a raw CSV riddled with missing values, duplicate submissions, inconsistent formatting, and mistyped columns, and turns it into a trustworthy, analysis-ready dataset — every cleaning decision explained, not just executed.
- **Week 2** takes that cleaned dataset and actually digs into it — asking specific questions about applicant behavior, answering them with aggregations and charts, and summarizing what a program manager could act on.

## ✨ What's Inside

**Week 1 — Data Cleaning**

| Task | Description |
|------|-------------|
| 🔍 Exploration | Full profiling of the raw dataset — shape, dtypes, missing values, duplicates — before any changes are made |
| 🧩 Missing Value Handling | Column-by-column decisions (drop vs. fill), each with a written justification |
| 🔁 Deduplication | Exact duplicate rows removed, plus near-duplicates caught via a cleaned email key |
| 🔤 Text Standardization | Inconsistent spellings/casing mapped to single, consistent category labels |
| 🗓️ Type Correction | Text dates converted to real `datetime` objects; phone numbers normalized |
| 📊 Documentation | A full Data Quality Summary comparing the dataset before and after cleaning |

**Week 2 — Exploratory Data Analysis**

| Question | What It Answers |
|----------|------------------|
| Domain popularity | Which of the 5 applicant tracks gets the most applications |
| Time trend | How application volume changes month over month |
| Acceptance rate | Overall and per-domain breakdown of Selected / Rejected / Under Review, by count and by percentage |
| Top universities | Which schools send the most applicants, and how concentrated that is |
| Bonus: day of week | Whether applications cluster on certain days, and what that means for timing outreach |

## 🗂 Repository Structure

```
.
├── Week1_Data-Cleaning_Natasha-Fatima.ipynb   # Cleaning notebook — exploration, cleaning, documentation
├── Week2_EDA_Natasha-Fatima.ipynb              # EDA notebook — aggregations, charts, key insights
├── applicants.csv                        # Raw, unprocessed dataset
├── applicants_cleaned.csv                # Cleaned dataset (output of Week 1, input to Week 2)
└── README.md
```

## 🛠 Tech Stack

- **Python 3** — core language
- **[pandas](https://pandas.pydata.org/)** — data cleaning, aggregation, and reshaping
- **[matplotlib](https://matplotlib.org/)** & **[seaborn](https://seaborn.pydata.org/)** — visualization
- **[Faker](https://faker.readthedocs.io/)** — synthetic raw data generation
- **Jupyter Notebook** / **Google Colab** — interactive, documented workflow

## 🚀 Getting Started

### Option A — Google Colab (no setup required)
1. Open [Google Colab](https://colab.research.google.com)
2. Upload `Week1_Data_Cleaning_Natasha-Fatima.ipynb`, run all cells, and let it produce `applicants_cleaned.csv`
3. Upload `Week2_EDA_Natasha-Fatima.ipynb` and `applicants_cleaned.csv`, then run all cells

### Option B — Run locally
```bash
git clone https://github.com/natashafatii/nextgenlearners-week1-applicant-cleanup.git
cd nextgenlearners-week1-applicant-cleanup
pip install pandas faker matplotlib seaborn jupyter
jupyter notebook
```
Run `Week1_Data-Cleaning_Natasha-Fatima.ipynb` first, then `Week2_EDA_Natasha-Fatima.ipynb`.

## 🧪 Week 1: Cleaning Process

| Step | Issue Found | Action Taken |
|------|-------------|---------------|
| 1 | Missing `Applicant Name` / `Email` | Dropped — unusable without them |
| 2 | Missing `University` / `Status` | Filled with `"Not Specified"` / `"Under Review"` |
| 3 | Exact + near-duplicate applications | Removed via `drop_duplicates()` + cleaned-email matching |
| 4 | Inconsistent `Domain Applied` spellings | Mapped to standardized category labels |
| 5 | `Application Date` stored as text | Converted with `pd.to_datetime(..., format='mixed', errors='coerce')` |
| 6 | Inconsistent `Phone` formatting | Stripped to digits-only text |

**Before & After**

| Metric | Raw Data | Cleaned Data |
|--------|----------|--------------|
| Rows | 95 | 84 |
| Missing values (critical fields) | Several | 0 |
| Duplicate rows | Several | 0 |
| `Domain Applied` categories | 9+ inconsistent variants | 5 standardized values |
| `Application Date` dtype | `object` (text) | `datetime64` |

## 📊 Week 2: What the Data Shows

| Finding | Detail |
|---------|--------|
| Domain popularity | Graphic Design, App Development, Digital Marketing, and Data Science are tied at 18 applications each; Web Development trails at 12 |
| Peak activity | Applications ramp up from August 2025 and peak at 13 in March 2026, then decline |
| Best acceptance rate | App Development leads at 27.8% selected |
| Worst acceptance rate | Graphic Design, despite equal application volume to App Development — 50% rejected |
| Top universities | LUMS and FAST NUCES tied at 11 applicants each; top 3 schools make up ~45% of applications with a known university |
| Application timing | Wednesday and Monday are the busiest days; weekends are the quietest |

*(Full aggregation tables, all 6 charts, and the complete Key Insights section are in `Week2_EDA_Natasha-Fatima.ipynb`.)*

## 💡 Key Takeaways

- Missing data has no universal fix — the right call depends on how critical each field is.
- `drop_duplicates()` alone only catches exact matches; a cleaned key field (like email) reveals duplicates that formatting differences would otherwise hide.
- Mixed-format date columns need `format='mixed'`, not a single fixed format, or valid dates silently become `NaT`.
- Application volume and acceptance rate don't move together — the same number of applications can hide very different outcomes, which only shows up once you look at percentages, not raw counts.
- Documenting *why* a decision was made — in cleaning and in analysis — is what makes the results trustworthy, not just the numbers themselves.

## 📄 License

Released under the [MIT License](LICENSE).

---

<p align="center"><i>Built as part of the NextGenLearners Data Science Internship — Weeks 1 & 2.</i></p>
