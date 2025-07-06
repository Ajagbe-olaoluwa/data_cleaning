#  Data Science Job Listings – Data Cleaning & Preparation

This project focuses on cleaning and preparing a dataset of job listings for data science roles. The dataset was sourced from online job platforms and contains raw, unstructured information. My objective was to transform this messy data into a structured, analysis-ready format suitable for further exploration, modeling, and storytelling.

---

##  Dataset Overview

The dataset (`Uncleaned_DS_jobs.csv`) includes various job attributes such as:

- Job Title
- Salary Estimate
- Company Name and Rating
- Job Description
- Location
- Headquarters
- Company Size
- Type of Ownership
- Founded Year
- Industry and Sector
- Revenue
- Competitors

Many of these fields were messy, missing, or incorrectly formatted, and required extensive cleaning before analysis.

---

##  Project Goals

- Clean and standardize job-related fields (e.g., Job Title, Description)
- Separate combined fields (e.g., Company Name with Rating)
- Parse and convert salary estimates into numeric values
- Handle missing values and placeholder values (e.g., `-1`)
- Prepare the dataset for downstream tasks like EDA or modeling

---

##  Data Cleaning Workflow Summary

###  Step 1: Load Dataset  
Import the raw CSV into a pandas DataFrame for inspection and cleaning.

---

###  Step 2: Clean Job Descriptions and Extract Company Ratings  
Remove unreadable characters from job descriptions and separate ratings embedded within company names into their own column.

---

###  Step 3: Clean and Extract Salary Ranges  
Strip out symbols and text from salary estimates, and split them into minimum, maximum, and average numeric salary fields.

---

### ✅ Step 4: Clean Revenue, Company Size, and Competitors  
Standardize formats, remove extra text or placeholder values, and handle missing or null entries.

---

### Step 5: Apply Universal Cleaning to All Columns  
Run a final cleaning pass across all columns to remove unwanted characters, whitespace, and standardize missing data.

---

##  Project Outcome

After the cleaning process, the dataset was transformed into a well-structured form, enabling:

- Exploratory Data Analysis (EDA)
- Salary prediction modeling
- Comparative analysis by company, location, or industry
- Trend visualization across company size, ownership type, or rating

---

## 📂 Repository Structure

