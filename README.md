#  Data Science Job Listings – Data Cleaning & Preparation

This project involves cleaning a dataset of job listings for data science roles. The dataset includes fields like job title, salary estimate, company name, rating, location, revenue, competitors, and more. The goal is to transform raw, messy data into a structured and analysis-ready format.

---

##  Dataset Overview

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

##  Tools Used

- Python
- Pandas
- NumPy
- Regular Expressions (Regex)
- Jupyter Notebook / VS Code

---

##  Data Cleaning Workflow

###  Step 1: Load Dataset

```python
import pandas as pd
df = pd.read_csv('Uncleaned_DS_jobs.csv')



 ###  Step : Load Dataset



df['Job Description'] = df['Job Description'].str.encode('utf-8', 'ignore').str.decode('utf-8', 'ignore')


# Backup original column
df['Original Company Name'] = df['Company Name']

# Extract name and rating
extracted = df['Company Name'].str.extract(r'^(.*?)(?:\s*(\d\.\d))?$')
df['Company Name'] = extracted[0].combine_first(df['Original Company Name'])
df['Rating'] = extracted[1].astype(float)

# Drop helper column
df.drop(columns=['Original Company Name'], inplace=True)
# Remove parentheses text
df['Salary Estimate'] = df['Salary Estimate'].str.replace(r'\(.*?\)', '', regex=True).str.strip()

# Remove $ and K, then split
df['Salary Estimate Clean'] = df['Salary Estimate'].str.replace('$', '', regex=False).str.replace('K', '', regex=False)
df[['Min Salary', 'Max Salary']] = df['Salary Estimate Clean'].str.split('-', expand=True)

# Convert to integers
df['Min Salary'] = df['Min Salary'].astype(float).astype(int)
df['Max Salary'] = df['Max Salary'].astype(float).astype(int)

# Optional: Add average salary
df['Avg Salary'] = ((df['Min Salary'] + df['Max Salary']) / 2).astype(int)
import numpy as np

# Clean Revenue
df['Revenue'] = df['Revenue'].astype(str).str.replace(r'\(.*?\)', '', regex=True).str.strip()
df['Revenue'] = df['Revenue'].replace(['-1', ' -1', '-1.0', -1, -1.0], np.nan)

# Clean Company Size
df['Company Size'] = df['Company Size'].astype(str).str.replace('employees', '', regex=False).str.strip()

# Clean Competitors
df['Competitors'] = df['Competitors'].astype(str).str.strip().replace(['-1', ' -1', '-1.0', -1], np.nan)
def clean_dataframe(df):
    for col in df.columns:
        df[col] = df[col].astype(str).str.strip()
        df[col] = df[col].str.replace(r'\(.*?\)', '', regex=True)
        df[col] = df[col].replace(['-1', '-1.0', ' -1', '-1 ', ' -1.0 ', -1, -1.0], np.nan)
        df[col] = df[col].replace('', np.nan)
    return df

df = clean_dataframe(df)

