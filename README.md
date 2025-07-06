# 🧹 Data Science Job Listings – Data Cleaning & Preparation

This project involves cleaning a dataset of job listings for data science roles. The dataset includes fields like job title, salary estimate, company name, rating, location, revenue, competitors, and more. The goal is to transform raw, messy data into a structured and analysis-ready format.

---

## 📁 Dataset Overview

The dataset (`Uncleaned_DS_jobs.csv`) contains job listings scraped from various online platforms. Some of the key columns include:

- `Job Title`
- `Salary Estimate`
- `Company Name`
- `Rating`
- `Location`
- `Size`
- `Founded`
- `Type of Ownership`
- `Revenue`
- `Competitors`

---

## 🛠️ Tools Used

- Python
- Pandas
- NumPy
- Regular Expressions (Regex)
- Jupyter Notebook / VS Code

---

## 🔄 Data Cleaning Workflow

### ✅ Step 1: Load Dataset

```python
import pandas as pd
df = pd.read_csv('Uncleaned_DS_jobs.csv')
