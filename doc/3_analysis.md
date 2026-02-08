# Analysis: Movie Correlation Analysis

## Objective
The objective of this analysis is to explore relationships between movie features and identify which factors are most strongly associated with box office revenue (`gross`). The analysis focuses on correlation patterns rather than causation.

---

## Dataset Overview
After data cleaning, the dataset contains movies with the following key features:

- Numeric features: score, votes, budget, gross, runtime, year
- Categorical features: name, rating, genre, released, director, writer, star, country, company

Two approaches were used:
1. Correlation using **numeric features only**
2. Exploratory correlation using **numerized categorical features**

---

## Correlation Method
Pearson correlation was used throughout the analysis to measure the strength and direction of linear relationships between features.

---

## 1. Correlation Matrix (Numeric Features Only)

Only numeric columns were included to ensure valid Pearson correlation calculations.

```python
correlation_matrix = df.corr(numeric_only=True, method="pearson")
