# 🧹 DataWrangle: Applicant Records Cleanup

[![Python](https://img.shields.io/badge/Python-3.10+-3776AB?logo=python&logoColor=white)](https://www.python.org/)
[![Pandas](https://img.shields.io/badge/Pandas-2.x-150458?logo=pandas&logoColor=white)](https://pandas.pydata.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?logo=jupyter&logoColor=white)](https://jupyter.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

> Week 1 of the NextGenLearners Data Science Internship — cleaning and exploring a messy applicant dataset with Pandas.

## 📌 Overview

Raw data is never clean. This project takes a bootcamp applicant-tracking dataset riddled with missing values, duplicate submissions, inconsistent formatting, and mistyped columns, and transforms it into an analysis-ready dataset using Pandas — with every cleaning decision explained, not just executed.

## 📑 Table of Contents

- [What's Inside](#-whats-inside)
- [Repository Structure](#-repository-structure)
- [Tech Stack](#-tech-stack)
- [Getting Started](#-getting-started)
- [Cleaning Process](#-cleaning-process)
- [Before & After](#-before--after)
- [Key Takeaways](#-key-takeaways)
- [License](#-license)

## ✨ What's Inside

| Task | Description |
|------|-------------|
| 🔍 **Exploration** | Full profiling of the raw dataset — shape, dtypes, missing values, duplicates — before any changes are made |
| 🧩 **Missing Value Handling** | Column-by-column decisions (drop vs. fill), each with a written justification |
| 🔁 **Deduplication** | Exact duplicate rows removed, plus near-duplicates caught via a cleaned email key |
| 🔤 **Text Standardization** | Inconsistent spellings/casing mapped to single, consistent category labels |
| 🗓️ **Type Correction** | Text dates converted to real `datetime` objects; phone numbers normalized |
| 📊 **Documentation** | A full Data Quality Summary comparing the dataset before and after cleaning |

## 🗂 Repository Structure

```
.
├── Week1_Data_Cleaning_YourName.ipynb   # Main notebook — exploration, cleaning, documentation
├── applicants.csv                        # Raw, unprocessed dataset
├── applicants_cleaned.csv                # Final cleaned dataset
└── README.md
```

## 🛠 Tech Stack

- **Python 3** — core language
- **[pandas](https://pandas.pydata.org/)** — data cleaning and manipulation
- **[Faker](https://faker.readthedocs.io/)** — synthetic raw data generation
- **Jupyter Notebook** / **Google Colab** — interactive, documented workflow

## 🚀 Getting Started

### Option A — Google Colab (no setup required)
1. Open [Google Colab](https://colab.research.google.com)
2. Upload `Week1_Data_Cleaning_YourName.ipynb`
3. Upload `applicants.csv` when prompted
4. Run all cells (**Runtime → Run all**)

### Option B — Run locally
```bash
git clone https://github.com/natashafatii/nextgenlearners-week1-applicant-cleanup.git
cd nextgenlearners-week1-applicant-cleanup
pip install pandas faker jupyter
jupyter notebook Week1_Data_Cleaning_YourName.ipynb
```

## 🧪 Cleaning Process

| Step | Issue Found | Action Taken |
|------|-------------|---------------|
| 1 | Missing `Applicant Name` / `Email` | Dropped — unusable without them |
| 2 | Missing `University` / `Status` | Filled with `"Not Specified"` / `"Under Review"` |
| 3 | Exact + near-duplicate applications | Removed via `drop_duplicates()` + cleaned-email matching |
| 4 | Inconsistent `Domain Applied` spellings | Mapped to standardized category labels |
| 5 | `Application Date` stored as text | Converted with `pd.to_datetime(..., format='mixed', errors='coerce')` |
| 6 | Inconsistent `Phone` formatting | Stripped to digits-only text |

## 📈 Before & After

| Metric | Raw Data | Cleaned Data |
|--------|----------|--------------|
| Rows | *95* | *84* |
| Missing values (critical fields) | Several | 0 |
| Duplicate rows | Several | 0 |
| `Domain Applied` categories | 9+ inconsistent variants | 5 standardized values |
| `Application Date` dtype | `object` (text) | `datetime64` |

*(Exact counts are generated live in the notebook's Data Quality Summary section.)*

## 💡 Key Takeaways

- Missing data has no universal fix — the right call depends on how critical each field is.
- `drop_duplicates()` alone only catches exact matches; a cleaned key field (like email) reveals duplicates that formatting differences would otherwise hide.
- Mixed-format date columns need `format='mixed'`, not a single fixed format, or valid dates silently become `NaT`.
- Documenting *why* a decision was made is what makes a cleaned dataset trustworthy — not just the cleaning itself.

## 📄 License

Released under the [MIT License](LICENSE).

---

<p align="center"><i>Built as part of the NextGenLearners Data Science Internship — Week 1.</i></p>
