# Movie Correlation Analysis

This section documents the full exploratory data analysis and correlation analysis performed on the movie dataset.
All steps below follow the exact order and code executed in the Jupyter Notebook.

---

## 1. Inspecting High and Low Grossing Movies

To better understand the distribution of movie earnings, the dataset was sorted by gross revenue in descending order.
This helps identify blockbuster films as well as low-performing movies.

```python
# Order our data a little bit to see
df.sort_values(by=["gross"], inplace=False, ascending=False)
```
![mca](/images/1.png)
---

## 2. Scatter Plot: Budget vs Gross (Matplotlib)

A scatter plot was created to visually inspect the relationship between a movie’s production budget and its gross earnings.

```python
# Scatter plot with budget vs gross
plt.scatter(x=df["budget"], y=df["gross"], alpha=0.5)
plt.title("Budget vs Gross Earnings")
plt.xlabel("Budget for Film")
plt.ylabel("Gross Earnings")
plt.show()
```
![mca](/images/2.png)
---

## 3. Budget vs Gross with Regression Line (Seaborn)

To better visualise the trend and strength of the relationship, a regression line was added using Seaborn.

```python
# Plot budget vs gross using seaborn
sns.regplot(
    x="budget",
    y="gross",
    data=df,
    scatter_kws={"color": "red"},
    line_kws={"color": "purple"}
)
```
![mca](/images/3.png)
---

## 4. Correlation Matrix (Numeric Columns Only)

A correlation matrix was generated using only numeric columns to quantify relationships between numerical features.

```python
# Correlation matrix (numeric columns only)
corr_matrix = df.corr(numeric_only=True, method="pearson")
corr_matrix
```
![mca](/images/5.png)
---

## 5. Heatmap of Numeric Correlations

To improve interpretability, the numeric correlation matrix was visualised as a heatmap.

```python
plt.figure(figsize=(10, 6))
sns.heatmap(
    corr_matrix,
    annot=True,
    cmap="coolwarm",
    vmin=-1,
    vmax=1
)
plt.title("Correlation Matrix for Numeric Features")
plt.show()
```
![mca](/images/4.png)
---

## 6. Converting Categorical Columns to Numeric Codes

To explore correlations involving categorical features, all categorical columns were converted to numeric codes.
This transformation is strictly for exploratory correlation purposes and does not imply ordinal meaning.

```python
# Convert categorical columns to numeric codes (for exploratory correlation)
df_numerized = df.copy()

categorical_cols = df_numerized.select_dtypes(
    include=["object", "string"]
).columns

for col in categorical_cols:
    df_numerized[col] = df_numerized[col].astype("category").cat.codes

df_numerized.head(10)
```
![mca](/images/6.png)
---

## 7. Correlation of All Features with Gross Revenue

To identify which features are most strongly associated with movie revenue, correlations with `gross` were sorted in descending order.

```python
df_numerized.corr()["gross"].sort_values(ascending=False)
```
![mca](/images/7.png)
---

## 8. Correlation Matrix (All Features – Numerized)

Finally, a full correlation matrix was created using the numerized dataset, including both original numeric and encoded categorical features.

```python
# Correlation matrix (All Features - Numerized)
correlation_matrix = df_numerized.corr(method="pearson")

plt.figure(figsize=(15, 8))
sns.heatmap(
    correlation_matrix,
    annot=True,
    cmap="coolwarm",
    vmin=-1,
    vmax=1
)
plt.title("Correlation Matrix (All Features - Numerized)")
plt.show()
```
![mca](/images/8.png)
---

## End of Analysis

This concludes the exploratory data analysis and correlation investigation for the movie dataset.
