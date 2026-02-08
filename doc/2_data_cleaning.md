# Data Cleaning Documentation – Movie Correlation Project

## Overview
This document records every data cleaning step completed so far in the *Python Movie Correlation Project*.  
It includes the **reason for each step**, the **exact code used**, and the **result**, so the work is easy to reproduce and easy to explain in an interview.

---

## 1. Import Libraries

**Purpose:**  
Import the libraries needed for data loading, cleaning, and plotting.

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
```

---

## 2. Load the Dataset

**Purpose:**  
Load the CSV file from the project folder into a pandas DataFrame and preview the first rows.

```python
df = pd.read_csv("../data/movies.csv")
df.head()
```

**Outcome:**  
The dataset loaded successfully and displayed the first five rows.

---

## 3. Check Missing Values (Percent)

**Purpose:**  
Identify which columns contain missing values and how many, as a percentage.  
This helps decide whether to drop rows, fill values, or leave as-is.

```python
# Check percentage of missing values per column
for col in df.columns:
    pct_missing = df[col].isna().mean()
    print(f"{col}: {pct_missing:.1%}")
```

**Outcome:**  
All columns were `0.0%` missing except **`budget`**, which showed approximately **`0.3%`** missing values.

---

## 4. Remove Rows with Missing Values

**Purpose:**  
Remove rows with missing data so calculations (especially correlations) are not affected by null values.  
Because the missing percentage was small, dropping rows was a safe and reasonable choice.

```python
# Remove rows with missing values
df = df.dropna()

# Confirm missing values are gone
df.isna().sum()
```

**Outcome:**  
All columns showed `0` missing values after dropping null rows.

---

## 5. Check Column Data Types

**Purpose:**  
Confirm each column has the correct data type.  
This matters because correlations and calculations work correctly only when numeric fields are stored as numeric types.

```python
# Check data types
df.dtypes
```

**Outcome:**  
Several numeric columns were stored as `float64`, including `budget`, `gross`, `votes`, and `runtime`.

---

## 6. Convert Numeric Columns to Integers

**Purpose:**  
Convert numeric fields to integer format where appropriate.  
These values represent whole numbers, so integers improve consistency and readability.

```python
# Convert numeric columns to integers
df["budget"] = df["budget"].astype(int)
df["gross"] = df["gross"].astype(int)
df["votes"] = df["votes"].astype(int)
df["runtime"] = df["runtime"].astype(int)
```

**Verification:**

```python
df.dtypes
```

**Outcome:**  
`budget`, `gross`, `votes`, and `runtime` were successfully converted to `int64`.  
`score` remained `float64`, which is correct because movie ratings are decimal values.

---

## 7. Create a Correct Year Column from Released Date

**Purpose:**  
The dataset contains both a `year` column and a `released` column.  
Some values in the original `year` column are inconsistent, so a corrected year needed to be derived from the `released` date field.

---

### 7.1 First Attempt (Failed Approach)

**Approach:**  
The initial attempt assumed the year appeared at the start of the `released` string and tried to extract the first four characters.

```python
df["year_correct"] = df["released"].astype(str).str[:4].astype(int)
```

**Issue:**  
Many `released` values start with the **month name** (for example, `"June 13, 1980 (United States)"`).  
Extracting the first four characters returned strings like `"June"` or `"July"`, which cannot be converted to integers.

**Result:**  
This caused a `ValueError` when attempting to convert non-numeric strings to integers.

---

### 7.2 Final Solution (Regex-Based Extraction)

**Approach:**  
To reliably extract the year regardless of date format, a regular expression was used to capture any four-digit number within the `released` string.

```python
df["year_correct"] = (
    df["released"]
    .astype(str)
    .str.extract(r"(\d{4})")
    .astype(int)
)
```

**Verification:**

```python
df[["year", "year_correct"]].head()
```

**Outcome:**  
The corrected year was successfully extracted for all rows, producing a consistent and reliable year field.

---

## 8. Remove the Original Year Column (Option 1)

**Purpose:**  
Remove the original `year` column to avoid ambiguity and ensure only the corrected year is used for analysis.

```python
df = df.drop(columns=["year"])
```

**Outcome:**  
The dataset now contains a single, reliable year column (`year_correct`) for analysis.

---

## Data Cleaning Status

✅ Missing values checked and handled  
✅ Data types reviewed and corrected  
✅ Year extracted reliably from released date  
✅ Ambiguous year column removed  
✅ Dataset is clean and ready for analysis

---

## Next Step

Proceed to **Exploratory Data Analysis and Correlation Analysis**, starting with sorting by `gross` revenue and analysing relationships between movie features.
